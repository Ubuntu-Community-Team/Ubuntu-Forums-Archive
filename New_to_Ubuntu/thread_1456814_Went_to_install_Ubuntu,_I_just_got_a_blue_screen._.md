---
title: "Went to install Ubuntu, I just got a blue screen. What went wrong?"
date: 2010-04-17
forum: New to Ubuntu
---

### Post by chrisxuk on 2010-04-17
Hi, tried to install Ubuntu 9.10 earlier today but encountered a problem.

Booted from CD-Rom, and got the menu that asks if you want to install Ubuntu or boot a Live CD etc. Chose to install Ubuntu and then I got a black screen with a white Ubuntu logo glowing. A few seconds later a screen of text appeared. It disappeared too fast though so didn't get chance to read it.

At this point I was thinking "excellent, it's working". I was wrong. After the screen of text disappeared my monitor just glowed blue, like when it's on but there's no input. Hope that makes sense, any ideas what's going wrong and how I can install Ubuntu?

Thanks

---

### Post by cuberts on 2010-04-17
> **chrisxuk said:**
> Hi, tried to install Ubuntu 9.10 earlier today but encountered a problem.

Booted from CD-Rom, and got the menu that asks if you want to install Ubuntu or boot a Live CD etc. Chose to install Ubuntu and then I got a black screen with a white Ubuntu logo glowing. A few seconds later a screen of text appeared. It disappeared too fast though so didn't get chance to read it.

At this point I was thinking "excellent, it's working". I was wrong. After the screen of text disappeared my monitor just glowed blue, like when it's on but there's no input. Hope that makes sense, any ideas what's going wrong and how I can install Ubuntu?

ThanksOk so what I do when I boot from a CD rom is that first you should test Ubuntu out, and play around with it. WHen you are satisfied, click on one of the things on the desktop that say install Ubuntu. Then it will ask you to go through 7 steps to install Ubuntu. Follow them, and you should be fine. Hope this helps.

---

### Post by cuberts on 2010-04-17
> **chrisxuk said:**
> Hi, tried to install Ubuntu 9.10 earlier today but encountered a problem.

Booted from CD-Rom, and got the menu that asks if you want to install Ubuntu or boot a Live CD etc. Chose to install Ubuntu and then I got a black screen with a white Ubuntu logo glowing. A few seconds later a screen of text appeared. It disappeared too fast though so didn't get chance to read it.

At this point I was thinking "excellent, it's working". I was wrong. After the screen of text disappeared my monitor just glowed blue, like when it's on but there's no input. Hope that makes sense, any ideas what's going wrong and how I can install Ubuntu?

ThanksOk so what I do when I boot from a CD rom is that first you should test Ubuntu out, and play around with it. WHen you are satisfied, click on one of the things on the desktop that say install Ubuntu. Then it will ask you to go through 7 steps to install Ubuntu. Follow them, and you should be fine. Hope this helps.

---

### Post by thomas144 on 2010-04-17
I would recommend about the same as cuberts. Try booting from the live CD. When the screen comes up, select your language and then "Try Ubuntu without any changes to your computer." Here, you can play around, see what programs are included, try the Internet connection, etc. If the boot fails, or something doesn't work, post back here for help.

---

### Post by halitech on 2010-04-17
> **chrisxuk said:**
> Hi, tried to install Ubuntu 9.10 earlier today but encountered a problem.

Booted from CD-Rom, and got the menu that asks if you want to install Ubuntu or boot a Live CD etc. Chose to install Ubuntu and then I got a black screen with a white Ubuntu logo glowing. A few seconds later a screen of text appeared. It disappeared too fast though so didn't get chance to read it.

At this point I was thinking "excellent, it's working". I was wrong. After the screen of text disappeared my monitor just glowed blue, like when it's on but there's no input. Hope that makes sense, any ideas what's going wrong and how I can install Ubuntu?

Thanks

What kind of system specs are you working on right now? (ie. video card, ram, cpu?) Using a crt or lcd monitor?

---

### Post by candtalan on 2010-04-18
Also, keep in mind that one of the options  in th einitial menu when booting up from the CD is I think 
F4 (safe graphics)
(this is not the 'same' as a Windows safe mode)

If this works ok in the live CD running then do the install from the live CD desktop icon, and I believe the safe graphics inforanmation will b ecarried forward into the install.

---

### Post by chrisxuk on 2010-04-18
Thanks for the replies. Just woken up now, so I can reply :)

> **halitech said:**
> What kind of system specs are you working on right now? (ie. video card, ram, cpu?) Using a crt or lcd monitor?

AMD Dual Core Athlon X2 2.80GHz
ATI HD Radeon 4850 512mb
4GB DDR2 RAM

Got two monitors plugged in at the moment. 1 x 22" & 1 x 19". The 22" is connected to my GFX card via HDMI and my 19" is connected to my graphics card via D-sub.

> **candtalan said:**
> Also, keep in mind that one of the options  in th einitial menu when booting up from the CD is I think 
F4 (safe graphics)
(this is not the 'same' as a Windows safe mode)

If this works ok in the live CD running then do the install from the live CD desktop icon, and I believe the safe graphics inforanmation will b ecarried forward into the install.

Thanks, i'll give this a go :)

---

### Post by chrisxuk on 2010-04-18
Great news, going into Safe Graphics mode has meant that I was able to install Ubuntu! :D 

My wireless adapter worked straight away, it was even easier to set up on Ubuntu than on XP. Didn't need any drivers!

Only problem I think i'm having is that the screen resolution is all wrong. The only resolution choice I have is 640 x 480, which is horrible. It cuts off half the screen! Any idea how I can fix this? Thanks.

---

### Post by marshmallow1304 on 2010-04-18
Check in System->Administration->Hardware Drivers to see if there are any restricted drivers available.

---

### Post by chrisxuk on 2010-04-18
All sorted now, thanks. Got my native resolution of 1440x900 working fine :D

---

### Post by Kayden on 2010-04-18
> **marshmallow1304 said:**
> Check in System->Administration->Hardware Drivers to see if there are any restricted drivers available.
This. Also, if it's an nVidia card, enabling any restricted drivers may install the nVidia X Server Settings Manager, which should allow you to set your screen resolution to the proper size (theoretically, it *should* also change your xconfig to reflect the altered settings, though I've had trouble with this feature in the past).

**EDIT:** Apologies. I just noticed your post saying you got it working. Hope you enjoy Ubuntu!

---

