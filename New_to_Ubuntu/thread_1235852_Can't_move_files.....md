---
title: "Can't move files...."
date: 2009-08-09
forum: New to Ubuntu
---

### Post by Jim2029 on 2009-08-09
I'm trying to run OpenTTD (Open Transport Tycoon Deluxe) and I have to copy 5 file from the original game to the OpenTTD data folder. I have found the folder, but when I goto move the files there is get an error saying I don't have permission. I don't know terminal yet... so I'm just trying to drag them over there....

What should I do?

---

### Post by credobyte on 2009-08-09
In terminal:
```
gksudo nautilus

```

---

### Post by Jim2029 on 2009-08-09
> **credobyte said:**
> In terminal:
```
gksudo nautilus

```

Didn't work. I typed it in, put in my password. Then this showed up:

jim@jim-laptop:~$ gksudo nautilus
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

 Then went to copy the files into the directory and says error Permission denied. I'm trying to move the files from a folder on my desktop to usr/share/games/openttd/data

---

### Post by jauntyjackalope on 2009-08-09
I have no idea if this will make a difference, but you could try this instead...It's what I always use :) ```
gksu nautilus
```

---

### Post by relay_man on 2009-08-09
It may not be necessary at all to know the terminal.
Many times the terminal is quickest way to do something, but rarely is it the only way.

If you have the folder of interest on your desktop, I suggest that you right click on it, and select properties.  In the box that opens, select the permissions tab.  In the permissions tab the owner of that folder will be listed at the top and underneath the owners permissions.
Next will be listed the group name and the groups permissions. 
Last will be others and their permissions.
Post back with what you find and we will proceed from there.

---

### Post by Jim2029 on 2009-08-09
> **jauntyjackalope said:**
> I have no idea if this will make a difference, but you could try this instead...It's what I always use :) ```
gksu nautilus
```

This is what I get with that command...

jim@jim-laptop:~$ gksu nautilus
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


--- Hash table keys for warning below:
--> file:///root

(nautilus:4448): Eel-WARNING **: "nautilus-metafile.c: metafiles" hash table still has 1 element at quit time (keys above)

(nautilus:4448): Eel-WARNING **: "nautilus-directory.c: directories" hash table still has 1 element at quit time
jim@jim-laptop:~$

---

### Post by mapes12 on 2009-08-10
Jim

Do you by any chance have a CD/DVD or something in you CD/DVD drive? If you do then remove it and have another go with ```
gksu nautilus
```

---

