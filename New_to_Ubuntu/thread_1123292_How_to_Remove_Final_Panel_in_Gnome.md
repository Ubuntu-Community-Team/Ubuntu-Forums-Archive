---
title: "How to Remove Final Panel in Gnome"
date: 2009-04-12
forum: New to Ubuntu
---

### Post by Ayeco on 2009-04-12
This is somewhat frustrating to me.  I am running Intrepid and I have Compiz, Emerald, and AWN all set up how I like, and when I go to say bye to all the panels, the last one says no?  What, did the software developers think I am too stupid to be trusted with control over my panels?  I have tried " sudo apt-get -s remove gnome-panel " , " killall gnome-panel " , and adjusting my settings in gconf-editor like suggested in other posts.  This seems like more work than it should be...

---

### Post by mcduck on 2009-04-12
You'll just have to remove the gnome-panel from your Gnome session. As long as it's configured to be part of the session it will spawn automatically back when killed.

Open gconf-editor, browse to desktop/gnome/session and remove the panel from required components.

---

### Post by Ayeco on 2009-04-12
Thanks man, that was just what I was looking for.  Where were to help these guys? [http://ubuntuforums.org/showthread.php?t=609771](http://ubuntuforums.org/showthread.php?t=609771).  lol

---

### Post by theozzlives on 2009-04-12
> **Ayeco said:**
> This is somewhat frustrating to me.  I am running Intrepid and I have Compiz, Emerald, and AWN all set up how I like, and when I go to say bye to all the panels, the last one says no?  What, did the software developers think I am too stupid to be trusted with control over my panels?  I have tried " sudo apt-get -s remove gnome-panel " , " killall gnome-panel " , and adjusting my settings in gconf-editor like suggested in other posts.  This seems like more work than it should be...

I'm curious, how'd you do it? I'm down to one panel. I can see the clock, and menu (don't care for AWN's menu). What about notification area, window switcher, and trash (well I guess you can put the trash on the desktop). I would like to run with no panels and get more desktop. Here's a screenshot:

---

### Post by Paqman on 2009-04-12
> **theozzlives said:**
> What about notification area, window switcher, and trash 

AWN has applets that will do all of that. Make sure you've installed all the AWN applet packages through Synaptic.

---

### Post by theozzlives on 2009-04-12
What Main Menu do you use?

---

