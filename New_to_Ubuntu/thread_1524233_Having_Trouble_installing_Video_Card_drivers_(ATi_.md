---
title: "Having Trouble installing Video Card drivers (ATi x1250)"
date: 2010-07-04
forum: New to Ubuntu
---

### Post by len1444 on 2010-07-04
Hello. I am using Ubuntu 10.04 LTS Desktop Edition, and am completely new to ubuntu (just switched yesterday and haven't looked back). :guitar:

I am running Ubuntu on a virtual machine(virtualbox) before I actually dual-boot it on my actual machine, to see if it works (I assume it should work the same).

With that said, my problem is that I can not install ati x1250 Drivers; to change resolution, better performance in games, etc.

**----Things I have tried-----**


[LIST]
[*]I have searched the forums for similar problems, but what seems to work for others doesn't work for me.
[/LIST]


[LIST]
[*]I have tried the official ati linux drivers, but I learned that 9.3 Catalyst was not supported anymore by "Jaunty" (which I assume is code for Ubuntu).
[/LIST]


[LIST]
[*]I have tried jockey/Hardware Drivers, but it could not find anything.
[/LIST]


[LIST]
[*]I have tried changing resolution by going to System>Preferences>Monitors, but I encounter errors (pics 1+2)
[/LIST]


[LIST]
[*]I have successfully installed fglrx using the command "sudo apt-get install xorg-driver-fglrx" (Which I assume does nothing since ati x1250 is not supported by linux)?
[/LIST]


[LIST]
[*]My xorg.conf (located in /etc/X11/xorg.conf) is empty, and changing it with someone elses does no good either.
[/LIST]


[LIST]
[*]I have tried "sudo dpkg-reconfigure xserver-xorg", but it just stalls and does nothing (pic 3).
[/LIST]


[LIST]
[*]typing "sudo startx" in the terminal gets me another error (see pic 4)
[/LIST]

I would appreciate it if you could help me get these drivers installed (which I'm sure there is a way since the open source drivers support all the xpress chipsets, but I'm simply too uneducated to know how to do it).

Thanks for all your future help! ;)

Regards, Leo

---

### Post by kimikrishna on 2010-07-04
> **len1444 said:**
> 

I am running Ubuntu on a virtual machine(virtualbox) 
To change resolution, better performance in games, etc.



Virtual machine is not the same as "Your" Machine.

So you can't expect Better resolutions and performances etc...

---

### Post by Joe325 on 2010-07-04
Have you looked at [envy]("http://albertomilone.com/nvidia_scripts1.html")...  This has helped me in the past

---

### Post by len1444 on 2010-07-04
> **kimikrishna said:**
> Virtual machine is not the same as "Your" Machine.

So you can't expect Better resolutions and performances etc...

I don't expect better performance, just want to see if it will install graphics card successfully (if not, it'll just be a waste of time dual-booting only to find out the graphics don't work). Also, about the resolution, I have done installation of xp drivers before, and that changed the resolution (on the virtual machine).

> **Joe325 said:**
> Have you looked at [envy]("http://albertomilone.com/nvidia_scripts1.html")...   This has helped me in the past

I have looked up envy, but it was replaced by Jockey: ****[COLOR=red][B]"Envy is no longer supported  starting from Ubuntu  10.04. Please use Jockey instead."
[/B][/COLOR]

Thanks for the help, 

Leo

---

### Post by Joe325 on 2010-07-04
Sorry - just saw you had 10.04 version. My bad :(

---

### Post by len1444 on 2010-07-04
> **Joe325 said:**
> Sorry - just saw you had 10.04 version. My bad :(

Hey at least you bothered to try and help, no harm done right?

Leo

---

### Post by tom.swartz07 on 2010-07-04
Hiya, I have an ATI x1270 card, and I had the same questions as you.

ATI x1250 is listed under the same circumstances as the ATI x1270; the legacy drivers are the only things supported.

This means: the latest version of Ubuntu that you could use that takes advantage of the official ATI drivers is 8.04. Jaunty is the code name of Ubuntu 9.04 (released in April of 2009) You could install the older version of 8.04 and use the drivers there (I did when I was still big on the Half-Life games) but that's entirely up to you. Unfortunately, with that card, even with the official drivers installed, you wont get the best performance for gaming, so you might need Windows if you really really want to use games.

You can, however, simply use the default kernel acceleration that Ubuntu provides. I've experienced some problems with Compiz (the program that gives all of those cool visual effects), and I had to disable them in favor of the other method for window decoration.

Other than that, what is installed by default should be all you need; you shouldn't have to worry about video drivers.


If you have experienced a 'lag' in the way that the windows work and move, I could help walk you through the steps to switch off Compiz and turn on Metacity.

---

### Post by len1444 on 2010-07-05
> **tom.swartz07 said:**
> Hiya, I have an ATI x1270 card, and I had the same questions as you.

ATI x1250 is listed under the same circumstances as the ATI x1270; the legacy drivers are the only things supported.

This means: the latest version of Ubuntu that you could use that takes advantage of the official ATI drivers is 8.04. Jaunty is the code name of Ubuntu 9.04 (released in April of 2009) You could install the older version of 8.04 and use the drivers there (I did when I was still big on the Half-Life games) but that's entirely up to you. Unfortunately, with that card, even with the official drivers installed, you wont get the best performance for gaming, so you might need Windows if you really really want to use games.

You can, however, simply use the default kernel acceleration that Ubuntu provides. I've experienced some problems with Compiz (the program that gives all of those cool visual effects), and I had to disable them in favor of the other method for window decoration.

Other than that, what is installed by default should be all you need; you shouldn't have to worry about video drivers.


If you have experienced a 'lag' in the way that the windows work and move, I could help walk you through the steps to switch off Compiz and turn on Metacity.

Thanks for the quick reply!

I'm afraid running without the display drivers is more than just a performance problem, I can't stand using 800x600 resolution! (Also, even flash games suffer a performance hit). 

I was meaning to try switching versions, but was not sure what version to switch to. Just to clarify, if I switch to Ubuntu 8.04, I would be able to use the latest ati drivers for linux?

The only thing holding me back is that if I go to a less recent system, would updates for ubuntu still work, will I get more vulnerability to viruses/bugs? Will certain programs/software be unaccessible ( Basically, what are the differences for Ubuntu 10.04 and Ubuntu 8.04? Also, would this be a good link to get it from? [http://releases.ubuntu.com/hardy/](http://releases.ubuntu.com/hardy/)

About Compiz, I have never seen any cool desktop effects or anything (apart from switching through desktops 1 and 2, but there are no effects involved in that). But if it decreases performance, yes, I would like to know how to uninstall it.

I hope this is not asking too much, thanks for the help.

Leo

---

### Post by tom.swartz07 on 2010-07-05
> **len1444 said:**
> Thanks for the quick reply!

I'm afraid running without the display drivers is more than just a performance problem, I can't stand using 800x600 resolution! (Also, even flash games suffer a performance hit). 

I was meaning to try switching versions, but was not sure what version to switch to. Just to clarify, if I switch to Ubuntu 8.04, I would be able to use the latest ati drivers for linux?

The only thing holding me back is that if I go to a less recent system, would updates for ubuntu still work, will I get more vulnerability to viruses/bugs? Will certain programs/software be unaccessible ( Basically, what are the differences for Ubuntu 10.04 and Ubuntu 8.04? Also, would this be a good link to get it from? [http://releases.ubuntu.com/hardy/](http://releases.ubuntu.com/hardy/)

About Compiz, I have never seen any cool desktop effects or anything (apart from switching through desktops 1 and 2, but there are no effects involved in that). But if it decreases performance, yes, I would like to know how to uninstall it.

I hope this is not asking too much, thanks for the help.

Leo

Hey Leo,

Lets try this. 

Since you already have 10.04 installed, we'll see what we could do using Metacity (the alternative to Compiz)

First, I need you to run one simple terminal command: this will tell me what resolutions you could run on your screen.
Open the terminal from Applications, Accessories, Terminal and type the following ```
xrandr
```
_Copy and paste the output here_ (you could use CRTL+SHIFT+C to copy from the terminal)


The easiest way that I have seen to switch to Metacity is to use a program called Ubuntu-Tweak. Let's install that and get on with the show.

1) Install Ubuntu-Tweak from here: [http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)
2) Right click on your background, Select 'Change Background', then click on the Visual Effects tab on the top. Select NONE.
3) Open Ubuntu Tweak (Applications, System Tools) and select the 2 options highlighted in the attached picture.

Once you restart your computer, you will be using the Metacity window decorations, rather than the Compiz decorations that were causing a problem.



If you still are having problems with this, and you REALLY really want to get it fixed now, I'd suggest just dropping back to 8.04. It is fully supported until April 2011, so you don't have to worry about security- Cannonical will provide patches and fixes up until then. I do have to warn you though, it is a bit 'hairier' than 10.04- the interface has changed quite a bit since then. 
You could download it from here: [http://old-releases.ubuntu.com/releases/8.04.2/](http://old-releases.ubuntu.com/releases/8.04.2/)
**JUST MAKE SURE YOU UPDATE YOUR COMPUTER RIGHT AWAY IF YOU CHOOSE THIS ROUTE.** There is a major security flaw that they patched, and it is only available once you update after an install. 


I hope that clears things up for you!

Cheers,
Tom

---

### Post by 3rdalbum on 2010-07-05
Two things:

1. Virtual machines do NOT expose the host's graphics card. As far as the virtualised Ubuntu is concerned, you don't have an ATI graphics card, so it will use a generic driver. You can improve performance in the virtual machine by installing the Virtualbox Guest Additions, either from the repositories or by using the "Mount Guest Additions" function from Virtualbox.

2. Ubuntu comes with the only driver for the X1250. ATI does not make a driver for this card, only the Linux community does. The correct driver will be activated by default when you install Ubuntu on real hardware.

---

### Post by len1444 on 2010-07-05
> **3rdalbum said:**
> Two things:

1. Virtual machines do NOT expose the host's graphics card. As far as the virtualised Ubuntu is concerned, you don't have an ATI graphics card, so it will use a generic driver. You can improve performance in the virtual machine by installing the Virtualbox Guest Additions, either from the repositories or by using the "Mount Guest Additions" function from Virtualbox.

2. Ubuntu comes with the only driver for the X1250. ATI does not make a driver for this card, only the Linux community does. The correct driver will be activated by default when you install Ubuntu on real hardware.

Thank you! This is all I needed, sorry tom, I was going to try your solution but he just gave me another route.

Thanks again,

Leo 
(Will mark this thread as Solved now)

---

### Post by carolpaul on 2010-07-05
> **len1444 said:**
> Thank you! This is all I needed, sorry tom, I was going to try your solution but he just gave me another route.
 
Thanks again,
 
Leo 
(Will mark this thread as Solved now)
 
 
This also helped me. Thank you So much!!!!!
 
 
[FONT=Calibri][SIZE=1]Any international friends who need any help in China, pls contact carol ! We would like to protect your business and rights in China![/SIZE][/FONT]
[SIZE=1] [/SIZE]
[FONT=Calibri][SIZE=1][www.wincomchina.com.cn]("http://www.wincomchina.com.cn")[/SIZE][/FONT]
[FONT=Calibri][SIZE=1][www.wincomchina.com]("http://www.wincomchina.com")[/SIZE][/FONT]

---

### Post by kimikrishna on 2010-07-05
@celinar,
This topic has been marked solved by the person who created this topic. 

Create a new topic. And Post your questions/problems and also computer specs there.

---

### Post by tom.swartz07 on 2010-07-05
> **3rdalbum said:**
> Two things:

1. Virtual machines do NOT expose the host's graphics card. As far as the virtualised Ubuntu is concerned, you don't have an ATI graphics card, so it will use a generic driver. You can improve performance in the virtual machine by installing the Virtualbox Guest Additions, either from the repositories or by using the "Mount Guest Additions" function from Virtualbox.

2. Ubuntu comes with the only driver for the X1250. ATI does not make a driver for this card, only the Linux community does. The correct driver will be activated by default when you install Ubuntu on real hardware.


I was confused- he had mentioned that 10.04 was both installed in virtualbox, AND as a dual boot. I had assumed he was trying to get the drivers installed for the dual boot situation

---

