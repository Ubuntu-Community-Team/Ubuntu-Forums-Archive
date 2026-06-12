---
title: "motion blur messed up my laptop :("
date: 2009-09-20
forum: New to Ubuntu
---

### Post by Soul_Fly on 2009-09-20
Very brief..... I messed up my laptop somehow when i turned on Motion blur....whenever i hover over the panels or click icons...the os hang..YES it HANGS!!..and crashes and multiple restarts aren't helping me..plz if sum1 could tell me a wasy to disable this process from terminal..(Crl F12 toggle shortcut doesnt seem to work) or a safe mode like MS frm where i can switch this horror of plz... its urgents...

EDIT: the screen starts going black

---

### Post by Liolikas on 2009-09-20
Reboot but do not login then ctl+atl+F1. You have command prompt now. Longin into it and:
sudo apt-get remove <name>
Then ctrl+alt+F7 then login into again working desktop.

---

### Post by CatKiller on 2009-09-21
What you're trying to achieve is to amend the /apps/compiz/general/allscreens/options/active_plugins GConf key so that it doesn't include *mblur*. Since you can't use *gconf-editor*, since your screen is messed up, you'll have to do it the old-fashioned way.

Log into a virtual console as Liolikas suggests, and then use ```
nano .gconf/apps/compiz/general/allscreens/options/%gconf.xml
``` to open the XML file that controls this key value for editing. Remove the mblur string list entry, and you'll have disabled the Motion Blur plugin. Save (Ctrl-o) and close (Crtl-x). Alt-F7 will take you back to the graphical environment, and you should be able to log in normally.

---

