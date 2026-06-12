---
title: "Share top panel with multiple users"
date: 2010-01-26
forum: New to Ubuntu
---

### Post by japhyr on 2010-01-26
Hello,

I have set up a top panel with many useful shortcuts, and would like to share the top panel with other users on my desktop.  But when other users log in, they get the default top panel.  Is there an easy way to share my top panel settings with all users on the machine?

---

### Post by warfacegod on 2010-01-26
I suspect the easiest way would be to modify each panel indvidually from each users account. Unless you have an obsurd number of users, it shouldn't take more than 15 - 20 minutes, I'd guess.

---

### Post by Paqman on 2010-01-26
It shouldn't be hard to do, you just need to find the right settings files in your home folder and copy them to your other users.

I'm not at my Ubuntu machine to check right now, but a quick Google suggests the top panel config might be in:

~/.gconf/apps/panel/profiles/default/toplevels/top_panel/%gconf.xml

---

### Post by philinux on 2010-01-26
> **japhyr said:**
> Hello,

I have set up a top panel with many useful shortcuts, and would like to share the top panel with other users on my desktop.  But when other users log in, they get the default top panel.  Is there an easy way to share my top panel settings with all users on the machine?

If you want all users to be standard I would copy the folder

~/.gconf/apps/panel

to all users. Why not create a test user and try it out.

---

