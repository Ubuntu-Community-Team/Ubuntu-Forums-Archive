---
title: "Ubuntu machines on the same network can't ping each other, but others can"
date: 2018-04-10
forum: Networking &amp; Wireless
---

### Post by larschrjensen on 2018-04-10
I've run in to an odd issue. 

I have two ubuntu 16.04 machines connected to the same wireless network. The network is a public guest network hosted by my university with no security. The two machines can't ping each other, but other machines(mac, windows, ubuntu from livedisc) on the same network can ping to both machines. Both of the machines can in turn also ping to any other machine. 

What I've tried so far:

```
sudo ufw disable
``` on both machines / no effect

```
iptables -L
``` returns only accept policies (input, forward, output) on both machines. 

When I insert a USB wifi dongle and deactivate the internal wifi interface it works and I am able to ping both ways, so something's up with the network interface I just can't figure out what. Since the network otherwise works fine, I'm assuming it's a software issue.

Any ideas?

---

