---
title: "ndiswrapper problem"
date: 2006-12-03
forum: Networking &amp; Wireless
---

### Post by ilhabia0 on 2006-12-03
I am currently installing edgy on my laptop and am having trouble getting my wireless to work.  I have a Broadcom 4306 card in a Dell Inspiron 5160.  I went through the howto that is posted as "Broadcom 4306 With Ndiswrapper 54 Mbps" and everything went well until I tried to input the command "sudo modprobe ndiswrapper".  When I did that I got this message back:

FATAL: Error inserting ndiswrapper (/lib/modules/2.6.17-10-generic/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Invalid argument

I am definately new to linux in general and ubuntu in specific.  I was just wondering if anyone had any suggestions as to what I am doing wrong here, any help would be greatly appreciated.  By the way, the error message I posted was not directly copied from the terminal as I do not have any sort of internet on my laptop because my ethernet port is busted so hopefully I didn't make any typos.

---

### Post by spd106 on 2006-12-03
This usually means that the ndiswrapper kernel module is not compatible with your kernel.
Try refreshing the packages with ```
sudo apt-get update
``` Then try installing the newer ndiswrapper package.
```
sudo apt-get install ndiswrapper-utils-1.8
```

---

### Post by ilhabia0 on 2006-12-03
Thank you very much, that fixed the problem instantly!!!

---

