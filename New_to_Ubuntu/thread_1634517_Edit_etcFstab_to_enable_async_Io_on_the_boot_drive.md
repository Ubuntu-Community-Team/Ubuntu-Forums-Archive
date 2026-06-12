---
title: "Edit /etc/Fstab to enable async I/o on the boot drive"
date: 2010-11-30
forum: New to Ubuntu
---

### Post by vskipper on 2010-11-30
Hi there,

I'm trying to edit my fstab to enable async I/O on the boot drive (which is a memory stick). Anyone able to help?

Below are the details of my fstab:

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sdb1       /               ext2    errors=remount-ro 0       1

Thank you.

V

---

### Post by Wobblybob on 2010-11-30
not come across this before but try this link, it looks like you just add it in the option field of the fstab. [[COLOR="Navy"]http://www.go4expert.com/forums/showthread.php?t=7416[/COLOR]]("http://www.go4expert.com/forums/showthread.php?t=7416")

---

### Post by vskipper on 2010-11-30
Sorry for the daft question but to which column would I add the option?

---

### Post by vskipper on 2010-11-30
like this:

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sdb1       /               ext2    errors=remount-ro,[COLOR=Red]async[/COLOR] 0       1

---

### Post by vskipper on 2010-11-30
it worked!!! What a difference.... recommend to everyone running Ubuntu 10.10 on flash USB drive. V

---

### Post by Wobblybob on 2010-11-30
great stuff you got there before I got back to you, well done.:) you can mark this thread as solved now.

---

### Post by vskipper on 2010-11-30
Thx very much fro your help. Sorry another daft question. How/where do mark this thread as solved?

---

