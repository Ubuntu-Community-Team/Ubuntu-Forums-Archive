---
title: "Separate LANs"
date: 2008-11-05
forum: Networking &amp; Wireless
---

### Post by rayfidelity on 2008-11-05
Hi,

I'd like to setup 2 totally different LANs on Intrepid...
I have 2 interfaces, i'd like the first one (eth0) to be setup by DHCP...this part is already done automatically...

Now the problem...the second interface will be used for IPTV from a different provider than the internet part (differet GW,netmask,ip range,...)...

eth1 needs to be static with it's own gateway,netmask,...

How to setup the eth1 so that it wouldn't interfere with eth0 (internet connection).

I've tried it by editing /etc/network/interfaces but it didn't work together...if internet was working IPTV wasn't and the other way around...

Thanks!

---

### Post by rayfidelity on 2008-11-06
Anyone??

---

### Post by superprash2003 on 2008-11-06
could you post your interfaces file here.. did you restart networking after your made changes to the interfaces file?

---

### Post by rayfidelity on 2008-11-06
i've already gone back to the original config...

but it was like this
--------------------------
auto eth0
iface eth0 inet dhcp

iface eth1 inet static
address 10.112.113.114
netmask 255.255.255.0
broadcast 10.112.113.255
gateway 10.112.113.1

ip's are made up...

The problem was that it always started using DNS from eth1 (which should be IPTV - no internet traffic allowed)

---

### Post by its_johan on 2011-11-13
Was this ever solved ? I have the same problem at the moment but no sollution.

---

