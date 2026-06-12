---
title: "preferred app. not workin"
date: 2010-03-26
forum: New to Ubuntu
---

### Post by degarb on 2010-03-26
Firefox with every update is becoming less responsive and a pig. Crashing frequently, locking up my system.

I installed OPERA, a big improvement in every aspect.  But I cannot get html to open in Opera from nautisist. I looked through all nautist prefs and opera prefs, but not there.

I set the system>preferences> preferred applications to Opera for html.  Rebooted. But it is opening up Mozilla, and freezing the system for minute, when it could open in Opera in 2 seconds.

---

### Post by wojox on 2010-03-26
Right click on the file and select Open with other Application
Choose Opera

---

### Post by degarb on 2010-03-26
> **wojox said:**
> Right click on the file and select Open with other Application
Choose Opera

Thanks.  This works, but doesn't keep wife from locking up the system opening with Firefox.  Also, less convenient and could get old after a while.

---

### Post by da burger on 2010-03-26
Right click on an html file. Click properties. Open with. Opera.
I think that should stay until you change it back.

---

### Post by macogw on 2010-03-26
Is your wife on a different user account? It's a per-user setting.  

You could also be tricky and "sudo chmod -x /usr/lib/firefox-__/firefox"  (you'd have to look around a bit for the right path... it changes based on version of Firefox but if you do "ls /usr/lib/firefox*" it should tell you) so that Firefox *can't* run...

---

### Post by lovinglinux on 2010-03-27
You could fix Firefox - [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567)

---

