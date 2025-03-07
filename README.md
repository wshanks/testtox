A small project to test building an sdist and wheel with tox.

`python -m build` builds an sdist and then a wheel from it.
Here there is a `MANIFEST.in` that excludes `__main__.py`.
Using

```shell
python -m build
pip install dist/testtox-0.1.0-py3-none-any.whl
PYTHONSAFEPATH=1 python -m testtox
```

gives

```
.tox/py/bin/python: No module named testtox.__main__; 'testtox' is a package and cannot be directly executed
```

as does

    tox run

while

    tox --override testenv.package=wheel run

prints `hello, tox` because it is packaging `__main__.py` by skipping the sdist.
