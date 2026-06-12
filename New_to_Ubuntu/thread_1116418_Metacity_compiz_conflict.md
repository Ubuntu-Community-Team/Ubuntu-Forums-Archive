---
title: "Metacity compiz conflict"
date: 2009-04-04
forum: New to Ubuntu
---

### Post by hollowtd on 2009-04-04
I just got compiz working sort of I think there is conflict btw metacity and compiz on my dell using hardy does a gone know how to help this? Thanks

---

### Post by gettinoriginal on 2009-04-05
Not exactly sure what you are asking, compiz and metacity are both window managers.  Open a terminal and type:
```
compiz --replace
```
that should fix your problem.  :p

---

### Post by hollowtd on 2009-04-05
Yeah they both seem to want to run simultaneous. I type the coMpiz replace and it says xgl ok and then says there's no nvidia. I am so close but when I have compiz as the win manager I can't select anything from the scroll down menus like system or place. I am not surewhy. It sort of locks up. Thanks

---

### Post by gettinoriginal on 2009-04-05
System, Preferences, Appearance, Visual Effects, should be Extra or Custom.

---

### Post by hollowtd on 2009-04-05
I have been told this but there is no visul effects tab, can you tell me if there is something I need to download from terminal to get this visual effects tab?I have fusion icon and compiz manager.when I run compiz 3d cube works but I can't select anything from menu pulldown.

---

### Post by gettinoriginal on 2009-04-05
If your appearance window does not look like this, then something is wrong.  You may want to reinstall "gnome-desktop"
[ATTACH]108783[/ATTACH]

---

### Post by masque7 on 2009-04-05
> **gettinoriginal said:**
> If your appearance window does not look like this, then something is wrong.  You may want to reinstall "gnome-desktop"
[ATTACH]108783[/ATTACH]
I suppose for "Custom" to be showing, you would have to have Compiz installed?

---

### Post by hollowtd on 2009-04-05
I am using hardy 8.04.1 and it has where you choose a theme like human etc

---

### Post by hollowtd on 2009-04-05
I have compiz on there too

---

### Post by gettinoriginal on 2009-04-05
Yes, where you choose the theme, should be tabs: themes, background, fonts, interface, and visual effects, click that tab and apply "extra or custom"
[ATTACH]108817[/ATTACH]

---

### Post by hollowtd on 2009-04-05
Mine is missing that tab And that is very odd thanks for the pics too. Do you know if there is a way to get that tab? I know I have compiz and even the fusion icon but not that tab. Thanks ps. Is this normal in 8.04 hardy .

---

### Post by hollowtd on 2009-04-05
I may need nvidia first ??

---

### Post by gettinoriginal on 2009-04-05
I am not sure why that is missing, so may I suggest you try the following:
System Restore
Reboot > during grub splash, hit escape > Recovery mode > Enter (let finish)
Repair Broken Packages > Enter (if it asks about updates hit N) (let finish)
Try to fix X server > Enter (Let finish)
Resume normal Boot > Enter

---

### Post by hollowtd on 2009-04-06
I will try that and let you know. I just removed compiz and all the files with emrald and rebooted and was going to try and reinstall those. I assume the Visual Effects tab should still be under appearances though. This is strange as the computer is new. Thanks for that.

---

### Post by hollowtd on 2009-04-06
After some research now that I'm back home, it seems that Dell and Conical have done this on purpose I suppose. Not sure if I can get it working or not. Darn it

---

### Post by gettinoriginal on 2009-04-06
Ah hah, did not realize that you had a factory installed version, please check this thread, it should help you.  :p
[http://ubuntuforums.org/showthread.php?t=980355&highlight=visual+effects+tab](http://ubuntuforums.org/showthread.php?t=980355&highlight=visual+effects+tab)

---

### Post by hollowtd on 2009-04-06
I checked that out and actually found some things on it earlier. I have 8.4.1 though. I have the same problem though, with no tab for Visual Effects. I am not sure what to do as when I have compiz running, things are slow or don't come up at all. The boxes turn to lines and it takes about 5 minutes for anything to work after selecting it. I just don't know what to do. I've removed all the compiz stuff and redid it through synatptic but still to no avail. I wonder if anyone has used 8.10 on this machine (the mini 12) or another and gotten things to work (without the pen drive). Thanks

---

### Post by gettinoriginal on 2009-04-07
I have never used a preinstalled OS, but go here and then the circled sub-forum, there are alot of discussions of it there:
[http://ubuntuforums.org/forumdisplay.php?f=130](http://ubuntuforums.org/forumdisplay.php?f=130)
[ATTACH]108979[/ATTACH]

---

### Post by billgoldberg on 2009-04-07
Yeah, Dell butchers Ubuntu.

You could start hacking away to get things back to normal or install the real Ubuntu.

---

