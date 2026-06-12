---
title: "Trouble with automating network connection"
date: 2007-07-14
forum: Networking &amp; Wireless
---

### Post by Carleton91 on 2007-07-14
I can connect to my wireless router fine manually, but when i try to automate it by editing the /etc/networking/interfaces file, it is unsuccessful.

My interfaces file looks like this:

auto lo
iface lo inet loopback

iface wlan0 inet dhcp
wireless-essid "2WIRE154"
wireless-key 3127487812

auto wlan0

This doesn't connect my on a reboot or on doing /etc/init.d/networking restart.
Instead i am forced to do it manually with
sudo ifconfig wlan0 down
sudo iwconfig wlan0 essid "2WIRE154"
sudo iwconfig wlan0 key 3127487812
sudo ifconfig wlan0 up

---

### Post by kevdog on 2007-07-14
I remember this problem about a week ago and I still cant explain it.

Can you change this:
iface wlan0 inet dhcp
wireless-essid "2WIRE154"
wireless-key 3127487812

auto wlan0

to
auto wlan0
iface wlan0 inet dhcp
wireless-mode Managed
wireless-essid "2WIRE154"
wireless-key 3127487812

What if you dont use the quotes when specifying the wireless-essid name?

Does that make any difference??

---

