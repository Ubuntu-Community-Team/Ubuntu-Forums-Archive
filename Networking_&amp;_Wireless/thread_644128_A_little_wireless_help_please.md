---
title: "A little wireless help please"
date: 2007-12-18
forum: Networking &amp; Wireless
---

### Post by browning_man9 on 2007-12-18
I am trying to connect to the wireless network at my home (and I'm a beginner, so try please don't be too technical). I am running Ubuntu 7.10.

I believe that I have installed the driver correctly using ndiswrapper becuaes when I type:

ndiswrapper -l, I get: 
mrv8335: Driver installed
device(11AB:1FAA) present

However, when I type iwconfig, the two entries I get are:

lo
eth0

Based on the hardware address, eth0 is my onboard LAN, and not my wireless card. lo is a loopback thingy from what i've read. Shouldn't there be another entry that says something about my wireless card? When I click on Network from Administration, I have the options of a "wired network" or a modem. Shouldn't it be picking up the wireless network.

I appreciate any guidance! Thanks!

---

### Post by buntunub on 2007-12-18
Do a search on these forums under your wireless card chipset type and you should find the answers to every one of your questions.

> (and I'm a beginner, so try please don't be too technical)

Based on that, you should NOT be messing around with ndiswrapper and kernel modules without strictly following a guide posted by someone much more knowledgeable and experienced.

---

### Post by browning_man9 on 2007-12-18
I've been doing lots of research all day, and have not found any answers.

Also, I have nothing important to lose, so I can mess around with ndiswrapper. This is simply a learning experience for me.

I just don't know why the wireless card doesn't show up in iwconfig when ndiswrapper said that I have my driver installed...

---

### Post by rustybronco on 2007-12-18
Try...
[http://ubuntuforums.org/showthread.php?t=603154](http://ubuntuforums.org/showthread.php?t=603154)

---

### Post by browning_man9 on 2007-12-18
In that article, it says this (which is where I am at):

If you do not see any network lines when you first open network manager, there are two possibilities:

a.) There are no networks of sufficient signal strength in your area (if at home, your wifi router may be turned off). Solution: move to an area where there are networks, or turn on your router.

b.) Your network wireless card is not working with your ubuntu system. In this case you will have to delve into the requirements for your wireless card -- drivers, etc. this is covered elsewhere in wikis and documentation online.

I don't see my wireless network listed. All that is there is modem and a "wired network" which i think to be just a generic configuration like "modem".

I believe I can eliminate (a) because I have enough signal strength in windows.

That leaves option 2, but I think that my driver is installed properly becuase it is listed when I type ndiswrapper -l...... What is my next step?

---

### Post by browning_man9 on 2007-12-18
This is my latest "come across." I'm not sure what this is telling me, maybe one of you can decipher it. Does it matter that I'm using a 64 bit version of Ubuntu, and using 32 bit drivers (I guess)? Thanks again! I appreciate this!


dave@dave-ubuntu:~$ sudo modprobe ndiswrapper
dave@dave-ubuntu:~$ dmesg | grep ndiswrapper
[ 241.102488] ndiswrapper version 1.45 loaded (smp=yes)
[ 241.146026] ndiswrapper (check_nt_hdr:153): kernel is 64-bit, but Windows driver is not 64-bit;bad magic: 010B
[ 241.146035] ndiswrapper (load_sys_files:216): couldn't prepare driver 'mrv8335'
[ 241.146891] ndiswrapper (load_wrap_driver:11: couldn't load driver mrv8335; check system log for messages from 'loadndisdriver'
[ 241.153261] usbcore: registered new interface driver ndiswrapper
dave@dave-ubuntu:~$

---

### Post by buntunub on 2007-12-18
type 

[PHP]$iwlist scan[/PHP]

Some networks should show up. If you get nothing then your wireless is not setup. You first must identify what your wireless chipset is. type:

[PHP]$sudo lspci[/PHP]

You should see something like this:

01:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 02)

Once you have identified your card and chipset like so, then you can do your search on the forums for a guide or howto to get your card up and running.

---

### Post by browning_man9 on 2007-12-18
When I run those commands, I only get lo and eth0, which is the ethernet controller for a wired network, which I am not using. So, I guess I have to figure out how to correctly install the driver for: 

01:05.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)

Once I install this driver, I should pick up my wireless network. Am I heading in the right direction now?

DOES IT MATTER THAN I'M USING 64-BIT UBUNTU, AND TRYING TO INSTALL DRIVERS FROM 32-BIT WINDOWS??????

---

### Post by buntunub on 2007-12-19
try [this]("http://ubuntuforums.org/showthread.php?t=609654&highlight=88w8335")

