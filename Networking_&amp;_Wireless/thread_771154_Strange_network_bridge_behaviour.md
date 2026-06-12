---
title: "Strange network bridge behaviour"
date: 2008-04-27
forum: Networking &amp; Wireless
---

### Post by mintochris on 2008-04-27
After upgrading to hardy (tested on a clean install as well though) my network bridge setup was behaving very oddly, my /etc/network/interfaces was;

*/etc/network/interfaces*
```
auto lo
iface lo inet loopback
iface br0 inet dhcp
bridge_ports eth0 eth1
auto br0
```

In gutsy this (along with a single *sudo ifup br0* after setup) was enough.
In hardy this meant that neither network card worked, I couldn't ping the router or reach the web.

I could fix it if i brought the network bridge down with
```
sudo ifdown br0
```
and raised it again with
```
sudo ifup br0
```
but ONLY if i accessed the internet BEFORE i issued the second command.

Eventually I tracked the problem down to a duplicated IP assigned to both br0 and eth1, so... finally, the important bit.

In hardy to get the network bridge working you must change /etc/network/interfaces to the following; (where eth* is your NIC that is connected to the internet)

*/etc/network/interfaces*
```
auto lo
iface lo inet loopback

iface eth* inet manual
up ifconfig $IFACE 0.0.0.0 up
down ifconfig $IFACE down


iface br0 inet dhcp
bridge_ports eth0 eth1
auto br0
```
and then reboot and type the following into the terminal
```
sudo ifup br0
```
then it should work, at least until the next update.
hope this helps someone, as it took me ages to work out!

---

