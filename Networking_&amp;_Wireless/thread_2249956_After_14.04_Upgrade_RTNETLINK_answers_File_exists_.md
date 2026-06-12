---
title: "After 14.04 Upgrade: RTNETLINK answers: File exists Failed to bring up eth0"
date: 2014-10-25
forum: Networking &amp; Wireless
---

### Post by marc40 on 2014-10-25
Hi,

this issue came up here before in other posts but none of the supplied solutions worked for me as I did not have the related problems. So after hours of googling and troubleshooting I try my luck here and hope for someone smart to point me into the right direction :-).
I upgraded my Ubuntu 10.04 LTS (server) to 12.04 (and later on to 14.04) and after the upgrade Ubuntu aparently cannot start networking any more and boots without full networking.
Networking after boot looks like this:
```
root@thor:~# ip link:

1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN mode DEFAULT group default 
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
2: eth0: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state [COLOR=#ff0000]**DOWN **[/COLOR]mode DEFAULT group default qlen 1000
    link/ether 00:1f:d0:9b:17:70 brd ff:ff:ff:ff:ff:ff

root@thor:/etc# ifconfig -a
eth0    Link encap:Ethernet  HWaddr 00:1f:d0:9b:17:70  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:41 errors:0 dropped:0 overruns:0 frame:0
          TX packets:41 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2448 (2.4 KB)  TX bytes:2448 (2.4 KB)

```

-> only the lo interface is up.
When manually trying to ifup eth0 I get the following error:
```
RTNETLINK answers: File exists 
Failed to bring up eth0.

```

Network Settings are configured via /etc/network/interfaces:

```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.1.4
netmask 255.255.255.0
gateway 192.168.1.1
dns-nameservers 192.168.1.1

```

I am running the server version without X so I do not have network-manager installed. 
Trying to restart networing with /etc/init.d/networking restart fails as well.

However, by running [FONT=courier new]dhclient eth0[/FONT] the interface comes up. ifconfig then shows eth0 as being up and network connectivity is given:
```
root@thor:/etc# ifconfig
eth0    Link encap:Ethernet  HWaddr 00:1f:d0:9b:17:70  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          [COLOR=#ff0000]**UP **[/COLOR]BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo ... 
```

However, a strange thing I noticed then was that the server now apparently has two active IP addresses, .4 and .49. I noticed that when doing an nslookup on the hostname from my desktop box. It returned both adresses and the host responds on both adresses to ping and services like apache and ssh bind to both IPs. 
```
C:\Users\>nslookup thor
Server:  fritz.box
Address:  192.168.1.1

Name:    thor.fritz.box
Addresses:  192.168.1.4
          192.168.1.49

C:\Users\>arp -a
Interface: 192.168.1.220 --- 0xa
  Internet Address       Physical Address     Type
  192.168.1.4          00-1f-d0-9b-17-70     dynamisch
  192.168.1.49         00-1f-d0-9b-17-70     dynamisch

```

Possibly, the .49 is the DHCP address but strangely enough it does not show up anywhere on the system! ifconfig does not show it (see above).

As another troubleshooting step, I then upgraded to Ubuntu 14.04.1 LTS, hoping that this would fix it but I had no luck. The issue stayed exactly the same.

So I am desperately looking forward to hints, suggestions or definite solutions to my issue. I am happy to supply any additional info if needed.

Thanks in advance!

---

### Post by marc40 on 2014-10-27
Anybody? Any ideas?

---

