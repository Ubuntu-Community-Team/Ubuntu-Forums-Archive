---
title: "RTL8111/8168/8411 firmware=rtl_nic/rtl8168e-2.fw slow, r8168-dkms bug"
date: 2017-08-06
forum: Networking &amp; Wireless
---

### Post by volkswagner on 2017-08-06
Greetings,


I'm trying Ubuntu 16.04.3 LTS \n \l on MiniITX [GA-D525TUD]("http://www.gigabyte.co.za/Motherboard/GA-D525TUD-rev-1x#ov").

Out of the box Ubuntu has slow network performance (Max 200Mbs) on full Gigabit network.
I installed r8168-dkms from repository which did not help performance. It did however cause segfault when
trying to ssh into the box using keyAuth.

```
srvadmin@srv01:~$ tail /var/log/syslog
Aug  6 09:55:48 srv01 systemd[1454]: Reached target Sockets.
Aug  6 09:55:48 srv01 systemd[1454]: Reached target Paths.
Aug  6 09:55:48 srv01 systemd[1454]: Reached target Basic System.
Aug  6 09:55:48 srv01 systemd[1454]: Reached target Default.
Aug  6 09:55:48 srv01 systemd[1454]: Startup finished in 165ms.
Aug  6 09:55:48 srv01 systemd[1]: Started User Manager for UID 1000.
Aug  6 09:56:12 srv01 systemd[1]: Started Session 2 of user srvadmin.
Aug  6 09:56:41 srv01 systemd[1]: Started Session 3 of user srvadmin.
Aug  6 09:56:41 srv01 kernel: [  141.705643] show_signal_msg: 9 callbacks suppressed
Aug  6 09:56:41 srv01 kernel: [  141.705655] lsb_release[1541]: segfault at 10 ip 082222a9 sp bfb8a620 error 4 in python3.5[8048000+414000]
```

Removing r8168-dkms has fixed the segfault issue.

I'm still left with slow performance, is there anything I can do, or should I just invest in an Intel add-on card.
The board does have one PCI slot, but I'd prefer to leave that available.

Any thoughts on getting the following hardware working?

```
root@srv01:/home/srvadmin# lshw -class network
  *-network               
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: enp1s0
       version: 06
       serial: 50:e5:49:de:b1:f1
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8168e-2.fw ip=192.168.82.164 latency=0 link=yes multicast=yes port=MII speed=1Gbit/s
       resources: irq:27 ioport:ee00(size=256) memory:fdcff000-fdcfffff memory:fdcf8000-fdcfbfff
```

I don't see any spike in CPU utilization, so I'm confident in my testing that the NIC/Drivers is the bottleneck.

My testing consisted of copying file to/from RAMDISK locally then over the wire. locally I can get >500MBs and over the wire I get ~26MBs.

Should I file bug report for r8168-dkms, or is this driver not compatible with my hardware?

---

### Post by praseodym on 2017-08-06
It still shows r8169 instead of r8168. Did you blacklist r8169?

---

### Post by volkswagner on 2017-08-06
Yes, 
I switched back to r8169 because of the segfault caused by r8168-dkms.

I did verify r8168 was in fact loading when I had segfault issue.

---

### Post by volkswagner on 2017-08-19
Well it seems this issue may be due to poor quality switches. I need to get myself an better
switch or move my test environment to an enterprise LAN.

I've tried with a Netgear GS308-100PAS, Netgear GS308P, and Netgear EX7000 (strictly as a switch).
All of the above switches offered near identical performance.
I even tried directly from my MacBook Air to my Lenovo X1 carbon, both have SSD's and my
test results were way lower than expected for a Gigabit LAN (~240Mbs using WinSCP).

I know this may not be an Ubuntu issue, but if anyone has any insight as to what tests
I can run to prove these Netgear gigabit switches are maxing out at 240Mbs.

I have tried alternate patch cables.

---

### Post by praseodym on 2017-08-20
What about driver version 44?

[https://packages.ubuntu.com/artful/r8168-dkms](https://packages.ubuntu.com/artful/r8168-dkms)

---

