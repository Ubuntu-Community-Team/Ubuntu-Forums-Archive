---
title: "Problems with newly (and repetedly) installed Xubuntu"
date: 2008-12-13
forum: New to Ubuntu
---

### Post by 2blue on 2008-12-13
Hi

I have an old laptop I'm using to get to now Linux and as an extra workstation. I have just installed Xubuntu 8.10 and it is working fairly well so far. 

When I installed the system to the hard drive I chose the second alternative in the menu for it to overtake the whole hard drive without any partition. I really didn't understand these choices and went for the one I thought would be best.  

This is an old computer Packard Bell easy one, DC 700 MHz processor and only 10GB hard drive, so very limited recourses. I,m not shore about RAM, I have replaced the memory cards with two each 512MB, but that doesn't say very much (probably 256MB or 512MB). Luckily it works, hardware is recognized, wireless card is working, office applications, DVD and I can even play youtube videos (a bit jerky).  

I have one major problem that ruins everything; when I have been messing with settings (or not!!) the framework (I don't know what it's really called) in the desktop environment disappears. All I'm left with when I start the computer are the standard three icons to the left on the screen. Top and bottom line does not appear and what ever I do I can to retrieve them. Does this happen because the laptop are very limited when it comes to memory, processor and storage capacity? Or is it some kind of setting that I cannot find that will fix this. 

This happened both to the previous version of Xubuntu, and now twice to the current version 8.10. If this did not happen Xubuntu would be just fine on this computer. Every thing works, nothing is particularly slow and if I don't have to many things running simultaneously no freeze-ups either.

To sum all up; what can I do to keep all the features of the desktop environment and prevent them for disappearing unexplainably ? 

I hope you can make sense of my English :-)

---

### Post by cardinals_fan on 2008-12-13
> **2blue said:**
> 
I have one major problem that ruins everything; when I have been messing with settings (or not!!) the framework (I don't know what it's really called) in the desktop environment disappears. All I'm left with when I start the computer are the standard three icons to the left on the screen. Top and bottom line does not appear and what ever I do I can to retrieve them. Does this happen because the laptop are very limited when it comes to memory, processor and storage capacity? Or is it some kind of setting that I cannot find that will fix this. 

Do you mean the panels (the bars on the top and bottom)?  Try hitting Alt-F2 and typing "xfce4-panel".  If you want to check memory usage, do this in a terminal (Accessories -> Terminal):
```

sudo apt-get install htop
htop
```
Look at the third bar down from the top that says "Mem" and check the amount used.

Xubuntu is very heavy for a Xfce system.  You could try a lighter weight window manager.  Here are some links for Fluxbox, one option:

[https://help.ubuntu.com/community/Fluxbox](https://help.ubuntu.com/community/Fluxbox)
[http://linuxowns.wordpress.com/2008/07/22/fluxbox_on_ubuntu_guide/](http://linuxowns.wordpress.com/2008/07/22/fluxbox_on_ubuntu_guide/)

---

### Post by 2blue on 2008-12-14
Thank you for your help cardinal :-)  I shall try fluxbox. I find it a bit strange to equip Xubuntu with something that barely suports its functions? 

Another thing I am looking for is a way to check how my computer is running, a sort of system check that tells me how things are running.

---

### Post by cardinals_fan on 2008-12-15
> **2blue said:**
> Thank you for your help cardinal :-)  I shall try fluxbox. I find it a bit strange to equip Xubuntu with something that barely suports its functions? 
Xfce isn't really that heavy.  Xubuntu is just a fairly monstrous implementation *grumbles*.
> **2blue said:**
> 
Another thing I am looking for is a way to check how my computer is running, a sort of system check that tells me how things are running.
There are some graphical apps, but I strongly recommend htop.  You can install it with "sudo apt-get install htop" and run it with "htop".  It can take a little getting used to, but I love it.

---

