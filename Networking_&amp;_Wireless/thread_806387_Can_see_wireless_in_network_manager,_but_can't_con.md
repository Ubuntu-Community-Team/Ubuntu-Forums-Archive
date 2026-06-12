---
title: "Can see wireless in network manager, but can't connect to any of them"
date: 2008-05-24
forum: Networking &amp; Wireless
---

### Post by dpick on 2008-05-24
I'm running 8.04 with a Linksys wmp54gs
Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
I installed b43-fwcutter and now I can see every network in range and the signal strength,  but I can't connect to any of them. Any ideas? Thanks

---

### Post by spd106 on 2008-05-25
Could this be a range issue? Can you try it closer to the Access Point? 

While the b43 devs are doing a great job reverse engineering the wifi driver it still doesn't get anywhere near the Windows driver for range or speed yet.


Also check that the AP is set to broadcast it's SSID and that you have the right kind of encryption selected when you enter the key.

---

### Post by dpick on 2008-05-25
There is no encryption so thats not the problem, and the computer is about 3 feet from the router, so I don't think thats the issue either.

---

### Post by spd106 on 2008-05-26
Try looking in the syslog for error messages or maybe a clue as to where it's failing. 

You can access the logs through the System -> Admin -> System Log program or at /var/log/syslog.

---

### Post by vault_guard on 2008-05-26
Hi - I'm having the same trouble. I've gone through about a billion threads trying to come up with a decent solution. There is not a range problem on my network either - I'm about 10 feet from my AP, but it's still not connecting. When I look at my system logs at "connection time" I get the info:

NetworkManager: <info> Removing wireless (802.11) device 'eth1'.
MetworkManager: <info> Deactivating device eth1.
kernel: [163018.36000] ADDRCONF(NETDEV_UP): eth1: link is not ready

Which then, the log proceeds to tell me:

dchlient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
(repeated 4 times, at with different interval numbers)
avahi-autoipd(eth1[10521]: Found user 'avahi-autoipd' (UID 105) and group 'avahi-autoipd' (GID 113).
(continues with less important details - I assume)
avahi-autoipd(eth1)[10521]: Starting with address 169.265.6.172

I'm assuming the address starting with the 169 is similar to the Windows local address being part of a loopback. It's assigning an IP, but it's not one that goes through my network router.

I installed WICD, which detects several wireless networks in my neighborhood, but will not, however connect to any of them. I have my proper credentials to my network here at home, but I still can't connect to it. When I try, the system log comes back with:

kernel: [4213848000] ADDRCONF(NETDEV_UP): eth1: link is not ready

I don't understand that message. Do I need to go in and adjust a hardware setting?

My computer is a Dell Inspiron 1150 laptop:
Broadcom 4306 802.11b/g Wireless LAN controller (not sure official name)
Broadcom 4401 100Base-T LAN Adapter

---

### Post by mapes12 on 2008-05-26
Have a look around here:

[https://help.ubuntu.com/community/WifiDocs](https://help.ubuntu.com/community/WifiDocs)

Loads of good info to sort out wireless.

:guitar:

---

### Post by vault_guard on 2008-05-26
Ok -

My dad and I looked at the problem and he remembered a solution that worked on another system. Our AP doesn't support IPv6, so we had to change a setting and use a static IP. The minute I changed that setting, it went right in. :) 

How about that?!

---

### Post by Nixie Pixel on 2008-11-04
I am having a similar issue in 8.10 - is there a workaround other than setting a static IP address?  If I try to connect to a free public network, I have no idea what IP address range to use...

---

### Post by Nixie Pixel on 2008-11-04
Well, nevermind - for some reason after pushing the wireless button to turn it off and on, then rebooting, I was able to connect.

I'll just cross my fingers and hope this continues...

---

