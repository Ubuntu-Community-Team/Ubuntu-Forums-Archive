---
title: "ubuntu doesn't start"
date: 2009-05-27
forum: New to Ubuntu
---

### Post by seseberg on 2009-05-27
I just downloaded wubi and ubuntu 9.04 32-bit, and installed it onto my toshiba satellite a305d-s6848 with plenty of hard drive space. I selected 30 gigs from wubi, because I need to do some dara recovery in ubuntu (dont ask why) and I need to use dd which will make a huge .img of a drive.
The thing is that everytime I select ubuntu from my boot manager (I have windows 7 32-bit installed) I get this error and ubuntu takes me to the initramfs command line.
I have had ubuntu 9.04 installed through wubi even before under this same windows (I think) but Ive uninstalled it because I didnt need it any longer, and now that I do need it again, this odd problem pops up. No, please dont suggest me to install through cd, because I dont want to, I like the idea of quickly getting rid of the OS once Im done with it, without having to modify partition structurs.

Please if anyone knows the answer to this help me!
Thanks!!!

---

### Post by Hospadar on 2009-05-27
I don't know anything about wubi, but:

If you're just doing data recovery, why do you even need to install ubuntu at all, just running it off the livecd will let you dd your drive (and it's a better way to do it since you don't need to mount the filesystem in any way).

Also you could install to a usb stick, that would certainly provide easy OS removal

---

### Post by seseberg on 2009-05-27
the thing is that I need to dd if=/dev/disk0 | ssh <username>@<computer-ip> 'dd of=iphone-dump.img' an I need 16 gb of free space..............................................
oh yeah, and some stuff I install needs restarting................
why, just why can't ubuntu function normally as any os does? (boot-up-wise)

---

### Post by Mark Phelps on 2009-05-28
Admit up front that I'm not a Wubi expert, but there have been a LOT of posts on this forum of folks trying to get Wubi to work under Windows 7 and not succeeding.

There is a very new version out and perhaps it works better under Windows 7 -- but understand, you're talking about an OS that's still not scheduled to be released for several months  (July or October, depending on who you believe).  

So, it's not surprising that a Linux tool doesn't work well with it yet.

---

### Post by seseberg on 2009-05-28
What's that got to do with anything? Windows 7 has absolutely zero issues as far as I use it, and it's the best Windows OS ever made. Not to mention Ubuntu's 8.10 and 9.04 sata issues......... give me a break, even a freakin windows xp without any service pack can properly boot up from a sata hard drive, but no, the oh so bragged about ubuntu cant because it's to developed.......................
people have been submitting bug reports to launchpad for 2 years now and the issue hasn't been fixed (I have an other post with that specific issue). Someone HAS found the fix, but no one cared about it, neither did they bother to add it to the kernel... 
[http://kerneltrap.org/mailarchive/git-commits-head/2008/6/14/2122314](http://kerneltrap.org/mailarchive/git-commits-head/2008/6/14/2122314)

the fact that ubuntu behaves so poorly with even unraided sata hard drives has led me to use wubi unfortunately......... but not even this one works..........

---

