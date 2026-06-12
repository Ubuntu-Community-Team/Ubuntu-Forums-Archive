---
title: "Video cards, backups, and Multi Boot (oh, I'm also a noob)"
date: 2009-01-26
forum: New to Ubuntu
---

### Post by mvalenti on 2009-01-26
Ok so I have been running Ubuntu 8.1 for about a week. I love it. There were many issues in the beginning mainly my nvidia fx5200 128mb video card. I would use the 177 drivers and the system would act up. Like if I used a pull down, the contents were illegible as well as any windows. So I had to reinstall. I have not enabled the 177 or the 93? drivers for fear of screwing up and reinstalling again. I would like to back up my present install so I can try some of the suggestions here in forums, but my backup ([http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)) steps in this thread gave me errors.. I am unconformable with BASH, trying to learn.. Any suggestions? Once I solve the first 2 I will be creating a drive for multiboot, some windows programs i NEED dont run under wine. But I'm sure there are fixes there too, but I am affraid to do anything until I back my system up.

-Mark

jetway v600dap motherboard
Athlon xp 2400+
1 gig 400ddr ram
fx5200 nvidia 128mb
(2) 40 gb drives
(1) 300 gb drive

---

### Post by candtalan on 2009-01-26
A simple backup app is sbackup (simple backup) although it is not intended to restore a system like windows Restore I believe. Also it is tricky to know if it has finished its activity. In a terminal you can use command:
htop 

There may be other apps for you.

It almost sounds as if you are thinking of taking an image of the partition? Once you know what to do - it is easy.....

Ubuntu is generally so easy and quick to install, that a common approach is to backup your data files (the directory /home/user) at least, and use these if you need to re install.

Nowadays I use a completely separate directory ( /data) and ensure that a re install does not touch it.

btw if Wine does not play nice, it might be easier at first to use dual boot maybe, even though it may feel uncomfortable?

btw
for nvidia drivers I recently discovered the app
envyng-gtk
may be worth considering at some time.

---

### Post by mvalenti on 2009-01-26
Much appreciated! I will look into that for sure! And yes, I think I will, gulp, have to do a dual boot..  sobs...

---

### Post by mvalenti on 2009-01-27
Still real buggy. I have shut down desktop effect. Hoping better drivers come soon.

---

