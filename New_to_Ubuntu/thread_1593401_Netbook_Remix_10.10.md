---
title: "Netbook Remix 10.10"
date: 2010-10-11
forum: New to Ubuntu
---

### Post by Cfmarq on 2010-10-11
Hi fellas.. I'm new at Ubuntu Forums but not too new at Ubuntu OS.
I'm trying to install ubuntu netbook remix at my toshiba nb305 and I'm not beeing able to do it. I'ved created an usb drive as usually, it worked perfecty on 10.04 but not this time. 

I'ved formatted the usb drive and created as new several times with different software. In Universal Usb Installer does not appear any Ubuntu Netbook Remix 10.10 option. 
So I've tryed usb creator that comes with ubuntu software and fedora's usb creator. 
This time when I boot my pc with usb drive appears **"SYSLINUX 3.82 2009-06-09 EBIOS Copyright (C) 1994-2009 H. Peter Anvin et al"** and then freezes.

Can I get some help please? :-?



(sorry about my poor english)

---

### Post by sandyd on 2010-10-11
> **Cfmarq said:**
> Hi fellas.. I'm new at Ubuntu Forums but not too new at Ubuntu OS.
I'm trying to install ubuntu netbook remix at my toshiba nb305 and I'm not beeing able to do it. I'ved created an usb drive as usually, it worked perfecty on 10.04 but not this time. 

I'ved formatted the usb drive and created as new several times with different software. In Universal Usb Installer does not appear any Ubuntu Netbook Remix 10.10 option. 
So I've tryed usb creator that comes with ubuntu software and fedora's usb creator. 
This time when I boot my pc with usb drive appears **"SYSLINUX 3.82 2009-06-09 EBIOS Copyright (C) 1994-2009 H. Peter Anvin et al"** and then freezes.

