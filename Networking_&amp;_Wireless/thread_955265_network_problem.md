---
title: "network problem"
date: 2008-10-22
forum: Networking &amp; Wireless
---

### Post by sadiqdude on 2008-10-22
after installing ubuntu 8.4 i am having problem in network it is not getting detected.even windows is also not detecting my network:confused::confused::confused:

---

### Post by melojo on 2008-10-22
open a terminal and type
sudo lspci

---

### Post by 0x29a on 2008-10-22
> **sadiqdude said:**
> after installing ubuntu 8.4 i am having problem in network it is not getting detected.even windows is also not detecting my network:confused::confused::confused:

Hi,

a few questions:

*) Is it a wired or wireless network?
*) Did it ever work under windows?
*) What type of computer? (laptop or workstation)
*) Do you know who the manufacturer of the card is?
*) When is the last time the network worked?

Can you post the output of:
```

lspci -b

```


This will help give us a starting point. 

Thanks!

Andrew

---

### Post by Bucky Ball on 2008-10-22
> **melojo said:**
> open a terminal and type
sudo lspci

From the result of that, try to find your wireless card. It should be somewhere near the bottom. Machine make and model and specs would be good also. Can you get online with a hardwire ethernet cable for now?

---

### Post by sadiqdude on 2008-10-22
thanks guys i'll try it and let u know:cool::cool::cool:):P

---

### Post by melojo on 2008-10-22
> **sadiqdude said:**
> thanks guys i'll try it and let u know:cool::cool::cool:):P

post the output of lspci

---

### Post by Iowan on 2008-10-22
If Windows is not detecting network either, it could either be:
a bad adapter,
a bad (or wrong kind of) cable - if wired,
 or (if internal card) a BIOS setting.

---

