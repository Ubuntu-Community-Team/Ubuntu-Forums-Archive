---
title: "How to sync folders in Ubuntu 10.04 LTS"
date: 2011-06-27
forum: New to Ubuntu
---

### Post by pauloz on 2011-06-27
Hello all Dropbox for Linux experts:

I've downloaded Dropbox into my Ubuntu 10.04 LTS, but I want to sync a folder that can't be moved from it's present position to the main folder in Dropbox.

Because my computer dual boots with Windows 7, I downloaded a DropboxAddon called Dropbox Folder Sync, but that is only available for Windows and I've got that up and running OK. 

Is there a way to issue a command in Terminal to sync folders and if so, what is the command? The location of the 2 folders are as follows:

/home/name/Desktop/Documents/e-Sword

and

/home/name/Dropbox/e-Sword

The first folder described above can not be moved because the program (e-Sword) will only recognise this as a sub-folder in the Documents folder. If it's missing, e-Sword automatically generates a new folder in the same location.

Thanks.

---

### Post by Paqman on 2011-06-27
You could create a symbolic link from one location to the other. The create a symlink, hold down Ctrl-Shift and drag the file to the new location. You can create a split window in the file manager to make this easier by hitting F3.

---

### Post by pauloz on 2011-06-27
> **Paqman said:**
> You could create a symbolic link from one location to the other. The create a symlink, hold down Ctrl-Shift and drag the file to the new location. You can create a split window in the file manager to make this easier by hitting F3.
Thanks Paqman - looks like it's working over both of my computers as well as both Ubuntu and Windows. Just what I wanted and it will save me a lot of time. Cheers!

---

