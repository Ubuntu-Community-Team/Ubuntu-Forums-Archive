---
title: "Problems with Urban Terror"
date: 2011-01-21
forum: New to Ubuntu
---

### Post by vanbroeK on 2011-01-21
Assuming that ubuntu wasn't at all capable at gaming due to steam games performing to a point where they are unplayable, I ignored all games and focused on fine tuning my system only to stumble upon Urban Terror. 

I installed the Urban Terror Optimised found in Synaptic but when I started playing there was a big problem with the graphic as you can see in the attachment. The graphics were repeating and it was impossible to play.

I have no idea how this happened and not a clue how to fix it but I was thinking about my graphics card (Intel HD Graphics) and was wondering if it was even configured properly. How do i found this out?

Please help, I've tried to research this but I couldn't dig up anything. If you need more info please let me know.

I'm running Ubuntu 10.10

---

### Post by NightwishFan on 2011-01-21
If you enabled any 3d tweaks in the "3d acceleration" program, disabled them. Other I am not sure, generally Intel graphics work well for Urban Terror. I have an Intel Series 4 Mobile and it works fine for UrT.

---

### Post by vanbroeK on 2011-01-21
No i have not touched the 3d accelerations settings, i wasn't even aware of that.

EDIT: I just installed assault cube only to encounter unbearable lag. Is this just my graphics?

Full system specs are: Acer Aspire 5740, Core i3, 2gb ram, Intel HD Graphics

---

### Post by stamoulohta on 2011-01-21
Maybe you should try downloading and installing the latest proprietary drivers for your card. If that doesn't work, backup "/etc/X11/xorg.conf" and then play with it's settings trying to pinpoint what is causing the problem.

- a somewhat "Windows approach" but maybe it helps.. ;)

good luck.
g

---

### Post by NightwishFan on 2011-01-21
Intel Graphics have no proprietary drivers, though I am unsure why they seem to be working so poorly. Perhaps try to google your exact graphics card for work around.

---

### Post by treesurf on 2011-01-21
Perhaps try the version of UrT found on the Urban Terror website, as opposed to the repo version.  I have no problem running it on a laptop with integrated intel graphics and a slower processor than yours.

---

### Post by dudetime on 2011-01-28
I too am having the same problem. i think it must be 10.10 because it works fine on 10.4

---

### Post by vanbroeK on 2011-01-29
Would try the download from the site but I don't think there would be any change due to other games not working well.

I am running the 64-bit version of 10.10, would this be an issue?

---

### Post by vanbroeK on 2011-01-29
I read around and found that some problems were fixed through adding the user to the video group. I did that and rebooted but nothing. I also enabled direct rendering I think it was but neither helped at all.

---

### Post by treesurf on 2011-01-29
OK some research at the gaming forum here has turned up a solution.  It sounds like 64-bit may be your problem.  There are links to optimized binaries here.  Looks like an easy fix to try:

[http://ubuntuforums.org/showthread.php?t=1433663&highlight=urban+terror&page=2](http://ubuntuforums.org/showthread.php?t=1433663&highlight=urban+terror&page=2)

---

### Post by vanbroeK on 2011-01-29
> **treesurf said:**
> OK some research at the gaming forum here has turned up a solution.  It sounds like 64-bit may be your problem.  There are links to optimized binaries here.  Looks like an easy fix to try:

[http://ubuntuforums.org/showthread.php?t=1433663&highlight=urban+terror&page=2](http://ubuntuforums.org/showthread.php?t=1433663&highlight=urban+terror&page=2)

Okay thanks I'm in the middle of downloading the game from the site and I will try that also. Cheers.

Also what do I do with this file exactly?

---

### Post by treesurf on 2011-01-29
One last option for you.  Some folks who were having problems reported that installed from playdeb worked for them.  You can try that here:

[http://www.playdeb.net/updates/ubuntu/10.10/?q=urban+terror](http://www.playdeb.net/updates/ubuntu/10.10/?q=urban+terror)

Good luck. :)

---

### Post by vanbroeK on 2011-01-29
> **treesurf said:**
> One last option for you.  Some folks who were having problems reported that installed from playdeb worked for them.  You can try that here:

[http://www.playdeb.net/updates/ubuntu/10.10/?q=urban+terror](http://www.playdeb.net/updates/ubuntu/10.10/?q=urban+terror)

Good luck. :)

Thanks again but what do i do with the ioq3 file that I got from your link?

---

### Post by treesurf on 2011-01-29
Put it in the folder with the other Urban Terror files and use it as the game launcher.  You may have to right click>Properties>Permissions>Make executable before it will launch properly.

I haven't tried this version of the launcher myself, but others seem to have had luck with it.

---

### Post by vanbroeK on 2011-01-29
> **treesurf said:**
> Put it in the folder with the other Urban Terror files and use it as the game launcher.  You may have to right click>Properties>Permissions>Make executable before it will launch properly.

I haven't tried this version of the launcher myself, but others seem to have had luck with it.

It's all good. Once I finished downloading the game I chucked in the launcher and it worked perfectly. 

Thanks for all your help.

---

### Post by treesurf on 2011-01-29
Glad to hear you've got it sorted.

---

