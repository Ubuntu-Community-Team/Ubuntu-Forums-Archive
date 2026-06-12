---
title: "Some confusing internet problems"
date: 2006-12-06
forum: Networking &amp; Wireless
---

### Post by fixit on 2006-12-06
Hi guys. I have some very annoying problems with my Ubuntu box. I'm with Ubuntu 6.10 and connecting to internet via ADSL modem(router). I'm connected to switch which is connected to the modem. So I have big problems with my outgoing connections, I mean that I can receive messages (via msn and skype), receive mail but most of the time I can't send back. When I open google I do some searches but sometimes (not always) it just refuses to reload. I read many posts and tutorials, to disable ipv6 and many other tricks but nothing changed. And also I have problems with writing on windows shared folder over my local network. I have full rights and I can read, copy files from win share but can't copy my files over shared folder. I gave you the output of some commands and I would be very thankfull if s.o. can help me.

$ ifconfig eth0

eth0      Link encap:Ethernet  HWaddr 00:16:E6:41:8A:EE  
          inet addr:192.168.1.26  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:16813 errors:2295 dropped:0 overruns:0 frame:2295
          TX packets:21860 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7466400 (7.1 MiB)  TX bytes:4208314 (4.0 MiB)
          Interrupt:225 Base address:0xa000 


$ lspci | grep Eth

00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)


$ route -n

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0


$ cat /etc/resolv.conf

nameserver 212.5.134.3
nameserver 212.39.90.42
nameserver 212.39.90.43


$ cat /etc/network/interfaces

auto lo
iface lo inet loopback

iface eth0 inet static
address 192.168.1.26
gateway 192.168.1.1
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255

auto eth0

---

### Post by fixit on 2006-12-06
So I noticed some other strange behavior. Now I'm writing from another computer because I can't send my authethication information (from mine) to log into the forum. So my computer crashes every time when i power it off (not shut it down) and then turn it on again. This happens from 5 to 25 minutes from when I turn it on. In this time my internet connection works well but after the crash it stops working fine. I don't know if this is software or hardware problem because it works only with Ubuntu and no other OS. If anybody have any suggestions or questions or if you need some additional information please write me. Thanks!

---

### Post by zgornel on 2006-12-06
Try adding to your nameserver list (/etc/resolv.conf) the gateway address (192.168.1.1 if I understood well).

---

### Post by fixit on 2006-12-07
Thank you for the responce. I think i've solved the problem. It's not dns problem at all. There is something called acpi which has to be disabled on booting. Now it seems that everything works fine.

---

