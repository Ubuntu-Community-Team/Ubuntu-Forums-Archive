---
title: "internet connection on eth1"
date: 2009-03-21
forum: New to Ubuntu
---

### Post by frogchild on 2009-03-21
hi all. First I have to say that i am loving linux - although I feel way out of my depth the challenges are great - most of the time because the people here are friendly and very helpful, so thank you so far for all the info that has been available to help me with my little problems :-)

However I have now created a problem due to lack of knowledge I guess. when I was in a hotel I could not get connected via Ubuntu but could via XP. I looked this problem up and found that I needed to change a few things - this is what i did:
sudo gedit /etc/network/interfaces
I changed theses setting from - auto lo
iface lo inet loopback

to

auto dchp eth1
iface dchp inet eth1

The reason for eth1 as i understood was because when I first installed ubuntu and connected to the internet via cable that was shown in network connection when i left click on the two little computers.

Any the wired version did not work but for some reason the wireless version did. great i thought until i got back home :-(

I connected and nothing.

so i went back to sudo gedit /etc/network/interfaces
and re-entered
auto lo
iface lo inet loopback

still nothing. I then read about something similar so i added auto eth1 in another line under iface.

at this point i would like to add so there is no confusion i did type sudo /etc/init.d/networking restart when ever i made any changes but still
nothing. i read further and find more info.

an answer to a similar problem suggested to type this:

sudo dhclient eth1

the out put is this:

There is already a pid file /var/run/dhclient.pid with pid 8147
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:10:c6:c0:4a:98
Sending on   LPF/eth1/00:10:c6:c0:4a:98
Sending on   Socket/fallback
DHCPREQUEST of 192.***.1.*** on eth1 to 255.255.255.255 port 67
DHCPACK of 192.***.1.*** from 192.168.1.254
bound to 192.***.1.*** -- renewal in 42361 seconds.

result i get a connection, however this does not show in my network connections - the two little computers do not turn into green dots with the blue swurrling around they just stay computers with an exclamation mark.

So with regards to this - please could someone tell me what i am doing right and then what is wrong?


2ND problem - now my wireless sees the network goes to connect but gets nothing - I know it is trying to get an IP because the green dots come back but nothing. If you need more info to help with this 2nd issue then please tell what to type in a terminal and i will post again.

Thank you in advance for your help

---

### Post by frogchild on 2009-03-22
:(

---

