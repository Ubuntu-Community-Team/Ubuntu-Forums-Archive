---
title: "how to install downloaded programs?"
date: 2009-11-01
forum: New to Ubuntu
---

### Post by greenie2009 on 2009-11-01
Hi there, I just installed ubuntu 9.10 on my HP compaq 2510p. I am totally new to linux so sorry if this question has been answered in the forum - I've tried various things for the last couple of hours and I am completely confused.

Main question: how do I install programs I've downloaded? And how can I see whether they have been installed?

Specific problems: my touchpad (and buttons) don't work, so I tried downloading gsynaptics. I see it in my downloads list, and have extracted it. The readme file says: 

"Ubuntu GNOME user:
    You have to add gsynaptics-init on [System] - [Preferences] - [Sessions] - [Startup Programs] in GNOME Menu.
    If it is already added (look for an entry with the word "Touchpad"), you just need to enable it."

I don't see the [sessions] line in [preferences]? I tried adding gsynaptics to [System] - [Preferences] - [Startup Applications] instead, but the touchpad still doesn't work.

I also tried to figure out the [Applications] - [Ubuntu software center], but clicking on e.g. [touchpad] it just says "not available in the current data". I's the same with all the programs I tried.

Thanks a lot!

---

### Post by oldos2er on 2009-11-01
Gsynaptics is in the repositories. Open a terminal (Applications, Accessories, Terminal), and run ```
sudo apt-get update && sudo apt-get install gsynaptics
```

---

### Post by ZankerH on 2009-11-01
For a more general overview on installing stuff in Ubuntu, see this tutorial:

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

Note that 99% of the stuff you'll ever need is in the repositories, so you'll only ever need to use the Synaptic package manager.

---

### Post by heyho on 2009-11-01
You could also use the package manager.

System > Administration > Synaptic package manager, then type gsynaptics in the search box.  When the search is done, check the box then apply.

---

### Post by X1R1 on 2009-11-01
Also note that if you want to manually download a program that is not on the repos or if you want an updated version, look for debian/ubuntu specific packages, they are on .deb extension. That allows you to just click and install.

---

### Post by greenie2009 on 2009-11-01
Thanks a lot, I really appreciate your fast help, all three.
Helene :)

---

