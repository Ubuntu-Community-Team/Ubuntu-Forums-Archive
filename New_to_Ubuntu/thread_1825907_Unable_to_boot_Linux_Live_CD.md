---
title: "Unable to boot Linux Live CD"
date: 2011-08-15
forum: New to Ubuntu
---

### Post by emmerthalc on 2011-08-15
I have run into a problem. Yesterday I installed Ubuntu to begin exploring, I think it was Ubuntu 10.4, it was downloaded it a few weeks back, but I never got around to doing anything with it.) In any event I ran into a problem almost immediately. I was unable to connect to my wireless network. After some research and experimentation with ndiswrapper I decided to start over. So I put back in the Live CD to reinstall. However while booting to the CD it is now hanging at the load screen. It sits there and looks like it is loading for 5-10 minutes then turns black. I burned a new CD thinking that the CD I installed from previously may have become corrupted, but still no luck. A little more research led me to download a gparted .iso and I using this tool I deleted the partitions that once held my Ubuntu installation. (I left all other partitions intact.) Now I am still unable to boot to the CD and am getting the grub rescue screen so now I am also not able to boot to Windows. Any ideas? I did back up all important information from Windows, so if I have to scrap everything I can, but I really do not want to do that. There is some software I would lose without any hope of recovering if that happens. 

Also, while booting to the Live CD I am able to get to the menu screen that gives the options to Try Ubuntu Without Installing, Install Ubuntu, Check Disk for Defects, etc. . From this point both the Try Ubuntu WIthout Installing and Install Ubuntu Options hang.


Sorry I can't give more information. Not sure what I should\can give at this point.

---

### Post by HarrisonNapper on 2011-08-26
Sorry about the delay. In the case you have not already figured it out, would recommend downloading and creating a new Live CD. If it still doesn't work, check the integrity of the disk at the startup menu. If you still have problems with it, post here so we can troubleshoot it more to determine whether ndiswrapper is necessary for the card.

---

### Post by emmerthalc on 2011-09-08
Thanks for the reply, and sorry about my delay as well. I am going to try to download and install again. I have downloaded both the text based alternate as well as the new Live CD. I don't think I need the text based installer since the last time I installed, the Live CD worked just fine, but I figured I would give it a try anyway. My problem now is trying to find a computer that I can use to burn them to a CD. That was my only computer with a burner. Never needed another because I always had that one. Thank you again for the reply. I will let you know how it goes.

---

### Post by corncob on 2011-09-08
If your computer can boot from a USB stick try that.  Instructions are at
[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)
In step 2 uncheck CD and check USB stick and click on Show me how.
Hope this helps.

---

### Post by I2k4 on 2011-09-08
> **corncob said:**
> If your computer can boot from a USB stick try that.  Instructions are at
[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)
In step 2 uncheck CD and check USB stick and click on Show me how.
Hope this helps.

Agree entirely with this, and more so, if you can set BIOS to USB priority and use Live USB, look at the PenDrive installer when you run it, and set Persistence to at least half the USB size. (Persistence will save your settings and installations between boots.  Just run from USB for a while to see if everything on your computer works with Ubuntu. It's only a little slower and there's no risk of hard drive muck ups.  (Some older PCs won't boot from USB and then you need to use the CD method.)

---

### Post by emmerthalc on 2011-09-10
I have downloaded and burned the iso to a new CD following the procedures outlined in your link. When trying to boot to the CD I am getting an error. 

Kernel Panic - not syncing: VFS: Unable to mount root fs on unknown-block(8,1)

There is much more. Let me know if you need to see it.

I am going to try the alternate CD. Will let you know if it works.

Would have used the USB, but just don't have one on me at this time. Left them all at the office.

---

### Post by nm_geo on 2011-09-10
> and am getting the grub rescue screen so now I am also not able to boot to Windows. Any ideas?

You could recover the MBR from a Windows recovery disk and then go from there. It would help with the preparation of the live CD or USB too. When you delete the Ubuntu installed partition grub had still changed the MBR..

---

### Post by emmerthalc on 2011-09-11
Thanks. I was able to get Ubuntu installed off the alternate CD that I downloaded. Not sure why I was able to run the Live CD earlier, but when I removed my previous installation it now longer worked. I tried every way I could think of to install off any of the Live CDs I created. Just out of curiosity, any idea why it would work when I first installed it, but didn't work after removing? 

I still don't have wireless, but I will continue messing around with it until I find a solution. I did find a that the Broadcom STA Wireless Driver has been activated and is in use, but still it doesn't appear to be able to discover any wireless broadcasts. In any event , thanks for all of your help.

---

### Post by emmerthalc on 2011-09-11
Well I now have wireless. I have no idea how I did it, but its now there. I was just messing around and viola I had wireless. Really wish I knew how I did it, so I could replicate. Guess I'll have the opportunity to figure it out again as I will inevitably need to reinstall. On that note, I am very interested in learning more about this OS. Does anyone know where I could or should start? 

Thank you all for the help you have offered me.

---

### Post by corncob on 2011-09-11
> **emmerthalc said:**
>  I am very interested in learning more about this OS. Does anyone know where I could or should start? 

[http://ubuntuforums.org/showthread.php?t=801404](http://ubuntuforums.org/showthread.php?t=801404)

---

