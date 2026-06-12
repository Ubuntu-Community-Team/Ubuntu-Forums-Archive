---
title: "Routing or Bridging Between Local Subnets"
date: 2014-08-03
forum: Networking &amp; Wireless
---

### Post by Brett_Johnson on 2014-08-03
HI;

I have a Ubuntu 13.10 box in my shop about 400 feet from my house which contains my internet connection. I currently have the following setup:

wlan1 - connectected to my house via wifi
IP: 192.168.0.200/24
wlan0 - setup with AP-Hotspot for shop wireless internet
IP: 192.168.150.1/24
eth0 - setup for internet sharing.
IP: 10.42.0.1/24
Currently almost everything works great.  Systems on the eth0 subnet can access the internet and can ping other systems on all other subnets including subnet 192.168.150.0. However, systems on the AP (wlan0) can't ping systems on the eth0 subnet 10.42.0.0.

I understand that I'll need to either find a way to create a bridged connection between wlan0 and eth0 on the same subnet or create a route between the subnets.  I'm not sure which is best, nor do I have a clue how to do either method.

Any help will be greatly appreciated
Thanks
Brett

---

### Post by TheFu on 2014-08-05
[http://www.ubuntu.com/info/release-end-of-life](http://www.ubuntu.com/info/release-end-of-life) - is where I'd begin.  13.10 support ended last month.

Then I'd use iptables to create the routing necessary, like it was a VPN server. The output from route and iptables -L might help someone to help you.

---

