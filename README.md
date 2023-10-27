![a night owl](https://github.com/trouchet/eule/blob/main/images/eule_small.png?raw=true)

[![Version](https://img.shields.io/pypi/v/eule.svg)](https://pypi.python.org/pypi/eule)
[![python](https://img.shields.io/pypi/pyversions/eule.svg)](https://pypi.org/project/eule/)
[![downloads](https://img.shields.io/pypi/dm/eule)](https://pypi.org/project/eule/)
[![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/trouchet/eule/HEAD)

[![codecov](https://codecov.io/gh/trouchet/eule/branch/main/graph/badge.svg?token=PJMBaLIqar)](https://codecov.io/gh/trouchet/eule)
[![Documentation Status](https://readthedocs.org/projects/eule/badge/?version=latest)](https://eule.readthedocs.io/en/latest/?version=latest)
[![Lint workflow](https://github.com/trouchet/eule/actions/workflows/check-lint.yaml/badge.svg)](https://github.com/trouchet/eule/actions/workflows/check-lint.yaml)

Euler\'s diagrams are non-empty Venn\'s diagrams. For further information about:

1. the library: on URL <https://eule.readthedocs.io>;
2. Euler diagrams: on wikipedia article <https://en.wikipedia.org/wiki/Euler_diagram>

Motivation
================

<img src="https://github.com/trouchet/eule/blob/main/images/euler_venn.png?raw=true" width="400" height="364"/>

How to install
================

We run the command on desired installation environment:

``` {.bash}
pip install eule
```

Minimal example
================

<details>
    <summary>
    Click to unfold usage
    </summary>

We run command `python example.py` on the folder with file `example.py` and following content:

``` {.python}
#!/usr/bin/env python
from eule import euler, euler_keys, euler_boundaries, Euler

sets = {
    'a': [1, 2, 3],
    'b': [2, 3, 4],
    'c': [3, 4, 5],
    'd': [3, 5, 6]
}

euler_diagram = euler(sets)
euler_keys = euler_keys(sets)
euler_boundaries = euler_boundaries(sets)
euler_instance=Euler(sets)

# Euler dictionary:
# {'a,b': [2], 'b,c': [4], 'a,b,c,d': [3], 'c,d': [5], 'd': [6], 'a': [1]}
print(euler_diagram)
print(euler_instance.as_dict())

print('\n')

# Euler keys list:
# ['a,b', 'b,c', 'a,b,c,d', 'c,d', 'd', 'a']
print(euler_keys)
print(euler_instance.euler_keys())

print('\n')

# Euler boundaries dictionary:
# {
#   'a': ['b', 'c', 'd'],
#   'b': ['a', 'c', 'd'],
#   'c': ['a', 'b', 'd'],
#   'd': ['a', 'b', 'c']
# }
print(euler_boundaries)
print(euler_instance.euler_boundaries())

print('\n')

# Euler instance match:
# {'a'}
# {'a', 'b'}
# {'c', 'a', 'b'}

print(euler_instance.match({1,2,3}))
print(euler_instance.match({1,2,3,4}))
print(euler_instance.match({1,2,3,4,5}))

print('\n')

# Euler instance getitem dunder:
# [1, 2, 3]
# [1, 2, 3]
# [1, 2, 3, 4]
# [1, 2, 3, 4, 5]
print(euler_instance['a'])
print(euler_instance[('a', )])
print(euler_instance[('a', 'b', )])
print(euler_instance[('a', 'b', 'c',)])

print('\n')

# Euler instance remove_key:
euler_instance.remove_key('a')
print(euler_instance.as_dict())
```

</details>
