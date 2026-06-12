---
title: "Synaptic Package Manager"
date: 2009-04-21
forum: New to Ubuntu
---

### Post by goose2378 on 2009-04-21
I just installed Ubuntu 8.10 a few days ago and have been trying to learn how to use it. was trying to use a tutorial online. instructions were to go to System - Administration - Synaptic Package Manager. i got there, and got an error message  
E: dpkg was interupted, you must manually run 'dpkg --configure -a' to correct problem. E: _cache-> open() failed, please report.   
i have no idea what this means or how to report it. if anyone out there could clue me in as to what to do to fix this, it would be greatly appreciated. and if this has already been addressed, please point me in the right direction to search for it. thanks.

---

### Post by Lunx on 2009-04-21
> **goose2378 said:**
> I just installed Ubuntu 8.10 a few days ago and have been trying to learn how to use it. was trying to use a tutorial online. instructions were to go to System - Administration - Synaptic Package Manager. i got there, and got an error message  
E: dpkg was interupted, you must manually run 'dpkg --configure -a' to correct problem. E: _cache-> open() failed, please report.   
i have no idea what this means or how to report it. if anyone out there could clue me in as to what to do to fix this, it would be greatly appreciated. and if this has already been addressed, please point me in the right direction to search for it. thanks.


I am a luddite at most of this so cant give you a reason why it happens (someone here will explain hopefully), however if you run the command that the message threw up it should sort everything out. Open a terminal **Applications --> Accessories --> Terminal**, then enter the following code

```
sudo dpkg --configure -a
``` 

That should get it working for you again

---

### Post by huxain1981 on 2009-04-21
> **goose2378 said:**
> I just installed Ubuntu 8.10 a few days ago and have been trying to learn how to use it. was trying to use a tutorial online. instructions were to go to System - Administration - Synaptic Package Manager. i got there, and got an error message  
E: dpkg was interupted, you must manually run 'dpkg --configure -a' to correct problem. E: _cache-> open() failed, please report.   
i have no idea what this means or how to report it. if anyone out there could clue me in as to what to do to fix this, it would be greatly appreciated. and if this has already been addressed, please point me in the right direction to search for it. thanks.

did you run the command in the terminal
```
sudo dpkg --configure -a
```

you need "sudo" cause the command needs root privilege.

---

### Post by barney385 on 2009-04-22
> **huxain1981 said:**
> did you run the command in the terminal
```
sudo dpkg --configure -a
```you need "sudo" cause the command needs root privilege.

I have the same problem and this is my output:

barney@barney-laptop:~$ sudo dpkg --configure -a
dpkg: failed to write status record about `gnome-terminal' to `/var/lib/dpkg/status': No space left on device
barney@barney-laptop:~$

---

### Post by llamabr on 2009-04-22
It looks like your disk is full.  You have been downloading movies to your hard drive, and now you need to delete some.

Post the output of:

```
df -h
```

---

### Post by juancarlospaco on 2009-04-22
**sudo apt-get clean ; sudo apt-get autoremove**

install and use Bleachbit

---

### Post by barney385 on 2009-04-23
Unfortunately, I borked my OS. It became completely unresponsive. I couldn't even go into safe mode or use my earlier kernel.

I reinstalled, and I'm currently updating Ubuntu 8.04LTS.

The reason this happened is I was downloading a bunch of stuff from synaptic and aborted in the middle of the download.

My fault.

Fortunately I always keep back-ups, so this will only be minor annoyance...

Thanks for your responses guys.

I wish I had those commands you posted Carlos, but I'll definitely make a note of them for future crashes...

:smile:

---

### Post by llamabr on 2009-04-24
> **barney385 said:**
> Unfortunately, I borked my OS. It became completely unresponsive. I couldn't even go into safe mode or use my earlier kernel.

I reinstalled, and I'm currently updating Ubuntu 8.04LTS.

The reason this happened is I was downloading a bunch of stuff from synaptic and aborted in the middle of the download.

My fault.

Fortunately I always keep back-ups, so this will only be minor annoyance...

Thanks for your responses guys.

I wish I had those commands you posted Carlos, but I'll definitely make a note of them for future crashes...

:smile:

quitting a dload in the middle from synaptic shouldn't hurt your system at all.  You can just begin it again, and it will start where you left off.

The reason is that your disk is too full.  apt-get clean will delete all those old debs that are already installed, and that you don't need anymore.  This would have freed plenty of disk space.

---

