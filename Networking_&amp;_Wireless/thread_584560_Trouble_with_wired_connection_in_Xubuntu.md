---
title: "Trouble with wired connection in Xubuntu"
date: 2007-10-21
forum: Networking &amp; Wireless
---

### Post by fredturk on 2007-10-21
I'm running Xubuntu 7.10.

When I log in, the following error message appears:

"Could not look up internet address for dell. This will prevent Xfce from operating correctly. It may be possible to correct the problem by adding dell to the file /etc/hosts on your system"

How do I go about this?

Also,  outputs for lspci and ifconfig 

```
dell@dell:~$ lspci
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 02)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 02)
00:07.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
00:0e.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 74)
01:00.0 VGA compatible controller: NVidia / SGS Thomson (Joint Venture) Riva128 (rev 21)
dell@dell:~$ 

dell@dell:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:01:02:2E:9C:2D  
          inet6 addr: fe80::201:2ff:fe2e:9c2d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:808 errors:0 dropped:0 overruns:151 frame:0
          TX packets:59 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:253746 (247.7 KB)  TX bytes:13997 (13.6 KB)
          Interrupt:10 Base address:0xc000 

eth0:avah Link encap:Ethernet  HWaddr 00:01:02:2E:9C:2D  
          inet addr:169.254.3.225  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:10 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:140 errors:0 dropped:0 overruns:0 frame:0
          TX packets:140 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9000 (8.7 KB)  TX bytes:9000 (8.7 KB)

```

---

### Post by fredturk on 2007-10-21
bump?

---

### Post by kevdog on 2007-10-21
You are not receiving an IP address -- that is the first problem.

What network driver are you using?
lshw -C network

---

### Post by fredturk on 2007-10-21
3Com 3c905c-TX/TX-M

---

### Post by fredturk on 2007-10-21
driver = 3c59x

---

### Post by fredturk on 2007-10-21
anyone who can help?

---

### Post by fredturk on 2007-10-21
update: I turned off IPv6 and tried to force the DNS server, but to no avail

Can anyone help me?

---

