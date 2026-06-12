---
title: "how to remove a DIR"
date: 2010-07-14
forum: New to Ubuntu
---

### Post by bj218 on 2010-07-14
How do I remove a Directory? I have a dir. called "home.bak" that I want to remove It is located "/home/home.bak/bill!!

root@bill-desktop:/home/bill# rmdir /home/home.bak/bill
rmdir: failed to remove `/home/home.bak/bill': Directory not empty
root@bill-desktop:/home/bill# rmdir --ignore-fail-on-non-empty /home/home.bak/bill
root@bill-desktop:/home/bill#

---

### Post by darolu on 2010-07-14
Try with:
```
$ rm -rf /home/home.bak/bill
```
Be careful, it's a powerful command, "-r" stands for "recursive" so it will remove the directories and their contents recursively; "-f" stands for "force", it will ignore nonexistent files and won't prompt.

By the way, it is **not** wise nor recommended to be doing stuff as root; use sudo always.

---

### Post by nmaster on 2010-07-14
rm -rf /home/home.bak/bill

---

### Post by KdotJ on 2010-07-14
Use this command very carefully! Be careful not to add extra spaces in it by mistake

---

### Post by The Cog on 2010-07-14
If the directory is empty, **rmdir home.bak** would do it. That's safer than **rm -rf** because it refuses if the directory is not empty, but it's also much less useful for the same reason.

---

### Post by bj218 on 2010-07-14
This worked just greate THANK YOU. I will also take your advice & use sudo in the future.

---

### Post by Ctrl-Alt-F1 on 2010-07-14
> **darolu said:**
> 
By the way, it is **not** wise nor recommended to be doing stuff as root; use sudo always.
Debatable, but according to the Ubuntu philosophy this is correct.  For the beginner this is true mostly because sudo will timeout.

---

### Post by philinux on 2010-07-14
> **bj218 said:**
> This worked just greate THANK YOU. I will also take your advice & use sudo in the future.

Using sudo is just the same. Be very careful with that command you can nuke your system. Much safer to instal nautilus-gksu and use nautilus itself.

---

