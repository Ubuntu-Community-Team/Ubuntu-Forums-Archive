---
title: "intermittant internet connection after recent upgrade"
date: 2007-10-15
forum: Networking &amp; Wireless
---

### Post by mistaex on 2007-10-15
I performed a upgrade yesterday (Ubuntu 7.04) and since the upgrade I am no longer able to maintain an network connection. All the other computers on the network are still connected but my ubuntu machine does not see the network for some reason.

eth0 is configured to use a static ip address and worked fine prior to the upgrade. If I reboot the system it will work again for approx 12 or so hours, Bbut being a static ip it is not a dhcp release issue. If I do an ifconfig eth0 down / up it still does not work. 

I am kind of at a loss here. I think it may have something to do with the ipchains upgrade but cannot really tell.. 

Any ideas?

ps: this was not a system upgrade but an incremental package upgrade. Sorry for confusion.

---

### Post by noob12 on 2007-10-15
This is your wired net right?

Can you post the output of these?
```

lspci -nn

sudo lshw -C network

cat /etc/network/interfaces

# yes, static I know, but there is a known issue with stale leases...
ls /var/lib/dhcp3

```

Do you see anything from these
```

tail -15 /var/log/syslog

tail -15 /var/log/kern.log

```
run soon after you lose connectivity?

What does **ifconfig -a** show after you've lost connectivity?

What about **sudo ethtool eth0** ?

---

