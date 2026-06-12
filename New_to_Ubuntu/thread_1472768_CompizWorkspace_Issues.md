---
title: "Compiz/Workspace Issues"
date: 2010-05-04
forum: New to Ubuntu
---

### Post by beegary on 2010-05-04
Im having a couple of issues since installing 10.04:


[LIST]
[*]Please see attached screenshot. I have 3 workspaces shown in the bottom right. In my 9.10 install I could switch between them by pressing Ctrl-ALt-Rht, or click one of the icons. Neither now work.
[*]I have enable the desktop cube, but cannot seem to get it working, I thought I had to press both mouse buttons in with ?Alt. I have tried all sorts of combinations with no success.
[*]Compiz has sooooo many options, is there a list of keyboard short cuts?
[/LIST]

I seem to have regressed. I have been using Lucid since release, beta before that, and Karmic since December but suddenly it all seems foreign to me!

---

### Post by r-senior on 2010-05-04
Nice theme! ;) I can't see your workspaces on it though.

Are you sure you are using compiz? 

System - Preferences - Appearance - Visual Effects

What's it set to?

---

### Post by beegary on 2010-05-04
> **r-senior said:**
> Nice theme! ;) I can't see your workspaces on it though.

Thanks, all Im using at the moment is Radiance, with the stock glass background. My panel colours need a bit of work. Sorry I have attached another!

> **r-senior said:**
> 
Are you sure you are using compiz? 
System - Preferences - Appearance - Visual Effects

What's it set to?

Ahhh I see my problem........that setting is currently Off. But I had set it to extra. When I turn it back to extra I have the workspace selection back. 
But when I go to System - Preferences - Appearance - CompizConfig Settings Manager and turn on the Desktop Cube - the visual effects becomes unselected (2nd screenshot)

What is the mouse/keyboard shortcut for the cube?

Thank you for your help

---

### Post by Hospadar on 2010-05-04
you probably want to install the compiz configuration manager.  It will let you change all the settings exactly the way you want and view and edit the keybindings as well

Either grab it from synaptic/software center, or in a terminal
```
sudo apt-get install compizconfig-settings-manager
```

You'll then find it in System-Preferences

---

### Post by r-senior on 2010-05-04
Default cube spin is Ctrl-Alt-Left and Ctrl-Alt-Right.

For setting up Compiz initially, I tend to use the Simple Compiz Config Settings Manager, then tweak with the complete one that Hospadar refers to. No harm in having both on there while you are playing with a theme.

$ sudo apt-get install simple-ccsm

You might also want compiz-fusion-plugins-extra if you want to use any of the extra animations, etc.

If there's a suspicion that it's not working properly, have a look here:

[http://ubuntuforums.org/showthread.php?t=799070]("http://ubuntuforums.org/showthread.php?t=799070")

---

### Post by beegary on 2010-05-04
Is what you are referring to anything to do with this screenshot?
Im confused!!!!

---

### Post by beegary on 2010-05-05
> **r-senior said:**
> Default cube spin is Ctrl-Alt-Left and Ctrl-Alt-Right.

For setting up Compiz initially, I tend to use the Simple Compiz Config Settings Manager, then tweak with the complete one that Hospadar refers to. No harm in having both on there while you are playing with a theme.

$ sudo apt-get install simple-ccsm

You might also want compiz-fusion-plugins-extra if you want to use any of the extra animations, etc.

If there's a suspicion that it's not working properly, have a look here:

[http://ubuntuforums.org/showthread.php?t=799070](http://ubuntuforums.org/showthread.php?t=799070)

I have installed simple-ccsm and the extras. Ahhh that makes compiz setup allot easier!!! So everything seems to work until I try to enable desktop cube?
I have checked out the forum post you linked and run the script, which states that all should be ok for compiz.
I must be missing something here???

---

### Post by beegary on 2010-05-05
Im not sure what I did. I was playing around with the cube settings, to sphere, back to cube etc in Simple Compiz Settings Manager..........Now it is working, Yes!

Marked as solved, thank you for your helpings

---

