---
title: "Can't move files out of trash"
date: 2009-12-06
forum: New to Ubuntu
---

### Post by tarahmarie on 2009-12-06
I have a friend I'm doing the phone support thing for.  He's apparently deleted files on his Ubuntu box, and now cannot move them from the Trash. Any ideas why this is?  I thought it might be a permissions issue, and asked him to crack open an instance of Nautilus in root mode.  He was then unable to view the files at all in the Trash directory.  

Is it that trash is a virtual directory?  How would I go about helping him to restore those files?  There's apparently no "restore" option in the context menu for the directory.

---

### Post by hansdown on 2009-12-06
Hi tarahmarie.

Not able to help with deleting the files, but you can drag and drop the files from the trash to the desktop, etc.

---

### Post by tarahmarie on 2009-12-06
> **hansdown said:**
> Hi tarahmarie.

Not able to help with deleting the files, but you can drag and drop the files from the trash to the desktop, etc.

Actually, I wasn't looking for help DELETING the files; apparently, my friend cannot drag and drop the files elsewhere due to permissions issues.  That's where the crux of the problem lies: I could have walked him through a chmod and chown sequence in the shell, but because he doesn't know WHERE the files are located in the directory structure, I can't tell him how to navigate there and change permissions/ownership.

---

### Post by hansdown on 2009-12-06
Sorry.

---

### Post by ArgentStar on 2009-12-06
The root trash in Ubuntu 9.10 is:

/root/.local/share/Trash/files/

**EDIT:** In case anyone reading this *does* want to delete them, do one of the following:

1) open the directory with:

```
sudo nautilus /root/.local/share/Trash/files/
```

Then select everything and press SHIFT + DELETE.  If you don't press SHIFT as well, they'll just be sent right back to that same directory. :)

Or, 2) open a root terminal.  E.g.:

```
sudo gnome-terminal
```

Then, in the terminal that opens:

```
cd /root/.local/share/Trash/files/
rm -rf *
```

[COLOR="Red"]**WARNING: Careful with that last command!**[/COLOR] 

Make *sure* you're in the right directory because it will delete everything in the current directory (including subdirectories and their contents) *without warning.*

---

