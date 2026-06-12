---
title: "accessing files in windows"
date: 2011-08-03
forum: New to Ubuntu
---

### Post by shawnic on 2011-08-03
I accidentally uninstalled python and FUBAR'd my ubuntu harddrive.
I need to transfer my pictures and important documents to either my windows harddrive or a flashdrive.

I have looked around and can't find a program that will let me access my ubuntu harddrive in windows.
I can't figure out how to transfer my files in ubuntu without graphics.

Please help! I don't want to lose my personal files when i re-install ubuntu.

---

### Post by amjjawad on 2011-08-03
> **shawnic said:**
> I accidentally uninstalled python and FUBAR'd my ubuntu harddrive.
I need to transfer my pictures and important documents to either my windows harddrive or a flashdrive.

I have looked around and can't find a program that will let me access my ubuntu harddrive in windows.
I can't figure out how to transfer my files in ubuntu without graphics.

Please help! I don't want to lose my personal files when i re-install ubuntu.

Just boot from ANY LiveCD or LiveUSB, access your /home folder and copy-paste your important files, period.

:)

---

### Post by skatinjj on 2011-08-03
Do you have copy of the ubuntu livecd burned?  You can just boot into that to get a GUI to copy over your files.

---

### Post by skatinjj on 2011-08-03
> **amjjawad said:**
> Just boot from ANY LiveCD or LiveUSB, access your /home folder and copy-paste your important files, period.

:)

Always beat to the punch XD

---

### Post by shawnic on 2011-08-03
I booted from a liveUSB but I cant copy the files over because I don't own them.
This may sound like a n00b question but how do i take ownership of them

---

### Post by skatinjj on 2011-08-03
For now it is probably easier to just use sudo and change ownership once you got a fresh install (assuming you are planning a fresh install).  To do this, open the terminal and type:

```
sudo nautilus
```

That will open the nautilus file manager with sudo permissions so you can copy everything over.

I believe if you have the same username as your old install, permissions and ownership shouldn't be a problem.  But if it is:

Once you are in a new install, open the terminal and navigate to where the folder(s) you backed up and type:

```
sudo -R chown /path/to/folder username
```

Replace /path/to/folder with the directory path.  That will change all ownership over to the username you type in.

---

### Post by shawnic on 2011-08-03
I can't move the files to the backup because I don't own them.
I'm trying to back them up before I do a fresh install.

---

### Post by skatinjj on 2011-08-03
Should be able to move whatever you want once you use

```
sudo nautilus
```

Did you try that yet?

---

### Post by shawnic on 2011-08-03
```
it still says i don't have permission.
```

nevermind. I got it. thank you all very much.

---

### Post by skatinjj on 2011-08-03
Glad we could help =)

Also, this is a reason I have a separate home partition and a backup using rsync that runs incremental backups daily.

---

