---
title: "Installling NIC"
date: 2007-03-25
forum: Networking &amp; Wireless
---

### Post by JengaBlocks on 2007-03-25
Need help installing a DLink DFE 530TX+ NIC. 

/etc/network/interfaces reads:

iface lo inet loopback
iface eth0 inet static
address 192.168.0.2
netmask 255.255.255.0
gateway 102.168.0.1

Ping is getting me "Network is unreachable"

Any ideas?

---

### Post by chili555 on 2007-03-25
I hope your interfaces file reads more like:```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.0.2
netmask 255.255.255.0
gateway 1**9**2.168.0.1

```

After you amend the file as noted, please restart networking sudo /etc/init.d/networking restart and try your ping again.

---

### Post by JengaBlocks on 2007-03-25
Thanks Chilli... that did the trick with the auto's... I also noticed I made a mistake as I had two systems sharing the same 192.168.0.2 IPs. Of all things my Windows box notified me of the problem! :shock: 

Ok one down, one more to go. Next up - the Linksys WMP54G ](*,)

---

