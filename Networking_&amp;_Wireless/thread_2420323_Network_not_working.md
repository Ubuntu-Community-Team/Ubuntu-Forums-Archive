---
title: "Network not working"
date: 2019-06-03
forum: Networking &amp; Wireless
---

### Post by Azyx on 2019-06-03
Hey
Have Ubuntu 18:04. My network stop work on one machine. Have changed cabels but stilll broken. It just says " Connection failed   Activation of network connection failed " in a pop-up window. Under Settings network [ Wired, Connection - 100Mb/s  ON ]. If I unplugg the network cabel, [ Cabel unplugged ] and also a pop-up windows says so. It looks like my Router give the computer an ip-adress, but I don't have ipconfig in the standard installation of 18:04. :(
How can I find the error?

Cheers  /Azyx

---

### Post by crip720 on 2019-06-03
Do you know if this happened after a reboot?  Try to reboot with the cable unplugged and then plug cable back in after reboot and see if network starts working again.  Report back.

---

### Post by #&amp;thj^% on 2019-06-03
If a dual boot with Windows 10, you may need to disable the fast startup options first. 
Also check:
```
sudo lshw -C network
```
Is there anything on your network that provides DHCP? If not, you may need to set up the addressing scheme by hand.

---

### Post by ynota on 2019-06-05
you should use the command ifconfig for ubuntu not ipconfig, that is for Windows... you could also try the command 'ip address' on your ubuntu

---

### Post by Azyx on 2019-06-05
Yes I have rebooted many times. When I connect the cabel to ethernet, a network-symbol, with 3 dots on it. Then after a while, "Connentionfailed  Activation of network connection failed".

I don't, think the computer get any IP-adress from the router.

---

### Post by Azyx on 2019-06-06
There are no dual boot. Yes there are a DHPC-server inte rooter. I have also rebooted the rourer and the mechinte are not nonected, i think.

---

### Post by drv9977 on 2019-06-06
use ifconfig instead of ipconfig. ipconfig is for windows systems. check for network proxy, whether its on or off. if it also not works then try to ping other systems on network and check its working or not.

---

