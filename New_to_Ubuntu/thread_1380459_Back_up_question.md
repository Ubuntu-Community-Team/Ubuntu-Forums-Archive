---
title: "Back up question"
date: 2010-01-13
forum: New to Ubuntu
---

### Post by weichimaster on 2010-01-13
Hi

I just installed "Simple Backup Suite 0.10.4" via Synaptic. It backs my files up successfully to /var/backup.

I want to save the back ups to a USB. However, the directory above is read only unless I'm logged in as root.

How do I do this? The permissions on the file give me read/write access if I'm logged in as root.

I thought
```
sudo cp -r /var/backup /dev/sdf
```might work, but I'm wary of trying it in case I've got it 'orribly wrong...

---

### Post by Norm24 on 2010-01-13
Rsync is a great backup program.If you like a gui(as I do) Grsync is the way to go.

---

### Post by patros on 2010-01-13
> **weichimaster said:**
> Hi

I just installed "Simple Backup Suite 0.10.4" via Synaptic. It backs my files up successfully to /var/backup.

I want to save the back ups to a USB. However, the directory above is read only unless I'm logged in as root.

How do I do this? The permissions on the file give me read/write access if I'm logged in as root.

I thought
```
sudo cp -r /var/backup /dev/sdf
```might work, but I'm wary of trying it in case I've got it 'orribly wrong...

You should be running something like
```
cp -r /var/backup /media/usblabel
```
Just have a look in /media when you have your usb drive inserted to see exactly what it's called. Also no need to run as root if you have read access to it.

You could also configure the Simple Backup Suite to backup straight to the usb drive.

---

### Post by weichimaster on 2010-01-13
Thanks to both or you for the help so far. I'll probably use Grysync in the future, but I'm trying to get the hang of command lines.

 For some reason, simple backup suite doesn't manage to output to this USB (hence the copying plan.)

I don't actually have read access to /var/backup, so I think I do need the sudo.

Trying this:
```
sudo cp -r /var/backup /media/USB  
```
copied some folders over. However, the files are called things like .trash-1000 and are all empty! And the contents of my backup are:
```

sudo ls /var/backup
2010-01-13_01.11.56.447437.matt-desktop.ful
2010-01-13_01.14.01.863444.matt-desktop.inc
2010-01-13_01.25.05.322922.matt-desktop.inc
2010-01-13_01.38.25.255855.matt-desktop.inc
2010-01-13_22.10.13.263101.matt-desktop.inc
2010-01-13_22.23.26.856708.matt-desktop.inc

```This isn't empty. Could it be an issue with the USB stick? (It contained windows files before this.)

I'll try changing the permissions (temporarily) on/var/backup and then see if I can copy in Nautilus.

---

### Post by weichimaster on 2010-01-13
OK - my plan worked. 

I temporarily gave myself full permissions to /var/backup and everything in it, which let me cp it to USB.  I then changed permissions back to their starting values. It's a bit of a faff, though, so I'll different approaches in the future.

---

### Post by patros on 2010-01-13
> **weichimaster said:**
> OK - my plan worked. 

I temporarily gave myself full permissions to /var/backup and everything in it, which let me cp it to USB.  I then changed permissions back to their starting values. It's a bit of a faff, though, so I'll different approaches in the future.

No need to give yourself full permissions, you could just give yourself read permissions, but you couldn't do much damage with write permissions as well. Or change the group to admin (which I assume you are a member of).

---

