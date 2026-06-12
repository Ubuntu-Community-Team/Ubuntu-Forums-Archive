---
title: "[SOLVED] NDISwrapper issues on AMD64"
date: 2007-08-07
forum: Networking &amp; Wireless
---

### Post by captainfullet on 2007-08-07
Hey all,

I have just installed Feisty 64-bit on my Core2 processor, and am trying to get my wireless pci card (Netgear WG311v3, Marvell chipset) up to speed. Although I am new to both Ubuntu and Linux, I have played around with it a bit and am fairly familiar with the terminal, so I decided to post here.

My problem is this: NDISwrapper can't get a 32-bit driver for Windows to work in a 64-bit distro of Linux, which means that the driver which came with my card (and this driver is listed as working on NDISwrapper's list) does NOT work on my install. (in the terminal, it ndiswrapper detects the driver and the hardware, but in ndiswrapper's gui, it doesn't detect the hardware, and basically just doesn'twork, no wireless network config showing up). So I need a 64-bit driver to work it (at least that's what the NDISwrapper website says). I downloaded the newest driver from Netgear's website (Version 2.0) which says in it's changelog that it supporst Windows Vista. Now, I did read on another thread that Netgear has said that they won't do 64-bit drvers, but I think that this Vista-compatible driver is probably my best bet. The problem is this: the driver is an .exe, but won't respond to unshield, cabextract, or unzip, even though it is an installshield wizard. I have 32-bit windows xp running, so when I run the driver on my windows install, it just gives me the 32-bit drivers, not the 64-bit. My question is basically this:

How do I crack open that .exe?
or, if that isn't possible:
is there some other way to get my wireless nic to work in ubuntu?

My biggest problem in this whole process is that I have windows and ubuntu dual boot, and the wireless card is my only access to the internet, which means everytime i try something new, or download another .deb or tarball, I have to restart, ugh.

Thanks for all the help!

---

### Post by Jouke74 on 2007-08-07
Have you tried this driver + recipe?

[http://ubuntuforums.org/showthread.php?t=419727](http://ubuntuforums.org/showthread.php?t=419727)

You say you have a Marvell chipset, so this might work for you also. At least, this marvell 64-bit driver is known to work with Ndiswrapper and serves me still well at the moment.

---

### Post by captainfullet on 2007-08-07
I'll give it a shot, but I'm not sure it will work because the pciid on that one is 11ab:1fa6 (rev 07) whereas mine is 11ab:1faa (rev 03)

Still worth a try, and I'll also try looking for any drivers that ubuntu is attempting to load instead of my ndiswrapped ones. Any other suggestions?

---

### Post by captainfullet on 2007-08-07
alright, I uninstalled the ndiswrapper utils and common, and compiled from source (ver 1.47) in order to try again using this new 64-bit ASUS driver. Before, i got NDISwrapper to see my wg311v3 driver, it even said, driver present, device present. However, with the asus/marvell driver, no such luck. It said driver present, but not device present. I don't even have a wlan0 showing up on my Networks page!

Does anybody have ANY more knowledge on the topic?

---

### Post by Jouke74 on 2007-08-08
That simply means that the driver of Asus cannot be used for this card, unfortunately. You have to uninstall the driver and try another one. 

From Ndiswrapper site:

Netgear WG311 v3 (Marvell 88w8335 Libertas)
Chipset: Marvell 88w8335 Libertas 54Mbps Wireless Interface
pciid: 11ab:1faa
Driver copied from [http://kbserver.netgear.com/products/WG311v3.asp](http://kbserver.netgear.com/products/WG311v3.asp)
From Initial Release 6.20 MB May 16,
Running Mandriva Free 2007 DVD
Program Computer Configuration - Network and Internet-Cofiguration New Device
Works Great

It only does not say whether these are 64 bit also... (sigh).

---

### Post by captainfullet on 2007-08-08
YES!! Finally!!

Thanks to [this GLORIOUS thread]("http://ubuntuforums.org/showthread.php?t=320111")!

After installing the suggested drivers from that thread, I pretty much just messed around with all of my settings, trying static, and so on, eventually upgrading my router firmware and getting rid of encryption, rebooting a bunch of times, etc. After I got rid of encryption, Wifi radar could connect to the network, then I added WEP encryption back in....I am SO RELIEVED.

---

