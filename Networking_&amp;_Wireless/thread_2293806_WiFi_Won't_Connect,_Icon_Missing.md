---
title: "WiFi Won't Connect, Icon Missing"
date: 2015-09-07
forum: Networking &amp; Wireless
---

### Post by Y.P._Delta on 2015-09-07
I woke up today to find that the WiFi on my laptop was no longer working. That's cool, happens every now and again, I've a quick list of things that typically makes it work again. The odd thing, though, was that my phone, tablet, desktop, and media centre were all connected just fine, and it was only my laptop that wouldn't connect. Desktop, laptop, and media centre are all running 14.04.

The laptop was locked but not off or hibernating/sleeping, and actually, the icon was still showing that I was connected to the router, but two extension icons in Chromium which are greyed out when not connected to the internet were, indeed, greyed out. No sites would load, either. Okay, I've seen something similar to this before, but it usually affects every device, not just one. Whatever, I'll get to work.

First thing I did was disconnect the computer from the WiFi, wait a bit, then reconnect. It connected back to the router just fine, but again, nothing worked. Next step was to reset the router itself. Everything disconnected, obviously, and then reconnected when the router was plugged back in -- except, again, the laptop.

Now, usually with issues like this, this is as far as I get before everything starts working again. But since that didn't happen, the only thing I could think to do was to reboot the laptop. So that's what I did. When it restarted, I saw that the Redshift icon was missing. I went to start it but it was nowhere to be found. When I tried to start it from the terminal, it said it wasn't installed. Um...okay? So I tried to install it, but nothing would happen, and that's when I noticed that the WiFi icon was also missing, and it took the actual connection itself with it.

I've attempted to connect through Network Connections, but that didn't work (says I'm still connected to the router, but that doesn't really help me when the internet itself won't work on here).

Help?

*tl;dr - Computer disconnected itself from WiFi in the night, wouldn't reconnect in the morning, reboot took away the icon (among others), still won't connect.*

---

### Post by howefield on 2015-09-08
Thread moved to the "*Networking & Wireless*" forum for better support.

---

### Post by Bucky Ball on 2015-09-08
Sounds like you are only checking in Chromium whether it is connected. Open a terminal and ping the router. You need the router IP for this. This will tell us whether you are communicating with the router. If so, that does not mean you are connecting to the outside world, just your router, your LAN or local area network.

If the router IP is 192.168.0.1, then:

```
ping 192.168.0.1
```

Do you get a ping time or the fact that can't connect? If you get a ping time, try:

```
ping google.com
```

That will tell us if you are getting the WAN. Then run this and post back the output for starters:

```
sudo lshw -C network
```

Post the output between code tags (see last link in my signature). Thanks.

---

### Post by kc1di on 2015-09-08
also if the ping does not work, try this in a terminal ```
inxi -Fxz
```
post the output here so we can see what your using.

---

### Post by Y.P._Delta on 2015-09-08
Thanks very much for your help. I've actually checked the connection with Chromium, Chrome, Firefox, Skype, etc., as well as checking for updates and all that. No dice in any fashion. I'm definitely connected to the router though, as I can access the router control panel and I'm showing as connected under Network as well. Also, when Googling around for solutions before I posted here, I found a couple threads with instructions on pinging. While these situations didn't quite fit mine, I pinged some of the addresses listed in those forums, and each were successful. Despite this, I still did as you asked, and I pinged both my router and Google, and both of these were, again, successful. The output of the final code you asked me to run is:

```

  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 05
       serial: a0:1d:48:6f:cd:65
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8105e-1.fw latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:43 ioport:2000(size=256) memory:f0004000-f0004fff memory:f0000000-f0003fff
  *-network
       description: Wireless interface
       product: AR9485 Wireless Network Adapter
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: wlan0
       version: 01
       serial: 40:f0:2f:0f:93:f1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.16.0-46-generic firmware=N/A ip=192.168.1.21 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:f0200000-f027ffff memory:f0280000-f028ffff

```

Hopefully this helps. It's strange that I can ping the outside world and get a response, but can't actively connect for what I want to do. Also, could this be at all related to the fact that the wireless indicator went AWOL at the same time as the actual connection itself, or is that just an odd coincidence? I've never had a problem with the indicator disappearing before now, and all WiFi issues I've had up until this point could always be traced back to the router (it's one that drops connections every few days and has to be rebooted, so I have it on an auto refresh), and always affected every device.

---

### Post by Bucky Ball on 2015-09-08
You have this card: AR9485 Wireless Network Adapter

The correct driver appears to be installed. Will ponder.

---

### Post by kc1di on 2015-09-09
I have the same wireless card as you have and have had no problems. do you by any chance have a firewall enabled that might restrict incoming traffic either at the router or on your ubuntu machine?

If that is not the case i'd purge and re-install the driver just in case.

---

### Post by Y.P._Delta on 2015-09-09
I don't have any firewall, not that I'm aware of, anyway...as I said in the original post, this just happened overnight on its own. It was working before I went to sleep, and when I woke up, the signal was gone. Rebooting also took away the indicator icon for the WiFi as well as Redshift, for some reason, and disabled Redshift as well. (And I apparently no longer have redshift-gtk installed, either.) Would the driver affect those, somehow?

Also, how exactly would I go about purging and reinstalling the driver?

---

### Post by Y.P._Delta on 2015-09-10
I hope bumping a thread here isn't in poor taste, but this is quite distressing. My main questions currently are:


[LIST=1]
[*]How would I go about purging and reinstalling my wireless driver?
[*]If that's not the best solution to this problem, what could it be?
[*]How, if at all, does this relate to the missing indicator icons?
[/LIST]

---

