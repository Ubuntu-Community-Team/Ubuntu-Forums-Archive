---
title: "[SOLVED] Error loading GRUB"
date: 2008-12-31
forum: New to Ubuntu
---

### Post by looi76 on 2008-12-31
On my computer I Triple-Boot Vista, XP and Ubuntu. Using Vista I have delete XP Partition. Now, when I switch on my computer I get a GRUB error. I think that has happened because ubuntu partition number has changed from the third partition to the second partition.

I tried to fix it using the LiveCD. I entered the Terminal and went to Grub. Then I try: 
```
find /boot/grub/stage1
Error 15: File not found
```

Need Help!:(

---

### Post by drs305 on 2008-12-31
*Edit Added:* logos34 correctly pointed out that newer versions of ubuntu use UUIDs and deletion of a partition would not change the UUIDs of existing partitions. Rather than recompose this entry I'll just delete it.

---

### Post by logos34 on 2008-12-31
the thing is, if this is a newer ubuntu release, it uses UUIDs and partition UUID numbers don't change...Grub stage1 on the MBR can't even find / with the menu.lst, it just errors out immediately, no menu screen...

Can you post your 

sudo fdisk -l

?

---

### Post by drs305 on 2008-12-31
> **logos34 said:**
> the thing is, if this is a newer ubuntu release, it uses UUIDs and partition UUID numbers don't change...Grub stage1 on the MBR can't even find / with the menu.lst, it just errors out immediately, no menu screen...

Can you post your 

sudo fdisk -l

?

You are right and I didn't ask what version. I'll just remove the post.

---

### Post by looi76 on 2008-12-31
Here is the output:

```
ubuntu@ubuntu:~$ sudo fdisk -l
omitting empty partition (5)

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb8b59c4b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       23054   185181223+   7  HPFS/NTFS
/dev/sda3           37421       38913    11992522+   7  HPFS/NTFS
/dev/sda4           29587       37420    62926605    5  Extended
/dev/sda5           29587       36376    54540643+  83  Linux
/dev/sda6           36377       37420     8385898+  82  Linux swap / Solaris

Partition table entries are not in disk order
```

---

### Post by logos34 on 2008-12-31
can you mount ubuntu / (sda5) on the live cd?  

"omitting empty partition (5)" -- ?

Both ntfs partitions are still there (apparently you formatted rather than deleted XP)

---

### Post by looi76 on 2008-12-31
/dev/sda1 is Vista
/dev/sda3 is Recovery Disk
/dev/sda4 is Extended Partition
/dev/sda5 is Ubuntu
/dev/sda6 is Swap

I can mount ubuntu using the LiveCD.

---

### Post by logos34 on 2008-12-31
hmm...with ubuntu mounted navigate to /boot/grub (actually it will be sth like '/**media/disk**/boot/grub').  Do you see the files there (stage1)?

you should be running:

> sudo grub

grub> find /boot/grub/stage1

etc.

(BTW, even if you were using drive letters rather than uuids, the partition number of / would not have been affected since it's on a logical partition)

---

### Post by looi76 on 2009-01-01
I got an error, please look at the screenshot:

[[IMG]http://img58.imageshack.us/img58/3641/grubam9.th.png[/IMG]](http://img58.imageshack.us/my.php?image=grubam9.png)

Now, when I switch on my computer. I don't get an error but I get this message:

```
GRUB Loading stage1.5
```

and nothing happens later...

---

### Post by bumanie on 2009-01-01
You should be sending the root of grub to (hd0,4) as the filesystem is on sda5 - grub starts its count at zero, thus partition #5 to grub would equate to (hd0,4). > sudo grub > root (hd0,4) > setup (hd0) > quit reboot and it should boot to ubuntu. Setting grub up in (hd0,5) is telling grub to boot from the swap area.

---

### Post by logos34 on 2009-01-01
> **bumanie said:**
> You should be sending the root of grub to (hd0,4) as the filesystem is on sda5 - grub starts its count at zero, thus partition #5 to grub would equate to (hd0,4).   reboot and it should boot to ubuntu. Setting grub up in (hd0,5) is telling grub to boot from the swap area.

yeah, let's hope that works, that would be the next thing I'd try...because what's strange is, the 'find' command in the grub shell is saying '(hd0,5)'.  And it even succeeds until the last, when it halts at 'error 12: invalid device request'.  hmm...

---

### Post by looi76 on 2009-01-01
I entered (hd0,4) but I got an error. Look at the screenshot:

[[IMG]http://img175.imageshack.us/img175/8092/ssxr9.th.png[/IMG]](http://img175.imageshack.us/my.php?image=ssxr9.png)

---

### Post by logos34 on 2009-01-01
what does 

sudo sfdisk -d /dev/sda 

show?

there might be a way to use sfdisk to clear up the empty partition

---

### Post by looi76 on 2009-01-01
Here is the result:

[[IMG]http://img84.imageshack.us/img84/5536/eabb2.th.png[/IMG]](http://img84.imageshack.us/my.php?image=eabb2.png)

---

### Post by logos34 on 2009-01-01
Try this:

sudo sfdisk -d /dev/sda | sudo  sfdisk  --force /dev/sda

(it was used successfully [here]("http://ubuntuforums.org/showthread.php?t=1006079"))

Hopefully that will rewrite the partition table back to disk omitting sda2 (deleted)

After you do that run 

sudo fdisk -l

again and post output

---

### Post by looi76 on 2009-01-01
Here is the output: (for the command **sudo sfdisk -d /dev/sda | sudo sfdisk --force /dev/sda**)

```
ubuntu@ubuntu:~$ sudo sfdisk -d /dev/sda | sudo sfdisk --force /dev/sda
Checking that no-one is using this disk right now ...
BLKRRPART: Device or resource busy

This disk is currently in use - repartitioning is probably a bad idea.
Umount all file systems, and swapoff all swap partitions on this disk.
Use the --no-reread flag to suppress this check.

Disk /dev/sda: 38913 cylinders, 255 heads, 63 sectors/track
Old situation:
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sda1   *      0+  23053   23054- 185181223+   7  HPFS/NTFS
		end: (c,h,s) expected (1023,254,63) found (1022,254,63)
/dev/sda2          0       -       0          0    0  Empty
/dev/sda3      37420   38912    1493   11992522+   7  HPFS/NTFS
		start: (c,h,s) expected (1023,254,63) found (1022,254,63)
		end: (c,h,s) expected (1023,254,63) found (1022,254,63)
/dev/sda4      29586   37419    7834   62926605    5  Extended
		start: (c,h,s) expected (1023,254,63) found (1022,254,63)
		end: (c,h,s) expected (1023,254,63) found (1022,254,63)
/dev/sda5      29586+  36375    6790-  54540643+  83  Linux
		start: (c,h,s) expected (1023,254,63) found (1022,1,1)
		end: (c,h,s) expected (1023,254,63) found (1022,87,6)
/dev/sda6      36376+  37419    1044-   8385898+  82  Linux swap / Solaris
		start: (c,h,s) expected (1023,254,63) found (1022,1,1)
		end: (c,h,s) expected (1023,254,63) found (1022,87,6)
New situation:
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sda1   *        63 370362509  370362447   7  HPFS/NTFS
/dev/sda2             0         -          0   0  Empty
/dev/sda3     601152300 625137344   23985045   7  HPFS/NTFS
/dev/sda4     475299090 601152299  125853210   5  Extended
/dev/sda5     475299153 584380439  109081287  83  Linux
/dev/sda6     584380503 601152299   16771797  82  Linux swap / Solaris
Successfully wrote the new partition table

Re-reading the partition table ...
BLKRRPART: Device or resource busy
The command to re-read the partition table failed
Reboot your system now, before using mkfs

If you created or changed a DOS partition, /dev/foo7, say, then use dd(1)
to zero the first 512 bytes:  dd if=/dev/zero of=/dev/foo7 bs=512 count=1
(See fdisk(8).)
ubuntu@ubuntu:~$ 

```

Here is the output for the command **sudo fdisk -l**

```
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb8b59c4b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       23054   185181223+   7  HPFS/NTFS
/dev/sda3           37421       38913    11992522+   7  HPFS/NTFS
/dev/sda4           29587       37420    62926605    5  Extended
/dev/sda5           29587       36376    54540643+  83  Linux
/dev/sda6           36377       37420     8385898+  82  Linux swap / Solaris

Partition table entries are not in disk order
ubuntu@ubuntu:~$ 



```

---

### Post by logos34 on 2009-01-01
ok, good.  See, fdisk is no longer complaining about 'omitting empty partition (5)'.

Now try to reinstall grub like you did before.  Hopefully the 'find' command will now return '(hd0,4)' and allow you to successfully do setup without error

---

### Post by looi76 on 2009-01-02
THANKS **logos34**, it worked! :)

[[IMG]http://img66.imageshack.us/img66/4634/asdfev7.th.png[/IMG]](http://img66.imageshack.us/my.php?image=asdfev7.png)

---

### Post by logos34 on 2009-01-02
ok, good to hear.  Be sure to thank the folks in the thread I linked to.

enjoy

---

