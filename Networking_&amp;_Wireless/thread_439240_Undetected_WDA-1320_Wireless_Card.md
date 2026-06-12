---
title: "Undetected WDA-1320 Wireless Card"
date: 2007-05-10
forum: Networking &amp; Wireless
---

### Post by _Herb_ on 2007-05-10
I just installed a D-Link WDA-1320 wireless card in a computer running Xubuntu with Feisty 7.04. Upon reboot, the Restricted Driver Manager announces that the Atheros HAL is now in use, indicating (I'm guessing) that the new card is detected at some level. However, Applications -> Systems -> Network doesn't show the card, showing only the Modem and Wired connections (both disabled).

lspci gives
01:01.0 Ethernet controller: Atheros Communications, Inc. AR5005G 802.11abg NIC (rev 01)

I'm new with wireless and have no idea what to try next. Any suggestions?

---

### Post by _Herb_ on 2007-05-11
I should add that madwifi, the driver for the Atheros chip in the card, is installed.

Any help will be greatly appreciated.

---

### Post by raymac46 on 2007-05-11
Start with this link.
[https://help.ubuntu.com/7.04/internet/C/index.html](https://help.ubuntu.com/7.04/internet/C/index.html)
If that doesn't help you more details can be found here.
[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)
Are you using WPA on your router?

---

### Post by _Herb_ on 2007-05-12
My router is set up with WEP but I think my problem is more basic.

Thanks for the link to Trouble Shooting. Even though madwifi is installed by default in Xubutu Feisty, the card driver is apparently not properly installed. I've tried various commands suggested in the fourm with no luck.

I can post the output from commands that would be useful to get things working. Any help will be greatly appreciated.

---

### Post by QwUo173Hy on 2007-05-20
I'm surprised you're having trouble with that card as a number of users reported it to work perfectly

Maybe this thread will be of use to you
[http://ubuntuforums.org/archive/index.php/t-211780.html](http://ubuntuforums.org/archive/index.php/t-211780.html)

---

### Post by _Herb_ on 2007-05-28
The reason I purchased the WDA-1320 card is that it seems to work OTB for many. Not for me.

Making some progress, however.

Here's my interfaces file:

```
$ cat /etc/network/interfaces 
auto lo
iface lo inet loopback


iface ath0 inet dhcp
wireless-essid linksys_SES_27930
wireless-key s:<ascii key is here>

auto ath0

```

and my config

```
$ iwconfig ath0
ath0      IEEE 802.11g  ESSID:"linksys_SES_27930"  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:1A:70:68:D7:3F   
          Bit Rate:54 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=31/94  Signal level=-64 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

which I think means the card is working.

However, I can't get an IP address from the wireless router, as follows:

```
$ sudo dhclient ath0

Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:15:e9:89:8a:a9
Sending on   LPF/ath0/00:15:e9:89:8a:a9
Sending on   Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 1
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

Thoughts or suggestions?

---

### Post by QwUo173Hy on 2007-05-28
Can you get the routers web page up? It's usually 192.168.0.1 or something similar. I'd also make sure that there isn't a setting in the router somewhere. My 3com router for example, detects the wireless computer, but won't let it connect until an administrator adds the MAC address of the network card to the whitelist.

It's does seem like a router problem to me. I've been there :)

---

### Post by _Herb_ on 2007-05-30
Found the problem. Thanks for the suggestion to look at the wireless router settings. It wasn't the MAC because MAC filtering was disabled. Looking more carefully at the help files and at the router settings, I realized the required WEP key was in hex while I was submitting it as ascii. Removing the "s:" from the client key caused the wireless connection to finally come alive.

Would be nice if iwconfig, dhclient or one of the other wireless routines could somehow indicate that the WEP key is invalid so I would have known where to look for my mistake.

Now on to getting sound from my speakers.

---

### Post by QwUo173Hy on 2007-05-31
Glad you got it going!

---

### Post by Techmobowl on 2008-01-04
I'm running Xubuntu 7.10 and similar to _Herb_  I got the WDA1320 because it seemed to work for everyone OTB.

In my /etc/network/interfaces file I just get:
auto lo
iface lo inet loopback


Should I type in the rest of the stuff manually?

Thanks for any help.

---

### Post by Techmobowl on 2008-01-04
Nevermind, got it working.  There must have been a conflict in the PCI bus because I moved the card to a different slot (and removed another card that may have been the conflict) and now it works.

---

