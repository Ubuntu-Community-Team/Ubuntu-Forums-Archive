---
title: "Why I have to do: &quot;sudo dhclient eth0&quot; for connect to Internet"
date: 2008-04-03
forum: Networking &amp; Wireless
---

### Post by manuparra on 2008-04-03
I haven't internet connection, but when i use:  sudo dhclient eth0, i have internet connection.

I don't know, why always i have to do it for internet works.

Thanks in advance.

---

### Post by kevdog on 2008-04-03
You are either missing the auto eth0 line in your /etc/network/interfaces file, or you are trying to connect manually.  Either way the line dhclient eth0 asks your dhcp server or router to give you a dynamically assigned IP address.  Obviously you get one, and then can use the internet.

---

### Post by manuparra on 2008-04-03
This is my Innterfaces File:

auto lo
iface lo inet loopback


iface eth0 inet static
address 192.168.1.185
netmask 255.255.255.0
gateway 192.168.1.1

auto eth0

Did yo refer auto eth0?

Thanks

---

### Post by kevdog on 2008-04-03
try this:

auto eth0
iface eth0 inet static
address 192.168.1.185
netmask 255.255.255.0
gateway 192.168.1.1

---

