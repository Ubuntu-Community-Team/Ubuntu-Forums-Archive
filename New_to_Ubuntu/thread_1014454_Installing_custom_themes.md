---
title: "Installing custom themes?"
date: 2008-12-17
forum: New to Ubuntu
---

### Post by Grimhound on 2008-12-17
I just downloaded this:
[http://lokheed.deviantart.com/art/Graphite-Suite-2-0-28688856](http://lokheed.deviantart.com/art/Graphite-Suite-2-0-28688856)

What do I have to do and where do I have to move the folders to get it to register under Appearances? Where is all the stuff for themes stored?

---

### Post by starcannon on 2008-12-17
System>Preferences>Appearance>Install

ack my bad, thats not packaged to cooperate with our theme manager, that looks like it'll need manually installed. 
anyone?

---

### Post by xjcannonx on 2008-12-17
yeah just extract the zip file then you will need to create a .tar.gz of the file that is extracted,

 it looks like there is another zip file inside the newly extracted file so you will need to extract that as well, 

after all the zips are extracted then its time to go to the terminal and cd to the graphite_suite folder...all the extracted files should be in there, once you cd your way to that folder put in this to make your .tar.gz```
tar czf graphite_suite.tar.gz graphite-clearlooks graphite-icon-set office-metacity-theme graphite-splash.png graphite-bmp-skin
``` also make sure you have the other dependencies that the sebsite lists installed as well i.e. the gperfection iconset....This should do the trick

---

### Post by evilkastel on 2008-12-17
solved it. you have to unzip the gtk folder, and then compress it as a tar.gz. then install it as properly. same procedure goes for icons. hope this works.

---

### Post by Grimhound on 2008-12-18
I still am completely unable to figure this out. What do I need to run it, and how do I install it? Steps, please.

---

### Post by xjcannonx on 2008-12-18
First make sure gtk-engines is installed

this can be done by entering this in a terminal ```
apt-cache policy gtk2-engines
```

---

