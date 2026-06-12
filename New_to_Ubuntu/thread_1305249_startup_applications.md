---
title: "startup applications"
date: 2009-10-29
forum: New to Ubuntu
---

### Post by tim1970 on 2009-10-29
I just did a fresh install of 9.10, and after configuring everything to my liking, I went to add conky to my startup applications.  But when I re-boot, conky is not running.  Does anyone have any ideas?  This is something  i have done many times on this and my other computers with previous versions of Ubuntu.


Thanks


Tim

---

### Post by barbz127 on 2009-10-29
I had the same problem - its a bug with 9.10 - I was told to add the command as you normally would, before you close down the window click add again enter nothing and close it all down.

Open startup applications and conky should be there still.
Paul

---

### Post by tim1970 on 2009-10-29
That still does not work.  When I close down startup applications and re-open I see conky there, but when I re-start nothing happens.

Is there another alternative until the bug is fixed?  Some type of shell script that runs automatically at startup or something else?


Thanks

Tim

---

### Post by a20365354 on 2009-10-31
I have smiler problem too :(
I add a application in startup list but it gone when I re-open the startup config application :(
I think if we know the file of startup list or the folder that application will start by boot inside,the problem will solved.

---

### Post by michaelzap on 2009-10-31
Same problem here with Guake.

---

### Post by a20365354 on 2009-11-01
Aha! :D
The bug can't fix currently but I found the path of auto-start folder :D
/userfolder/.config/autostart
Add some desktop file there.

Here is a simple desktop file:
[Desktop Entry]
Name=[NAME]
Exec=[THE COMMAND THAT YOU WANT TO RUN]
Terminal=[TURE OR FALSE]
Type=Application
X-GNOME-Autostart-Phase=Applications
X-GNOME-AutoRestart=true
X-GNOME-Autostart-enabled=true

Hope it helps. ;)
-a20365354

---

