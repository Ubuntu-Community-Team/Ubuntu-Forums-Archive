---
title: "I can't connect to the internet from my Hardy!"
date: 2008-05-07
forum: Networking &amp; Wireless
---

### Post by Fixman on 2008-05-07
I can't connect to the internet from my Hardy, and I think its the network card. Can someone help me or give me new drivers for it? Here are some commands I ran:

```

dmesg | grep -i eth
[   28.135880] Driver 'sd' needs updating - please use bus_type methods
[   34.220945] sis190 Gigabit Ethernet driver 1.2 loaded.
[   34.811838] 0000:00:04.0: SiS 191 PCI Gigabit Ethernet adapter at f8896c00 (IRQ: 20), 00:1e:8c:14:0b:7d
[   34.811842] eth0: GMII mode.
[   34.811847] eth0: Enabling Auto-negotiation.
[   36.039581] udev: renamed network interface eth0 to eth1
[   45.799733] ADDRCONF(NETDEV_UP): eth1: link is not ready
[ 3458.606189] ADDRCONF(NETDEV_UP): eth1: link is not ready


ifconfig
eth1      Link encap:Ethernet  HWaddr 00:1e:8c:14:0b:7d  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:72 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:11612 (11.3 KB)  TX bytes:0 (0.0 B)
          Interrupt:20 Base address:0xdead 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1392 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1392 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:69600 (67.9 KB)  TX bytes:69600 (67.9 KB)


lspci -nn | grep -i eth
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] 191 Gigabit Ethernet Adapter [1039:0191] (rev 02)

```

---

### Post by spiderbatdad on 2008-05-07
I believe driver 'sd' is referring to a scsi device. Not sure what that mode is for eth0. Are you using some boot parameters for hardware detection?
Is eth0 configured in network manager. Maybe upload dmesg as an archived text file.

Possibly a BIOS setting for ethernet?

---

### Post by Fixman on 2008-05-07
> **spiderbatdad said:**
> I believe driver 'sd' is referring to a scsi device. Not sure what that mode is for eth0. Are you using some boot parameters for hardware detection?
Is eth0 configured in network manager. Maybe upload dmesg as an archived text file.

Possibly a BIOS setting for ethernet?

Nope, there was no BIOS setting disabling ethernet.

---

### Post by spiderbatdad on 2008-05-07
you might edit /boot/grub/menu.lst kernel line by removing --quiet splash and replace with pci=routeirq

---

### Post by Fixman on 2008-05-07
> **spiderbatdad said:**
> you might edit /boot/grub/menu.lst kernel line by removing --quiet splash and replace with pci=routeirq

Nope

---

### Post by Fixman on 2008-05-07
bump

---

### Post by Fixman on 2008-05-08
Some days ago, I upgraded from Ubuntu 7.10 to Ubuntu 8.04 and everything went smoothly. But, a week later, I changed my computer and preserved only the hard drive. Now, after doing some dpkg-reconfigures (yay to linux, my win partition just died), I can everything work perfectly, except for the internet (that its a hardware problem and not an installation problem, because internet does not work from the Live CD).

