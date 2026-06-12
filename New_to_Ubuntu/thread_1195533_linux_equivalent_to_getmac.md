---
title: "linux equivalent to getmac"
date: 2009-06-23
forum: New to Ubuntu
---

### Post by ant2ne on 2009-06-23
what is  the linux equivalent to windows command getmac. getmac is pretty cool as you can type "getmac /s {hostname}" or "getmac /s {ip addy}" and it will return the mac address. (I think you may need authority over the target computer)

---

### Post by .Maleficus. on 2009-06-23
'ifconfig' will display the MAC address in 'HWaddr'.  'iwconfig' will display the same if you use wireless.


Edit:  And you can also specify the device if you want - 'ifconfig eth0' will display just eth0.  'ifconfig' will display all active adapters, including the loopback interface.

---

### Post by unutbu on 2009-06-23
```
sudo apt-get install arp-scan
sudo arp-scan 192.168.1.0/24
```

This will search for and report MAC addresses on the local subnet.
Change 192.168.1.0 to match your local network.

---

### Post by .Maleficus. on 2009-06-23
Ah, you aren't talking about your host computer.  Serves me right for not reading the post :D.

---

