---
title: "Wireless issues (No wireless firmware)"
date: 2011-06-15
forum: New to Ubuntu
---

### Post by M1k3y on 2011-06-15
I am new to ubuntu and so far I really like linux (over windows which SUCKS). I installed it using the wubi installer (I also have windows xp). The first time I booted it up I went to connect to a wireless network and no networks were up. Then I clicked on the wireless thing again and realized it said no wireless firmware. I have scoured the internet and found issues similar to mine but nobody has the same exact wireless card (Broadcom BCM 4312 802.11g/b, I figured this out by running recover and then the shell, after that I typed in the command: lspci -v | less).
Please help me
-M1k3y

---

### Post by StrayEddy on 2011-06-15
Should be what you need:

[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

---

### Post by mikewhatever on 2011-06-15
For BCM 4312 802.11g/b, all there is to do is plug in a cable and wait for a popup prompting to install the driver.
I nothing happens, search for bcmwl-kernel-source and install it.

---

### Post by M1k3y on 2011-06-15
> **StrayEddy said:**
> Should be what you need:

[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)


Thanks so much.

---

### Post by M1k3y on 2011-06-15
Still having issues. I didnt install it because I have no idea how to. I dont know where to put the files or the commands. I also did a bit of searching and underneath ubuntu help they had a section for this. I went into the terminal and it turns out that the adapter isnt disabled. But the wireless is. Thats literally what it said. Please help.
-M1k3y

---

### Post by gandaran on 2011-06-15
> **M1k3y said:**
> Still having issues. I didnt install it because I have no idea how to. I dont know where to put the files or the commands. I also did a bit of searching and underneath ubuntu help they had a section for this. I went into the terminal and it turns out that the adapter isnt disabled. But the wireless is. Thats literally what it said. Please help.
-M1k3y
you just need to connect to cable internet and update the software package list then look in additional drivers to activate the broadcom driver, it's all very easy to get the driver working from ubuntu repositories, no need to download and install drivers manually.

---

### Post by M1k3y on 2011-06-15
I have already tried that. I plug directly into my modem and I get internet access for like 30 seconds then it disconnects me. I have no idea why. I tried connecting to the modem different ways. I tried resetting the modem, nothing has worked. The only way is manually I just need directions.

---

### Post by mikewhatever on 2011-06-15
According to the [README.txt]("http://www.broadcom.com/docs/linux_sta/README.txt") you have to compile the driver, which you won't be able to do without the build-essential package. Quite honestly, I don't know why that link was posted, perhaps you should PM StrayEddy and ask.
Anyway, back to the problem, since your wired connection doesn't work either, the only practical option is to use the installation CD.
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#STA%20-%20No%20Internet%20access](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#STA%20-%20No%20Internet%20access)

---

### Post by M1k3y on 2011-06-15
Thanks

---

### Post by wep940 on 2011-06-15
+1 on the CD - the build-essential package is on the LiveCD in the /pool/main folder tree - it might be the "b" folder in that tree, but I don't remember right off the top of my head.  Do you have an ethernet port on the PC that you could temporarily hard wire to your router?  If so, I would do that rather than trying to connect with a modem.  Then just do the following:

- sudo apt-get update

- go to system/administration/additional drivers - this will run for a while and search for a driver.  When it finds it it will download it, then it will show in the window.  Just be sure to activate it - just because it shows in the window doesn't mean the driver has been enabled.

---

### Post by M1k3y on 2011-06-15
would a USB stick with the 11.04 32 bit burned to it be the equivalent of a live cd?

---

### Post by wep940 on 2011-06-15
Should be - plug it in and then explore it to see if you see the folder /pool - if so, go to the /pool/main/b folder (I think that's where build-essential is).  If I remember correctly, the bcmwhatever kernel source is in the same folder as build-essential.

---

### Post by M1k3y on 2011-06-15
Hey I got another problem.
I downloaded the 32 bit installer and put onto my 16 gig flash drive then extracted it with winrar. I got /pool/main/d/dkms, and /pool/restricted/b/bcmwl, and the one that the other guy said pool/main/d/dkms. But pool/main/p/patch and pool/main/f/fakeroot. This is driving me crazy. I cant connect to the internet on my laptop for the driver update on ubuntu and I cant find the pool/main/p/patch or pool/main/f/fakeroot online. Please help. Thanks
-M1k3y

---

### Post by M1k3y on 2011-06-15
I downloaded the two off of here:
[https://ftp.in.kernel.org/ubuntu/pool/main/f/fakeroot/](https://ftp.in.kernel.org/ubuntu/pool/main/f/fakeroot/)
fakeroot 1.16.orig.tar.bz2
and
[https://ftp.in.kernel.org/ubuntu/pool/main/p/patch/](https://ftp.in.kernel.org/ubuntu/pool/main/p/patch/)
[]("https://ftp.in.kernel.org/ubuntu/pool/main/p/patch/patch_2.5.9-2.diff.gz")patch 2.4.9-2.diff.gz
Are these still good?

---

### Post by M1k3y on 2011-06-15
Nevermind they are no good. I dont know how to use them. Can you please help me. I downloaded the ubuntu 11.04 installer (32 bit) and it was missing /pool/main/p/patch and poo/main/f/fakeroot. I need these 2 files. Please help
-m1k3y

---

### Post by garvinrick4 on 2011-06-15
There is a package installer called Synaptics pre installed in Ubuntu. You need
2 of the packages for broadcom 4312 card.
bcmwl-kernel-source
b43-fwcutter
Open Synaptics type "bcm in" upper right search box.
check mark the two packages, right click and choose install hit apply arrow.
reboot machine. 
*Make sure nothing else installed in bcm group if so uninstall them before rebooting.

Wire your wired connection from router to laptop to get the wired connection working
so these packages will download.

---

### Post by garvinrick4 on 2011-06-15
Forgot to give you screenshot click on thumbnail.

---

### Post by mikewhatever on 2011-06-16
> **M1k3y said:**
> Nevermind they are no good. I dont know how to use them. Can you please help me. I downloaded the ubuntu 11.04 installer (32 bit) and it was missing /pool/main/p/patch and poo/main/f/fakeroot. I need these 2 files. Please help
-m1k3y

Hm..., if those files aren't on the installation media, perhaps they aren't needed. Anyway, you can download them using the links below.
patch -> [http://packages.ubuntu.com/natty/i386/patch/download](http://packages.ubuntu.com/natty/i386/patch/download)
fakeroot -> [http://packages.ubuntu.com/natty/i386/fakeroot/download](http://packages.ubuntu.com/natty/i386/fakeroot/download)

---

### Post by dFlyer on 2011-06-16
> **mikewhatever said:**
> For BCM 4312 802.11g/b, all there is to do is plug in a cable and wait for a popup prompting to install the driver.
I nothing happens, search for bcmwl-kernel-source and install it.

Start synaptic package manager. Under filter enter bcmwl-kernal-source. If it's marked as installed, right click it and mark it for reinstall. Click apply and restart ubuntu.

---

### Post by sompo on 2011-06-16
actually i am very new to this thread but i want to share something that maybe someone can help to resolve it.  Every time i format my laptop i have to find another driver to install wireless drive even i have given full drive setup for my laptop....it seem like the giver wireless driver not compatible with my laptop anymore.

---

### Post by wildmanne39 on 2011-06-16
> **sompo said:**
> actually i am very new to this thread but i want to share something that maybe someone can help to resolve it.  Every time i format my laptop i have to find another driver to install wireless drive even i have given full drive setup for my laptop....it seem like the giver wireless driver not compatible with my laptop anymore.Hi, thats normal if you reinstall you have to reinstall the drivers too, because it is against the law for linux to include them in ubuntu installion.

---

### Post by M1k3y on 2011-06-16
Instead of fooling around with those files I installed Ubuntu with a USB and deleted my windows partition (I was going to do it eventually). Then during installation I turned my wireless on. Rebooted and the additional drivers windows popped up. It asked me to enable the driver. I rebooted after that and it worked. But thanks for all of the help.
-M1k3y

---

### Post by wep940 on 2011-06-16
Glad you got that going.  I know you said your only other network connection was via a modem, so I was trying to stay away from the download path and let you install the packages from the LiveCD.  But......since you got it figured out it doesn't matter anymore anyway!
 
Congrats on getting this going!
 
Enjoy ;)

---

### Post by M1k3y on 2011-06-16
Thanks
:D
-m1k3y

---

