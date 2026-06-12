---
title: "I cannot start Ubuntu 9.10 from HD after install"
date: 2009-11-10
forum: New to Ubuntu
---

### Post by Automat2 on 2009-11-10
I installed the new Ubuntu 9.10 on a dual boot basis from the install CD. It made the partition to the HD, downloaded the OS and so and finally entered the config options.
 
After that, I rebooted my PC and on the option screen, selected to load Ubuntu 9.10 "normal mode".
 
My surprise is that the first black screen asks me for my password. Trying to enter that is rather difficult, because the screen seems to "open and close" several times per second. I can just make it with my username, but it's impossible to type the password properly -you can't see the characters, therefore I don't know whether the  PC has recognized me typing the character or not.
 
After 60 seconds, a message to start again appears on the screen saying that I have to restart the process.
 
If I tried to load the "secure mode", the same old black screen appears but this one doesn't freeze, so I am able to log on. However, it only loads the "Terminal" and I don't know whether I can log on to the Desktop, or even if you are meant to do so.
 
Does anybody can help me?

---

### Post by Bunnybugs on 2009-11-10
Something went wrong at the install of Ubuntu (had the same trouble with karmic)

Just re-install Ubuntu on the partition you've created for ubuntu

Or, try to load the revovery mode in the Grub screen!

---

### Post by ukripper on 2009-11-10
Does it happens same when you boot from your ubuntu 9.10 cd?

---

### Post by Automat2 on 2009-11-10
> **ukripper said:**
> Does it happens same when you boot from your ubuntu 9.10 cd?
 
I haven't tried since I intalled 9.10 to the HD, but I'll try. It had never happened before either from the Kubuntu 9.04 nor Ubuntu 9.10, both from the live CD.

---

### Post by philinux on 2009-11-10
Choose the second option from grub - recovery mode.

You should end up at a menu. Then select resume normal boot.

If you just end up with the terminal. Use your username and password to login. Then type startx. See if the desktop will load.

---

### Post by Automat2 on 2009-11-10
I think I'll try to re-install. But, is there an option to "re-install" Ubuntu? Will the installer recognize that I have already created a partition for Ubuntu and write the new one on there being the same version?

---

### Post by oldfred on 2009-11-10
As long as you know your partitions you can use manual install. You manually choose root, swap and if /home is different you can choose that also.

I had created several new partitions on a new drive and I had one partition named data and the other test. Of course since I had lots of partitions I installed my test version into data. Since they were new partitions I did no lose anything but be sure of which partition is which.

---

### Post by Automat2 on 2009-11-10
> **philinux said:**
> Choose the second option from grub - recovery mode.

You should end up at a menu. Then select resume normal boot.

If you just end up with the terminal. Use your username and password to login. Then type startx. See if the desktop will load.

I've tried it, and there is an error and doesn't load the Desktop.

---

### Post by philinux on 2009-11-10
Boot your livecd and choose "Check CD for Defects".

---

### Post by Automat2 on 2009-11-10
Well, I finally got Ubuntu 9.10 installed and running well, so far.

I suppose the bug appeared when I tried to install Windows folders -Root and Documents-, to Ubuntu. After a couple of tentatives, I left those two boxes unticked, and here I am!

Thanks to all those who have tried to help me! ;)

---

