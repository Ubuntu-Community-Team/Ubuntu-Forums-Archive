---
title: "lxde openbox menu"
date: 2010-04-23
forum: New to Ubuntu
---

### Post by dzon65 on 2010-04-23
How can I edit the openbox menu in lxde.There's no menu xml in config/openbox and no obmenu in the OB menu.

---

### Post by warfacegod on 2010-04-23
Change the binary code itself.

---

### Post by dzon65 on 2010-04-23
AH W.How would I do that?

---

### Post by warfacegod on 2010-04-23
Haven't got a clue.

---

### Post by dzon65 on 2010-04-23
Lol.Was thinking of "importing" some,with a obmenu in it and edit it afterwards.

---

### Post by MooPi on 2010-04-23
I'll switch computers shortly to log into my Openbox rig so I can answer your question. But basically you open an xml document and and and tweak as needed. Give me a minute.

---

### Post by warfacegod on 2010-04-23
Found this. Hope it helps. [http://ubuntu-lxde.wikidot.com/menu]("http://ubuntu-lxde.wikidot.com/menu")

---

### Post by dzon65 on 2010-04-23
> **MooPi said:**
> I'll switch computers shortly to log into my Openbox rig so I can answer your question. But basically you open an xml document and and and tweak as needed. Give me a minute.
I just imported the openbox menu.xml from my other pc,added it to the config/openbox and.....nothing.

---

### Post by MooPi on 2010-04-23
Your menu file is located in /etc/X11/openbox/menu.xml 
Below are my menu and xml file in action. It is very simple clean menu but it's all I need.
[http://dl.dropbox.com/u/5209151/thisNthat/menu.xml](http://dl.dropbox.com/u/5209151/thisNthat/menu.xml)
[http://dl.dropbox.com/u/5209151/thisNthat/Openbox_menuxml.png](http://dl.dropbox.com/u/5209151/thisNthat/Openbox_menuxml.png)
It appears that the LXDE folks may have changed how the openbox menu is incorporated into the system. Don't know if your menu.xml file is located in the same local.

---

### Post by dzon65 on 2010-04-23
> **warfacegod said:**
> Found this. Hope it helps. [http://ubuntu-lxde.wikidot.com/menu]("http://ubuntu-lxde.wikidot.com/menu")

Gives errors.I think I have to insert/replace that imported xml somewhere else as well,just don't know where to look for it.

---

### Post by dzon65 on 2010-04-23
> **MooPi said:**
> Your menu file is located in /etc/X11/openbox/menu.xml 
Below are my menu and xml file in action. It is very simple clean menu but it's all I need.
[http://dl.dropbox.com/u/5209151/thisNthat/menu.xml](http://dl.dropbox.com/u/5209151/thisNthat/menu.xml)
[http://dl.dropbox.com/u/5209151/thisNthat/Openbox_menuxml.png](http://dl.dropbox.com/u/5209151/thisNthat/Openbox_menuxml.png)

Aha,thanks moopi.

---

