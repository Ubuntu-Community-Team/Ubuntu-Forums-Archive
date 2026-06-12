---
title: "Three strange errors"
date: 2009-09-27
forum: New to Ubuntu
---

### Post by argos3016 on 2009-09-27
DosBox doesn't recognize the arrow keys
Nautilus doesn't preview any video and images 
I can't change permissions of my folders
Any idea?

---

### Post by halitech on 2009-09-27
are you trying to change permissions on folders inside your home folder? Folders outside your home folder don't belong to you so you shouldn't be changing permissions on them anyway unless you want to chance blowing your system up.

---

### Post by ibuclaw on 2009-09-27
> **argos3016 said:**
> DosBox doesn't recognize the arrow keys
Nautilus doesn't preview any video and images 
I can't change permissions of my folders
Any idea?
Incase you are trying to change the permissions of folders inside your home directory:
Press **Alt+F2**
Type in:
```
gksudo nautilus /home
```
and enter your password to launch the browser in super user mode.
Right-click on your **home directory** in the browser and go to **Properties**, then select the **Permissions** tab.
Ensure that your name is listed as the Owner and Group, then click **Apply Permissions to Enclosed Files**.
See attached screenshot for reference.

If you are trying to change the permissions elsewhere, please state, as chances am you are messing with the wrong stuff, and you should just leave it that way.

Regards
Iain

---

### Post by argos3016 on 2009-09-27
I can't change permission with gksu nautilus. This problem occurred after I writed to disk all folders from an a primitive backup.

---

### Post by rCXer on 2009-09-27
> **argos3016 said:**
> DosBox doesn't recognize the arrow keys
This is a bug. See [here](http://ubuntuforums.org/showpost.php?p=7839874&postcount=2).

---

### Post by grturner on 2009-09-27
have you tried chmod files from command line?

---

### Post by sandyd on 2009-09-27
i think i know the problem.
The files in the backup belong to another username that is currently not the same as the one that your using now.

Then, cd into your home directory and 
```

sudo chown -R *currentusername* *

```

---

### Post by argos3016 on 2009-09-28
Wow!God job carlee!  sudo chown -R currentusername * works!! and rCXer , god job , now I can play DOOM! Thanks to all.

---

### Post by argos3016 on 2009-09-28
But what about Nautilus, which libraries I have to install to see the preview? I remember that it was some of plugins bad, i dont know.

---

