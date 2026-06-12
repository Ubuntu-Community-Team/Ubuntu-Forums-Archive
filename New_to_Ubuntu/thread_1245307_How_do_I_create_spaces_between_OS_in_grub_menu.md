---
title: "How do I create spaces between OS in grub menu"
date: 2009-08-20
forum: New to Ubuntu
---

### Post by ubume2 on 2009-08-20
Using 8.04 LTS. have XP, Ubuntu 9.04,8.10 installed and in menu.lst with SDA5 as /. 

How do I  create spaces in menu.lst to make grub menu more readable?

Thanks for your help

Jerry

---

### Post by rajeev1204 on 2009-08-20
> **ubume2 said:**
> Using 8.04 LTS. have XP, Ubuntu 9.04,8.10 installed and in menu.lst with SDA5 as /. 

How do I  create spaces in menu.lst to make grub menu more readable?

Thanks for your help

Jerry


This is not possible as of now.PLease put it on launchpad as a wish.

One crazy idea would be to put a lot of dots after the kernel names :D.Might create an illusion of space? TRy such ideas.

---

### Post by Penguin Guy on 2009-08-20
You can't. But I believe you can put anything else there. Just stick [COLOR="Green"]title -[/COLOR] in between two OSs to insert a dash between them in the grub menu.

```
title		Windows XP
root		(hd0,0)
makeactive
chainloader	+1

# Ubuntu 9.04, kernel 2.6.28-11-generic
title		Ubuntu 9.04
uuid		33954389-0a03-4822-96c4-c6e5924de048
kernel		/vmlinuz-2.6.28-11-generic root=UUID=44549c7f-d040-4322-ae8c-c48ae0713952 ro quiet splash vga=794 
initrd		/initrd.img-2.6.28-11-generic
quiet

title		-

# Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
title		Ubuntu 9.04 (recovery mode)
uuid		33954389-0a03-4822-96c4-c6e5924de048
kernel		/vmlinuz-2.6.28-11-generic root=UUID=44549c7f-d040-4322-ae8c-c48ae0713952 ro  single vga=794
initrd		/initrd.img-2.6.28-11-generic

# Ubuntu 9.04, memtest86+
title		Ubuntu 9.04 (RAM test)
uuid		33954389-0a03-4822-96c4-c6e5924de048
kernel		/memtest86+.bin vga=794
quiet
```

Shows as:
```
Windows XP
Ubuntu 9.04
-
Ubuntu 9.04 (recovery mode)
Ubuntu 9.04 (RAM test)
```

---

### Post by LewRockwell on 2009-08-20
when we edit our menu.lst file we do this```
title     Empty Partition Reserved
```to reference partitions we haven't utilized yet

you may "say" anything you wish and it will show on the grub menu wherever you put them

as per the above post

*****************************

also, while we're on the subject:```
# title		Ubuntu 9.04
# uuid		33954389-0a03-4822-96c4-c6e5924de048
# kernel	/vmlinuz-2.6.28-11-generic root=UUID=44549c7f-d040-4322-# ae8c-c48ae0713952 ro quiet splash vga=794 
# initrd	/initrd.img-2.6.28-11-generic
# quiet
```hides older kernel entries until you're sure you want to edit them out of your menu.lst file

.

---

### Post by ubume2 on 2009-08-21
Thanks for the help.

There really isn't a way to separate the various operating systems on the grub menu list.

I guess it's not a big problem  as long as I have the default boot setup in menu.lst

Thanks again

---

