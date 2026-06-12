---
title: "Wine Instal ?"
date: 2011-02-04
forum: New to Ubuntu
---

### Post by MadMonkey1966 on 2011-02-04
Did not know really where to put this.....but if in doubt :)

I want to run a couple of .exe files, so done some searching & reading, and come across so many different things i am totally lost....At least i know i need Wine.

Even the first post that you must read (in the WINE Forum here) is dated 2008, and says about going to add/remove programs which does not exist in my Ubuntu version.

Anyway, being pretty new to Ubuntu, i don't want to get the installetion wrong. In the Wine Wiki it says:

"Before you install Wine, make sure that there is no previous Wine installation on your system, either from a package or from source. If you haven't yet installed Wine, you should be fine. See the Removing old Wine versions chapter in the User Guide for details. Many Linux distributions come with an included Wine package, but due to Wine's rapid development rate these are usually old and often broken versions. It is best to uninstall your distribution's included package versions and update to the latest Wine version available here."

I had a look in Ubuntu Softare Manager, and there are a couple of files in there, so the first question (and hopefully the last lol) is 

Do i have to remove these and instal the one from the Wine site ?? Or can i just go with the 2 i have already ??

Many Thanks to anyone who can give me a clear lead :P

---

### Post by davidmohammed on 2011-02-04
have a look in either software centre of synaptic manager for wine1.2

alternatively

sudo apt-get install wine1.2

have a read of [this]("https://help.ubuntu.com/community/Wine") to get you going

---

### Post by Tyggna on 2011-02-04
I'd be curious to know exactly what .exe you want to run.  In most cases, it's better to find Linux equivalent software if you can.

In other cases, Wine will work some of the time.  I believe Ubuntu does come with wine.  You can check by going to a terminal (accessories list I believe) and typing "wine"

If you get a message saying it's not installed, it'll tell you what you need to type to install it.  The proper usage for wine is:

wine program.exe [additional arguments]

It also works with .msi files

---

### Post by MadMonkey1966 on 2011-02-04
Hey, Thanks again my friend....you must have been knowing i was about to post again lol

Will have a go :)

---

### Post by MadMonkey1966 on 2011-02-04
The main one is an obscure board game. I have searched for a Ubuntu version, but no joy.

Will see how i get on, thanks

---

### Post by MadMonkey1966 on 2011-02-04
> **davidmohammed said:**
> have a look in either software centre of synaptic manager for wine1.2

alternatively

sudo apt-get install wine1.2

have a read of [this]("https://help.ubuntu.com/community/Wine") to get you going
Thanks David, i installed the one that was in Software Centre. Located the .exe file to download, when i clicked it, it even said open with Wine, and it downloaded and run properly (after i had been into the .exe properties and ticked the little box allowing to run as an application).

I think someone should update the Wine forum :)

Great stuff, have not had one major problem really. Still have that Flash crashing, but it is only on one game.

Take care
Ian

---

