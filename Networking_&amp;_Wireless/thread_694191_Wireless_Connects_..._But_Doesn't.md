---
title: "Wireless Connects ... But Doesn't"
date: 2008-02-11
forum: Networking &amp; Wireless
---

### Post by darthdavid on 2008-02-11
I'm running Gutsy on a Toshiba Satellite A215-S747. I've got ndiswrapper set up with the Atheros drivers. All the appropriate hardware gets detected. It connects to networks (either manually or through Wicd). At least it says it does. The problem lies in the fact that it won't actually connect to anything. 

It gets an IP Address. I can ping it from other computers on the network. It won't connect to the internet. Other computers on the same network do connect. Advice?

Thanks,
David

---

### Post by anindya_m on 2008-02-11
Looks like your DNS settings are not correct. Check /etc/resolv.conf.

---

### Post by darthdavid on 2008-02-11
It's the same as on a computer that can get on the internet through this network :(.

---

### Post by anindya_m on 2008-02-11
Ok let's try to see if the DNS query is really working:

```
host ubuntuforums.org
```

Do you get any reply? The IP I am getting here in Canada is 91.189.94.186 (and also a MX record) and I am able to ping it.

The basic networking should be working since you can access other machines on the same network. Also please check if two interfaces are active at the same time (eg eth0 and eth1). In that case disable the one you are not using.

---

### Post by darthdavid on 2008-02-20
Sorry for the delay. 
I get 
```
:: connection timed out; no servers could be reached
``` 
as a result for 
host ubuntuforums.org
The laptop has the same servers in resolv.conf, it can ping and be pinged by other machines on the network the only difference I can find is that it doesn't connect to the internet while the wired machines do :(.

---

