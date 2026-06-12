---
title: "Permissions problem"
date: 2010-08-16
forum: New to Ubuntu
---

### Post by adam_himself on 2010-08-16
So, I solved my network issue and I was finally able to move some files for back up reasons from my Macbook to my uBuntu machine.  Well, now I am not able to delete files from the folder on my uBuntu machine because I do not have permissions!

I created a folder on my desktop called "macbook_backup" and moved all kinds of images and such.  I was able to delete the images, but I had a problem moving and deleting the folder "home movies" I moved into the macbook_backup.  I checked the properties on it and it says owner is "nobody" and unknown for the most part.  I can't move it to trash or anything and it says something like "you are not the owner of this file and as such you may not delete it."  What the hell?  I thought I had admin access on here.  This is the only profile I have and it says I am an admin.

So what now?

---

### Post by Zilioum on 2010-08-16
Have you tried deleting it with sudo (root access)?
Navigate to the file you want to delete with the terminal and type:```
sudo rm "name_of_file_to_be_deleted"
```
"rm" is the command to delete files.
Before anything is deleted, you will be asked for your admin password.

---

### Post by arpanaut on 2010-08-16
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by L2U2K2E on 2010-08-16
you can use that delete command or a graphic solution is to run nautilus as a root. This can solve most permissions issues you will run into.
```
sudo nautilus
```

---

### Post by pythonscript on 2010-08-16
> **L2U2K2E said:**
> you can use that delete command or a graphic solution is to run nautilus as a root. This can solve most permissions issues you will run into.
```
sudo nautilus
```

For security reasons, I *highly recommend* that you use 
```
gksu nautilus
``` instead of *sudo*.

That's the preferred way to run *any* graphical application with root privileges. 

Also, to change the ownership of a file, try this:
```
sudo chown *username* *filename*
```. For example, I could run this command on my machine:
```
sudo chown pythonscript myfile.txt
```, which would give me ownership of myfile.txt. Then you should be able to delete it, maybe not using sudo, but definitely when using it.

---

### Post by adam_himself on 2010-08-16
Thanks a ton guys.  I really appreciate it.

I was able to remove the files using "sudo rm movie.m4v"

But, when I typed "sudo rmdir home_movies" it says the directory is not empty.  I checked and double checked and there are no files in it.  I even have hidden files shown.

I was able to delete it through my desktop (GNOME) and move it to trash with no problems.

Why would it not let me use the rmdir command?

---

### Post by mapes12 on 2010-08-17
> **L2U2K2E said:**
> you can use that delete command or a graphic solution is to run nautilus as a root. This can solve most permissions issues you will run into.
```
sudo nautilus
```

The command I would use is ```
gksudo nautilus
```because this is a GUI application.

**IMPORTANT!** If you delete anything when in gksudo nautilus remember to hold down the shift key at the same time as pressing delete. If you don't then all that will happen is that the stuff you are deleting will be moved to roots trash bin and you will wonder why you are losing disk space. If you already have this problem then post back for a solution.

Mark

---

