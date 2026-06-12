---
title: "ubuntu hangs after boot"
date: 2010-01-30
forum: New to Ubuntu
---

### Post by iRounak on 2010-01-30
i enabled "reflection" in compiz and ubuntu hanged. I did a hard shut down. 
Since then, this is what happens:
At startup, Ubuntu boots completely. I can see my desktop, its icons etc. Then it hangs. 
What to do now?

---

### Post by NightwishFan on 2010-01-30
Try this:

On the login screen at the bottom there is something called session. Choose xterm as the session, and then log in.

In the terminal at the top type:
```
gconf-editor
```

A box should open. At the folder tree on the side navigate to /apps/compiz/allscreens/options

In the list on the top right, right click on the top option called "active_plugins" and choose "Set As Default".

Quit the program at File-> Quit, and type exit in the terminal. At the logon screen choose "Gnome" as the session, and then log back in. If the problem is fixed, set desktop effects to none in System-> Preferences-> Appearence-> Desktop Effects. We can figure out how to fix it from that point on.

I think that your card does not support Pixel Shaders.

---

### Post by iRounak on 2010-01-30
many thanks for the reply, Nighwishfan. I had login screen turned off. It was set to automatically login with one specific user. So I don't see the login screen. what should i do?

---

### Post by NightwishFan on 2010-01-30
If you are quick enough while booting, press alt+f2, and when the dialog box comes up, type:
```
metacity --replace
```

This is an oddly puzzling problem. :D

If that does not work, I think we can fix it. When booting after bios hold in shift. A menu will appear saying Ubuntu-2.***generic and Ubuntu****recovery mode, etc. Choose recovery mode. When you see another menu, choose root shell. When you type commands you should see no output that they succeed, that is what you want.

When you get a command line, type:
```
cd /home/yourusername
```
then
```
mv .gconf .gconf_old
```
then
```
mv .gconfd .gconfd_old
```

---

### Post by iRounak on 2010-01-31
Many thanks, NightwishFan.
I used mv .gconf and mv .gconfd. 
It worked perfectly.
However, I am surprised that there is no shortcut to see the login screen if automatic login is turned on.

---

### Post by NightwishFan on 2010-01-31
You can set the log in screen to boot in a timeout of like 10 seconds, or just skip it and log in. You can configure under: System -> Administration -> Login Screen

---

