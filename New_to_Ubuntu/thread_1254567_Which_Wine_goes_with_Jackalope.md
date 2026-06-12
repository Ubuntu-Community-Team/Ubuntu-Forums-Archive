---
title: "Which Wine goes with Jackalope?"
date: 2009-08-31
forum: New to Ubuntu
---

### Post by Gulfvet91 on 2009-08-31
I'm looking at Synaptic and It shows 3 Wine files.  There is Wine, Wine.dev and Wine.gecko  Which one should I install since I am using Xubuntu 9.04?

---

### Post by sydbat on 2009-08-31
> **Gulfvet91 said:**
> I'm looking at Synaptic and It shows 3 Wine files.  There is Wine, Wine.dev and Wine.gecko  Which one should I install since I am using Xubuntu 9.04?All 3. Can't hurt.

Also, to answer your thread title - red...I prefer Merlot...

---

### Post by howefield on 2009-08-31
> **Gulfvet91 said:**
> I'm looking at Synaptic and It shows 3 Wine files.  There is Wine, Wine.dev and Wine.gecko  Which one should I install since I am using Xubuntu 9.04?

Wine, which when selected I think, will pull in any dependancies it needs (one of them being wine-gecko).

---

### Post by Gulfvet91 on 2009-08-31
Okay, everything is supposedly done installing but all I can find is WineFish LATex Editor.  How does Wine work to help you run Windows apps?

---

### Post by Gulfvet91 on 2009-08-31
Apparently I did something wrong on the Wine installation.  There go eight hours for nothing.

---

### Post by LowSky on 2009-08-31
what can you do wrong, go to synaptic click on WINE, and then install... thats it.

then to install a windows program you run the setup.exe or install file form the windows media.

---

### Post by 4Orbs on 2009-08-31
After installing wine, the first thing you gotta do is configure it by opening the wine configuration utility. It should be in the application menu and listed under "Other". If you can't find it there then you can enter in a terminal:
```
winecfg
```
Then select the correct audio driver in the utility (since you are on xfce, probably the oss is correct... but maybe alsa). The simple act of opening the wine configuration gui automatically creates the necessary initial folder and files (hidden) in your personal user home folder. You will probably also need to tell xubuntu to open windows exe files with the wine program loader. To do this, right click on any win .exe file and select properties, then select "Open With" the Wine Windows Program Loader.

---

### Post by Gulfvet91 on 2009-09-01
Do I need to re-do the config every time I reboot?  I found the files last night but when I brought my system back up today I couldn't find them anywhere.

---

### Post by Gulfvet91 on 2009-09-01
Never mind, I found them.

---

### Post by Gulfvet91 on 2009-09-01
Solved I think.  I'm still a bit unsure about how to use Wine to get things done with applications that depend on Windows.

---

### Post by Ms_Angel_D on 2009-09-01
If you could tell us what applications your trying to use wine for, maybe someone can help or even suggest a native Linux alternative.

---

