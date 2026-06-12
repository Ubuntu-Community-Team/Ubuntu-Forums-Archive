---
title: "Wireless on boot (feisty)"
date: 2007-03-31
forum: Networking &amp; Wireless
---

### Post by myquidproquo on 2007-03-31
Hi.

I'm having problems with my wireless not connecting on boot. 
I need to use the address 192.168.1.105.

In interfaces I have 

auto wlan0
iface wlan0 inet static
wireless-essid RedeWireless
wireless-key _________
address 192.168.1.105
netmask 255.255.255.0
gateway 192.168.1.1

As I was having problems with "Network Manager" I have disabled it.
Now I go to "Network" every boot and change connection to DHCP and then back to static and it works.

---

### Post by Drate on 2007-03-31
Is your Access Point using a WPA password?

What kind of wireless card are you using?

---

### Post by myquidproquo on 2007-03-31
No WAP.

The Wireless works, I have no problem with it. Just need to go to "Network", change to DHCP and back to static.

---

### Post by myquidproquo on 2007-03-31
Solved

Ifdown wlan0
ifup wlan0

to /etc/rc.local

I know that this is not the best solution, if you know a better way let me know.

Thank you.

---

