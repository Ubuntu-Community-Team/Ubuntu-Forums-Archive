---
title: "wired network connection not working"
date: 2007-02-04
forum: Networking &amp; Wireless
---

### Post by carnytom on 2007-02-04
Hi, i'm new to linux.. I first booted from the live CD and everything seemed to work great. So I ran the install and everything was still fine. I then updated my nvidia drivers (unsing the command found on the ubuntu help page). I rebooted and no have no network connection. 

when I cat /etc/network/interfaces  I get 

auro lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

.. 

I then tried booting the live CD and got the same results no nework
I shutdown and added a new NIC (first NIC is onboard). 
Same results with the new NIC. 

Anyone have any ideas?????

---

### Post by gradedcheese on 2007-02-04
I'm guessing eth0 is your onboard NIC.  If so, try:

sudo ifconfig eth0 up
sudo dhclient eth0

dhclient will attempt to get an address (via DHCP), printing its status.  What happens?  ALso I would edit /etc/network/interfaces and comment out the lines for eth1 and eth2 since they probably don't exist (you can put a '#' in front of a line to comment it out).  

when the 'networking' script runs, it parses /etc/network/interfaces and sets things up according to what it finds.  When it sees lines like:

auto eth0
iface eth0 inet dhcp

it runs dhclient.  So if you have 'extra' interfaces in there, you can comment them out and run again like this:

sudo /etc/init.d/networking restart

---

