---
title: "Static IP Woes"
date: 2008-01-24
forum: Networking &amp; Wireless
---

### Post by Chebyshev on 2008-01-24
I'm trying to set a static IP for this box (Gutsy). I tried with the System->Administration->Network panel and that didn't work at all, so I edited /etc/network/interfaces and added:
```

auto eth0
iface eth0 inet static
        address 192.168.1.2
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.1
```

then I run 
```
sudo /etc/init.d/networking restart
```
and the static IP works.

Then like 10 hours later (after sleep), the IP of the machine is back to 192.168.1.104. It is like it decided it didn't want to be static and went out and requested an IP from the DHCP server!

Anyone know what I've screwed up?

---

### Post by chewearn on 2008-01-25
Top Panel Menu > System > Administration > Network

You will be prompted for the admin password, then the "Network Settings" dialog will pop-up. Select your network interface from the list, then click Properties, uncheck Roaming, and then specify your static IP configurations.

Why won't this work?

---

### Post by Chebyshev on 2008-01-29
I don't know why it didn't work, but when I changed that stuff in the Networking panel, ifconfig showed no IP for eth0.

---

