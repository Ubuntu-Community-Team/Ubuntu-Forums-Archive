---
title: "Ubuntu Disk Not Working"
date: 2010-10-25
forum: New to Ubuntu
---

### Post by ShadowVegan on 2010-10-25
I made two Ubuntu CDs (10.10, 32 and 64 bit versions) a few hours ago. I've never installed Ubuntu before. I have my BIOS set to boot from CD, and at first it seems to work fine. It will show the purple Ubuntu color scheme and it will get to the loading screen with the Ubuntu logo and alternating red/white dots. However, it freezes at this point and never gets past the loading screen. This goes for both disks, and I've tried booting from the CD as well as installing from the CD. The same thing always happens. I want to first boot Ubuntu from the disk to delete the Vista partition, then install Ubuntu. How do I get my computer to boot  from the CD and stop freezing at this point? Or do I just need to wait a really long time? (I've waited a lot longer than it should take an OS to boot.) Thanks.

---

### Post by NickJones on 2010-10-25
Try a "WUBI" install, boot into Windows, and pop in the CD, the autorun should take it from there and give you the option to perform a Wubi install, this allows you to install Ubuntu from within Windows and you don't risk accidentally deleting partitions when playing around with partition manger.
You can find more info on Wubi [http://www.ubuntu.com/desktop/get-ubuntu/windows-installer](http://www.ubuntu.com/desktop/get-ubuntu/windows-installer)
Cheers,
Nick

---

### Post by tajiknomi on 2010-10-25
[SIZE=2][I]Looks like image(Ubuntu) have some error or you may have burn ur disk Not correct....

try this...

i you have memory stick...make a disk (Create-startup) disk from that image...and check then...if you got the same problem then it must be image problem....
[/I][/SIZE]

---

### Post by anewguy on 2010-10-25
> **NickJones said:**
> Try a "WUBI" install, boot into Windows, and pop in the CD, the autorun should take it from there and give you the option to perform a Wubi install, this allows you to install Ubuntu from within Windows and you don't risk accidentally deleting partitions when playing around with partition manger.
You can find more info on Wubi [http://www.ubuntu.com/desktop/get-ubuntu/windows-installer](http://www.ubuntu.com/desktop/get-ubuntu/windows-installer)
Cheers,
Nick

Note the OP wants to get rid of his Vista partition(s).

It would help if we could know what brand/model of PC we're dealing with here, including such things as the video adapter.  We may be able to give you instructions (such as nomodeset on the boot line) to get you around the problems.  But there are several "depends" here - such as the CPU, video adapter, amount of memory, etc..  That's why we need as much info as you can give us, as it's possible your hardware won't support the GUI install.  If you want, you could try downloading and burning the alternate CD and see if you have better luck with it.  It seems to require less resources the the GUI'd version.

First, though, as already noted, you should really run the md5sum against your download and check it to the original.  Then, try burning at the slowest speed your drive allows (don't ask me why, outside of perhaps a cleaner burn if the drive isn't new, but this is recommended a lot on the forum regarding install CD problems).

Dave ;)

---

### Post by Mark Phelps on 2010-10-25
Just to save you some grief ... I would strongly advise AGAINST Wubi installation of 10.10 at this time.  The latest Release Notes indicate there are STILL problems with Wubi installs.  No point in asking for trouble.

---

### Post by anewguy on 2010-10-25
As Mark Phelps said, wubi just isn't a good idea.  It is at most a way of trying ubuntu without messing with partitions, only a little step better than just running off the LiveCD.  If you check the forum, you will see a lot of problems with people using wubi.  Your best bet is a straight install of ubuntu.  

If you have a way of providing the information requested, we can help you get there.

Dave ;)

---

### Post by ShadowVegan on 2010-10-25
Thanks for the replies. I don't want to do the Wubi install because, as I understand it, I wouldn't be able to remove Vista. My specs are:
Asus G50 VT
286GB HDD (235 free)
4GB RAM
2.13GHz Intel Core2 Duo CPU

How do I find out what video adapter I have? I have Nvidia graphics if that means anything.

If any other specs are needed let me know.

Edit: Taking Anewguy's suggestion, I made another CD and the slowest available burning speed (x10) and it's working. I'm on Ubuntu now. Still took a while to load, but at least its working. I haven't installed yet, running from the disk now, but it seems to be working fine. Thanks for all the suggestions.

---

