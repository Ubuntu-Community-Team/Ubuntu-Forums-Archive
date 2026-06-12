---
title: "Howto scan disks for errors"
date: 2009-12-15
forum: New to Ubuntu
---

### Post by L a r r y on 2009-12-15
Hello all.

I just encountered a disk drive failure, because apparently the power cable was not fully seated.  The computer was frozen, my email inbox was open on Thunderbird, as was a compose window, and my Firefox was open.

I powered off the computer and turned it back on.

**BOOT FAILURE** Insert system disk.

Now what! I said, and turned off the computer.

After putting in a different drive cable and finding the power connection a bit loose, I retightened it and fired up the computer.

Up it came, and it booted right up.  However, I remember from my days running Windows, MS always reminded me that Windows was not properly shut down and a disk needed to be checked for consistency.

I had some corrupted pictures that I had downloaded prior to the failure, that were not valid, even though I saw them in their full glory.  They apparently were in the buffer and not written to disk when the disk went down.  So I was suspicious and wanted to run a disk scan before I go any further.

A check on the Web led to using **file2fs** to set the maximum number of boots before a disk check is performed.  Ubuntu defaults to a disk scan every 20 boots or so.

I had recalled that I was using partitions 5, 6 and 7 for swap, system and home.  So I needed to set the maximum count before a check is performed to 1 so the disk would scan on the next boot.

Open the Terminal and enter:```
sudo tune2fs -c1 /dev/sda6
```

You are prompted for your password.  Type it in, but remember, there is nothing that will appear on the screen while you type the password.  In the Terminal, there are no ******* stars as you enter your password as is the case with graphical windows.


Close all windows and restart the computer.  A disk check is performed.

In my case, I had a multitude of errors on my home partition and I was instructed to run fsck manually.

On the black screen I was presented with a bash prompt following this set of instructions, and there I typed:```
fsck /dev/sda7
```

The filesystem checker ran and reported a bunch of errors, to which I had to hit y to fix or clear until the check was complete.  Then I typed:```
exit
``` in the bash prompt and let the boot process complete.

Once booted, I returned to the Terminal, hit the up-arrow key and recalled my previous command and changed the -c1 to -c13 by running the left arrow key (not the backspace key, that would delete characters to the left of the cursor) until the cursor was positioned and then I entered the 3.


If I understand the system correctly, I can set the maximum number of boots for each disk partition on my system, so if I stagger the number I will not be hit with two partitions being checked on the same boot, which can extend the startup time considerably.


I ended up losing my corrupted pictures, and even the few pictures that were good, because they were sitting on a corrupted filesystem.  I have asked my correspondent for a re-send of those pictures if he has them.

But I stopped the bleeding by making repairs to the file system now rather than have many more pieces of work go down the tubes later.

Hope this post is helpful to someone!

---

### Post by wojox on 2009-12-17
Even easier way to force a file system check:

```
sudo touch /forcefsck
```

Reboot. Then:

```
sudo rm -rf /forcefsck
```

---

### Post by L a r r y on 2009-12-29
I read up on the use of **sudo touch /forcefsck** from a Google search.  Neat thing about it in my case, I looked to remove it after the boot and it was already gone.

I also came across a Computer Janitor complaint that I was missing the **relatime** option in my /etc/fstab (filesystem table) for the drive partition I set to auto-mount in the /mnt directory.

I have corrected it to read:
```
/dev/sda1	/mnt/music+backups			ext3	relatime	0	3
```

The last number, 3, in this code, is for the pass number.  I have a 1 at the end of my / partition, and a 2 at the end of my /home partition.

When a filesystem check is performed on the three partitions of the same drive, the pass number sets the order in which the partitions will be checked, with 1 being first and 3 being last.

My swap partition has a pass number of 0, which sets disk checks to never.  This was set by default, as were the 1 and 2 order of / and /home, when I installed.

---

### Post by plusnplus on 2009-12-29
Hi L a r r y,
If my pc only have ubuntu OS, can i just type:

sudo tune2fs -c1 /dev/sda

then reboot ?

Can I do this scan disks weekly? will it damage the harddisk?

---

### Post by L a r r y on 2011-11-12
> **plusnplus said:**
> Hi L a r r y,
If my pc only have ubuntu OS, can i just type:

sudo tune2fs -c1 /dev/sda

then reboot ?

Can I do this scan disks weekly? will it damage the harddisk?

I'm sorry I didn't see this question sooner!

Rather than doing the tune2fs code, any time you want to check the disks, just do a ```
sudo touch /forcefsck
```
in the Terminal.

What this does is create a zero-length file named /forcefsck in the root of the filesystem.

Reboot and it will check the disks, rejournal the data and defragment, though Linux filesystems are a lot more intelligent about minimizing fragmentation than the Windows filesystems are.

This will not harm the disk.

Today I am running a fresh install of Ubuntu 10.04 from the Live CD, and have the default schedule for disk checks.  Being that I restart my computer maybe 2 to 3 times a week, it will be a while before I encounter a disk check.

---

