---
title: "Make a shared printer"
date: 2009-12-05
forum: New to Ubuntu
---

### Post by desmondh99999 on 2009-12-05
Have setup a printer HP Photosmart 7800 in a desktop with Ubuntu installed. It is again linked to another desktop through a router. Anybody tell me how do I share the printer with the other PC through the said router?

---

### Post by cariboo on 2009-12-05
Just go the the cups web interface, [http://localhost:631](http://localhost:631) and make sure Share printers connected to this system is enabled. See screenshot.

I'm running Lucid, so if you are using a version older than Karmic the screen will look slightly different.

---

### Post by odonth09 on 2009-12-13
i seem to have a problem because i have done what you said above and i still can't find the printer on my XP computer. now i am completely lost, it may be a problem with settings on the PC or on Ubuntu and i don't know where to start. any help would be appreciated.
PS. i'm a newbie (as in i installed Karmic yesterday) so please try to dumb it down and if there is a solution that doesnt require me to use the terminal to edit config files etc.. it would help.

EDIT: 
don't worry i figured it out. i just had to enter the printer manually on the XP printer setup wizard by entering http://<hostname>:631/printers/<printername> in the  "connect a printer on the Internet or on a home or small office network" box

---

