---
title: "Problem establishing a connection using wlan0, eth0, usb0 and so on"
date: 2015-10-07
forum: Networking &amp; Wireless
---

### Post by henrique11 on 2015-10-07
Hello everyone

I've been using my Ubuntu 14.04 installation for a year on my laptop (Sony Vaio) and all of sudden I wasn't capable of connecting to my Wifi Access Point anymore. What happens is that the Wifi icon on the top right never indicates that the connection is estabilished.

I started to investigate and found out that issuing the command "dhclient -v wlan0" I get an IP and could establish a connection with the Internet, but not for long, in about 20 seconds or so I get the same problem again, when I run ifconfig I notice I don't have an IP address anymore. It works for another 20 seconds if I run dhclient again.

I tryed to use the access point mode of my cell phone but the problem is the same, I also tryed USB tethering mode of my phone, but the problem is also the same with my temporary usb0 interface.

So to try to have an Internet connection to search for a solution I started using eth0, I found out that the problem is the same, excepts that dhclient doesn't work for 20 seconds, but fixing an adequate IP address, gateway, etc via /etc/network/interfaces the connection works fine, so at least I have an internet connection right now at home.

Does anyone can help me with that problem which is apparently dhcp related? If I fix de wlan0 I have no connection at all, the network-manager simply disapears so it is not a solution right now.

Thank you so much.

---

### Post by henrique11 on 2015-10-09
Hello

Couldn't solve this. I did what is suggested on the thread "Before posting...". I can't post the output here because this page does not allow me to do so, but it's here anyway [http://pastebin.com/S6EqNrfH](http://pastebin.com/S6EqNrfH). I also tryed uninstalling and installing network-manager and many other things found on the Internet.

What strikes me more is how an operational system fails like that...estabilishing an Wi-Fi connection shouldn't be a task for operational system experts and we're not in 1997 when you cold brag about having a linux box running, anyway there is no easy way to solve the problem other than reinstalling the entire system, someting that would be an awkward solution even for a Windows 95 user...

Plus it's not driver specific issue since no interface works, it's pure operational system problem that should be easy to fix.

---

### Post by henrique11 on 2015-10-10
Just uninstalled network-manager and installed wicd instead. Wi-Fi connection works fine.

---

