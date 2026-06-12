---
title: "Cannot get WG311TNA to connect to network"
date: 2005-11-06
forum: Networking &amp; Wireless
---

### Post by cajunaggie on 2005-11-06
I gave up on my Belkin USB drive and exchanged it for a Netgear WG311TNA PCI wireless network card. I installed it in WinXP first to make sure there were no underlying issues with routers and it works beautifully (I'm using it to post this actually). Next I pulled the drivers from the installation CD of the card and ndiswrapper-utils from Badger installation CD and followed it to no avail. Then I followed the instructions posted here [https://wiki.ubuntu.com/WiFiHowto]("https://wiki.ubuntu.com/WiFiHowto") and couldn't connect to the internet. I ran the setup again and copied the output I got here.

After entering iwconfig at the terminal I got this:
```

lo     no wireless extenstions
ath0   IEEE 802.11 ESSID:"CUNNINGHAM"
Mode:Managed Frequency Frequency:2.462GHz Access Point: 00:00:00:00:00:00
Bit Rate:1 Mb/s TX-Power:18 dBm Sensitivity=0/3
Retry:off RTS thr:off Fragment thr:off
Power Management:off
Link Quality=0/94 Signal level=-95 dBm Noise level=-95 dBm
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 invalid misc:0 Missed beacon:0

sit0  no wirless extensions
```

I tried pinging it and go this:
```
connect: Network is unreachable
```

Just for grins I tried sudo if up ath0 to see if anything would happen and I got this:
```

There is already a pid file /var/run/dhclient.ath0.pid with pid 0
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium
All rights reserved
For info, please visit http://www.isc.org/products/DHCP

sit0: unknown hardware adress type 776
sit0 unknown hardware address type 776
Listening on LPF/ath0?00:0f:b5:f8:1b:44
Sending on LPF/ath0?00:0f:b5:f8:1b:44
Sending on  Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 4
No DHCPOFFERS recieved
No working leases in persistent database - sleeping.

```

If it helps here are the contents of my etc/network/interaces file, minus the commented-out sections:
```
auto lo
iface lo inet loopback


iface ath0 inet hdcp
wireless-essid Cunningham
wireless-key: [I censored the key number. I don't trust y'all *that* much;)  
]

autho ath0
```

I have no idea what is going on here. I know it's broke, I just don't know why. Can anyone explain to me what's going on, or, better yet, tell me how to fix it? I'd much rather use Linux than WinXP for the net.

---

### Post by Lambert on 2005-11-06
At the top panel did you try going into System>Administration>networking

You look like you've set your network config. Just highlight the wireless interface in the list and click on activate. If it doesn't connect click on properties and double check your settings.

If you're using wpa instead of wep it's a little more difficult. If you're using wpa it's a lot more difficult to get working if at all. I had to back down to wep encryption to get my card to work.

---

### Post by audax321 on 2005-11-06
Well you have some issues with your /etc/network/interfaces file. Try this exactly:

> 
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map ath0

# The primary network interface

iface ath0 inet dhcp
wireless-essid Cunningham
wireless-key #####################

auto ath0


Specifically there is no : after wireless-key, it's dhcp not hdcp, and auto ath0 not autho ath0.

Give that new file a try and replace ############ with your wirless-key.

---

### Post by cajunaggie on 2005-11-07
[QUOTE=Lambert]At the top panel did you try going into System>Administration>networking[/QUOTE]

That was the first thing I tried. The card itself is detected, under the ath0 label and I clicked the activate button and it said it was active. Apparently it just doesn't want to go to the network.

---

### Post by cajunaggie on 2005-11-07
I tried your remedy audax321. No dice, still not getting through to the net. What other information would be useful for to solve this here dilemna?

---

### Post by audax321 on 2005-11-07
Not sure, but with my wireless card (intel 2200) I had better luck bringing it up and down using ifup and ifdown (but this was on Hoary). Do you use that or the System > Preferences > Networking?

Try this:
  sudo ifdown ath0
  sudo ifup ath0

If that doesn't work, I'm stumped. Sorry. :confused:

---

### Post by cajunaggie on 2005-11-07
I tried both GUI and the command line sequences, no response. Meh, don't worry, someone knows the answer.

---

### Post by cajunaggie on 2005-11-09
[QUOTE=audax321]Well you have some issues with your /etc/network/interfaces file. Try this exactly:



Specifically there is no : after wireless-key, it's dhcp not hdcp, and auto ath0 not autho ath0.

Give that new file a try and replace ############ with your wirless-key.[/QUOTE]

Tried it with no response. I'm still getting the same messages. Other suggestions?

---

