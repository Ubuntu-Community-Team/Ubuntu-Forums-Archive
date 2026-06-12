---
title: "stop desktop showing the home folder icons"
date: 2010-09-25
forum: New to Ubuntu
---

### Post by libihero on 2010-09-25
i tried using the x.org edgers ppa, and when i restarted my computer my desktop was showing my home folder.
i purged the ppa and restarted, and the folders were still there
i went to gconf-editor to see if "show home folder" was checked in apps>nautilus>desktop and it wasn't
i tried deleting them off the desktop but that also deleted the folder in my home file

any fix? :S

---

### Post by themusicalduck on 2010-09-25
I think I heard about this happening before.

Apparently the Desktop folder in the home folder had gotten deleted somehow. So make sure it's there and if not recreate it.

---

### Post by libihero on 2010-09-25
ur right it is gone, how do i create a new desktop folder?  Making a folder and naming it desktop didnt help lol

---

### Post by oneadvent on 2010-09-25
did u try with a capital d? it should be "Desktop"

---

### Post by libihero on 2010-09-25
ya i named it "Desktop", but it didnt change into a picture of a desktop, and i logged in and out and it didnt fix it either

---

### Post by oneadvent on 2010-09-25
found this thread, mentions gconf, which i suspect is your issue, can you try these things and let us know?

[http://ubuntuforums.org/showthread.php?t=341607](http://ubuntuforums.org/showthread.php?t=341607)

---

### Post by libihero on 2010-09-25
yes! it worked, just edited the file ~/.config/user-dirs.dirs 
THANKS!! :)

---

