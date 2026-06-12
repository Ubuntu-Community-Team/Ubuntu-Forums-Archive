---
title: "[SOLVED] reset pidgin/kopete settings to new"
date: 2009-01-01
forum: New to Ubuntu
---

### Post by natman on 2009-01-01
I am using KDE4 am having problems with kopete and pidgin old setting files and wish to start totally from scratch, is there any way to delete ( permenantly ) all pidgin and kopete files, where are they stored?

---

### Post by kestrel1 on 2009-01-01
Not sure as I don't use either program, but I would imagine they are stored in your home folder under something like .pidgin or .kopete & will be hidden folders. Just go to the View menu & select to show hidden folders.

---

### Post by nhasian on 2009-01-01
you could go to the synaptic package manager and mark them for complete removal. that should remove the program as well as the preferences.  pidgin's data is saved in ~/.purple

---

### Post by drs305 on 2009-01-01
> **natman said:**
> I am using KDE4 am having problems with kopete and pidgin old setting files and wish to start totally from scratch, is there any way to delete ( permenantly ) all pidgin and kopete files, where are they stored?

Your pidgin personal settings are stored in ~/.purple  If you delete that folder all your personal settings will be removed. The folder will be restored when you restart pidgin. Synaptic has an option for 'complete removal' should you want to remove everything.

---

### Post by natman on 2009-01-01
Thats fine for pidgin, but no matter what i do i cant get rid of kopete. I asked for complete removal and went and deleted the kopete directory, still every time i start it back up ( after a reinstall ) it remembers my old ids! how do i get a fresh install!! :)

---

### Post by drs305 on 2009-01-01
I don't use kopete but I installed it and created an account. Here is where it put the information:
```

~/.kde/share/config  # You might look into this folder and edit out kopete info
~/.kde/share/config/kopeterc
~/.kde/share/apps/kopete
~/.kde/share/apps/kopete/contactlist.xml
~/.kde/share/apps/kopete/jabber-capabilities-cache.xml

```

---

### Post by natman on 2009-01-01
Perfect, it was > ~/.kde/share/config  # You might look into this file and edit out kopete info

That i was missing, thank you. This has also solved the problem of > <p> </p> on either side of all my outgoing messages to yahoo contacts in case anyone needs help on this too . Thanks again!

---

