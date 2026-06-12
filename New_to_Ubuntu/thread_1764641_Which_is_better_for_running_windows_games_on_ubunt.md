---
title: "Which is better for running windows games on ubuntu?"
date: 2011-05-22
forum: New to Ubuntu
---

### Post by cyanide0007 on 2011-05-22
I just installed natty last week and am very much new too linux(ubuntu).
i want to run COUNTER STRIKE and GTA 3 as well as GARENA on UBUNTU,i searched for applications which can run windows programs on linux. I found WINE, CROSSOVER LINUX, PLAYONLINUX and others but i cant open COUNTER STRIKE using WINE so i uninstalled it,,,,,,,


Now am too much confused whether to go for PLAYONLINUX or CROSSOVERLINUX... and some of the articles do say WINE is better for running win APPs.. but i can't run COUNTER STRIKE 1.6 and even GARENA is not opening 





SO plz help me!!!!!!!!!!!!!!!!!!!!

---

### Post by robro on 2011-05-22
Couple things might be the problem:
1. You didn't mark the games installers as executable (right click the game, properties, permissions and tick "Allow executing file as program")
2. The game is not supported, to find out go to: [http://appdb.winehq.org/](http://appdb.winehq.org/) and search the games to see if they are supported

hope this helps :)

---

### Post by Cope57 on 2011-05-22
Why not just run your Windows games in Windows?

Did you create a dual boot system, or did you wipe Windows from your PC?  If you only have Linux on your PC, what was the purpose for getting rid of Windows?

For future reference, you should have asked about how to dual boot your system, so you can still have the functionality of your Windows games.  You could also look into games that are native to Linux, and play quite well.

CounterStrike is a good game, but have you looked at other Linux First Person Shooters?

The list of available first person shooters is actually pretty big, I only included the ones that I have installed and play frequently.
Take a look at these:
[LIST]
[*][AssaultCube]("http://assault.cubers.net/")
[*][Alien Arena]("http://red.planetarena.org/")
[*][BZFlag]("http://bzflag.org/")
[*][Cube 2: Sauerbraten]("http://sauerbraten.org/")
[*][Nexuiz]("http://www.nexuiz.com")
[*][Open Arena]("http://openarena.ws")
[*][Tremulous]("http://tremulous.net/")
[*][True Combat: Elite]("http://www.truecombatelite.com/")
[*][Urban Terror]("http://www.urbanterror.info")
[*][Warsow]("http://www.warsow.net/")
[*][Wolenstein: Enemy Territory]("http://www.splashdamage.com/wolfet")
[/LIST]


As for GTA 3, I do not know what to tell you.  I have but a couple racing type games, but they are not like GTA 3.

[LIST]
[*][Armegetron Advanced]("http://www.armagetronad.net/")
[*][Extreme Tux Racer]("http://extremetuxracer.com/")
[*][Trigger]("http://trigger-rally.sourceforge.net/")
[/LIST]


[Garena supports Windows operating system only at the moment.]("http://support.garena.com/")

---

### Post by cayphed on 2011-05-22
I just installed PLAYONLINUX from the software store, it's basically a "easy to use" front-end to wine, which is supposed to configure wine to the application in it's list. (requires install cd/file/ect to install programs)
I haven't played arround with it too much (my little lappy isn't a gaming machine) but I did get it to install
Assasins Creed (number 1) without a hitch by following the promts and it works fine.
It did take a while to install it however.... But I expected the lag with my laptop to begin with.

Hope that helps.

P.S: I'm new to forums and I cant find how to start a thread... Sad I know, but any tips will be great.

---

### Post by cyanide0007 on 2011-05-22
> **Cope57 said:**
> Why not just run your Windows games in Windows?

Did you create a dual boot system, or did you wipe Windows from your PC?  If you only have Linux on your PC, what was the purpose for getting rid of Windows?

For future reference, you should have asked about how to dual boot your system, so you can still have the functionality of your Windows games.  You could also look into games that are native to Linux, and play quite well.

CounterStrike is a good game, but have you looked at other Linux First Person Shooters?

