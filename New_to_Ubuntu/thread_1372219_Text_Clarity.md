---
title: "Text Clarity"
date: 2010-01-04
forum: New to Ubuntu
---

### Post by rosswmcgee on 2010-01-04
Why do words not appear clearly in the dual boot set up, with Win 7. Win 7 text is clear all works well. Using the same computer using Ubuntu 9.10
words appear with letters that are faded or pink or blue. Also Opera works fine in win7 but has issues in Ubuntu 9.10. Yet I am sure if I ran a
clean install with 100% HD used this would not occur. Using 320gb hd. emachine slim line brand new. 



Some may appear blue, some pink

---

### Post by pmlxuser on 2010-01-04
it has to do with the graphics not the installation see documentation on the typr of graphics card you are using there should be some configuration needed to make it work better.

---

### Post by SuperSonic4 on 2010-01-04
Sounds like a video problem

---

### Post by mcduck on 2010-01-04
> **rosswmcgee said:**
> Why do words not appear clearly in the dual boot set up, with Win 7. Win 7 text is clear all works well. Using the same computer using Ubuntu 9.10
words appear with letters that are faded or pink or blue. Also Opera works fine in win7 but has issues in Ubuntu 9.10. Yet I am sure if I ran a
clean install with 100% HD used this would not occur. Using 320gb hd. emachine slim line brand new. 



Some may appear blue, some pink

Sounds like you have subpixel smoothing enabled, but are either using wrong DPI settings for your monitor/resolution, or wrong subpixel layout.

Go to System/Preferences/Appearance, and click the Details-button in the Fonts-tab to access the settings. First set the dots per inch setting (it's calculated from your display resolution & size), and after that try the different subpixel order settings to find the one that doesn't result in color artifacts in text.

---

### Post by landy rover on 2010-01-04
hi 

had the same problem with my ubuntu 8.10 i was my ati graphics card but downloaded the updated drivers from ati and it was fine installed them..but the restricted drivers is not so good as the real thing 

hope i was any help

---

### Post by rosswmcgee on 2010-01-04
You are on the right track here but still I have not figured it out. Note now I discover there is no system log out or shut down i AM GOING TO RE-INSTALL.

---

### Post by rosswmcgee on 2010-01-04
In the install even the graphics are as previously described.

---

### Post by rosswmcgee on 2010-01-04
Ok no more partition just a clean install/still fiddling with appearance/ but what happened to the shut down mode/ system/ there is no shut down option, how do I get that back?

---

### Post by rosswmcgee on 2010-01-04
OK the problem has been solved. The problem was the display setting not the Appearance. 

But where is the system shut down?

---

### Post by Miljet on 2010-01-04
Mine is at the far right of the top panel. Where are you expecting it to be? If it is not there, you can add it by right clicking on the panel, clicking on "Add to panel" and then "Log out."

---

### Post by rosswmcgee on 2010-01-04
It is there but as a matter of habit I always removed it and use system/ shut down/ or restart but it is not an option for some reason, it is still there on my wife's Ubuntu, but not on my new install. Its just a difference that I can not explane.

---

### Post by Miljet on 2010-01-04
Sorry, but Shutdown/Restart is no longer listed under System as of version 9.04.

---

### Post by mcduck on 2010-01-05
> **rosswmcgee said:**
> It is there but as a matter of habit I always removed it and use system/ shut down/ or restart but it is not an option for some reason, it is still there on my wife's Ubuntu, but not on my new install. Its just a difference that I can not explane.

If you remove the default shutdown applet (actually it's called "Indicator Applet Session") from the panel the shutdown/logout options should appear again in the System menu. But you'll probably have to log out or at least restart the panel before that happens.

It was changed this way to avoid having the same options in two different places. So if the applet is in use, the options are there. Otherwise they are in the System menu. But never in both places at the same time.

---

### Post by rosswmcgee on 2010-01-05
Well how about that! Again I learned something today.

---

