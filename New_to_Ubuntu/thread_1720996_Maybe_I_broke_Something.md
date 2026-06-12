---
title: "Maybe I broke Something"
date: 2011-04-03
forum: New to Ubuntu
---

### Post by windowsdown on 2011-04-03
background info: 
i have this asus eee pc 1005 netbook that shipped with win 7 starter. i imaged it, formatted it, and installed ubuntu 10.10 on it with the intent of attempting opensusu, openbsd, and win 7 (yeah, i know, but might as well know, huh?) in virtualbox.  i couldn't make the add-on dvd drive operate, so i went to the site and found a netbook remix edition of ubuntu.

first thing i noticed after installing the netbook remix is the absent menu bar (applications, places, system, etc.) and a button bar on the left side that looks like an attempt at integrating the ubuntu menu bar into something more windows-y.

all that is fine except that i have been working for a week trying to find out how to put icons on the desktop.  sounds stupid, right? i thought so, but apparently my right-click functionality has been taken hostage.  i have been on the forums and attempted the following with the indicated results.


[LIST]
[*]right-click on the desktop and/or the application shortcut --> no response.
[/LIST]

[LIST]
[*]sudo apt-get update and sudo apt-get upgrade just to update everything --> it did its job, but didn't do anything to help mine
[/LIST]

[LIST]
[*]gconf-editor --> nothing applicable stuck out (although i did find it nice to be able to move the window control buttons back to the right-hand side of the window)
[/LIST]

[LIST]
[*]alt+F2 --> no response
[/LIST]

[LIST]
[*]system preferences, as suggested by the official ubuntu documentation --> nothing there
[*]forum surfing --> i found a similar thread in xubuntu (unsolved, though); figured this didn't meet that criteria
[/LIST]
sooo....here i am, hoping someone can help me identify that one small thing that i must have overlooked. as -- ahem -- pretty as the button bar is, i would much rather have access to the menu bar and a couple of desktop icons.

thanks in advance.

---

### Post by idoitprone on 2011-04-03
First, Ubuntu 10.10 netbook edition have an unity interface, so the missing menus are a feature of gnome 2.x. This is normal. I am not sure of the status of the alt-f2 or run command, since i heard ubuntu broke it. I guess you also hate the Unity interface.

If you want the classic gnome get the desktop edition. Also avoid natty. 

Second, Please dont bother with virtual box. I tried it once and the atom cpu do not virtualize well. Btw never try opensuse in a virtual enviroment, since i heard it is little crippled unlike Ubuntu which runs very well

---

### Post by Paqman on 2011-04-03
> **windowsdown said:**
> 
[LIST]
[*]right-click on the desktop and/or the application shortcut --> no response.
[/LIST]


You don't really have a "desktop" that you can add things to in the netbook edition's Unity interface. If you want to add a launcher, add it to the bar.

> 
[LIST]
[*]alt+F2 --> no response
[/LIST]


This doesn't work in the Maverick version of Unity, but will in Natty.

> 
as -- ahem -- pretty as the button bar is, i would much rather have access to the menu bar and a couple of desktop icons.


No problem. To switch to the default Gnome interface you'll need to log out, click your user name and pick "Gnome" from the session menu at the bottom of the screen.

I agree with idoitprone about virtualisation. Atom CPUs don't have virtualisation features built into them, and the CPU's speed and the amount of RAM in an Eee PC are way below what you need to run VMs. If you want alternative OSes I suggest your dual- or multi-boot.

---

### Post by windowsdown on 2011-04-04
thanks all for the responses.  i have learned quite a bit today.  i now know what 'unity' is, as well as why the opensuse vm didn't cooperate within the vm.  i fully expect windows to be uncooperative as well, specifically 7; possibly xp.  looking to do something just to say i did it. and to migrate e-mail without touching two pc's (silly enough when my backups are on an external device as we speak). 

eh well. at least i was able to justify maxing the ram. :)

---

