---
title: "[SOLVED] Build Essential wont install"
date: 2008-09-26
forum: Networking &amp; Wireless
---

### Post by AmbiguousOutlier on 2008-09-26
Hello Newbie here, I've spent the last week when I first installed kubuntu trying to get wifi working. I've tried to install Madwifi and then the ndiswrapper. Now I'm going back to Madwifi. I'm using this guide

[http://ubuntuforums.org/showthread.php?t=816780&highlight=AR242x+madwifi](http://ubuntuforums.org/showthread.php?t=816780&highlight=AR242x+madwifi)

The wifi card is: AR242x 802.11abg Wireless PCI Express Adapter
Laptop is: Toshiba Satellite A205-S5825

After I run the first step I get this message;

```

Reading package lists... Done
Building dependency tree 
Reading state information... Done
E: Couldn't find package build-essential

```

Does this mean it's failed hence why I couldn't install it first time around.

Does anyone know how to get around this problem?

---

### Post by shanix on 2008-09-26
you probably need to check the sources.list or System> Administration> Software Sources and enable main, universe, restricted ...etc

Then 

sudo apt-get update; sudo apt-get install build-essential

---

### Post by shanix on 2008-09-26
Here is mine /etc/apt/sources.list file

> 
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-security main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-security multiverse



---

### Post by AmbiguousOutlier on 2008-09-26
I did a lot more googling and 20 more sites and I found

```

sudo aptitude update

```

which worked

but thank you

---

