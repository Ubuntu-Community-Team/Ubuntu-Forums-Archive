---
title: "Untarring a file. can this be done"
date: 2010-06-21
forum: New to Ubuntu
---

### Post by newport_j on 2010-06-21
I downloaded a tar.gz file (CILK) from the Intel website. I wanted to try and use it in my work. It went into the download directory. I thought it went into the desktop directory. So when I tar -xvzf the file. Everything is fine except all directories are off the download directory, not the desktop as I would like them to be.
 
So I have to move then tar file over to the desktop directory and tar -xvzf again. However, I will still have the CILK subdirectory off the download directory7. I do not want that!
 
Is there a way to reverse the tar command and simply get the subdirectory and all of directories off my system? Is there a reverse tar command that would do the trick? Or do I have to go and remove all of this by hand?
 
 
Respectfully,
 
Newport_j

---

### Post by Penguin Guy on 2010-06-21
This should do the job:
```
OLDIFS=${IFS}; IFS='
'; rm -rf `tar -tf archive.tar.gz`; IFS=${OLDIFS}
```
EDIT: [COLOR="Red"]Be careful using an [FONT="Courier New"]rm[/FONT] command, it can be potentially dangerous.[/COLOR]

---

### Post by JKyleOKC on 2010-06-21
you could also do
```
mv downloads/tar.file.new.directory Desktop/tar.file.new.directory
```
and that should move the subdirectory and all of its files in one fell swoop. If you were running Xubuntu, you could open two file manager windows, one in Desktop and the other in downloads, and simply drag the icon for the directory that tar created from "downloads" to "Desktop" but I don't know if this works in Nautilus the way it does in thunar...

---

### Post by -kg- on 2010-06-21
> **Penguin Guy said:**
> This should do the job:
```
OLDIFS=${IFS}; IFS='
'; rm -rf `tar -tf archive.tar.gz`; IFS=${OLDIFS}
```

Note:  If you try this method, be ***_very,_ _very_ _careful_!***  The "rm" command is potentially very dangerous and can cause untold havoc with one little typo!

Be sure you know exactly what you're doing before doing it!

---

