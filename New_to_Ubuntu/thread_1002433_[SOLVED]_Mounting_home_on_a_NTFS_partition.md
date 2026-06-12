---
title: "[SOLVED] Mounting home on a NTFS partition"
date: 2008-12-05
forum: New to Ubuntu
---

### Post by ernesto55 on 2008-12-05
I was wondering if it was possible to move my home partition to a NTFS partition I have created for storing media in windows xp?

---

### Post by ernesto55 on 2008-12-05
I have did further research and found an answer sorry for opening the thread.

---

### Post by theozzlives on 2008-12-05
> **ernesto55 said:**
> I have did further research and found an answer sorry for opening the thread.

What was  the  answer?

---

### Post by Xeneth on 2011-06-14
Old post I know, and I do not know if it is the same as the answer OP has, but here's mine.

mount --bind

This will make what is saved in one directory be saved else-ware.  For me, this was because my main storage was NTFS because it had to be readable in my Windows 7.  So in /etc/fstab, I mounted the NTFS partition as normal, done for me by Ubuntu 11.04:
```

# /windows was on /dev/sda3 during installation
UUID=FC843ED0843E8D60 /windows        ntfs    defaults,umask=007,gid=46 0      $

```Then I set the base storage folders to save their instead.

```

/windows/user/Documents/       /home/user/Documents/   none    bind  0  0
/windows/user/Downloads/       /home/user/Downloads/  none    bind  0  0
/windows/user/Pictures/        /home/user/Pictures/   none    bind  0  0
/windows/user/Videos/          /home/user/Videos/   none    bind  0  0
/windows/user/Music/           /home/user/Music/   none    bind  0  0

```This is all In /etc/fstab so it gets redone on boot.



Edit:  I posted because while I was searching for the answer, I got here, and I wanted to make sure this post was useful to other's searching.

---

