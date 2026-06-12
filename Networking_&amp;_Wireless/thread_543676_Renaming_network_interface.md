---
title: "Renaming network interface"
date: 2007-09-05
forum: Networking &amp; Wireless
---

### Post by hrsvan on 2007-09-05
Hi, I need to change the name of my eth1 to eth0. For doing this I've used this guide;
[http://www.debianhelp.co.uk/udev.htm](http://www.debianhelp.co.uk/udev.htm)
but without luck.
the output from ifconfig:

eth1      Link encap:Ethernet  HWaddr A6:A6:D3:30:61:9B
          inet addr:10.0.0.17  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::a4a6:d3ff:fe30:619b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:744 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1104 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000
          RX bytes:465140 (454.2 KiB)  TX bytes:364799 (356.2 KiB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

and the /etc/udev/rules.d/010_netinterfaces.rules file:
KERNEL=="eth1", SYSFS{address}=="56:3b:6a:61:a0:ea", NAME="eth0"

I've found a thread on this forum about editing iftab, which looks like:
 eth0 mac 2a:e6:3c:6e:00:91 arp 1

which doesn't match the hwadress... but the hwadress seems to change everytime I reboot my computer.

---

### Post by eluzi on 2007-09-05
You may have thought of this but somehow it doesn't apply to fix your problem, but anyway: change the NIC to other slot... ?!

---

### Post by kevdog on 2007-09-05
Comment out everything first in the /etc/iftab and then reboot.  See if the interface comes up as eth0

If this doesnt work put something in the file like the following:

eth0 mac 00:12:17:35:17:10 arp 1

The MAC address can be found from ifconfig:

eth0     Link encap:Ethernet  HWaddr 00:12:17:35:17:10  

The MAC address shouldnt change.

---

### Post by hrsvan on 2007-09-10
I've tried some stuff, but what I've noticed is that the hwadress seems to change - everytime I reeboot it gets another hex;

96:41:db:d1:bb:d9
fe:49:b4:ed:85:d6
56:3b:6a:61:a0:ea
9e:e4:11:4e:92:d4
7a:c4:89:90:94:1c

One thing that does not change is when I type "arp -a" which returns the following;
? (10.0.0.1) at 00:13:49:30:8D:84 [ether] on eth0
So I tried to add this to /etc/iftab;
eth0 mac 00:13:49:30:8D:84 arp 1
which resulting in the arp -a returning
? (10.0.0.1) at 00:13:49:30:8D:84 [ether] on eth1
Still the hwadress changing.

I found this link on changing the mac-adress, but how will this help me?
[http://www.irongeek.com/i.php?page=security/changemac](http://www.irongeek.com/i.php?page=security/changemac)

---

### Post by hrsvan on 2007-09-11
Well, thanks a lot for the help... don't know what's happened, but now it seems to be working. It might have helped to make the comment in /etc/iftab. Didn't work yesterday, but letting the computer stand still through the night seems to help... anyway, just posting my outputs if it can be for any help to others;

$ cat /etc/udev/rules.d/010_netinterfaces.rules
#KERNEL="oldnameprefix*", SYSFS{address}=="MACaddress", NAME="newname"

KERNEL=="eth1", SYSFS{address}=="56:3b:6a:61:a0:ea", NAME="eth0"


$ ifconfig
eth0      Link encap:Ethernet  HWaddr C2:80:DF:4C:EE:7A
          inet addr:10.0.0.13  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::c080:dfff:fe4c:ee7a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:38761 errors:0 dropped:0 overruns:0 frame:0
          TX packets:40097 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000
          RX bytes:28694376 (27.3 MiB)  TX bytes:10011876 (9.5 MiB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:404 errors:0 dropped:0 overruns:0 frame:0
          TX packets:404 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:36569 (35.7 KiB)  TX bytes:36569 (35.7 KiB)

$ arp -a
? (10.0.0.1) at 00:13:49:30:8D:84 [ether] on eth0

---

