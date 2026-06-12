---
title: "[SOLVED] No Internet"
date: 2007-11-19
forum: Networking &amp; Wireless
---

### Post by ezphilosophy on 2007-11-19
It seems that there are quite a few threads on this issue, but without any solutions.  I thought I'd post some more specifics.  Maybe we can get this thing worked out.

I recently installed Gutsy on a friends computer.  He is running a dual-boot with Vista.  He has ADSL and is using a router.  Vista connects to the internet without any problem.

In Gutsy, he cannot connect to the internet and cannot get any updates (time out).  What interesting is that he can connect to the router.  Ubuntu recognizes the wired connection.  He can ping addresses.  Moreover, if he inputs the numbered address (e.g., 66.94.234.13) in the browser's address bar, the page **will** load.  So, I'm thinking this is a ipv6 problem.  I have gone to about:config and disabled ipv6 and the internet/update manager still doesn't work.  I have tried to change "roaming mode" to DHCP.  Still nothing.

What am I forgetting?

**Some specs:**

From ping
```
ubuntu@ubuntu:~$ ping 66.94.234.13
PING 66.94.234.13 (66.94.234.13) 56(84) bytes of data.
64 bytes from 66.94.234.13: icmp_seq=1 ttl=51 time=197 ms
64 bytes from 66.94.234.13: icmp_seq=2 ttl=52 time=196 ms
64 bytes from 66.94.234.13: icmp_seq=3 ttl=51 time=196 ms
64 bytes from 66.94.234.13: icmp_seq=4 ttl=51 time=196 ms
64 bytes from 66.94.234.13: icmp_seq=5 ttl=52 time=196 ms
64 bytes from 66.94.234.13: icmp_seq=6 ttl=52 time=196 ms
64 bytes from 66.94.234.13: icmp_seq=7 ttl=51 time=196 ms
64 bytes from 66.94.234.13: icmp_seq=8 ttl=51 time=196 ms
64 bytes from 66.94.234.13: icmp_seq=9 ttl=51 time=196 ms
64 bytes from 66.94.234.13: icmp_seq=10 ttl=51 time=196 ms
64 bytes from 66.94.234.13: icmp_seq=11 ttl=52 time=194 ms
64 bytes from 66.94.234.13: icmp_seq=12 ttl=51 time=196 ms
64 bytes from 66.94.234.13: icmp_seq=13 ttl=52 time=198 ms
64 bytes from 66.94.234.13: icmp_seq=14 ttl=51 time=194 ms

--- 66.94.234.13 ping statistics ---
14 packets transmitted, 14 received, 0% packet loss, time 13001ms
rtt min/avg/max/mdev = 194.716/196.607/198.625/1.059 ms
ubuntu@ubuntu:~$ ping 72.14.253.99
PING 72.14.253.99 (72.14.253.99) 56(84) bytes of data.
64 bytes from 72.14.253.99: icmp_seq=3 ttl=237 time=277 ms
64 bytes from 72.14.253.99: icmp_seq=4 ttl=237 time=275 ms
64 bytes from 72.14.253.99: icmp_seq=5 ttl=237 time=275 ms
64 bytes from 72.14.253.99: icmp_seq=6 ttl=237 time=275 ms
64 bytes from 72.14.253.99: icmp_seq=8 ttl=237 time=275 ms
64 bytes from 72.14.253.99: icmp_seq=9 ttl=237 time=277 ms
64 bytes from 72.14.253.99: icmp_seq=10 ttl=237 time=275 ms
64 bytes from 72.14.253.99: icmp_seq=11 ttl=237 time=277 ms
64 bytes from 72.14.253.99: icmp_seq=12 ttl=237 time=275 ms

--- 72.14.253.99 ping statistics ---
12 packets transmitted, 9 received, 25% packet loss, time 11010ms
rtt min/avg/max/mdev = 275.087/275.786/277.172/1.172 ms    
```

From ifconfig -a

```
ubuntu@ubuntu:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:1A:4D:4A:57:9A  
          inet addr:192.168.1.101  Bcast:255.255.255.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:4dff:fe4a:579a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9 errors:0 dropped:0 overruns:0 frame:0
          TX packets:81 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2060 (2.0 KB)  TX bytes:8771 (8.5 KB)
          Interrupt:17 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
```

