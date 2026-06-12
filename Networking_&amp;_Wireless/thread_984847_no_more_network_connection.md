---
title: "no more network connection"
date: 2008-11-17
forum: Networking &amp; Wireless
---

### Post by dunskii on 2008-11-17
Hello all,
The other day my PC turned off unexpectedly due to a blackout, when everything came back up one of my PC running 8.04 no longer had a network connect.  

At first I thought the NIC may have got fried but all the right lights were flashing and ifconfig -a returns the mac address etc. I´ve  tried roaming, dhcp and static ip addresses with no luck.  

In my haste I followed a forum post blindly which recommended apt-get remove network-manager net-tools.  I have recovered some of the removed items but not all.

If I do dhclient eth0 I get No DHCPOFFERS received

Is there a way to reset all the network settings like after a fresh install.

Any help would be greatly appreciated.
Cheers,
D :confused:

---

### Post by jnorthr on 2008-11-17
Just a wild shot here: It sounds that your router is no longer giving the offer to the same i/p address as your machine had before the power failure. As i understand it, the NODHCPOFFERS is because the server or router won't allocate an i/p address to your system cos it already has an i/p address - just not the same one as before. 
you could try 
[COLOR="Red"]ifdown eth0[/COLOR]
then[COLOR="Red"]
ifup eth0[/COLOR]
to restart your network.

---

### Post by Bucky Ball on 2008-11-17
Try this in a terminal:

[B]sudo /etc/init.d/networking restart
[/B]
That should look for any dhcp servers if they are about.

---

