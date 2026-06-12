---
title: "dlink dwl-650 on dell latitude CPx using ubuntu 6.10 desktop live cd"
date: 2007-02-14
forum: Networking &amp; Wireless
---

### Post by ubinewbee on 2007-02-14
Greetings,

I booted the Ubuntu 6.10 desktop cd on an ancient dell Cpx and it booted fine.  After the desktop appeared, I placed in a dlink dwl-650 card in side one of its pcmcia slot.  No pop-up window showed up asking for wep information.

I then went to the graphical device manager and saw that it detected the card.  Under device tab the vendor, device, device type, and capabilities were labeled as "unknown".  Under Advanced tab there was lots of info about the pci card (I am writing from a separate pc - not sure how to have copied the info into a media which I could bring over).

Under the graphical Networking tool - there was only a modem device listed and no wireless.

I looked on [https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide#check](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide#check) and ran lshw in a terminal window.  What I saw under pcmcia:1 was a *-network with the following:
description:  DWL-650 Wireless PC  Card RevP
product:  ISL37101P-10
vendor:  D-Link
physical id:  0
version:  A3
slot:  Socket 1
below this was a *-bridge:0 UNCLAIMED, but I don't think this one is relevant.

So what I'm wondering:
1.  Does lack of complete detection has to do with me running this off the livecd?
2.  How would I enable the DWL-650 within the livecd environment?
3.  If the only way to enable it is to install it on the hard disk - I'm ok with this, but then what would I need to do to enable the card?  (it looks to me that its sort of "half" detected)

Sincerely,

ubinewbee

---

### Post by gradedcheese on 2007-02-14
Open up a terminal and run "iwconfig", if a device with wireless extensions shows up, then you're probably good to go.  There's not supposed to be any WEP pop-up (this makes sense: which access point would it ask about, right?) or anything like that.  You can also run "ifconfig" to see which interfaces are available.  I am not sure if the Live CD includes all the possible firmware files that Ubuntu comes with, so it may have to do with that.  I think my Atheros-based card doesn't work on Live CDs but works perfectly in a real installation, for example.

---

### Post by ubinewbee on 2007-02-14
Hello gradedchees,

Thank you for your response.

> **gradedcheese said:**
> Open up a terminal and run "iwconfig", if a device with wireless extensions shows up, then you're probably good to go.  There's not supposed to be any WEP pop-up (this makes sense: which access point would it ask about, right?) or anything like that.  You can also run "ifconfig" to see which interfaces are available.  


I'll try iwconfig.  I had ran ifconfig and didn't see any interfaces beyond the local one.

> 
I am not sure if the Live CD includes all the possible firmware files that Ubuntu comes with, so it may have to do with that.  I think my Atheros-based card doesn't work on Live CDs but works perfectly in a real installation, for example.

From what I read about the dwl-650 there are a couple of different chipsets and I'm not sure how to figure out what my card has.  However, from what you say - it sounds like a good idea to install ubuntu on the hard disk and see whether it is detected properly.

Thanks for your help.

---

### Post by gradedcheese on 2007-02-14
Ah, no sense in running iwconfig if ifconfig sees nothing.  Run "lspci" to see what cards are found and what chipset you have.  For example, on my PC here:

```

0a:0c.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)

```

This tells me that I have a card with the Atheros AR5212 (which is supported)

---

### Post by ubinewbee on 2007-02-14
Hi gradedcheese,

> **gradedcheese said:**
> Ah, no sense in running iwconfig if ifconfig sees nothing.  Run "lspci" to see what cards are found and what chipset you have.  For example, on my PC here:

```

0a:0c.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)

```

This tells me that I have a card with the Atheros AR5212 (which is supported)

Ok - so I went ahead and installed 6.10 on the Dell's hard disk (default install of everything).  However, I am still seeing the same issues as before with the wireless card.

When i do lspci I don't see any Ethernet controller type of lines.  However, as before - in the graphical device manager I do see the card's detection.  Any additional suggestions?

Thanks for your help.

---

### Post by drdre on 2007-02-14
Hi Ubinewbie,
I have the same card and the same response. I went even further and got the drivers from dwl for the ndiswrapper.  However, for the life fo me and 3 other much mroe experienced linuxers, we couldnt get the driver files extracted properly.   Let me know if you find a solution.

DRE

---

### Post by ubinewbee on 2007-02-15
Hello Drdre

> **drdre said:**
> Hi Ubinewbie,
I have the same card and the same response. I went even further and got the drivers from dwl for the ndiswrapper.  However, for the life fo me and 3 other much mroe experienced linuxers, we couldnt get the driver files extracted properly.   Let me know if you find a solution.

DRE

I'm going to try to re-install ubuntu from the livecd with the card in the laptop.  My next steps were going to attempt the ndiswrapper but what you indicate seems rather discouraging.

I was amazed how well Ubuntu worked right "out of the box" for the dell...only to be foiled by the pcmcia card which is a deal breaker (no internet access makes the laptop useless).  I've looked around and this seems to be quite the achilles heel for many distros.

If my install test works - I'll report back.

ubinewbee

---

### Post by ubinewbee on 2007-02-15
Well - I re-installed with the dwl-650 card in during installation and I had the same problem.  I found the following link which describes almost identically this problem:
[http://www.linuxforums.org/forum/debian-linux-help/64476-wireless-problems-newbe-linux.html?highlight=dwl-650+dell](http://www.linuxforums.org/forum/debian-linux-help/64476-wireless-problems-newbe-linux.html?highlight=dwl-650+dell)

The difference is that dmesg | grep pcmcia doesn't show those errors and the Ubuntu 6.10 kernel is 2.6.17

So...my options are:
1.  try another distro like Fedora or Simply Mephis (or perhaps something that's more laptopy)
2.  pay $250 for the 1 year of support for Ubuntu
3.  Pay redhat $179 for their desktop enterprise with 30 day of install support.

I'm going to go with step 1 for now and perhaps go with step 3 (though for $179 - I might as well look for a new laptop).

I would gladly pay $50 to get this problem resolved bad sadly - I don't see that as an option.

Bummed about Ubuntu not working out.

---

### Post by ubinewbee on 2007-02-16
Found a different solution - :guitar: 

Different wireless card....I had an older one than the dwl-650 around (an old intell wireless card) and pooft....it showed up as a device under "Networking" and it worked perfectly.

Ok - so this didn't solve the original problem about the dwl-650 BUT - it did solve my original goal of getting an old laptop to run ubuntu and connect wirelessly.


So for anyone who might be reading this and having problems with dwl-650 do yourself a big favor and:  DON'T USE THE dwl-650.  I tried the following distros (via live cds) on this Dell Cpx: Ubuntu (obviously), simply mephis, gentoo, fedora core 6 (didn't even boot), test fedora core 7 (booted fine but still no connection), and Knoppix.  None of them recognized the dwl-650.  This card has different chipsets for the same model number and it simply not worth one's time.

What should you do?
1.  Go to Best Buys or whatever electronics store with a 30 day return policy and buy 5 wireless cards.
2.  Boot up ubuntu. 
3.  Plug each card and test if it shows up as a device under networking (if it does - configure and test)
4.  Return the cards that didn't work
5.  Sell the DWL-650 on ebay or use it as a paper weight.

The above will  make your life easier without having to purchase extra support and it will show you the sheer joy of using Ubuntu "out of the box".

Good luck.

Ubinewbee

:guitar: 
:guitar:

---

### Post by lorpi on 2007-03-03
This card works fine with Ubuntu 6.06.1. How you will describe that? I got two different outputs with "lshw" in Ubuntu 6.06.1 and 6.10;

[INDENT][FONT="Monospace"]**bash on 6.06.1:**
$ lshw
     *-network
          description: Wireless interface
          product: AR5212 802.11abg NIC
          vendor: Atheros Communications, Inc.
          physical id: 0
          bus info: pci@03:00.0
          logical name: ath0
          version: 01
          serial: 00:15:e9:30:01:db
          width: 32 bits
          clock: 33MHz
          capabilities: bus_master cap_list ethernet physical wireless
          configuration: broadcast=yes driver=ath_pci ip=192.168.1.23 multicast=yes wireless=IEEE 802.11g
          resources: iomemory:e8400000-e840ffff irq:177[/FONT][/INDENT]

[INDENT][FONT="Monospace"]**bash on 6.10:**
$ lshw
     *-network UNCLAIMED
          description: Ethernet controller
          product: AR5212 802.11abg NIC
          vendor: Atheros Communications, Inc.
          physical id: 0
          bus info: pci@03:00.0
          version: 01
          width: 32 bits
          clock: 33MHz
          capabilities: cap_list
          resources: iomemory:e8400000-e840ffff irq:177[/FONT][/INDENT]

I hope you can see the differences. "lspci" has on both installs the same output:

[INDENT][FONT="Monospace"]**bash:**
$ lspci
0000:03:00.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)[/FONT][/INDENT]

Are there possibilities to get this wlan-device to work on Ubuntu 6.10?

---

