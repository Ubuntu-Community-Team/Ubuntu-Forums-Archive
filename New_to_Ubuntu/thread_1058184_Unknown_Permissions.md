---
title: "Unknown Permissions?"
date: 2009-02-02
forum: New to Ubuntu
---

### Post by Heathtech on 2009-02-02
I recently upgraded from 8.04 to 8.10.
Now I am unable to create folders and such in any directory besides my home directory.  When I right click a folder and go to the "Permissions" tab, everything is grayed out and it says at the bottom: "You are not the owner, so you cannot change these permissions".
In addition, I am not able to extract, create, or delete any files from/to these locations.  I don't recall this problem in 8.04...

I tried "gksudo nautilus", but that didn't do any good.  I still can use terminal commands like "rm" and "mkdir" just fine, so long as it is preceded with "sudo".

Perhaps someone can help me resolve this issue.

---

### Post by jbrown96 on 2009-02-02
To get ownership back run the following command. Change USER to your username ```
sudo chown -R USER:USER /home/USER
```

---

### Post by Heathtech on 2009-02-02
Er, I got this message when I typed in that command:
"chown: cannot access `/home/tech/.gvfs': Permission denied"

---

### Post by jbrown96 on 2009-02-02
That's strange. Could you post the output of ```
ls -alX /home/$USER
``` so I can get a better idea of what the permissions are?

---

### Post by Heathtech on 2009-02-02
```
total 12
drwxr-xr-x 78 tech tech 4096 2009-02-02 14:49 tech
drwxr-xr-x  3 root root 4096 2008-05-26 14:58 .
drwxr-xr-x 21 root root 4096 2009-01-31 16:39 ..

```

---

