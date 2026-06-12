---
title: "2 ubuntu entries Grub help"
date: 2010-12-03
forum: New to Ubuntu
---

### Post by hunter99507 on 2010-12-03
When i start my PC just recently, i get 2 entries to start ubuntu. It looks like they are different versions. My question is how do i remove the older version?

---

### Post by azertyh on 2010-12-03
hello,
stay with these 2 kernels. in case of having some troubles with the newest, you can always boot with the oldest.

---

### Post by hunter99507 on 2010-12-03
What causes that? How did it get on the system?

---

### Post by garvinrick4 on 2010-12-04
> **hunter99507 said:**
> What causes that? How did it get on the system?
When you do upgrades it is in the repositories and is installed in your machine. Do you have your upgrades in Software Sources set to download in background or do you tell it
to upgrade? Any which way you do your upgrades the system is told by the settings you have told it to do. They come out with new kernels every once in a while so they will add up. Install aptitude and use it to upgrade:
```
sudo apt-get install aptitude 
```
```
sudo aptitude upgrade && sudo aptitude safe-upgrade
```
It will tell you what it is going to upgrade and new and remove.

#If you want to learn to remove kernels through Synaptic Package Manager you can do that.

---

### Post by uRock on 2010-12-04
> **hunter99507 said:**
> What causes that? How did it get on the system?
You get those when your system does a kernel upgrade. It is normal. If it is running well, then you can remove the old kernels via Synaptic Package Manager. In the left column, select Status, then Installed, then enter 2.6.32 for Ubuntu 10.04 or 2.6.35 for Ubuntu 10.10, then mark the three older versions for complete removal.

For Ubuntu 10.04, you should be keeping the ones that are listed in my screenshot. You want to remove the ones with the lowest numeric after the dash (-).

---

