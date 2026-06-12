---
title: "ATI Radeon Xpress 200 - display not supported"
date: 2011-01-17
forum: New to Ubuntu
---

### Post by Ethan hunt on 2011-01-17
have recently installed Ubuntu 10.10. The graphics card is 
ATI RAD-EON XPRESS 200. 

01:05.0 VGA compatible controller [0300]: ATI Technologies Inc RC410 [Radeon Xpress 200] [1002:5a61]

Does this support graphics for Ubuntu 10.10?

whenever i try to play games, the sounds appear in the background, but display shows "not supported"

My monitor is Acer H163HQ.

please help, I am absolutely new to Ubuntu.

---

### Post by Mark Phelps on 2011-01-17
It's supported -- but only minimally.  AMD/ATI dropped Linux driver support for that chipset years ago.  The default open-source driver DOES support that, but you'll probably be limited to 2D (desktop) graphics and very basic 3D support.  Sorry, but there are no newer drivers that will work with recent Ubuntu versions and your ATI chipset.

---

### Post by Ethan hunt on 2011-01-17
@Mark Phelps - Thanks for the reply. It seems i must change my PC.

---

### Post by 3rdalbum on 2011-01-17
The game must be using a resolution that your monitor can't handle. The monitor is saying 'not supported'. Your 3d support on that card might not be good enough for games anyway.

---

### Post by Ethan hunt on 2011-01-18
yes, i am able to get the sound output but not the display in monitor.
i use a Acer 163HQ. Also i use windows 7 but no problem in display while playing game in win 7.
i am encountering this problem only while using ubuntu 10.10
i searched for monitor driver updates in acer website. but couldnt find any.
is there any open source so that i can get the display in my monitor?

---

### Post by mastablasta on 2011-01-18
what game? you need to set propper resolution in game. 
 
you odnt' need special drivers for monitor.

---

### Post by Mark Phelps on 2011-01-18
> **Ethan hunt said:**
> yes, i am able to get the sound output but not the display in monitor.
i use a Acer 163HQ. Also i use windows 7 but no problem in display while playing game in win 7.
Totally unrelated situation -- given that the Win7 drivers are totally different from Linux drivers.
> 
i searched for monitor driver updates in acer website. but couldnt find any.
is there any open source so that i can get the display in my monitor?
The only time you need monitor drivers is when you have a monitor that has embedded other hardware (such as speakers) and you need drivers for that other hardware.  In general, monitors just work.

Monitor drivers are not going to affect 3D performance in any way.  That is governed by the drivers for your video card/chipset.

---

### Post by Ethan hunt on 2011-01-18
> **Mark Phelps said:**
> Totally unrelated situation -- given that the Win7 drivers are totally different from Linux drivers.

The only time you need monitor drivers is when you have a monitor that has embedded other hardware (such as speakers) and you need drivers for that other hardware.  In general, monitors just work.

Monitor drivers are not going to affect 3D performance in any way.  That is governed by the drivers for your video card/chipset.

I am getting all the sounds of the game in my speakers, but display is "Display not supported". what to do?

---

### Post by Ethan hunt on 2011-01-18
The game is EA sports FIFA 2008

---

### Post by Ethan hunt on 2011-01-21
I am able to get the sound output. only display is the problem..
how to solve it?

---

### Post by mastablasta on 2011-01-21
you are probably running the game under WINE. if not then this might be the problem.
 
There are a couple of options. 
 
Most obvious is that poor linux drivers for this card don't allow you to play this game under linux with this card.
 
Then it could be that you need to adjust some settings or add something in WINE (check their site for support on this game) [http://appdb.winehq.org/objectManager.php?sClass=application&iId=5736](http://appdb.winehq.org/objectManager.php?sClass=application&iId=5736)
 
Or it may be that the game is not running well under wine.
 
 
IF you run it from terminal then you should get some error outputs.

---

