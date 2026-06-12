---
title: "Problems installing wrath of the lich king and I can't find the files I install"
date: 2009-02-20
forum: New to Ubuntu
---

### Post by SpaRa16 on 2009-02-20
With wine/playonlinux? Where can I find them? I know the program>wine> etc but I need to enter the file where everything is to put something in there how can I do this? Also I got serious trouble installing world of warcraft wrath of the lich king how can I do this?

---

### Post by Mercury_Alpha on 2009-02-20
Any program you install with Wine should be putting a link (shortcut) on the desktop. Right-click on the shortcut icon, select Properties, and the location of the program is listed at the end of the Command field. Look for a "z:" drive entry.

---

### Post by SpaRa16 on 2009-02-20
> **Mercury_Alpha said:**
> Any program you install with Wine should be putting a link (shortcut) on the desktop. Right-click on the shortcut icon, select Properties, and the location of the program is listed at the end of the Command field. Look for a "z:" drive entry.

Well I've found the file where it is but there's no real ''map'' or whatever like on windows and other thingys on linux ^^ it's only 1 icon :/


Anyone knows how to install world of warcraft wrath of the lich king? Because if I can't install it by tomorrow I'll remove ubuntu and install windows again I cba spend serveral days trying to get this working really :/

---

### Post by Mercury_Alpha on 2009-02-20
The directory tree (the "map") is listed in the shortcut, like I said. Right-click on the icon, select Properties, and look for the directory in the Command text field that starts with "z:"

Z: is the virtual directory in which Wine installs all your Windows software.


If you're having problems accessing the installer on the WoW discs, [look here]("http://www.wowwiki.com/Troubleshooting_Wine"). In Ubuntu's case, you'll be using "CDROM1" or "CDROM0" instead of "SR0."

---

