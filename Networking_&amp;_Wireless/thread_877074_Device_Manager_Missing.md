---
title: "Device Manager Missing"
date: 2008-08-01
forum: Networking &amp; Wireless
---

### Post by Frederick J. Harris on 2008-08-01
I just did a fresh install of 8.04 Hardy Heron on one of my test laptops on which I had 6.1 Edgy Eft.  There is no "Device Manager" on the System >> Administration menu as there is with Edgy Eft.  I'm in the same boat as several other fellows on this thread which doesn't appear to have been successfully resolved...

[http://ubuntuforums.org/showthread.php?t=858297&highlight=Device+Manager](http://ubuntuforums.org/showthread.php?t=858297&highlight=Device+Manager)

This Device Manager applet or whatever it is provides critical technical information.  How can I get it installed on Hardy Heron?    I will do that tonight when I get home to my dsl connection if I know what to install.  What I'm trying to do is follow the instructions in Kier Thomas's "Beginning Ubuntu Linux" so that I may learn how to use ndiswrapper.  In that book he describes how to glean important info from "Device Manager", but apparently this subsystem was removed from Hardy Heron.  I realize this technical info can probably (surely) be obtained through the command line, but a GUI interface to it would be nice.  I can't believe something like this was removed from the basic install!

---

### Post by AndrewTheArt on 2008-08-01
For some reason the Device Manager (gnome-device-manager) isn't included by default in Hardy.

```
sudo apt-get install gnome-device-manager
```

Now look in Applications -> System Tools and find the entry "Device Manager".

Alternatively, run it from the command line - 

```
gnome-device-manager&
```

---

