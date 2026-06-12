---
title: "[SOLVED] Vista Boot problem"
date: 2008-12-05
forum: New to Ubuntu
---

### Post by MasterShihoChief on 2008-12-05
I recently created a dual boot on my system. I had windows vista, and i partioned the drive and made room for ubuntu 8.10. Grub worked great and everything was working perfectly. I could boot to either vista or ubuntu, but i mostly stuck with ubuntu cuz vista i such crap. I was able to mount a drive called "WINXP" and was able to import my music into amarok, and was able to run games i already preinstalled there through wine. Like i said perfect :). Then however today i went to boot up vista because i needed to sync my iphone, and it wouldnt boot vista. The picture i posted is of the error and i took it with my iphone. Now i know how to fix vista and make it boot. I could just insert my vista dvd and type:
Bootrec /RebuildBcd
Bootrec /FixMBR
Bootrec /Fixboot

But then i assume that overwrites Grub and would kill linux which i dont want to happen. I wouldnt know how to do that, and if any of this would fix my problem anyways. It might just leave me with a bricked comp. 

What is my best course of action so i can get vista back, so i can boot to it, and mount it again inside of ubuntu(since i cant now)

---

### Post by nhasian on 2008-12-05
i had the same problem when i used gparted to resize my partitions.  i just booted off a windows vista cd.  it detected a problem with the ntloader or bootloader or whatever its called and asked if i wanted to fix it.  after it fixed it I still had the grub menu and could then boot into either vista or ubuntu.  worst case scenario if vista does clobber grub you can use the super grub disc to fix it afterwards.

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by caljohnsmith on 2008-12-05
Just run those commands you posted *except* the "bootrec /fixmbr" command, because that will replace Grub with a Windows MBR. In other words, run:
```
bootrec /rebuildbcd
bootrec /fixboot
```
And also it is a good idea to run a chkdsk to make sure you don't have any basic file system problems that need correcting:
```
chkdsk /r

```
Doing all the above commands is probably all it will take to get Vista booting OK again, based on what you describe. How about giving it a shot and let me know how it goes. :)

---

### Post by MasterShihoChief on 2008-12-05
No good vista wants to install. I can't get to repair console to start command prompt. It sees three partitions to install on. The vista partition named WINXP like when I mounted it in ubuntu. The Linux swap partition
And ubuntu are also in the partition list. Does this mean a complete reinstall of vista? I know that might kill grub so I guess I use that super grub disk listed above.

---

### Post by caljohnsmith on 2008-12-05
How about downloading a Vista Recovery CD from [here]("http://neosmart.net/blog/2008/download-windows-vista-x64-recovery-disc/"), and then you can use that to run those commands. Let me know how that goes.

---

### Post by MasterShihoChief on 2008-12-05
Ok so I booted from that disk. It detected vista , it restarted it repaired. Then it did a check of drive h formatted FAT which I assume was a USB flash drive I had plugged in. It went to the desktop and ya it worked cept for **** being slow or not starting or stuff being corrupted and crashing. But ya that's vista I will do a chkdsk /r later. Booted to ubuntu and no problems, it booted but I'm still unable to mount the vista partition the ubuntu and it's done it successfully before. I guess that's a new question XD.  Thanks to ur help I appreciate it

---

### Post by MasterShihoChief on 2008-12-06
I fixed the vista mounting problem as well myself, everything is perfect again, thanks a lot for the help. I would like to apologize for the grammar. I posted all from my iphone, which has an epic fail autocorrect system that screws up everything I type :( 
(PROBLEM SOVED)
(THREAD CLOSED)

---

### Post by caljohnsmith on 2008-12-06
Glad to hear you have it working; cheers and have fun with your OSes. :)

---

