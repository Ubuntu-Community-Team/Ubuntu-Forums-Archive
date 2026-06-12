---
title: "ifconfig eth0 resets configuration"
date: 2007-06-29
forum: Networking &amp; Wireless
---

### Post by MacacoPreto on 2007-06-29
Hello

I did this:
sudo ifconfig eth0 xxx.xxx.xxx.xxx netmask yyy.yyy.yyy.yyy

but after a few minutes or when I log off it resets to it's previous DHCP configuration.  Is there any step I'm skipping to commit changes? :confused:

---

### Post by spd106 on 2007-07-01
It's probably a good idea to kill the dhclient process before you do this.

Usually I take the interface down like this.
```
sudo ifdown eth0 
```
That script should kill off any processes associated with the interface. Then in order to bypass the automatic starting of those processes instead of running ifup use ifconfig up. i.e.
```
sudo ifconfig eth0 x.x.x.x netmask y.y.y.y up
```

---

