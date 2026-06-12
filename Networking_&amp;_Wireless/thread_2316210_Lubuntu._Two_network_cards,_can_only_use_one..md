---
title: "Lubuntu. Two network cards, can only use one."
date: 2016-03-06
forum: Networking &amp; Wireless
---

### Post by Andy_Weston on 2016-03-06
Hi, Im new to Lubuntu, and Linux, and not really sure where to start. My overall goal is to try and make a firewall box using a system I have that has two network cards. Ive installed Windows and can see and use both of the cards so I know that they work. Ive tried one or two of the firewall distros but I dont know enough yet to be able to even start to configure them so I thought I would use an "easier" (?) distro to start with.
I installed Lubuntu and I can use one of the network points fine (using it to post this) but the second one just doesnt work, when I connect the cable to I just loose my network connection.
I dont know how to check if it is seen by the system, and if drivers are required.
I ran $ifconfig and got this;

```
enp1s0    Link encap:Ethernet  HWaddr 00:90:fb:21:6d:8a  
          inet addr:192.168.0.37  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::290:fbff:fe21:6d8a/64 Scope:Link
          inet6 addr: fd8c:34fd:e24f:f000:290:fbff:fe21:6d8a/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:54002 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5926 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:13062297 (13.0 MB)  TX bytes:682168 (682.1 KB)
          Interrupt:16 Memory:fdde0000-fde00000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:1902 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1902 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:203550 (203.5 KB)  TX bytes:203550 (203.5 KB)
```

Any pointers?

Thanks

*Edit*
After some more searching, I installed lshw and ran it. I found out that one of the network adaptors is "unclaimed", and now Im stuck again, details of both are;

```
Ethernet interface
/0/100/1c/0


product: 82573L Gigabit Ethernet Controller [8086:109A]
vendor: Intel Corporation [8086]
bus info: pci@0000:01:00.0
logical name: enp1s0
version: 00
serial: 00:90:fb:21:6d:8a
size: 100Mbit/s
capacity: 1Gbit/s
width: 32 bits
clock: 33MHz
capabilities:
    Power Management,
    Message Signalled Interrupts,
    PCI Express,
    bus mastering,
    PCI capabilities listing,
    ethernet,
    Physical interface,
    twisted pair,
    10Mbit/s,
    10Mbit/s (full duplex),
    100Mbit/s,
    100Mbit/s (full duplex),
    1Gbit/s (full duplex),
    Auto-negotiation
configuration:
    autonegotiation: on
    broadcast: yes
    driver: e1000e
    driverversion: 3.2.5-k
    duplex: full
    firmware: 0.5-7
    ip: 192.168.0.37
    latency: 0
    link: yes
    multicast: yes
    port: twisted pair
    speed: 100Mbit/s
resources:
    irq: 26
    memory: fdde0000-fddfffff
    ioport: cf00(size=32)

```
AND
```

Ethernet controller
/0/100/1c.1/0


product: 82573L Gigabit Ethernet Controller [8086:109A]
vendor: Intel Corporation [8086]
bus info: pci@0000:02:00.0
version: 00
width: 32 bits
clock: 33MHz
capabilities:
    Power Management,
    Message Signalled Interrupts,
    PCI Express,
    PCI capabilities listing
configuration:
    latency: 0
resources:
    memory: fd9e0000-fd9fffff
    ioport: bf00(size=32)
this device has not been claimed
```

---

### Post by TheFu on 2016-03-06
Please edit the post to use "code tags" - much easier to read.

