---
title: "Wireless DHCP woes"
date: 2006-07-19
forum: Networking &amp; Wireless
---

### Post by TrafficJan82 on 2006-07-19
Hi all,

I'm relatively new to Linux, tried Ubuntu a while ago and abandoned it for Fedora, mostly because networking worked better in Fedora. When I read about Breezy, I decided to give it a shot again and was absolutely impressed: clean, easy to use, everything worked, including networking, right out of the "box" (if there was one).

Some background: I'm using a laptop with a wireless card and want to switch between profiles. I started with just one wireless network at home, the applet worked like a charm and I got connected with WEP 128 bit encryption. Then I took the computer for a walk, tried to connect to a different network and installed network manager since it's easier to use. NM didn't let me connect to a different wireless network (also WEP), so I got rid of it again. Now, back at home, suddenly nothing works anymore, be it Ubuntu's Applet or network manager - it seems none of them can get an IP via DHCP from the router anymore. To make sure it's not something I messed up, I tried the LiveCD, which used to work like a charm and - nothing, doesn't work anymore. I reinstalled Ubuntu, again no luck. Needless to say (even if I hate to admit it), the card works just fine in Windows.

I've tried entering the key in HEX, manually editing all the settings, using WifiRadar to connect, using Ubuntu's applet, all no good. The only way I can get it to work is by turning off WEP, but I don't want to do that. After spending the last week weeding through the forums here with no answer, I decided to post myself.

Does anyone have a clue what's going on here? Anybody else with a similar problem?

It's not the card, by the way: Cisco wireless card, fully compliant and - as mentioned before - used to work, no problems.

Any help would be amazing, I'm about to get the sledgehammer out or (even worse!) move back to Windows (nah, just kidding).

TrafficJan82

---

### Post by x64Jimbo on 2006-07-19
Just a hunch - do you have the WEP key exchange set to "Shared" in your router? If so, you should either revert to "Open" or do:
iwconfig <interface> essid <SSID> key <key> restricted

---

### Post by TrafficJan82 on 2006-07-19
It's on open, so that's not it. Thanks for the quick reply!

---

### Post by x64Jimbo on 2006-07-19
Have you tried configuring the interface from iwconfig? I know it's archaic and dos-like, but the CLI is often the best way to do something that doesn't work quite well enough in the graphical mode. 
sudo iwconfig <interface> essid <SSID> key <key>
sudo dhclient <interface>

---

### Post by TrafficJan82 on 2006-07-19
Here's what I get:

```
jan@jan-laptop:~$ sudo dhclient eth1
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/eth1/00:40:96:39:31:40
Sending on   LPF/eth1/00:40:96:39:31:40
Sending on   Socket/fallback
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 2
No DHCPOFFERS received.
Trying recorded lease 192.168.0.100
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.

--- 192.168.0.1 ping statistics ---
1 packets transmitted, 0 received, +1 errors, 100% packet loss, time 0ms

No working leases in persistent database - sleeping.

```

It does work if I have the ethernet cable plugged in, but that's not what we want, obviously.

---

### Post by x64Jimbo on 2006-07-19
> **TrafficJan82 said:**
> Here's what I get:

```
jan@jan-laptop:~$ sudo dhclient eth1
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/eth1/00:40:96:39:31:40
Sending on   LPF/eth1/00:40:96:39:31:40
Sending on   Socket/fallback
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 2
No DHCPOFFERS received.
Trying recorded lease 192.168.0.100
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.

--- 192.168.0.1 ping statistics ---
1 packets transmitted, 0 received, +1 errors, 100% packet loss, time 0ms

No working leases in persistent database - sleeping.

```

It does work if I have the ethernet cable plugged in, but that's not what we want, obviously.
change that command to sudo dhclient wifi0

---

### Post by TrafficJan82 on 2006-07-19
Same result, as follows:

```
jan@jan-laptop:~$ sudo dhclient wifi0
Password:
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/wifi0/
Sending on   LPF/wifi0/
Sending on   Socket/fallback
DHCPDISCOVER on wifi0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wifi0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wifi0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on wifi0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wifi0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wifi0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on wifi0 to 255.255.255.255 port 67 interval 1
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

---

### Post by afrinspray on 2006-07-19
I had the same issues until I changed my key to 64 bit and ascii in the router. 

After that, everything worked perfectly.  I have no idea why :-k  So try that.

---

### Post by TrafficJan82 on 2006-07-20
Thanks for the idea, it didn't work, but got me on the right track. Here's what I tried:

-64 bit ASCII: no luck
-no encryption: works like a charm
-128 bit ASCII: no luck
-128 bit HEX: VOILA! it works!

Why? No idea. Ascii used to work just fine before, now it decided to stop working. Oh well, at least it works. I guess the moral of the story is, try all options.

Thanks everyone for your help. I'll be back once it stops working again (tomorrow?).

---

### Post by x64Jimbo on 2006-07-20
I've never had any luck whatsoever getting ascii keys working in Linux and always assume that I will be typing in HEX. From now on, I would imagine that would be your best bet.

---

