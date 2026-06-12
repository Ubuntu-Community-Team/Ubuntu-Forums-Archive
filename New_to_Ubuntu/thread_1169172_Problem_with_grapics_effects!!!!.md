---
title: "Problem with grapics effects!!!!"
date: 2009-05-24
forum: New to Ubuntu
---

### Post by EmilyAmundson on 2009-05-24
Hello,

I am completely new to Ubuntu and Linux in general, so I don't exactly know what/where my problem is. I would really like to use the wobbly windows and the desktop cube, but whenever I try to enable graphics effects I have this problem:
[IMG]http://i327.photobucket.com/albums/k478/eamundson/Screenshot.png




I have tried many things and looked at many forums.

I have an Intel Mobile GM965/GL960 Integrated Graphics card on my Dell XPS M1330.

What I did was go directly to the Ubuntu home page, downloaded Ubuntu Desktop Edition 9.04, and chose to run it "inside of Windows". I have not installed any drivers or anything (for I do not know what I need even though I have searched) or anything (I know it says I have Emerald on the screenshot of my desktop, but I have installed nothing).

Detailed, For Dummies-type responses would be very much appreciated! Thank you!

---

### Post by random_hypocrisy on 2009-05-24
Never mind I re-read your question. 

Go back to Windows, Intel on Linux is hell!

---

### Post by EmilyAmundson on 2009-05-24
I have no idea. I saw that somewhere online, but I didn't know what it was...

---

### Post by EmilyAmundson on 2009-05-24
:'( ok...

---

### Post by random_hypocrisy on 2009-05-24
> **EmilyAmundson said:**
> I have no idea. I saw that somewhere online, but I didn't know what it was...

Yeah sorry, my bad. Your using Jaunty.

Just go back to Windows. Intel on Linux sucks.

---

### Post by overdrank on 2009-05-24
Hi and you may look at the link in my signature about intel graphics on Jaunty. :)

---

### Post by random_hypocrisy on 2009-05-24
> **overdrank said:**
> Hi and you may look at the link in my signature about intel graphics on Jaunty. :)

I dont think someone THAT new wants to edit a x.org file...

---

### Post by overdrank on 2009-05-24
> **random_hypocrisy said:**
> I dont think someone THAT new wants to edit a x.org file...

Some would think saying going back to windows is not nice. :)

---

### Post by TheNosh on 2009-05-25
you can get by just fine if you don't enable desktop effects/compiz

if you really want to it's doable, but the drivers are blacklisted and can cause the system to hang (then again i run intel graphics and don't have any trouble... i still turn off compiz if i'm working on something important as an extra precaution thou)

---

### Post by EmilyAmundson on 2009-05-25
> **TheNosh said:**
> you can get by just fine if you don't enable desktop effects/compiz

if you really want to it's doable, but the drivers are blacklisted and can cause the system to hang (then again i run intel graphics and don't have any trouble... i still turn off compiz if i'm working on something important as an extra precaution thou)


Yeah, it's running just fine right now... I really don't do much that would require graphics use, since I have a desktop for gaming and whatnot, so I don't have to worry about it making other things run slowly or anything like that... I just would really like to know what to do...

---

### Post by Kareeser on 2009-05-25
Stick with Ubuntu. I have an an Intel graphics card older than yours, and mine works quite well.

Take a look at the link mentioned above:
[http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582)

---

### Post by EmilyAmundson on 2009-05-25
Thank you! I'm going to try it...

---

### Post by zeroseven0183 on 2009-05-25
Did you happen to see any notification to install Hardware Drivers (Proprietary drivers)?
If not, you can check it at **System** > **Administration** > **Hardware Drivers**.

---

### Post by Richard9795 on 2009-05-25
These instructions Fixed My problem:

Go to System > Administration > Software Sources, Then Go To Third-Party Software Tab, push the add button, Then Input These 2 lines (make sure it is one by one):

deb [http://ppa.launchpad.net/siretart/ppa/ubuntu](http://ppa.launchpad.net/siretart/ppa/ubuntu) jaunty main

deb-src [http://ppa.launchpad.net/siretart/ppa/ubuntu](http://ppa.launchpad.net/siretart/ppa/ubuntu) jaunty main

Then Lets Go to The Terminal (Applications > Accessories > Terminal.

Input This line: 
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 0xce90d8983e731f79

Then input this:
sudo aptitude update

then 
sudo aptitude install xserver-xorg-video-intel-2.4

When done, log out, then log back in, Done!

What it does, it uses the graphics drivers from the previous version of ubuntu (ubuntu 8.10), because the ones that came with 9.04 SUCK, so people should install these instead.

---

### Post by &#21315;&#23547;cc on 2009-05-25
too bad!

---

### Post by EmilyAmundson on 2009-05-25
Thank you everyone for your help! I followed all of the advice given to me, but then I just put in this code:
sudo apt-get update && sudo apt-get upgrade

and it started working, for anyone who has the same problem. I'm not sure if it's a combination of the advice or just this code, but it's working now and nothing has slowed down! Thank you!

---

