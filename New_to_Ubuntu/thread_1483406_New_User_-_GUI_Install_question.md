---
title: "New User - GUI Install question"
date: 2010-05-14
forum: New to Ubuntu
---

### Post by TroppoAlto on 2010-05-14
I am trying to get 10.04 setup on an older machine I picked up. The full distro's kept failing with I/O error at 29%. I re-downloaded and reburned at slower speeds but that didn't change anything. I did get the minimum install .iso w downloading components to install successfully.
 
So now I can log in, but where do i go from here? I've read that I should launch gnome or kde.
 
Which one should I use?
How do I check which packages the installer has downloaded?
 
I've done some searches and read some of the links provided in the stickies. Is there a better place to read up on getting the GUI up and running, or should I keep sloshing through the links?
 
Thank you.

---

### Post by aysiu on 2010-05-14
If you used the mini.iso, this guide should help (especially the bottom bit with the commands to install the GUI):
[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

---

### Post by halitech on 2010-05-14
if you did the minimal install then you don't have a gui. You need to install a desktop before you can launch it. 

What are the specs of the machine?

log in and run
```
sudo apt-get install xubuntu-desktop
``` or
```
sudo apt-get install ubuntu-desktop
```

---

### Post by TroppoAlto on 2010-05-14
> **halitech said:**
>  
What are the specs of the machine?

 
Abit NF-M2 nView
Athlon 64 x2 3600+
4 GB RAM
80 GB IDE HD
using integrated graphics
 
Thank you for the quick replies.  I will check out the link and try out the command when I get home later.  I realize there is more to do than this, just need some help getting started.

---

### Post by halitech on 2010-05-14
with those specs Ubuntu will run fine. any other questions, feel free to ask :)

---

### Post by StephanG on 2010-05-14
Well, you have more than enough RAM and processing power to run any GUI.

So you can choose to either install Ubuntu (standard) with:

```
sudo apt-get install ubuntu-desktop
```

Or you could go for Kubuntu (slightly more resource intensive) with:

```
sudo apt-get install kubuntu-desktop
```

Or if speed is the most important to you, you could go for Xubuntu (extremely light on resources) with:

```
sudo apt-get install xubuntu-desktop
```

Personally I suggest you research each and choose the one that works for you.

---

### Post by TroppoAlto on 2010-05-17
That worked out great, thanks again for everyone's advice.  
Now on to getting Vista, XP remote desktop to Ubuntu working.  It's been a while since I've tackled something genuinely new, is a lot of fun.

---

