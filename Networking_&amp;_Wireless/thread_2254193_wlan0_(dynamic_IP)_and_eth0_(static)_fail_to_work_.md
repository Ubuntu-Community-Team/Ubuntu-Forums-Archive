---
title: "wlan0 (dynamic IP) and eth0 (static) fail to work simultaneously"
date: 2014-11-25
forum: Networking &amp; Wireless
---

### Post by thekiwi5000 on 2014-11-25
Hello,

On my pc I need to have both wlan ( to have intenet access) and ethernet (to ssh to my raspberry pi) up. The problem is that after connecting crossover cat5 cable to my PC eth0 and RasPi eth0, my PC transfers all of the network traffic to eth0 making me unable to connect to the internet.

 I need to have ability to browse the internet from my PC, while being connected to raspi.
I know that this needs to be done with two IP families ( avail. 10.0.0.X , and 192.168.0.X ), but i don't know how to make it.

I'm on ubuntu 13.04 .


Several additional notes:
 [I]- wlan0 must be given dynamic IP, because the crappy ISP's router rejects manually-set IP connections.
 - eth0 must have mannually-set IP, because there's no DHCP between PC and RPi.
 - it would be nice if RPi could connect to the internet via my PC.[/I]

---

### Post by sotiris2 on 2014-11-25
Well for connecting a laptop to my desktop directly I did click on network indicator, selected edit connections, chose wired connection 1 (choose applicable) and set IPv4 Settings -> Method to Shared to other Computers. I didn't touch my desktops wifi connection (i did disable the laptop's one) and it worked, I actually think my laptop got 'seen' by my router and got assigned an I.p. via it.

---

