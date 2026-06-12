---
title: "New linux user"
date: 2011-09-08
forum: New to Ubuntu
---

### Post by mulroydm on 2011-09-08
I am a CIS freshman in college and recently have been gaining interest in switching from windows to linux.  I have been playing around with LiveCD's with a few distros(Ubuntu, mint, fedora) and have come to like Ubuntu with UNITY despite, what seems to be, disliked by many people.  Either way, I tried installing Ubuntu 11.04 this past weekend on my new Dell Xps 15 l502x with the Nvidia 540M card and the i7 2720QM processor.  Everything seemed to be going fine until UNITY randomly stopped working due to, what I'm guessing to be my Nvidia card being active but not in use?  I've read about Optimus being all screwy on linux and also read about Bumblebee.   Ubunut eventually would not load up and was getting caught up in a console screen and I had to remove the partition and  go back to windows 7.  What advice do you guys have, or what are some mandatory things I need to do get Ubuntu running comfortably on my machine?  Also does anyone have a watered down version of how to install bumblebee?  Thanks a lot from a noob :]  Also, would you guys reccomend installing from the LiveCD or using Wubi?

---

### Post by nothingspecial on 2011-09-08
Hi,

I would recommend installing to your hard drive rather than wubi. Wubi is great for trying Ubuntu but if you want full performance you need to install it.

Did you try the restricted drivers manager?

Also, I'd ask your questions on a busier board like absolute beginner talk or General help.

---

### Post by mulroydm on 2011-09-08
Alright thanks man.

---

### Post by mulroydm on 2011-09-08
I am a CIS freshman in college and recently have been gaining interest  in switching from windows to linux.  I have been playing around with  LiveCD's with a few distros(Ubuntu, mint, fedora) and have come to like  Ubuntu with UNITY despite, what seems to be, disliked by many people.   Either way, I tried installing Ubuntu 11.04 this past weekend on my new  Dell Xps 15 l502x with the Nvidia 540M card and the i7 2720QM processor.   Everything seemed to be going fine until UNITY randomly stopped  working due to, what I'm guessing to be my Nvidia card being active but  not in use?  I've read about Optimus being all screwy on linux and also  read about Bumblebee.   Ubunut eventually would not load up and was  getting caught up in a console screen and I had to remove the partition  and  go back to windows 7.  What advice do you guys have, or what are  some mandatory things I need to do get Ubuntu running comfortably on my  machine?  Also does anyone have a watered down version of how to install  bumblebee?  Thanks a lot from a noob :]  Also, would you guys reccomend  installing from the LiveCD or using Wubi?

---

### Post by mmsmc on 2011-09-08
ive got the same computer, but i refuse to install linux because of the graphics problem, at least until they come out with an oficial release of bumblebee

---

### Post by howefield on 2011-09-08
Threads merged, please use only one thread per issue.

Thank you :)

---

### Post by ubun2geek on 2011-09-08
Hello,
Did you try booting into ubuntu classic?

---

### Post by anewguy on 2011-09-08
I would try including nomodeset on the boot line.  You can edit it at boot time to try it - I know there are many posts on that, but post back if you need help doing so.

If you can at least get to the log on screen, enter your userid but before accepting your password look at the bottom of the screen - there is a group for the session type - click on it and click on Ubuntu Classic and you'll get Gnome and bypass Unity.

Dave ;)

---

### Post by CatKiller on 2011-09-08
Don't install the NVidia driver. It won't work with an Optimus setup.

---

### Post by nmanoogian on 2011-09-08
Definitely install from LiveCD. Its better to keep the file systems separate. I was running some anti-virus software once and it picked up and deleted a pretty critical ubuntu Wubi file - and my data was gone for good. Plus, I try to keep Windows as far away as possible :P

Best of Luck!

---

### Post by Vusys on 2011-09-10
I have the same laptop, but with an i5 and a 525m graphics card. 

In short, nothing works for me and I've given up until 11.10 when I'll try again. 

Hopefully you'll have better luck.

---

