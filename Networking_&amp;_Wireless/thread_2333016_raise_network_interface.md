---
title: "raise network interface"
date: 2016-08-06
forum: Networking &amp; Wireless
---

### Post by codemachine on 2016-08-06
i am unable to boot faster to my linux server 16.04 due to a start job is running for raise network interface. i have to wait for approx 5 min for this job. but whenever ethernet cable is connected this it boots normaly. how to fix it

---

### Post by chili555 on 2016-08-06
If this is a server, may I assume you are not running a desktop environment and therefore, not running Network Manager? If so, then I assume you have declared the connection details in /etc/network/interfaces. If so, and if your file contains the usual line, 'auto enp3s0' or similar, then the 'auto' part means that the system is to automatically connect when it is booted. 

If you boot with the ethernet cable detached, you are asking the system to connect when no connection is possible. It tries, fails, tries again, fails, etc.; hence the long pause.

You can either boot with the ethernet attached or else comment out the 'auto' line:```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
[COLOR="#FF0000"]#[/COLOR]auto enp3s0
    iface enp3s0 inet static
    address 192.168.0.100
    netmask 255.255.255.0  
    gateway 192.168.0.1
    dns-nameservers 8.8.8.8
```That tells the system that it needn't connect automatically; you will tell the system to connect at a later time:```
sudo ifup enp3s0
```Generally, a server sits in the closet and is connected at all times, so the default behavior is generally correct.

---

