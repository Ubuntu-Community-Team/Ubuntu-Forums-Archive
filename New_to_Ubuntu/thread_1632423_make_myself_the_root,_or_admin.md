---
title: "make myself the root, or admin?"
date: 2010-11-27
forum: New to Ubuntu
---

### Post by solitario on 2010-11-27
Hello all. I've ditched Windows completely and need a little help. I'm new so forgive the ignorance... I've successfully installed PHP, Apache on Ubuntu 10.10, however I can't drag and drop files directly into my var/www/ folder without doing the whole Terminal->sudo cp jazz.
So... how can I set up my installation so I don't have to do that anymore? I'd like to be able to drag and drop anywhere.
I am the only user on this computer.
Many thanks.

---

### Post by marshmallow1304 on 2010-11-27
Doing so would defeat the purpose of permissions.  For drag-and-drop, you can run

```
gksudo nautilus
```

which will open an instance of the file browser as root.

---

### Post by Zzl1xndd on 2010-11-27
Its not normally discussed in the forums as keeping the Root user account disabled is considered a security feature. 

That being said I would just change the owner of the Directory you need access too from Root you your user Name.

I normally do this using 

```
gksudo nautilus
``` Navigating to the file right click it > Select properties > Permissions. And change the owner.

---

### Post by bodhi.zazen on 2010-11-28
Running LAMP on a desktop is "OK", however, on a production environment it is not a great idea.

If you want a graphical interface, use web tools such as webmin.

---

### Post by jwbrase on 2010-11-28
> **tweakedenigma said:**
> Its not normally discussed in the forums as keeping the Root user account disabled is considered a security feature. 

That being said I would just change the owner of the Directory you need access too from Root you your user Name.

I normally do this using 

```
gksudo nautilus
``` Navigating to the file right click it > Select properties > Permissions. And change the owner.

Careful! You don't want to do that with just any folder. Doing that to certain system folders could well screw up your system.

A better solution: Using whatever package manager you're most comfortable with (Software Center, Synaptic, whatever), download the "nautilus-gksu" package. Once you've installed that, you can just right click on a folder and click "Open as administrator" to open that folder in a nautilus window with root privileges. (You can also, for example, use right-click -> Open as administrator to open a text file with gedit as root, or whatever).

---

### Post by solitario on 2010-11-28
gksudo nautilus did it. many thanks.

---

