---
title: "wlan0 to browse network eth0 for internet"
date: 2006-11-27
forum: Networking &amp; Wireless
---

### Post by sonni_kuba on 2006-11-27
I have tried to make the title as descriptive as possible :-k 

I have two cards attached, and detected, wlan0 and eth0.
As my internet connection, is MUCH faster on eth0, I was wondering if there is an easy way to assign ALL internet traffic to eth0 and dedicate wlan0 for local network browsing and printing.:confused: 

Thank you in advance,
kuba

---

### Post by king20878 on 2006-11-27
Hi 

Can you give a more complete description of your network setup?  Do you have a router, other computers that need to access the internet, etc?

---

### Post by sonni_kuba on 2006-11-27
Yes, of course, I should have included that info 

Computer 1 - Ubuntu 6.10 x86_64 
           - connected to internet (wired) eth0
           - connected to Computer 2 (wireless) wlan0

Computer 2 - Windows XP Pro
           - connected to router (Linksys)
           - connected to local printer
           - part of MSHOME         

Router - broadcasting SSID (WEP enabled)
       - other laptops (Win32) connect to Computer 2 for printer


Output of /etc/network/interfaces

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface

iface eth0 inet dhcp

iface wlan0 inet dhcp
wireless-essid XXXX
wireless-key ABCDEABCDE

auto wlan0

auto eth0

---

### Post by koenn on 2006-11-27
You'll probably be able to do this by adding routes :
a route to your private lan via wlan0
a route to (anything else - i.e. the internet) via eth0

This can be done in /etc/network/interfaces, as explained here :
[http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch03_:_Linux_Networking#Adding_Permanent_Static_Routes_2](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch03_:_Linux_Networking#Adding_Permanent_Static_Routes_2)

this requires static up addresses. 
I would try that and see if it works. 
If it does, you can try and see if you can configure the dhcp server to pass default gateway information so you can repeat this setup with dynamic addresses.

---

### Post by king20878 on 2006-11-27
I'm a bit confused as to why connecting both computers through the router (wired) is not an option, and why wireless is necessary at all on Comp 1?  

I'm obviously missing something.

---

