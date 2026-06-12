---
title: "ubuntu 6.06:Got ip from wired router (dhcp) but cannot ping it"
date: 2006-10-31
forum: Networking &amp; Wireless
---

### Post by bluefin on 2006-10-31
Hi, this is my first attempt at setting up linux and I cannot get the pc online. It looks like I acquire an IP address via dhcp but I cannot ping my router. Below is the info that I think is relevant. Thanks in advance for any tips you might have.

distro:
fresh install of ubunto 6.06 LTS

network layout:
pc-ethernet_cable-router-internet
 
router setup 
ip=192.168.1.1
dhcp starts at 192.168.1.100
(I have other computers on this network)

```

$ ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data
From 192.168.1.102 icmp_seq=2 Destination Host Unreachable
:

```
```

$ ping 192.168.1.102
PING 192.168.1.102 (192.168.1.1102) 56(84) bytes of data
64 bytes from 192.168.1.102:icmp_seq=1 ttl=64 time=.050 ms
:

```
```

$cat interfaces
auto lo
iface lo inet loopback
auto eth0 inet dhcp
auto eth1
iface eth1 inet dhcp
auto eth2 iface eth2 inet dhcp
auto ath0
iface ath0 inet dhcp
iface wlan0 inet dhcp

```
```

$ifconfig
eth0
Link encap:Etherenet HWaddr 00:08:A1:02:03:31
inet addr:192.168.1.102 Bcast:192.168.1.255 Mask:255.255.255.0
inet6 addr: fe80::208::a1ff:fe02:332/64 Scope:Link
UP BROADCAST MULTICAST MTU:150 Metric:1
Rx packets:136 errors:1022 dropped:0 overrruns:0 frame:0
TX packets:14 errors:2 dropped:0 overruns:0 carrier:2
collsions:0 txqueueln:1000
Interrupt:177 Base address:0xd800

lo
...

```

```

$lspci|grep Ether
0000:02:0b.0 Ethernet controller: Davicom Semiconducto, Inc. 21x4x DEC-Tulip compatible 10/100 Ethernet (rev31)

```

---

### Post by stream303 on 2006-11-01
Is your router listed as the default gateway?

route -n

should confirm.  I'm not too strong in this area but I've also seen instances of where the modem and the router are set to the same ip address (bad).

A bit tired so perhaps someone else can spot it right off...

---

### Post by lloyd_b on 2006-11-01
$> cat interfaces
auto lo
iface lo inet loopback
auto eth0 inet dhcp
auto eth1
iface eth1 inet dhcp
auto eth2 iface eth2 inet dhcp
auto ath0
iface ath0 inet dhcp
iface wlan0 inet dhcp

Um, I'm not sure that single-line setup for eth0 is valid (might be - I'm not an expert on the subject).  At any rate, try changing
```
auto eth0 inet dhcp
```
to
```
auto eth0
iface eth0 inet dhcp
```

and see what happens....

FYI: stream303 has probably spotted the base problem - no default route is being defined.  I'm wondering if that odd format for "interfaces" could have something to do with it.

Lloyd B.

---

### Post by bluefin on 2006-11-01
Thanks for your responses. Here is the output of route which I think looks ok as my router has IP 192.168.1.1.

```

route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0

```

Also, as lloyd_b pointed out I made an error in transcribing my interfaces file. Since I am having network issue on the linux box I have been hand jamming the output and made a typo. Sorry for the confusion. Here is the correct output of interfaces:

```

$cat interfaces
auto lo
iface lo inet loopback

auto eth0 
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2 
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

iface wlan0 inet dhcp

```

Any other ideas to try? Thanks!

---

### Post by stream303 on 2006-11-01
Hmm..  Are *all* the machines on the network unable to reach the internet, or just your Ubuntu box?  I'd take them all offline temporarily if you can to isolate things

Is it just a case of not being able to ping the router, yet everything else works?  (I've seen ping-reject options in routers)

Any weird firewall options turned on in the router?

---

### Post by bluefin on 2006-11-01
The main issue is that I cannot get on the internet (using firefox that came with the distro). All other pcs on my network can. I even used the ubuntu live disk on one of the winxp pcs and it worked fine with no additional setup. I didn't try the live disk on the computer that is now causing me a problem before wiping it clean and installing ubuntu (wish i had!), but it did work fine with winxp home.

I don't have any special settings on my router. It is a linksys WRT54G and is setup for DHCP. The computer that is causing me issues is plugged directly to the router. 

Do you guys agree that my ubuntu pc is getting a valid IP address?  I think it is because it can ping itself using 192.168.1.102 and my dhcp starts at *.*.*.100. So to me this meens that dhcp worked. However I don't get how it could have acquired an IP from the router but cannot ping the router. 

Is it possible that this IP address was acquired in windows and is stuck in my ethernet card? Please forgive my ignorance on this subject. I just have no idea if IP addresses are stored in the PC on the card. 

Is there an ipconfig /release/renew equivalent in linux? If so maybe that would help.

Also, is there some sort log that is written two when you connect to the router? Maybe that would help.

Thanks!

---

### Post by dbott67 on 2006-11-01
Try disabling & re-enabling the interface:
```
sudo ifdown eth0
```
```
sudo ifup eth0
```
```
sudo dhclient eth0
```

-Dave

---

### Post by dbott67 on 2006-11-01
> **bluefin said:**
> Also, is there some sort log that is written two when you connect to the router? Maybe that would help.

Thanks!

```
tail -n 20 -f /var/log/syslog
```

Shows the last 20 lines of the syslog, and also will continue to show output (-f switch).

-Dave

---

