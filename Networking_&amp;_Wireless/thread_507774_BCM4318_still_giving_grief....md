---
title: "BCM4318 still giving grief..."
date: 2007-07-23
forum: Networking &amp; Wireless
---

### Post by jmusso on 2007-07-23
I've set up my laptop to run on the bcm4318 card using ndiswrapper. The only odd thing is that my home connection never connects automatically when I start my laptop. Ubuntu tries to connect to my home wireless connection, can't. When I disable networking, press my wireless button so its OFF, then enable networking, then turn the wireless button back ON, it then connects fine. Any ideas? And if there isn't a way to fix it, perhaps I can write a script to do all these things automatically when my computer starts... Thanks.

---

### Post by madmetal on 2007-07-24
> **jmusso said:**
> I've set up my laptop to run on the bcm4318 card using ndiswrapper. The only odd thing is that my home connection never connects automatically when I start my laptop. Ubuntu tries to connect to my home wireless connection, can't. When I disable networking, press my wireless button so its OFF, then enable networking, then turn the wireless button back ON, it then connects fine. Any ideas? And if there isn't a way to fix it, perhaps I can write a script to do all these things automatically when my computer starts... Thanks.

have you tried the broadcom 43xx-fwcutter driver ?
[http://bcm43xx.berlios.de/](http://bcm43xx.berlios.de/)
[http://packages.ubuntu.com/feisty/utils/bcm43xx-fwcutter](http://packages.ubuntu.com/feisty/utils/bcm43xx-fwcutter)

---

### Post by kevdog on 2007-07-24
Just a quick question.  If all you type in the command line is the following:
sudo /etc/init.d/networking restart

Will that work to basically restart and bring up the network???  If it is it would be easy to automate in a startup script!

---

