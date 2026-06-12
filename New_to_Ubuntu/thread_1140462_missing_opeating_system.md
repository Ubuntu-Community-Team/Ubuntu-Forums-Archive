---
title: "missing opeating system?"
date: 2009-04-27
forum: New to Ubuntu
---

### Post by natman on 2009-04-27
i had vista on my latop and it was givng me a "missing operating system at boot up " i ran bootrec.exe/fixmbr to repair the master boot record. That fixed the problem fine, now i have kubuntu installed and the "missing operating system " is back again. The message always just stays there for about 1 sec then everthing is as normal. So my question is should i run grub or windows to fix the problem?

---

### Post by ibuclaw on 2009-04-27
First, run:
```
bootrec.exe/fixmbr
```
This will allow Vista to overwrite the mbr, but since we want **grub** to control it, you will have to next boot into your **Kubuntu LiveCD**, open **konsole** (a terminal) and run the following:
```
sudo grub
```
Then type in:
```
find /boot/grub/stage1
```
It may output something like this:
> 
find /boot/grub/stage1
 (hd0,3)
grub> 

The value outputted in (brackets) is what you will need for the next command.
```
root (hd0,3)
```
Lastly, install grub on the mbr again:
```
setup hd0
```
Then type in
```
quit
```
to quit, and you can close/reboot and remove the CD from the tray.

Regards
Iain

---

