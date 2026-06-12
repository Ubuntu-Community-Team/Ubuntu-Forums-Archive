---
title: "Is there a standard mount point for shared (between users) partitions?"
date: 2009-10-31
forum: New to Ubuntu
---

### Post by mlippert on 2009-10-31
Hi,
I have a partition which contains music (ogg) files.

I want to mount this somewhere it will be accessible to all users, not just my user, which is why I don't want to mount it at [FONT="Fixedsys"]/home/mlippert/Music[/FONT].

I was wondering if there is a standard/traditional linux/unix location for data which should be accessible to multiple users, since that would be where I'd want to mount this partition.

I've seen some suggestions that I should use a mount point in /home, such as [FONT="Fixedsys"]/home/Music[/FONT]. However others have said that is a bad idea and /home should only contain actual users directories.

Other suggestions I've seen are to create the mount point in /mnt, ie [FONT="Fixedsys"]/mnt/Music[/FONT] or just put it in root, [FONT="Fixedsys"]/Music[/FONT].

I realize it's *my* system and I can do whatever I want, but I've found it's easiest in the long run to follow standards if they exist.

If there are no traditional standards for this, I'd also like to hear if you've got any standards of your own, and the reasoning behind them.

Obviously this would apply to music partitions, video partitions or just plain data partitions which are shared by many users on a multiuser system.

Thanks,
Mike

---

### Post by dvlchd3 on 2009-10-31
Try the /usr/share directory.  I believe you must have sudo rights to write to the directory, however, all users can read the directory.

Also, you could always create a directory someplace (like in the /home dir) and just do set the permissions so all users will have access to it:

```

mkdir /home/sharedDir
chmod 666 /home/sharedDir

```

Or, maybe more preferably for you, allow other users to only read from the directory, but you to write to it:

```

mkdir /home/sharedDir
chmod 644 /home/sharedDir

```

---

### Post by cariboo on 2009-10-31
I use the /media directory for shared directories. You shouldn't use /usr/share, as that is where the application configuration directories are.

---

