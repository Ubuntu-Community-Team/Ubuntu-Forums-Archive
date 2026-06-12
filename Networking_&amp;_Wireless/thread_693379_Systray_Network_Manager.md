---
title: "Systray Network Manager"
date: 2008-02-11
forum: Networking &amp; Wireless
---

### Post by snl2587 on 2008-02-11
This is going to sound a little stupid: I was trying to restore the "shutdown" button in the "Quit..." systray buttons menu (it spontaneously disappeared) and I accidentally removed my systray network manager. I really liked it: it displayed a series of vertical blue bars corresponding to the wireless network strength, would show a list of wireless networks whenever I left-clicked on it, and would show two dots with a green rotating thing whenever I connected to another network. For the life of me I can't remember what package installed it, so if anyone could tell me how to get it back I would greatly appreciate it.

(also, if anyone could tell me how to get the "Quit..." menu to display the shutdown button again or how to get my battery meter which only displays when charging the battery or draining it I would also appreciate it. I've been using Ubuntu through two versions and have spent so much time programming I haven't really learned the gui stuff)

---

### Post by MONODA on 2008-02-11
I think you could try re-installing a package called "nm-applet" without the quotation marks. That is the name of the networkmanager. to get the shutdown back in the quit menu I would think you would have to go into apps->systools->config manager. There I think you should be able to control mostly all gnome options. I removed hibernate from my quit menu that way.

---

### Post by snl2587 on 2008-02-11
Thanks a bunch! I solved it by running "nm-applet" after re-installing "gnome-network-manager" (which was already there, so probably just running it would have been fine). I also got the battery thing to work again with the config manager...still trying to find where the shutdown option is, but I'll find it eventually.

---

### Post by Tenken on 2008-02-11
Are you talking about the Shutdown button that comes on the panel by default? Try right-clicking your panel and selecting add to panel.

---

### Post by snl2587 on 2008-02-11
Not the button, but the option to shutdown after clicking the button. At the moment it gives me the option to switch users, logout, lock screen, suspend and hibernate, but not to shutdown.

---

### Post by Tenken on 2008-02-11
Did you recently enable desktop effect because I heard that it sometimes removes the shutdown option. Try taking a look at [this thread]("http://ubuntuforums.org/showthread.php?t=244662").

---

### Post by snl2587 on 2008-02-11
Just fixed it. Turns out in System>>Administration>>Login Window, the button to show actions menu on the local tab was unchecked. Not sure how that happened, but now everything is back to normal.

---

