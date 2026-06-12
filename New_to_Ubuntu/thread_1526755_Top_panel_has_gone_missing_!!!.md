---
title: "Top panel has gone missing !!!"
date: 2010-07-08
forum: New to Ubuntu
---

### Post by Sandy.1 on 2010-07-08
Don't know what I did but the top panel and all it's usefulness has disappeared.

I was watching some video so maybe the screen resolution has been changed.

Please advise, how do I get it back

Merci d'avance

Sandy

---

### Post by launchy on 2010-07-08
type "killall gnome-panel" in the terminal without the "". this will restart all your panel/s.

---

### Post by Sandy.1 on 2010-07-08
Thanks for your prompt reply but I'm afraid it didn't work. I'm still without a top panel
Sandy

---

### Post by spiky001 on 2010-07-08
if you right click bottom panel then new panel that should put it back

---

### Post by launchy on 2010-07-08
heres a link and follow the instructions:
[http://ubuntuforums.org/showthread.php?t=1475584](http://ubuntuforums.org/showthread.php?t=1475584)

or you could go to your ~/.gconf/apps delete the panel folder. log out and log back in.
this will set your panel to its default settings

---

### Post by RiceMonster on 2010-07-08
You're going to havr to re-add it. Right click on the bottom panel, and select "New Panel". You will have add all the widgets again as well. Right click on the new panel, and go to "add to panel". You can re-add them all from there. You'll want to add the menu bar, window list, clock, notification area and the indicator applet again.

---

### Post by keroman on 2010-07-08
this is what I did to get panels back 
[http://www.watchingthenet.com/restor...-settings.html]("http://www.watchingthenet.com/restore-panels-in-ubuntu-back-to-their-default-settings.html")

if you do this you should have a backup on your desktop
[http://www.starryhope.com/linux/ubun...els-in-ubuntu/]("http://www.starryhope.com/linux/ubuntu/2010/restore-the-default-panels-in-ubuntu/")

---

### Post by Sandy.1 on 2010-07-08
Thanks to one and all. Top panel back in place.

---

### Post by spiky001 on 2010-07-08
Have you got all the applets back as well

---

### Post by doublewitt on 2010-07-20
Add this to your collection of software...

download this nice little application that either restores your default panels (top and bottom) or restores saved panels that you personally customized. You might have to re-boot your computer to see the results.

The application is called **PanelRestore**
[http://www.starryhope.com/linux/ubuntu/2010/restore-the-default-panels-in-ubuntu/](http://www.starryhope.com/linux/ubuntu/2010/restore-the-default-panels-in-ubuntu/)

It's tiny (787 bytes). Simply follow the instructions on the webpage - it's easy to use...

---

### Post by doublewitt on 2010-07-28
In the **Ubuntu Tweak** application, there is a setting under [COLOR="Blue"]GNOME Settings[/COLOR] that enables a - *[COLOR="Red"]warning message[/COLOR]* - in case you delete a panel... this can be a useful setting to prevent an accidental deletion...

---

### Post by doublewitt on 2010-08-29
As of **today**, in the same [COLOR="Blue"]Ubuntu Tweak[/COLOR] application, you can use the new "Desktop Recovery" feature to backup and restore your desktop settings (including panels)... *you can also restore to system defaults..*.

---

