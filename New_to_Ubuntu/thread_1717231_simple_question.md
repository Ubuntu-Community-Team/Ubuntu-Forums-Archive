---
title: "simple question"
date: 2011-03-29
forum: New to Ubuntu
---

### Post by dphil6236 on 2011-03-29
If I'm going to back up files from a current Windows Vista machine on to an external hard drive, do a complete erase and install Ubuntu on that computer, does it matter what file system is on the external?

---

### Post by donkyhotay on 2011-03-29
You want it to be compatible with both the old system as well as the new system. If the old system can't read the partition you won't be able to backup to it, if the new system can't read the partition you won't be cable to recover from it. So you need to know what file system the old system is compatible with and what the new file system will be (or at least compatible with). When in doubt, NTFS is usually the best choice for dealing with windows systems since that is what windows uses natively (though of course linux is different).

---

### Post by nothingspecial on 2011-03-29
Not unless you ever want to use it with windows again.

If you do choose a windows compatible file system.

If you are going 100% linux, use ext3 or 4

---

### Post by wormyblackburny on 2011-03-29
Go NTFS regardless of whether you are going all Linux. Ubuntu has no problems playing nice with NTFS whereas Window$ does not like EXT filesystems. Since it is a removable device, you may as well make sure you can use it with either OS.

---

### Post by dphil6236 on 2011-03-29
That's where my confusion was. I am not going back to windows and have no other windows computers so I guess I should go with NTFS to pull the data off the windows machine then after I drop it onto the newly revamped Ubuntu computer I can reformat it to EXT and use it as a backup drive for all my linux systems

---

