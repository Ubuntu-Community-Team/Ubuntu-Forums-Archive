---
title: "network config probs"
date: 2005-06-21
forum: Networking &amp; Wireless
---

### Post by mailophobic on 2005-06-21
i have been looking at the help guide but didnt found anything usefull for my prob =\

First of all i wanted to know how to change from ipv6 to ipv4, but that is the least of my problems i thought i had ocnfigured everything but still my network dosent work, and its dificult to say what is the exact problem because i really dont know, i dont kknow how to test it to find out. 

this is info i gathered and my interface config file
ifconfig
eth0      Link encap:Ethernet  HWaddr 00:50:FC:4B:F1:4E
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::250:fcff:fe4b:f14e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1189 errors:0 dropped:0 overruns:0 frame:0
          TX packets:60 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:120700 (117.8 KiB)  TX bytes:9637 (9.4 KiB)
          Interrupt:11 Base address:0x2000

-------------------------------

interfaces file
auto lo
iface lo inet loopback

mapping hotplug
	script grep
	map eth0

iface eth0 inet static
address 192.168.1.4
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1

-------------------------------

oh and i tried to do this and it didnt work
modprobe eth0
FATAL: Module eth0 not found.
should it be the interface name?

any tips or directions to the tips would be welcome, thanks in advance

---

### Post by xy77 on 2005-06-21
Since ifconfig shows a network interface, the card is recognised and you don't have to load any modules. try
```

$ lspci -v

```
to see which network card you have and then try to figure out which driver is necessary **if you network card would not have been recognised**.

To troubleshoot your problem:
1) do you use a router? If yes, guessed 192.168.1.1 is your routers IP, report output of
```

$ ping 192.168.1.1

```
as well as
```

$ route

```
as well as
```

$ cat /etc/resolv.conf

```

then we will be able to locate the problem better.

Greetings,
  David (xy77)

---

### Post by mailophobic on 2005-06-21
ok then i have the data you required

here it is, the cat /etc/resolv.conf didnt produce any output. Don't mind my ancient hardware its a scrap computer all i can afford =|

lspci -v
0000:00:00.0 Host bridge: ALi Corporation M1541 (rev 04)
        Subsystem: ALi Corporation ALI M1541 Aladdin V/V+ AGP System Controller
        Flags: bus master, slow devsel, latency 32
        Memory at d8000000 (32-bit, non-prefetchable) [size=64M]
        Capabilities: <available only to root>

0000:00:01.0 PCI bridge: ALi Corporation M1541 PCI to AGP Controller (rev 04) (prog-if 00 [Normal decode])
        Flags: bus master, slow devsel, latency 32
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
        Memory behind bridge: dc000000-ddffffff
        Prefetchable memory behind bridge: d0000000-d7ffffff

0000:00:02.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03) (prog-if 10 [OHCI])
        Flags: bus master, medium devsel, latency 32, IRQ 11
        Memory at df001000 (32-bit, non-prefetchable) [size=4K]

0000:00:07.0 ISA bridge: ALi Corporation M1533 PCI to ISA Bridge [Aladdin IV] (rev b4)
        Flags: bus master, medium devsel, latency 0

0000:00:08.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
        Subsystem: Realtek Semiconductor Co., Ltd. RT8139
        Flags: bus master, medium devsel, latency 32, IRQ 11
        I/O ports at 2000 [size=256]
        Memory at df000000 (32-bit, non-prefetchable) [size=256]

0000:00:09.0 USB Controller: Silicon Image, Inc. (formerly CMD Technology Inc) USB0670 (rev 06) (prog-if 10 [OHCI])
        Flags: bus master, medium devsel, latency 32, IRQ 10
        Memory at df002000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <available only to root>

0000:00:0a.0 Multimedia audio controller: Ensoniq ES1371 [AudioPCI-97] (rev 06)
        Subsystem: Ensoniq Creative Sound Blaster AudioPCI64V, AudioPCI128
        Flags: bus master, slow devsel, latency 32, IRQ 12
        I/O ports at 2400 [size=64]
        Capabilities: <available only to root>

0000:00:0f.0 IDE interface: ALi Corporation M5229 IDE (rev 20) (prog-if fa)
        Flags: bus master, medium devsel, latency 32, IRQ 255
        I/O ports at 2800 [size=16]

