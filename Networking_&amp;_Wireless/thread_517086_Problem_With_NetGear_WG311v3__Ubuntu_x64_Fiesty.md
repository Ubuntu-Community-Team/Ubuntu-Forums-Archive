---
title: "Problem With NetGear WG311v3  Ubuntu x64 Fiesty"
date: 2007-08-04
forum: Networking &amp; Wireless
---

### Post by bharathan100 on 2007-08-04
I am using Ubuntu 7.04 Fiesty Fawn for amd64. I use a NetGear WG311v3 network card.Initially I couldn't set up the card, then, I used this thread : [http://ubuntuforums.org/showthread.php?t=320111](http://ubuntuforums.org/showthread.php?t=320111)

to set up the card. Thanks to dkreiger, I was able to connect.  

I have a windows machine connected to a Belkin router(Connects to net with a PPPoE modem) and one dual booting XP and Ubuntu(WG311v3 is here!!). 

I discovered that I have to reboot Ubuntu to reconnect each time I switch of and switch on my router. What happens is that on switching of the router causes a disconnect(Network Monitor shows wlan0 is disconnected). On switching on the router, it doesn't reconnect.

I would appreciate help on the issue

Thanks in advance.

[COLOR="DarkOrange"][SIZE="5"][B][U]
Some Debug Data[/U][/B][/SIZE][/COLOR]
bharathan@bharathan-desktop:~$ ndiswrapper -l
wg311v3 : driver installed
        device (11AB:1FAA) present
bharathan@bharathan-desktop:~$ ndiswrapper -v
utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.20-15-generic/misc/ndiswrapper.ko
version:        1.47
vermagic:       2.6.20-15-generic SMP mod_unload 
bharathan@bharathan-desktop:~$ sudo dhclient wlan0
Password:
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:14:6c:c4:5b:3c
Sending on   LPF/wlan0/00:14:6c:c4:5b:3c
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPOFFER from 192.168.2.1
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPACK from 192.168.2.1
SIOCSIFMTU: Invalid argument
bound to 192.168.2.3 -- renewal in 2147483648 seconds.
bharathan@bharathan-desktop:~$ sudo iwconfig wlan0 essid <Ashok> channel 8bash: Ashok: No such file or directory
bharathan@bharathan-desktop:~$ sudo iwconfig wlan0 essid Ashok channel 8


















bharathan@bharathan-desktop:~$

---

### Post by bharathan100 on 2007-08-04
I am so bugged with this problem. I am sorry if this is a newbie question, I'd really appreciate the help
:(

---

### Post by bharathan100 on 2007-08-04
Restarting the networking daemon does the trick... Still Shouldn't this scan and reconnect happen automatically?
I used:
sudo /etc/init.d/networking restart

---

### Post by bharathan100 on 2007-08-04
Does anybody else have this kind of problem with NetGear?
I read up most of the other threads and most of them deal with installation issues.

---

### Post by bharathan100 on 2007-08-04
By the way, what is Network Manager??

---

