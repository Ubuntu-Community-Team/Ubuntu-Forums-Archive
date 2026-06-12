---
title: "bridging problems"
date: 2016-08-23
forum: Networking &amp; Wireless
---

### Post by betchern0t on 2016-08-23
Hi,
      I have had to change a motherboard in my VM host. This motherboard has an R8168 based nic built in. I am finding that it doesn't work:

1) checked connectivity with a USB NiC (DM9601) with the same results so it is not hardware related but must be software/config

2) When either card are used with the bridge down and the card not linked as a port of the bridge, the networking works

3) When either card are used with the bridge up and the card as the first interface on the bridge the networking doesn't work.

4) if the bridge is then brought down and the card is removed from the bridge, networking is still tanked.

5) the cable is connected to a simple 10/100 switch that is part of my home network

Configuration 

1) The only MACs seen are local
2) All ports apart from the bridge itself are forwarding
3) behaviour is the same whether STP is on or off
4) ebroute reports all empty rules
5) ifconfig reports things as up when they should be up

Not sure what to look at or where to go with this. Any suggestions are welcome

Cheers Paul

---

### Post by betchern0t on 2016-08-25
Hi,
    this seems to be now fixed. One of the big weaknesses of the whole Linux packaging system is that it is quite hard to install software if you don't have an internet connection. In this case I installed the latest drivers for the r8168 manually and something probably went wrong. In the end I brought up a nic on my network and used apt to upgrade all packages to the latest. On a reboot that seems to have solved the problem. The other thing I did which I think had nothing to do with the problem was change the bridge to DHCP rather than static. This was to allow me to update my ipfire firewall to match the new mac address with the static ip.

Cheers Paul

---

