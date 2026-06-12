---
title: "Delete backup files on HD?????"
date: 2009-07-06
forum: New to Ubuntu
---

### Post by Pappy1911 on 2009-07-06
I wish to free up some space on my HD.
I see where Simple Backup Config has placed several back ups on my HD.
Since I now back up to an external device, I want to delete the others.
It won't let me (as I probably need to log in as root), i.e. permission denied..
The files are located at /var/backup

Any help?? Thank you.

---

### Post by Tyke91 on 2009-07-06
type
```
sudo
```
before your command to get permissions
OR
```
sudo -i
``` 
to give yourself a root shell.

---

### Post by cariboo on 2009-07-06
The easiest way if you are graphically inclined is to press Alt-F2 and type:

```
gksu nautilus
```

Then navigate to /var/backup.

---

### Post by Pappy1911 on 2009-07-06
> **cariboo907 said:**
> The easiest way if you are graphically inclined is to press Alt-F2 and type:

```
gksu nautilus
```

Then navigate to /var/backup.

BINGO!!!!  Thank you all....

---

