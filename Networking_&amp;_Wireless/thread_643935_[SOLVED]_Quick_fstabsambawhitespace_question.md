---
title: "[SOLVED] Quick fstab/samba/whitespace question"
date: 2007-12-18
forum: Networking &amp; Wireless
---

### Post by zyberwoof on 2007-12-18
I'm trying to add lines to fstab on my xubuntu box to access a share on my Windows machine.  I have two lines that look like:

```
//mediacenter/my music   /media/music     smbfs        username=xxxx,password=xxxx   0   0
//mediacenter/tv         /media/tv        smbfs        username=xxxx,password=xxxx   0   0
```

Next, I run ```
sudo mount -a
```.  The second line mounts fine, but the first does not.  The output is:```
[mntent]: line 12 in /etc/fstab is bad
```


I am assuming that the reason is because the Windows share has white space between "my" and "music".  Is there a special syntax for the fstab file for this, or what else do I need to do?

---

### Post by brennydoogles on 2007-12-18
I would try ```
//mediacenter/my\ music   /media/music     smbfs        username=xxxx,password=xxxx   0   0
```
and see if that works. That's usually how you escape whitespace.

---

### Post by zyberwoof on 2007-12-18
> **brennydoogles said:**
> I would try ```
//mediacenter/my\ music   /media/music     smbfs        username=xxxx,password=xxxx   0   0
```
and see if that works. That's usually how you escape whitespace.

Nope, that doesn't do it.  Thanks for the suggestion though.

---

### Post by jazty on 2008-01-31
In fstab entries you need to use a special character code for space, which is "\040" without the quotes.

try the following out:
```

//mediacenter/my\040music   /media/music     smbfs        username=xxxx,password=xxxx   0   0

```

---

