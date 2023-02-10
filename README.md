# Helm `merge` bug

### Rendering with no values
```
$ helm template ./chart
---
# Source: chart/templates/test.yaml
parent:
  a: null
  b: 2
```

### Rendering with values
```
$ helm template ./chart --set config.parent.c=3
```
#### Expected
We expect `a: null` to be present in the result
```
---
# Source: chart/templates/test.yaml
parent:
  a: null
  b: 2
  c: 3
```

#### Actual
However, it is not
```
---
# Source: chart/templates/test.yaml
parent:
  b: 2
  c: 3
```


