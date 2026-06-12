---
title: "im frustrated..!!!"
date: 2008-12-16
forum: New to Ubuntu
---

### Post by linux_dragon on 2008-12-16
after a week of suffering with installing my wifi card on ubuntu 8.04,
it doesnt work!, i restarted my laptop, n hit the wifi power key,,, n still
nothing!!!!

lspci gives these for the wifi card:
05:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express [14e4:1713] (rev 02)
06:00.0 Network controller [0280]: Broadcom Corporation BCM4310 USB Controller [14e4:4315] (rev 01)

ndiswrapper -l gives this:
bcmwl6 : driver installed
	device (14E4:4315) present (alternate driver: wl)

---

### Post by gn2 on 2008-12-16
Have you tried [Wicd]("http://wicd.sourceforge.net/") yet instead of Network manager?

[Downloads here]("http://sourceforge.net/project/showfiles.php?group_id=194573&package_id=229460")

Or just by an Ubuntu compatible USB wireless adapter?

---

### Post by linux_dragon on 2008-12-16
no, plz give me the full thing..

---

### Post by doobiest on 2008-12-16
don't broadcom card required the ndiswrapper, or have they started making linux drivers for them?

---

### Post by Michael.Godawski on 2008-12-16
hi, 
I must say you have picked a real beast to set up. Broadcom always turned me mad.
My advice: remove the broadcam thing and buy yourself a out-of-the-box working wlan usb stick.

---

### Post by Ayuthia on 2008-12-16
> **linux_dragon said:**
> after a week of suffering with installing my wifi card on ubuntu 8.04,
it doesnt work!, i restarted my laptop, n hit the wifi power key,,, n still
nothing!!!!

lspci gives these for the wifi card:
05:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express [14e4:1713] (rev 02)
06:00.0 Network controller [0280]: Broadcom Corporation BCM4310 USB Controller [14e4:4315] (rev 01)

ndiswrapper -l gives this:
bcmwl6 : driver installed
	device (14E4:4315) present (alternate driver: wl)

You will need to use a bcmwl5 driver.  The ones from Vista do not work.

Have you tried the wl driver (from the Terminal):
```
sudo modprobe -r ndiswrapper b43 ssb wl
sudo modprobe wl
sudo /etc/init.d/networking restart
sudo iwlist scan
```

If you have, you might try this driver:
[ftp://ftp.us.dell.com/network/R174291.exe](ftp://ftp.us.dell.com/network/R174291.exe)
You can extract the file by using:
```
unzip R174291.exe
```
You will need to remove the prior driver first:
```
sudo ndiswrapper -r bcmwl6
```

---

### Post by doobiest on 2008-12-16
go into synaptic and do a search for ndiswrapper.. install that then run it. You'll likelyhave to download the windows drivers

---

### Post by ibizatunes on 2008-12-16
Maybe try ubuntu 8.10 
Ubuntu 8.10 has a newer kernel, will ALOT more wireless drivers
That may work

---

### Post by doobiest on 2008-12-16
me and Ayuthia are on the same page, thanks for the detail.

I'm pretty darn sure broadcom doesnt have linux drivers for their wireless products.  at least last time i checked, which was a year ago when I had a broadcom wireless card.

Basically the ndiswrapper takes your windows drivers and emulates them to work on linux. Once set up the usages is seamless

---

### Post by linux_dragon on 2008-12-16
ok, thanx every body....
i bet it doesnt work cuz im using VISTA drivers.....
ill try n find XP drivers...

---

### Post by Ayuthia on 2008-12-17
> **doobiest said:**
> me and Ayuthia are on the same page, thanks for the detail.

I'm pretty darn sure broadcom doesnt have linux drivers for their wireless products.  at least last time i checked, which was a year ago when I had a broadcom wireless card.

Basically the ndiswrapper takes your windows drivers and emulates them to work on linux. Once set up the usages is seamless

Just more information.

Broadcom just came out with a driver in July for the 4311, 4312, 4321, 4322, and some 4328 cards.  It is known as the Broadcom STA or the wl module.

The one the comes in the Linux kernel is the b43/b43legacy module.  To see the list of supported cards, you can to go this [link]("http://linuxwireless.org/en/users/Drivers/b43").  However, the 4310 card (which is now known as the 4312 card) or the 14e4:4315 chipset is not supported by this module at the time.  Work is being done for it, but there is no timeline on when it will be complete.  This module does require additional firmware that has to be downloaded in order to make it work.  It cannot be included in Ubuntu because of the proprietary rules that is tied to the firmware.

The last option is NDISwrapper.  It is the "when all else fails" option for some people.  It is the NDIS module that can read the Windows driver and can make the wireless card work in most cases.  However, it can only use XP (or older) drivers.  Vista drivers are not yet supported.

---

