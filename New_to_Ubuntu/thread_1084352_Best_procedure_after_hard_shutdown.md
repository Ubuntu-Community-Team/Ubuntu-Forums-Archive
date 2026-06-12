---
title: "Best procedure after hard shutdown?"
date: 2009-03-01
forum: New to Ubuntu
---

### Post by Orographic on 2009-03-01
Hi all,

Been using Ubunu 8.10 since about late October '08. Really love it and its my main OS now but now and then I have to do a forced hard shutdown. Its only once every month or two but its annoying. It happened today after backing up my documents via external usb drive (NTFS formatted). I unmounted the drive first (always like to do this in case of shutdown probs) then shutdown my system. It froze at that point and I had to to a reset. 

I'm very careful with my system and use UPS (battery backup) to keep everything as safe as possible but this hard shutdown issue still occurs sometimes but not often.  

Anyway, as a result, I just did an Acronis image restore (also have Clonezilla images) then restored my documents from a backup and all is fine. 

Is that the best option, to just do an image restore or is there another way? The hard shutdowns bother me as I haven't had one in Windows for a couple of years but they are more common in Ubuntu.

---

### Post by Shazaam on 2009-03-01
Better for the os than hitting the kill button...
Hold down the ALT+SysRq(PrintScreen) keys and type in-
```
reisub
```
From here...
[http://en.wikipedia.org/wiki/Magic_SysRq_key](http://en.wikipedia.org/wiki/Magic_SysRq_key)

---

