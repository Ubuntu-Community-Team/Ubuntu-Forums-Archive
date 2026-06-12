---
title: "Can't click in flash games"
date: 2009-12-01
forum: New to Ubuntu
---

### Post by Space-Wolf on 2009-12-01
If I load up a flash-based game in Opera or Firefox, I can't click when I'm playing.  Any advice?

EDIT:  Actually, it seems to work in FF, just not in Opera...

---

### Post by tom.swartz07 on 2009-12-01
> **Space-Wolf said:**
> If I load up a flash-based game in Opera or Firefox, I can't click when I'm playing.  Any advice?

EDIT:  Actually, it seems to work in FF, just not in Opera...

Its a confirmed bug with the Linux version of flash. If you are using a x64 bit version of Ubuntu, then try the beta flashplayer (google 'ubuntu flash 64 10.1')

for the time being, middle click and left click to do the job.

---

### Post by Chame_Wizard on 2009-12-01
you can use the newest flash plugin via the software centre.

---

### Post by 3rdalbum on 2009-12-01
> **tom.swartz07 said:**
> Its a confirmed bug with the Linux version of flash. If you are using a x64 bit version of Ubuntu, then try the beta flashplayer (google 'ubuntu flash 64 10.1')

for the time being, middle click and left click to do the job.

You can generally click outside the Flash movie, and then your next click inside it will work.

---

### Post by herbertportillo on 2009-12-01
1. Open a Terminal (Application -> Accessories -> Terminal).
2. Type **gksudo gedit /usr/lib/nspluginwrapper/i386/linux/npviewer**
3. Add the following line BEFORE the last line of text: **export GDK_NATIVE_WINDOWS=1**
4. Save the changes.
5. Restart any open browsers.

---