Just because some HW works under Windows, that doesn't mean it will work under Linux.  Driver thing.
[http://blog.jdpfu.com/2013/03/01/linux-troubleshooting-101-networking](http://blog.jdpfu.com/2013/03/01/linux-troubleshooting-101-networking) has some commands to run and post the output from.  Always use "code tags" when posting here so things line up.

---

### Post by Andy_Weston on 2016-03-07
Sorry about the code thing, didnt know.
Thanks for the reply, and the link.
Below are the commands from the link and the output they produced.

dmesg |grep eth[0-9] produced this:-
```

andy@Firewall:~$ dmesg |grep eth[0-9]
[    1.766501] e1000e 0000:01:00.0 eth0: (PCI Express:2.5GT/s:Width x1) 00:90:fb:21:6d:8a
[    1.766507] e1000e 0000:01:00.0 eth0: Intel(R) PRO/1000 Network Connection
[    1.766582] e1000e 0000:01:00.0 eth0: MAC: 2, PHY: 2, PBA No: FFFFFF-0FF
[    1.843095] e1000e 0000:01:00.0 enp1s0: renamed from eth0

```

sudo lshw -C network produced this:-
```
 
*-network
       description: Ethernet interface
       product: 82573L Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: enp1s0
       version: 00
       serial: 00:90:fb:21:6d:8a
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=3.2.5-k duplex=full firmware=0.5-7 ip=192.168.0.37 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:26 memory:fdde0000-fddfffff ioport:cf00(size=32)
  *-network UNCLAIMED
       description: Ethernet controller
       product: 82573L Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
       resources: memory:fd9e0000-fd9fffff ioport:bf00(size=32)

```

ifconfig -a produced this:-

```

enp1s0    Link encap:Ethernet  HWaddr 00:90:fb:21:6d:8a  
          inet addr:192.168.0.37  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::290:fbff:fe21:6d8a/64 Scope:Link
          inet6 addr: fd8c:34fd:e24f:f000:290:fbff:fe21:6d8a/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3191 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1982 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2333406 (2.3 MB)  TX bytes:282827 (282.8 KB)
          Interrupt:16 Memory:fdde0000-fde00000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:768 errors:0 dropped:0 overruns:0 frame:0
          TX packets:768 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:78993 (78.9 KB)  TX bytes:78993 (78.9 KB)

```

more /etc/resolv.conf produced this:-

```

# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.1.1
search lan

```


route produced this:-
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         192.168.0.1     0.0.0.0         UG    100    0        0 enp1s0
192.168.0.0     *               255.255.255.0   U     100    0        0 enp1s0

```

---

### Post by TheFu on 2016-03-09
Sorry for the delay - was traveling.
Appears you have 2 Intel PRO/1000 NICs. Yes?  
Somehow 1 is renamed ... I wouldn't do it when new to Linux.  I think the way to fix that so you end up with eth0 and eth1 is to clean up /etc/udev/rules.d/70-persistent-net.rules file.  Just delete the lines that aren't comments and reboot. It will be regenerated automatically and you should have eth0 and eth1 then.

Unless this is a dual/quad NIC card.  Then we just need to see /etc/network/interfaces (the entire file).
Thanks for showing both the command AND the output inside the code-tags. Helpful.   Have you seen the ubuntu server manual? That could be helpful too.

This won't be a popular statement, but if you are new to Linux, trying to make a secure firewall with it isn't the brightest idea.  There are many details to setup and 1 tiny mistake will leave the system in a non-secured stated.  I'm not really a fan of Linux-based firewall systems - much prefer BSD for that - something like pfSense or OpenSense would be my first choice for an edge firewall.  If you just want an internal firewall and something to learn on, fine, start with a minimal Ubuntu server (using the minimal install, not the "server" or "desktop" installs) and practice a bunch with it. Also run all the hacking tools against it (which we cannot discuss here - forum rules) to ensure as much as possible that nothing trivially non-secure is left with a bad configuration.  I believe that open-wrt or dd-wrt have x86 releases. Might that be something to check out?

Of course, if you are a Unix admin, then you have all the skills - just the specific commands are a little different under Linux than other Unix-OSes.  You'll figure this stuff out and have a secured Linux firewall in no-time.

---

### Post by Andy_Weston on 2016-03-11
Thanks for the reply, and the warning. It is a learning exercise, and not off to a good start!!, so I will look at the other systems you recommend. Ill also check the server manual.

I do have two intel NIC's, built into the motherboard.

/etc/udev/rules.d is an empty folder and a quick search doesnt find 70-persistent-net.rules

/etc/network/interfaces is as follows;

> # interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback



---

### Post by TheFu on 2016-03-11
Are you running the latest LTS release? If not, that would be my first recommendation. Stay stable. Stay secure.
[http://blog.jdpfu.com/2013/07/19/why-ubuntu-users-should-run-an-lts-release](http://blog.jdpfu.com/2013/07/19/why-ubuntu-users-should-run-an-lts-release) explains my stance on non-LTS releases.

---

### Post by Andy_Weston on 2016-03-11
A quick check on system information shows;

> -Version-
Kernel        : Linux 4.2.0-30-generic (i686)
Compiled        : #36-Ubuntu SMP Fri Feb 26 00:57:19 UTC 2016
C Library        : Unknown
Default C Compiler        : GNU C Compiler version 5.2.1 20151010 (Ubuntu 5.2.1-22ubuntu2) 
Distribution        : Ubuntu 15.10
-Current Session-
Computer Name        : Firewall
User Name        : andy (andy)
Home Directory        : /home/andy
Desktop Environment        : LXDE (Lubuntu)
-Misc-
Uptime        : 2 days, 1 hour and 57 minutes
Load Average        : 0.34, 0.29, 0.16



---

### Post by TheFu on 2016-03-11
So - that would be a "no."  Appears that things have changed too much thanks to udev being merged into systemd and I just don't have the knowledge to help.  Sorry.

Hopefully, someone who does use 15.10 will answer.

[https://wiki.ubuntu.com/LTS](https://wiki.ubuntu.com/LTS) might help with more clarification about LTS.

---

### Post by Andy_Weston on 2016-03-11
so I should install 14.04?

---

