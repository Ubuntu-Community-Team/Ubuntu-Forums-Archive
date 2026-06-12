---
title: "Why do my multiple pppoe connections die?"
date: 2007-04-13
forum: Networking &amp; Wireless
---

### Post by Jongi on 2007-04-13
I have setup two connection, ppp0 and ppp1 as per [these instructions](http://mybroadband.co.za/vb/showpost.php?p=970432&postcount=1).

Thing is the connections will start and I can surf if I start them manually with sudo ifup ppp0 and sudo ifup ppp1. Thing is is that if after (i'm guessing here) 5 minutes on inactivity on the lines, I can no longer connect. However ppp0 and ppp1 remain up. This is evidenced by running ifconfig and seeing ppp0 and ppp1 still up. What I then need to do is run sudo ifdown pp0 and sudo ifdown ppp1, and then restart the connections.

When I run ifup, the error below comes up for both interfaces

```

# sudo ifup ppp0
ppp0: ERROR while getting interface flags: No such device
Plugin rp-pppoe.so loaded.
# sudo ifup ppp1
ppp1: ERROR while getting interface flags: No such device
Plugin rp-pppoe.so loaded.
```

Remember though that I am able to browwse the net despite these errors. Until a prolonged break in surfing takes place.

```

# cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

auto ppp0
iface ppp0 inet ppp
provider international

auto ppp1
iface ppp1 inet ppp
provider local

pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf

```

Kubuntu Feisty (latest beta) is the distro. I might get out my Edgy tomorrow and see if the same problems befall me there.

---

### Post by Jongi on 2007-04-13
This seems to be a Feisty related error. After leaving Edgy untouched for short of 10 minutes I was still able to connect to the internet. Same instructions followed.

EDIT: Spoke too soon. Edgy also eventually lost connection.

---

