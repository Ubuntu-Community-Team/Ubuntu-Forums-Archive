---
title: "Help!  Lost my network!"
date: 2007-05-03
forum: Networking &amp; Wireless
---

### Post by FRuMMaGe on 2007-05-03
I connect to the internet through a wireless router in my house.  Yesterday I had to unplug it from the wall as my sister had to practice her keyboard and there were no spares.  I plugged it back in, and now Ubuntu doesn't see it anymore!  I have to use Winsux for internet!

I know it is not a problem with the router, as all windows computers connect fine.  I also know that it is not a problem with my network card, as I can connect via windows and in ubuntu I can still see my next-door neighbour's network.

Please help me!

---

### Post by FRuMMaGe on 2007-05-03
bump?

---

### Post by php_penguin on 2007-05-03
Hey there, i am having a similiar problem and i know why it is happening

First, we are gonna check if you have any sort of connectivity, so open a terminal (Apps->accesories->terminal). Run
```
ping 66.102.9.99 -c 5
```

This should reply with something like:
```
PING 66.102.9.99 (66.102.9.99) 56(84) bytes of data.
64 bytes from 66.102.9.99: icmp_seq=1 ttl=244 time=38.0 ms
64 bytes from 66.102.9.99: icmp_seq=2 ttl=244 time=37.6 ms
64 bytes from 66.102.9.99: icmp_seq=3 ttl=244 time=37.3 ms
64 bytes from 66.102.9.99: icmp_seq=4 ttl=244 time=37.9 ms
64 bytes from 66.102.9.99: icmp_seq=5 ttl=244 time=37.3 ms
```

If it doesnt then do this in the terminal:
```
route
```

There should be some stuff there, especially in the column marked "Gateway". The name will be something like "TheBrandOfYourRouter.YourDomain"

 there is totally no connection, so its not the same problem as mine. If it does reply, then the problem is as follows:

In your System->Admin->Network settings the DNS tab should have an ip adress (eg 10.0.0.38). This IP adress could well not be the right one. The ip adress you are looking for is probably (although not definitely) the same as your router. Try changing it to the router's IP adress (you can find this info in the routers admin pages, or via windoze' network config (ipconfig in windoze).

Hope this helps, and if it doesnt sorry you had to read all that crap.

---

### Post by FRuMMaGe on 2007-05-03
This looks very helpful, but before I reboot into linux, I have used the wireless network scanner and it picked up my neighbour's netowkr but not mine.  Is this a problem?

---

### Post by php_penguin on 2007-05-03
Hello again,

Have you got the "Broadcast SSID" ticked to "yes" in your routers admin pages?

---

### Post by FRuMMaGe on 2007-05-03
I don't know.

I'll reboot now.  Thanks for your help :)

---

### Post by php_penguin on 2007-05-03
Hey there, if it does turn out to be something to do with your DNS nameserver, this is the way to solve it (i think).

Terminal ```
sudo gedit /etc/network/interfaces
```

Now, underneath wherever it says ```
iface **eth0** inet dhcp
``` put the following in: ```
dns-nameservers address.of.your.router
```

"eth0" is whatever interface you are connecting via, and "address.of..." is the IP of your router. This will stop it redoing the DNS each time you connect.

---

### Post by FRuMMaGe on 2007-05-04
> **php_penguin said:**
> Hey there, i am having a similiar problem and i know why it is happening

First, we are gonna check if you have any sort of connectivity, so open a terminal (Apps->accesories->terminal). Run
```
ping 66.102.9.99 -c 5
```

This should reply with something like:
```
PING 66.102.9.99 (66.102.9.99) 56(84) bytes of data.
64 bytes from 66.102.9.99: icmp_seq=1 ttl=244 time=38.0 ms
64 bytes from 66.102.9.99: icmp_seq=2 ttl=244 time=37.6 ms
64 bytes from 66.102.9.99: icmp_seq=3 ttl=244 time=37.3 ms
64 bytes from 66.102.9.99: icmp_seq=4 ttl=244 time=37.9 ms
64 bytes from 66.102.9.99: icmp_seq=5 ttl=244 time=37.3 ms
```

If it doesnt then do this in the terminal:
```
route
```

There should be some stuff there, especially in the column marked "Gateway". The name will be something like "TheBrandOfYourRouter.YourDomain"

 there is totally no connection, so its not the same problem as mine. If it does reply, then the problem is as follows:

In your System->Admin->Network settings the DNS tab should have an ip adress (eg 10.0.0.38). This IP adress could well not be the right one. The ip adress you are looking for is probably (although not definitely) the same as your router. Try changing it to the router's IP adress (you can find this info in the routers admin pages, or via windoze' network config (ipconfig in windoze).

Hope this helps, and if it doesnt sorry you had to read all that crap.

Okay, I tried these commands and recieved no response from the ping and a blank table from "route"

Thanks for trying.  Any other suggestions?

---

### Post by FRuMMaGe on 2007-05-06
bump

---

