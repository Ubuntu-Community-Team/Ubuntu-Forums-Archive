---
title: "Change kernel module for nic"
date: 2006-08-17
forum: Networking &amp; Wireless
---

### Post by steveo_mcg on 2006-08-17
I'm having trouble with dapper. The nic driver that is loaded for my onboard nic is e100 and this doesn't seem to work, i've spent hours on this. If i boot to the DSL live cd it uses a different module eepro100 and it seems to work fine. The question i have is how do i force ubuntu to use the other module for the nic?

---

### Post by mgor on 2006-08-17
you can blacklist the e100 module in /etc/modprobe.d/blacklist,
```
blacklist e100
```
and then add the eepro100 module in /etc/modules,
```
eepro100
```

---

### Post by steveo_mcg on 2006-08-17
Just had a look at the black list eepro100 is listed in there any reason for it? 
Not had chance to try your suggestion mate in the middle of making my dinner.

---

### Post by steveo_mcg on 2006-08-17
Ok got the new driver to load, thanks thats stopped me going mad!
However the bloody thing still will not connect. The hardware is clearly supported since dsl will make everything work, but it appears thats its not that driver that is the problem. Any one have any suggestions?

---

