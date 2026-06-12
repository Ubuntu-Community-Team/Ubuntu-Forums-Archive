---
title: "Compatible dial-up modems"
date: 2005-04-05
forum: Networking &amp; Wireless
---

### Post by Bashar on 2005-04-05
Hi,
Is there a list for (out of the box) ubuntu compatible modems, anything to avoid the agony of trying to install a driver.  If such a list doesn't exist are there any clearly written tutorials, how-tos or help documents that could help me on this subject.  Thanx

---

### Post by m4ng0 on 2005-04-05
Read [this thread](http://www.ubuntuforums.org/showthread.php?t=17973).
If you have an external serial modem, you won't even need a driver, they work out of the box. For internal modems you have to be lucky. Some Lucent and Intel modems are well supported, but it depends on the chipset. You can visit [www.linmodems.org](http://www.linmodems.org) for more informations.

---

### Post by az on 2005-04-05
The ltmodem drivers (lucent) are included in the restricted modules package.  They should work out-of-the-box.  The driver is packaged with a number of userspace apps.  I would like to know if the modem works withouth these apps since the kernel modules are build, but none of the apps are included.

If someone with a lucent modem can confirm that this is actually the case, that would be great.

As for the intel modem, to compile the driver (since the driver is part userspace and part kernel module) you will need to install the sl-modem-daemon along with the sl-modem-module.  The sl-modem-module is something that you have to compile.  It is easy to do.  You will need to install build-essential and linux-headers from your Hoary cd, but you will need to download the sl-modem-source from Multiverse and the module-assistant package from Universe.

I can make the sl-modem-modules package available.  I'll do that tonight.  I'll leave a link here...

---

### Post by m4ng0 on 2005-04-05
[QUOTE=azz]The ltmodem drivers (lucent) are included in the restricted modules package.  They should work out-of-the-box.  The driver is packaged with a number of userspace apps.  I would like to know if the modem works withouth these apps since the kernel modules are build, but none of the apps are included.

If someone with a lucent modem can confirm that this is actually the case, that would be great.
[/QUOTE]

I've installed Ubuntu on a pc with a Lucent Winmodem. I didn't know ltmodem was included in restricted modules package, so I installed linux-headers and build-essential and used the sources provided by
[http://linmodems.technion.ac.il/packages/ltmodem/kernel-2.6/ltmodem-2.6-alk-7.tar.bz2](http://linmodems.technion.ac.il/packages/ltmodem/kernel-2.6/ltmodem-2.6-alk-7.tar.bz2). I compiled the modules, loaded ltmodem and everything went fine (without userspace apps).
I don't have that pc with me anymore (I've installed Ubuntu on it and returned back to the owner) so I can't try with restricted modules package, but I think there should not be many differences.

---

### Post by az on 2005-04-05
"I've installed Ubuntu on a pc with a Lucent Winmodem. I didn't know ltmodem was included in restricted modules package, so I installed linux-headers and build-essential and used the sources provided by
[http://linmodems.technion.ac.il/pac...6-alk-7.tar.bz2](http://linmodems.technion.ac.il/pac...6-alk-7.tar.bz2). I compiled the modules, loaded ltmodem and everything went fine (without userspace apps)."

Compiling all that makes that apps.  Make install installs them.  That is my point,  Only the modules are included.  Also, was that Hoary or Warty?

Here are the links to the procompiled modules:

[http://apqi.com/ubuntu/sl-modem-modules-2.6.10-5-386_2.9.9a-1ubuntu2+2.6.10-29_i386.deb](http://apqi.com/ubuntu/sl-modem-modules-2.6.10-5-386_2.9.9a-1ubuntu2+2.6.10-29_i386.deb)
[http://apqi.com/ubuntu/sl-modem-daemon_2.9.9a-1ubuntu2_i386.deb](http://apqi.com/ubuntu/sl-modem-daemon_2.9.9a-1ubuntu2_i386.deb)

Download them and save them to a floppy or usb stick.  
cd there
sudo dpkg -i sl-modem*

Use /dev/modem when asked about your modem.

----



I need a newer version of ndiswrapper to deal with my motherboard.  Here it is:

[http://apqi.com/ubuntu/ndiswrapper-modules-2.6.10-5-386_1.1-1_i386.deb](http://apqi.com/ubuntu/ndiswrapper-modules-2.6.10-5-386_1.1-1_i386.deb)
[http://apqi.com/ubuntu/ndiswrapper-utils_1.1-1_i386.deb](http://apqi.com/ubuntu/ndiswrapper-utils_1.1-1_i386.deb)

---

### Post by Bashar on 2005-04-06
[QUOTE=m4ng0]
If you have an external serial modem, you won't even need a driver, they work out of the box..[/QUOTE]
What if I buy an external USB modem, is that guaranteed to work out-of-the-box as well?  thank you for your patience

---

### Post by az on 2005-04-06
No, it is not.

---

### Post by jllitvay on 2005-04-08
[QUOTE=azz]Here are the links to the procompiled modules:

[http://apqi.com/ubuntu/sl-modem-modules-2.6.10-5-386_2.9.9a-1ubuntu2+2.6.10-29_i386.deb](http://apqi.com/ubuntu/sl-modem-modules-2.6.10-5-386_2.9.9a-1ubuntu2+2.6.10-29_i386.deb)
[http://apqi.com/ubuntu/sl-modem-daemon_2.9.9a-1ubuntu2_i386.deb](http://apqi.com/ubuntu/sl-modem-daemon_2.9.9a-1ubuntu2_i386.deb)

Download them and save them to a floppy or usb stick.  
cd there
sudo dpkg -i sl-modem*

Use /dev/modem when asked about your modem.
 [/QUOTE]
These packages is for the lucent modems? should I dpkg both?

---

### Post by az on 2005-04-08
No, they are for sl-modems (Intel, ac97 codec)

---

### Post by inaki.gonzalez on 2005-09-30
Hi

I was able to use my serial modem with my first ubuntu HH now when I change my ubuntu to breeze it does not connect it my modem gives a sound and dies and thats it. I tried to use the auto detect and it did detect my modem.

inaki

---

### Post by pkoebbe on 2005-10-01
inaki.gonzalez
The pre-release version of Breezy doesn't have the LT modem drivers in the restricted-modules package.  Not sure if that is an oversight or planned omission.  Only time will tell.  I've been wrestling with this a little, and so far my only solution is to not run Breezy on the box that has the modem.

When I upgraded to Breezy, the restricted-modules from Hoary wasn't removed, so I still had the modules on my drive.  I booted using the Hoary kernel, thinking that I could load the existing modules and everything would be great.  Well, it was, until it came time for pppd to do its thing.  The modules loaded, the modem was recognized, it dialed, and pppd failed to load.  My guess is that Breezy's pppd was compiled against the 2.6.12.* kernel that is default in Breezy, and since I was running the 2.6.10.* kernel of Hoary, it choked.

This was on a box that I had just blasted and started over, so I blasted again and went back to just Hoary.  I'm connected and writing this from that box now.  So I'll wait until Breezy is final and see if the LT modules are in restricted-modules or not.  If not, I'll have to make a decision on what modem to buy.  I don't want to be stuck at Hoary forever.
Peace,
Phillip

---

### Post by vgeddes on 2005-10-11
Trust me, get an standard external modem!

They might be bulky and old-fashioned, but it will save you the mind-bending horror of trying to get these internal winmodems to work.

I made a mistake and bought a conexant winmodem. I then had to spend an extra $ 15 on a linux driver, which hardly works and is buggy as hell. I can't upgrade my kernel because the driver won't play nice, and if I try to send data via the modem, the whole computer just locks up hard ;-(

---

### Post by mips on 2005-10-11
external serial modems are your best bet for linux imho. Very happy with my old reliable USR Sportster, has always served me well.

---