Can I get some help please? :-?
[http://www.ubuntu.com/netbook/get-ubuntu/download](http://www.ubuntu.com/netbook/get-ubuntu/download)


(sorry about my poor english)
[http://www.ubuntu.com/netbook/get-ubuntu/download](http://www.ubuntu.com/netbook/get-ubuntu/download)
check #2 "show me how"

---

### Post by jespdj on 2010-10-11
> **sandyd said:**
> [http://www.ubuntu.com/netbook/get-ubuntu/download](http://www.ubuntu.com/netbook/get-ubuntu/download)
check #2 "show me how"

Thanks, but that doesn't help.

I have the same problem. The Universal USB Installer doesn't have any option for Ubuntu Netbook Edition 10.10. I've tried different ways, including selecting the very last option in the list, which allows you to select any ISO. But that doesn't work - I get exactly the same as Cfmarq: it hangs at boot with that SYSLINUX message.

Why does Canonical put these instructions on their website? Aren't they aware that these instructions don't work for 10.10 Netbook Edition?

I'm trying to install it on my Dell Mini 9.

---

### Post by Shibblet on 2010-10-11
Try using Unetbootin to make your USB Stick bootable.  It will create a bootable USB drive, properly formatted, from an ISO, or download a distribution for you on the fly.

You can get Unetbootin for Windows or Linux.

---

### Post by Cfmarq on 2010-10-11
There's no option to ubuntu netbook remix 10.10 so I'ved tryed "Try some other live linux ISO" and I've selected the ISO from ubuntu netbook remix that I've download from Ubuntu website. Still doesn't working, same error.

---

### Post by Umkus on 2010-10-11
I can confirm that. Strugling just now. Failed to make bootable usb from "bootable usb creator" under Ubuntu. Failed to make bootable usb form Unetbootin under Ubuntu. Failed via Universal-USB-Installer under Windows as well, it just freeses, just like Cfmarq says.

Trouble with Dell Mini 10v with Snow Leopard on board.

---

### Post by jespdj on 2010-10-11
I tried Unetbootin instead of Universal USB Installer - unfortunately that also doesn't work.

I finally got it to work by using my Ubuntu 10.04 system, with Startup Disk Creator (one of the system tools in Ubuntu). Select the 10.10 Netbook Edition ISO and create a bootable USB stick.

The Windows tools to make a bootable USB don't seem to work. Still strange that Canonical puts this on their website. Did they not even test if it works?

---

### Post by telltom on 2010-10-11
i can't get it to work on a usb. Have to use a cd.

---

### Post by salabanzi on 2010-10-11
> **jespdj said:**
> I tried Unetbootin instead of Universal USB Installer - unfortunately that also doesn't work.

I finally got it to work by using my Ubuntu 10.04 system, with Startup Disk Creator (one of the system tools in Ubuntu). Select the 10.10 Netbook Edition ISO and create a bootable USB stick.

The Windows tools to make a bootable USB don't seem to work. Still strange that Canonical puts this on their website. Did they not even test if it works?

Yea, I tried both methods and I have the same errors as yours. Hopefully Canonical will figure something out soon. :confused:

---

### Post by Umkus on 2010-10-11
By the way, the "mac os way" didn't work for me either from the hackintosh on my dell mini. Is it really me or there's something weird going on with the remix image?

---

### Post by Cfmarq on 2010-10-11
unetbootin launch the installer but it works really slow. It have taked 3  hours to install, no errors ocurred, but now still don't boot. I'll try to do the usb drive in ubuntu like jespdj said.

---

### Post by mikewhatever on 2010-10-11
The universal USB installer has been updated and now supports UNR 10.10 and various other *buntu incarnation. Get it from [http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)

---

### Post by salabanzi on 2010-10-11
> **mikewhatever said:**
> The universal USB installer has been updated and now supports UNR 10.10 and various other *buntu incarnation. Get it from [http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)

Thanks! Works great! :D

---

### Post by Umkus on 2010-10-13
I managed to fix this the easy way:
1 Just go ahead and make a bootable usb with "USB Startup disc creator".
2 Edit /syslinux/syslinux.cfg (or /boot/syslinux/syslinux.cfg, I can't remember for sure) on the newly created bootable usb: remove the 'ui' string from the beginning of the last line.
3 ...
4 PROFIT

I managed to successfully start Netbook Remix from usb, make sure it is bugged as hell, create another bootable usb with desktop version and install from that.

In the end:
Wired network not working
Mac OS X installation broken

Dell Mini 10v, Lucid Lynx Desktop 10.10

---

### Post by trentscott on 2010-10-13
This was solved here:

[http://trentscott.com/2010/10/07/fixing-usb-install-issues-with-ubuntu-10-10-maverick-meerkat/](http://trentscott.com/2010/10/07/fixing-usb-install-issues-with-ubuntu-10-10-maverick-meerkat/)

Be sure to check out the comments.

Good luck : )

---

### Post by mikewhatever on 2010-10-13
> **Umkus said:**
> I managed to fix this the easy way:
1 Just go ahead and make a bootable usb with "USB Startup disc creator".
2 Edit /syslinux/syslinux.cfg (or /boot/syslinux/syslinux.cfg, I can't remember for sure) on the newly created bootable usb: remove the 'ui' string from the beginni
...

Wow! That was simple. Thank you.

---

### Post by Cfmarq on 2010-10-14
I'ts working but.. It's normal to be soo slow? 
I'ved installed 10.10 desktop in my laptop and it was really quick as usual, with UNR the installation proceeds really slow in my netbook! It's a toshiba nb305, with an atom n450 and 2gb ram. I think that the problem is not the netbook..

---

### Post by Thameslink on 2010-10-19
I've had some problems installing it I deleted the keyword ui from the syslinux config file then it seems to work fine.
I've also done that to get jolicloud (ubuntu-based) to work.

---

### Post by Cfmarq on 2010-10-19
I did that too, but I still have the same problems..

---

### Post by ngrieb on 2010-11-24
Is the legacy USB support enabled in BIOS? I say stick with the normal Ubuntu version. I just got this installed and it is a pain in the ***. I have the odd msdos grub message and some other cons. 

The menu loading is super slow, and I think the plan to make the stupid side dock on such a small screen already is absolutely absurd. I can't find anything in the menus. The boot time is slower (as far as I can tell might be the effect of the msdos crap), but I booted in about 35 sec with the 10.04 x64 version. The suspend and hibernate time is worse. I'm going back to 10.04-i386 myself on my NB305.

I guess you can find out for yourself though. And maybe...hopefully I am wrong about the speed of my machine, but I have not read enough on the grub boot problem to know.

Hope this helps.

---

### Post by LoRDxRaVeN on 2011-02-26
> **mikewhatever said:**
> The universal USB installer has been updated and now supports UNR 10.10 and various other *buntu incarnation. Get it from [http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)

I created the USB Stick with usb-creator.exe which is included in the ubuntu.iso.
So i also had the problem with **"SYSLINUX 3.82 2009-06-09 EBIOS Copyright (C) 1994-2009 H. Peter Anvin et al"** and then freezes on my Thinkpad Edge 11.

But with the linked universal-USB-installer it now works fine!

Thanks!

---

### Post by bjje on 2011-03-01
Quote:
 	 	 		 			 				 					Originally Posted by **mikewhatever** 					[[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=9955915#post9955915") 				
 				*The universal USB installer has been updated and now supports UNR 10.10 and various other *buntu incarnation. Get it from [http://www.pendrivelinux.com/univers...easy-as-1-2-3/]("http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/")*


[LEFT]It does include 10.10 but when I make one and boot off of it, system tells me that no drivers detected for UNITY. is it the distro?

[/LEFT]


[]("http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/")

---

