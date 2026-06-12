---
title: "Cant install backtrack"
date: 2011-08-13
forum: New to Ubuntu
---

### Post by piperider on 2011-08-13
ok im extremly new to unbuntu.I decided to give it a try so i got it up and running im connected to wireless and figured out some odds and ends(basics).Now my next step is to install backtrack and use it.I have read elseware and asked alot of questions but im getting no where fast.Farthest i got was launching commands in terminal but still got no backtrack.Im really lost here if someone can explain how i would go about this.I can do anything with windows but id like to learn unbuntu

---

### Post by mmsmc on 2011-08-13
just a suggestion, do not use backtrack until you are more experienced, backtrack is a command line os, you need to learn ho to use the terminal first, backtrack is difficult, even to install :) and if you want to go on anyways, i would suggest you use live cd, because once you install it it is hard to get rid of

---

### Post by piperider on 2011-08-14
backtrack is my first goal i always wanted to learn how to use it.so if i make a copy of it how do i get started from there

---

### Post by spiky001 on 2011-08-14
[This]("http://www.backtrack-linux.org/tutorials/") will start you off,
 Then you can download [here]("http://www.backtrack-linux.org/downloads/")

Bactrack is no different than using Ubuntu, It is just a linux distro designed for pen testing, you would really learn more with a run of the mill distro. It dosn't have all the day to day programs which you need and is not ment for daily use, or designed for it.

---

### Post by varunendra on 2011-08-14
> **mmsmc said:**
> just a suggestion, do not use backtrack until you are more experienced, backtrack is a command line os, you need to learn ho to use the terminal first, backtrack is difficult, even to install :) and if you want to go on anyways, i would suggest you use live cd, because once you install it it is hard to get rid of

Sorry, but I have to disagree with you. Perhaps you haven't had a look on it recently. I've used BT4 (just to see what it looks like) and now have a live iso of BT5 which I've tested on a VM. It does start with a commandline session (with a fancy graphical background :)), but getting the normal Ubuntu-like desktop is just a matter of command **startx**.

Getting the networking up is nothing more than **sudo ifconfig eth0 up**. Installing or removing is same as Ubuntu with the only difference that BT4 used grub legacy (I didn't notice the grub version in BT5).


> **spiky001 said:**
> [This]("http://www.backtrack-linux.org/tutorials/") will start you off,
 Then you can download [here]("http://www.backtrack-linux.org/downloads/")

Bactrack is no different than using Ubuntu, It is just a linux distro designed for pen testing, you would really learn more with a run of the mill distro. It dosn't have all the day to day programs which you need and is not ment for daily use, or designed for it.+1

---

### Post by piperider on 2011-08-14
yeah its probably a mistake to start off with backtrack but id like to start there cause if i figure out how to use that i will want to do alot more.Thanks for the help although i followed the instructions on the backtrack site already i,ll give it another hook

---

### Post by spiky001 on 2011-08-14
How far have you got, Have you installed it yet

---

### Post by gandaran on 2011-08-14
> **spiky001 said:**
> [This]("http://www.backtrack-linux.org/tutorials/") will start you off,
 Then you can download [here]("http://www.backtrack-linux.org/downloads/")

Bactrack is no different than using Ubuntu, It is just a linux distro designed for pen testing, you would really learn more with a run of the mill distro. It dosn't have all the day to day programs which you need and is not ment for daily use, or designed for it.
true, but you can make it work as your normal daily desktop, I have BT5 KDE installed alongside Ubuntu and what I did was create a home user to avoid running root BT (some applications don't work in root) then it took me a day to get sound and video working and another two days to get Cups printing work at start up, installed all my favorite KDE applications and now when I get fed up using ubuntu/gnome I just login to BT5 wonderful KDE desktop environment.

---

### Post by spiky001 on 2011-08-14
I have setup the user account as well, I switch to it as well sometimes BT4. But the op dose say he is new to linux I was just trying to explain what to expect

---

