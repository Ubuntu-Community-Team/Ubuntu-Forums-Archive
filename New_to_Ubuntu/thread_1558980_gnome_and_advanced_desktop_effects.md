---
title: "gnome and advanced desktop effects"
date: 2010-08-23
forum: New to Ubuntu
---

### Post by Sleven7 on 2010-08-23
I started reading the articles from this page:

[http://blog.thesilentnumber.me/2010/04/ubuntu-1004-post-install-guide-what-to.html](http://blog.thesilentnumber.me/2010/04/ubuntu-1004-post-install-guide-what-to.html)

 I installed the --->(upcoming version 3.0 of the GNOME desktop environment uses GNOME Shell)

rebooted, and see no difference, was I suppose to see a difference?

I then installed the following three:

compiz-fusion-plugins-extra
simple-ccsm
compizconfig-settings-manager

I found the two managers under system preferences but am now at a lose as what to do with them.
I clicked the 3d button and the water button, but see no difference in any of the windows.  Is there a 
tutorial for these managers somewhere that will tell me how to use them?  I don't want to just start
 pushing buttons and changing setting.  I would like to see some of the special effects but am unsure 
how to do that.  I don't mind reading how to article on how to use these features instead of taking up 
your time, if someone can kindly point me in the right direction I would greatly appreciate it, thanks.

---

### Post by Zorgoth on 2010-08-23
3D windows is a plugin that only applies when you are rotating the desktop cube I believe - it makes no other difference.

For the water effect, to see something happen you would need to not just check the box but click the icon and bind some keyboard shortcuts.  Note that the water effect is the most unproductive thing I believe ever devised for a desktop environment.

I would say the best place to start configuring compiz is probably the Animations plugin.  Enable it and the Animations Addon plugin.

Personally I am also a big fan of the "Wobbly Windows" plugin that you may be familiar with :D

Expo, Scale, Desktop Cube, Rotate Cube, and Shift/Ring switcher are some other plugins with cool effects.

I assume you ran "compiz --replace" (thus presumably losing your panel if you were working in GNOME Shell) - if you plan to use compiz in GNOME 3 you will need an alternative program launcher (Alt-F2 - an example of a good alternative would be gnome-do) and an alternative panel/dock, of which there are many.  Personally, I use cairo-dock (and no gnome-panel).  It has lots of cool effects and applets, including a detachable system tray and a quite good taskbar.

---

### Post by Nick_Jinn on 2010-08-23
You need to start messing around with Compiz settings :)

---

### Post by Sleven7 on 2010-08-23
Nick, ok I will start messing around with it :D

Zorgoth, I understood what you were saying up to this point

I assume you ran "compiz --replace" (thus presumably losing your panel  if you were working in GNOME Shell) - if you plan to use compiz in GNOME  3 you will need an alternative program launcher (Alt-F2 - an example of  a good alternative would be gnome-do) and an alternative panel/dock, of  which there are many.  Personally, I use cairo-dock (and no  gnome-panel).  It has lots of cool effects and applets, including a  detachable system tray and a quite good taskbar.

I am brand new to both Linux and Ubuntu.  Basically I'm playing and have very little idea as to what I am doing and that paragraph might as well be Greek :???:

I did not run "compiz --replace"  as the article I was reading said nothing about running that.

program launcher?
gnome do? 
panel dock?

help!  ](*,)

---

### Post by Sleven7 on 2010-08-23
ok, I ran "compiz --replace" and this is the message the terminal gave

compiz (cube) - Warn: Failed to load slide: /usr/share/gdm/themes/Human/ubuntu.png

and I lost the prompt, the curser is just sitting there in the terminal blinking with nothing before it.  When I try to x out of the terminal it says a program is still running with the option of stopping it.
and everything still looks the same on the desktop.  

Some of the features I have been able to get to work in the compiz manager just by turning them on.  This was before I ran "compiz --replace"

---

### Post by coffeecat on 2010-08-23
> **Sleven7 said:**
> this is the message the terminal gave

compiz (cube) - Warn: Failed to load slide: /usr/share/gdm/themes/Human/ubuntu.png

and I lost the prompt, the curser is just sitting there in the terminal blinking with nothing before it.  When I try to x out of the terminal it says a program is still running with the option of stopping it.
and everything still looks the same on the desktop. 

That's a feature of the way the terminal works. You issued a command and it gave you an error message which means that it couldn't finish executing the command - hence everything unchanged on the desktop. But the process was still trying to run, hence the missing prompt. What you do in such a situation (with any hung terminal command you want to abort) is to press control-C to kill the process. That will restore the prompt.

When you tried to close the terminal the program that it said was still running was the (hung) 'compiz --replace'.

HTH because you're likely to want to use the terminal again for other things. :)

---

### Post by Nick_Jinn on 2010-08-23
Compiz is in a different location in Mint, which is what I use, than in regular Ubuntu. For me its in the 'control panel' For you its under administration-preferences I think.

Make sure your video card is enabled. Go to hardware drivers and search for drivers.

---

