---
title: "Are these compatible with Ubuntu 8.10"
date: 2009-02-26
forum: New to Ubuntu
---

### Post by mistypotato on 2009-02-26
[B][SIZE="5"]libc.so.6

librt.so.1[/SIZE][/B]

---

### Post by smani on 2009-02-26
Those libraries are provided by packages that can be found in the intrepid repositories, hence yes.
Generally, if you search for a specific file, I would recommend you apt-file:
```

sudo apt-get install apt-file
sudo apt-file update
sudo apt-file search filename
```

---

### Post by mistypotato on 2009-02-26
ok, thx.

When I open synaptic, they arent there so you say they're in the repositories ?


Also, when I ran sudo apt-get install libc.so.6


it said  "couldn't find package"

---

### Post by smani on 2009-02-26
They are part of packages that are found in the repositories, by using apt-file you can identify in which package they are. For example
```
sandro@PC4:~$ apt-file search libc.so.6
libc6: /lib/libc.so.6
libc6-dbg: /usr/lib/debug/libc.so.6
libc6-i386: /lib32/libc.so.6
ppu-sysroot: /usr/lib/cell/sysroot/lib/libc.so.6
ppu-sysroot64: /usr/lib/cell/sysroot/lib64/libc.so.6
sandro@PC4:~$ apt-file search librt.so.1
libc6: /lib/librt.so.1
libc6-dbg: /usr/lib/debug/librt.so.1
libc6-i386: /lib32/librt.so.1
ppu-sysroot: /usr/lib/cell/sysroot/lib/librt.so.1
ppu-sysroot64: /usr/lib/cell/sysroot/lib64/librt.so.1

```
Tells you that the files you are searching are in the libc6 package (okay, they are also in the ppu one, chances are high that you are searching for a file that is located in a directory which is in your PATH environment variable)

---

### Post by mistypotato on 2009-02-26
thnks for the assist smani :D

---

