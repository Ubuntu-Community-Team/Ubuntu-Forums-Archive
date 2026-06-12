---
title: "Home networking question"
date: 2007-07-28
forum: Networking &amp; Wireless
---

### Post by PaulFXH on 2007-07-28
We have three computers on our home network all of which are connected (wired) to a Netopia 3347WG router.
One computer (multiboot - various Linux and XP) has a static IP (192.168.1.137) which, in general, works fine.
Another (Vista only) uses DHCP and also works fine.
The third (dual boot - Ubuntu and XP) did use the same static IP as the first one. However, I found that when this computer was on a large (>100 MB) download, it stopped downloading after 10-20 minutes.
I fixed this, to my surprise, by switching the network connection to DHCP. Is this behaviour normal?

Just to throw in a second question here; the first computer wih several OSes uses the same static IP on ALL (including XP) OSes except for one (Mandriva) which only sustains an internet connection if the static IP is set to 192.168.1.139 (with the same DNSes).  The expected 192.168.1.137 gives absolutely no connection to the internet. In addition, although DHCP does give some connectivity, it is abominably slow.Can this be explained as other than an act of God?

Note that the router has only ONE enabled static IP (NAT) which is the 192.168.1.137

Thanks 
Paul

---

### Post by KyleBrandt on 2007-07-28
First, computer one and computer two can not share the same IP, this will cause an IP conflict, and this is bad.  Not sure if that is what you are doing, but just to make sure.  By this I mean that two computers can't have the same IP at the same time--every computer on your network must have a unique ip address.

Second, are you sure you really want to be using static ips?

---

### Post by PaulFXH on 2007-07-29
> every computer on your network must have a unique ip address.
Thanks for the reply. 
Our router seems to only allow ONE enabled static IP. Therefore, based on what you said, only ONE of our computers can have a static IP. The other two MUST use DHCP.
> are you sure you really want to be using static ips?
Can't say that I am. Only did this because of some P2P stuff I was doing on Azureus some time ago but I rarely, if ever, use this now.  You question suggests there are disadvantages associated with a static IP.

Thanks
Paul

---

### Post by noob12 on 2007-07-29
Yeah, so "normally" one would have the one static IP on the outside of a NAT-ing gateway router, and a mix of static (but unique) and dynamic addresses (also unique) all on a private network inside that gateway router.  You would maybe forward a few selected ports to servers inside that net.

---

### Post by KyleBrandt on 2007-07-29
The disadvantage of static routing is that you have to maintain it.  This becomes more of a real disadvantage if you have a large network.  If you are not using port forwarding anymore (what you needed to do to get Azureus to work), then you should probably just switch them all to DHCP.  And if you are going to use bit torrent only rarely, just enable port forwarding for whatever ip when it is needed, and disable when you are done.

---

