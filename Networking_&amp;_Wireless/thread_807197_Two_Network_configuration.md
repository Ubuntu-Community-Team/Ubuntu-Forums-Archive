---
title: "Two Network configuration"
date: 2008-05-25
forum: Networking &amp; Wireless
---

### Post by jaymill on 2008-05-25
I couldn't find a good explantation to my problem so I was wondering if someone could help me out, here is the situation;

I have two networks, wlan0 and eth0. Wlan0 is my wireless conection to the internet, and thats all its used for. Eth0 however is connected to a wireless router and is serving as basically an access point to a ftp server that I am running serving other people around me. I can't get the network configuration to work properly so that the internet still works. I think it might be a problem with roaming mode, or possibly the ip address range, but I really have no clue at this point. If someone could point me in the right direction it would be really appreciated, thank you.

OS: ubuntu 8.04 fully updated

---

### Post by SpaceTeddy on 2008-05-25
network manager (called nm from now :) ) does not support two network card configruations in roaming mode at the same time. You will need to configure either your wifi or your ethernet manually. 

The easiest way of doing this is to connecto your wifi and make sure you have internet connectivity. Also make sure that the cable is plugged in at this point. 

Once that is done, try to get a dhcp-lease manually from the other network via this command
```
sudo dhclient eth0
```
if that succeeds, then you should have connectivity to both network. The only problem here is that you might have two (?!) gateways which would collide. But for that to figure out i would need some more details. So, please just try the above, and if that still runs you into problem, i will query for some output from you...

hope it helps :)

---

### Post by jaymill on 2008-05-25
I can connect to both individually, when I turn off one or the other, the problem comes in when I try to run both at the same time. This may be the default gateway problem

---

### Post by SpaceTeddy on 2008-05-26
right - then please connect to both and post the output of the following commands

```
ifconfig
route -n
```

the first will print your network card configuration, the second will show information about your gateway and routes.

---

