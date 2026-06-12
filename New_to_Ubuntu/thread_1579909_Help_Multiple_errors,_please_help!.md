---
title: "Help: Multiple errors, please help!"
date: 2010-09-22
forum: New to Ubuntu
---

### Post by gmerindol on 2010-09-22
mount: mounting /dev on /root/dev failed: No such file or directory 
mount: mounting / sys/ on root/sys failed: No such file or directory 
mount: mounting /proc on /root/proc failed: No such file or dirctory 
Target filesystem doesn't have /sbin/init. No init found. Try passing init= boot arg 
BusyBox v1.10.2 (Ubuntu 1:1.10.2.2ubuntu7) built-in shell (ash) 

This is what apparently has failed. ( I think, im only a beginner)

So, basically what happened was that i left my computer on (running ubuntu 9.10) to update, and while i thought it was charging it wasn't and i went to sleep, the next morning it was shut down and it wouldn't boot and that was the error it gave me. I tried using the 9.10 CD, no luck it won't boot it's stuck at the loading screen, same with the 9.04 Live CD, no luck. Anyone know how to fix this?

(I don't care about my data, i didn't have anything on there)

I'm running a dell d620 with intelcore duo. 32 bit....

Please help me, i've searched everywhere with no answer.

---

### Post by ubudog on 2010-09-23
Well, if you don't care about your data, then you can just reinstall Ubuntu.  Install from the CD or USB Disk again, fixing everything (but wiping out everything).

---

### Post by Rubi1200 on 2010-09-23
Post the results of the bootscript linked to at the bottom of my post so we can see what your setup looks like.

You need to do this from the LiveCD.

Chances are, however, that you may have to reinstall as ubudog suggested.

---

### Post by ubudog on 2010-09-23
Or, you can use Gparted, which is included in the livecd, just post a screenshot of it here.

---

### Post by Jazzy_Jeff on 2010-09-23
Excuse me if I am being dense, but I believe he has stated that he cannot boot into the CD. I am not sure what to do about this myself. The only thing I can suggest is to download the alternate install cd and see if it will boot into that. I have problems using live CD's as well.

---

### Post by Rubi1200 on 2010-09-23
> **Jazzy_Jeff said:**
> Excuse me if I am being dense, but I believe he has stated that he cannot boot into the CD. I am not sure what to do about this myself. The only thing I can suggest is to download the alternate install cd and see if it will boot into that. I have problems using live CD's as well.
Not dense; good point.

Or try burning another CD on another computer or if your computer allows it create a LiveUSB and boot from that.

---

### Post by Jazzy_Jeff on 2010-09-23
> **Rubi1200 said:**
> Not dense; good point.

Or try burning another CD on another computer or if your computer allows it create a LiveUSB and boot from that.

I always get a busybox error whenever I try and use the Live CD. The alternate install CD works every time.

---

### Post by gmerindol on 2010-09-23
Thanks a lot all of you,

Could any one point me out to where to find the alternate install CD?

Thanks

---

### Post by Rubi1200 on 2010-09-23
Here: [http://www.ubuntu.com/desktop/get-ubuntu/alternative-download#alternate](http://www.ubuntu.com/desktop/get-ubuntu/alternative-download#alternate)

---

### Post by ubudog on 2010-09-23
Or you could boot off USB if that's possible.

---

### Post by bcbc on 2010-09-23
Have you tried an older kernel? Hold down SHIFT at startup to see grub menu, then select another kernel.

---

### Post by ubudog on 2010-09-23
Sometimes that works for me.

---

