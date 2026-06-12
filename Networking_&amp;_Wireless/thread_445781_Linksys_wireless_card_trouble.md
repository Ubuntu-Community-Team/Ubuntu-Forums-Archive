---
title: "Linksys wireless card trouble"
date: 2007-05-16
forum: Networking &amp; Wireless
---

### Post by waylow on 2007-05-16
can somebody help me get my wireless card working
been playing around with different solutions on the forum and haven't got anything to work

I am new to Linux - tried it on a virtual machine loved it - ended up installing ubuntu studio as a dual boot
now I have it as a "real" machine have regretted it ever since

I have a Linksys wmp54g Broadcom BCM4306 

things I am confused about:

1.the system sees the card as eth1,  does the system need to see it as wlan0? -  I have tried to change the /etc/network/interfaces to make it say wlan0 but either I didn't do it right or it doesn't work

2. do I need to upgrade the driver with the bcm43xx-fwcutter thingy? - I don't have a wired connection so I can't just install in from the terminal - I have to DL it with my windows partition and then install it but I can't get it working either

3. when I type "iwconfig --version" it says ```
 iwconfig Wireless-Tools version 28
compatible with Wireless Extension v11 to v20

Kernel  Currently compiled with Wireless extension v21

eth1 recommended Wireless Extension v18 or later
currently compiled with Wireless extension v21
```

do I need to update the iwconfig? if so how? - i have also DL it but got stuck in the compiling process


any help in pointing me in the right direction would be awesome

thanks
over

---

### Post by Kobalt on 2007-05-16
Here are [some instructions]("http://ubuntuforums.org/showthread.php?t=201902") to get your broadcom 4306 card working.

Welcome to Ubuntu :)

---

