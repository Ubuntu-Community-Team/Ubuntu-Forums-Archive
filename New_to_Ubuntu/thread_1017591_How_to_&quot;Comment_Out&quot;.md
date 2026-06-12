---
title: "How to &quot;Comment Out&quot; ?"
date: 2008-12-21
forum: New to Ubuntu
---

### Post by imjscn on 2008-12-21
I need to edit /etc/inittab and comment out tty2,tty3, and tty4, leaving tty1. 
This is original lines in inittab:

> 
1:12345:respawn:/bin/bash -login >/dev/tty1 2>&1 </dev/tty1
2:234:respawn:/bin/bash -login >/dev/tty2 2>&1 </dev/tty2
3:234:respawn:/bin/bash -login >/dev/tty3 2>&1 </dev/tty3
4:234:respawn:/bin/bash -login >/dev/tty4 2>&1 </dev/tty4


I don't know where is the commented words , > or / ?   How can I comment out?

---

### Post by abn91c on 2008-12-21
# in front of the line

---

### Post by Hospadar on 2008-12-21
The convention for linux configuration files is to comment out with #
Many programming languages use a double slash //
Shell scripts also use #

---

### Post by imjscn on 2008-12-21
But in my quoted codes, you can see there's no # or //
Please check my code again?

---

### Post by ajcham on 2008-12-21
> **imjscn said:**
> But in my quoted codes, you can see there's no # or //
Please check my code again?

That's because nothing is commented out yet. You need to use the # symbol to comment out lines.

---

### Post by abn91c on 2008-12-21
> **imjscn said:**
> But in my quoted codes, you can see there's no # or //
Please check my code again?
here is an example #   2:234:respawn:/bin/bash -login >/dev/tty2 2>&1 </dev/tty2

---

### Post by imjscn on 2008-12-21
Thanks! My fault- I thought it was commented and I need to remove the comment :-)

---

### Post by ajcham on 2008-12-21
> **imjscn said:**
> Thanks! My fault- I thought it was commented and I need to remove the comment :-)

Ah, I see.  No, commenting out means turning a line into a comment so that it is ignored.  This is preferable to deleting the line as, should you ever need to restore it, you can just remove the #, rather than having to remember/look up what to put back in.

---

### Post by handydan918 on 2008-12-21
FYI there is another common "comment" character. The semi-colon is used in Debian config files (Samba?) IIRC.

---

