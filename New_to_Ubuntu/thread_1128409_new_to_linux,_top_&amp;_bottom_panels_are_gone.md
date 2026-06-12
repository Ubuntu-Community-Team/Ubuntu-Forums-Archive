---
title: "new to linux, top &amp; bottom panels are gone"
date: 2009-04-17
forum: New to Ubuntu
---

### Post by bgmomof2 on 2009-04-17
I'm a new convert to Linux, and started with xubuntu 8.10 on a used laptop.  All has been good for nearly a month and for some reason both the top and bottom panel are hidden or missing.  I've looked for a reason with no luck, just how to manage in gnome desktop user guide.
Can anyone point to a cause or better yet a cure!

---

### Post by LunaticHiatus on 2009-04-17
I had a situation with xfce back in the day where the panels disappeared due to a bug but I reinstalled, updated, and never had the problem again. perhaps you ran into the bug before updating everything?
You can install Gnome Panel for a quick fix in add/remove progams. although it wont show all your applications and there will be some issues between gnome and xfce.

---

### Post by LowSky on 2009-04-17
hit Alt +F2
type 

gnome-panel

---

### Post by CatKiller on 2009-04-17
Make a launcher on your Desktop that runs **xfce4-panel**. You should only need to run it once. This will start up the panels to let you do whatever it is you need to to make them autostart again.

---

### Post by bgmomof2 on 2009-04-19
I installed xfce-panel w/synaptic, but when I log-in I have to run ALT F2 command line.  I'm confused as to why it was there, then went away and I had to reinstall.  Sorry for the elementary question, but what is a launcher on the desktop?  Is there a start menu/command that I can add the xfce-panel to?

---

### Post by Bölvaður on 2009-04-19
> **bgmomof2 said:**
> I installed xfce-panel w/synaptic, but when I log-in I have to run ALT F2 command line.  I'm confused as to why it was there, then went away and I had to reinstall.  Sorry for the elementary question, but what is a launcher on the desktop?  Is there a start menu/command that I can add the xfce-panel to?

It is called "sessions" should be there in the menu somewhere. just add a new item there with the command "xfce4-panel"


*added*
a luncher is a powerful tool, but to make it short... it is like shortcuts in windy

---

### Post by bgmomof2 on 2009-04-19
I looked up info on sessions.  The settings manager has a sessions and startup icon.  but there is not a place to add a new item.  So, in applications>settings>settings manager>autostarted apps, I added xfce-panel.  Seems to work.

---

### Post by Gingerman on 2010-11-20
> **LowSky said:**
> hit Alt +F2
type 

gnome-panel

**I'm having the same problem, and this solution returns the message, "the command, gnome-panel failed to run."**

I am running Docky (all right, I'm a gadget freak).  Could this be interfering?  When I close Docky, the panels don't return.

The panels are there for about 3 minutes when I start up the computer, and then go away.

---

