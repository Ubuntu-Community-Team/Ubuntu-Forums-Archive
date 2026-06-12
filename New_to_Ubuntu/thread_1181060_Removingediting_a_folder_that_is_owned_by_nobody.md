---
title: "Removing/editing a folder that is owned by nobody"
date: 2009-06-07
forum: New to Ubuntu
---

### Post by Edgewalker_001 on 2009-06-07
How do I remove a folder that is owned by noone?

I recently had a small network problem where my computers couldn't receive windows share directories from the server, which made me copy a bunch of files to one of my computers by directly connecting to the share using the "connect to server" option in the places menu, however, the folder created is listed as being owned by nobody, and no group, which makes ubuntu refuse to remove it because I don't have permission.

How do I fix this?

PS: I'm on the first user account that I made when installing the OS, shouldn't I have permission to override any other user, or do I need to change my permissions to do that?

---

### Post by eilios on 2009-06-07
```

sudo nautilus

```
delete the folder
and exit out immediately

---

### Post by kwacka on 2009-06-07
open terminal and use ```
sudo rmdir foldername
```

If there is a complaint that the folder is not empty, use
```
cd foldername 
rm *
cd ..
```
and then the first (rmdir) command

Alternatively open terminal and type ```
sudo nautilus
```

You will then be able to delete in nautilus **BUT TAKE CARE you will be able to delete any file on your drive**

---

### Post by Edgewalker_001 on 2009-06-07
I used Nautilus, being able to delete any file isn't really a problem if you take care.

However, I didn't have the "delete" command, only "move to trash" or whatever...

I can't find the folder in my recycler though... Did I screw up majorly? XD

---

### Post by michy99 on 2009-06-07
The folder is in root's trash.```
sudo rm -r /root/.local/share/Trash
```

---

### Post by Edgewalker_001 on 2009-06-07
Thanks ^_^

---

### Post by glotz on 2009-06-07
> **eilios said:**
> ```

[color=red]**sudo nautilus**[/color]

```
delete the folder
and exit out immediately

You should use *gksudo* to run graphical apps, sudo is for command line.

---