From lspci -v
```
ubuntu@ubuntu:~$ lspci -v
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
        Subsystem: Giga-byte Technology Unknown device 5000
        Flags: bus master, fast devsel, latency 0
        Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        I/O behind bridge: 0000b000-0000bfff
        Memory behind bridge: f4000000-f7ffffff
        Prefetchable memory behind bridge: 00000000e0000000-00000000efffffff
        Capabilities: <access denied>

00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Giga-byte Technology Unknown device 5004
        Flags: bus master, medium devsel, latency 0, IRQ 16
        I/O ports at e100 [size=32]
        Capabilities: <access denied>

00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Giga-byte Technology Unknown device 5004
        Flags: bus master, medium devsel, latency 0, IRQ 18
        I/O ports at e200 [size=32]
        Capabilities: <access denied>

00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Giga-byte Technology Unknown device 5004
        Flags: bus master, medium devsel, latency 0, IRQ 19
        I/O ports at e000 [size=32]
        Capabilities: <access denied>

00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02) (prog-if 20 [EHCI])
        Subsystem: Giga-byte Technology Unknown device 5006
        Flags: bus master, medium devsel, latency 0, IRQ 19
        Memory at fa205000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
        Subsystem: Giga-byte Technology Unknown device a022
        Flags: bus master, fast devsel, latency 0, IRQ 22
        Memory at fa200000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        I/O behind bridge: 0000a000-0000afff
        Capabilities: <access denied>

00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
        I/O behind bridge: 0000c000-0000cfff
        Memory behind bridge: fa000000-fa0fffff
        Capabilities: <access denied>

00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
        I/O behind bridge: 0000d000-0000dfff
        Memory behind bridge: f8000000-f9ffffff
        Prefetchable memory behind bridge: 00000000fa300000-00000000fa3fffff
        Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Giga-byte Technology Unknown device 5004
        Flags: bus master, medium devsel, latency 0, IRQ 20
        I/O ports at e300 [size=32]
        Capabilities: <access denied>

00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Giga-byte Technology Unknown device 5004
        Flags: bus master, medium devsel, latency 0, IRQ 21
        I/O ports at e400 [size=32]
        Capabilities: <access denied>

00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Giga-byte Technology Unknown device 5004
        Flags: bus master, medium devsel, latency 0, IRQ 19
        I/O ports at e500 [size=32]
        Capabilities: <access denied>

00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02) (prog-if 20 [EHCI])
        Subsystem: Giga-byte Technology Unknown device 5006
        Flags: bus master, medium devsel, latency 0, IRQ 20
        Memory at fa204000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92) (prog-if 01 [Subtractive decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=05, subordinate=05, sec-latency=32
        Memory behind bridge: fa100000-fa1fffff
        Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801IR (ICH9R) LPC Interface Controller (rev 02)
        Subsystem: Giga-byte Technology Unknown device 5001
        Flags: bus master, medium devsel, latency 0
        Capabilities: <access denied>

00:1f.2 IDE interface: Intel Corporation 82801IR/IO/IH (ICH9R/DO/DH) 4 port SATA IDE Controller (rev 02) (prog-if 8a [Master SecP PriP])
        Subsystem: Giga-byte Technology Unknown device b002
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 21
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at f000 [size=16]
        I/O ports at fc00 [size=16]
        Capabilities: <access denied>

00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
        Subsystem: Giga-byte Technology Unknown device 5001
        Flags: medium devsel, IRQ 9
        Memory at fa206000 (64-bit, non-prefetchable) [size=256]
        I/O ports at 0500 [size=32]

00:1f.5 IDE interface: Intel Corporation 82801I (ICH9 Family) 2 port SATA IDE Controller (rev 02) (prog-if 85 [Master SecO PriO])
        Subsystem: Giga-byte Technology Unknown device b002
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 21
        I/O ports at e700 [size=8]
        I/O ports at e800 [size=4]
        I/O ports at e900 [size=8]
        I/O ports at ea00 [size=4]
        I/O ports at eb00 [size=16]
        I/O ports at ec00 [size=16]
        Capabilities: <access denied>

01:00.0 VGA compatible controller: nVidia Corporation G80 [GeForce 8800 GTX] (rev a2) (prog-if 00 [VGA])
        Subsystem: LeadTek Research Inc. Unknown device 2a70
        Flags: bus master, fast devsel, latency 0, IRQ 10
        Memory at f6000000 (32-bit, non-prefetchable) [size=16M]
        Memory at e0000000 (64-bit, prefetchable) [size=256M]
        Memory at f4000000 (64-bit, non-prefetchable) [size=32M]
        I/O ports at b000 [size=128]
        [virtual] Expansion ROM at f7000000 [disabled] [size=128K]
        Capabilities: <access denied>

03:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02) (prog-if 01 [AHCI 1.0])
        Subsystem: Giga-byte Technology Unknown device b000
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at fa000000 (32-bit, non-prefetchable) [size=8K]
        Capabilities: <access denied>

03:00.1 IDE interface: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02) (prog-if 85 [Master SecO PriO])
        Subsystem: Giga-byte Technology Unknown device b000
        Flags: bus master, fast devsel, latency 0, IRQ 17
        I/O ports at c000 [size=8]
        I/O ports at c100 [size=4]
        I/O ports at c200 [size=8]
        I/O ports at c300 [size=4]
        I/O ports at c400 [size=16]
        Capabilities: <access denied>

04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
        Subsystem: Giga-byte Technology Unknown device e000
        Flags: bus master, fast devsel, latency 0, IRQ 17
        I/O ports at d000 [size=256]
        Memory at f9000000 (64-bit, non-prefetchable) [size=4K]
        [virtual] Expansion ROM at fa300000 [disabled] [size=64K]
        Capabilities: <access denied>

05:06.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link) (prog-if 10 [OHCI])
        Subsystem: Giga-byte Technology Unknown device 1000
        Flags: bus master, medium devsel, latency 32, IRQ 19
        Memory at fa104000 (32-bit, non-prefetchable) [size=2K]
        Memory at fa100000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

ubuntu@ubuntu:~$ 

```

