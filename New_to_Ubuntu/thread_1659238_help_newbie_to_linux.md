---
title: "help newbie to linux"
date: 2011-01-03
forum: New to Ubuntu
---

### Post by Sirius B on 2011-01-03
hi all im new to linux and have installed Kubuntu 10.10 along side windows xp

I must say operating of linux in general is fast and easy however i know nothing about linux so im sort of messing about trying things out thats all well and good till something goes wrong and i have 1001 problems and questions.

could someone help me?

Question 1

I installed kubuntu along side xp and when switching on the laptop i get grub screen saying this:

Kubuntu 2.6.35 -22 
Failsafe
memtest
windows xp

then since i have run the update process in Kpacketkit i now get 2 kubuntus on the grub screen

kubuntu 2.6.35 - 24
Failsafe
Kubuntu 2.6.35 -22
Failsafe
Memtest
windows xp

as you can see there is 2 kubuntu one saying -24 and one saying -22 Why is this?
and how do i get rid of one of them?

Question 2

the bottom on the screen is what is known in xp as the task bar, well it normally shows what programs or windows i have open or minimized...well ive acidently lost it so if i minimise anything like firefox then it disapears completly instead of showing on the taskbar.

How do i get it back?


thanks in advance to anyone who can help

---

### Post by logangorence on 2011-01-03
First Question-This is Normal, Grub shows memtest, which tests your system in a linux terminal.
This is also normal, you have updated your linux terminal to a higher version, so it leaves the old one there. My computer does that too. Don't click the other one it won't boot Ubuntu.
Second Question-
Open a Terminal, if you don't have applications menu just hit ALT + F2 and type terminal and hit enter.
Type this and hit enter gconftool-2 --shutdown
Type this and hit enter rm -rf ~/.gconf/apps/panel
Type this and hit enter pkill gnome-panel
Restart your Computer
The Panels Should be Back
Or...You can add a new panel by clicking on your top panel and right click on new panel and add to panel...
Add a Show Desktop, Window List, Workspace Switcher, and a Trash
And just move them around to your liking.

---

### Post by Sirius B on 2011-01-03
> **logangorence said:**
> First Question-This is Normal, Grub shows memtest, which tests your system in a linux terminal.
Second Question-This is also normal, you have updated your linux terminal to a higher version, so it leaves the old one there. My computer does that too. Don't click the other one it won't boot Ubuntu.
thanks there thats a big worry lifted. I thought i had messed something up...i will forget about that now.

thanks

Do you know how to get my taskbar back showing my minimised running windows/programs?

---

### Post by Bucky Ball on 2011-01-03
The second one SHOULD boot Ubuntu. They are both 2.6.35 kernels. 

The second one is there in case your latest kernel crashes for some reason. At least you can boot into the machine and figure things out.

---

### Post by sandyd on 2011-01-03
> **Sirius B said:**
> thanks there thats a big worry lifted. I thought i had messed something up...i will forget about that now.

thanks

Do you know how to get my taskbar back showing my minimised running windows/programs?
right click -> add widgets -> task manager/smooth tasks/stasks or whatever you use.

---

### Post by Sirius B on 2011-01-03
> **sandyd said:**
> right click -> add widgets -> task manager/smooth tasks/stasks or whatever you use.
thats it, its worked

thanks all who have replied your all very clever.

this is now solved

---

### Post by Bucky Ball on 2011-01-03
Well done. Please mark thread as 'solved' using 'thread tools'. ;)

Enjoy the OS, the learning curve, and post in a new thread with any other probs.

---

### Post by Sirius B on 2011-01-04
Dont suppose anyone knows if you can add the terminal to the panel bar so i can quickly access it with out having to go through k menu => Apps => system => terminal

---

