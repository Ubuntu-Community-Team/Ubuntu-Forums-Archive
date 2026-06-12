---
title: "installing windows on a system already running ubuntu"
date: 2009-10-22
forum: New to Ubuntu
---

### Post by gwilkins82 on 2009-10-22
ok.  first off, completely satisfied with ubuntu - been a convert for about a year now (looking forward to 10/29!).  that said, i want to install windows as well for a dual boot system for a few compatibility issues - espn360, a few other apps as well.  to do this, i need to partition my HD.  i have downloaded both gparted and the ntfs extension for it, but am still unclear as to how i need to go about doing this.  anyone? bueller?  thanks for any info!

---

### Post by Dark_Stang on 2009-10-22
You need to repartition your drive. Depending on how much you're using windows and which version you're using you'll want to allocate plenty of space for it. Whenever you boot the windows disc to install just choose the new ntfs partition you created. After you get Windows installed you'll have to use your Ubuntu live CD and re-install Grub because windows is going to hijack your master boot record.

That's about as simplified as I can make it. There are some step by step directions if you search google.

---

### Post by gwilkins82 on 2009-10-22
right - i guess my question is how to repartition - searched around a bit and havent found anything i really understand.  would it just be easier to back up what i have, install windows and then reinstall ubuntu from within windows?  or, i also have an external (usb) hd - is it possible to install windows on that?  btw, thanks for the ultraquick reply!

---

### Post by Dark_Stang on 2009-10-22
I wouldn't put an OS on an external drive, that would be pretty slow. To repartition you can use gparted within ubuntu, gparted on the Ubuntu live cd, or another stand alone partitioner (if it's Vista or 7 DO NOT USE partition magic). I'd recommend just using a live CD and repartitioning from that. However always back up if possible before repartitioning. You never know when you might lose all your data doing that.

Once the live CD loads go System > Administration > Partition editor. Select your linux partition (or whichever partition you are going to shrink) and just hit resize. Once you get it to the size you want hit okay. You'll see some free space. Select the new free space and hit New. Make the new partition ntfs. Then hit apply. Your partitioner will start doing it's thing. 

After a while it will be done and you can reboot. That while depends on how many files have to be moved. Once it's done reboot and pop your windows disk in. When windows asks where you want to install just choose the ntfs partition and let it go. Windows takes a while...

Once that's done pop the Ubuntu live cd back on and boot from that. Here are directions for that.
[http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/](http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/)

---

### Post by gwilkins82 on 2009-10-22
you, sir, are a gentleman and a scholar.  thanks.  answered everything.  liveCD it is.

---

### Post by emra2emra on 2009-10-22
> **gwilkins82 said:**
> ok. first off, completely satisfied with ubuntu - been a convert for about a year now (looking forward to 10/29!). that said, i want to install windows as well for a dual boot system for a few compatibility issues - espn360, a few other apps as well. to do this, i need to partition my HD. i have downloaded both gparted and the ntfs extension for it, but am still unclear as to how i need to go about doing this. anyone? bueller? thanks for any info!
 
 
 
I can recommend you try out VMware player and install windows inside it.

---

### Post by NCLI on 2009-10-22
Or Virtualbox. It's in the repos.

---

