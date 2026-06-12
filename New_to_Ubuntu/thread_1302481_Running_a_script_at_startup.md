---
title: "Running a script at startup"
date: 2009-10-27
forum: New to Ubuntu
---

### Post by Amablue on 2009-10-27
I want to map caps lock to escape, and I have a script that does so. I made an entry for it in System -> Preferences -> startup applications, and the checkbox is appropriately ticked, but every time I start up it doesn't work. As soon as I run it manually it works fine though. 

I thought putting something in that list made it run at startup. What am I missing here?

---

### Post by BbUiDgZ on 2009-10-27
> **Amablue said:**
> I want to map caps lock to escape, and I have a script that does so. I made an entry for it in System -> Preferences -> startup applications, and the checkbox is appropriately ticked, but every time I start up it doesn't work. As soon as I run it manually it works fine though. 

I thought putting something in that list made it run at startup. What am I missing here?

do u need to run your script with "sudo" to get it to work?

---

### Post by DarkDemonNT on 2009-10-27
You should insert your script link in /etc/rc.local file.

---

