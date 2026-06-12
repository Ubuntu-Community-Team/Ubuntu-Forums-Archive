---
title: "How can an user mount without fuse an IMG made with dd of DVD ?"
date: 2010-09-20
forum: New to Ubuntu
---

### Post by honeybear on 2010-09-20
Hello,

I know cdemu, fuse for fusermoutn and so on... 

can a simple script make the operation of seeing the data of all img. 

there is isomaster but it is X11 and not for DVD :(
isomaster - A graphical CD image editor

---

### Post by Joe of loath on 2010-09-20
What about ```
mount image.img /mnt
```?

---

### Post by honeybear on 2010-09-23
> **Joe of loath said:**
> What about ```
mount image.img /mnt
```?

- well, sorry but mount is a sudo / su / root thing. I dream about something for all kind of users (sthg like isomaster for everyone, - it doesnt required su nor fuse

---

### Post by Joe of loath on 2010-09-23
Ah, I see what you want to do now.

AFAIK there's no way to do it without sudo/admin rights. You might be able to give a user permission to use mount, but I'm not sure how you'd go about doing that.

---

### Post by srs5694 on 2010-09-23
> **Joe of loath said:**
> What about ```
mount image.img /mnt
```?

That won't work as-is, but it's close; you need to add "-o loop" right after "mount". The "loop" kernel module must also be loaded.

Since the OP wants this to be an any-user sort of thing, one option would be to create an /etc/fstab entry like this:

```

/foo/image.iso    /media/foo     auto      noauto,loop,users    0 0

```Create the mount point /mnt/foo, create the /foo directory and give it 0777 permissions, and then any user who copies or links an image file to /foo/image.iso will be able to mount it at /media/foo by typing "mount /media/foo".

This particular configuration is a bit awkward and is not very multi-user-friendly -- two users can't mount different image files at the same time. For that matter, even one user can't mount multiple image files at once. If you've got just a few users, you could set up a similar configuration for each user -- say, to mount /home/fred/image.iso at /home/fred/image, /home/judy/image.iso at /home/judy/image, and so on. This would get awkward to manage as the number of users grows, though. Perhaps an [autofs]("https://help.ubuntu.com/community/Autofs") setup would be useful for this sort of thing, but I haven't looked into the details of doing that.

---

