---
title: "Blueman install on Feisty"
date: 2007-12-14
forum: Networking &amp; Wireless
---

### Post by Virgofenix on 2007-12-14
I'm trying to run Blueman 0.3 on my Feisty install. I compiled from the source code available from the Blueman homepage and was able to install it. However, it doesn't launch.

I tried running it from terminal.
------------------------------------------------
Terminal output of the error:

* Initializing 'Bluetooth.manager' Class
* Initializing 'Bluetooth.services' Class
* Adapter Found
* Initializing adapter hci0
* Initializing 'Bluetooth.inquiry' Class
* Initializing 'Bluetooth.dbusAgent' Class
* Passkey agent registered
* Authorization agent registered
Traceback (most recent call last):
  File "/usr/bin/blueman", line 159, in <module>
    Globals.main_list = main_list(xml)
  File "/usr/lib/python2.5/site-packages/blueman/Gui/main_list.py", line 40, in __init__
    self.treeview.set_property("has-tooltip", True)
TypeError: object of type `GtkTreeView' does not have property `has-tooltip'
-------------------------------------------------

---

### Post by rouge568 on 2007-12-14
I would recommend installing from the repositories. 
```
 sudo apt-get install blueman
```
This will take far lesser time to install, and is sure to be stable.

---

### Post by Virgofenix on 2007-12-14
Blueman isn't on the Feisty repos, unfortunately.

I have all the dependencies installed, I think. Some of the packages have different names in Synaptic (so if you know which specific packages are needed, please list). I'm guessing it's the GTK+ packages that are the problem. What's GTKTreeView? I've been unable to comprehend the technical stuff I've found so far on my searches.

---

### Post by walmis on 2007-12-16
blueman uses latest GTK (2.12), feisty has 2.10.

---

### Post by Virgofenix on 2007-12-20
Sorry for the late reply.

Is there any way to update the GTK in Feisty without upgrading to Gutsy?

---

