---
title: "Another person with WINE problems?  Newbie!"
date: 2009-12-03
forum: New to Ubuntu
---

### Post by Malt Frisky on 2009-12-03
Hi there.

This is my first question on the Ubuntu forms, so be gentle :confused:

I coverted to Linux a few months ago and love it.  However, I am a solid gamer and having problems with a few things in WINE, so I'm wondering if anyone could provide a solution and some help :D

From what I can tell, I've downloaded WINE successfully and the games install but do not run.

I'll give a few examples of games I've tried to get up and running.

Peggle:  Placed games in folder and right clicked Peggle Nights Deluxe.exe and clicked on Open with Wine Windows Program Loader.  Installed game.  Then tried to open up game and got the following message 'Invalid Command Line Parameter C:\program files\peggle nights deluxe\pegglenights.exe.

World of Goo: Same as above, tried to open and got 'An unexpected error has occured'

Curse of Monkey Island: Again, same as above, this time it successfuls loads but the sound is very dodgy, sort of an underwater effect, then cutting out.

I'm very new to Linux, so any ideas what I'm doing wrong are much appriciated and welcome.

Thanks

---

### Post by Cheesemill on 2009-12-03
I can't help with wine but did you know there's a native Linux version of World of Goo.

---

### Post by themusicalduck on 2009-12-03
Wine isn't guaranteed to work with every windows game, but a good place to check to see if something might work is here - [http://appdb.winehq.org/](http://appdb.winehq.org/) There are usually tips to get things to work on there too. It looks like both peggle and monkey island might work.

How are you trying to run peggle? from the menus?

Also there is a native version of world of goo, but not sure if you can get a copy of it without repaying for it.. especially if you got it from steam.

---

### Post by Malt Frisky on 2009-12-03
> **themusicalduck said:**
> Wine isn't guaranteed to work with every windows game, but a good place to check to see if something might work is here - [http://appdb.winehq.org/](http://appdb.winehq.org/) There are usually tips to get things to work on there too. It looks like both peggle and monkey island might work.

How are you trying to run peggle? from the menus?

Also there is a native version of world of goo, but not sure if you can get a copy of it without repaying for it.. especially if you got it from steam.


Cool, I've used the following link and it's really good to find new games that work with Linux that you cna check with... BOOKMARKED :p

Though I'm still having problems, I've tried a few more links from the web site and it's failing to make a link.  I think it might be with the WINE program itself, I don't know wether I have to change prefrences or there something else I'm missing?

---

### Post by marshmallow1304 on 2009-12-03
I can confirm that if you purchased World of Goo from the 2DBoy website (not Steam), you will be able to download any version.  You'll just have to find the download link in the confirmation email.

---

### Post by ed-koala on 2009-12-03
Did you install Peggle, or did you just copy everything and then try to run the exe file?

I'm not familiar with the game so I don't know if it has a setup.exe or not. If it does, it needs to be installed using Wine first.  Then comes running it.

Are you using the menu entry? Or are you navigating to the directory and trying to run the game file directly?

---

### Post by Malt Frisky on 2009-12-03
Once I've downloaded the game, I place it in a folder in my file manager and start the set-up by right clicking and opening with Wine Windows Loader Program (these are all .exe files).

Once I've completed the set-up (e.g. Peggle) I go to Application/Wine/Programs/Peggle/Peggle and open it up.

Aside from Curse of Monkey Island (where I'm getting sound problems), all the rest of my games don't work.  Peggle message gave me 'Invalid Line Command Parameter' and World of Goo gave me 'An unexpected error has occured'.

I've also tried a few other games and get pretty much the same messages, I think it might be with something in WINE preferences but I've got no idea.

---

### Post by beastrace91 on 2009-12-03
What Wine version are you using? (Run **wine --version** in terminal if you are unsure)

The latest beta is 1.1.33 - Wine updates fix many issues most times be sure you are running the latest version :)

EDIT: I'm willing to bet you are running the "stable" version of Wine 1.0.1 - because all three of the games you listed are Plat/Gold rated on the Wine AppDB using later version of Wine.

