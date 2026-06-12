---
title: "no IP address on asus a8n board after startup"
date: 2006-08-31
forum: Networking &amp; Wireless
---

### Post by jklaps on 2006-08-31
I've installed Ubuntu 6.06 on an Asus A8N SLI Premium board with an AMD X2 4600.

(on this machine is also installed Windows XP and Fedora 5, they are both working fine)

The only troubles I have is with the networking under Ubuntu.

I've got a broadband connection at home, a Linksys  WRT54G router acts as DHCP server and gives my machine an IP.

The Asus A8N has 2 Ethernet devices
- the nForce4 Gigabit port
- MARVELL PCI Gigabit port

I have the nForce port connected to the Linksys router.

Ubuntu detects 2 Ethernet devices eth0 (nForce) and eth1 (MARVELL).

I have the eth1 disabled in the network settings.

Now, when Ubuntu is started, allthough the eth0 is active, it does not get an IP address. I always have to open the Network settings, select the eth0 and do an "deactivate" + "activate" on the eth0 device in order to get my network running.

Any help is highly appreciated.

My ifconfig right after startup:
```

eth0      Link encap:Ethernet  HWaddr 00:13:D4:49:DD:B0
          inet6 addr: fe80::213:d4ff:fe49:ddb0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:899 (899.0 b)  TX bytes:810 (810.0 b)
          Interrupt:217 Base address:0x2000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:272 (272.0 b)  TX bytes:272 (272.0 b)
```

---

### Post by nbzero on 2006-09-16
I also have an nForce networking chip. Installing the K7 version of the kernel image fixed it for me.

---

### Post by gils0040 on 2006-09-16
if you run
sudo dhclient eth0
do you recieve an ip?

---

### Post by jklaps on 2006-09-18
yes, "sudo dhclient eth0" gives me an ip.

Is there a way to automatically get an ip after booting?

Thanks.

---

