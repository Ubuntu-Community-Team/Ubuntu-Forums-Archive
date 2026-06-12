---
title: "USB drivers not found when plugging in a Senao/EnGenius USB device"
date: 2011-04-27
forum: New to Ubuntu
---

### Post by rocksockdoc on 2011-04-27
It appears I'm sailing in uncharted seas ... and that I don't know the sequence of steps that "are supposed" to occur when you plug in an external USB wifi device into Ubuntu 10.04 lucid.

When I plug this device into the USB port (one or two ports), nothing happens!

The device is:
- [Senao EnGenius EUB9603H]("http://www.engeniustech.com/index.php?option=com_content&view=article&id=326&Itemid=192") Wireless 11b/g/n Hight Power USB Adapter (2,000 mW, & a 5 dBi detachable antenna)

Here's what 'happens' (essentially nothing that I can tell):

[LIST=1]
[*]Plugging the EUB9603 WiFi extender into two available USB slots, nothing happens
[LIST]
[*]No lights blink on the device
[*]The /var/log/messages file lists some information; but nothing useful I can glean:
[LIST]
[*]usb 2-1: new high speed USB device using ehci_hcd and address 3
[*]usb 2-1: configuration #1 chosen from 1 choice
[/LIST]
 
[/LIST]
 
[*]"lsusb" reveals this Senao/EnGenius WiFi extender uses the "1740:9603 Senao" chipset
[LIST]
[*]Bus 001 Device 006: ID 1740:9603 Senao
[/LIST]
 
[*]"ifconfig | grep wlan" reveals there is no wlan1 external adapter (just the wlan0 internal radio card):
[LIST]
[*]wlan0 Link encap:Ethernet  HWaddr 00:a3:f8:2e:e7:df
[/LIST]
 
[*]"iwconfig | grep wlan" also reveals only the internal card connection point:
[LIST]
[*]wlan0 IEEE 802.11abgn  ESSID:"linksys"
[/LIST]
 
[*]"lsmod | grep rt2" didn't reveal any entries
[*]A search for "1740:9603 Senao" in these Ubuntuforums reveals only a single thread:
[LIST]
[*] [SOLVED] [Engenius eub9703 usb]("http://ubuntuforums.org/showthread.php?t=1623442&highlight=1740%3A9603+Senao") by phoenixpb, November 17th, 2010
[/LIST]
 
