---
title: "Suspected radeon issue"
date: 2010-06-26
forum: New to Ubuntu
---

### Post by nickdc on 2010-06-26
I'm an experienced pc user but still fairly baffled by Linux. Fell in love with ubuntu after installing on an older pc, so installed (10.04) on main desktop as dual boot with Winxp. Very disappointed to run into immediate problems with my dual display (2 x lcd screens on dvi outputs from radeon X1950 pro (RV570)). I've spent several weeks now on and off searching these forums, reading documentation etc but so far no solution to the biggest problem, a lag in scrolling, moving windows etc, even delayed response after mouse clicks, which really makes the GUI unusable. I can live with the panels etc appearing on the right hand screen and not being abke to make the left-hand one primary (without physically changing the monitor inputs, which then messes it up for Windows) but not this lack of responsiveness. From what I've read, I'm pretty sure it's the combination of the graphics card and the drivers that's causing the problem, but would be grateful for confirmation of this and any suggestions (apart from changing the graphics card) for solving it. I've confirmed that ubuntu is using the default open source drivers and I've not tried to load anything else, believing from what I've read that they are the best option available; but unless there are some further teaks I can do they are not up to speed on my system (self-built with 3GHz P4 and 2Gb RAM). A lot of the postings I've read suggest there may be further configuarations I could possibly do, but they assume a technical familiarity with Linux which I don't have ... yet, which is why I've posted in this forum.

Grateful for any advice ...

---

### Post by tom.swartz07 on 2010-06-26
> **nickdc said:**
> I'm an experienced pc user but still fairly baffled by Linux. Fell in love with ubuntu after installing on an older pc, so installed (10.04) on main desktop as dual boot with Winxp. Very disappointed to run into immediate problems with my dual display (2 x lcd screens on dvi outputs from radeon X1950 pro (RV570)). I've spent several weeks now on and off searching these forums, reading documentation etc but so far no solution to the biggest problem, a lag in scrolling, moving windows etc, even delayed response after mouse clicks, which really makes the GUI unusable. I can live with the panels etc appearing on the right hand screen and not being abke to make the left-hand one primary (without physically changing the monitor inputs, which then messes it up for Windows) but not this lack of responsiveness. From what I've read, I'm pretty sure it's the combination of the graphics card and the drivers that's causing the problem, but would be grateful for confirmation of this and any suggestions (apart from changing the graphics card) for solving it. I've confirmed that ubuntu is using the default open source drivers and I've not tried to load anything else, believing from what I've read that they are the best option available; but unless there are some further teaks I can do they are not up to speed on my system (self-built with 3GHz P4 and 2Gb RAM). A lot of the postings I've read suggest there may be further configuarations I could possibly do, but they assume a technical familiarity with Linux which I don't have ... yet, which is why I've posted in this forum.

Grateful for any advice ...



All of the symptoms that you are experiencing are exactly similar to my problems with 10.04.

I cant directly speak for you, but in my case I have an ATI Radeon X1270 and the card is no longer supported by ATI at all. Because of this, I must rely on the Ubuntu kernel for the utility of my graphics card. 

When I upgraded to 10.04 (Ive been using it since 8.04, heh) I noticed that visual effects completely wrecked the system. Although it could handle them, there would be some kind of error when interfacing with the window manager and Xorg, causing everything to be laggy.


Here is what I suggest you do, and the choice is ultimately up to you.

If you really don't want to live without Visual Effects, buy an NVidia card; they have almost full support for Ubuntu. 

If you don't want to go buy another graphics card, there is 3 easy steps to turn off compiz (the program thats doing this). 
1) Install Ubuntu-Tweak from here: [http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)
2) Right click on your background, Select 'Change Background', then click on the Visual Effects tab on the top. Select NONE.
3) Open Ubuntu Tweak (Applications, System Tools) and select the 2 options highlighted in the attached picture.

Once you restart your computer, you will be using the Metacity window decorations, rather than the Compiz decorations that were causing a problem.



Let me know how it works out for you! :D

---

### Post by nickdc on 2010-06-26
> **tom.swartz07 said:**
> 

Let me know how it works out for you! :D

Hey, it works great Tom! Thanks so much for your help. Smooth scrolling and everything snappy at last.:p

---

### Post by tom.swartz07 on 2010-06-26
> **nickdc said:**
> Hey, it works great Tom! Thanks so much for your help. Smooth scrolling and everything snappy at last.:p

Wonderful!

Im really glad to help!

If you would be so kind, would you please mark this thread as "Solved" from the thread tools menu up top? This way, other people who may have the same problem could use this as reference! :D

Cheers!

---

