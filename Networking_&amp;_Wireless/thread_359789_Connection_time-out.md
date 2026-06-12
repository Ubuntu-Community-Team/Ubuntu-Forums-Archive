---
title: "Connection time-out"
date: 2007-02-12
forum: Networking &amp; Wireless
---

### Post by qwasi_nodough on 2007-02-12
I'm pretty new to Linux and have the following problem. My browser (Firefox) times out whenever I try to reach any internet page. The only adress it will pick up is my routers adress (192.168.1.1). I conclude from that, that there is no problem with the network connection (DHCP). I might be wrong here. What else could be wrong? Tnx for any help!

---

### Post by LotsOfPhil on 2007-02-12
It could be lots and lots of things. 

Try this command:
```
ping -c 1 128.112.128.81
```
Then try this one:
```
ping -c 1 www.princeton.edu
```

If the first one works but not the second, you have a problem with DNS. ("works" means that it says "0% packet loss").

---

### Post by qwasi_nodough on 2007-02-15
Thanks for your help. It worked like a charm after I copied the IP of the DNS into the network settings. Cheers!

---

### Post by LotsOfPhil on 2007-02-15
Good to hear!

---

