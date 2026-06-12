---
title: "ROOT user privileges"
date: 2009-03-28
forum: New to Ubuntu
---

### Post by ozark_hillbilly on 2009-03-28
Where do I assign myself for ALL PERMISSIONS?

Problem: files in floppy drive are owned by "root" and I cannot delete them.

I went into System>Admin>Users&Groups selected my account and went to Advanced and selected Main Group and changed it to root.

Still can't delete floppy files.

I have administrator privileges which I thought would give me ability to do what I want (right or wrong).

Ed

---

### Post by freak42 on 2009-03-28
use a root nautilus (file browser) instance

hit alt-f2 and enter

gksudo nautilus

with this you can delete all files everywhere (be careful)

hth

---

### Post by SunnyRabbiera on 2009-03-28
You may also want to install nautilus-gksu

---

### Post by ozark_hillbilly on 2009-03-28
> **SunnyRabbiera said:**
> You may also want to install nautilus-gksu

i installed nautilus-gksu thru synaptic pkg mgr.

Went into terminal mode and invoked nautilus program.

Looking at floppy drive files and attempting to modify file permissions or send files to Trash still not working. 

Error code on changing owner:

Sorry could not change the owner of xyz file.
Error setting owner: Read-only file system,

Also when I right click on file 'move to Trash' is not an option; lettering is at half intensity.

This was all done under nautilus which i thought allowed you to do whatever you wanted as far as removing/renaming/moving ANY file.

???

---

### Post by nisaky on 2009-03-28
Maybe you should try gksudo nautilus as freak42 said, and change permissions of files. THEN CLOSE THAT NAUTILUS! IT CAN CRASH YOUR SYSTEM VERY EASILY! If you copy and paste with gksudo nautilus, root will be owner of that files. 

Or you can do it in console by writing:
"cd youeflopy (/media/something) 
sudo chmod -R 777 *"
So all files will be read/write and create/delete for all users.

---

### Post by ozark_hillbilly on 2009-03-28
tried gksudo nautilus as well....

there is something about the error message: READ ONLY FILE SYSTEM.

Will file permissions change if the disk format is non-Linux based? 

does this error message when invoking nautilus point to problem:

eld@House:/media/floppy0$ gksudo nautilus
Initializing nautilus-share extension
seahorse nautilus module initializedNautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


** (nautilus:7352): WARNING **: Unable to add monitor: Operation not supported

---

### Post by Dr Small on 2009-03-28
> **nisaky said:**
> THEN CLOSE THAT NAUTILUS! IT CAN CRASH YOUR SYSTEM VERY EASILY!

That's really throwing things out of proportion.

---

### Post by The Cog on 2009-03-28
If it's a readonly filesystem then even root cannot delete the files. I can think of two reasons it might be readonly: Either the floppy has the write-protect tab set to protect, or it's an NTFS filesystem that wasn't shut unmounted cleanly last time. The command **mount** should display some useful info.

---

### Post by ozark_hillbilly on 2009-03-28
Cog,

result of 'mount'

/dev/fd0 on /media/floppy0 type vfat (rw,nosuid,nodev,utf8)

write protect tab is not set on floppy disk.

---

### Post by freak42 on 2009-03-28
As a workaround you might want to copy the files off the floppy (the ones you want to keep) , reformat the floppy and put them back?

hth

---

