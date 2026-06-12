---
title: "shell scripts, 2 files and wait command?"
date: 2009-09-16
forum: New to Ubuntu
---

### Post by Kaymeerah on 2009-09-16
```
#! /bin/sh
# EVE
#
#
metacity --replace
cd /home/kaymeerah/.wine/drive_c/EVE && wine eve.exe && wait -1 ; compiz --replace
```


thats my shell script, however thanks to EVE launching an exe file JUST for the splash, THEN ExeFile.exe, it starts compiz again when eve.exe dies, any ideas how i can wait for ExeFile.exe?

---

### Post by bodhi.zazen on 2009-09-16
use sleep

```
sleep 1
```

---

### Post by Kaymeerah on 2009-09-16
i cant use sleep, it just doesnt fit in

---

