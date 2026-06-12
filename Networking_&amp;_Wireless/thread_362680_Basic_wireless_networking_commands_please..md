---
title: "Basic wireless networking commands please."
date: 2007-02-15
forum: Networking &amp; Wireless
---

### Post by telovoyagarcar on 2007-02-15
Im trying to configure the card manually, because i set my router to not be a DHCP server.

These commands are the ones im using, but i cant get connected to the internet. I can ping my router though...

ifconfig ath0 192.168.2.5 (that sets the ip fine)

iwconfig ath0 key XXXXXX (my wep key)
iwconfig ath0 channel 6 (sets the card to channel 6 like my AP)
route add default gw 192.168.2.1 ath0 (adds the default gateway)
ifconfig ath0 up (brings up the interface?)

and i also tried

echo nameserver 192.168.2.1 >> /etc/resolve.conf

I dont know what else i need. because all this will not get me connected to the internet.

If i use DHCP, i can get connected without problems... but i need to keep things manual in this case.

Any clue?

---

### Post by spd106 on 2007-02-16
The Debian/Ubuntu way is to edit the /etc/network/interfaces file. Then use ifup and ifdown to control the interface. 
It should look like this ```
$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto ath0
iface ath0 inet static
address 192.168.2.5
netmask 255.255.255.0
gateway 192.168.2.1
wireless-essid linksys28
wireless-key 0123456789

```
These line are the ones that are necessary for a static address, you can add others.

---

