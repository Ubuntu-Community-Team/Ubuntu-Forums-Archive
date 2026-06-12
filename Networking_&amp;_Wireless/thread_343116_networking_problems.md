---
title: "networking problems"
date: 2007-01-21
forum: Networking &amp; Wireless
---

### Post by k4wedi on 2007-01-21
Right now I have my laptop (Ubuntu 6.06) configured to connect to my home network (WPA1) by following the guide that wieman01 wrote.

At school the network there uses WEP. So as it stands I can connect to either... but I would have to change my "/etc/network/interfaces" each and everytime I want to switch between networks. 

Is there an easy solution to get it working so that I can connect to both my home network and my school network (or even any given network with security assuming I have the passkey)?

I've tried switching profiles under networking but it doesn't seem like its working. Both networks are wireless.

---

### Post by featherking on 2007-01-21
look into networkmanager-gnome, i recently helped someone get this going see the post [[COLOR="Red"]here[/COLOR]]("http://www.ubuntuforums.org/showpost.php?p=2024518&postcount=4")

but first you will need to:

```
sudo apt-get install network-manager network-manager-gnome
```

then follow the directions in that post

good luck

---

### Post by k4wedi on 2007-01-21
Wow that did the trick! I can't believe it was just that simple. Thank you very much :D

---

### Post by featherking on 2007-01-21
No problem, sometimes i wonder why network manager isnt installed by default, but there are arguments on both sides of that issue..

Anyways, glad you got it going!

---

