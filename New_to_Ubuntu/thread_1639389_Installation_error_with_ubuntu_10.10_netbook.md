---
title: "Installation error with ubuntu 10.10 netbook"
date: 2010-12-06
forum: New to Ubuntu
---

### Post by Elgar on 2010-12-06
Hi guys I have this error installing ubuntu-
[http://s142.photobucket.com/albums/r84/Drognar_2006/?action=view&current=ubuntuerror.jpg&newest=1](http://s142.photobucket.com/albums/r84/Drognar_2006/?action=view&current=ubuntuerror.jpg&newest=1)

Anyway I run a dell 1420 laptop with windows 7, Intel Core 2 Dou,prior to using ubuntu, I had jolicloud. I've tried installing ubuntu in just about every way I know(burned cd,wubi, demo on and full installation, inside windows) Someone please help me, I'm trying to install from windows 7. If you need any help just reply. I'm sorry if the photo is poor quality, I took it with my cell phone(Droid Eris)

---

### Post by cariboo on 2010-12-06
That's a normal error if you don't have an [ipv6]("http://en.wikipedia.org/wiki/IPv6") enabled router,most consumer routers don't support ipv6.

Does the installation complete?

---

### Post by Elgar on 2010-12-06
> **cariboo907 said:**
> That's a normal error if you don't have an [ipv6]("http://en.wikipedia.org/wiki/IPv6") enabled router,most consumer routers don't support ipv6.

Does the installation complete?

No, of course not. it just generates a little more text and stays like that.

---

### Post by sikander3786 on 2010-12-06
> **Elgar said:**
> No, of course not. it just generates a little more text and stays like that.
Let us see the text that comes after IPv6 error.

---

### Post by owiknowi on 2010-12-06
You could first try the live CD to see what does and doesn't work on your computer.

Or try to install a default Ubuntu from the alternate installation CD in expert mode (F6, select expert mode, press space and esc and continue).

This way you'll have more options available during installation (example: do not configure network now).

If this works you can install the netbook version from Ubuntu (search forum for how to).

---

### Post by Elgar on 2010-12-06
> **sikander3786 said:**
> Let us see the text that comes after IPv6 error.

I'm trying ubuntu desktop now, currently its capping at 142% installation and not doing anything :(

---

### Post by Elgar on 2010-12-07
Well using an ethernet cable gets it to 571%, still no progress into the installation. Good night people, I'll probably check this thread in the morning so please do reply if you can help

---

### Post by sikander3786 on 2010-12-07
> Well using an ethernet cable gets it to 571%

?? 571%? Where does that show up. I think installation should complete at 100% :confused:

I would recommend to check the downloaded image for defects.

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

If ok, check your disc for defects. Gain access to the Boot Menu by pressing any key as soon as the computer starts booting from disc and select "Check disc for defects".

[https://help.ubuntu.com/community/LiveCDBootOptions](https://help.ubuntu.com/community/LiveCDBootOptions)

If you need to burn a new disc, burn it at the lowest possible speed (4x recommended).

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

You can also use a USB drive to boot from and install Ubuntu ;-)

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

[http://unetbootin.sourceforge.net](http://unetbootin.sourceforge.net)

---

### Post by Elgar on 2010-12-07
> **sikander3786 said:**
> ?? 571%? Where does that show up. I think installation should complete at 100% :confused:

I would recommend to check the downloaded image for defects.

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

If ok, check your disc for defects. Gain access to the Boot Menu by pressing any key as soon as the computer starts booting from disc and select "Check disc for defects".

[https://help.ubuntu.com/community/LiveCDBootOptions](https://help.ubuntu.com/community/LiveCDBootOptions)

If you need to burn a new disc, burn it at the lowest possible speed (4x recommended).

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

You can also use a USB drive to boot from and install Ubuntu ;-)

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

[http://unetbootin.sourceforge.net](http://unetbootin.sourceforge.net)
I think the file for ubuntu desktop was only about 1.40 MB so its kinda hard for that to be a corrupt file. Also, I'm using windows, how to do I run this stuff?

---

### Post by sikander3786 on 2010-12-07
> **Elgar said:**
> I think the file for ubuntu desktop was only about 1.40 MB so its kinda hard for that to be a corrupt file. Also, I'm using windows, how to do I run this stuff?
1.40 MB? How can that contain a complete OS?

It should be around 680 MB - 700 MB.

Where did you download that? Grab one here.

[http://www.ubuntu.com/netbook](http://www.ubuntu.com/netbook)

---

### Post by Elgar on 2010-12-07
> **sikander3786 said:**
> 1.40 MB? How can that contain a complete OS?

It should be around 680 MB - 700 MB.

Where did you download that? Grab one here.

[http://www.ubuntu.com/netbook](http://www.ubuntu.com/netbook)

ok first off, I'm trying the desktop version now. second off, the link for that same file is windows edition desktop ubuntu, link here-http://www.ubuntu.com/desktop/get-ubuntu/windows-installer
and here is the latest from using the official(non-windows,universal installer)-http://i1115.photobucket.com/albums/k547/Keith_Limoli/ubuntuerror.jpg, its been stuck like that for about 20 minutes with no sign of progress
Oh and enjoy :popcorn:

---

### Post by sikander3786 on 2010-12-07
First of all I would want to know, how do you plan to install Ubuntu? Inside Windows using Wubi installer or in true dual boot to Windows with Ubuntu on its own separate partition?

---

### Post by Elgar on 2010-12-07
> **sikander3786 said:**
> First of all I would want to know, how do you plan to install Ubuntu? Inside Windows using Wubi installer or in true dual boot to Windows with Ubuntu on its own separate partition?

Well whichever way is easiest and fast :) Now when, ubuntu runs and tell you can test it after a reboot and install it from inside ubuntu, my experience is usually that windows doesnt even regonize that, it just restarts the computer and adds nothing. I guess I would prefer to get the off cd version working. I mean big the 690ish mb file is preferable.

---

### Post by sikander3786 on 2010-12-07
Ok. Download the complete ISO (which you are doing right now ? ) and burn it to disc.

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

Or burn to a USB.

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

[http://unetbootin.sourceforge.net](http://unetbootin.sourceforge.net)

Configure you Bios to boot from USB or CD and Try Ubuntu. Test all your hardware and also post the output of this command from Applications > Accessories > Terminal.

```
sudo fdisk -lu
```

---

### Post by Elgar on 2010-12-07
> **sikander3786 said:**
> Ok. Download the complete ISO (which you are doing right now ? ) and burn it to disc.

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

Or burn to a USB.

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

[http://unetbootin.sourceforge.net](http://unetbootin.sourceforge.net)

Configure you Bios to boot from USB or CD and Try Ubuntu. Test all your hardware and also post the output of this command from Applications > Accessories > Terminal.

```
sudo fdisk -lu
```
Ok, your really confusing me here, what file,what bios?

---

### Post by sikander3786 on 2010-12-08
> **Elgar said:**
> Ok, your really confusing me here, what file,what bios?
There are more than 1 methods of installing Ubuntu. Thats why I asked you in [post # 12.]("http://ubuntuforums.org/showpost.php?p=10211189&postcount=12")

Wubi installer installs Ubuntu inside Windows just as you'd have installed a Windows program by running a .exe file. It creates a virtual HDD on your Windows partition for Ubuntu which just shows like a folder. It is easier because you don't need to touch your partitions or create new partitions for Ubuntu. Wubi installer does everything for you. But it is just intended for testing Ubuntu. Not a long-term solution as it is a bit slower and a bit less stable than a complete install.

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

The proper method is to install Ubuntu by booting from an Ubuntu CD/USB just as you do when you install Windows. You need to create/assign at least two partitions for Ubuntu then. 1. Ubuntu Root Partition (Just like Windows C: drive). 2. Swap partition.

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

And for booting from Ubuntu CD or USB, you need to make CD Drive or your USB Drive, first boot device under your Bios menu. Refer to your manufacturer's documentation for more details.

So you first need to decide how are you going to install Ubuntu ;-)

---

### Post by Elgar on 2010-12-08
> **sikander3786 said:**
> There are more than 1 methods of installing Ubuntu. Thats why I asked you in [post # 12.]("http://ubuntuforums.org/showpost.php?p=10211189&postcount=12")

Wubi installer installs Ubuntu inside Windows just as you'd have installed a Windows program by running a .exe file. It creates a virtual HDD on your Windows partition for Ubuntu which just shows like a folder. It is easier because you don't need to touch your partitions or create new partitions for Ubuntu. Wubi installer does everything for you. But it is just intended for testing Ubuntu. Not a long-term solution as it is a bit slower and a bit less stable than a complete install.

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

The proper method is to install Ubuntu by booting from an Ubuntu CD/USB just as you do when you install Windows. You need to create/assign at least two partitions for Ubuntu then. 1. Ubuntu Root Partition (Just like Windows C: drive). 2. Swap partition.

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

And for booting from Ubuntu CD or USB, you need to make CD Drive or your USB Drive, first boot device under your Bios menu. Refer to your manufacturer's documentation for more details.

So you first need to decide how are you going to install Ubuntu ;-)

Well I'd rather do the wubi method if I could get it to work :) Wubi sounds a lot easier lol. If I have to do the other method though the steps should look like this-
1.Burn ubuntu installer to CD/DVD
2.Installing that Partiationing program run that.
3.Bios menu, that still confuses me and I dont really understand why the manufactor would mean anything there.

Anyway try to get me setup up using wubi.

---

### Post by sikander3786 on 2010-12-08
> **Elgar said:**
> Well I'd rather do the wubi method if I could get it to work :) Wubi sounds a lot easier lol. If I have to do the other method though the steps should look like this-
1.Burn ubuntu installer to CD/DVD
2.Installing that Partiationing program run that.
3.Bios menu, that still confuses me and I dont really understand why the manufactor would mean anything there.

Anyway try to get me setup up using wubi.
Just follow the Wubi guide linked in my above post. It is very easy to setup Wubi.

After the intallation is successful, in order to make your Wubi install a bit stable, follow the steps under **Permanent Fix** portion in this guide.

courtesy of forum member **Rubi1200**

[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

---

### Post by Elgar on 2010-12-08
> **sikander3786 said:**
> Just follow the Wubi guide linked in my above post. It is very easy to setup Wubi.

After the intallation is successful, in order to make your Wubi install a bit stable, follow the steps under **Permanent Fix** portion in this guide.

courtesy of forum member **Rubi1200**

[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

Hey, I noticed this earlier and its been bothering me for a long time, I did that checksum test and never got matching checksums, I tried redownloading different ways still never the same, I dont know why and I've got four copys of wubi that all dont match the ones on that site.

---

### Post by sikander3786 on 2010-12-08
Try using bittorent, links on the same Ubuntu home-page.

---

### Post by Elgar on 2010-12-08
> **sikander3786 said:**
> Try using bittorent, links on the same Ubuntu home-page.

tried getting ubuntu 10.10 desktop torrent, I wound up with this-http://i1115.photobucket.com/albums/k547/Keith_Limoli/ubun.jpg frozen for too long to be working.

I've gotten there before but only by closing in the install thing out and typing in ubuntu and no password, either way the result is the same. I also have an embarrasing mouse issue with ubuntu :P

---

### Post by sikander3786 on 2010-12-08
> **Elgar said:**
> tried getting ubuntu 10.10 desktop torrent, I wound up with this-http://i1115.photobucket.com/albums/k547/Keith_Limoli/ubun.jpg frozen for too long to be working.

I've gotten there before but only by closing in the install thing out and typing in ubuntu and no password, either way the result is the same. I also have an embarrasing mouse issue with ubuntu :P
Seems like your machine doesn't like Linux.

Please sum it up once again. You downloaded a new ISO of Ubuntu. Did you check the MD5SUM? Did you burn the disc at lowest speed? Did you check the disk for defects?

What happens when you boot from that disc? Where does it get stuck? Any errors?

---

### Post by Elgar on 2010-12-08
> **sikander3786 said:**
> Seems like your machine doesn't like Linux.

Please sum it up once again. You downloaded a new ISO of Ubuntu. Did you check the MD5SUM? Did you burn the disc at lowest speed? Did you check the disk for defects?

What happens when you boot from that disc? Where does it get stuck? Any errors?

I downloaded a new bittorent file of Ubuntu desktop 10.10, I went in the demo and full installation mode and even created a Help Booter, then I restarted selected Ubuntu from the boot and it dragged me straight into Ubuntu's desktop as soon as everything finished loading, I double clicked the install Ubuntu thing and it froze, but I could still toy around with Ubuntu, I forgot to run the checksum test. I'm concerned though that even if Ubuntu works I won't be able to click anything.

---

