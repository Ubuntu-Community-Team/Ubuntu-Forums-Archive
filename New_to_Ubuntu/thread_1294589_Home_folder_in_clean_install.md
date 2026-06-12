---
title: "Home folder in clean install"
date: 2009-10-18
forum: New to Ubuntu
---

### Post by captgadget on 2009-10-18
I partitioned my harddrive so I could have a partition for the home folder. When I open partition editor I can see it as sda4, but when I open file system it doesn't show. Is this right or do I have a problem?

---

### Post by cariboo on 2009-10-18
When you created the partition did you set the mount point as /home?

If you didn't you can mount it manually as /home:

```
sudo mount /dev/sda4 /home
```

If that works for you, you can edit /etc/fstab to automagically mount the partion on boot:

```
# /home was on /dev/sda3 during installation
UUID=aa523fb1-3b13-470b-8877-54e7628a397f /home           ext4    defaults        0       2
```

To find the uuid of the partition open a terminal and type:

```
blkid
```

and note the uuid for /dev/sda4

---

### Post by captgadget on 2009-10-18
Yes, I set a mount point as  home. Should have done it differently?

---

### Post by lidex on 2009-10-18
Open up your "Partition Editor" (GParted) in "System>Administration" menu. The lower pane will give partition info. If done correctly you will have an entry under the "mount point" column of "/home". In Nautilus, under "Places", it won't show as a separate partition but as your username.

---

### Post by sblunix on 2009-10-18
> **captgadget said:**
> Yes, I set a mount point as  home. Should have done it differently?
Open GParted and give us all properties of your /home partition please.

---

### Post by captgadget on 2009-10-18
Here's what I got.

---

### Post by captgadget on 2009-10-18
Here's the message I got: mount: according to mtab, /dev/sda4 is already mounted on /home

---

