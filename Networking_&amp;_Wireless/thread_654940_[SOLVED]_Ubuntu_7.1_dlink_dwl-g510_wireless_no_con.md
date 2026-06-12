---
title: "[SOLVED] Ubuntu 7.1 dlink dwl-g510 wireless no connection"
date: 2007-12-31
forum: Networking &amp; Wireless
---

### Post by steve_d on 2007-12-31
Ok, so I'm very new to linux, I just installed ubuntu last night. 

I have been trying to setup my wireless network card, a dlink dwl-g510.

I have installed the ndisgtk & associated packages, and have successfully loaded the windows driver.

Heres where the problems start (or continues as none of this was as straight forward as I thought):

the network connections panel in ubuntu shows two connections:
A wired one
and a loopback one

I have no option of using my wireless card.
I have tried the following commands and included the info:

lspci -v command (i filtered out all the non-network adapters)

02:05.0 Ethernet controller: 3Com Corporation 3c940 10/100/1000Base-T [Marvell] (rev 12)
        Subsystem: ASUSTeK Computer Inc. A7V600/P4P800/K8V motherboard
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 21
        Memory at feaf8000 (32-bit, non-prefetchable) [size=16K]
        I/O ports at d800 [size=256]
        Capabilities: <access denied>

02:0c.0 Ethernet controller: Marvell Technology Group Ltd. Marvell W8300 802.11 Adapter (rev 07)
        Subsystem: D-Link System Inc Unknown device 3b09
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 4
        Memory at feae0000 (32-bit, non-prefetchable) [size=64K]
        Memory at fead0000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>

steve@steve-ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

steve@steve-ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0E:A6:4B:EC:A1  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:21 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

If anyone knows where I should go from here, I would be most grateful. But please be as simple as possible, I have NO clue how linux functions, and the most basic of CLI's are so different even from dos I just run myself around in cirlces.

Thanks
-Steve

---

### Post by kegobeer on 2007-12-31
What is your card's revision?  Check this out:

[http://madwifi.org/wiki/Compatibility/D-Link#DWL-G510](http://madwifi.org/wiki/Compatibility/D-Link#DWL-G510)

If it's in there, you can install the madwifi drivers (I think).  I installed the development drivers and got my DWA-643 working.  It's not the same, but at this point anything is worth a shot, right?

Here's what I did to get things working:

[http://madwifi.org/wiki/UserDocs/FirstTimeHowTo](http://madwifi.org/wiki/UserDocs/FirstTimeHowTo)
[http://www.thinkwiki.org/wiki/How_to_checkout_and_install_madwifi_experimental_driver_for_ar5008](http://www.thinkwiki.org/wiki/How_to_checkout_and_install_madwifi_experimental_driver_for_ar5008)

Follow the experimental install instructions, then flip back to the first time page.  Read both before doing anything, of course.

Hope that helps.

---

### Post by steve_d on 2007-12-31
Thanks for the link,

I followed the first link, which shows that the adapter is compatable, except for a few versions. I have ver A1, on that page it says the A series is a atheros chipset. It also makes light that there is a odd ball version that uses a marvell w8300 chipset, which has no opensource support.

Unfortunately i've got the w8300... Does this mean I am only able to use the windows drivers? and seeing as they don't seem to be working, that I'm out of luck with this particular adapter?

---

### Post by kegobeer on 2007-12-31
No, I think that means the madwifi drivers should get your adapter working.  You can either install the 0.9.3.3 drivers or the experimental ones.  Give it a shot, it certainly can't hurt.  You can always uninstall the drivers (sudo make uninstall).

---

### Post by steve_d on 2008-01-02
Well, i finally got my wireless card to work, interestingly enough I just did the same thing I've been doing the last few times over again, and magico presto, it worked.

I just used the windows drivers through the GUI ver of ndiswrapper.

Thanks for the direction, although I should add that the card I have doesn't support those drivers, I would have needed an ath.. chipset, whereas i have a marvel.

Steve

---

