---
title: "If I am not using Gnome then how do I ....."
date: 2009-09-21
forum: New to Ubuntu
---

### Post by harisund on 2009-09-21
So Gnome uses too much memory and I am contemplating a lighter replacement (and no, LightWeightBuntu is not for me). 

So I install Ubuntu 9.04 and let's say remove the gdm service and decide to use startx with a ~/.xinitrc file that says "startfluxbox" or "icewm" or something like that. 

It's only after trying to get away from Gnome that I realize there are lots of things that I take for granted. I would like to find command line equivalents (such as MC instead of Nautilus, for starters) 

I am guessing for applets like system manager, CPU speed, date, time, temp I can use conky. 

1. How do I change volume with a barebones window manager? 
2. Change screen brightness? 
3. Network Manager's command line replacement? 
4. Use command line to change screen resolution and set monitor settings when connected to external monitor (such as mirror screen, extend screen, turn one screen off etc etc)
5. Printing panel

I think just about for everything else I know the command line equivalents or can handle it without the gnome-panel's applets and menus.

---

### Post by dagoth_pie on 2009-09-21
Any reason you aren't just using Xubuntu or Fluxbuntu?

---

### Post by Maravilha on 2009-09-21
Thats right, both Xubuntu and Fluxbuntu run quite a lot quicker than regular installation of Ubuntu with Gnome. 

I tried it on my netbook and was really surprised with the results.

---

### Post by renkinjutsu on 2009-09-21
> 1.
How do I change volume with a barebones window manager? 
2. Change screen brightness? 
3. Network Manager's command line replacement? 
4. Use command line to change screen resolution and set monitor settings when connected to external monitor (such as mirror screen, extend screen, turn one screen off etc etc)
5. Printing panel


if you have nvidia drivers, it comes with a GUI display properties manager anyway.. so you can set brightness, resolution or twinview/xinerama there, otherwise, search for tutorials on how to edit your xorg.conf file, it shouldn't be too hard

as for networking, you also shouldn't have a problem unless you need to set up wireless.. You should be able to set up networking from the terminal, though i put my settings into an rc file
look up the man pages for ifconfig and route (or you can use the DHCP service.. i think you have to install dhcpd or something.. not sure)

for printing, can't you stick with CUPS?

---

### Post by harisund on 2009-09-21
> **dagoth_pie said:**
> Any reason you aren't just using Xubuntu or Fluxbuntu?

Basically bloat and lack of support. 

First, Xubuntu is just Ubuntu with XFCE, it does not really have that much less memory footprint that Ubuntu / Gnome has. It's like people start developing their own LowMemoryBuntu and then go "ooh this feature is awesome, let's add it" and "ooh that feature is awesome, let's add it". And eventually it's just about as bloated with features that the developers think is good for the user, and it might be too. Let's face it, Xubuntu is no Puppy or DSL or whatever, but it's not really a good solution. 

Second, support. I hang out much more in the IRC channel than here, and if I say I am not using Ubuntu, it appears as if I have voided the warranty or something. They ask me to go to the relevant channel, and nobody is in the relevant channel ever. Also, almost every piece of support on the web etc are for Ubuntu (such as repos etc.) Take [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683) or something. Everything only works on Ubuntu, the repos are customized for Ubuntu and so on. 

So yeah .. that's why I prefer "installing Ubuntu" and then customizing it so I can still have the high memory Ubuntu when I want it but low memory Ubuntu whenever I need that too.

---

### Post by ATL™ on 2009-09-21
have you ever looked at CrunchBang? they also have a "lite" version. [http://crunchbanglinux.org/](http://crunchbanglinux.org/)

---

