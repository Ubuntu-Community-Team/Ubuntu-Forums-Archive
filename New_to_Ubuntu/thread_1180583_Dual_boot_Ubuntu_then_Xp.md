---
title: "Dual boot Ubuntu then Xp"
date: 2009-06-07
forum: New to Ubuntu
---

### Post by Duskao on 2009-06-07
Hello,
Right now I have Ubuntu 9.04 and I am extremely happy with it, however there are a few games that I cannot play while using Ubuntu, mostly cause of my Radeon vid card... 
Anywho, I would like to install XP and have a dual boot system. I am going to install XP on a second internal HD and keep my main HD with ubuntu. Now I have read a bit about windows deleting GRUB. Will it still delete GRUB since I am installing it on a separate HD? If so, how can I avoid this? 
I would prefer not to reinstall Ubuntu because I have a fair amount of info on it now that I would not like to loose. 
If I have to I suppose I could just move all my info that I don't want to loose to my second drive then install ubuntu and XP fresh beside each other on the single HD. 
Thanks

---

### Post by easybake on 2009-06-07
It should leave grub alone as long as you install it to the proper hdd during the windows install.

Edit: You will have to edit your /boot/grub/menu.lst file and add a windows entry after you install windows.

---

### Post by QIII on 2009-06-07
If I may make a recommendation . . .

Set up your dual boot on separate physical drives.  It causes a lot fewer problems.

After you install XP on the other drive, you can edit your menu.lst to let you boot to the other drive.

Of course, that depends on what you have on the other drive and how you want to back it up before you mistakenly overwrite anything important by installing Windows.

BTW -- The default timeout is 3 seconds on the GRUB menu.  Edit that line to give yourself 10 or 15 seconds.

---

### Post by -kg- on 2009-06-07
Or alternatively, you can install XP on your second hard drive autonomously, and select which drive you want to boot to in BIOS.  This way, the boot loader for each OS is in the MBR of the hard drive that the OS is on, and you just select the hard drive that you want to boot to, if your BIOS will support it.

---

### Post by Phasmagon on 2009-06-07
Actually you can do whatever you what.
Install on the same hard drive or on different hard drives and then configure grub the way you want. But because installing windows on a machine that has another OS isn't trivia (Windows won't play nice), everything depends on your familiarization with linux. So if you are still on the novice side I would suggest -kg-'s solution (if applicable) but with one more step. While installing windows unplug the linux drive. You never know when windows might decide that it owns the other drive's MBR.

---

### Post by Duskao on 2009-06-07
Very interesting. I'm a little hesitant to go the BIOS way purly because that seems like a bit more of a hassle to be honest. My computer boots quite quickly and I only get about a second or sometimes less to be able to enter BIOS and if that happens I will likely be hard reseting more often then I would like. But it certainly is a good idea and one that i will have to keep in mind. 

I found this site [http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/](http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/)
and I am wondering if that will work. Has anybody tried this before? It seems quite simple.

---

### Post by jbruced on 2009-06-07
> **Duskao said:**
> Very interesting. I'm a little hesitant to go the BIOS way purly because that seems like a bit more of a hassle to be honest. My computer boots quite quickly and I only get about a second or sometimes less to be able to enter BIOS and if that happens I will likely be hard reseting more often then I would like. But it certainly is a good idea and one that i will have to keep in mind. 

I found this site [http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/](http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/)
and I am wondering if that will work. Has anybody tried this before? It seems quite simple.

Yes I used the same process, it worked for me in the past.

I do have Windoze as the first partition though. If you really want to understand grub, go to the supergrub site, more info than you probably want, but he is very thorough.

---