I have a ethernet cable connected to a router (that has a light saying that the cable is connected, bu I can't even ping it).

Here are some commands:

```

dmesg | grep -i eth

[   24.773809] Driver 'sd' needs updating - please use bus_type methods
[   30.921684] sis190 Gigabit Ethernet driver 1.2 loaded.
[   31.509949] 0000:00:04.0: SiS 191 PCI Gigabit Ethernet adapter at f88f2c00 (IRQ: 20), 00:1e:8c:14:0b:7d
[   31.510013] eth0: GMII mode.
[   31.510055] eth0: Enabling Auto-negotiation.
[   32.824666] udev: renamed network interface eth0 to eth1
[   40.432361] ADDRCONF(NETDEV_UP): eth1: link is not ready
[ 1245.317999] ADDRCONF(NETDEV_UP): eth1: link is not ready


ifconfig
eth1      Link encap:Ethernet  HWaddr 00:1e:8c:14:0b:7d  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:180 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:26969 (26.3 KB)  TX bytes:0 (0.0 B)
          Interrupt:20 Base address:0xdead 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1396 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1396 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:69800 (68.1 KB)  TX bytes:69800 (68.1 KB)


lspci | grep -i eth

00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] 191 Gigabit Ethernet Adapter (rev 02)

```

---

### Post by Fixman on 2008-05-08
Some days ago, I upgraded from Ubuntu 7.10 to Ubuntu 8.04 and everything went smoothly. But, a week later, I changed my computer and preserved only the hard drive. Now, after doing some dpkg-reconfigures (yay to linux, my win partition just died), I can everything work perfectly, except for the internet (that its a hardware problem and not an installation problem, because internet does not work from the Live CD).

I have a ethernet cable connected to a router (that has a light saying that the cable is connected, bu I can't even ping it).

Here are some commands:

```

dmesg | grep -i eth

[   24.773809] Driver 'sd' needs updating - please use bus_type methods
[   30.921684] sis190 Gigabit Ethernet driver 1.2 loaded.
[   31.509949] 0000:00:04.0: SiS 191 PCI Gigabit Ethernet adapter at f88f2c00 (IRQ: 20), 00:1e:8c:14:0b:7d
[   31.510013] eth0: GMII mode.
[   31.510055] eth0: Enabling Auto-negotiation.
[   32.824666] udev: renamed network interface eth0 to eth1
[   40.432361] ADDRCONF(NETDEV_UP): eth1: link is not ready
[ 1245.317999] ADDRCONF(NETDEV_UP): eth1: link is not ready


ifconfig
eth1      Link encap:Ethernet  HWaddr 00:1e:8c:14:0b:7d  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:180 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:26969 (26.3 KB)  TX bytes:0 (0.0 B)
          Interrupt:20 Base address:0xdead 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1396 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1396 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:69800 (68.1 KB)  TX bytes:69800 (68.1 KB)


lspci | grep -i eth

00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] 191 Gigabit Ethernet Adapter (rev 02)

```

---

### Post by Fixman on 2008-05-08
Some days ago, I upgraded from Ubuntu 7.10 to Ubuntu 8.04 and everything went smoothly. But, a week later, I changed my computer and preserved only the hard drive. Now, after doing some dpkg-reconfigures (yay to linux, my win partition just died), I can everything work perfectly, except for the internet (that its a hardware problem and not an installation problem, because internet does not work from the Live CD).

I have a ethernet cable connected to a router (that has a light saying that the cable is connected, bu I can't even ping it).

Here are some commands:

```

dmesg | grep -i eth

[   24.773809] Driver 'sd' needs updating - please use bus_type methods
[   30.921684] sis190 Gigabit Ethernet driver 1.2 loaded.
[   31.509949] 0000:00:04.0: SiS 191 PCI Gigabit Ethernet adapter at f88f2c00 (IRQ: 20), 00:1e:8c:14:0b:7d
[   31.510013] eth0: GMII mode.
[   31.510055] eth0: Enabling Auto-negotiation.
[   32.824666] udev: renamed network interface eth0 to eth1
[   40.432361] ADDRCONF(NETDEV_UP): eth1: link is not ready
[ 1245.317999] ADDRCONF(NETDEV_UP): eth1: link is not ready


ifconfig
eth1      Link encap:Ethernet  HWaddr 00:1e:8c:14:0b:7d  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:180 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:26969 (26.3 KB)  TX bytes:0 (0.0 B)
          Interrupt:20 Base address:0xdead 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1396 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1396 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:69800 (68.1 KB)  TX bytes:69800 (68.1 KB)


lspci | grep -i eth

00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] 191 Gigabit Ethernet Adapter (rev 02)

```

---

### Post by spiderbatdad on 2008-05-08
[http://howtoforge.com/creating-the-sis191-gigabit-ethernet-driver-on-linux-2.6](http://howtoforge.com/creating-the-sis191-gigabit-ethernet-driver-on-linux-2.6)

Or get a different card.

---

### Post by Fixman on 2008-05-08
> **spiderbatdad said:**
> [http://howtoforge.com/creating-the-sis191-gigabit-ethernet-driver-on-linux-2.6](http://howtoforge.com/creating-the-sis191-gigabit-ethernet-driver-on-linux-2.6)

Or get a different card.

That tutorial is for resolving a bug on Linux 2.6.22, I have Linux 2.6.26 (the kernel from Hardy), that has that bug resolved.

---

### Post by spiderbatdad on 2008-05-08
OIC. The bug has been fixed, so you're all set then?

```
Version numbering

The version number of the Linux kernel currently consists of four numbers, following a recent change in the long-standing policy of a three-number versioning scheme. For illustration, let it be assumed that the version number is composed thus: A.B.C[.D] (e.g. 2.2.1, 2.4.13 or 2.6.12.3).

    * The A number denotes the kernel version. It is changed least frequently, and only when major changes in the code and the concept of the kernel occur. It has been changed twice in the history of the kernel: In 1994 (version 1.0) and in 1996 (version 2.0).

    * The B number denotes the major revision of the kernel.
          o Prior to the Linux 2.6.x series, even numbers indicate a stable release, i.e. one that is deemed fit for production use, such as 1.2, 2.4 or 2.6. Odd numbers have historically been development releases, such as 1.1 or 2.5. They were for testing new features and drivers until they became sufficiently stable to be included in a stable release. It was an even/odd version number scheme.
          o Starting with the Linux 2.6.x series, there is no significance to even or odd numbers, with new feature development going on in the same kernel series. Linus Torvalds has stated that this will be the model for the foreseeable future.

    * The C number indicates the minor revision of the kernel. In the old three-number versioning scheme, this was changed when security patches, bugfixes, new features or drivers were implemented in the kernel. With the new policy, however, it is only changed when new drivers or features are introduced; minor fixes are handled by the D number.

    * A D number first occurred when a grave error, which required immediate fixing, was encountered in 2.6.8's NFS code. However, there were not enough other changes to legitimize the release of a new minor revision (which would have been 2.6.9). So, 2.6.8.1 was released, with the only change being the fix of that error. With 2.6.11, this was adopted as the new official versioning policy. Bug-fixes and security patches are now managed by the fourth number, whereas bigger changes are only implemented in minor revision changes (the C number).

```

---

### Post by Fixman on 2008-05-08
> **spiderbatdad said:**
> OIC. The bug has been fixed, so you're all set then?

```
Version numbering

The version number of the Linux kernel currently consists of four numbers, following a recent change in the long-standing policy of a three-number versioning scheme. For illustration, let it be assumed that the version number is composed thus: A.B.C[.D] (e.g. 2.2.1, 2.4.13 or 2.6.12.3).

    * The A number denotes the kernel version. It is changed least frequently, and only when major changes in the code and the concept of the kernel occur. It has been changed twice in the history of the kernel: In 1994 (version 1.0) and in 1996 (version 2.0).

    * The B number denotes the major revision of the kernel.
          o Prior to the Linux 2.6.x series, even numbers indicate a stable release, i.e. one that is deemed fit for production use, such as 1.2, 2.4 or 2.6. Odd numbers have historically been development releases, such as 1.1 or 2.5. They were for testing new features and drivers until they became sufficiently stable to be included in a stable release. It was an even/odd version number scheme.
          o Starting with the Linux 2.6.x series, there is no significance to even or odd numbers, with new feature development going on in the same kernel series. Linus Torvalds has stated that this will be the model for the foreseeable future.

    * The C number indicates the minor revision of the kernel. In the old three-number versioning scheme, this was changed when security patches, bugfixes, new features or drivers were implemented in the kernel. With the new policy, however, it is only changed when new drivers or features are introduced; minor fixes are handled by the D number.

    * A D number first occurred when a grave error, which required immediate fixing, was encountered in 2.6.8's NFS code. However, there were not enough other changes to legitimize the release of a new minor revision (which would have been 2.6.9). So, 2.6.8.1 was released, with the only change being the fix of that error. With 2.6.11, this was adopted as the new official versioning policy. Bug-fixes and security patches are now managed by the fourth number, whereas bigger changes are only implemented in minor revision changes (the C number).

```

Thats actually the problem. My internet does not work, even on the new Kernel.

---

### Post by dupin on 2008-05-21
The problem you have is that the driver can't see the wire connected to the NIC (Network Interface Card). I had the same issue, I could solve it half way. 
you can see what I did here:
> [http://ubuntuforums.org/showthread.php?t=188060](http://ubuntuforums.org/showthread.php?t=188060)
I suggest you check the problem you have is the same as the posted in that thread before modifing the source of the module.

Why my problem is solved half way? Because I can connect but I have a huge packet loss, and I suspect I also have packet malformation (and that's causing packet loss) because I can't connect through a proxy to the internet and scp (ssh copy) does not work in the LAN, it tries to start transfer and it gets stalled. 
Still could not find a solution for this, but still searching.

Hope this information was useful ;)

---