0000:01:00.0 VGA compatible controller: S3 Inc. Savage 4 (rev 04) (prog-if 00 [VGA])
        Subsystem: S3 Inc. 86C394-397 Savage4 32bit
        Flags: bus master, 66MHz, medium devsel, latency 248, IRQ 11
        Memory at dd000000 (32-bit, non-prefetchable) [size=512K]
        Memory at d0000000 (32-bit, prefetchable) [size=128M]
        Capabilities: <available only to root>

-----------------------------------------------------------------------------------------------------------------

ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
From 192.168.1.4 icmp_seq=2 Destination Host Unreachable
From 192.168.1.4 icmp_seq=3 Destination Host Unreachable
From 192.168.1.4 icmp_seq=4 Destination Host Unreachable
From 192.168.1.4 icmp_seq=6 Destination Host Unreachable
From 192.168.1.4 icmp_seq=7 Destination Host Unreachable
From 192.168.1.4 icmp_seq=8 Destination Host Unreachable
From 192.168.1.4 icmp_seq=10 Destination Host Unreachable

(i imagine it would go on till seq=64 ttl field so i stopped it)

-----------------------------------------------------------------------------------------------------------------

suli@ubuntu:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
default         192.168.1.1     0.0.0.0         UG    0      0        0 eth0

---

### Post by xy77 on 2005-06-22
[QUOTE=mailophobic]
here it is, the cat /etc/resolv.conf didnt produce any output. Don't mind my ancient hardware its a scrap computer all i can afford =|
[/QUOTE]
The /etc/resolv.conf contains your nameserver. Without, you won't be able to connect to any website via [www.something.org](www.something.org). For you, it should contain
```

nameserver 192.168.1.1

```

[QUOTE=mailophobic]
lspci -v
0000:00:08.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
        Subsystem: Realtek Semiconductor Co., Ltd. RT8139
        Flags: bus master, medium devsel, latency 32, IRQ 11
        I/O ports at 2000 [size=256]
        Memory at df000000 (32-bit, non-prefetchable) [size=256]
[/QUOTE]
No problem here, this is your ethernet card.

[QUOTE=mailophobic]
ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
From 192.168.1.4 icmp_seq=2 Destination Host Unreachable
From 192.168.1.4 icmp_seq=3 Destination Host Unreachable
(i imagine it would go on till seq=64 ttl field so i stopped it)
[/QUOTE]
It wouldn't stop at all, unless you tell it to do a specific number of pings (via -n IIRC). Host unreachable means, no connection could be established. Double check, if 192.168.1.1 is the IP of your router. Telling us a bit about your network's configuration would probably help, ("I use Router foo and there are no/other pcs connected, I use a switch/hub, etc.")

Greetings,
  David (xy77)

---

### Post by rps63ifid on 2005-06-23
If you are still in a position of wanting to turn off IPv6, here are a couple of thoughts based on my (admittedly limited) experience:

1. I struggled with some pretty significant network problems on a couple of by Linux boxes here at home until I did (horribly slow throughput when it would work, and most of the time, it wouldn't work at all). I knew it wasn't a hardware problem, 'cuz the Windows side of my dual-boot boxes were fast, and it was consistent across my Linux boxes (which are all over the map, hardwarewise). From the output of your ifconfig command above, it would appear that IPv6 is still turned on.

2. I was able to turn off IPv6 by modifying /etc/modprobe.d/aliases and find the the line that reads "alias net-pf-10 ipv6" (without the quotes, of course), commenting it out with a "#" at the first character (again, without the quotes), and adding a line that reads 

alias net-pf-10 off

and then restarting my system. All of a sudden, my network connection was rock solid and fast.

Hope this helps!

---

### Post by mailophobic on 2005-06-24
I will expliain my situation, i wanted to connect my pc to my bro's pc he uses window 2000, i was going to configure samba when i noticed that my network configs must be wrong. So i started to configure my ip address i was going to use a dhcp server but that wasnt working so i tried to static arrange my ip. Its hard to explain were im at because i am quite lost =|, at one point it seemed i had so troubles with my interface configurations but no they both seem fine 

the ipv4 is working now thanks for that! =)

---

