---
title: "What commands runs network-admin to bring up/down a network interface ?"
date: 2007-05-04
forum: Networking &amp; Wireless
---

### Post by nightrain on 2007-05-04
Hi all.

Mi laptop has a Dlink DWL-G650+ wireless card. This card is supported by ACX driver but that driver does not support WPA. So I had to install ndiswrapper and dlink driver for windows, configured wpa and everything works fine. I wrote a shell script to automate the installation of ndiswrapper driver and then brings down and up the card. That script works sometimes and other do not and I dont know why. If I run network-admin, uncheck and check de wifi card, it starts running inmediatly. So I wonder what runs network-admin when I do that.

My script is something like this: 

ifconfig wlan0 down
rmmod acx
ndiswrapper -i /usr/local/wifindiswrapper/GPLUS.inf
modprobe ndiswrapper
ifconfig wlan0 up
sleep 3
ifdown -v wlan0
ifdown eth0
ifup -v wlan0

---

