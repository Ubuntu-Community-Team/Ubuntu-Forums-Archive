---
title: "firestarter wont start and broke gksu"
date: 2008-09-13
forum: Networking &amp; Wireless
---

### Post by shineymcshine on 2008-09-13
Hi all,

I want to share my internet connection from my ubuntu "file server" to my winXP box. 
```

WINXP-----------UBUNTU(eth0)
                UBUNTU(eth1)-------CABLE MODEM
```

I tried and failed following a number of guides on configuring iptables. Then i set up a simple bridge by editing /etc/network/interfaces to include 
```
auto br0
iface br0 inet dhcp
bridge_ports eth0 eth1
```

This was not satisfactory because my cable modem DHCP gives the two computers totally different ip addresses as follows meaning I can ssh in only one direction.

```
CABLE MODEM   192.168.100.1
UBUNTU        144.136.different.different 
WINXP         144.136.different.different
``` 

I don't understand too much about this but basically i want something like this.

```
CABLE MODEM   192.168.100.1
UBUNTU        192.168.100.2  
WINXP         192.168.100.3
```

Now I have installed firestarter thru synaptic. Originally it didn't work. It would give the error "Internal network device eth0 is not ready" or "Internal network device eth is not ready" depending on its mood. Then I reinstalled it thru synaptic and now it has around **7 mins** of lag when i start it. Now when I try to run it nothing happends for 7 mins and then an empty popup appears that i can't get rid of. Also now gksu produces a similar ammount of lag. For instance
```
gksu gedit <something> 
```
takes around 10 mins to open a grey non responsive window. Does anyone know how firestarter killed gksu or how to fix any of my problems?

peace

---

### Post by shineymcshine on 2008-09-13
UPDATE:

I've been doing other things on the net since my first post and now after more than an hour, a firestarter window has poped up! I would like to know what could cause a program to delay over an hour between typing the command and it actually opening up?

Thanks

ps. It obviously still doesn't work...

---

