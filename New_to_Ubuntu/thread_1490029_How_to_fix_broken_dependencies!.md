---
title: "How to fix broken dependencies!"
date: 2010-05-21
forum: New to Ubuntu
---

### Post by MBG1987 on 2010-05-21
there's a lot of broken dependencies on my system, i couldn't remove them because it will remove important system packages
how to handle with this issue?

---

### Post by SlidingHorn on 2010-05-21
Googled: ubuntu fix dependencies and this was the 3rd result:

[https://help.ubuntu.com/community/SynapticHowto#How to fix broken packages]("https://help.ubuntu.com/community/SynapticHowto#How to fix broken packages")

Moral: try google...it's pretty awesome.

---

### Post by bodhi.zazen on 2010-05-21
> **MBG1987 said:**
> there's a lot of broken dependencies on my system, i couldn't remove them because it will remove important system packages
how to handle with this issue?

How did this happen ? Did you add a repository or add a deb from outside the ubuntu repositories ?

You can try 

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by MBG1987 on 2010-05-21
> **SlidingHorn said:**
> Googled: ubuntu fix dependencies and this was the 3rd result:

[https://help.ubuntu.com/community/SynapticHowto#How to fix broken packages]("https://help.ubuntu.com/community/SynapticHowto#How%20to%20fix%20broken%20packages")

Moral: try google...it's pretty awesome.

I've searched ,but non of the results was useful (at least for my problem),
thank you for posting this reply


> **bodhi.zazen said:**
> How did this happen ? Did you add a repository or add a deb from outside the ubuntu repositories ?

You can try 

```
sudo apt-get update
sudo apt-get upgrade
```

yes.i've installed some packages from outside repos,and i will see if your suggestion helps 
thanks

---

### Post by bodhi.zazen on 2010-05-21
> **MBG1987 said:**
> yes.i've installed some packages from outside repos,and i will see if your suggestion helps 
thanks

Well, that is probably the cause of your problems. Just because is it a .deb does not mean you can install it.

If the problem persists, you will have to remove these packages, perhaps manually.

IMO it is best to install from source rather then alien or a foreign repository.

---

### Post by MBG1987 on 2010-05-21
Nice tip, actually i installed a lot of them at once! it's a king of trouble to try removing around 200+ packages, see my related post _[http://ubuntuforums.org/showthread.php?p=9338407#post9338407](http://ubuntuforums.org/showthread.php?p=9338407#post9338407)_

---

