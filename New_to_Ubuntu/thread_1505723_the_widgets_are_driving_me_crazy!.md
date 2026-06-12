---
title: "the widgets are driving me crazy!"
date: 2010-06-09
forum: New to Ubuntu
---

### Post by thomz92 on 2010-06-09
hi everyone. i just installed kubuntu 10.04 as my second operating system on my computer. installation seemed to go fine and everything, and it booted up as normal. theres a few bugs here and there, but overall i think the looks and functionality are amazing! way to go, kubuntu team, whoever you guys are! 

BUT! the widgets are driving me absolutely crazy. it seems like i can't keep them in the spot i want. they just move around on their own! ill drag a widget to a corner, for example, and it might stay there, or it might pop back to where it was before. ill resize something, and it might stay that way or it might go back the origional size and/or move to the spot it used to be two days ago. could this be a bad install or something? or maybe a bad CD? i tried the CD on my friends computer and the same thing happens. i find it hard to believe that something this bad was overlooked by the kubuntu team. can anyone give some advice or comment?

---

### Post by ankspo71 on 2010-06-09
Hi,
I don't have this problem now, but I did twice already, both times after fresh installs of Kubuntu 10.04. In my case, it went away both times after installing the closed-source nvidia graphics drivers. Being that installing the drivers seemed to cure my widget moving/resizing problems, I assumed it had something to do with the nouveau graphics drivers for nvidia graphics cards, but other users told me it happens to them with other types of drivers/cards too. 

Here is another topic started about this:
[http://ubuntuforums.org/showthread.php?t=1464681](http://ubuntuforums.org/showthread.php?t=1464681)
I don't think anyone has found a fix for this yet, except for trying to restart plasma-desktop, which might or might not permanently fix it.
```
killall plasma-desktop
plasma-desktop
```
Here is a bug report for the problem: 
[https://bugs.launchpad.net/ubuntu/+source/kdebase/+bug/569877](https://bugs.launchpad.net/ubuntu/+source/kdebase/+bug/569877)
If you have the time, you can log in can use the option to say "this effects me too" and add a comment too if you wish. (Registering will be required though)
Hope this helps.

---

