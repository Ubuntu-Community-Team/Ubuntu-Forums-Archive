---
title: "help with DHCP"
date: 2013-12-14
forum: Networking &amp; Wireless
---

### Post by ulao2 on 2013-12-14
I got he following code to fix an issue with my old android deice but I dont know where to put it?  I'm running Apache2 and have installed a dhcp server. this example was for a [dnsmasq]("http://www.thekelleys.org.uk/dnsmasq/docs/dnsmasq.conf.example"). Does umbuntu have this file somewhere or can I use iptables?



#dentify android devices
dhcp-mac=android,A0:75:91:B0:97:*


# Disable classless static routes for Android
dhcp-option=android,121,0.0.0.0/0,192.168.0.91

---

### Post by ulao2 on 2013-12-15
I was able to make it work using isc-dhcp-server like so:

host android-metroPCS {
  hardware ethernet A0:75:91:B0:97:60;
  fixed-address 192.168.0.91;
}

---

