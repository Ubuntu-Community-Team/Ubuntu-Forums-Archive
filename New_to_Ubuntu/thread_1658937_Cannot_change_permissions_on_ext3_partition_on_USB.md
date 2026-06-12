---
title: "Cannot change permissions on ext3 partition on USB hard disk"
date: 2011-01-03
forum: New to Ubuntu
---

### Post by Johniatwork on 2011-01-03
I am a total Ubuntu/Linux newbie running Ubuntu 10.04 LTS.

I used gparted to create and format an ext3 partition on a USB-attached hard disk.

When I mount this partition, I see a lost+found folder.

When I try to create a new folder in the root of the partition, there is no option to do so.

When I look at the permissions it says: “You are not the owner, so you cannot change these permissions.” 
I created the partition, so why wouldn't I be the owner?

I want to use this USB hard disk to write files and folders to from two or three Ubuntu machines but I cannot see any way of doing this.

---

### Post by TeoBigusGeekus on 2011-01-03
Try this
```
sudo chown yourusername /media/mountfolder
```

---

### Post by Johniatwork on 2011-01-03
TeoBigusGeekus:

Thanks, but the external USB disk will be used by different users on different machines. 

I need a solution that allows any user to write to the partition.

---

### Post by TeoBigusGeekus on 2011-01-03
The only thing I can think of for you to get rid of permissions and restrictions, is to reformat the drive to ntfs, which doesn't support any ownership at all.

---

### Post by Johniatwork on 2011-01-03
TeoBigusGeekus:

But I am trying to get away from Windows. In any case, I'm not sure I trust Linux to write to NTFS, which is not a publicly documented file system.

I could use FAT32, but it's a bit fragile and won't support large file sizes.

---

### Post by TeoBigusGeekus on 2011-01-03
I have used ntfs with linux in the past (during the dual booting era). Never experienced any problems.
Other than that, I don't believe that the intrinsic architecture of linux would have a feature like "give unlimited access to anyone". It would betray the reasons we've chosen linux for in the first time...

---

### Post by coffeecat on 2011-01-03
@johniatwork. Firstly, NTFS read-write is reliable in Ubuntu. NTFS certainly has the advantage of getting around Linux permissions and ownership problems. TeoBigusGeekus' suggestion is the easiest way of achieving what you want. There is one caveat though: if you use NTFS you must have access to Windows if you ever experience NTFS filesystem corruption. You need chkdsk from Windows - no Linux tool can do everything that chkdsk can.

However, there is an answer, based on a little understood feature of Linux filesystems, that you can modify the root of the filsystem with chown and chmod, not just folders and files. If you mount an ext3 partition and chmod or chown the mountpoint, it has the curious effect of changing permissions on the root of the filesystem and **not** the mountpoint.

Try this. Plug the ext3 drive in and let it be automounted. Take a note of the mountpoint. Let's call this /media/mountpoint for illustration. Now:

```
sudo chmod 777 /media/mountpoint
```Any user can now create folders and read and write to the filesystem. This change survives unmounting and remounting because, I repeat,[B] the chmod command in this situation acts on the root of the filesystem and not on the mountpoint.

EDIT: [/B]By the way, if you're worried about such permissive permissions, some others don't work. For instance, chmod 666 doesn't work - in this situation. I don't know why.

---

### Post by TeoBigusGeekus on 2011-01-03
Thanks for the info coffeecat! Appreciated.

---

### Post by Johniatwork on 2011-01-03
@ coffeecat:

Just tried this and it does just what I want - thanks!

My only misgiving is: will this go on working, or will this "feature" be fixed out of existence at some future date?

Time will tell!

---

### Post by matt_symes on 2011-01-03
Hi

@coffeecat

Nice. I did not know that. *Nods head in appreciation*

Kind regards

---

### Post by audiomick on 2011-01-03
> **Johniatwork said:**
> ..
My only misgiving is: will this go on working, or will this "feature" be fixed out of existence at some future date?...

My guess is that it will keep on keeping on, though coffeecat is likely to have more idea than me, I'm sure.

If I understand it right, that chmod command and it's effect is extremely fundamental to the way linux file systems work. I think that it would almost require a re-design from scratch of the file system to change the way it operates.

---

### Post by coffeecat on 2011-01-03
To all those asking: I'm fairly sure this is hard-wired into the way all Unix filesystems are designed. I've even managed to chmod and chown the non-journalled version of Apple's hfs+ filesystem this way from Ubuntu. Which is handy! :)

Try this. Plug a USB drive in that you don't mind reformatting. It doesn't matter whether it's a hard drive or flash drive. Open Disk Utility and select the drive for reformatting. A small window will open defaulting to ext4, but see the "Take ownership of filesystem" with the box ticked. I should imagine that's offering to do a chown on the new filesystem for you. Try any of the other filesystem types. The tickbox is there for any of the Linux/Unix filesystems (except) swap, but not for FAT or NTFS, which of course you can only own through mount options.

The way I discovered this (by accident) was by doing a 'sudo chown myusername: /media/mountpoint' on an automounted ext3 external drive. I thought I was chowning the mountpoint, but when I next plugged the drive in I was pleased to see that I could still write to it. The mountpoint for automounted drives is dynamic - i.e. it would have been deleted once the device was unmounted - so I assumed the ownership was being "remembered" in something like udev rules. Not so. When I plugged the drive into a completely different Ubuntu machine it was automounted and I still owned the drive. Clearly, the memory was being held on the drive, not in the operating system. I eventually found the explanation on another forum - that the ownership/permissions are held in the root of the filesystem.

Further experiments showed that the mountpoint isn't affected at all. If you create a mount folder for an internal partition and do a chown or chmod when the partition is mounted, and then do a 'ls -l', you'll see that the mountpoint seems to have whatever permissions you assigned with the chmod or chown. If you then unmount the partition and repeat the 'ls -l' you'll see that the mounpoint permissions revert to whatever they had when first created - usually owned by root.

All very interesting. I still have some of the potentials and pitfalls of chmodding to discover. As I said in my earlier post 'sudo chmod 666' doesn't work for some reason to make the drive universally writeable, but I'm sure some creative chmodding could come up with something useful.

---

