---
title: "promiscuous mode on hawking hwl2 (zd1211)"
date: 2006-12-12
forum: Networking &amp; Wireless
---

### Post by Ryanmt on 2006-12-12
Having trouble getting wireshark working on ubuntu, it picks up my own packets but not other ones. i have the promiscus tab ticked too.

ive tried

ryanmt@penguin:~/Desktop$ sudo ifconfig wlan0 -promisc
but i just end up back at the prompt

dmesg is full of so i cant see if its done anything.
[17183172.736000] zd1211:zd1205: cmd = 8b27
[17183173.736000] zd1211:zd1205: cmd = 8b03
[17183173.736000] zd1211:zd1205: cmd = 8b09
[17183173.736000] zd1211:zd1205: cmd = 8b1d
[17183173.736000] zd1211:zd1205: cmd = 8b27

ive tried two versions of the driver
zd1211-driver-r77 and r83 both have the same thing (the later version doesnt full up dmesg though)

when i run airoscript i get this error too

ryanmt@penguin:~/Desktop$ ./airoscript-1.7RC7.sh
./airoscript-1.7RC7.sh: 35: function: not found
SIOCSIFFLAGS: Permission denied

wlan0 ZyDAS zd1211 (monitor mode enabled)
./airoscript-1.7RC7.sh: 39: Syntax error: "}" unexpected

---

### Post by tturrisi on 2006-12-12
If behind a router or wifi router then you can only sniff packets on the lan, else you'd have to hook the modem directly to the comp to sniff outside the lan, else use Kismet.  See if your card is supported by kismet: (unlikely as zd linux drivers are buggy, butmay work if lock to a specific channel)  [http://www.kismetwireless.net/documentation.shtml](http://www.kismetwireless.net/documentation.shtml)

---

