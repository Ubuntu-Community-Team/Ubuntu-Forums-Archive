---
title: "Belkin F5D8001"
date: 2006-12-05
forum: Networking &amp; Wireless
---

### Post by Bartender on 2006-12-05
The Belkin F5D8001 PCI wireless card doesn't show up in the Hardware Support list.  Has anyone had any success?  A friend has one of these in his upstairs PC and can't get it to participate on his wireless network.

---

### Post by hey_ygbsm on 2007-01-18
Same problem for me. I'm currently researching a workaround using madwifi or Ndiswrapper, however, I'm a Linux Newbie and have limited experience with compiling/installing XP drivers. On the 'Up' side, I've had pretty fast throughput with the Belkin N1 setup in Windoze.

---

### Post by hey_ygbsm on 2007-01-22
Quick update.  Using the net5416.inf Belkin driver and ndiswrapper, I was able to connect in open mode to my Belkin N1 router.  However, I have no intention of operating my wireless network unsecured.  So, my Plan-B was to backup and install the madwifi driver and give it a try.  Still bumbling through the initial stages of adding the correct repositories and learning bash commands. Looking for the 'Ubuntu/Debian-For-Dummies' Tutorial on downloading/extracting/compiling madwifi.  Can somebody throw me a bone over here?

---

### Post by hey_ygbsm on 2007-01-24
Hello again.  After much gnashing of teeth & online research, I can report the following:
- As of Jan 2007, there is no current madwifi driver support for the Atheros AR5008 chipset contained in our Belkin F5D8001 adapter. Not sure about DriverLoader, but I suspect nobody has published a workable linux-based driver for this chip yet.
- Ndiswrapper + wpa_supplicant is the best workaraound for the moment.
- Instead, I chose to remove this card & use it in a Windoze computer. I installed a linux-supported NIC found on this database: [http://linux-wless.passys.nl/](http://linux-wless.passys.nl/).  
- I'm now using the Belkin F5D7000 v5000 which worked right-out-of-the-box.  Although it's a less capable card (54 Mbps) it was a snap to install & works beautifully with Network Manager. I was online in minutes with no stalls or hiccups.
- If I had more computer downtime available, I might have opted for a faster, 108 Mbps, Atheros-based, linux-supported card such as the Netgear WG311T or D-Link G520
- Hope this post helps other folks with similar F5D8001 issues
Cheers!

---

### Post by Spr0k3t on 2007-02-01
The AR5008 chipset is starting to become very common across laptops and desktops alike.  I've seen the chipset used in a USB adapter (one of the first draft-n designs) and in several PCI cards.  The MacBook Pro now uses this chipset and I believe the new airport uses it as well.  I have a DLink DWA-542 which also uses this chipset.  So I believe there will be demand for the driver support.  I've donated to the NDISWrapper project with a request to support this chipset.

---

### Post by brucedixon on 2007-11-19
So near and yet so far.  My wife wants the ethernet cable off the floor and I really don't feel like pulling cable through the walls.  I just did a clean install of Ubuntu Studio 2.6.22-14-rt, Gutsy Gibbon I guess and pulled the ndiswrapper GUI off Synaptic to work with the Belkin Windows driver.

This one seems to have the AR5416 Atheros chipset, not the AR5008 others have referred to in this thread.

Did not see any instructions for how to set up the GUI, but a "Windows wireless drivers" icon appeared at the bottom of System-Administration.  It prompted me to select the same .inf file I use for the Windows setup, and the rest was very straightforward.

I am used to using a 128-bit encryption key, but it did not seem to let me enter that many digits.  When I entered a 64 bit key I did not connect either.  I wiped out the password and that did not seem to work.

I did 

[INDENT]sudo wlan0 up[/INDENT]

and 

[INDENT]sudo iwlist scanning[/INDENT]

and it saw the interface but got no IP address.

I rebooted and now the interface seems to have acquired an IP address, so I know I ought to be close. 

[INDENT]bruce@ogun:~$ sudo ifconfig wlan0 
wlan0     Link encap:Ethernet  HWaddr 00:11:50:F7:E9:4B  
          inet addr:192.168.2.152  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::211:50ff:fef7:e94b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:44 errors:0 dropped:0 overruns:0 frame:0
          TX packets:25 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8180 (7.9 KB)  TX bytes:4123 (4.0 KB)
          Interrupt:23 Memory:f8400000-f8410000[/INDENT] 

encryption is off.  My Belkin N-1 wireless F5D8001 wireless interface has an address.  But when I pull the ethernet cable I am alone, disconnected from the net.  So close.  And yet so far.

Does anyone have an idea what the problem might be?

bd

---

