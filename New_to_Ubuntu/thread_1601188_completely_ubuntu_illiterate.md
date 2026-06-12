---
title: "completely ubuntu illiterate"
date: 2010-10-19
forum: New to Ubuntu
---

### Post by zombiejess on 2010-10-19
i just got ubuntu a couple of days ago. i have been using windows until now. I must say, i'm having a bit of  tough time getting used to it. Im trying to install diablo 2, so i downloaded wine using the software center, but since i'm using ubuntu 10.10 i don't have the most recent version of wine apparently. I went to the winehq website, and it tell me how to update it to the newest version, which is just going to my system>administration>advanced software but i can't even figure out how to get to that... can anyone help?? I feel like such a noob... :(

---

### Post by Bluesan on 2010-10-19
You can start learning about your new operating system here:

[http://ubuntuguide.org/wiki/Ubuntu:Maverick](http://ubuntuguide.org/wiki/Ubuntu:Maverick)

And here:

[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)

And, you might want to take a look at this too, just to get a proper perspective on Linux:

[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

Good luck, and have fun...

:)

---

### Post by anarchy404 on 2010-10-19
in a terminal, try entering

```
sudo apt-get update
```

then try going to System>Administration>Update Manager and see if wine is in there.

If all else fails, try following the instructions here [http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)

---

### Post by Zzl1xndd on 2010-10-19
I normally don't use wine myself (just stick with Native Linux games). However you might want to install Play On Linux from the Software Center, adds a nice graphical tool for installing things through wine.

I do believe the version of Wine in the Repos is fine for Diablo 2 and LOD.

---

### Post by lyall on 2010-10-19
also you can look thing up on the Ubuntu documentation site
[https://help.ubuntu.com/community/TitleIndex]("https://help.ubuntu.com/community/TitleIndex")

good luck and have fun learning

---

### Post by zombiejess on 2010-10-19
thanks fr the links! i have tomorrow off so will most likely spend the day familiarizing myself with thenew os..

> **anarchy404 said:**
> in a terminal, try entering

```
sudo apt-get update
```then try going to System>Administration>Update Manager and see if wine is in there.

If all else fails, try following the instructions here [http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)


this is all great, but i dont even know how to get to system.... i guess i should havewaited until i was more famliar with everything before trying to tackle a windows emulator... i should be able to use what i have before adding more on top of it /blush

---

### Post by ender4 on 2010-10-19
"System" refers, to the menu launcher at the upper left of your screen, you should see three menus: Applications, Places, and System.  Click on System, then click on the Administration Item, and then click on Update Manager, or whatever.

---

### Post by bigsmitty64 on 2010-10-19
**" i dont even know how to get to system"**

Assuming you have a basic Ubuntu install, "system" is on the top panel on the left side.

So you would click **system**, then a dropdown mennu appears and you find **Administration**, another dropdown menu appears, then **Update Manager**.

Hope this helps a little. :)

---

### Post by mastablasta on 2010-10-20
> **zombiejess said:**
>  
this is all great, but i dont even know how to get to system.... i guess i should havewaited until i was more famliar with everything before trying to tackle a windows emulator... i should be able to use what i have before adding more on top of it /blush
 
 
good luck. it's quite complicated. Play on linux is graphical interface for WINE. might help.
 
but i am currently battling with diablo 2 install as well. managed to install it but the thing doesn't work propperly and i can't increase/stretch the window. I will try a few other tricks and if they don't work it will be time to boot in the XP partition which i just planned to remove :(. because so far i haven't even started to tackle the lan connection in the game...
 
Gold rating? more like garbage on mine...

---

### Post by mcduck on 2010-10-20
> **zombiejess said:**
> i just got ubuntu a couple of days ago. i have been using windows until now. I must say, i'm having a bit of  tough time getting used to it. Im trying to install diablo 2, so i downloaded wine using the software center, but since i'm using ubuntu 10.10 i don't have the most recent version of wine apparently. I went to the winehq website, and it tell me how to update it to the newest version, which is just going to my system>administration>advanced software but i can't even figure out how to get to that... can anyone help?? I feel like such a noob... :(

If you downloaded Wine from the software center, then you already have the latest version available from Ubuntu's software sources. :)

You'll probably find some PPA repository with more up-to-date versions available, but you probably should just forget about that for now and try getting a bit more familiar with Ubuntu first..

---

### Post by zombiejess on 2010-10-20
> **bigsmitty64 said:**
> **" i dont even know how to get to system"**

Assuming you have a basic Ubuntu install, "system" is on the top panel on the left side.

So you would click **system**, then a dropdown mennu appears and you find **Administration**, another dropdown menu appears, then **Update Manager**.

Hope this helps a little. :)


im guessing i dont have the basic install then... i have a bunch of icons on the left hand side of my screen, some of which are the software center, a music player, workspaces, etc... but no system icon.

---

### Post by JKyleOKC on 2010-10-20
Do you have a panel (think taskbar) across the top of your screen? If you do, that's where you'll find System, rather than on the desktop itself.

I'm using Xubuntu, which has a different window manager and so has a slightly different layout, but operates in much the same way. Ubuntu has a number of different ways to install: Ubuntu itself uses the Gnome desktop environment, Kubuntu uses KDE instead of Gnome, Xubuntu uses XFCE, and there are a number of others. All are essentially the same under the hood, however.

You'll find the differences between Linux and Windows confusing for a while, but once you become more familiar with the Linux way of doing things you'll probably prefer it -- at least that's what most of us here have experienced. The trick is to be aware of the differences, and ask about anything that you find confusing. The only stupid questions are those that are never asked!

Welcome to the party!

---

### Post by zombiejess on 2010-10-20
i actually dont have a panel across the top of my screen... just the one to the right of it and system is no where to be seen on that one.

---

### Post by ubudog on 2010-10-20
Play on Linux is a great piece of software, and I think it actually has Diablo in it's software list.  Good luck and welcome to Ubuntu!

---

### Post by mcduck on 2010-10-21
> **zombiejess said:**
> im guessing i dont have the basic install then... i have a bunch of icons on the left hand side of my screen, some of which are the software center, a music player, workspaces, etc... but no system icon.

So you are actually running the Netbook version of Ubuntu? Might have been easier to help you had you said so in your first post. :)

No, there is no System menu on UNE. Just go though your applications and you'll find "Preferences" (or whatever it was called), it contains all the same things that would be in the System menu on a desktop Ubuntu install. (Can't check the exact name in the icon you use on UNE to access your system options, but it should be pretty obvious, "preferences", "control panel" or something like that.)

---

