---
title: "WLan hangs with static IP address, fine with DHCP"
date: 2007-11-04
forum: Networking &amp; Wireless
---

### Post by orbister on 2007-11-04
I have a Toshiba Staellite Pro A120 running Gutsy.

I connects to my home network without problems if I tell it to use DHCP. However, it is useful to me to have a static address so that I can connect in by ssh from elsewhere in the house.

So I tell it to use a static IP address: 10.0.0.8. Netmask 255.0.0.0, gateway 10.0.0.2 (my router). DNS server is 10.0.0.2 as well: the router works as a DNS proxy.

When I do this the system can take an age to get a network connection - anything from 5 minutes to (apparently) infinite. Anyone got bright ideas why this should happen? I have a Netvista desktop, also running Gutsy, with the identical setup on a wired connection and it never has this problem.

---

### Post by kevdog on 2007-11-04
Are you sure that netmask is correct, rather than 255.255.0.0??   You want a class B network, correct??

---

### Post by jaydeflix on 2007-11-04
I'm getting something very similar, actually.  I get a connection but it randomly just drops and some amount of fiddling with disabling the network, unplugging the usb wifi dongle and switching from DHCP to static turns it back on, until an indeterminate time later, when it stops working again.

Unfortunately, my router doesn't give me the ability to give the machine a static ip address, but will accept a static ip address.

And yeah, everything seemed to be fine before the upgrade.

---

### Post by the ber on 2007-11-28
i get a similar problem. my wlan connection will work fine for a while, days or weeks, then suddenly it won't connect. when the connection is gone i can only ping my usb stick and nothing else. if i then change from static to dhcp, then suddenly the network is back. if instead i was already running dhcp, then i have to switch to static for the network to come back.
it doesn't seem to matter how i connect, at some point the network will be gone and i have to change to the other type of connection, and then the network is back.
any ideas?

---

