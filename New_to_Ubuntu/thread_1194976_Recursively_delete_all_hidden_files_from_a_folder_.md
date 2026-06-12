---
title: "Recursively delete all hidden files from a folder and it's subfolders?"
date: 2009-06-23
forum: New to Ubuntu
---

### Post by crazyfuturamanoob on 2009-06-23
```

**$ rm -R .***
rm: cannot remove directory `.'
rm: cannot remove directory `..'
**$rm -R .??***
rm: cannot remove `.??*': No such file or directory

```

Help :( :( :( :( :( :( :( :(

Edit: Solved.

---

### Post by Joeb454 on 2009-06-23
Try ```
rm -R ./.*
```

You have to remember that . is the current directory. But if you put ./. that implies that the file/folder is hidden **in** the current directory :)

---

### Post by Trebaruna on 2009-06-23
. and .. represent the current (.) and parent (..) directories. You cannot delete them. You can delete this and parent directories by going above them and using their name.
e.g. you're in /home/user/mydir/bla and you want to delete bla, first go up (cd ..) and then delete the directory ("rmdir bla" when empty, otherwise "rm -r bla").

EDIT: Even if you do issue rm -r .* all the files should be gone. The complaint does not mean it stops working. (Just checked quickly).

---

### Post by crazyfuturamanoob on 2009-06-23
```

**$ rm -R ./.***
rm: cannot remove `.' directory `./.'
rm: cannot remove `..' directory `./..'

```
Yes, I know what . and .. are. I don't want to delete folders nor all files, just hidden files.

---

### Post by sisco311 on 2009-06-23
```
find /path/to/dir -type f -name ".*" -delete
```;)

---

### Post by unutbu on 2009-06-23
```
find . -type f -name ".*" -delete
```
This will delete only (and all) files whose name begin with a period.

When you type "rm -R ./.*", bash gets first whack at expanding the *. So only files or directories that begin with a period get sent as an argument to rm. 

Suppose you have a hidden file located at ./test/.hidden.
Since test does not begin with a period, "rm -R ./.*" doesn't operate on the test subdirectory. So ./test/.hidden doesn't get deleted.

---

### Post by crazyfuturamanoob on 2009-06-23
> **sisco311 said:**
> ```
find /path/to/dir -type f -name ".*" -delete
```;)

Thanks :D :D :D

> **Trebaruna said:**
> 
EDIT: Even if you do issue rm -r .* all the files should be gone. The complaint does not mean it stops working. (Just checked quickly).

False.

---

### Post by DouglasAWh on 2011-06-02
> **unutbu said:**
> ```
find . -type f -name ".*" -delete
```
This will delete only (and all) files whose name begin with a period.


I'm confused.  Where's the recusiveness in that?

EDIT: I figured out my profile.  I needed *.* for what I was doing...well, not that specifically, but that's the general idea of my failure.

---

### Post by AlexanderDGreat on 2011-07-25
I was able to read an archived forum on how to delete HIDDEN FILES recursively and safely. I just can't remember the site, but it was really helpful!

But at the end this is what everyone agreed:

```
cd /home/myuser/myfiles/ ; cp -pr * .??* /home/myuser/backups/ ; rm -rf * .??*
```

1. The first (cd) command will go the folder you want.

2. The 2nd (cp) command will back up ALL your files from #1 to a backup folder.

3. Finally, the 3rd (rm) will remove ALL your files, hidden and not hidden, from #1.

Neat.

---

### Post by uRock on 2011-07-25
Necrothread Closed

---