From route -n
```
ubuntu@ubuntu:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0

```

**Any Ideas?**

---

### Post by LRT on 2007-11-19
if you can see websites by using ip addresses, then it is most likely you have a DNS issue. make sure you are using the name servers your ISP provides, these should be the same as those configured in Vista, if you say you can browse websites when you boot into Vista.

---

### Post by ezphilosophy on 2007-11-20
> **LRT said:**
> if you can see websites by using ip addresses, then it is most likely you have a DNS issue. make sure you are using the name servers your ISP provides, these should be the same as those configured in Vista, if you say you can browse websites when you boot into Vista.

Yes!  Solved.

I looked in the router settings and found the DNS servers and used them.  

A couple more questions:

1. Why weren't the DNS servers right in the first place?  Why on my computer (not my friend's) was the DNS correct and I had no problems, but on his, they were wrong?  What can be done to avoid this?

2.  How do I mark this thread as "solved"?  (two years on the ubuntu forums and don't know how to do this...  a little embarrased.  :oops:)

---

### Post by LRT on 2007-11-20
> 1. Why weren't the DNS servers right in the first place? Why on my computer (not my friend's) was the DNS correct and I had no problems, but on his, they were wrong? What can be done to avoid this?

they may not have been "wrong" per say, just set to some default value. actually, now that i am thinking about it, if he was not plugged in to the router during the gutsy installation, then the nameservers were probably set to some default value. when i installed feisty i was plugged in to my modem and all connection settings were automatically detected.

> 2. How do I mark this thread as "solved"?

i'm not sure but i think all you have to do is put "SOLVED" in front of the title of the post.


Question for you...

Where did you assign the name servers in gutsy?

---

### Post by ezphilosophy on 2007-11-21
> **LRT said:**
> they may not have been "wrong" per say, just set to some default value. actually, now that i am thinking about it, if he was not plugged in to the router during the gutsy installation, then the nameservers were probably set to some default value. when i installed feisty i was plugged in to my modem and all connection settings were automatically detected.

He was plugged into the router at the time of the install.

> **LRT said:**
> 
i'm not sure but i think all you have to do is put "SOLVED" in front of the title of the post.


But you can't edit the title.  I remember there is a forum member around here with the link on how to do it in his/her signature.  Wish they would reply to this thread! (or I wish I had read it!)

> **LRT said:**
> Question for you...

Where did you assign the name servers in gutsy?

in system-admin-network-dns

---

### Post by ezphilosophy on 2007-11-21
Another problem has seemed to present itself.  The DNS servers won't stay changed!  They seem to change back.  They changed after an update.  Possibly, that has something to do with it.  But not likely.  Shouldn't have to go back and change them all the time.  I'll have to get back to my friend's computer to check it out.
Anyone ever heard of this?

---

### Post by LRT on 2007-11-21
figured it out. to mark a thread as solved, all you have to do is click on the drop-down arrow "Thread Tools" at the top of the thread and then click on "mark this thread as solved"

---

