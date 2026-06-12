---
title: "iptv over lan"
date: 2007-07-15
forum: Networking &amp; Wireless
---

### Post by Hakimio on 2007-07-15
My internet service provider provides iptv. I can watch many different channels without any problem using VLC under linux when no firewall is active. The problem is when [ubuntu-firewall](http://rob.pectol.com/content/view/2/1/) (or firestarter, or guarddog, or any other firewall) is active it doesn't work. Also I would like to be able to stream iptv to my home lan using one low-end pc which I use as a linux router.
Now, here is what I would like to know:
1) Would it be possible to route the iptv stream through that pc without taking all the pc's resources (it's 300Mhz Celeron with 128MB RAM)? If yes, how?
2) How do I make the iptv work when firewall is active?

Thanks for any help in advance :)

---

### Post by Hakimio on 2007-07-15
Ok, found the answers myself.
1) IPTV stream can be routed with igmpproxy. It works flawlessly and it is really lightweight (to be honest, it doesn't seem to hog my 300MHz Celeron AT ALL)
2) To make IPTV work with ubuntu-firewall, these custom rules are needed:
```
# change 217.0.119.0/24 and 193.158.35.0/24 to subnets where the multicast traffic originates
iptables -I FORWARD -s 217.0.119.0/24 -d 224.0.0.0/4 -j ACCEPT
iptables -I FORWARD -s 193.158.35.0/24 -d 224.0.0.0/4 -j ACCEPT
# Multicast rules 
iptables -I INPUT -d 224.0.0.0/4 -j ACCEPT
iptables -I FORWARD -d 224.0.0.0/4 -j ACCEPT
```

Thanks to [_THIS_](http://man-wiki.net/index.php/T-Home_IPTV_without_speedport_W_700V) WIKI  post :)

---

