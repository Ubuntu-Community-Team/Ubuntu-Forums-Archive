---
title: "two network interface, but one is extremely slow in samba"
date: 2016-02-19
forum: Networking &amp; Wireless
---

### Post by drei2 on 2016-02-19
Dear All,
 
   i have two network interfaces, one is eth0 for connect internet, and one is p1p1 to connect another computer(win7) directly through LAN cable. I can browse the folder both in win7 and ubuntu, but i cannot write/or extremely slow any files..here is my interfaces


   # The loopback network interfaceauto lo
iface lo inet loopback


# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.1.220
boardcast 192.168.1.255
netmask 255.255.255.0
gateway 192.168.1.1
network 192.168.1.0
dns-nameservers 192.168.1.1


auto p1p1
iface p1p1 inet static
address 192.168.2.11
netmask 255.255.255.0

and i got 2k errors on RX packets, is it normal to get so many errors RX packets?

Thx

---

### Post by praseodym on 2016-02-20
[COLOR="#FF0000"]boardcast[/COLOR] 192.168.1.255

typo?

---

