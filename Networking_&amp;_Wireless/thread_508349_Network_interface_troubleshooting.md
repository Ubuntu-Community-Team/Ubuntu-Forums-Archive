---
title: "Network interface troubleshooting"
date: 2007-07-24
forum: Networking &amp; Wireless
---

### Post by psykro on 2007-07-24
I could really use some help with how to check if a network card is working. I have just put a new card into my Ubuntu server and it doesn't seem to be functioning. 

Am I correct in assuming that the new card will be installed automatically or is there something I have to do to install it. 

I am very lost here, and I don't even know where to begin. any help would be appreciated.

I am running Ubuntu 7.04 as a web server so i only have command line access

Thanks

---

### Post by bapoumba on 2007-07-24
Hello, to get help on this, we'll need a little more infos on your hardware. What card are you using?
What does return:
```
lspci
```

---

### Post by psykro on 2007-07-24
I am assuming you need the Network Card details. 
As I cannot connect to the machine I have to write this out and then type it up instead of being able to copy/paste, so I'm only doing the Ethernet Controller Line. Hope this is the right thing.

```
00:0f.0 Ethernet Controller: Realtek Semiconductor Co., Ltd RTL-8139/8139C/8139C+ (Rev 10)
```

---

### Post by psykro on 2007-07-24
I have been able to resolve the problem. running "ip addr" let me see that the new card was eth1 and not eth0 so all I had to to was edit my /etc/network/interfaces file accordingly.

Learning more about ubuntu every day

---

