---
title: "Thumbs.db"
date: 2009-06-08
forum: New to Ubuntu
---

### Post by Zopiac on 2009-06-08
Windows puts Thumbs.db files all over the place, and they really bug me while looking through my windows partition in linux. Is there a command to delete all files names 'x' so that I can just get rid of them? I don't boot into windows very often, so they won't keep reappearing.

Or, perhaps I can hide a certain filetype so that it doesnt show up in Nautilus and/or Thunar? Just a thought.

---

### Post by Celauran on 2009-06-08
Assuming they're only showing up in your home directory, you could try this:

```
find . -name Thumbs.db -exec rm {} \;
```

Execute from /home/yourusername

---

### Post by amingv on 2009-06-08
This files are created as sort of a cache for thumbnails of pictures/videos in thumbnail view.
The most effective solutions would be to disable thumbnail view in all folders or to turn off thumbnail caching on the folder's properties:

[ATTACH]116894[/ATTACH]

That should do them out permanently.

---

### Post by Zopiac on 2009-06-08
> **Celauran said:**
> Assuming they're only showing up in your home directory, you could try this:

```
find . -name Thumbs.db -exec rm {} \;
```

Execute from /home/yourusername

if i execute from, say, /media/disk will it delete all in that mounted partition?

---

### Post by Celauran on 2009-06-08
```
find .
```

Starts find in the current directory and goes through all subdirectories. You could either do it from within /media/disk or simply specify the location instead of .

```
find /media/disk -name Thumbs.db -exec rm {} \;
```

---

### Post by Zopiac on 2009-06-08
> **Celauran said:**
> ```
find .
```

Starts find in the current directory and goes through all subdirectories. You could either do it from within /media/disk or simply specify the location instead of .

```
find /media/disk -name Thumbs.db -exec rm {} \;
```

cool, thanks a ton :)

---

### Post by niteshifter on 2009-06-08
Hi,

What Celauran posted may be problematic. Reason: the path. Let's make a couple of assumptions here: the Windows partition mounts in /media as WinDrive and your Windows user name is WinUser. Using find, ala Celauran as:
> find /media/WinDrive -name Thumbs.db -exec rm {} \;
will break. Classic Windows places like My Documents/My Pictures will have this path in Ubuntu:

/media/WinDrive/Documents and Settings/WinUser/My Documents/My Pictures/Thumbs.db

For Windows user John Doe the above will be:
/media/WinDrive/Documents and Settings/John Doe/My Documents/My Pictures/Thumbs.db

The problem is the space after "My" and "John", the rm command isn't going to "see" what we think it should. The rm command is going have the full path passed to it via the shell, and the shell is going to break it apart at the spaces.

Single and double quotes - anywhere in the path - will also cause failure. One might wind up deleting things unintentionally.

Safer way to do it is this:

```
find /media/WinDrive/Documents\ and\ Settings/WinUser -name Thumbs.db -type f -print0 | xargs -0 /bin/rm -f
```
will clear Thumbs.db from just your user area in the Windows partition.

Now, you might be thinking of having at it like this:
> find /media/WinDrive -name Thumbs.db -type f -print0 | xargs -0 /bin/rm -f
Note that the above will delete Thumbs.db wherever it is found - like in the Windows, System, System32, Program Files, etc. folders. Probably not what you want to do (could break some Windows stuff).

---

### Post by Celauran on 2009-06-08
Spaces in the path name haven't been a problem for me. I tested the code before posting it, and ~/temp/My Documents/Thumbs.db was deleted just fine.

---

### Post by lavinog on 2009-06-09
I am pretty sure the find command can handle spaces.
I use the exec and delete switches frequently to manage ntfs partitions.

when in doubt you can always run this first:
```
find /media/WinDrive -name Thumbs.db -exec echo {} \; 
```

This should also work:
```
find /media/WinDrive -name Thumbs.db -delete
```

---

