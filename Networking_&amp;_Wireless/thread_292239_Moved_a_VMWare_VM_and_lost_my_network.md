---
title: "Moved a VMWare VM and lost my network"
date: 2006-11-03
forum: Networking &amp; Wireless
---

### Post by rhouston on 2006-11-03
Hi all,

I recently built a Dapper install in Vmware 5.5 and now want to move the VM to a different Vmware workstation install. Once I moved the VM I lost my network card. This is a server install so I don't have the gui tools.

I guess I need to know how I can get the server to detect and or reconfigure the network card. 

I have tried a ifup eth0 and I get the device does not exist error. Everything else works just fine.

Any help would be greatly appreciated. 

Rich Houston

---

### Post by MyAnda on 2006-11-03
sometimes when you move a vm you get a new mac address (it generally asks something about a new uuid i think)... look at 
/etc/iftab 
see if the one for eth0 matches yours (probaly now eth1), if not change it to yours
you can get/see yours by running ```
ifconfig -a
```

after you change it run ```
sudo /etc/init.d/network restart

```
if that is not the case, post the output from ifconfig -a

---

