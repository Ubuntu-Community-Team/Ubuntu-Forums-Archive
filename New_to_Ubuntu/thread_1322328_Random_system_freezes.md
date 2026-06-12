---
title: "Random system freezes"
date: 2009-11-10
forum: New to Ubuntu
---

### Post by downhiller2010 on 2009-11-10
9.10 is randomly freezing on me after a fresh install.  I would believe its my graphics card radeon 9200se/rv 280.  Is there any alternate drivers that might fix this?

---

### Post by twisted_steel on 2009-11-10
I'm not sure if this is related, but I was experiencing random lockups with my 9600 Mobility (RV350) card.  I have to use the open source driver in 9.10 because the official ATI driver no longer supports the card, and you cannot use the old driver because it needs a different version of X.Org.  I had to add the following lines to my /etc/X11/xorg.conf file:
```
Section "Device"
        Identifier      "ATI Radeon"
        Option          "AccelMethod"   "XAA"
EndSection
```My xorg.conf is otherwise empty.

---

### Post by downhiller2010 on 2009-11-10
I found a couple bug reports linked to this.  I followed the path to the xprg.conf file but I do not have on in that directory.  Should I create it?

---

### Post by twisted_steel on 2009-11-10
Yes, you can go ahead and create the file.  You will have to do this with sudo due to the directory permissions.  I don't believe the file is there by default in Karmic.

This should do the trick to get the file open:
```
gksudo gedit /etc/X11/xorg.conf
```

---

### Post by dillandriskell on 2009-11-10
I had the exact same issue downhiller.  I think the Ubuntu team just hasn't made a fix for our video drivers yet, though I'm sure it will be released sometime in the near future.

What fixed it for me, was as soon as I logged in (before it could crash) I would go into **System > Preferences > Appearance** then from there go to the **Visual Effects** tab, then click **None**.  

Also before you log in, press Ctrl + Alt+ F1, this will take you into a terminal where you can't freeze up.  Then type this; 

```
sudo apt-get update && sudo apt-get upgrade
```

That will update and upgrade your system, so if any fixes have been made you'll get them.

Hope that helped!

---

### Post by downhiller2010 on 2009-11-10
I have all my visual effects set to minimum and Im still freezing.  I am going to try and edit my xorg.conf file later.

---

### Post by dillandriskell on 2009-11-10
Hmm...I hate to say it but if you can't get it to work a downgrade may be in order :(

I was on the brink of doing it myself until I found a workaround, Ubuntu 9.04 is still a wonderful and stable system.  Maybe if you stick with that for a month or two, then upgrade, a fix will have been made for your drivers.

Absolute last resort though

---

