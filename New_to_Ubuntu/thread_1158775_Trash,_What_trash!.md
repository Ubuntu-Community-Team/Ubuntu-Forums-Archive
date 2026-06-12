---
title: "Trash, What trash?!?"
date: 2009-05-14
forum: New to Ubuntu
---

### Post by dan1973 on 2009-05-14
Morning all,

Have jaunty installed on dual boot system with windoze vista (not WUBI)

Just trying to get things straight at the moment, but have noticed that when i move items to the trash and subsequently look in there, surprise surprise, there's nothing there.

Even the trash icon does not fill up with rubbish.

Does anyone know what is going on? Or how to fix?

Many thanks,

Dan

---

### Post by AndThenWhat on 2009-05-14
Check this thread out:

[http://ubuntuforums.org/showthread.php?t=206792](http://ubuntuforums.org/showthread.php?t=206792)

Sounds like it might be possible to fix it by right-click'ing on it and removing it from the panel then re-adding it (right-click -> Add to Panel).

---

### Post by mprince on 2009-05-14
It could be that the files are being sent to your /root trash. Ubuntu actually has 2 trashes.

The root trash gets items that are deleted while using the command 'gksudo nautilus'.

```
/root/.local/share/Trash
```

You can check and see if there is anything in the root trash by typing this command in a terminal:

```
sudo dir --size /root/.local/share/Trash/files
```

or this will tell how much space is being used:

```
sudo du -hs /root/.local/share/Trash
```


Also, removable drives have their own trash, too.

---

