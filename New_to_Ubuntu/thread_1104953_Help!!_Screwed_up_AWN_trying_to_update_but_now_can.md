---
title: "Help!! Screwed up AWN trying to update but now can't remove it!"
date: 2009-03-24
forum: New to Ubuntu
---

### Post by humphreybc on 2009-03-24
So I was on 0.2.6 and heard that 0.3.1 fixed the custom icons problem, among some other fixes. I went to the wiki and installed the repositories, then used this command to install the new version:

sudo apt-get install avant-window-navigator-bzr awn-core-applets-bzr awn-manager-bzr

I didn't uninstall the old version first because I was hoping it would keep my settings.

Sure enough Awn was updated to 0.3.1 and most of my settings were intact. In fact in the preferences it still listed all of my launchers, but they were not on the bar. I deleted these and tried to re-add them by dragging and dropping but it wouldn't work. I went to Synaptic and searched for "awn" and "avant" and found all the packages.. but none were checked!! I couldn't uninstall it from there... how on earth do I remove 0.3.1 completely and install it properly?!

---

### Post by humphreybc on 2009-03-24
Don't worry I worked it out myself in the end haha.

I used sudo apt-get remove avant-window-navigator-bzr awn-core-applets-bzr awn-manager-bzr

sudo apt-get autoremove

sudo apt-get autoclean

to clean up my packages. Then following [these]("http://wiki.awn-project.org/Installation:Ubuntu") I added the correct PPA repository and deleted the other one, then installed the right packages from the command line.

---

### Post by mhgsys on 2009-03-24
have you tried 
```


sudo apt-get remove avant-window-navigator-bzr awn-core-applets-bzr awn-manager-bzr

```

edit:
lol. posted simultaneous

---

