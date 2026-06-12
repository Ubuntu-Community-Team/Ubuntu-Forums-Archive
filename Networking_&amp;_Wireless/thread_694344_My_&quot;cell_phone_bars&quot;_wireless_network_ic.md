---
title: "My &quot;cell phone bars&quot; wireless network icon is missing from upper panel."
date: 2008-02-11
forum: Networking &amp; Wireless
---

### Post by diablo75 on 2008-02-11
In the upper right hand corner of my own computer, I have an icon which displays the connection status of my wireless card.  So at startup, after I type my keyring password in, it shows the whirling thing with the green lights, and then the cell phone bars looking thing showing signal strength after successfully connecting to a wireless network.

However on a friends laptop, this icon is missing and I don't know how he got rid of it.  Nor do I know how to get it back.  Any ideas?

---

### Post by Schalken on 2008-02-12
That icon is the Network Manager Applet, and can be started with the command "nm-applet --sm-disable". Try running that command from a terminal (Applications > Accessories > Terminal) or from the Run dialog (Alt+F2) to make sure it works and what the problem is if it doesn't.

It is by default set to be started when you log in by being listed in the Startup Programs  under System > Preferences > Session. If it isn't there, add it, and it will hopefully startup when you log in.

---

### Post by diablo75 on 2008-02-12
Sweet, thank you very much!

---

