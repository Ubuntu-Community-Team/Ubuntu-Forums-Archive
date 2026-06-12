---
title: "unable to ping my desktop from laptop"
date: 2007-05-10
forum: Networking &amp; Wireless
---

### Post by OOzypal on 2007-05-10
My desktop static IP 192.168.1.3
My laptop eth0 (wired-not connected) static IP 192.168.1.2
My laptop eth1 (wireless) 192.168.1.101 (DHCP)
My router IP 192.168.1.1
My router starting number of IP address 192.168.1.100 with maximum user 50

I can connect to internet wirelessly for laptop and wired for my desktop but I can't ping my desktop from laptop and vice versa.

I can ping 192.168.1.1 from desktop but not from laptop (wireless)

---

### Post by Jussi Kukkonen on 2007-05-10
Your router probably has the "no ping from wireless" option on.

---

### Post by OOzypal on 2007-05-10
I have linksys WAG54GS and I could not find this feature/option.

---

### Post by troypdx on 2007-10-25
I have a very similar setup:
 1) UBUNTU 6.06 Desktop running Samba and CUPS, wireless connecton
 2) Laptop with XP, wireless connection
 3) Laptop with Damn Small Linux, wired connection
 4) LINKSYS Router

- I can print and ping between the UBUNTU Desktop and the XP Laptop.
- I can ping between the DSL Laptop and the XP Laptop
- All Internet connections work.

I can't ping (and thus can't print) between the DSL Laptop and the Desktop. 

I've added the following to /etc/cups/cups.d/ports.conf:
 Listen 192.168.0.*:631      # Listen on the LAN interface, Port 631 (IPP)
 Listen 192.168.1.*:631      

But this doesn't seem to be a CUPS issue. 

Thanks in advance for anyone's advice!

---

