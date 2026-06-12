---
title: "What is mounting?"
date: 2011-07-28
forum: New to Ubuntu
---

### Post by Foobarz on 2011-07-28
Migrating from Windows (HOORAY!) I do not understand this concept of mounting. It was simple in windows: Everything had its own drive letter. But on ubuntu everything's on root? And what does it mean when its mount point is a block device called /dev/sr0 (for CD's)? What does that do? Is that like some shortcut to the real CD? Why are CD's never mounted in /cdrom or /mnt? Why is everything mounted /media? What is /dev? What is the fstab and mstab inside it? These are VERY IMPORTANT QUESTIONS! (I kid, if anyone has the free time, could you explain this mounting concept to me?)

---

### Post by karlson on 2011-07-28
> **Foobarz said:**
> Migrating from Windows (HOORAY!) I do not understand this concept of mounting. It was simple in windows: Everything had its own drive letter.
Not always and not necessarily.

> But on ubuntu everything's on root?

Not really.

> 
And what does it mean when its mount point is a block device called /dev/sr0 (for CD's)?  What does that do?
What it means is that data from this device is accessed in blocks. [http://en.wikipedia.org/wiki/Device_file](http://en.wikipedia.org/wiki/Device_file)

> Is that like some shortcut to the real CD? Why are CD's never mounted in /cdrom or /mnt?

You could mount them on any existing directory so if you choose to mount on /mnt or /cdrom you could.  Actually I am not sure about now but in the earlier versions Slackware was mounting CDROM on /cdrom and RedHat on /mnt/cdrom

> Why is everything mounted /media?

For the most part it's convention.

> What is /dev?
Dev is a special filesystem or a directory, which contains files representing various devices.

> What is the fstab and mstab inside it?
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

/etc/fstab contains the definitions of how to gain access to different filesystems.
/etc/mtab contains the list of currently mounted devices.


> These are VERY IMPORTANT QUESTIONS! (I kid, if anyone has the free time, could you explain this mounting concept to me?)

Think of mounting as simply gaining access to the data on the filesystem via a directory structure.

Contrary to the DOS philosophy which most people using Windows subscribe to is having directory trees with multiple roots namely drive letters UNIX subscribes to the single directory tree philosophy, hence ability to mount various devices as different entries in the directory trees, so if you need to expand space in a particular area you can mount another physical device on a directory you need.

---

### Post by Jonny87 on 2011-07-28
> **karlson said:**
> ... so if you need to expand space in a particular area you can mount another physical device on a directory you need.

So are you saying that you can mount multiple drives under one directory

i.e.
> /media/Mass_Storage

and Linux will treat it as one directory, one drive?

---

### Post by karlson on 2011-07-28
> **Jonny87 said:**
> So are you saying that you can mount multiple drives under one directory


Be clear on what you mean because this
```

mount /dev/sdc /mnt/mass_storage
mount /dev/sdd /mnt/mass_storage

```

is actually perfectly legal the result though won't be contiguous space combined from /dev/sdc and /dev/sdd

> 
and Linux will treat it as one directory, one drive?

If you do this
```

mount /dev/sdc /mnt/mass_storage
mount /dev/sdd /mnt/mass_storage/extra_space

```

So if you write to any directory or file on /mnt/mass_storage/extra_space you will write on a drive represented by /dev/sdd and any place else under /mnt/mass_storage will be stored on device represented by /dev/sdc

Hope this clarifies it for you.

---

### Post by Jonny87 on 2011-07-28
> **karlson said:**
> Be clear on what you mean because this
```

mount /dev/sdc /mnt/mass_storage
mount /dev/sdd /mnt/mass_storage

```is actually perfectly legal the result though won't be contiguous space combined from /dev/sdc and /dev/sdd



If you do this
```

mount /dev/sdc /mnt/mass_storage
mount /dev/sdd /mnt/mass_storage/extra_space

```So if you write to any directory or file on /mnt/mass_storage/extra_space you will write on a drive represented by /dev/sdd and any place else under /mnt/mass_storage will be stored on device represented by /dev/sdc

Hope this clarifies it for you.

It does a bit, so then under the first example;
```

mount /dev/sdc /mnt/mass_storage
mount /dev/sdd /mnt/mass_storage

```
What would be the result as far as reading and writing? to the mass_storage? and is it safe?

---

### Post by karlson on 2011-07-28
> **Jonny87 said:**
> It does a bit, so then under the first example;
```

mount /dev/sdc /mnt/mass_storage
mount /dev/sdd /mnt/mass_storage

```
What would be the result as far as reading and writing? to the mass_storage? and is it safe?

Writing to any place under /mnt/mass_storage would mean writing to /dev/sdd.

---

### Post by Foobarz on 2011-07-30
Awesome answers karlson! Thank you, I now understand the mounting mechanism of Linux!

PS: Nice profile!

---