[*]I've tried all that was listed in that thread ... but it's not the  same situation as that OP was emulating with Wine so he apparently had  the necessary drivers (the unit doesn't come with Linux drivers).
[*]So I sent a message to Senao technical support (fae@senaousa.com) from this web page
[LIST]
[*][http://www.senaousa.com/support.html](http://www.senaousa.com/support.html)  (888-735-7888)
[/LIST]
 
[/LIST]
I ask for DEBUGGING help here. What specifically is 'supposed' to happen when I plug in a USB device?

Any idea how to get Linux to recognize this external USB device?

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=190184&stc=1&d=1303936194[/IMG]

---

### Post by rocksockdoc on 2011-04-29
No troubleshooting advice?

---

### Post by rocksockdoc on 2012-01-30
This appears to be a bug in Ubuntu ... but I did list some troubleshooting advice over here:

[LIST]
[*][How do we tell Ubuntu 10.04 to use a DIFFERENT wireless radio card?]("http://ubuntuforums.org/showthread.php?t=1737183")
[/LIST]
In addition, I recently found a WiFi extender device that will extend the puny Lenovo X61t laptop wireless range (1 dBi omni antenna, 17 dbM radio, 50mW transmit power):

[LIST]
[*][Is there a 802.11 laptop wifi range extender that is known to work with Ubuntu 10.04?]("http://ubuntuforums.org/showthread.php?t=1738444")
[/LIST]
The main problem is that Ubuntu is apparently so buggy that almost no USB wireless device will work properly. At least nobody has reported any USB wifi extenders that have worked with Ubuntu distributions.

---

### Post by anewguy on 2012-01-30
> The main problem is that Ubuntu is apparently so buggy that almost no USB wireless device will work properly. At least nobody has reported any USB wifi extenders that have worked with Ubuntu distributions. 

The problem isn't Ubuntu - the problem is a lack of drivers.

---

### Post by rocksockdoc on 2012-01-30
> **anewguy said:**
> The problem isn't Ubuntu - the problem is a lack of drivers.

I think Ubuntu, in the case below, is actually loading the WRONG driver:
- Ubuntu should be loading the "rtl819xU" driver.
- But, instead, Ubuntu loads the "rtl819xE" driver.

I think that's a bug.

What happened when I plugged in the USB-powered WiFi radio + antenna ("Amped UA600 500mW 5dBi Wireless Router) to my Lenovo X61t laptop, was that ifconfig did 'not' detect this new wlan1 device nor did it seem to load **any** driver into memory.

However, the device '**was**' apparently detected, as shown by the list-short-usb command:
```
                              $ lsusb
... stuff ... 
Bus 002 Device 002: ID 0bda:[COLOR=DarkRed]**8172 Realtek Semiconductor Corp. **[/COLOR]
... stuff ...                       
```According to Realtek, the hardware ID 0bda:8172 uses the Realtek RTL8191S**[COLOR=DarkRed]U[/COLOR]** chip  set. Therefore, the correct driver is supposed to be the "RTL8191S**[COLOR=DarkRed]U[/COLOR]** Linux Version 0006.20100625" software driver.

When I plugged in and unplugged that wlan1 device, the /var/log/messages revealed that the **WRONG driver **was being loaded:
```
Linux kernel driver for RTL8192 based WLAN cards 
Copyright (c) 2007-2008, Realsil Wlan 
... 
rtl8192_proc_init_one+0x25/0x460 [r8192s_usb] 
rtl8192_usb_probe+0x148/0x191 [r8192s_usb] <==== Useful for modinfo command syntax! 
... 
usbcore: registered new interface driver rtl819xU   <=== [COLOR=DarkRed]NOTICE that "**U**" [/COLOR](Ubuntu has only the "**[COLOR=DarkRed]E[/COLOR]**") 
usb 2-1: firmware: requesting RTL8192SU/rtl8192sfw.bin
```

Apparently, this is the driver that should be loaded (but it doesn't exist in Ubuntu):

[LIST]
[*]/lib/firmware/RTL8192SU/rtl8192sfw_bin
[/LIST]
Here is the result of a modinfo command:
> $ modinfo r8192s_usb 

... 

filename:  /lib/modules/2.6.32-31-generic/kernel/drivers/staging/rtl8192su/r8192s_usb.ko 

description:    Linux driver for Realtek RTL8192 USB WiFi cards 

...


Note: I tried to workaround the Ubuntu bug by fooling Ubuntu into thinking it was loading the right driver - but this attempt didn't work:
NOTE: The** E** vs the** U** below.

> $ sudo ln -s /lib/firmware/RTL8192S**[COLOR=DarkRed]E[/COLOR]**/rtl8192sfw.bin /lib/firmware/RTL8192S**[COLOR=DarkRed]U[/COLOR]**/rtl8192sfw_bin


So, the problem 'appears' to be a Ubuntu bug - but I have no experience other than simply trying to get two of these wireless USB wifi devices to work! Sigh.

[LIST]
[*] In summary, (apparently) the Realtek (0bda:8172) hardware was 'looking' for this driver:
[LIST]
[*]/lib/firmware/RTL8192S**[COLOR=DarkRed]U[/COLOR]**/rtl8192sfw_bin
[/LIST]
[*]Unfortunately, Ubuntu 10.04 only had this driver:
[LIST]
[*]/lib/firmware/RTL8192S**[COLOR=DarkRed]E[/COLOR]**/rtl8192sfw_bin
[/LIST]
[/LIST]
It looks like a LOT of people have been similarly burned by this Ubuntu bug:
- [Ubuntu Karmic 32bit Realtek 8192SU driver]("http://ubuntuforums.org/showthread.php?p=10719084#post10719084")
- [Realtek RTL8192SU driver compiling issues]("http://ubuntuforums.org/showthread.php?t=1425697")
-[ [STAGING] realtek rtl8192su chipset based USB wireless devices fail to work    ]("http://ubuntuforums.org/showpost.php?p=10125636&postcount=17")
**- **[Mvix Solido driver (rtl8712/8172) on 10.04]("http://ubuntuforums.org/showthread.php?t=1466185")
- [Firmware for Realtek 8192  ]("http://www.linuxquestions.org/questions/linux-wireless-networking-41/firmware-for-realtek-8192-a-761714/page2.html")
etc.

---

### Post by anewguy on 2012-01-30
The hardware doesn't look for a driver - the OS sees the hardware and tries to determine what driver to use.  The OS, via the USB subsystem software, detected the device and "requested" the driver from the kernel (all software).  In this case it chose what it thought was correct because it was the closest it could come with what drivers and firmware it has. A device being detected - as in your lsusb - doesn't mean it can be accessed - like in a missing driver.  Note the "sfw" is probably referring to the "s" version firmware.  A driver may or may not fix missing firmware - more may be required.

Let me see - iI just randomly picked the last thread you showed [http://www.linuxquestions.org/questions/linux-wireless-networking-41/firmware-for-realtek-8192-a-761714/page2.html]("http://www.linuxquestions.org/questions/linux-wireless-networking-41/firmware-for-realtek-8192-a-761714/page2.html") to check - that a ***_Fedora_*** forum - how did this magically become "proof" of a bug in Ubuntu (debian based)??

So let me see if I have this right - Windows and Ubuntu are delivered with a limited set of ?drivers -> hence why the manufacturers enclose a driver disk.  So with Windows it's ok since the manufacturer gives you a driver disk, but in Ubuntu it's Ubuntu's fault because the manufacturer either doesn't have open-source drivers (the only kind that can be included with Ubuntu and still have Ubuntu be open-source) so they couldn't give them to be included with Ubuntu or they wouldn't give them for inclusion in Ubuntu?  Think not.

I'll take a look at your problem, but don't keep blaming Ubuntu - your support chances will deminish quite quickly.

---

### Post by anewguy on 2012-01-30
So, this page says exactly how to get it working in 10.04 - and if it was me I'd be trying it first.  Keep in mind this is for the last device you posted - the Realtek.  Simply search of ubuntu and the usb manufacturer:product id's showed this right away.

[http://samiux.blogspot.com/2010/05/howto-realtek-8192su-usb-dongle.html]("http://samiux.blogspot.com/2010/05/howto-realtek-8192su-usb-dongle.html")

What I can't tell from your thread - do you want help on the Senao device or the Realtek device, as given the usb manufacturer:product id's they seem to be 2 very separate devices.

---

### Post by anewguy on 2012-01-30
For your Senao device, just follow this thread -I wouldn't worry about the stuff they do after they get it working the first time.

[http://ubuntuforums.org/showthread.php?t=1817450]("http://ubuntuforums.org/showthread.php?t=1817450")

Again, a simple search engine search turned this up.

---

### Post by rocksockdoc on 2012-01-31
> **anewguy said:**
> The hardware doesn't look for a driver

This is good information because, having come from Windoze, it was all magic for me.

[LIST=1]
[*]The OS sees the hardware and tries to determine what driver to use.
[*]The OS, via the USB subsystem software, detected the device and "requested" the driver from the kernel (all software).
[*]In this case it chose what it thought was correct because it was the closest it could come with what drivers and firmware it has.
[*]A driver may or may not fix missing firmware - more may be required.
[/LIST]
   > **anewguy said:**
> don't keep blaming Ubuntu

I had no idea of this issue of drivers needing to be of 'open source' origin. I hadn't even thought about it. I just 'assumed' the operating system (by magic) loads the right drivers if it loads any drivers. I stand corrected.

All I really know is that the thing doesn't work and what I think is that the wrong driver is loaded. That's all. I assumed it was the OS fault - but - you've shown that it's really the manufacturer's job to make sure the right driver exists for Ubuntu. And, we know they did NOT supply the right driver.

So I apologize for blaming the operating system. I really don't know how this stuff works but I am learning (slowly).

---

### Post by anewguy on 2012-01-31
That's okay - we all had (and I still need to learn a LOT) to learn sometime and somehow - and a lot of us had the same views having come from Windows.

Please, let me know if any of those links help you and if you need help trying to do what's in them.  I'm hoping we can make this work for you!

Dave ;)

---

