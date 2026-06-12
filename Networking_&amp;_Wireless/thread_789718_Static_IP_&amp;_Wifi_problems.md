---
title: "Static IP &amp; Wifi problems"
date: 2008-05-10
forum: Networking &amp; Wireless
---

### Post by tutwabee on 2008-05-10
I set a static IP address for my computer a while back to make port forwarding easier on my network.  I am using the "Manual Configuration" window in knetworkmanager to manage the IP.

A few times a day my network connection will go down and I have found one fairly reliable but unusual way to fix it.  The only way I have managed to fix it each time is to change the key type (I use a WEP key) from Hexadecimal to ASCII.  Then I click OK and wait for the settings to change.  Running "ip addr" after this gives me:
```
4: eth1: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc pfifo_fast qlen 1000
    link/ether 00:13:02:e0:c6:5d brd ff:ff:ff:ff:ff:ff
    inet 192.168.0.55/24 brd 192.168.0.255 scope global eth1
```



Then I reopen the window and set the key to Hexademical again (like it should be) and I re-enter the key.  After this my problem is solved until the next time I lose a connection to the network.  Running "ip addr" at this point gives me this:
```
 4: eth1: <NO-CARRIER,BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast qlen 1000
    link/ether 00:13:02:e0:c6:5d brd ff:ff:ff:ff:ff:ff
    inet 192.168.0.55/24 brd 192.168.0.255 scope global eth1
    inet6 fe80::213:2ff:fee0:c65d/64 scope link
       valid_lft forever preferred_lft forever
```

Why does this happen and how can I fix it?

---

### Post by tutwabee on 2008-05-12
I am still having this problem.  In fact, I am recently running into the problem that I often cannot re-establish a wifi connection until I obtain a dynamic ip via dhcp and then follow the above steps.  Sometimes I simply need to obtain a dynamic ip address and then get a proper static ip and it will work.

This problem is very annoying so it would be wonderful if someone could help me with it.  This is the most annoying problem I have had with my system in a while considering I have to go through the motions repeatedly to obtain a new ip address multiple times a day and my internet connection never stays up over night.

---

