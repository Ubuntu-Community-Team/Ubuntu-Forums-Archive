---
title: "Can't connect to the internet"
date: 2015-04-09
forum: Networking &amp; Wireless
---

### Post by Jorge_Calderon on 2015-04-09
I just installed xubuntu.  I'm using a VPN on my host machine.  I can't connect to the internet.  I tried pinging a public IP address with no luck.  I have stopped and restarted networking.

---

### Post by slickymaster on 2015-04-09
*Moved to the ***Networking & Wireless*** sub-forum*

---

### Post by michi1983 on 2015-04-09
please post the output of ```
sudo ifconfig
```

---

### Post by tjiagoM on 2015-04-10
Please also post the output of 
```
route -n
```

As it could be a problem of routing

---

### Post by Jorge_Calderon on 2015-04-13
I edited /etc/NetworkManager/NetworkManager.confand commented out "dns=dnsmasq".

based on the second answer here:
[http://askubuntu.com/questions/137037/networkmanager-not-populating-resolv-conf](http://askubuntu.com/questions/137037/networkmanager-not-populating-resolv-conf)

---

