---
title: "No LAN connect"
date: 2008-01-14
forum: Networking &amp; Wireless
---

### Post by carrajung on 2008-01-14
Hi,
I,m having a real problem with my new computer.
Ubuntu 7.10 cant find my LAN.
My new motherboard is a Gigabyte s-seris with gigabyte lan (I dont know if this may be the problem).
I have had to install Windows so that I can connect to the network.

This all worked perfectly with my old PC but not with the new one. 

Please help, I dont know how much longer I can stand Windows.

---

### Post by wieman01 on 2008-01-14
Please post the results of:
> sudo lshw -C network
> sudo ifconfig
> sudo iwconfig
> route
> sudo cat /etc/network/interfaces
Have you used the terminal (i.e. command line) before? Simply type these commands and paste the results into your post. Enter your user password when prompted.

---

### Post by carrajung on 2008-01-14
ubuntu@ubuntu:~$ sudo cat /etc/network/interfaces
auto lo
iface lo inet loopback

ubuntu@ubuntu:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
link-local      *               255.255.0.0     U     0      0        0 eth0
default         *               0.0.0.0         U     1000   0        0 eth0
ubuntu@ubuntu:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ubuntu@ubuntu:~$ sudo ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1D:7D:A2:C9:71  
          inet6 addr: fe80::21d:7dff:fea2:c971/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:4294967270 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17 Base address:0xe000 

eth0:avah Link encap:Ethernet  HWaddr 00:1D:7D:A2:C9:71  
          inet addr:169.254.8.87  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:17 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:752 errors:0 dropped:0 overruns:0 frame:0
          TX packets:752 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:57328 (55.9 KB)  TX bytes:57328 (55.9 KB)

ubuntu@ubuntu:~$ sudo lshw -C network
PCI (sysfs)

---

### Post by wieman01 on 2008-01-15
> **carrajung said:**
> ubuntu@ubuntu:~$ sudo lshw -C network
PCI (sysfs)
Is that all? Strange...

What happens when you plug in the network cable... Is the little green LED lit and blinking?

Please try the following (it's safe, don't worry)...

Open this file:
> sudo gedit /etc/network/interfaces
No make the contents look exactly like this (copy & paste):
> auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
Now restart the network and post the results of:
> sudo ifdown -v eth0
> sudo ifup -v eth0
> route
What networking application do you use in order to connect?

---

