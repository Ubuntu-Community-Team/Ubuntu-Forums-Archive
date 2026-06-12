---
title: "Rescuing USB drive"
date: 2009-01-20
forum: New to Ubuntu
---

### Post by Clever_User_Name on 2009-01-20
In a moment of sheer idiocy and desperation while trying to reformat a thumb drive, I went to "properties," opened the "drive" tab and typed "FAT16" in the "File system" space under "Settings." Now (obviously) I am unable to mount the drive. Is there any way to save it or should I just throw it out?

Edit: Also, running Ubuntu 8.10 if that's relevant

---

### Post by mc4man on 2009-01-20
In a terminal go
```
gconf-editor
```

when it opens go system -> storage -> drives and you should see a listing for it. highlight and in box on right you should see the entry you made.
Right click on it -> 'edit key' and remove your entry completely (right click on the fs_override and choose Unset,
Make sure the entry is blank.

---

### Post by Clever_User_Name on 2009-01-20
Thanks for the help. When I open gconf-editor there is no drives folder (See atachment). Dowloading gparted right now but I'd prefer not to have to wipe it.

---

### Post by mc4man on 2009-01-20
**Don't touch **the one your showing, what's listed under the volumes tab? (in properties of any drive you can edit both 'drive' or 'volume'

Here, I just did what you say you did using volume, this is what your looking for

---

### Post by Clever_User_Name on 2009-01-20
one folder, _org_freedesktop_Hal_devices_volume_uuid_0000_02F7 containing one file, fstype_override

---

### Post by mc4man on 2009-01-20
right click on the fs_override and choose Unset, the **complete entry** should disappear, then plug your drive back in and see

Edit if everythig doesn't go away r. click and Unset again

---

### Post by Clever_User_Name on 2009-01-20
Worked wonderfully. Thanks so much for saving me from my own idiocy.

---

### Post by mc4man on 2009-01-20
Great, now you know pretty much nothing good can come from editing the properties of a volume or drive. (but can be fixed

---

