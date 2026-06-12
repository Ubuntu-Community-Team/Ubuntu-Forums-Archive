---
title: "Samsung NC10 dual boot?"
date: 2008-12-08
forum: New to Ubuntu
---

### Post by Luomeng on 2008-12-08
I'm getting a Samsung NC10 for Christmas, and was thinking of installing Ubuntu on it. This will be my first foray into Linux and I wanted to keep the XP it came with just in case i didn't like it or it didn't work like I wanted it to. I plan on upgrading it to 2gb of ram. So my question is how do I dualboot XP and Ubuntu on the Samsung and is 2 gb of memory enough to dualboot it? I've read this guide 
[https://help.ubuntu.com/community/NC10#External%20Links](https://help.ubuntu.com/community/NC10#External%20Links)
but it doesn't tell me how to dual boot it. Help would be greatly appreciated

---

### Post by Jon Bradbury on 2008-12-09
Try looking further up the page.

If you have an external USB cd drive, you can install Ubuntu as per a normal PC. Otherwise, you need to use a USB pendrive (memory stick thingie) and boot off that.

The NC10 already has two partitions, the XP partition and a recovery partition. I deleted all of them, installed XP from the CD that came with the NC10 then ran the Ubuntu 8.10 livecd. Clearly it's just a case of clicking "Install Ubuntu" on the live cd's desktop and going through the normal Ubuntu install procedure.

If you don't have a USB cd drive, I recommend you get one, as it is much easier than playing around with pendrives.

See also this forum : [http://nc10ubuntu.forumcircle.com/](http://nc10ubuntu.forumcircle.com/)
..and the corresponding blog : [http://nc10ubuntu.wordpress.com/](http://nc10ubuntu.wordpress.com/)

They are all from the same people.

---

### Post by nmg196 on 2008-12-09
Hi,
I'm totally new to Ubuntu and haven't used linux in a few years. I wanted try Ubuntu on the NC10, but looking at some videos (eg [http://www.vimeo.com/2259823](http://www.vimeo.com/2259823)) it seems it's REALLY slow to boot - far slower than Windows XP for example. Is this really right? I'd always been told Linux generally boots faster than Windows, but so far, the 2-3 videos I've seen show exactly the opposite.

Thanks,
Nick

---

### Post by Luomeng on 2008-12-11
Okay, I think I know how to dual boot it, but is 2GB ram enough for a dual boot? I thought I read somewhere that you have to have enough ram to dual boot...

---

### Post by halitech on 2008-12-11
as long as you have the minimal amount of ram that is required for the OS, thats all you need.

---

### Post by Duck2006 on 2008-12-11
> but is 2GB ram enough for a dual boot

Yes, more than enough.

---

### Post by ugm6hr on 2008-12-11
> **Luomeng said:**
> Okay, I think I know how to dual boot it, but is 2GB ram enough for a dual boot? I thought I read somewhere that you have to have enough ram to dual boot...

The amount of RAM is independent of dual-booting.  Dual-booting means that there is one OS running at any one time.

And 2GB is loads for Ubuntu (more than me).

---

### Post by Luomeng on 2008-12-11
Okay, thanks. One last question, for the fixes that I must do to make Ubuntu work better on the NC10, do I have to change anything I do because Im dual booting it?

Btw, the instructions I'm talking about are here 
[https://help.ubuntu.com/community/NC10#Wireless%20Networking%20-%20Atheros](https://help.ubuntu.com/community/NC10#Wireless%20Networking%20-%20Atheros)

---

### Post by ugm6hr on 2008-12-11
> **Luomeng said:**
> Okay, thanks. One last question, for the fixes that I must do to make Ubuntu work better on the NC10, do I have to change anything I do because Im dual booting it?

No.

---

### Post by halitech on 2008-12-11
> **Luomeng said:**
> Okay, thanks. One last question, for the fixes that I must do to make Ubuntu work better on the NC10, do I have to change anything I do because Im dual booting it?

Btw, the instructions I'm talking about are here 
[https://help.ubuntu.com/community/NC10#Wireless%20Networking%20-%20Atheros](https://help.ubuntu.com/community/NC10#Wireless%20Networking%20-%20Atheros)

for all intents and purposes, other then during the first few moments of the boot when you have to select if you want windows or ubuntu, its basically as if you only have 1 OS on your system.

---

### Post by Luomeng on 2008-12-11
okay thank you all

---

### Post by XopherH on 2008-12-18
I had a dual-boot working within the first hour.

Upon initial Startup and config, the samsung restore thingy asked which size to make the drives, I selected 30GB for XP(C: ) and then I left the rest, minus the 6gb restore partition for D: which it where Ubuntu would go.  I then let the restore maker do its job.

So then, to create the USB boot drive, this worked flawlessly, [http://www.pendrivelinux.com/2008/10/06/usb-ubuntu-810-install-from-windows-non-persistent/](http://www.pendrivelinux.com/2008/10/06/usb-ubuntu-810-install-from-windows-non-persistent/)

Then, its like any other Ubuntu install procedure, I then turned that original D: in windows into a 80gb media partition.  So ubuntu got 3 logical partitions for swap, root, and home totaling about 40gb at the end of the hard drive.

Then you will need 4 downloaded packages to get Wireless to work, all of which should just be added to the USB boot drive after its made and copied over to the ubuntu desktop after install:
#1 linux-image-2.6.27-9-generic_2.6.27-9.19_i386.deb
#2 linux-backports-modules-2.6.27-9-generic_2.6.27-9.5_i386.deb
#3 linux-backports-modules-intrepid-generic_2.6.27.9.13_i386.deb
#4 linux-backports-modules-intrepid_2.6.27.9.13_i386.deb

Each package above must be installed for the package below it to install, so follow the order.

Then you have to blacklist the old drivers.
```
sudo su
echo "blacklist ath_pci" >> /etc/modprobe.d/blacklist
echo "blacklist ath_hal" >> /etc/modprobe.d/blacklist
```

A restart or two should then get an enabled wireless card upon boot.

---

