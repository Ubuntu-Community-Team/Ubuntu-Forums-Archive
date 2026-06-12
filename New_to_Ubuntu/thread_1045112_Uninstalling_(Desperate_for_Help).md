---
title: "Uninstalling (Desperate for Help)"
date: 2009-01-20
forum: New to Ubuntu
---

### Post by Canon Man on 2009-01-20
Hi everyone,

I've had a short time with Ubuntu but find that the performance of Vista, by dual-booting, is compromised and I can't work properly. I need therefore to uninstall Ubuntu and claim back the disk space for vista.
So how do I do it?

Am I correct in believing this is the right procedure - btw I am a bit of a computer noob, I don't know very much of the terminology.

- Uninstall Grub (How do I do this?)

- Recover the bootloader for Vista (Again how?)

- Delete the Linux/Ubuntu partition (I can do this using Vista's computer management I believe)


Please correct me if I'm wrong. I need this sorted today and preferably in the next few hours.

Thanks, I'm counting on you guys/gals.

---

### Post by azr on 2009-01-20
I suggest booting into windows searching in help for a program to fix the master boot record (MBR) or boot into recovery mode (with or without  cd/dvd) and it should definitely have a program of sorts to fix. 

As to recovering the space - i suggest using a program within windows such as partition magic, or window's own ntfs tools to delete the linux partition and extend your windows partition to take up that space.

---

### Post by insanity99 on 2009-01-20
if you were testing you should have used Wubi.

---

### Post by HavocXphere on 2009-01-20
Haven't done that myself, but here is my guess:

Use gparted to kill the nix partition. Then resize the MS partition to use the extra space now created.(Or you could create a second parition, like a D drive in windows). Then do a windows repair, which will replace grub with the MS loader.

---

### Post by Canon Man on 2009-01-20
Hi again,

I'm kind of getting what you are saying but kind of not.

Basically can I put the Windows installation CD that came with my computer into the drive, restart my computer, select repair my computer, do all the fuddly stuff and then finally select startup repair - I did this via a hardrive version a minute a go but grub still remains.

Will this remove any of my files?

I know how to do the partition - I used Gparted to do it for linux but am happy to use Vista's computer management this time.

---

### Post by lovelyvik293 on 2009-01-20
to restore the vista boot loader go to the recovery mode with the cd
and use 
```

fixmbr
fixboot

```

---

### Post by RyanVanDiemen on 2009-01-20
yes, lovely`s idea should solve it you need to fix MBR (that`s how windows call it :-o ). Afterwards, all you need to do is delete the linux partition and allocate it to vista. I don`t know if vista has its own tool to do it (heh, never used vista before :-) ) but Partition Magic is perfect or you can still boot Live Ubuntu CD and use GParted...

---

### Post by Canon Man on 2009-01-20
So I've now deleted the volume which had ubuntu on it. I typed in bootrec.exe/fixmbr and bootrec.exe/fixboot and now my system auto loads vista, FAB!!!

The problem is that the partition that was Linux is now "extended partition". Can GParted simply destroy that partition and reallocate it to Vista without damaging my system?

Thanks for helping me you guys/gals

---

### Post by RyanVanDiemen on 2009-01-20
If there`s only one logical partition on this extended partition (I assume it is) you can safely remove it with gparted and then just allocate the space to Vista partition. But before doing so can you post how many partitions and in what order do you currently have on your HDD?

---

### Post by Noblacktie on 2009-01-20
Vista has a built in disk partitioning tool that can expand your existing Windows  partition to envelope the old Ubuntu partition. It's best to let Windows manage its own file systems, I find.

In Vista:

Click on 'Start' > Right Click 'Computer' > Click 'Manage' > Click 'Disk (Or Storage?) Management' > Delete the Extended partition > Expand Vista partition.

But why not leave that space free for when you itch to install Linux again? ;)

---

### Post by RyanVanDiemen on 2009-01-20
Like I said, I`ve never used Vista so didn`t know it has its own partition manager. I would also use the Vista`s one. But remember Linux uses only small part of the drive. e.g. I have currently only one linux (ubuntu) installed on my desktop but still have 2 more partitions ready if I want to try something else :-) They say playing with partitions is not that safe (nothing ever happened to me though) so you could spare some GB for future...

---

