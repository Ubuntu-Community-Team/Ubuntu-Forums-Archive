---
title: "eth0 and eth1 disapeared"
date: 2007-02-18
forum: Networking &amp; Wireless
---

### Post by jmvidalvia on 2007-02-18
I use Xubuntu-Edgy.
Suddently, this morning, I couldn't connect to the Internet.
I checked System-Network and **eth0 (wireless) and eth1 (cable) didn't appear!**, just modem connection.
Obviously I cannot connect to any network..
How could they desapear?
Any Idea about how to solve this, please?
Thanks in advanced!

---

### Post by jmvidalvia on 2007-02-18
Some more information:
Now my USB is not working neither..
There seems to be a problem "starting things"
Some help! please...

---

### Post by jmvidalvia on 2007-02-18
Please, find more information here...
[http://www.ubuntuforums.org/showthread.php?p=2173673#post2173673](http://www.ubuntuforums.org/showthread.php?p=2173673#post2173673)
Thanks,

---

### Post by eppoh on 2007-02-18
> **jmvidalvia said:**
> I use Xubuntu-Edgy.
Suddently, this morning, I couldn't connect to the Internet.
I checked System-Network and **eth0 (wireless) and eth1 (cable) didn't appear!**, just modem connection.
Obviously I cannot connect to any network..
How could they desapear?
Any Idea about how to solve this, please?
Thanks in advanced!

Did yu by chance update your packages including the kernel headers last night, via the update manager?

I did and now my wireless card no longer exists.

Try booting with the previous kernel in grub- if it exists

---

### Post by jmvidalvia on 2007-02-18
Thank you.
With the previous kernel everything works.
I just updated linux-headers-generic and linux-image-generic and now I can boot the latest kernel.
The problem was my grub was updated by another partition's linux, but not my system.
Thank you.

---

