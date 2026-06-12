---
title: "GNOME equivalent of KDE's Kate (text editor)?"
date: 2010-05-02
forum: New to Ubuntu
---

### Post by ajk95 on 2010-05-02
I used Kubuntu for about a week and decided that the hardware I was running it on wasn't powerful enough for KDE, so I switched to Ubuntu instead. I need to know what the text editor (not word processor) for GNOME is (Kate equivalent).

---

### Post by madjr on 2010-05-02
gedit

but i use kate and kwrite in gnome anyways

---

### Post by ajk95 on 2010-05-02
> **madjr said:**
> gedit

but i use kate and kwrite in gnome anyways
I opened gedit just to see what it looked like, and I would prefer Kate. Could I possibly install *just* Kate without bringing the entire KDE environment along with it?

---

### Post by anewguy on 2010-05-02
You can install Kate in Gnome, but do it through Synaptic Package Manager.  It will come up with a long list of things it has to install as well - all of these are dependencies for Kate to run (like libraries, etc., for KDE).  I don't think it will install the kde desktop package also, but I'm not sure.  Either way, you have to go with the dependencies Synaptic comes up with.  Far easier that way then trying to just install Kate via apt-get, as you'll just come up with a ton of missing dependencies that way.

Dave ;)

---

### Post by aysiu on 2010-05-02
If you install Kate with *apt-get* in [the terminal](http://www.psychocats.net/ubuntu/terminal) be sure to install only what you need: ```
sudo apt-get update
sudo apt-get install kate --no-install-recommends
```

---

### Post by anewguy on 2010-05-02
> **aysiu said:**
> If you install Kate with *apt-get* in [the terminal](http://www.psychocats.net/ubuntu/terminal) be sure to install only what you need: ```
sudo apt-get update
sudo apt-get install kate --no-install-recommends
```

It does still have to install KDE libs, etc., though, doesn't it?  That has always seemed to be the case when I have installed a KDE app in Gnome - it wants the appropriate libs in order to run, if you don't have any of KDE installed.

Curious - maybe I've done more in the past than I needed to?

Thanks
Dave ;)

---

