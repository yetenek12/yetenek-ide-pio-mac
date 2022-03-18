Put the contents of the .platformio folder here. Then delete this file.

## PlatformIO'yu tasinabilir hale getirmek icin;

1. penv/bin/ icindeki dosyalarin ilk satirindaki path'i duzenle
```
#!/bin/sh
"exec" "`dirname $0`/python" "$0" "$@"
```
See: https://stackoverflow.com/questions/20095351/shebang-use-interpreter-relative-to-the-script-path/33225909#33225909

2. Fix platformio python symbolic link
```
~ rm .platformio/penv/bin/python3

~ cd .platformio/penv/bin

~ ln -s ../../python3/bin/python3 python3
```

3. penv/pyvenv.cfg birinci satiri duzelt

```
home = ../python3/bin
```

4. penv/bin/activate dosyalarindaki VIRTUAL_ENV degiskenini ../ yap

```
VIRTUAL_ENV="../"
```

5. penv/bin/bottle.py icindeki 
```
from __future__ import with_statement
```
satirini en basa al