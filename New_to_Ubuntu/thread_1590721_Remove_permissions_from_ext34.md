---
title: "Remove permissions from ext3/4"
date: 2010-10-08
forum: New to Ubuntu
---

### Post by hugo87 on 2010-10-08
I use an external hard drive for storing lots of files I share with friends and family.

I know I can set 666, but I can only do this in contained files and directories, NOT on the actual disk root.  This means people can't write to the disk root.

Also, setting 666 might cause some issues when someone else pastes files and applies some other permissions.

Is there some way to remove permissions completely from an ext3 filesystem?  I mean, have the entire "permissions" layer removed?  Otherwise, what can I do?

Changing fstab is out of the question, this is a shared EXTERNAL disk; people use it on their computers, I can't go around changing their fstab.
The same goes to mount parameters.

---

### Post by Hippytaff on 2010-10-08
You could use chown to change ownership, so that everyone has ownership?

---

### Post by coffeecat on 2010-10-08
This is not widely understood but you can, in fact, change the ownership of a whole ext2/3/4 fileystem by chown-ing the mountpoint of a mounted filesystem. Then, when you remount, the ownership of the filesystem over-rides whoever the mountpoint is owned by. Very handy.

I've only ever changed the ownership to myself with:

```
sudo chown coffeecat: /media/mountpoint
``` Note the trailing colon which sets my default group. Your situation is slightly more complicated in that you need to set the group ownership. I've never done this, but I should think you need to create a group and then configure everyone's group for that. When doing the chown, you have to specifiy a username, so I suppose you'll have to use your own. Let's say the group you've created is 'hd', then it would be:

```
sudo chown hugo87:hd /media/mountpoint
```You could try the plugdev group because everyone is in that but that group is for a purpose and I don't know whether this would interfere.

I've tried chmodding a filesystem through the mountpoint but it didn't work.* However, the chown I've described seems to have given me 777 permissions on one of my internal ext4 mounted partitions. I thought it was only giving me 660 so that's come as a surprise. Why not try it and see what you get?

**Edit:** Sorry - the 777 took me by surprise. That would, of course, give everyone carte blanche to do anything so you wouldn't need to bother with a group. But I've got three ext4 partition currently mounted to this system, all of which I've chowned in the past and I get variously 777, 755 and 777. Curious. I don't think it's to do with the mountpoint itself because the filesystem overrides the mountpoint, but I'll do some investigation.

*** Edit2:** Hmmm. My earlier experiment must have been faulty. I've just discovered that I can chmod the filesytem. I have an internal ext4 partition mounted through fstab with a simple 'defaults' in the options. If I unmount it, it is owned by root. If I mount it 'ls -l' shows the ownership as myself. And I've discovered a curiosity. If I chmod the filsystem to 766 or 777, it shows on the desktop (mounted in /media), but with 666 it mounts but doesn't show on the desktop. You'll have to see what happens with automounted filesystems.

---

### Post by hugo87 on 2010-10-09
@coffeecat:
Being, as I said, an external hard drive I SHARE, every person I share it with will mount it on their own computer.

I've no way of chmoding the mountpoint before the drive is mounted, since I may never even have access to the computer at all.



@Hippytaff:
Who would I set as the owner?  It might be user 1000 on my computer, 1003 on another, and 500 on another who's using the disk.

---

### Post by coffeecat on 2010-10-09
> **hugo87 said:**
> @coffeecat:
Being, as I said, an external hard drive I SHARE, every person I share it with will mount it on their own computer.

I've no way of chmoding the mountpoint before the drive is mounted, since I may never even have access to the computer at all..

You have completely misunderstood what I said. My mention of  internal partitions may have misled you. That was merely an illustration. It works just the same way with external drives.

Mount the drive on your own computer, then chown and chmod the mountpoint. This has the effect of chowning (and chmodding) the filesystem, **not** the mountpoint. When you then plug it into another Ubuntu system you will find the whole filesystem has the ownership and permissions you set on the first computer. I discovered this by accident and have done this with external drives between different computers. Try it and you'll see.

It's very similar to what you can do in Disk Utility. If you create a Linux filesystem, you have the option of 'owning' it.

---

