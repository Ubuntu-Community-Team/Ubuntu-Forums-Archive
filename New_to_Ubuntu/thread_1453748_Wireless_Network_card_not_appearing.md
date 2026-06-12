---
title: "Wireless Network card not appearing"
date: 2010-04-13
forum: New to Ubuntu
---

### Post by m1rocking on 2010-04-13
I am new to linux/ubuntu know around zip at the moment.  I have installed ubuntu 9.10, it has picked up the wired network card but not the wireless. 

I have a dlink dwl 520+    card hardware version A2   Firmware 1.0 * If I go to system -> administration -> network tools I can see the loopback interface and the ethernet card eth0 but no wireless card. 

Could anyone point me in the direction on how to install this card any help appreciated thank you

---

### Post by m1rocking on 2010-04-13
I have just run the following command lspci -v
Not sure if this helps

The results are:

01:00.0 Network controller: Texas Instruments ACX 100 22Mbps Wireless Interface
Subsytem: D-Link System Inc Device 3b01
Flags: bus master, medium devsel, latency 64, IRQ 10
I/O ports at df20 [size=32]
Memory at feaee000 (32 bit, non-prefetchable) [size=4k]
Memory at feaf0000 (32 bit, non-prefetchable) [size=64k]
Capabilities: <access denied>

---

### Post by skyeric on 2010-04-13
if you right click on network connections at the top of your screen does it give you the option to 'enable wireless' or just to 'enable networking'?

---

### Post by m1rocking on 2010-04-13
Hi it only gives me enable networking

---

### Post by skyeric on 2010-04-13
Okay sorry it took me a while been researching this,
as far as I can tell this project covers the driver you need --> [http://acx100.sourceforge.net/wiki/Firmware](http://acx100.sourceforge.net/wiki/Firmware)
I'm pretty new to ubuntu so don't want to try and give you too much direction from there but this table ([http://web.archive.org/web/20060510135035/http://acx100.erley.org/acx_fw/acx1xx.htm](http://web.archive.org/web/20060510135035/http://acx100.erley.org/acx_fw/acx1xx.htm) ) certainly shows you network card as being supported and the first link should tell you how to go about setting it up.
Hope this helps,
Eric

---

### Post by skyeric on 2010-04-13
A far easier method would be if you were able to connect to the internet using an ehternet cable and then you should be able to set it up through system > administration > hardware drivers.

---

### Post by rexwhitten on 2010-04-13
All,

I am also having the same issue with my WiFi driver on my Laptop. 

Laptop: HP Pavillion tx 2000 (Tablet) 

Wifi Device: Broadcom BXCM4322 

- The network icon at the top of the desktop only allows 'enable networking'

lspci -v   - outputs all data about by boardcom card

lshw -C network  also shows my wifi card. It does not show it as unclaimed. 

I tried to see if the device was blacklisted, but the directory /etc/modprobe.d does not contain a file for board com devices. I edited blacklist-aith.pci and this also had no effect. 

I am unable to use a wired connection because it to is not showing up as an active network connection. 

This leads me to belive that the system can see and access these devices atleast from a HAL perspective but it is unable to use them. 

These devices work in Win 2008 R2, Open Solaris, Ubuntu 9.08, and Kubuntu 9.something. 

I have seen this post ( [http://ubuntuforums.org/showthread.php?t=1307836](http://ubuntuforums.org/showthread.php?t=1307836) ) on this forum and tried everything they suggested, except for the apt-get (no network) 

Please advise thanks!

---

### Post by anewguy on 2010-04-13
> **rexwhitten said:**
> All,

I am also having the same issue with my WiFi driver on my Laptop. 

Laptop: HP Pavillion tx 2000 (Tablet) 

Wifi Device: Broadcom BXCM4322 

- The network icon at the top of the desktop only allows 'enable networking'

lspci -v   - outputs all data about by boardcom card

lshw -C network  also shows my wifi card. It does not show it as unclaimed. 

I tried to see if the device was blacklisted, but the directory /etc/modprobe.d does not contain a file for board com devices. I edited blacklist-aith.pci and this also had no effect. 

I am unable to use a wired connection because it to is not showing up as an active network connection. 

This leads me to belive that the system can see and access these devices atleast from a HAL perspective but it is unable to use them. 

These devices work in Win 2008 R2, Open Solaris, Ubuntu 9.08, and Kubuntu 9.something. 

I have seen this post ( [http://ubuntuforums.org/showthread.php?t=1307836](http://ubuntuforums.org/showthread.php?t=1307836) ) on this forum and tried everything they suggested, except for the apt-get (no network) 

Please advise thanks!



There are a TON of posts here on getting Broadcom wireless working, however, in the interest of helping a newbie (and who knows - maybe I'll learn something too), please open your own post for this and then we'll work on your problem.  We don't want to get 2 seperate strings going here since your problem and adapter are completely different than the OP's.

Dave ;)

---

### Post by m1rocking on 2010-04-25
Thanks for the replies, I have not really got much further and to make things worse .. .from what I see this card only accepts wep. I have no idea what I am doing. Could some one please advise me which card to purchase, I am looking at D-Link Airplus Xtreme-G DWL-G520 it might be an easier route out there.

Thanks

---

### Post by jerome1232 on 2010-04-25
Here is a list of supported wireless cards. Some cards require finagaling some don't. Mine (netgear wg311v3) requires ndiswrapper and xp windows drivers to work for example.

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

---

### Post by Windows Nerd on 2010-04-25
> **m1rocking said:**
> Thanks for the replies, I have not really got much further and to make things worse .. .from what I see this card only accepts wep. I have no idea what I am doing. Could some one please advise me which card to purchase, I am looking at D-Link Airplus Xtreme-G DWL-G520 it might be an easier route out there.

Thanks
If your existing card only grants access to WEP, it's useless. Setting your home network to WEP will crackable by a novice hacker. The D-link card is good and suppurts most (if not all) security protocols. It also has a 3-year warranty. Oh yeah and Cnet says that the card is compatible with Windows only, but they probably didn't think to test it on Linux. I am not sure what you will find for drivers/compatibility with Ubuntu.

Scott

---

