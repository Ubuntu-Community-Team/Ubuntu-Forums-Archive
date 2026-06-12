---
title: "SiS 900 Network Adaptors"
date: 2005-04-12
forum: Networking &amp; Wireless
---

### Post by oracledarren on 2005-04-12
Hi

Can anybody please tell me how to confirm whether an onboard Sis900 Network Adaptor is being detected and the driver loaded please ?

The reason is that I have a router coming in a couple of days I have never used the adaptor on my machine so I want to make sure everything is as configured as possible before the router arrives.

---

### Post by burlap on 2005-04-12
I use it without problems (sis900 onboard).

You can check if you have the module:
```
lsmod | grep sis900
```
And hardware 
```
lspci | grep 900
```
Or in device manager 
System->Administration->Device Manager

---

### Post by oracledarren on 2005-04-12
Brilliant, all looks good

the first command returns:-

sis900                  20100        0


and the second command does say it is a silicon graphics etc etc

Thanks for your help

---

### Post by kochen on 2006-10-24
I was wondering for the same thing & my sis900 is indeed installed properly.

but I can't have any network installed (neither on installation)...

anything I can do?

---

