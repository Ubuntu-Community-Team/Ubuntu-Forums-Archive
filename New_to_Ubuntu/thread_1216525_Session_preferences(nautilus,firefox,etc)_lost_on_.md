---
title: "Session preferences(nautilus,firefox,etc) lost on logoff/restar"
date: 2009-07-18
forum: New to Ubuntu
---

### Post by rodrigor on 2009-07-18
Hi.
Every time i reboot/logoff all my settings are lost.
·Firefox can't find bookmarks, sometime crashes when i access "organize bookmarks" and does not add new bookmarks.
·nautilus forgets bookmarks and settings.
·stickypads lost.
·compiz off.
The only things that survive are background and menu modifications.

I've been searching around for a solution... this works but i have to do it every time i log in... (or boot up)...

```
sudo chown -R rodrigo:rodrigo ~/
chmod -R u+rwx ~/
chmod 600 ~/.Xauthority
```The first time this happened i lost the terminal's profiles and command history... i wasn't able to recover that stuff...

help?
thanks!

---

### Post by rodrigor on 2009-07-18
I found this in "-xsession-errors"
** (nautilus:3941): WARNING **: writing file:///home/rodrigo/Documents
 to bookmark file failed: Error writing to file: No space left on device

Yesterday i set jdownloader to shutdown when finished and when to sleep. Today the pc was off and the trouble started, i only had 120 mb left on my home folder.
Could this be the cause?
thanks!

---

### Post by Romulusj on 2009-11-01
I don't know if you still need the confirmation on this or not, but I can tell you from experience that yes, that is the cause of your problems. Because of a few file transfers, I lost all of my .torrent files, leaving weeks and in some cases months of waiting in the dirt. 
On the up side, the fix is easy. You can move or delete files from your file system and  subfolders therein. Or, resize the partition that Ubuntu uses for its file system. Moral of the story is, keep your file system clean, or find out the hard way like us, why its a good idea to do so.

---

