---
title: "Problems with DHCP and NetworkManager"
date: 2007-05-12
forum: Networking &amp; Wireless
---

### Post by microsatan on 2007-05-12
Hello

Im using Ubuntu Desktop 7.04

Interface eth0 is set to get an IP via DHCP, but I dont want it to get any information about DNS servers, because im already running bind on my system and I have static entries in named.conf

So, I edited /etc/dhcp3/dhclient.conf so that the request line just got the bits i needed (everything except DNS servers) like this..
[FONT="Courier New"]
request subnet-mask, broadcast-address, time-offset, routers;[/FONT]

But now  it turns out that my /etc/resolv.conf file is being overwritten by NetworkManager -- with empty entries.

I had the nameserver set to the static IP of my second interface (eth1), but everytime I boot up NetworkManger overwrites this with blanks. 

Anyone know how to stop this from happening? I dont think I need NetworkManager running anyway, how do I disable it?

---

### Post by Psquared on 2007-05-14
I am not certain this will work, but you might try to uninstall network manager using synaptic. It will remove ubuntu-desktop which is no big deal.

Then edit /etc/resolv.conf manually.

---

