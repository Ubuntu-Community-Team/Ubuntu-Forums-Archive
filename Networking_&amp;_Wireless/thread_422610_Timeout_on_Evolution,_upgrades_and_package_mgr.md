---
title: "Timeout on Evolution, upgrades and package mgr"
date: 2007-04-25
forum: Networking &amp; Wireless
---

### Post by rpaco on 2007-04-25
Hi although my problems are related to Evolution mail and to upgrade/update manager I believe they are connected by the fact that when the application (evolution, update manager, package manager or add/remove applications) tries to connect to the inet it is not getting through. Chilli555  I must thank you for solving my earlier network connection problem by adding the line to the blacklist file, this allows me to be here now, (one motherboard and power supply on and with a non working windows system but I think that some other parameter needs to be set or changed or invented to allow the other applications to access the inet..

I give below the output from some commands you might need to determine what needs to be done. I am connecting via my Lynksys ADSL2MU modem/single port router via  wired ethernet.

rpa@rpa-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:19:66:0F:24:6C  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7967 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6623 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7323147 (6.9 MiB)  TX bytes:925256 (903.5 KiB)
          Interrupt:201 Base address:0xd400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:10 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:528 (528.0 b)  TX bytes:528 (528.0 b)

rpa@rpa-desktop:~$ sudo cat /etc/resolv.conf
Password:
nameserver 192.168.1.1
rpa@rpa-desktop:~$ sudo cat /etc/network/interfaces
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

auto wlan0
iface wlan0 inet dhcp

During the setup of Evolution there is an option to check what types of authentication are supported, this just times out as does it when I try and use any of the update or package installers, I  eventually get a list of failed file downloads from the update manager. I believe this is all to do with my network settings. I can download files via Firefox no problem at all. Please advise. Many thanks

---

