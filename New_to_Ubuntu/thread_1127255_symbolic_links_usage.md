---
title: "symbolic links usage"
date: 2009-04-16
forum: New to Ubuntu
---

### Post by blau2009 on 2009-04-16
I have a local music folder and a music folder on a networked PC. My plan is to create a symbolic link between these two folders, so when I tell (for example) Rhythmbox to watch my local music folder it will also see the files in the network folder.

I am aware that there may be other (easier) ways to do this, but am more interested in if this is possible... :)

---

### Post by subzero316 on 2009-04-16
YES. Just mount the network folder somewhere. And create a link to that in your music folder.

---

### Post by Alekz_ on 2009-04-16
Hi blau!

I didn't understand exatly what you want, but if you want to create a sym link, take a look:

ln -s /path/you/want link_name

Simple han? :)

If you have any doubts, give us more details about what you want! 

[]'s

Alekz_

---

### Post by llamabr on 2009-04-16
Hi.  Yes, a symlink will do what you want, if rythmbox can't look at the folder you want, for some reason.

You won't break anything.  Just do it, and if you don't like it, rm the link.

---

### Post by skitching on 2009-04-16
> **Alekz_ said:**
> ln -s /path/you/want link_name

And you can also do this graphically. With Gnome for example, use the file browser and hold down ctrl and shift buttons while dragging with the mouse; a shortcut to the file that you dragged will be created in the window you dragged to. I'm sure KDE has the equivalent, but am not certain what the key combination is.

The idea of linking directories together to "unify" your different music directories sounds good to me. This is what makes symbolic links so useful..

---

### Post by blau2009 on 2009-04-16
Used the command line version but it didn't work. Link showed up as (link broken) in Nautilus. The command I used (from in my local music directory) was:

```
ln -s smb://server/shares/Music Server_Music
```

Why wouldn't that have worked?

Anyway I used the GUI and it worked perfectly! :) Now Rhythmbox sees all the music from the server as well as from the local folder. Brilliant!

EDIT: Actually I just checked the properties of the link in Nautilus and it has this as the location:

/home/toby/.gvfs/shares on server/Music

Please explain? :)

---

### Post by cariboo on 2009-04-16
When mounting shares using nautilus, it always mounts it in ~/.gvfs. It may be an Idea to automatically mount your share in /etc/fstab to a directory in /media and then use a symbolic link, eg:

```
smb://server/shares/Music /media/music smbfs  relatime  0  2
```

You may want to have a look at this [thread=288534]howto[/thread].

Jim

---

