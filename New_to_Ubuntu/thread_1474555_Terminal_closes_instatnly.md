---
title: "Terminal closes instatnly"
date: 2010-05-06
forum: New to Ubuntu
---

### Post by ludwigr on 2010-05-06
Hey guys. 

I've just took the big step on beggining with Ubuntu instead of Windows and I installed the lastest Ubuntu from ubuntus website and everything worked fine until I woke up this morning. 

When I open the Terminal it instantly closes itself. 
Got any tips on how to solve this? 

Thanks.

With the kindest regards
LudwigR.

---

### Post by Peter09 on 2010-05-06
Is the rest of the system working OK?

---

### Post by ludwigr on 2010-05-06
> **Peter09 said:**
> Is the rest of the system working OK?

Yes, can't find any problems except for the sounds that stops working sometimes, but a quick reboot takes care of that.

---

### Post by warfacegod on 2010-05-06
I'd say use Synaptic to see if there are any broken packages, fix them if any, and then reinstall gnome-terminal.

---

### Post by ludwigr on 2010-05-06
> **warfacegod said:**
> I'd say use Synaptic to see if there are any broken packages, fix them if any, and then reinstall gnome-terminal.

Yeah. I'm reinstalling gnome-terminal atm, hopefully this will solve my problems. Thanks. :)

---

### Post by warfacegod on 2010-05-06
Actually, in hind sight, what I should have said before was; mark it for complete removal and then reinstall it. Oh well, see if simply reinstalling fixes the issue.

---

### Post by nothingspecial on 2010-05-06
Try a couple of other terminal emulators - xterm, eterm, roxterm, terminator.

Does it happen with any of the others?

---

### Post by ludwigr on 2010-05-06
> **warfacegod said:**
> Actually, in hind sight, what I should have said before was; mark it for complete removal and then reinstall it. Oh well, see if simply reinstalling fixes the issue.

Tried both reinstalling, complete removal and installing again, didn't work. 
Where can I find xterm, and the other emulators? 

Thanks

---

### Post by warfacegod on 2010-05-06
They're all in Synaptic. You should already have xterm. Hit Alt+F2> type xterm. If it works and you'd like to use that one. Create a New Item in System> Prefs.> Main Menu. Call it whatever you like but make the command: xterm

---

### Post by Peter09 on 2010-05-06
Create a new user - see if that user has the same problems, if not then its corruption in your .gnome? config.

---

### Post by ludwigr on 2010-05-06
> **Peter09 said:**
> Create a new user - see if that user has the same problems, if not then its corruption in your .gnome? config.

Created a new user and the problem still exists :(

---

