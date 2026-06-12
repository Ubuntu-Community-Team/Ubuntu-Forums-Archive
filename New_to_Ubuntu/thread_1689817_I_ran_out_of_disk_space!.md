---
title: "I ran out of disk space!"
date: 2011-02-17
forum: New to Ubuntu
---

### Post by nathasar on 2011-02-17
I have a full 8.5 GB HD and an empty 6.8 GB HD. Can I move my swap over to the empty HD?

---

### Post by psusi on 2011-02-17
You are better off moving some of your FILES over to the other drive.

---

### Post by Quackers on 2011-02-17
If you've got 2GB of ram or more, and don't use hibernate, you might be able to do without swap altogether. You would need to delete the swap entry from /etc/fstab too.
It is possible that booting up may be slightly slower with no swap - maybe.

---

### Post by kn0w-b1nary on 2011-02-17
Like said before, better to move files. I've freed over 100 megabytes before using the program bleachbit.
```
sudo apt-get install bleachbit
```
```
sudo bleachbit
```
Pick the options you want.

Hope this helps!

---

