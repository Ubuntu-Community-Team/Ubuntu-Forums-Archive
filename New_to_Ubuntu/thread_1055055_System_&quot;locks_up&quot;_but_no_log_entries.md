---
title: "System &quot;locks up&quot; but no log entries?"
date: 2009-01-30
forum: New to Ubuntu
---

### Post by moody_mark on 2009-01-30
A couple of times today when my laptop goes into screensaver for a while and I leave it for say 15mins. I cant seem to get any response out of it. The screensaver motion is stalled and there is no response to mouse clicks and / or the keyboard.

I have to use the ALT+SYSRQ_REISUB to reboot the PC. I tried CTRL+ALT+F1 and also CTRL+ALT+BACKSPACE but nothing.

I checked all logs in /var/logs/ and nothing that looks suspicious.

Q1: is there another key combination to get a prompt without rebooting?

Q2: im suspicious an application is hogging all the resources but unless i get a command prompt i cant tell, is there any other logs that might show this?

---

### Post by SteveDee on 2009-01-30
You could try running System Monitor as discussed here: [http://ubuntuforums.org/showthread.php?t=1046592](http://ubuntuforums.org/showthread.php?t=1046592)

Some of the screen savers are power hungry. Either disable or set for blank screen, and see if your problem goes away.

---

