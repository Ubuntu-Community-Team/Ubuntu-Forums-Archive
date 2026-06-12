---
title: "awn - desktop"
date: 2010-01-09
forum: New to Ubuntu
---

### Post by kwyto on 2010-01-09
Hi guys, well I'm in a pickle.  I went an installed awn in my laptop without problem. I'm running karmic koala. Then i proceed to strip the top panel of all the applets. After that went on to gconf-edit and erase the gnome-panel, in order to eliminate the top panel and make awn the only panel in the screen. My problem is that I can't install the applet for the battery status, nor the applet for network connections. When I try to install the battery's applet if gives an error and crashes. If someone has any idea of how I can restore the gnome-panel or what's is the command for the network applet, I would definetly appreciate any help. Thank you in advance.

---

### Post by Temposs on 2010-01-09
You can right click the desktop and click "Add Panel" and then do what you like.

Alternatively, if you want the default panel settings back, you can delete the .gnome2 directory(this will reset all your gnome settings to the default), or the appropriate subdirectories associated with the gnome panel within that directory. When you restart, the default settings will automatically be generated for you.

---

### Post by kwyto on 2010-01-09
the add panel option doesn't appear. also i trying to get the icon for the network connection. i deleted .gnome2 and restarted ubuntu, still don't get the option of adding a panel. i really don't want to reinstall ubuntu, because of it. any other suggestions are really appreciated?

---

### Post by Temposs on 2010-01-09
Also delete .gnome and .gconf

---

### Post by kwyto on 2010-01-09
i did it and basically it reset the appearance settings. i just went i reinstalled ubuntu 9.10 . Now what i wanted was to look like [http://news.softpedia.com/news/Create-Your-Own-Sexylicious-Ubuntu-Desktop-80189.shtml]("http://http://news.softpedia.com/news/Create-Your-Own-Sexylicious-Ubuntu-Desktop-80189.shtml"). where there isn't a panel except for awn. another thing that baffles me, it's that i cannot find, when adding applets to a panel, the battery status and network connections. help?

---

### Post by kwyto on 2010-01-09
ok i found it. battery status, network manager, bluetooth and sound control are bundle under Notification Area. Thank you for everything

---

