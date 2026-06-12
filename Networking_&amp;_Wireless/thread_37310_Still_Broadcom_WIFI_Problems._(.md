---
title: "Still Broadcom WIFI Problems. :("
date: 2005-05-26
forum: Networking &amp; Wireless
---

### Post by zoulman on 2005-05-26
Hi everyone,

first off let me just say , I love Ubuntu! But there is one thing missing (my wifi will not work).

Well I tried all the ndiswrapper HOW-TOS in the forum and still nothing. Well that is to say gnome can see wlan0 in the networking after "modprobe ndiswrapper" but it doesn't find any thing when scanning. I have a broadcom card, one that uses the bcmwl5 driver.

Please help me, I don't know where to go from here.  :-?

---

### Post by Alexander Kirillov on 2005-05-26
[QUOTE=zoulman]Hi everyone,

first off let me just say , I love Ubuntu! But there is one thing missing (my wifi will not work).

Well I tried all the ndiswrapper HOW-TOS in the forum and still nothing. Well that is to say gnome can see wlan0 in the networking after "modprobe ndiswrapper" but it doesn't find any thing when scanning. I have a broadcom card, one that uses the bcmwl5 driver.

Please help me, I don't know where to go from here.  :-?[/QUOTE]
 What is the output of 
sudo ifup wlan0

---

### Post by zoulman on 2005-05-27
[QUOTE=Alexander Kirillov]What is the output of 
sudo ifup wlan0[/QUOTE]

Internet Systems Consortium DHCP Client V3.0.1
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/wlan0/00:0b:6b:4a:74:ae
Sending on   LPF/wlan0/00:0b:6b:4a:74:ae
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 16
...
...

Keeps on doing the last part. ](*,)

---

### Post by Alexander Kirillov on 2005-05-27
[QUOTE=zoulman]Internet Systems Consortium DHCP Client V3.0.1
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/wlan0/00:0b:6b:4a:74:ae
Sending on   LPF/wlan0/00:0b:6b:4a:74:ae
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 16
...
...

Keeps on doing the last part. ](*,)[/QUOTE]
 I usually get this when the signal is low. But at least, it seems to show that all the drivers etc are isntalled correclty.

---

### Post by /usr/err on 2005-06-02
I'm having the exact same problem with a Broadcom BCM4306.  I used to have a D-Link router with this issue when I first started trying to get wireless to work on my laptop with Ubuntu about 6 weeks ago, but I've since replaced it (for other reasons) with a Linksys WRT54GS and I'm still having the same problem, so I'm assuming it has to be the driver setup with ndiswrapper but I can find no error output and I followed the HOWTO steps with no problems, it installed just fine and is recognized by the system... it just doesn't work.

```
$ dmesg
ACPI: PCI interrupt 0000:00:0c.0[A] -> GSI 18 (level, low) -> IRQ 18
ndiswrapper: using irq 18
wlan0: ndiswrapper ethernet device 00:90:96:8a:e7:5a using driver bcmwl5
wlan0: encryption modes supported: WEP, WPA with TKIP, WPA with AES/CCMP
ndiswrapper: driver bcmwl5 (Broadcom,06/13/2003, 3.20.23.0) added
```

```
$ sudo ifup wlan0
ifup: interface wlan0 already configured
```
(Note that doing the same thing for 'eth0' has the same message.)

```
$ sudo iwlist wlan0 scan
wlan0     No scan results
```

I've defined an essid with iwconfig (originally did all this with the Gnome tools with the same results); the router is setup right now to not have any encryption on it just so I can get it to 'work' and then bother with that, so I'm confused as to why it won't connect.  The laptop is not seeing any wireless connections in the area (under WindowsXP, I can see at least 2 other wireless connections from neighbors as well as my own and the connection to mine works just fine under Windows, so it is not a router problem -- originally, I was not broadcasting my ssid given I didn't have encryption turned on, but even turning on broadcasting to test this issue, I get the exact same results).

---

### Post by zoulman on 2005-06-03
Bump...  :???:

---

### Post by Toddy on 2005-06-03
When I was setting up wireless, I too was experiencing the same "DHCPDISCOVER..." scenario.  I then read something about Ubuntu not being able to handle "shared" authentication.  Once I changed my router to "open" authentication, everything worked.

---

### Post by aurelien on 2005-06-03
I had the same problem a few days ago. After a modprobe ndiswrapper, I see the wlan0 interface, but scanning leads  to no result. 
I found the solution in [http://www.ubuntuforums.org/showthread.php?t=25683&highlight=radio+state](http://www.ubuntuforums.org/showthread.php?t=25683&highlight=radio+state), it consists in changing the radio state value in the ndiswrapper configuration file. 
Now everything goes well

---

### Post by spd106 on 2005-06-04
[QUOTE=zoulman]Bump...  :???:[/QUOTE]
 Hi, have you tried a different driver?
Check the ndiswrapper website list
[http://ndiswrapper.sourceforge.net/phpwiki/index.php/List?PHPSESSID=945bcecf080b67c5c1c9bd4d1fbf37cd](http://ndiswrapper.sourceforge.net/phpwiki/index.php/List?PHPSESSID=945bcecf080b67c5c1c9bd4d1fbf37cd)
Double check it is for the correct rev of the card
```
$lspci
```

Check the driver is installed fully
```
$ndiswrapper -l
```

Compile the latest version of the ndiswrapper module.

Go over the /etc/network/interfaces file again just to be thorough.

Turn off any encryption (wep, wpa etc) just to check, make sure the ap is set to broadcast essid. Go over any firewalls to see if there's any probs there.

You could try manually seting all the details, if dhcp is a problem...

I suppose you've been over all these before, but I hope some of this helps.

---

