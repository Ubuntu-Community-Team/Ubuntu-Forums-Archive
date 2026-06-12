---
title: "MAC address script"
date: 2014-06-06
forum: Networking &amp; Wireless
---

### Post by scientia3 on 2014-06-06
Hello,

I'm trying to get a MAC address script running which changes the MAC address on each boot up.
I've tried editing /etc/rc.local but without success yet.

What I manually use to change my MAC address atm is;

```

sudo service network-manager stop
sudo ifconfig eth0 hw ether xx:xx:xx:xx:xx:xx
sudo service network-manager restart

```

This works just fine. Is there a way I can put this into a script so I dont have to manually do it everytime I boot?
Thanks in advance!

---

