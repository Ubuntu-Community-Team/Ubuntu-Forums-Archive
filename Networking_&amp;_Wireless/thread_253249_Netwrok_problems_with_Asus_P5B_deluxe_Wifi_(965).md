---
title: "Netwrok problems with Asus P5B deluxe Wifi (965)"
date: 2006-09-08
forum: Networking &amp; Wireless
---

### Post by amonsul on 2006-09-08
Hi all!

I have BIG problems with Ethernet-connection. Wifi dont works, normal LAN dont works.

My Hardware:
-Motherboard Asus P5B deluxe (wifi) 965
-Cpu Conroe 6600

Here some terminal output:

> root@amonsul-desktop:~# lspci | grep Ethernet
0000:02:00.0 Ethernet controller: Marvell Technology Group Ltd.: Unknown device 4364 (rev 12)
0000:05:04.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 14)
root@amonsul-desktop:~#

and

> root@amonsul-desktop:~# egrep -v "Ë†$|Ë†#" /etc/network/interfaces
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


iface wlan0 inet dhcp
wireless-essid admin
wireless-key amonsul77

root@amonsul-desktop:~#
root@amonsul-desktop:~# egrep -v "Ë†$|Ë†#" /etc/resolv.conf
root@amonsul-desktop:~#
root@amonsul-desktop:~# egrep -v "Ë†$|Ë†#" /etc/hosts
127.0.0.1 localhost amonsul-desktop
127.0.1.1 amonsul-desktop

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
root@amonsul-desktop:~#


I have already disabled WIFI but it doesnt works...

---

### Post by amonsul on 2006-09-09
With Windows all works fine. What can i do?

---

### Post by amonsul on 2006-09-10
Ok, I´ve solved the problem. It was a Bios-setting. 
Thank you all ](*,)

---

### Post by jespdj on 2006-09-12
> **amonsul said:**
> Ok, I´ve solved the problem. It was a Bios-setting. 
Thank you all ](*,)

Can you please tell us what BIOS setting?

I have the same (Asus P5B Deluxe + Intel Core 2 Duo E6600) and my network isn't working as well (neither WLAN, nor Ethernet).

---

### Post by devnu11 on 2006-12-05
Is there a solution to this Marvell LAN not functioning?  In Edgy one of the two nic's show up as eth0.  I would like to get the second to function.

---

### Post by montgoja on 2006-12-23
My ethernet works fine... don't know if both ports work or not.  No problems with connecting on the internet when I'm on campus.  My problem is trying to get the integrated WiFi (AP Solo) to work on my Edgy partition.  We just got DSL at home and decided to make everything wireless (yay for DSL vs. Dialup, but boo for WiFi now).  Installed the WiFi AP Solo software on my Windows partition, everything was fine, but don't know what to do on Linux.  Any other programs and things that I would have to download have to be done through Windows.

---

### Post by montgoja on 2006-12-23
devnu,
Try going to ASUS's site for the P5B Deluxe.  [http://www.asus.com/products4.aspx?modelmenu=1&model=1179&l1=3&l2=11&l3=307](http://www.asus.com/products4.aspx?modelmenu=1&model=1179&l1=3&l2=11&l3=307)

Left hand side of the page, there's a section marked Downloads.  There's a Marvel Ethernet download for linux systems.  It involves some kernel compiling and all, and I realized it wasn't going to help me any to go through all that, since it wasn't my ethernet that I needed to activate.

Hope that helps!

---

