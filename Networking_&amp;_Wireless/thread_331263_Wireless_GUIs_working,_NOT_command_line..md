---
title: "Wireless GUIs working, NOT command line."
date: 2007-01-04
forum: Networking &amp; Wireless
---

### Post by skela on 2007-01-04
I have a very strange problem indeed. My wireless (ipw2200) card on my HP dv1170ea laptop works fine most of the time, as long as I tell it EVERYTHING. I mean, at home, dhcp does not work, so I need to input everything manually. (DHCP not working wireless, but works flawlessly with wired connections, this is not the problem though).

So I input everything in the GUI, static IP, gateway, dns, essid, key.
However when trying this in command line, it simply does not work. Doesn't give me an error message, and everything looks fine with ifconfig and iwconfig. It just does not work.
This is the normal routine I do to set up a wireless connection via command line

sudo -s
ifconfig eth1 down
ifconfig eth0 down
sudo ifconfig eth1 up 192.168.0.54
sudo iwconfig eth1 essid "netname" key XXXXXXXX..
sudo route add default gw 192.168.0.1

eth0 is my wired interface, eth1 my wireless, 192.168.0.54 my desired ip and 192.168.0.1 my gateway. 
Any help would be much appreciated..

---

### Post by spd106 on 2007-01-04
What kind of key are you using, is it hex or a passphrase. You usually need to prefix it with an s: if it's not hex.

---

### Post by skela on 2007-01-04
So the GUI and command line use different standards?
I simply input the same key in both, 
it's a 13 number combination, could be hex, but not sure, due to all
of the numbers being below 10

---

### Post by skela on 2007-01-04
spd106, you sir, are a golden god! Cheers mate :D

---

