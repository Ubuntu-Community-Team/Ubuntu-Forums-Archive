---
title: "Where is nautilus located?"
date: 2009-07-24
forum: New to Ubuntu
---

### Post by beachwood23 on 2009-07-24
What is the folder/address of nautilus?

---

### Post by wojox on 2009-07-24
In a terminal:

```
whereis nautilus
```

---

### Post by beachwood23 on 2009-07-24
thanks!

---

### Post by Nburnes on 2009-07-24
What do you mean by "Where is Nautilus?" ?

Nautilus is the entire file manager.......

[http://en.wikipedia.org/wiki/Nautilus_(file_manager](http://en.wikipedia.org/wiki/Nautilus_(file_manager))

---

### Post by beachwood23 on 2009-07-24
> **Nburnes said:**
> What do you mean by "Where is Nautilus?" ?

Nautilus is the entire file manager.......

[http://en.wikipedia.org/wiki/Nautilus_(file_manager]("http://en.wikipedia.org/wiki/Nautilus_%28file_manager"))

I know that. I'm not a complete newbie. I just didn't know where to locate it. I needed to specify what file manager to use for a program, and I didn't want to search through all of the filesystem, so this was quicker

---

### Post by cariboo on 2009-07-24
Most executables are located in /usr/bin.

---

### Post by snakeman21 on 2009-07-25
Cool, I learned a new command today!  I must say, out of all the things I love about Linux, the commands are wonderful.  They're so logical!  sudo apt-get update!  So simple!  I actually laughed when I saw "whereis nautilus"  That just makes so much sense, I never thought of it.

---

### Post by llamabr on 2009-07-25
You don't want whereris, you want 'which':

```
brock@hops:~$ which nautilus
/usr/bin/nautilus
brock@hops:~$ 
```

---

