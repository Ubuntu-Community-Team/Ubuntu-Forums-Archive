---
title: "[SOLVED] Lubuntu - Same old Broadcom BCM4318 wireless problem"
date: 2016-03-06
forum: Networking &amp; Wireless
---

### Post by Xubuntist on 2016-03-06
I have spent almost a full day trying to fix this problem and finally solved it. I thought I'd post my experience here in case somebody with an older laptop falls into the same deep, depressing hole.

The laptop is an old Acer Aspire 3100. It had Windows XP on it and it had always used its Wifi connection to connect to the Internet. I decided to put an Ubuntu on it but since I'm always putting Xubuntu on laptops, I thought I'd try a few different flavours. Here are the ones I tried (mostly 14.04 i386):
[LIST]
[*]Ubuntu 
[*]Lubuntu 
[*]Xubuntu 
[*]Macbuntu 
[*]Kubuntu 
[*]Linux Mint 
[/LIST]
All of the above were put onto a SD card reader using Universal USB Installer and in the first instance I would run the Live version to see if I liked it with a view to then installing to the hard drive.

However, I noticed that **none **of the Live versions of Linux I tried found a Wireless network. The laptop was connected via Ethernet and I finally decided to install Lubuntu. 

My thanks go to [http://linuxwireless.sipsolutions.net/en/users/Drivers/b43/](http://linuxwireless.sipsolutions.net/en/users/Drivers/b43/) and many other thread contributors on ubuntuforums.org and elsewhere. [URL="http://linuxwireless.sipsolutions.net/en/users/Drivers/b43/"]
[/URL]
The first thing I did was:
```
 lspci -vnn -d 14e4:
```
which gave me:
```
06:02.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
    Subsystem: AMBIT Microsystem Corp. TravelMate 2410 [1468:0312]
    Flags: bus master, fast devsel, latency 64, IRQ 22
    Memory at d0200000 (32-bit, non-prefetchable) [size=8K]
    Kernel driver in use: b43-pci-bridge
```

So I searched everywhere for B34 issues and the floodgates opened. The whole world seems to have problems with this card on Linux. Oh well, how difficult can it be? Well, very, if my experience is anything to go by.

I won't bore you with the multitude of things that I did (following all sorts of [SOLVED] forum thread guides) because none of them worked, almost certainly because when you try too many things you completely c*ck up your configuration with too many "tips and tricks" fighting for supremacy. Instead, here is how I solved it. It's not that there are any steps in here that aren't mentioned elsewhere, it seems to be the order in which I did it that fixed it for me. I found on one thread a very knowledgeable chap who insisted that the WL driver would simply not work for the 4318 card and that you HAVE to use the B43 driver.

But the first thing I did was a complete wipe/reinstall of Lubuntu. I believe that this was crucial to my success.

Then I did:
```
rfkill list
```
This gave me:
```
0: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no
```
This confirmed that the wireless hardware switch on the front of the laptop wasn't the problem.

Next, I **de**blacklisted **bcm43xx** (which is blacklisted by default):

```
# replaced by b43 and ssb.
**#** blacklist bcm43xx
```
but on rebooting it still didn't detect a wireless network. But I have left it commented out anyway.

I then did what just about everybody recommends:
```
sudo apt-get purge bcmwl-kernel-source
```
but this told me :
```
Package 'bcmwl-kernel-source' is not installed, so not removed
```

I then installed the B43 firmware:
```
sudo apt-get install b43-fwcutter firmware-b43-installer
```

And finally I unloaded and then reloaded the B34 driver:
```
sudo modprobe -r b43 bcma
sudo modprobe b43
```

**Every** time I had tried [FONT=courier new]sudo modprobe b43 [/FONT]in previous efforts to fix this, the terminal would hang. After a couple of tries this would be enough to tell me that yet another attempt to fix the problem had failed. 

But this time it executed instantly and returned me to the prompt. And, lo and behold, all of a sudden** the laptop detected and connected to my wireless network**. It was truly a "Eureka" moment as I had spent literally HOURS on this. 

I can't say which step was the clincher. Maybe it was the order of execution, maybe it was the fact it was done on a virgin Lubuntu, maybe it was the fact no steps were repeated with just a slight alteration, who knows? But I was one step away from installing Windows 7 on the laptop and am now glad I persisted with *buntu. I hope this helps anybody else who finds themselves in the same boat.[URL="http://linuxwireless.sipsolutions.net/en/users/Drivers/b43/"]
[/URL]

---

### Post by chili555 on 2016-03-06
I have a few observations to offer. First:> I found on one thread a very knowledgeable chap who insisted that the WL driver would simply not work for the 4318 card and that you HAVE to use the B43 driver.Correct.> I won't bore you with the multitude of things that I did (following all sorts of [SOLVED] forum thread guides) because none of them worked, almost certainly because when you try too many things you completely c*ck up your configuration with too many "tips and tricks" fighting for supremacy.Also correct.> Next, I deblacklisted bcm43xx (which is blacklisted by default):

Code:

# replaced by b43 and ssb.
# blacklist bcm43xx

but on rebooting it still didn't detect a wireless network. But I have left it commented out anyway.There isn't and hasn't been for many years any module named bcm43xx. Blacklisting or unblacklisting it are meaningless either way.

On this forum and on askubuntu, there are very good guides for Broadcom cards. They are clear for your device.

> ```
14e4:4318                  firmware-b43-installer                firmware-b43-installer
```And also:> NOTE - If you have previously installed any drivers, have blacklisted or uncommented any driver files or configuration files or have done any changes whatsoever to the system to make the drivers work, you will need to undo them in order to follow this guide. We assume you are doing this from scratch and have not changed the configuration files, modules or drivers in the system in any way (apart from updating it).


For example, if you previously installed the bcmwl-kernel-source package, you will need to remove it by using the purge method:
Code:

```
sudo apt-get purge bcmwl-kernel-source
```

For the benefit of the searchers, I urge you to follow the sticky. It is all clearly explained there.

---

### Post by jeremy31 on 2016-03-07
Someone smarter than I could probably make a script using the info from the sticky that would tell a user what to use/download

---

### Post by chili555 on 2016-03-07
> **jeremy31 said:**
> Someone smarter than I could probably make a script using the info from the sticky that would tell a user what to use/downloadAnd definitely smarter than me. That is a great idea. I wonder if it could be a refinement to "Additional Drivers."

---

