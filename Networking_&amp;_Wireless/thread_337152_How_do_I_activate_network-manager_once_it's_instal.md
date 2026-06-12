---
title: "How do I activate network-manager once it's installed? [Resolved]"
date: 2007-01-12
forum: Networking &amp; Wireless
---

### Post by kindafunnylookin on 2007-01-12
> **aysiu said:**
> Install *network-manager*

I used aptitude to install network-manager and all seemed to go OK but now I cannot get it to open using: ```
network-manager
```Any ideas?

---

### Post by aysiu on 2007-01-12
I'm trying to remember how I got it activated.

Have you tried right-clicking the Gnome panel and adding it as a Gnome applet?

---

### Post by Paerez on 2007-01-12
System->preferences->sessions->Startup programs

add an item with the command:

nm-applet --sm-disable

then log out, log in.

---

### Post by kindafunnylookin on 2007-01-12
I don't know what you mean. I have very little experiance, in fact what I do know I owe to you and the Psychocat page. Thank's for that.

---

### Post by mtierney on 2007-01-12
Quick question back to you: Did you use synaptic (literally) or apt-get?

---

### Post by kindafunnylookin on 2007-01-12
I used aptitude.

---

### Post by Paerez on 2007-01-12
OK, click the "System" button on the top left of your screen. Then select Preferences, then Sessions. Click the "Startup Programs" tab. Click the Add button. Type in "nm-applet --sm-disable" (without the quotes) and hit ok. Then hit close. Then log out and back in again.

---

### Post by kindafunnylookin on 2007-01-13
I finally figured out what aysiu was talking about and got it activated. Thanks for the help.
> **aysiu said:**
> Have you tried right-clicking the Gnome panel and adding it as a Gnome applet?

---

