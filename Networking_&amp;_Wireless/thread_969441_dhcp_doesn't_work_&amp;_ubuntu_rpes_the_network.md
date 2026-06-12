---
title: "dhcp doesn't work &amp; ubuntu r*pes the network"
date: 2008-11-03
forum: Networking &amp; Wireless
---

### Post by rattusdatorum on 2008-11-03
hiya,

had Ubuntu running a while with static ip address and everything, now I moved and tried to get it working on the network of my sister, which works with dhcp.

Checklist:
1) Hardware works
2) Windows works (yeah, I have dual boot)
3) others pcs on the network work (all windows)
4) purged the /etc/network/interfaces file
 a) auto eth0
    iface eth0 inet dhcp
 b) only localloop + network manager on roaming mode.
5) sudo dhclient -> no DHCPOFFERS received

well, it doesn't work and to make matters worse - and trying to fix the problem more difficult - is the fact that my attempts to make it running f*cks up the network router/switch. (At least all the other computers can't establish an internet connection anymore (windows tells they can't refresh the ip address, hence the dhcp seems to be f*cked up).) I need to restart - read PULL THE PLUG for - those little blinking boxes on the top of the shelf.

<annoyance of low priority>
A further yet only little annoyance is the eth0:avahi, I deactivated the "avahi" service, yet this device dares to reappear - I tried to shut it down with "ifconfig eth0:avahi down" but it gets reactivated if I use sudo dhclient. I hate this little device since it gets a ip4 address and MY eth0 doesn't! Also the ip address appears to be totally random, weird and a lot of other stuff I don't like, especially because it shouldn't be there ;)
</annoyance of low priority>

any help is really appreciated!

greetings

---