Seems this guy got it all working. Im not familiar with your chipset, but if marvell is anything like broadcom, dont ever buy another thing from them again until they start to support Linux drivers.

---

### Post by buntunub on 2007-12-19
> **browning_man9 said:**
> 

01:05.0 [COLOR="Red"]Ethernet controller[/COLOR]: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)



Thats kind of weird. Wonder why it thinks your wireless card is an Ethernet NIC?

Anyway, its possible that you might have to symlink some files to get it to work on Ubuntu 64 bit, but if your not familiar with how to do that, just install the Ubuntu 32 bit and try that. 

> [ 241.146026] ndiswrapper (check_nt_hdr:153): kernel is 64-bit, but Windows driver is not 64-bit;bad magic: 010B

That kind of makes me think too that it might be a problem. Check and see if Marvell has 64 bit drivers. If they dont, thats just pathetic because its likely then that not even 64 bit Windows is supported!..

On the flip side, Ubuntu 64 bit leaves quite alot to be desired by my own experiences with it, and it does not support alot of common things like flash or Java well at all. IMO, if your set on 64 bit linux, then give another, more well developed 64 bit Linux distro a shot like SabayonLinux or maybe Fedora or Mandriva.

---

### Post by heindsight on 2007-12-19
> **browning_man9 said:**
> 
DOES IT MATTER THAN I'M USING 64-BIT UBUNTU, AND TRYING TO INSTALL DRIVERS FROM 32-BIT WINDOWS??????

That's your problem right there. You can't use 32bit drivers with a 64bit kernel. You'll have to try to find 64bit winXP drivers (which in my experience, with my Broadcom chipset based device, is extremely difficult if not impossible).

If you can't find a 64bit windows driver, then you might try to search around on the web, if you're lucky, then perhaps someone somewhere in the world is working on a native linux driver for your chipset. Otherwise, your only options would be to either install 32bit ubuntu and use ndiswrapper with your 32bit windows drivers, or go out and buy a new wifi card that does have proper linux drivers.

good luck...

---

### Post by buntunub on 2007-12-19
> **heindsight said:**
> That's your problem right there. You can't use 32bit drivers with a 64bit kernel. You'll have to try to find 64bit winXP drivers (which in my experience, with my Broadcom chipset based device, is extremely difficult if not impossible).

If you can't find a 64bit windows driver, then you might try to search around on the web, if you're lucky, then perhaps someone somewhere in the world is working on a native linux driver for your chipset. Otherwise, your only options would be to either install 32bit ubuntu and use ndiswrapper with your 32bit windows drivers, or go out and buy a new wifi card that does have proper linux drivers.

good luck...

That is certainly not true of my 32 bit ndiswrapper'd broadcom driver running on my 64 bit Ubuntu. Not sure about his chipset though.. Actually, never heard of that chipset before or that company in the wireless world. The fact that they seem to lack any 64 bit drivers is certainly NOT a good sign.

---

### Post by heindsight on 2007-12-19
> **buntunub said:**
> That is certainly not true of my 32 bit ndiswrapper'd broadcom driver running on my 64 bit Ubuntu. Not sure about his chipset though..

Really? How did you manage that? I spent months trying to get my usb dongle (with a bcm4320 chipset) working with ndiswrapper. I couldn't find any 64bit drivers for it, and everything I've read on the subject (including the [ndiswrapper faq]("http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,faq/#can_i_use_32-bit_windows_driver_in_64-bit_mode")) indicates that it's impossible to use 32bit drivers in 64bit mode. Luckily I eventually found a native driver (created by someone with the same problem, but with more time and knowledge than I have :) )

---

### Post by John Fraser on 2008-01-22
Hello. I've had exactly the same problem. I'd be really grateful for the native driver you refer to, heindsight.

All the best.

---

### Post by c21367 on 2008-05-11
[http://skd.de/e_en/support/driver_searchresults.html?navanchor=&term=typ.treiber+produkt.SK-54C1&produkt=produkt.SK-54C1&typ=typ.treiber&system=](http://skd.de/e_en/support/driver_searchresults.html?navanchor=&term=typ.treiber+produkt.SK-54C1&produkt=produkt.SK-54C1&typ=typ.treiber&system=)

is a 64-bit driver

[http://skd.de/e_en/support/driver_searchresults.html?navanchor=&term=typ.treiber+produkt.SK-54C1&produkt=produkt.SK-54C1&typ=typ.treiber&system=]("http://skd.de/e_en/support/driver_searchresults.html?navanchor=&term=typ.treiber+produkt.SK-54C1&produkt=produkt.SK-54C1&typ=typ.treiber&system=")

---

