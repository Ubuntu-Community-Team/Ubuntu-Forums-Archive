---
title: "question about upgrading"
date: 2009-04-24
forum: New to Ubuntu
---

### Post by a cup of tea on 2009-04-24
So, I decided to upgrade to 9.04. However, I wanted to use my other computer (which has Windows XP) while this one was upgrading, and I turned that computer on and it has serious problems. So now I'm concerned that if I have problems with upgrading this computer (which is currently working fine) I won't be able to use the other computer to get on the internet and get help. I'd rather wait until I get the issues with the other computer resolved. But since I'd already started the upgrade process, I didn't want to interrupt it. However, then my internet connection went out briefly (while the upgrade thing was doing a ton of downloads). When my internet came back up, the downloads didn't restart, and just stayed where they were. I had to cancel it, and it said it restored my system to the previous state. 

So, my question is: is my computer still running 8.10 (rather than being mid-upgrade to 9.04) and will it be fine to leave it like this for a few days and avoid upgrading while I deal with the issues with the other computer?

---

### Post by N_Nick on 2009-04-24
At which stage of the upgrade did your Internet go down? If it was still downloading then it didnt make any changes to your computer.

---

### Post by a cup of tea on 2009-04-24
I was about halfway through a download that it said would take 3 hours when the internet went down. :)

---

### Post by clive littlewood on 2009-04-24
Hi

As long as it had not reached the installation phase you should be OK  :)

It might even recognise the updates already downloaded when you retry.

Clive

---

### Post by JoshuaRL on 2009-04-24
It should recognize them and try to fix it, but I'd suggest using aptitude, as it handles fixing things like these a little easier.
```
sudo aptitude full-upgrade
```

---

### Post by por100pre1 on 2009-04-24
I experienced three unplanned power outages during the download stage (I'm glad I have a battery back-up for nice shutdowns). Every time the download continued without any problems.

---

