---
title: "mount command help for the new Ubuntu 10.04"
date: 2010-06-13
forum: New to Ubuntu
---

### Post by TerrieG on 2010-06-13
I upgraded to Ubuntu 10.04 LTS.  Since then I am no longer able to run the command "mount /dev/fd0" to mount a floppy.  It is asking me to specify "type" - I don't understand the discussion on the man page about type.  In my /dev/fstab file there is a line 
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

What should I type to mount a floppy?

---

### Post by Ozymandias_117 on 2010-06-13
Try: ```
mount -t auto /dev/fd0
```

---

### Post by TerrieG on 2010-06-13
I get the error that only root can do that.

The floppy I am trying to mount, I previously wrote to as "user"

---

### Post by rukiaEnix on 2010-06-13
try with this line at fstab:

```

/dev/fdo0      /media/floppy0  auto defaults,utf8 0 0 

```

---

### Post by Ozymandias_117 on 2010-06-13
> **TerrieG said:**
> I get the error that only root can do that.

The floppy I am trying to mount, I previously wrote to as "user"

But can you mount it as root?

---

### Post by TerrieG on 2010-06-13
When I run the command as root, it does not mount, but gives me what I think is a usage message, like it is asking me for more on the command line that just the  mount -t auto /dev/fd0

---

### Post by rukiaEnix on 2010-06-13
you are missing the mount point, put it like this:

```

mount -t auto /dev/fd0 /mount_point

```

---

### Post by TerrieG on 2010-06-13
> **rukiaEnix said:**
> try with this line at fstab:

```

/dev/fdo0      /media/floppy0  auto defaults,utf8 0 0 

```



Are you saying I should login as root and edit my /etc/fstab file?  If so should there be tabs or just spaces inbetween each word or number?

---

### Post by rukiaEnix on 2010-06-13
just spaces and yes as root :p

---

### Post by TerrieG on 2010-06-14
> **rukiaEnix said:**
> you are missing the mount point, put it like this:

```

mount -t auto /dev/fd0 /mount_point

```


First, I really appreciate the help - I am a newbie

I logged in as root and typed
mount -t auto /dev/fd0 /mnt
and now get the message that I have to specify the filesystem type

---

### Post by rukiaEnix on 2010-06-14
I don't know what filesystem uses floppy but try this:

```

mount -t vfat auto /dev/fd0 /mnt

```

---

### Post by TerrieG on 2010-06-14
I edited my /etc/fstab file with the line
/dev/fd0 /media/floppy0 auto defaults, utf8 0 0

then typed mount -t auto /dev/fd0 /media/floppy0


I get the message that I have to specify the filesystem type?  Is that "auto"?  When I do a man on mount "auto" is not one of the filesystem types it lists.  How do I  find out what my filesystem type is?

And the real mystery to me is why has this problem cropped up since I upgraded to 10.04

---

### Post by rukiaEnix on 2010-06-14
sorry I put vfat and then auto, try with vfat type:

```

mount -t vfat /dev/fd0 /mnt

```

---

### Post by TerrieG on 2010-06-14
> **rukiaEnix said:**
> I don't know what filesystem uses floppy but try this:

```

mount -t vfat auto /dev/fd0 /mnt

```


The following worked
mount -t vfat /dev/fd0 /media/floppy0


Thanks for your help.

The real mystery remains ---- why I am having to issue a different mount command and why do I have to be logged in as root to do it, just since I upgraded to 10.04.

---

### Post by rukiaEnix on 2010-06-14
but what do you mean with a different mount command?

---

### Post by Bodsda on 2010-06-14
> **TerrieG said:**
> The following worked
mount -t vfat /dev/fd0 /media/floppy0


Thanks for your help.

The real mystery remains ---- why I am having to issue a different mount command and why do I have to be logged in as root to do it, just since I upgraded to 10.04.

Do you mean that it is not auto-mounting? If so then you will have to edit /etc/fstab to get that working. Here is a great guide on fstab from a Staff member here. [http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

Bodsda

---

### Post by TerrieG on 2010-06-14
> **rukiaEnix said:**
> but what do you mean with a different mount command?


I mean, why can't I just type mount /dev/fd0 as user like I used to be able to do.  

Instead now the way it works is if I login as root and type
mount -t vfat /dev/fd0 /media/floppy0

---

### Post by TerrieG on 2010-06-14
> **Bodsda said:**
> Do you mean that it is not auto-mounting? If so then you will have to edit /etc/fstab to get that working. Here is a great guide on fstab from a Staff member here. [http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

Bodsda


I will check out  your recommended guide link.  My floppy has never automounted.  I have always had to issue the mount command from command line.   I have only had a computer in my home for a few months so consider the user.

---

### Post by Ozymandias_117 on 2010-06-14
I think the problem has to do with 10.04; I did some testing today, and it seems like whatever they use to check what filesystem is on a device, and automatically mount based on that, is broken. Unfortunately, I don't know what filesystem floppies use to have any idea for a workaround :(. I can try to do some googling in a little bit.

---

### Post by rukiaEnix on 2010-06-14
it works with vfat filesystem.
TerrieG please mark this thread as solved

---

### Post by Ozymandias_117 on 2010-06-14
> **TerrieG said:**
> I mean, why can't I just type mount /dev/fd0 as user like I used to be able to do.  

Instead now the way it works is if I login as root and type
mount -t vfat /dev/fd0 /media/floppy0

Ah, missed part of this post. Thanks Rukia, I had forgotten floppies use FAT 12.

Try modifying your /etc/fstab to ```
/dev/fd0 /media/floppy0 vfat rw,user,noauto,exec,utf8 0 0
``` and in theory you should be able to mount your floppy like you did before.

---

