---
title: "atl.ko problem"
date: 2007-08-14
forum: Networking &amp; Wireless
---

### Post by fredgoldie on 2007-08-14
Hi,

I am running Ubuntu on my computer and have got it to load up and work etc.

The problem i am having is that whenever i switch on the computer i have to run in the terminal

su
<my password>
insmod /lib/modules/2.6.20-15-generic/kernel/drivers/net/atl.ko

in order to connect to the internet. If i do not do this i cannot connect to the net.


Pleae help me!!

Thanks 
Fred

---

### Post by choroque on 2007-09-21
Add the command to /etc/rc.local

[http://www.jroller.com/ndpar/entry/ubuntu_7_04]("http://www.jroller.com/ndpar/entry/ubuntu_7_04")

---

