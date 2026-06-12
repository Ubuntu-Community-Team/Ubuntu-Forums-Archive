---
title: "Network card does not working : systemctrl status networking.service"
date: 2017-10-16
forum: Networking &amp; Wireless
---

### Post by manoj.az1 on 2017-10-16
I am new to Ubuntu. In my office, There is a system with Ubuntu 16.04 64 bit connected with DNS server with *enp2s0* card. Now it was suddenly disabled. I tried to restart network after give # (hash) to all lines in  /etc/network/interfaces.
  It is:  
```
auto lo  
iface auto inet loopback  

auto enp2s0  
iface enp2s0 inet static  
address 192.168.0.50  
netmask 255.255.255.0  
gateway 192.168.0.1  
dns-nameservers 192.168.0.100  
dns-search xxx.com
```
  except first two lines, which I entered after normal installation. Then restart the network using /etc/init.d/networking stop, then /etc/init.d/networking start/restart Then the system shows:
```
starting networking (via systemctrl): networking.serviceJob for networking.Service failed because the control process exited with error code.
See "systemctrl status networking.service" and "journalctrl - xe" for details**.
```
  I don't know how to check. I think somebody played with. in ifconfig, only **lo** shows.
network card is OK. (I tried system with another HDD with same OS installed).

---

### Post by mcparty2 on 2017-10-17
Hi,

Can you do the following and post the results please?:

```


systemctl start networking
systemctl status networking 


```

Then post the last 10 lines of output from - Hopefully that will catch any errors:

```
journalctl - xe
```

and finally a list of your interfaces:

```
ip a
```


Hopefully that will reveal some clues.

Thanks

---

