---
title: "Print Wirelessly"
date: 2007-05-05
forum: Networking &amp; Wireless
---

### Post by OOzypal on 2007-05-05
I have the following set up,

1. Desktop (Feisty) wired connected to ADSL Wireless router/modem
2. Laptop (Feisty) wireless connected to ADSL Wireless router/modem
3. Printer connected to Desktop

I would like to print wirelessly from the laptop to the desktop. I followed the instruction in following wiki but no help. When I print, my laptop says that server is busy.

[https://help.ubuntu.com/community/NetworkPrintingWithUbuntu](https://help.ubuntu.com/community/NetworkPrintingWithUbuntu)

---

### Post by davo8 on 2007-05-08
one suggestion, get a print server and hook up to router..

---

### Post by chili555 on 2007-05-08
The method in the tutorial you referred to works perfectly for me if I remember to set the machine with the printer, Desktop in your case, with a static IP. In other words, if you set the address of the printer as ```
ipp://192.168.0.1/printers/<name of printer>
```and then tomorrow the machine boots with 192.168.0.5, assigned by DHCP, the laptop will never find it.

You will want to set the static IP outside the DHCP range in the router. For example, if you set the router to assign 10 addresses by DHCP, starting at 192.168.0.2, then 192.168.0.15 is a safe static IP address.

---

