---
title: "reload an earlier version"
date: 2011-05-14
forum: New to Ubuntu
---

### Post by dr.drip on 2011-05-14
I have winxp and ubuntu 10.10 side by each. Can someone show the proper way to do a fresh install of ubuntu from a disc and not affect the xp portion.of the drive. I am lost when I get to the install side by side or chose manually.....I am told ubuntu is good for formatting this part, but can't go from that point. I love pictures....


Garth:P

---

### Post by Hedgehog1 on 2011-05-15
Here are the key steps for 'overwriting' the Ubuntu and not Harming the XP install:

**AFTER BACKING UP YOUR UBUNTU DATA!**

Start the install, and select this option:

[IMG]http://img51.imageshack.us/img51/337/mbrpariondemo15.png[/IMG]

First, right click on your '/' partition and define it as your '/' (root) partition:

[IMG]http://img31.imageshack.us/img31/7520/04allocdrivespace2.png[/IMG]

[IMG]http://img130.imageshack.us/img130/9673/05allocdrivespace3.png[/IMG]

If you have a seperate '/home' partiton, then define your '/home' partition:

**[SIZE="4"]IF YOU ARE DOING AN UPGRADE, DO NOT FORMAT THIS PARTITION![/SIZE]**

[IMG]http://img202.imageshack.us/img202/6828/07allocdrivespace5.png[/IMG]

This separates your documents and 'stuff' from the system files and 'stuff' in the '/' partition.

Once you have defined the '/' and (possibly) the '/home' partition, you can install/reinstall:

[IMG]http://img684.imageshack.us/img684/7977/mbrpariondemo16.png[/IMG]

***The Hedge***

:KS

p.s. To learn how to move your '/home' into it's own partition: **_[SeparateHomePartition]("http://www.psychocats.net/ubuntu/separatehome")_**

---