[World of Goo](http://appdb.winehq.org/objectManager.php?sClass=version&iId=15322)
[Peggle Nights](http://appdb.winehq.org/objectManager.php?sClass=version&iId=14215)
[Curse of Monkey Island](http://appdb.winehq.org/objectManager.php?sClass=version&iId=169)

Regards,
~Jeff

---

### Post by beastrace91 on 2009-12-03
> **ed-koala said:**
> I'm not familiar with the game so I don't know if it has a setup.exe or not. If it does, it needs to be installed using Wine first.  Then comes running it.

This is not always the case. For instance my Steam games are copied right over from a Windows install and run 100% fine under Wine.

~Jeff

---

### Post by sandyd on 2009-12-03
first, run this
```

gksudo gedit /etc/apt/sources.list

```add this to the bottom (on a new line)
```

deb http://wine.budgetdedicated.com/apt karmic main

```save and close.
then run this
```

sudo apt-get update
sudo apt-get upgrade
cd /usr/bin
sudo wget -c [http://winezeug.googlecode.com/svn/trunk/winetricks](http://winezeug.googlecode.com/svn/trunk/winetricks)
sudo chmod 777 winetricks
winetricks allfonts fontfix fontsmooth-rgb droid flash allcodecs directx9 gdiplus gecko volnum msxml3 msxml6
winecfg

```
go to the audio tab, wait a while, then make sure ONLY alsa is selected.
Then go to the "About" tab
enter in your name

that **should be it.

---

### Post by beastrace91 on 2009-12-04
> **carlee said:**
> first, run this
```

gksudo gedit /etc/apt/sources.list

```add this to the bottom (on a new line)
```

deb http://wine.budgetdedicated.com/apt karmic main

```save and close.
then run this
```

sudo apt-get update
sudo apt-get upgrade
cd /usr/bin
sudo wget -c [http://winezeug.googlecode.com/svn/trunk/winetricks](http://winezeug.googlecode.com/svn/trunk/winetricks)
sudo chmod 777 winetricks
winetricks allfonts fontfix fontsmooth-rgb droid flash allcodecs directx9 gdiplus gecko volnum msxml3 msxml6
winecfg

```
go to the audio tab, wait a while, then make sure ONLY alsa is selected.
Then go to the "About" tab
enter in your name

that **should be it.

While those are good suggestions - why are you recommending installing all those extra things through Winetricks? Typically less is more in the Winetricks area I've found, some of the packages (allfonts and allcodecs for example) are always fine to have - however other ones (like directx9) can cause issues for some...

idk, just my 2pence - personally I'd see if just updating the Wine version works before doing all the Winetricks.

~Jeff

---

### Post by ed-koala on 2009-12-04
Also, be forewarned that winetricks cannot be undone, or so I've read. So I'm very wary of doing any winetricks I don't absolutely have to do.

I'm waiting to hear what Wine version he is running myself, as this could easily be the problem.

As far as sound issues, another thing to try is installing pulseaudio-utilities from Synaptic, setting Wine audio to OSS, and starting Wine apps with padsp wine <program>.

I also made a HOWTO here [http://ubuntuforums.org/showthread.php?t=1340643]("http://ubuntuforums.org/showthread.php?t=1340643") on creating Desktop launchers for Wine programs, if you like having those.

---

### Post by Malt Frisky on 2009-12-04
Okay, I've upgraded to 1.1.33.

The audio is now working on Monkey Island YAY :D but now it's completely black :confused:

So I'm sort of making progress.

However, I still can load peggle up or World of Goo.  Peggles error messages is 'Failed to initialize DirectDraw: RESULT_SURFACE_FAIL CreateSurface Fullscreen Primary: 8876086c'
and World of Goo's error message is 

An unexpected error has occured!

Exception: Access Violation (code 0xc0000005) at address 004E0F13 in thread 30
Module: WorldOfGoo.exe
Logical Address: 0001:000DFF13

0033ED3C 004E0F13 0001:000DFF13 WorldOfGoo.exe
Params: AAE2B970 0033FB7C 0033F720 0000002F

0033F630 004E0A33 0001:000DFA33 WorldOfGoo.exe
Params: 7B8B4FF4 0033F6BC 7B844293 0033F720

(followed by anothe box)

The program WorldOfGoo.exe has encountered a serious problem and needs to close.

This can be caused by a problem in the program or a deficiency in Wine.  You may want to check [http://appdb.winehq.org](http://appdb.winehq.org) for tips about running this application.


So, I'm still pretty scoobied about what to do?  I also inputed the info in terminal that Carlee game me, but nothing different seems to have occurred.

---

### Post by sandyd on 2009-12-05
im just curious. does the demo even work?
if it does, i will guess that its something wrong with the version that you have...
```

wget -c [http://worldofgoo.com/dl2.php?lk=demo&filename=WorldOfGooDemo.1.0.exe](http://worldofgoo.com/dl2.php?lk=demo&filename=WorldOfGooDemo.1.0.exe)
wine WorldOfGooDemo.1.0.exe

```

---

### Post by sandyd on 2009-12-05
and i also found this
[http://2dboy.com/forum/index.php?topic=1321.0](http://2dboy.com/forum/index.php?topic=1321.0)

---

### Post by Malt Frisky on 2009-12-08
Hey

Okay, I've been downloading from various sites, tried the demos and installed various updates added by Ununtu Update Manager.

Still nothing, still running into the exact same problems that I posted in the previous post.

Are there any ideas on how to solve the black screen problem with Curse of Monkey Island?

All help has been very much appriciated and I thank the time people have taken to answer my plea. ;)

Jonny

---

