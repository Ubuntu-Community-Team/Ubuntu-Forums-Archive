---
title: "Wireless WPA, not working before network restart"
date: 2007-01-17
forum: Networking &amp; Wireless
---

### Post by MerZo on 2007-01-17
Hi!

I have a problem with my connection. I followed the guide in the sticky and somehow managed to get the network up and running. At least that was what I thought. :-D 

My problem is the following. I can get an IP-address when i run the command sudo /etc/init.d/networking restart but not when I boot the computer, it tries to initilize the network i think, the leds are working but it doesnt get anywhere.. Something isnt working at bootup because when I run the 'restart' everything works.

This is the output:

Listening on LPF/ath0/00:0d:88:a5:0b:4e
Sending on   LPF/ath0/00:0d:88:a5:0b:4e
Sending on   Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 6
DHCPOFFER from 192.168.0.1
DHCPREQUEST on ath0 to 255.255.255.255 port 67
DHCPACK from 192.168.0.1
bound to 192.168.0.103 -- renewal in 285761 seconds.

This looks normal I think? The only problem is that it takes some time before the network gets an IP, using ethernet it goes in a jiffy. Now it is just slow but eventually gets it.

HELP. Please. Reboot the network on a newly started computer is all but fun.

---

