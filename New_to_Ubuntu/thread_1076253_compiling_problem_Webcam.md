---
title: "compiling problem: Webcam"
date: 2009-02-21
forum: New to Ubuntu
---

### Post by dlawler on 2009-02-21
when trying to compile the drivers from my webcam, as provided by someone else (the commands that is) this is what i get:

daniel@daniel-laptop:~$ cd r5u87x && make
make: Nothing to be done for `all'.
daniel@daniel-laptop:~/r5u87x$ 

......

---

### Post by dlawler on 2009-02-21
so i figured i'd try running ./config 

it worked. but then i try this bit:

sudo ./loader --reload -f ucode/r5u87x-05ca-1839.fw

amd get this:

daniel@daniel-laptop:~/r5u87x$ sudo ./loader --reload -f ucode/r5u87x-05ca-1839.fw
r5u87x firmware loader v0.2

Searching for device...
Found camera: 0000:0000
Warning: Failed to get microcode status.

Error: Failed to upload firmware to device: Broken pipe (code -32).
daniel@daniel-laptop:~/r5u87x$

---

