---
title: "windows LAN - ubuntu dapper laptop"
date: 2007-10-16
forum: Networking &amp; Wireless
---

### Post by darkworld on 2007-10-16
Ive installed dapper on a spare laptop and connected into my companies windows LAN. I can see the windows network in PLACES > NETWORK and I can see the windows name assignments to servers. How do I get there IP? I tried properties with no luck. If I run traceroute on the assigned windows name it falls over. e.g. traceroute SERV1

If I go onto a windows machine and run tracert on the name then I get the ip... eg. tracert SERV1 will get the IP for me.

.How do I do this in ubuntu dapper?

---

### Post by dmizer on 2007-10-16
as root, edit /etc/nsswitch.conf

edit this line:
```
hosts:          files dns mdns
```
so that it looks like this:
```
hosts:          files dns mdns [COLOR="Red"]wins[/COLOR]
```
then install winbind and traceroute.
```
sudo aptitude update
sudo aptitude install winbind traceroute
```
restart networking
```
sudo /etc/init.d/networking restart
```
now you can get your routes and destination ip addresses via host name.
```
traceroute darkworld
```

---

