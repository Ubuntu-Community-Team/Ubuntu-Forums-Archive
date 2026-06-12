---
title: "Rescue files from Wubi?"
date: 2010-11-02
forum: New to Ubuntu
---

### Post by irishface on 2010-11-02
Hi all, 

Apologies for starting another thread. I'm looking for advice on rescuing files after wubi has failed/will not boot. Does anyone have any experience with this? 

I have - 

Samsung Netbook N150
Ubuntu netbook remix 10.4
Via Wubi (Windows 7 starter)

Ubuntu will not boot (I have tried all the kernels). Windows starts as normal. I tried ubuntu from a usb drive and it started no problem.  (Original thread here -[ http://ubuntuforums.org/showthread.php?t=1610864]("http://ubuntuforums.org/showthread.php?t=1610864")) 


Any advice would be greatly appreciated. 

Thanks

---

### Post by cpmman on 2010-11-02
Have you tried the options shown in the WubiGuide (booting problems and file accessing)? - (click in my signature.)

---

### Post by Hippytaff on 2010-11-02
> **irishface said:**
> Hi all, 
 
Apologies for starting another thread. I'm looking for advice on rescuing files after wubi has failed/will not boot. Does anyone have any experience with this? 
 
I have - 
 
Samsung Netbook N150
Ubuntu netbook remix 10.4
Via Wubi (Windows 7 starter)
 
Ubuntu will not boot (I have tried all the kernels). Windows starts as normal. I tried ubuntu from a usb drive and it started no problem. (Original thread here -[ http://ubuntuforums.org/showthread.php?t=1610864]("http://ubuntuforums.org/showthread.php?t=1610864")) 
 
 
Any advice would be greatly appreciated. 
 
Thanks
 Any luck with the documentation?

---

### Post by oldfred on 2010-11-02
Some more info:

How-to: Recover files from Wubi install with LiveCD
[http://neosmart.net/forums/showthread.php?t=5004](http://neosmart.net/forums/showthread.php?t=5004)
[Script] Mount Wubi Disk from Linux mount old wubi in new install
mount ntfs partition first:
[http://ubuntuforums.org/showthread.php?t=1037874](http://ubuntuforums.org/showthread.php?t=1037874)
mkdir /mnt/windows
mount -o loop /mnt/windows/ubuntu/disks/root.disk /mnt/ubuntu

---

### Post by irishface on 2010-11-02
Thanks for all the responses. I used the method quoted below and managed to rescue some of my files. Disaster averted! Still going to have a long, hard think before I make the move to ubuntu properly, though. 

Cheers for all your help and for being gentle with me! 


> **oldfred said:**
> Some more info:

How-to: Recover files from Wubi install with LiveCD
[http://neosmart.net/forums/showthread.php?t=5004](http://neosmart.net/forums/showthread.php?t=5004)


---

### Post by Hippytaff on 2010-11-02
glad you sorted it, but any os can break - that's why people keep banging on about backing stuff up :-)

If you decide to give ubuntu another bash for any length of time a real partition is far more stable than Wubi :-)

---

