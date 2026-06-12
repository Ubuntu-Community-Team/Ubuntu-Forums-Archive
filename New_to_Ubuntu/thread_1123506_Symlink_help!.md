---
title: "Symlink help!"
date: 2009-04-12
forum: New to Ubuntu
---

### Post by abhiroopb on 2009-04-12
So, I understand the principle of a symlink, in essence it creates a link to a file/folder elsewhere on the hard drive.

Now I have a folder in my hard drive where I save various config files. For example:

xorg.conf
sources.list
menu.lst
firefox bookmark backups
etc.

What I have done is created symlinks from the original files into this folder.

When I backup with DropBox ([https://www.getdropbox.com/](https://www.getdropbox.com/)) it syncs everything online all the symlinks online as the ORIGINAL files. So, essentially I have all these files backed up online.

No, my question is, when I backup to an external hard drive, do the symlinks get backed up as merely links, or do the original files themselves get backed up?

---

### Post by llamabr on 2009-04-12
Good question.  You can check this by navigating to the place where you have them backed up, in a terminal, and doing:

```
ls -l filename
```

If it's just a symlink, you will see the link.

What's the code you use to make the symlink?

---

### Post by abhiroopb on 2009-04-12
I'll be able to check this later tonight (don't have the external hard drive with me).

I didn't use any "code". I just dragged the file from its original location while holding down CTRL+SHIFT. This creates the link.

Actually I just realised that the problem can potentially get even more complicated...

The reason I am asking this symlink question is that I intend to do a CLEAN INSTALL of jaunty. After which I will copy over the files from my external hard drive (if they are the complete files and not merely links).

However, once they are copied back onto my hard drive will they be symlinks again? I.e. will the symlinks in the Config folder be symlinks or original files?

If this is getting confusing let me know and I'll try and clarify!

---

### Post by abhiroopb on 2009-04-18
Just like to point out that there is a "copy-links" command that can be added into rsync to copy symlinks as the actual things. Although be careful as sometimes the files being linked to can be very big!

---

### Post by Carl Hamlin on 2009-04-18
> **abhiroopb said:**
> However, once they are copied back onto my hard drive will they be symlinks again? I.e. will the symlinks in the Config folder be symlinks or original files?

I just did this a few days ago, and when I copied the links back to the target they came through broken. No biggie for me - I just recreated them. However, if you don't backup the linked files, then you'll be in trouble.

---

### Post by abhiroopb on 2009-04-18
Thanks...I guess I just have to remember which one's were links!

---

