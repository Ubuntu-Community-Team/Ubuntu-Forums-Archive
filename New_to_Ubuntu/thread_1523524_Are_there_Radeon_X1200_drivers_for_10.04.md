---
title: "Are there Radeon X1200 drivers for 10.04?"
date: 2010-07-03
forum: New to Ubuntu
---

### Post by Justin&#28814; on 2010-07-03
[FONT=Courier New][SIZE=4]Hey Everyone I just joined the ubuntu community here, and im still using this farely old _***toshiba satellite L305d***_ I got from walmart in hawaii. Everything runs fine and ubuntu found almost all my drivers right off, but i cant play any games and **I cant watch movies without thinking im watching FX at my friends house** and watching the **screen glitch every time more then 4 people walk into a room** in the movie. I looked up alot of stuff for the ati driver and found out that people mostly say that** im stuck with what i have right now** ?, I was wondering if any one has solved this problem on 10.04 or am i too selfish to be asking for relatively smooth video? [/SIZE][/FONT][FONT=Courier New]
[/FONT]

---

### Post by tom.swartz07 on 2010-07-03
> **Justin&#28814 said:**
> [FONT=Courier New][SIZE=4]Hey Everyone I just joined the ubuntu community here, and im still using this farely old _***toshiba satellite L305d***_ I got from walmart in hawaii. Everything runs fine and ubuntu found almost all my drivers right off, but i cant play any games and **I cant watch movies without thinking im watching FX at my friends house** and watching the **screen glitch every time more then 4 people walk into a room** in the movie. I looked up alot of stuff for the ati driver and found out that people mostly say that** im stuck with what i have right now** ?, I was wondering if any one has solved this problem on 10.04 or am i too selfish to be asking for relatively smooth video? [/SIZE][/FONT][FONT=Courier New]
[/FONT]

Hi, and welcome to the forums!

Since you're new, I understand that you may be unfamiliar with the Forum policies, and Im sure that many other users here will complain about it; PLEASE do not use fancy fonts and formatting. It makes the messages difficult to read, and will turn others off from answering your question.



That being said, Let's get to your question:

The short answer is, No. There are no open source drivers for the ATI Radeon X1200 card. I have the same card in my Dell Inspiron, and I have the same problems you experienced. 

I HAVE found, however, that disabling Compiz makes the problem a non-issue. Compiz and Metacity are two programs that handle the 'drawing' of the windows and images you see. By using Metacity instead of Compiz, you will get better performance at the expense of not being able to impress your friends with spinning desktop cubes and water ripples across your screen.


To enable Metacity, the easiest way is to do the following;

1) Install Ubuntu-Tweak from here: [http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)
2) Right click on your background, Select 'Change Background', then click on the Visual Effects tab on the top. Select NONE.
3) Open Ubuntu Tweak (Applications, System Tools) and select the 2 options highlighted in the attached picture.

Once you restart your computer, you will be using the Metacity window decorations, rather than the Compiz decorations that were causing a problem.

Let me know how it works out for you!

---

### Post by tom.swartz07 on 2010-07-03
Also, how were you watching the movies in question?
Were they just on the native LCD screen, or did you have the computer plugged into a TV screen?

---

### Post by metalfan_ on 2010-08-19
i disabled compiz, still i cant even play a simple dvdrip in fullscreen....
does this mean i have to downgrade to 9.04 again?


is there no way to get the old driver from 9.04 working with 10.04?

---

### Post by khelben1979 on 2010-08-20
Your Radeon X1200 is supported of the ATi Catalyst up to version 9.3. If this driver works with the supplied X server in Ubuntu 10.04, then yes! it would work! Otherwise you haveto use an older version of Ubuntu or change to another Linux distribution where this works.

The Ubuntu 10.04 uses a newer X server and this is the source of your problem.

If you want to use a more modern software with an older version of Ubuntu, then you can use [backports]("https://help.ubuntu.com/community/UbuntuBackports").

---

### Post by QIII on 2010-08-20
... and I have to say again:  This is not a fault with Ubuntu or any other Linux distribution.

AMD/ATI has chosen to stop supporting the drivers for those legacy cards, so they are not being updated to keep up with Xorg.

It is a difficult situation for you, but makes business sense to them.  They have to weigh the amount of effort and resources required to maintain those drivers against the possible number of those older cards still being used (which have, in general, probably reached and surpassed their expected mechanical lifetimes.)

---

### Post by Stigmata13 on 2010-08-20
I have an Acer Aspire 5515 with integrated Radeon X1250 graphics, so I suppose you're in the same boat as I am. The current drivers supplied by ATI for legacy cards are very outdated, and I know for sure they don't work with 10.04 or even 9.10 for that matter.
Your best bet would be to stick with the open source driver your computer had installed just after a fresh install, or go to an older Ubuntu release, such as 8.04 perhaps. 
Other than that, all you can do is wait and hope that ATI decides to upgrade these drivers to support the latest Xorg.

---

### Post by clhsharky on 2010-08-20
> still i cant even play a simple dvdrip in fullscreen....
Is your dvdrip on your harddrive(media player) or downloading from internet(adobe flash).
Big difference between players.

Sharky

---

### Post by Mark Phelps on 2010-08-22
> **Stigmata13 said:**
> ... and hope that ATI decides to upgrade these drivers to support the latest Xorg.

Now THAT is a complete waste of time.  ATI has made it clear in their release notes, when they dropped support, that they have no intentions of ever updating their legacy drivers.

In contrast, they did update their MS Windows legacy drivers ... but they appeared to stop that work as well, with Catalyst 10.2.

---

### Post by khelben1979 on 2010-08-24
> **Mark Phelps said:**
> In contrast, they did update their MS Windows legacy drivers ... but they appeared to stop that work as well, with Catalyst 10.2.

From a business perspective, they did the right thing.

I think that AMD/ATI would need more employees working on their linux graphic drivers. I wonder how many they have over there right now?

---

### Post by emanuel.b on 2010-08-24
I have an older ATI mobile graphics card (check the signature), and the open source drivers work perfectly for me. I run Compiz and flash games all the time on my machine. Perhaps you should run a software update, just to be sure you have the latest open source drivers...

---

### Post by khelben1979 on 2010-08-30
There is one possibility to use the non-free ATi legacy drivers, but I would **not** recommend it (and certainly not to newbies). Download the source files from xorg and then purge the configuration files from your present X server and remove it from the Ubuntu system.

Doing that makes you able to install an older version of the X server which is compatible with the 9.3 Catalyst driver without the need to go down to a lower version of Ubuntu. How that would affect the Ubuntu system I'm not certain of.. but it should work.

However... what I would recommend and what seems like the best choice, that is that you use the ATi open source driver which have been suggested in this thread. That driver is part of the Linux kernel and should be activated by itself if the X server detects your ATi graphics.

---

### Post by Wootyeah on 2012-04-09
Has anyone tried this?  I know this is an old thread, but this problem still exists as ATI has discontinued support.  I tried the xorg-edgers driver and actually had the Compiz cube working on 10.10...until I rebooted and/or updated.  I have tried everything I've come across in the last 4 days, open-source and proprietary.  I really don't want to give up and go back to Hardy (the last one that works with x1200) or Debian (been using Ubuntu since Fiesty) and have way too much time in this.  But, if Windows is all that works...

---

### Post by Mark Phelps on 2012-04-10
Replacing a current working X-server with one two years old is just asking for trouble.  You will have to lock the packages and thus be denied any future updates to them.  Plus, if there are problems, you won't be able to get any support.

---

