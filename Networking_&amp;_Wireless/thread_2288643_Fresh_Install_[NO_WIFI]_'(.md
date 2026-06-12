---
title: "Fresh Install [NO WIFI] :'("
date: 2015-07-28
forum: Networking &amp; Wireless
---

### Post by Sbo0Tr on 2015-07-28
Hello guys so I installed a frsh XUbuntu and now I cant seem to get the wifi to work, I used my mad google skill ( lol ) and tried everything I could find to fix this and nothing has worked ... All i can do is give u the specs on my pc and etc.. 

Memory: 1.3 gb
Processor: AMD Turion(tm) 64 X2 Mobile technology TL-56 x 2
Graphics: Gallium 0.4 on NV4E
OS Type: 32-bit
Storage: 155.9

Pc model: HP pavilion dv9410us Notebook PC

[img]http://i.imgur.com/eFs7xdU.png[/img]

---

### Post by dcutl002 on 2015-07-28
Hmmm...HP.  I'll bet that you have a Broadcom Network adapter.  What I did with my HP laptop was to plug it in directly to the router via ethernet cable and then let all of the updates download and install.  Once I did that, Linux found a driver for my HP pavilion with a Broadcom wifi adapter and it works perfectly.

---

### Post by dcutl002 on 2015-07-28
Hmmm...HP.  I'll bet that you have a Broadcom Network adapter.  What I did with my HP laptop was to plug it in directly to the router via ethernet cable and then let all of the updates download and install.  Once I did that, Linux found a driver for my HP pavilion with a Broadcom wifi adapter and it works perfectly.

---

### Post by Bucky Ball on 2015-07-28
Please open a terminal and:

```
sudo lshw -C network
```

Post the output here, please. Are there any drivers in Additional Drivers that pertain to your wireless card?

PS: Please use 'Adv Reply' and attach large pic using the paperclip icon. Thanks. :)

PPS: Yes, do an update via a cable. You will quite possibly need a cable to get this going.

---

