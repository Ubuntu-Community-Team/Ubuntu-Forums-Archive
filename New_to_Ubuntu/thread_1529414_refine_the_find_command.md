---
title: "refine the find command"
date: 2010-07-12
forum: New to Ubuntu
---

### Post by nnjond on 2010-07-12
Hi,

Ive tried to rsync from one ~/home on hdd a, to ~/home hdd b, using a live cd, but it returns a load of; eg:

rsync: opendir "/media/a2ab9331-effd-4855-8e0a-6c7f1a9d63b5/home/nnjond/.Skype" failed: Permission denied (13)

So i think i should fresh install and it would be convenient if i knew the refined commands to locate the saved files in /home hdd a, since 02_06_10 (not including all the hidden or deleted files), and then copy to a memory stick using the nautilus gui.

Can you help me please?

---

### Post by audiomick on 2010-07-12
Hallo.

You might find that your rsync works if you start it with sudo

```
sudo rsync
```

You can read about the options for find on the man page
```

man find
```

If you have similar permission denied problems using the nautilus route, try starting nautilus with root privileges

```
gksu nautilus
```

---

