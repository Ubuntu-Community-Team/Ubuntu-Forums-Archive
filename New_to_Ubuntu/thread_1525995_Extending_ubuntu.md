---
title: "Extending ubuntu"
date: 2010-07-07
forum: New to Ubuntu
---

### Post by Souptik on 2010-07-07
I have recently installed Lucid Lynx on my laptop. Not counting some hitches which every beginner faces, it is now running great. I had originally put my installation size at 15 GB, but now I want to extend the installation size to 30 GB without losing any data on the installation. Can it be done? Any help would be very much appreciated.

---

### Post by Darkness Des on 2010-07-07
Quite easily. Boot into a LiveCD, install GParted (or use the installer and cancel after expanding your partition[s]) and expand your install. Unless it was a Wubi install. In that case, no.

---

### Post by Souptik on 2010-07-07
> **Darkness Des said:**
> Quite easily. Boot into a LiveCD, install GParted (or use the installer and cancel after expanding your partition[s]) and expand your install. Unless it was a Wubi install. In that case, no.
Mr.Darkness Des I am sorry, but I am quite a novice, could you please explain the steps to me. For example, how can I install GParted from the CD?

---

### Post by RiceMonster on 2010-07-07
> **Souptik said:**
> how can I install GParted from the CD?

The same way you normally would.

---

### Post by Darkness Des on 2010-07-07
Boot from the LiveCD like you did to install but click Try Ubuntu instead of Install. Make sure you have an internet connection (Ethernet or Wireless, as long as it works) and go to Applications -> Accessories -> Terminal. Type in:
```
sudo aptitude install gparted
```
and that will install GParted. From there, go into System -> Administration -> GParted and resize partitions at will. Be careful though, if you're dual booting with Windows it gets upset if it finds that you resized it's partition and will go through some long unnecessary chkdsk procedure the next time you boot it up. However, this causes no harm and is just a minor nuisance.

---

### Post by Souptik on 2010-07-07
Thank you, that really worked.

---

### Post by Big Nate on 2010-07-07
Great info for anyone to know.  

Thanks Darkness Des.

This community is great

---

### Post by Trilby on 2010-07-07
I'm also looking to expand my Ubuntu partition, but have a question: Why do you have too install gparted and use it whilst on a live disk? Can't you do it from in a normal boot?

---

### Post by Trilby on 2010-07-07
> **Trilby said:**
> I'm also looking to expand my Ubuntu partition, but have a question: Why do you have too install gparted and use it whilst on a live disk? Can't you do it from in a normal boot?

Never mind, I know why now. Thanks anyway. :redface:

---