The list of available first person shooters is actually pretty big, I only included the ones that I have installed and play frequently.
Take a look at these:
[LIST]
[*][AssaultCube]("http://assault.cubers.net/")
[*][Alien Arena]("http://red.planetarena.org/")
[*][BZFlag]("http://bzflag.org/")
[*][Cube 2: Sauerbraten]("http://sauerbraten.org/")
[*][Nexuiz]("http://www.nexuiz.com")
[*][Open Arena]("http://openarena.ws")
[*][Tremulous]("http://tremulous.net/")
[*][True Combat: Elite]("http://www.truecombatelite.com/")
[*][Urban Terror]("http://www.urbanterror.info")
[*][Warsow]("http://www.warsow.net/")
[*][Wolenstein: Enemy Territory]("http://www.splashdamage.com/wolfet")
[/LIST]


As for GTA 3, I do not know what to tell you.  I have but a couple racing type games, but they are not like GTA 3.

[LIST]
[*][Armegetron Advanced]("http://www.armagetronad.net/")
[*][Extreme Tux Racer]("http://extremetuxracer.com/")
[*][Trigger]("http://trigger-rally.sourceforge.net/")
[/LIST]


[Garena supports Windows operating system only at the moment.]("http://support.garena.com/")






No am having DUAL boot system.. But i want to try ubuntu as a primary OS , soon am wiping my windows out of my system, for that i want to know whether all my windows games play in UBUNTU or nor. THANKS for your [SIZE=2]Suggestion[/SIZE]

---

### Post by 3rdalbum on 2011-05-22
Playonlinux is a program that helps set up Wine for specific programs. You haven't mentioned what problem you're having with using Wine directly, but I suspect it's what robro (post #2) suggested - however, if you're trying to install a program from CD his instruction won't work.

To use Wine directly, open up a terminal (click on the Ubuntu logo and type 'terminal' then choose the first item that comes up). Type the word 'wine' with a space at the end. Drag the .exe file to the terminal window. Click on the terminal window to bring it forward again and press Enter.

However, Wine is not perfect and will not run every Windows program. Especially not games. If you still want to play games, you'll need a dual-boot system OR a dedicated games console like an Xbox 360 or PS3.

Crossover is similar to the combination of Wine + Playonlinux, but with a slightly more advanced version of Wine. It might be worth a try.

---

### Post by Paqman on 2011-05-22
> **Cope57 said:**
> Why not just run your Windows games in Windows?


This is by far the easiest thing to do. Wine is very hit-and-miss, and you might need to put in quite a lot of effort fiddling about with it to get things to work. I've always found PlayonLinux to be pretty good, but i've not used Crossover.

Tbh, if something doesn't work perfectly first time with Wine I can't be bothered to fiddle about with it, I just boot into Windows and install it there. Who really cares what OS is running the game as long as it works?

---

### Post by Anuovis on 2011-05-22
A short answer would be... nobody knows whether they'd run on Ubuntu.

It depends on your hardware somewhat, especially your video card. Some are supported rather poorly when it comes to 3D graphics.

The compatibility programs exist but there is no guarantee they'd run the game. You have to try and see for yourself, really. Another option would be to emulate the Windows OS inside of Ubuntu via VirtualBox but that would eat up quite a bit of your machine's resources.

Possible solutions:

1. Moving to Ubuntu can be a good chance to cut down on gaming and do something more fun :) 

2. Check Wine app database on the web, it will give you a rough estimation how likely the game is to run and maybe a few solutions how to fix the problems. Try your particular games on Wine. If not, try installing them through PlayOnLinux. It's the same Wine really, just comes with pre-configured settings for a number of games making them easier to run.

3. Try other compatibility programs. As I never used them, can't really say how better or worse they are compared to Wine.

3. If you have a powerful PC and the games are fairly old, try emulating Windows OS within Ubuntu. VirtualBox is a good tool for that. Note, however, that this will not fix any hardware problems since everything would still be ran by Ubuntu drivers.

4. If nothing else works and you really need the games, go for dual-boot. Ubuntu is good for a lot of things but not for gaming, simply because very few of them are released for this OS. It's a surprise some Windows games works there at all.

---

### Post by 3rdalbum on 2011-05-22
> **Anuovis said:**
> 
3. If you have a powerful PC and the games are fairly old, try emulating Windows OS within Ubuntu.

