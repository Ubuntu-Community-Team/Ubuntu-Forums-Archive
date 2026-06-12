---
title: "Wireless on AMD64 X2"
date: 2008-07-17
forum: Networking &amp; Wireless
---

### Post by Wyer on 2008-07-17
I recently updated my computer, and now have an AMD64 duo-core processor. I wanted to try linux, so I installed the latest version of Ubuntu for amd64, but I can't get my wireless card (a Linksys WMP54GS) to work. I've tried various methods, including ndiswrapper, but have had no success, and I'm beginning to think it's because of the amd64 architecture.

Does anybody know how to get wireless working for an amd64 machine, or where the best place is to look for such help?

Thank You

---

### Post by MeeMaw on 2008-07-17
I'm not sure that it's any different for the amd64, but we still need to know what driver your Linksys wmp54gs is using (there are about 4) Please show us the output of the following 2 commands;

sudo lshw -C network

sudo iwconfig

That should get us knowledgeable about the next steps!
Don't give up!!!!  I'm sure we can get you going!
:)

---

### Post by Wyer on 2008-07-17
I left out the ethernet portion of lshw -C network as I assume you don't need that information

----------------------------------------------------------------------
lshw -C network 
----------------------------------------------------------------------

 *-network
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 7
       bus info: pci@0000:03:07.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:12:17:64:e7:35
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

------------------------------------------------------------------------
iwconfig
------------------------------------------------------------------------

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr: off   Fragment thr=2346 B   
          Encryption key: off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
-------------------------------------------------------------------------

By the way, I put on a clean install of Ubuntu just before I posted so that anything odd that happened from trying other methods would be cleared.

---

### Post by MeeMaw on 2008-07-17
OK, try this.

[http://ubuntuforums.org/showthread.php?t=201902&highlight=bcm43xx](http://ubuntuforums.org/showthread.php?t=201902&highlight=bcm43xx)

Post back any problems
:)

---

### Post by Wyer on 2008-07-17
Still no luck, these are the only differences I noticed:


step 2: rmmod bcm43xx returned ERROR: Module bcm43xx does not exist in /proc/modules


step 13: after the command: sudo ndiswrapper -i ~/folder where driver is/bcmwl564.inf

 I got: couldn't find SourceDisksFiles section - continuing anyway...

step 14: ndiswrapper -l displayed:

bcmwl564 : driver installed
	device (14E4:4320) present (alternate driver: ssb)



I noticed that my Network Settings window doesn't look exactly the same from step 20, but it's close. (might have to do with the version of Ubuntu I'm using "hardy")

I also went to System->Administration->Network Tools (it's right below Network) and next to Network Device it only shows: 

Loopback Interface (lo)

and

Ethernet Interface (eth0)


So Where do we go from here?

[edit]

I restarted, and it seems to be working for the time being... before I left, when I clicked on the nm icon, it had the title "Wireless networks" but nothing underneath it, After restarting I was my network (along with a couple neighbors') and after a couple attempts, it connected!

Thanks again for the help!

---

### Post by MeeMaw on 2008-07-18
> **Wyer said:**
> 
[edit]
I restarted, and it seems to be working for the time being... before I left, when I clicked on the nm icon, it had the title "Wireless networks" but nothing underneath it, After restarting I was my network (along with a couple neighbors') and after a couple attempts, it connected!

Thanks again for the help!

Excellent!!!!   I'm glad it's working!
(and you're welcome.)
:)

---

