---
title: "Compiz Animations"
date: 2009-09-14
forum: New to Ubuntu
---

### Post by Captainflowers91 on 2009-09-14
Help! I have the compizconfig menu. Anyway, I want to configure the animations for when I close a window, or open one, etc. Anyway, nothing I've tried works and I've looked everywhere

---

### Post by jualin on 2009-09-14
You need to open Compiz Config Manager and go to the Animations tab. In there you just need to go to the tab you want (Open Window Animation) and edit the effects from there. Good luck! 
P.S. This is assuming that you have Compiz enabled. You can check by going to System, Preferences, Appearance and then Visual Effects.

---

### Post by Captainflowers91 on 2009-09-14
yea, I know how to get that far, but when I get there how to I actually set the animations? I've tried everything and nothing works

---

### Post by Excedio on 2009-09-14
Does your Compiz Config look something like the 1st picture attached below?

If it does, try this
```
sudo apt-get simple-ccsm
```
Open the newly downloaded program and click on the Animations tab. Try setting the Animations from there. Program looks like the 2nd attachment.

---

### Post by ankspo71 on 2009-09-14
In compiz config, Enable desktop cube effects by enabling the following:

1 Desktop Cube.
2 Rotate Cube.
3 Cube Reflection and Deformation.
(you can tweak the settings later)

Next make sure you have about 4 workspaces in your panel.
(those were the 2-4 square boxes in the bottom of your ubuntu screen).

Next, try to rotate the cube by clicking on those workspaces (boxes).

The default hot keys to active the cube are:
ctrl + alt + arrow keys
----

For window, menu, and panel effects, enable the following:
1 Animations
2 Animations Addon. 
(you can tweak the settings later too)

Like the others have said, be sure to have the 'compiz' 3D effects enabled or else it won't do anything.

Btw, for the record, it took me a while to get used to using compiz config. 

Hope this helps.
James

---

### Post by Captainflowers91 on 2009-09-14
Ok, so I've followed all the instructions. Anyway, nothing has worked! The problem is in the set-up. I've used close options under animations for the experimental one until I figure out what to do. Anyway, I noticed that on all the other effect tabs, theres a line labeled Window Match. On all the standard ones I haven't messed with, theres a line of info, but I deleted the basic ones set with "Close Options" I think thats where the trouble is. Anyway thanks to everyone who answered so far. Your probably right, I'm just a noob :(

---

### Post by ankspo71 on 2009-09-14
> **Captainflowers91 said:**
> Your probably right, I'm just a noob :(

I didn't mean it like that... I just meant that the compiz configuration manager is not so user friendly. I still consider myself a noob too.

Anyways, if you click on the "preferences" button in compiz configuration manager, you will see a "reset to defaults" button towards the right. Click on that to restore the compiz to the original settings. Then you could go ahead and try it again.
James.

---

### Post by ankspo71 on 2009-09-14
Here you go,

I am uploading my compiz profile for you. It is in the attachment. Before you can use it, you have to rename it by removing .txt at the end.... so that the name says "jamesextrawobblycompiz.profile" .

After you get it, and rename it, you can import it into compiz configuration manager by clicking on Preferences and then Import.

Make sure you have 4 workspaces in your gnome panel because that's how many I have configured.

I have desktop cube enabled, and a rotating type effect for opening and closing things. Also, as the name implies, the windows are extra wobbly. I think this configuration has transparency too.

I hope this helps.
James.

---

### Post by JBAlaska on 2009-09-14
By default the animations (Minimize, Close and Open) effects have three effects "Stacked", Just delete the bottom two, then highlight and edit the first one with the effect you want..

Try Burn with a duration of 100 to 150 depending on your GPU speed.

---

### Post by Captainflowers91 on 2009-09-14
Yea, thats what I've tried. Like I said, theres what looks like a line of code that I need to input to get the selected animations to work, but I have no idea how or where to get this code. Its right beside the ones that are already installed

---

### Post by steveneddy on 2009-09-14
All I do is check the boxes.

I think you are making it too hard.

Please post a screen shot of what you are looking at.

I posted two screen shots of CCSM (Compiz Config Settings Manager)

---

### Post by K7522 on 2009-09-14
> **steveneddy said:**
> I think you are making it too hard.
I think he's talking about the Window Match box.

That line tells the program which types of windows are treated with the animation. The default for 'Minimize Action' is as follows:

```

Window Match: (type=Normal | Dialog | ModalDialog | Unknown)
Options: <BLANK>
```

You can just use the ones that were on the default animations if you dont understand how to use it.

---

### Post by steveneddy on 2009-09-14
> **K7522 said:**
> [COLOR=Red]**I think he's talking about the Window Match box.**[/COLOR]

You can just use the ones that were on the default animations if you don't understand how to use it.

I'm sorry, I misunderstood.
[B]
I agree that he should [COLOR=Blue]just use the defaults[/COLOR] at the moment.[/B]

List of windows available for that variable:

> unknown, combo, desktop, dialog, dnd, dock, dropdownmenu, fullscreen, modaldialog, menu, normal, notification, popupmenu, splash, toolbar, tooltip, utility

From this web page:

[http://wiki.compiz-fusion.org/WindowMatching](http://wiki.compiz-fusion.org/WindowMatching)

---

