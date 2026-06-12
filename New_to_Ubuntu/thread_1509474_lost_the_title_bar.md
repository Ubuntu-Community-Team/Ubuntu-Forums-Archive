---
title: "lost the title bar"
date: 2010-06-14
forum: New to Ubuntu
---

### Post by menotaur on 2010-06-14
yesterday I right-clicked the title bar to remove two instances of the title bar. now both are gone and i have lost the main menu too. so now i cant access anything. w/o reinstalling is there anything i can do in startup or boot that i can do to either go back or get the menus back?

---

### Post by migs73 on 2010-06-14
Do you mean you have deleted the Panel (the bar at the top/bottom of the screen) or the place where your open programs are displayed called windows list(like the windows task bar)?
If you have deleted one of the panels (top or bottom) there is the option to add a 'New Panel' when you right click on the existing one.
If you have deleted the windows list, right click on the panel and select 'Add to Panel' and select window list from the menu and then 'Add'.
If you have deleted all your panels that is a different kettle of fish.

Had look about and if you have deleted both panels you could try Alt-F2 and type in; gnome-panel ;and click run.(don't type the semicolons though!)

---

### Post by karthick87 on 2010-06-14
Execute these commands in terminal

 ```
gconftool-2 --shutdown
rm -rf ~/.gconf/apps/panel
pkill gnome-panel 
```

This will restore your panels..

---

### Post by thane1 on 2010-06-17
I too have lost my top and bottom panels after editing top panel.  Have gotten them back by creating terminal launcher on the Desktop running the commands above (which didn't result in addition of new top panel) and then creating a Desktop launcher for "gnome-panel" (without the quotes), which then made a new panel, which can be edited.  Unfortunately the panel is eliminated from the Desktop with each restart of the computer and won't re-establish itself.  How do I get it to stick on restart by default?

---

### Post by thane1 on 2010-06-18
Progress to date:  Found the hidden configuration files in my separate /home partition, but couldn't figure out what to change in them either directly or by using the gconf_editor program.  Deleted the hidden gnome files .gconf .gconfd and .gnome2  did a pkill of gnome and rebooted, which I understood should have gotten rid of my gnome menu settings letting ubuntu re-establish new ones again.  No joy.  Still the same as before.  Backed up /home partition data to a backup partition, reinstalled lucid again (this time also reformatting my /home partition) and I now have my menu panels back.  Must reconfigure everything and add extra programs yet, but at least the system is workable.  Cannot mark this post as solved though, since I still don't know, what the cause of the problem was.

---

### Post by OlaugeB on 2010-12-07
[@karthick87]("http://art.ubuntuforums.org/member.php?u=891422")
thank you, that snippet just cleared up the mess I had trying to get the preinstalled gnome tools back in a different panel.

---

### Post by LLudovic on 2011-01-07
> **karthick87 said:**
> Execute these commands in terminal

 ```
gconftool-2 --shutdown
rm -rf ~/.gconf/apps/panel
pkill gnome-panel 
```

This will restore your panels..
Thank you [karthick87]("http://art.ubuntuforums.org/member.php?u=891422"), your solution worked for me.

---

### Post by waynefoutz on 2011-01-07
consider installing Ubuntu Tweak, it enables you to lock the panels down so you won't delete them again. It also cures Gnome's annoying habit of moving items around on the panel when you change screen resolutions.

---