By "fairly old", you'd really mean "2D and requires no 3D acceleration". Virtualbox's 3D acceleration is useless for gaming.

---

### Post by hakermania on 2011-05-22
Well,  just to mention that i have a friend whose ubuntu run better GTA than his windows in the same pc :P

---

### Post by Paqman on 2011-05-22
> **3rdalbum said:**
> By "fairly old", you'd really mean "2D and requires no 3D acceleration". Virtualbox's 3D acceleration is useless for gaming.

It is improving. It's now got to the point where I can run some older 3D games (eg: Shogun: Total War). That's a pretty early 3D game though.

Overall though, yes, Vbox sucks for gaming. Games need to run as close to the metal as possible.

---

### Post by lmn. on 2011-05-22
I tried pretty much everything to get cs:s running on ubuntu, it's pretty much a lost cause.. even with a radeon 5770 and a phenom x4

install windows [img]http://baa.nu/6q[/img]

---

### Post by Lateralis on 2011-05-22
There is really only one resource that I use for this sort of stuff: [WineHQ]("http://www.winehq.org/").  According to the site, [Counter Strike: Source]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=3731") works well under Wine, as does [GTA 3]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=1230") and [Garena 3]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=14147").  If you follow some of the tips and instructions in these links you should be able to get them working OK.  

But as someone else pointed out, gaming in Linux is very much dependent on your hardware, specifically the graphics card.  What works for someone might not work for someone else, so a certain amount of trial and error is required.  

As for Crossover, the developers, Codeweavers, are the corporate backers of Wine.  Crossover makes use of Wine but with updated libraries and comes with a very useful GUI for managing, maintaining, updating, packaging and backing up your software bottles.  It also comes with the ability to easily add extra/necessary MS distributables, utilities and libraries.  The website says that [GTA3]("http://www.codeweavers.com/compatibility/browse/name/?app_id=2741"), [Counter Strike]("http://www.codeweavers.com/compatibility/browse/name/?app_id=2035") and [Garena]("http://www.codeweavers.com/compatibility/browse/name/?app_id=5795") all work well under Crossover.  You can also search the site to check for compatibility of other programs that you might need to use.

---

### Post by Fedz on 2011-05-22
Might be worth noting that anything that doesn't run within Linux maybe you could also email or form-mail from developers website & politely 'complain' ... you never know for future releases :)

---

### Post by muteXe on 2011-05-22
I agree with everyone who's said dual-boot.  Honestly this will be less hassle for someone who plays as many games as you do.

---

### Post by Sunfist on 2011-05-22
I do have a dual boot but I was hoping to get at least a few of my favorite games to run under Linux, installed crossover and as it says it is a supported game, installed Rift. Installation was easy as could be (long but easy). And it DOES play pretty much exactly as it does under windows...with one major exception..my fps went from 40 to 10. I am sure I could convince Ubuntu to install a newer graphics driver and that might improve that figure a bit, but in my case I said, why bother, go back to playing it under windows as it was 'meant' to be played. They keep improving wine and I have the feeling they may one day get it to the point that it will play games nearly as well as a true windows system, but its not quite there yet.

---

### Post by cayphed on 2011-05-22
That sounds like a driver issue, try this page [https://help.ubuntu.com/community/Cedega](https://help.ubuntu.com/community/Cedega), it's mostly info on a drivative of wine but Cedega is designed for game use hence the additional driver info.

@Cyanide0007 try this page, [https://help.ubuntu.com/community/WindowsGames](https://help.ubuntu.com/community/WindowsGames) or the one above.

---

### Post by Joe_Dude on 2011-05-24
I am having a problem running an executable file. I try to set the program to run as a program but when I click the check box it just unchecks itself a second or two later. I chose for the program to open with wine but when it opens it tells me that I need to set it to run as a program... which I cannot do. What do?


Actually it won't let me change any of the permissions.

---

### Post by Paqman on 2011-05-24
> **Joe_Dude said:**
> 
Actually it won't let me change any of the permissions.

Is the file on a CD? If so either copy it to your hard drive and change the executable bit, or open it on the CD by right clicking on it > open with other application > use a custom command > wine.

---

