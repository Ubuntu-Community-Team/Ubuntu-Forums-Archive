---
title: "Having Trouble Setting Widescreen Resolution"
date: 2009-07-17
forum: New to Ubuntu
---

### Post by yygyt on 2009-07-17
Hello everyone. I am also a newbie as you can guess so please forgive me for asking such a silly question.

Every time I open "Applications ->Other -> Screens and Graphics" and set my resolution to "Widescreen Monitor" it asks me to log off for changes to take effect, therefore I reboot the computer.
Log on screen opens in widescreen mode but after I enter username and pw, it returns back to the way it was.
Where do I make a mistake? How can I set it so that it stays in "widescreen monitor" resolution?

By the way, i have nvidia geforce go 7200, i don't know if it is important.

Thanks in advance.

---

### Post by RomeReactor on 2009-07-17
Hi. Which version of Ubuntu do you have (8.04, 8.10, 9.04)?

The 'Screens and Graphics' application is no longer used; you should try in 'System->Preferences->Display' to set your desired resolution, or use the **nvidia-settings** application .

---

### Post by yygyt on 2009-07-18
I have 8.04 . 
I have also tried "nvidia-settings" but I couldn't have found a "widescreen" option to choose in that application. Further, i cannot see a display tab under system->preferences.

What an idiot, right? Sorry for that. I just don't want to be scared of Linux. Seemingly, at this moment, I cannot solve my problems on my own.

---

### Post by DanYoSon on 2009-07-18
I would say that there would be no widescreen button but you just have to change the display resolution to be a widescreen resolution. check System>Administration>Nvidia X Server Settings if you are useing the vendor supplyed drivers.

hope this helps

---

### Post by fooman on 2009-07-18
> **yygyt said:**
> 
I have 8.04 . 
I have also tried "nvidia-settings" but I couldn't have found a "widescreen" option to choose in that application.

 
there will not be a widescreen "option"...there *should* however be diferent widescreen resolutions for you to choose from.
 
some widescreen resolutions would be 1280x800, 1440x900, 1680x1050....
 
what monitor (size, make, model #) are you using?
 
also, to make the settings stick with nvidia-settings, you need to make the changes as root. so, open a terminal (applications > accessories > terminal) and type or copy/paste the following:
 
```
 
gksudo nvidia-settings

```
 
make the changes, click "apply", then "save to x configuration file".
 
hope that helps.

---

### Post by CLomax on 2009-07-18
If the resolution you want isn't there you'll have to change the horizsync/vertrefresh in xorg.conf to values suitable for your monitor. You can google your desired resolution with "horizsync vertrefresh" to find out which values you need...

```
gksudo gedit /etc/X11/xorg.conf
```

This is the section you're looking for:
[PHP]
Section "Monitor"
.....
    HorizSync       XX - XX
    VertRefresh     YY - YY[/PHP]

---

### Post by yygyt on 2009-07-18
Thank you all, it worked.

Ubuntu rules :D

---

