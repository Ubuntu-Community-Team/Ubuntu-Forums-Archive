---
title: "0% wireless signal strength after connection"
date: 2007-07-03
forum: Networking &amp; Wireless
---

### Post by locust on 2007-07-03
Greetings.

I have tried connecting to my wireless network using 2 different wireless usb adapters. First one was ADD-180GWU and my second one is a ASUS WL-167g.

Using 7.04 I have never managed to receive any data from my wireless network. Even though i can see my network with 80% signal strength before I connect to it, as soon as I connect the signal drops to 0% and I have no communication whatsoever with the network.

The same thing happens using the gnome network manager, ndiswrapper, wifi-radar and RuTilt

Even though I dont think it is relevant since my system recognises my adapter, here is my lsusb output:

```

lsusb
Bus 003 Device 003: ID 0b05:1723 ASUSTek Computer, Inc. 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

```

iwconfig output
```

iwconfig 
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  IEEE 802.11g  Frequency:2.437 GHz  
          RTS thr:off   Fragment thr=2346 B   
          
wlan0     IEEE 802.11g  ESSID:"ikiou"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:17:3F:4B:B4:A6   
          RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

this is the network signal when I'm roaming and connected to the network through cable, as soon as I connect to it , it drops to 0

[IMG]http://i14.tinypic.com/4kfb0oo.png[/IMG]

and a screenshot of rautil after I'm connected.

[IMG]http://i12.tinypic.com/4mwg7yf.png[/IMG]

Any help would be greatly appreciated, I bought the ASUS card because i thought it was a problem with the ADDON card, and now I'm stuck with two wireless usb cards and no wireless internet.

---

### Post by doodaad_1 on 2007-07-03
The exact same thing is happening to me except i get a DHCP failed message and my router locks up.

---

### Post by kevdog on 2007-07-03
Im going to make some assumptions

The first screen shot seems to be from gnome-network-manager
The second from the RutilT program

This suggests to me you are using a card with a ra chipset.  ra cards conflict with network manager.  It seems many of the posts recommend upgrading ra drivers from the serialmonkey site, and then some specific modifications need to be made to the /etc/network/interfaces file to get these cards to work.  Its not hard, its just very different for this particular chipset and compared to broadcom, atheros, etc. cards in general

---

### Post by locust on 2007-07-04
[http://ubuntuforums.org/showthread.php?t=400236](http://ubuntuforums.org/showthread.php?t=400236)

This thread helped me solve my problem, I'm going to try and protect my network now, I hope it is going to work.

Non protected mode works just fine now.

---

