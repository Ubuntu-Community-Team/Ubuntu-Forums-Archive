---
title: "Compaq Pesario 1700 wireless issues"
date: 2009-09-04
forum: New to Ubuntu
---

### Post by jorilla on 2009-09-04
Hi,
 I am brand spank'n new to Linux, so if my questions seem dumb or if I come across as totally clueless, please have patience. 

 I come from the Mac environment, but have used PCs in the past. I inherited an OLD Compaq Laptop and I decided to install Linux on it. Went with xubuntu because ubuntu wouldn't load on it (8GB Hard Drive, 128MB of RAM). I really just want this system to be for my wife to use as an email/web device, and for a little trial run with Linux to see what we think about it. 

 Everything works for the most part, except the wireless card. A Linksys WPC11, what is confusing to me is that it sees my network, but will not connect, even with no security on the WIFI it asks for a password. The network was totally open and it was asking to enter a username and password as if the network was locked.

 Could anyone assist me with this issue? Unfortunately, if I can't get the WIFI working it pretty much voids the machine for me, aside from nosing around the OS.


Thanks,
Joe

---

### Post by keplerspeed on 2009-09-05
Just so we can see whats going on, enter this to the terminal of the compaq and post the output:

```

lspci | grep Network

```
```

iwconfig

```
```

iwlist scan

```

---

