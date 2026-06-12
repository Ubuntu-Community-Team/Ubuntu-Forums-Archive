---
title: "Cable internet"
date: 2007-03-10
forum: Networking &amp; Wireless
---

### Post by merike on 2007-03-10
I'm having trouble establishing my connection. I'm using network cable to modem, no router. I only get ip address from my service provider if I have constant mac address. I already managed to change it to the mac my desktop computer has, so it should give my laptop an ip. I don't need to enter any username and password in order to get connected.
However when I tried to load a page, it doesn't work. I also read some tutorials and from what I understood I seem to have a driver aswell. Under networking tools (I believe it's called something like that, I'm using half-translated version of Ubuntu) I found a place to see packets in/out and the number was much lower than when it is getting ip in windows, so I assume it doesn't really communicate to get ip. As I have no idea how networking actually works I don't know what else to check.
Forgot to add, that I have VIA Rhine II Fast Ethernet Adapter.

---

### Post by merike on 2007-03-15
Popped in #ubuntu on irc.freenode.net Fortunately someone was able to help.

Before I was using:
```
sudo ifconfig eth0 down
sudo ifconfig eth0 hw ether xx:xx:xx:xx:xx:xx
sudo ifconfig eth0 up
```

Got it to work with:
```
sudo ifdown eth0
sudo ifconfig eth0 hw ether xx:xx:xx:xx:xx:xx
sudo ifup eth0
```

---

