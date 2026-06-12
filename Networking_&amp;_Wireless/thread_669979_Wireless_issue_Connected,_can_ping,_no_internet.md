---
title: "Wireless issue: Connected, can ping, no internet"
date: 2008-01-16
forum: Networking &amp; Wireless
---

### Post by leingod86 on 2008-01-16
Ok, I posted another thread a little bit ago, however my problem has changed slightly and I have a better understanding of where the issues lie.

1. I can connect to my router
2. I can ping the outside world (tried Ubuntu's IP)
3. I can ping my laptop which is on the same network.
4. I cannot ping the Gateway.

I have tried to manually connect in the terminal,  and it's successful. Still no internet.

I have tried driver installation. It works. No internet.

I am using a Linksys WUSB54G wireless usb card and using the rt2500usb driver. I have a Belkin Wireless G Router. I am using WEP security.

I have a laptop which is also running Ubuntu 7.10 and it is working correctly.

My desktop's route has the following information:

Destination             Gateway         Genmask           Flags       Metric    Ref   Use   Iface
192.168.2.0       |     0.0.0.0       |  255.255.255.0   |   U         |    0     |    0  |  0 |   wlan0
0.0.0.0              |     192.168.2.1|  0.0.0.0              |   UG       |   0     |    0  |   0 |  wlan0

Any help that could be provided would be excellent and I will try to be as cooperative as possible.

Thank you.

---

### Post by leingod86 on 2008-01-17
UPDATE: Apparently I am able to download and connect to the internet. But it is ungodly slow (about 300 B/s). I'm fairly certain my drivers are installed correctly (used ndiswrapper and the sticky as a guide). I've also blacklisted IPv6 just to try it. My connection speed is fine on my laptop and when using said wireless card on my XP partition. Does anyone have any idea where I could start looking?

---

### Post by Hightide on 2008-01-17
Hi, have you checked out Kevdogs tutorial?

[http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)

:)

---

### Post by leingod86 on 2008-01-17
Yes. I've done it and it worked correctly. However, now I have horrendous connection speed (< 1 kb/s).  This is using the Update Manager by the way. Accessing websites is still impossible. I've tried disabling IPv6, and I don't believe it is (at least directly) an ISP/router issue because I have a laptop on the same network that isn't having any of my desktop's issues.

---

### Post by leingod86 on 2008-01-17
I just tried Kevdog's guide again. The final step looks as he describes it. However, when I run the command "sudo - dhclient -r wlan0" I get the message:

DHCPRELEASE on wlan0 to 192.168.2.1 (router IP) port 67
send_packet: Network is unreachable.

Could this be a security issue? Or maybe a closed off port? I ran port scanner on my IP and it came up empty.

---

### Post by Hightide on 2008-01-17
OK. I picked up this thread about wireless card problems and a possible conflict between certain drivers and network manager..  This may help

[http://ubuntuforums.org/showthread.php?t=594857](http://ubuntuforums.org/showthread.php?t=594857)

:)

---

### Post by rustybronco on 2008-01-17
> **leingod86 said:**
> I am using a Linksys WUSB54G wireless usb card and using the rt2500usb driver. 

please post the output of **lsusb**

---

### Post by leingod86 on 2008-01-17
lsusb:
Bus 004 Device 001: ID 0000:0000
Bus 005 Device 001: ID 0000:0000
Bus 003 Device 002: ID 06a3:8000 Saitek PLC
Bus 003 Device 001: ID 0000:0000
Bus 001 Device 002: ID 046d:c01e Logitech, Inc. MX518 Optical Mouse
Bus 001 Device 001: ID 0000:0000
Bus 002 Device 003: ID 13b1:000d Linksys
Bus 002 Device 001: ID 0000:0000

---

### Post by kevdog on 2008-01-17
It definitely sounds like a gateway problem -- What exactly is your LAN gateway address.

Is this correct?
0.0.0.0 | 192.168.2.1| 0.0.0.0 | UG | 0 | 0 | 0 | wlan0

What does ifconfig show?

---

### Post by leingod86 on 2008-01-17
I had to go in to work (blech) so I won't be able to check ifconfig until I get off. I'll reply with that information when I can. Thank you all for helping out.

---

### Post by rustybronco on 2008-01-17
Linksys 13b1:000d  is a wusb54g v4 with a rt2570 chipset...
*** edit*** didn't see that sorry
> I am using a Linksys WUSB54G wireless usb card and using the rt2500usb driver

---

### Post by leingod86 on 2008-01-17
Really? That could be my problem then. I was using the driver that came on the windows installation disk with the card. I figured that would be the correct one. I'll have to give that a try when I get back.

---

### Post by rustybronco on 2008-01-17
> **leingod86 said:**
> Really? That could be my problem then. I was using the driver that came on the windows installation disk with the card. I figured that would be the correct one. I'll have to give that a try when I get back.
If you are referring to me, No! you are using the correct driver, it was my fault for not reading it fully first.

---

### Post by leingod86 on 2008-01-17
Oh...well dammit...went and got my hopes up that it was a simple fix. lol

---

### Post by leingod86 on 2008-01-17
I did a little more digging around. Could the fact that I'm using the 64-bit version of Ubuntu cause this problem? If so is there a workaround?

---

### Post by leingod86 on 2008-01-17
Well, I'm back. I'm posting from my laptop and ran ifconfig on my desktop. Since I can't readily copy/paste the wall of text I got from it, is there a particular section I should post?

---

