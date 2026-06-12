---
title: "'service networking stop' is not working"
date: 2007-11-28
forum: Networking &amp; Wireless
---

### Post by tuxfan123 on 2007-11-28
Hi,

I have installed Ubuntu Fiesty Fawn. I am trying to stop the networking service, by giving the following command:
"service networking stop"

The output that i get is 
* Deconfiguring network interfaces.....  [OK]

But on seeing the interface status using ifconfig command, i see that all the interfaces are up and I am also able to send traffic out.. 

Any ideas why the "service networking stop" command is not working???


Thanks
TuxFan

---

### Post by rechick on 2007-11-28
sudo ifdown ethx where x is the ethernet adapter you want to turn off.

---

