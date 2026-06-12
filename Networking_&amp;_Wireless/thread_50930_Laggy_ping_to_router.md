---
title: "Laggy ping to router?"
date: 2005-07-21
forum: Networking &amp; Wireless
---

### Post by dbcoder on 2005-07-21
Here is my problem:

When I boot into ubuntu, I already have lag to my router.  I ping my router and it reports back with +1000ms ping times.  My internet access is terribly slow too.

I can fix it by doing the following
ifconfig eth0 down
ifconfig eth0 up
dhclient eth0

But after a few minutes the ping will just come back.  This doesn't happen with any other machines, and this machine doesn't run into this problem in windows.

Any help would be greatly appreciated.

---

### Post by gruepig on 2005-07-22
Have you tried rebooting your router?  (It might not fix anything, but it's worth a try.)

---

### Post by dbcoder on 2005-07-22
Yep, I have.

---

### Post by gruepig on 2005-07-22
Are you getting any errors?  Run 'ifconfig -a' and look for TX and RX errors and collisions, run 'dmesg' and look at the last few lines of output, and check the logs (/var/log/syslog, /var/log/daemon.log, etc.).

Post the output of 'ifconfig -a' and 'route -n' (or 'netstat -rn').

Also, is it possible that you have multiple DHCP processes running or something else which could be interfering?  And if you have a firewall enabled (iptables), you might want to disable it for testing purposes.

---

### Post by dbcoder on 2005-07-22
Well, this is a stock install of ubuntu, but I'll get on the machine and try it out.

---

### Post by dbcoder on 2005-07-22
ifconfig -a
```
eth0      Link encap:Ethernet  HWaddr 00:08:A1:0B:C2:AA
          inet addr:192.168.0.193  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::208:a1ff:fe0b:c2aa/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:153 errors:26 dropped:0 overruns:0 frame:0
          TX packets:145 errors:1 dropped:0 overruns:1 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:129975 (126.9 KiB)  TX bytes:18666 (18.2 KiB)
          Interrupt:18 Base address:0xe800
``` 

dmesg pertaining with the network
```
IPv6 over IPv4 tunneling driver
eth0: no IPv6 routers present
``` 

Nothing suspicous in the logs

Kernel Routing Table
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0
```

---

### Post by gruepig on 2005-07-22
[QUOTE=dbcoder]
```
 RX packets:153 errors:26 dropped:0 overruns:0 frame:0
          TX packets:145 errors:1 dropped:0 overruns:1 carrier:0
          collisions:0 txqueuelen:1000

``` [/QUOTE]

Well those receive errors (and the transmit error and overrun) definitely indicate a problem.  I'm not sure exactly what though.  Try turning off IPv6 support.  To do so, find the line in /etc/modprobe.d/aliases that references ipv6 and change it to off as per  [http://ubuntuforums.org/archive/index.php/t-6841.html](http://ubuntuforums.org/archive/index.php/t-6841.html).

If that doesn't do it ....What kind of ethernet card do you have, and what drivers/module does it use?  If it's a PCI card, run 'lspci' to get hardware information; other information should be available from 'dmesg' and perhaps 'lsmod'.  Is it possible you have some sort of hardware conflict or a bad ethernet card? Can you swap it with a different ethernet card?  (Also a different ethernet cable, though since it works in Windows it's hard to see how this could be the problem).

---

