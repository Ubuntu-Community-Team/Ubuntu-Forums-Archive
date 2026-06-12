---
title: "Is it possible to burn DVD's of PartImage backup files?"
date: 2011-01-07
forum: New to Ubuntu
---

### Post by Mo (Beginner) on 2011-01-07
I made a backup of my main partition and I would like to make a DVD of it, so I won't lose my backup files. I have also an external hard disk where the backup files are now stored, but I'm afraid that if my computer crashes, that hard disk will crash too and then I lose the backup files.
Is it possible to burn DVD's of PartImage backup files?
If negative, is there another way of storing the backup files in a safe way?

Thanks

---

### Post by seawolf167 on 2011-01-07
You don't have to worry about 2 drives crashing at the same time unless you get a massive power surge or a flood or tornado or something. The easiest and safest (IMO) way to store backups is to simply backup to an external hard drive, then store that hard drive unpowered in a safe location.

I know that for Clonezilla, and I believe for PartImage as well, the backups need to all be contained in 1 media (i.e. on 1 harddrive, 1 dvd, 1 cd, etc.)

You can always split the files using a command like 

```
split -d -b 4000m /path/to/backup.tar.gz /name/of/backup.tar.gz
```

and burn them to multiple dvds, then if you ever need to restore from your backups, copy the split parts back onto an external harddrive and recombine

```
cat *tar.gz* | tar -xvpzf - -C / 
```

---

