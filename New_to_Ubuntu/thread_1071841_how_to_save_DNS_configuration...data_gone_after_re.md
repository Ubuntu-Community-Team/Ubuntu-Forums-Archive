---
title: "how to save DNS configuration...data gone after reboot"
date: 2009-02-16
forum: New to Ubuntu
---

### Post by ozark_hillbilly on 2009-02-16
Two steps will solve this:

Remove the package resolvconf
with:
sudo aptitude remove resolvconf

Resolvconf is the package which will always check for dns at boot.

Then to fix /etc/resolv.conf so that no system process can change it use:

sudo chattr +i /etc/resolv.conf


also how do I set myself up as super user or administrator so that i don't have to keep adding password in Terminal mode?




Tks,

Ed

---

### Post by cariboo on 2009-02-16
THe only thing I can suggest for your dns problem is to add it to /etc/resolv.conf.

If you are running intrepid, the floppy module is not installed by default. To load the floppy module, open a terminal and type:

```
sudo modprobe floppy
```

You should now be able to mount your floppy by typing:

```
sudo mount /dev/fd0 /media/fd0
```

Jim

---

### Post by ozark_hillbilly on 2009-02-16
Jim,

What is procedure to:

add DNS data to /etc/resolv.conf   ???

Ed

---

### Post by matchstich on 2009-02-16
[https://www.opendns.com/start/ubuntu.php](https://www.opendns.com/start/ubuntu.php)

the site is for adding opendns , but it does show how to save dns changes.

at the bottom of page , shows where to go and what changes need to be made, be sure to un-commentt the prepend line after you add the opendns numbers

---

