---
title: "Help connecting HTC G1"
date: 2010-06-19
forum: New to Ubuntu
---

### Post by adobrakic on 2010-06-19
Usually when I plug my G1 into my laptop, a popup comes up on the phone asking if I want to mount it, and I press that and the computer recognizes it as a removable disk. When I plug it into my laptop running Ubuntu, the mount option on my phone never comes up. Are there some drivers I have to download?

---

### Post by ieee488 on 2010-06-19
[http://androidforums.com/support/3534-problems-mounting-communicating-g1-ubuntu.html](http://androidforums.com/support/3534-problems-mounting-communicating-g1-ubuntu.html)

---

### Post by adobrakic on 2010-06-20
> If you've got the udev rule added

Check

> turned on USB Debugging on your G1

Check

> and everything else seems to work

When I plug my phone in, the orange LED comes on, indicating that the battery is charging. I think this shows that there's at least a connection between the phone and the computer. 

> adb kill-server


```
ado@ado-laptop:~$ adb kill-server

No command 'adb' found, did you mean:
 Command 'cdb' from package 'tinycdb' (main)
 Command 'gdb' from package 'gdb' (main)
 Command 'aub' from package 'aub' (universe)
 Command 'dab' from package 'bsdgames' (universe)
 Command 'zdb' from package 'zfs-fuse' (universe)
 Command 'mdb' from package 'mono-debugger' (universe)
 Command 'tdb' from package 'tads2-dev' (multiverse)
 Command 'pdb' from package 'python' (main)
 Command 'jdb' from package 'openjdk-6-jdk' (main)
 Command 'ab' from package 'apache2-utils' (main)
adb: command not found
ado@ado-laptop:~$ 
```

I used [this](http://bradchow.wordpress.com/2009/02/16/adb-on-windows-and-ubuntu-linux/) to install ADB, but it still says it cant find the command.

---

### Post by adobrakic on 2010-06-21
Bumpage. Anyone?

---

