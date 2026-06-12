---
title: "How do edit a /etc file?"
date: 2011-07-09
forum: New to Ubuntu
---

### Post by alanmacuser on 2011-07-09
I have installed Ubuntu 11.04 onto an Acer 1362LC laptop but the screen is stuck in the top left corner, I think at 800x600 resolution. The top of a second screen is visible below that.

The control panel cant identify the screen and refuses to make changes. I have read this following item on the web but don't know how to perform the edit:
----------------------------------------------------

After some Google searching, I came across some Ubuntu forum posts that suggested various fixes that did not work, or which required programs that were not available on the live CD. Finally, the thing that worked was quite simple: I edited /etc/X11/xorg.conf, and in the “Monitor” section added the following line:

HorizSync 28 - 60
After restarting X with Ctrl-Alt-Backspace and logging back in, the Screen Resolution tool now showed a number of newly available screen resolutions, including the desired 1024×768. Apparently, the Trident display driver (or some other piece of X) wasn’t able to detect the monitor capabilities automatically (perhaps due to the monitor’s extreme antiquity), and the new line in xorg.conf provided just enough of the required information.
----------------------------------------------------

Can anyone describe the method? Its worth a try rather than immediately revert to PC Linux OS.

Thanks,

Alan.

---

### Post by el_koraco on 2011-07-09
click ALT + F2, type in **gksudo gedit /etc/X11/xorg.conf**, and you'll get a text file in which you need to input the line that the guy described, and then save the file.

---

### Post by waynefoutz on 2011-07-09
```
sudo gedit /etc/X11/xorg.conf
```

You'll probably get a blank file. Modern versions of xorg don't use that file anymore by default.

---

### Post by haqking on 2011-07-09
> **waynefoutz said:**
> ```
sudo gedit /etc/X11/xorg.conf
```You'll probably get a blank file. Modern versions of xorg don't use that file anymore by default.

you should use gksudo for graphical apps including editors

---

### Post by Wim Sturkenboom on 2011-07-09
Not wanting to hijack this thread but is there an easy way to create that file from e.g. the settings used by X; I do dearly miss that file.

---

### Post by mikewhatever on 2011-07-09
> **Wim Sturkenboom said:**
> Not wanting to hijack this thread but is there an easy way to create that file from e.g. the settings used by X; I do dearly miss that file.

Yep, you can generate it with the **Xorg -configure** command.

---

### Post by alanmacuser on 2011-07-09
"Yep, you can generate it with the Xorg -configure command."

I am not sure this advice was really intended for me but I have no idea at all what the Xorg -configure command is or how its used. I need a step by step guide.

All I want is to get my laptop showing a full screen.

Alan.

---

### Post by alanmacuser on 2011-07-09
The Alt+F2 plan as advised worked, but the file was empty just as another contributor predicted.

My wife's Fuji Amilio laptop works really well on 11.4 - with the exception of the Function Keys. 

It looks like PC Linux OS is better suited to the Acer laptop though. Time to revert I think.

Thanks everyone.

Alan.

---

### Post by mikewhatever on 2011-07-09
> **alanmacuser said:**
> "Yep, you can generate it with the Xorg -configure command."

I am not sure this advice was really intended for me but I have no idea at all what the Xorg -configure command is or how its used. I need a step by step guide.

All I want is to get my laptop showing a full screen.

Alan.

Actually, I've quoted the user I replied to. ;)

---

### Post by Wim Sturkenboom on 2011-07-09
> **mikewhatever said:**
> Actually, I've quoted the user I replied to. ;)
Yep,

and thanks for the reply. I've never known that there was an 'Xorg' command

---

### Post by wildmanne39 on 2011-07-09
Hi, here is a guide for creating a xorg,conf file.
[http://grenage.com/xorg.html](http://grenage.com/xorg.html)

---

### Post by jtarin on 2011-07-09
> **Wim Sturkenboom said:**
> Yep,

and thanks for the reply. I've never known that there was an 'Xorg' command
About 12 years ago I thought that was the "ONLY" command in the installation toolbox.:p

---

### Post by wildmanne39 on 2011-07-09
> **jtarin said:**
> About 12 years ago I thought that was the "ONLY" command in the installation toolbox.:pHi, it has almost become extinct, but natty has breathed new live into it.

---

### Post by jtarin on 2011-07-09
> **wildmanne39 said:**
> Hi, it has almost become extinct, but natty has breathed new live into it.
Like me!

---

