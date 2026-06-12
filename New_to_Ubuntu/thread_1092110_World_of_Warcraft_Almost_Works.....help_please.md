---
title: "World of Warcraft Almost Works.....help please"
date: 2009-03-10
forum: New to Ubuntu
---

### Post by chem_major on 2009-03-10
Ok, so I admit it I'm new. I've been using Ubuntu for about 2 years now, just basic playing around. Some of the technology I use as a chemist requires knowledge of Unix/Linux. 

So here's where I need help:
I swear I've followed how to install WoW word for word on the help pages, I've done my best to try and not repeat a post, but I'm at a loss after a couple of months of fidgeting with it.
I can watch all the intro cinematics with beautiful graphics and sound, but as soon as I get to the log-in screen, the graphics spaz, show all their base polygons, etc. Also the center that usually shows "username:", "passwords:" is pitch-black. I don't see anything.

I've tried  logging-in blind even to see if I could get to my character screen and it doesn't seem to even register the keyboard. 

Thanks for any help.

---

### Post by cb951303 on 2009-03-10
which card?

---

### Post by orethrius on 2009-03-10
Here's a quick command line (hold Alt and hit F2) that should kick back your graphics card to a file named **graphicscard.log** on your desktop.

EDIT: The "quotes" are not quotes here, but backticks (`).  The backtick is usually achieved on QWERTY keyboards by pressing the same key labeled with a '~' on it.

```
echo `lspci | grep VGA` > ~/Desktop/graphicscard.log
```

---

### Post by chem_major on 2009-03-10
Ok, here's my card. 

00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)

I guess I should also mention that the comp is a 3 year old Toshiba Satellite, 2.0 GHz Intel processor.

---

### Post by cb951303 on 2009-03-10
could you fire up a terminal (Menu > Accessories > Terminal)
and paste back the result of **glxinfo | grep "direct rendering"**

---

### Post by chem_major on 2009-03-11
glxinfo | grep "direct rendering"
direct rendering: Yes

---

### Post by cb951303 on 2009-03-11
> **chem_major said:**
> glxinfo | grep "direct rendering"
direct rendering: Yes

everything looks ok on paper.

which guide did you read to setup WoW?
did you activate opengl?

---

### Post by chem_major on 2009-03-11
I've used the Ubuntu help guide [https://help.ubuntu.com/community/WorldofWarcraft]()
I've also tried PlayOnLinux, which looked like it was going to work, but they haven't added an install for WotLK yet.

Yes, I added the opengl line to the WTF file, like the ubuntu help said to do.

---

### Post by ClaytonOT on 2009-03-11
You made the necessary changes to the WTF/config.wtf file?

Have you tried 
> wine "C:\Program Files\World of Warcraft\WoW.exe" -opengl

---

### Post by chem_major on 2009-03-11
Yep. Lets me watch intros, but goes to hell soon as I hit login screen.

---

### Post by cb951303 on 2009-03-11
then I guess it has something to do with the intel drivers + your specific intel card. your best bet is to search for your card in google to see if anyone had any luck with it on linux and wow

---

### Post by orethrius on 2009-03-12
Well, there's a WINE AppDB entry, I'll cite the relevant portion here.

> 
Bad graphical corruption in certain areas

    * Find the following registry entry:

      HKEY_CURRENT_USER\Software\Wine\Direct3D\

    * Add a new key (type String) and name it 'OffscreenRenderingMode'

    * Double click the new key and add the value 'pbuffer'

      This may or may not fix the 'indoor white minimap' problem. No guarantees though!

      Note: Pbuffer (Pixelbuffers) are an old 'experiment' that WoW started to use back when it was developed. They have since been replaced with Framebuffers, which is one of the reasons ATI hasn't included full support for them in the Linux drivers yet. Setting the above value to 'fbo' will switch the rendering mode to Framebuffers, which may speed up rendering on newer graphics cards.

      YMMV.

(Source: [http://appdb.winehq.org/objectManager.php?sClass=version&iId=14154](http://appdb.winehq.org/objectManager.php?sClass=version&iId=14154))


Additionally, it may be helpful to post the output (winever.log) of this command (Alt+F2):
```
wine --version > ~/Desktop/winever.log
```

---

