---
title: "how to change the permissions for my second hard drive"
date: 2008-12-03
forum: New to Ubuntu
---

### Post by cnaqe1 on 2008-12-03
i tried to save some videos to my second hard drive but i couldn't cause of the permissions. i was told that i was not the owner so i couldn't change or add anything. i need help.

---

### Post by sambarusty on 2008-12-03
I would try to su into the term, then umount the drive, then mount -o rw "drive_name"

---

### Post by theozzlives on 2008-12-03
```
sudo chown [username] /dev/sdb (or whatever the name)
```

---

### Post by kpkeerthi on 2008-12-03
> **cnaqe1 said:**
> i tried to save some videos to my second hard drive but i couldn't cause of the permissions. i was told that i was not the owner so i couldn't change or add anything. i need help.

How are you mounting this drive? Auto-mounted or through FSTAB (post the content)? 

What is the filesystem type of the drive?

---

### Post by cnaqe1 on 2008-12-03
> **sambarusty said:**
> I would try to su into the term, then umount the drive, then mount -o rw "drive_name"

can you explain it alittle more i'm still getting use to the terminal

---

### Post by nhasian on 2008-12-03
cnaqe1,

in a terminal could you use please post the output of

```
cat /etc/fstab
```

---

### Post by Wickd on 2008-12-03
Well there is an easier way of doing this:

1) Open a terminal and type: sudo Nautilus
2) Mount the drive and go to properties
3) Ubder the permissions tab change the Owner to your username
4) close

That should fix your problem :)

Cherio

---

### Post by m_l17 on 2008-12-03
Here are some links about the terminal and permissions.

Using the Terminal:

[https://help.ubuntu.com/community/UsingTheTerminal]("https://help.ubuntu.com/community/UsingTheTerminal")

User management:

[https://help.ubuntu.com/8.04/serverguide/C/user-management.html]("https://help.ubuntu.com/8.04/serverguide/C/user-management.html")

Permissions:

[https://help.ubuntu.com/community/FilePermissions]("https://help.ubuntu.com/community/FilePermissions")

---

### Post by nhasian on 2008-12-04
that works too.  i guess there's more than one way to skin a cat.

> **Wickd said:**
> Well there is an easier way of doing this:

1) Open a terminal and type: sudo Nautilus
2) Mount the drive and go to properties
3) Ubder the permissions tab change the Owner to your username
4) close

That should fix your problem :)

Cherio

---

### Post by Logan 1229 on 2009-01-18
> **Wickd said:**
> Well there is an easier way of doing this:

1) Open a terminal and type: sudo Nautilus
2) Mount the drive and go to properties
3) Ubder the permissions tab change the Owner to your username
4) close

That should fix your problem :)

Cherio

Than you Wickd! This was the answer I was looking for in order to set up a back up drive that I had been unable to save to! And the learning continues...

---

