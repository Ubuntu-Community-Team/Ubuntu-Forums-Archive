---
title: "kubuntu not showing in grub"
date: 2009-08-23
forum: New to Ubuntu
---

### Post by libihero on 2009-08-23
i just made a partition for kubuntu but for some reason it's not showing up on the grub startup

---

### Post by slakkie on 2009-08-23
You've installed Kubuntu next to Ubuntu?

Wipe that partition, since you can reuse that space mate, boot into your Ubuntu and then do:

```

sudo aptitude install kubuntu-desktop

```

Logout of gnome, and when gdm pops up, hit the session type selection box thing. Select KDE, login and you are running Kubuntu.

No need to install it on a seperate partition..

---

### Post by mathay on 2009-08-23
As slakkie said, there's no need to put Kubuntu on a separate partition.

Did you happen to install Kubuntu using apt-get or a package manager?

---

### Post by alexlafreniere on 2009-08-23
I think we need a little clarification here: do you want to install a second operating system in a separate partition, or just convert your Ubuntu installation to use the KDE desktop instead of the default GNOME?

---

### Post by libihero on 2009-08-23
i wanna be able to run both kde and gnome.  i was jus gonna use two different partitions and mount the drives if i needed files from different partitions

---

### Post by kansasnoob on 2009-08-24
> **libihero said:**
> i wanna be able to run both kde and gnome.  i was jus gonna use two different partitions and mount the drives if i needed files from different partitions

So, you actually installed both Ubuntu and Kubuntu in a dual boot?

That's not really neccassary, look here:

[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)

At the section:

> Playing Around
KDE/Gnome Comparison
Install KDE
Install XFCE
Install IceWM
Pure Gnome
Pure KDE
Pure XFCE
Make your own Ubuntu remix 

If you want a true dual boot then you must actually install one and then the other. Maybe having a look at the output from the following command would help us understand:

```
sudo fdisk -l
```

---

