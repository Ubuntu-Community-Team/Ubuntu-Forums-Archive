---
title: "Need static ip address on my LAN"
date: 2007-12-04
forum: Networking &amp; Wireless
---

### Post by gjaffe on 2007-12-04
I just bought a Dell Vostro 400 desktop computer and put Ubuntu 7.10 on it.  It would not boot without my placing a network card in a pci slot, despite the motherboard having a network card already.  I can live with that, but I can't set it to have a static, private ip address.

When I try to do that with the networking applet in the panel --> Manual Configuration, I loose eth0 altogether.  It's not even listed with netstat -rn.  I have to take my static ip information out of /etc/network/interfaces and reboot to get eth0 back.

Anyone know how I can set eth0 to a static, private ip address?

Thanks.

---

### Post by wieman01 on 2007-12-05
Yes, I do... It is based on the WPA tutorial in my signature:
> sudo gedit /etc/network/interfaces
Then replace the contents with:
> auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.168.40
gateway 192.168.168.230
dns-nameservers 192.168.168.230
netmask 255.255.255.0
Replace the IP addresses with your own and restart the network:
> sudo /etc/init.d/networking restart
The Network Manager (that also handles wireless networks) can do DHCP only. The next release of Ubuntu will fix that, but for the time being you need to configure it manually.

---

### Post by gjaffe on 2007-12-05
That worked great. :)   Thank you so much.

BTW, I had to uninstall vmware server first.  Otherwise my

```
/etc/init.d/networking restart
```

command would just freeze.

---

