---
title: "Acessing shared directories through terminal."
date: 2009-10-07
forum: New to Ubuntu
---

### Post by jezdawgz on 2009-10-07
Hello there,
I was wondering if any of you know how to access shared directories (eg. smb://jezdawgz/hello/) through the Ubuntu Terminal. 
I was unsuccessful in reaching this directory by using the 'cd' command.

Thanks in advance,
Jeremy.

---

### Post by Kobalt on 2009-10-07
Is your shared directory mounted? Usually, Windows shares are mounted in the /media folder, check this manually before entering the path..

---

### Post by jezdawgz on 2009-10-07
I just mounted it then, but could only find cdrom and floppy drives in media.

Is there a way to access it without mounting?
Jeremy.

---

### Post by achase79 on 2009-10-07
what is it's mountpoint?  you can check it out with just the mount command

---

### Post by achase79 on 2009-10-07
Here is a way to view without mounting
[http://ubuntuforums.org/showthread.php?t=304131]("http://ubuntuforums.org/showthread.php?t=304131")

---

### Post by 3rdalbum on 2009-10-07
If it is mounted in Gnome, then you need to navigate to ~/.gvfs and your mounted shares will be there.

I keep a bookmark to that location in Gnome and KDE Open/Save dialog boxes, to save time.

If the SMB share is not mounted, then you need to mount it.

---

### Post by jezdawgz on 2009-10-08
Thanks for the help everyone. 
3rdalbum's directory was accurate.

Is it possible to mount a folder through terminal?
Or even create a shared folder through terminal?

Thanks,
Jeremy.

---

### Post by Peter09 on 2009-10-08
you can create a directory with

```
mkdir <directory path><directory name>
```

if you type

```
man mount
```

you will see the manual page for the mount command

---

### Post by jezdawgz on 2009-10-08
> **Peter09 said:**
> you can create a directory with

```
mkdir <directory path><directory name>
```if you type

```
man mount
```you will see the manual page for the mount command

Thanks Peter, but is there a way to turn a directory in to a shared one (on the network) through terminal?
Jeremy.

---

### Post by 3rdalbum on 2009-10-08
You can create a shared folder through the terminal, but it involves editing the smb.conf file and then restarting the Samba service. Let's just say, I don't want to venture down that route when there's a graphical way (system-config-samba) and I'm running X :-)

You can mount a shared folder through the terminal, using the "smbfs" filesystem type. I can't advise further because I've never done this. I just get Gnome to mount it for me into ~/.gvfs.

---

### Post by jezdawgz on 2009-10-08
> **3rdalbum said:**
> You can create a shared folder through the terminal, but it involves editing the smb.conf file and then restarting the Samba service. Let's just say, I don't want to venture down that route when there's a graphical way (system-config-samba) and I'm running X :-)

You can mount a shared folder through the terminal, using the "smbfs" filesystem type. I can't advise further because I've never done this. I just get Gnome to mount it for me into ~/.gvfs.
Ah ok.
Thanks for clearing this up 3rdalbum, you've been a great help.

Jeremy.

---

### Post by Peter09 on 2009-10-08
Have you tried just selecting an appropriate folder in nautilus and selecting the sharing options in the right click menu?

---

### Post by alphaniner on 2009-10-08
Mounting a shared folder through the terminal can sometimes be tricky; I think there are several how-to's about it.  But accessing a shared folder is pretty easy using **smbclient**:

```
smbclient \\\\#.#.#.#\\FolderName
```

If the folder needs authentication and the username is different from yours, use

```
smbclient \\\\#.#.#.#\\FolderName -U username
```

---

