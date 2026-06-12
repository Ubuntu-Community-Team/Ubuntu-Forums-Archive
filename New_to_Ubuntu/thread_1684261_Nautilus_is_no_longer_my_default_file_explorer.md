---
title: "Nautilus is no longer my default file explorer?"
date: 2011-02-08
forum: New to Ubuntu
---

### Post by Cooperkid on 2011-02-08
I dont know how i did this...
but after messing around installing a few themes i have a problem - everytime i go to "places" and then pick a folder e.g "downloads" instead of nautilus opening up the folder "Appearance preferences" will launch instead!?!?

how do i get nautilus back?

---

### Post by drs305 on 2011-02-08
Open Nautilus, right click on any folder, select "Open With Other Application" and choose "File Browser". Make sure the "Remember" box is ticked.

---

### Post by Cooperkid on 2011-02-08
> **drs305 said:**
> Open Nautilus, right click on any folder, select "Open With Other Application" and choose "File Browser". Make sure the "Remember" box is ticked.

I cant even find Nautilus in my applications...how can i reinstall it?

---

### Post by wojox on 2011-02-08
Alt+F2 

nautilus

---

### Post by drs305 on 2011-02-08
Applications, Accessories, File Manager?

Does it open if you type "nautilus" or "nautilus --browser" to start it in a terminal (Applications, Accessories, Terminal)?

Try this to install it:
```
sudo apt-get install nautilus
```

---

### Post by bhaverkamp on 2011-02-08
ernieh@bernieh-lx:~$ dpkg -l | grep naut
ii  libnautilus-extension1                                      1:2.30.1-0ubuntu1.1                             libraries for nautilus components - runtime 
ii  nautilus                                                    1:2.30.1-0ubuntu1.1                             file manager and graphical shell for GNOME
ii  nautilus-data                                               1:2.30.1-0ubuntu1.1                             data files for nautilus
ii  nautilus-sendto                                             2.28.4-0ubuntu1                                 integrates Evolution and Pidgin into the Nau
ii  nautilus-sendto-empathy                                     2.30.3-0ubuntu1                                 GNOME multi-protocol chat and call client (n
ii  nautilus-share                                   

If it's not listed:

sudo apt-get install nautilus

---

### Post by Cooperkid on 2011-02-08
perfect that worked a treat!
thanks very much for all the help!:smile:

---

