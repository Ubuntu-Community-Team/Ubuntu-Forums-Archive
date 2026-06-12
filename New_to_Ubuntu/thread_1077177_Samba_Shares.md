---
title: "Samba Shares"
date: 2009-02-22
forum: New to Ubuntu
---

### Post by theozzlives on 2009-02-22
I put some mount commands in my fstab to some shares on my server so I wouldn't have to mount everytime I restart. I've tried smbfs and cifs and both work fine, but when I shutdown or restart i get this:

> ACPID: EXITING

[*numbers*]CIFS VFS: Server not responding
[*numbers*]CIFS VFS: no response for cmd 50 mid 69

It'll pause for a long time and then shut down or restart, any ideas PLEASE?

---

### Post by quinnten83 on 2009-02-22
no clue...
btw, i saw the other post.
I usually just install ntfs-3g.and i don't have these problems.

---

### Post by theozzlives on 2009-02-22
except I'm connecting Ubuntu to Ubuntu

---

### Post by theozzlives on 2009-02-22
I think I found the answer here [http://ubuntuforums.org/showthread.php?t=293513]("http://ubuntuforums.org/showthread.php?t=293513")

---

### Post by capscrew on 2009-02-22
from the man page of [COLOR="Blue"]mount.cifs[/COLOR]>  soft
          (default) The program accessing a file on the cifs mounted file sys&#8208;
          tem  will not hang when the server crashes and will return errors to
          the user application.


Your server hangs because you have hard mounted the share.  Soft mount will stop the problem.

---

### Post by Kellemora on 2009-02-22
Hi Ozz

Besides the other suggestion, I would suggest you remove smbfs completely.

It is KNOWN to prevent shares from showing up, quite often in fact.

You can experiment yourself to see too!

Remove smbfs and install smbtree if you don't have it installed already.
In terminal, type smbtree then look to see all of your shares are showing.
Now, install smbfs and run smbtree again!
I think you will find a few of your shares are failing to show now.
Remove smbfs and your shares are back showing again.

You might also NOTE that the shares that are failing to show when smbfs is installed are also those same ones that will not automount for you!!!!!

TTUL
Gary

---

### Post by theozzlives on 2009-02-23
I already am using cifs instead of smbfs as I thought that was my problem, turned out it is a bug in samba, that's why the workaround. My shares aren't dismounting at log off, should've googled before I posted.

Let's all pray to the forum gods, "I wanna be able to mark threads as solved"!

---

