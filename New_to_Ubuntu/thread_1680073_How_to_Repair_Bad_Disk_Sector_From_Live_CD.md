---
title: "How to Repair Bad Disk Sector From Live CD?"
date: 2011-02-01
forum: New to Ubuntu
---

### Post by marl30 on 2011-02-01
I ran Disk Utility and I noticed that it says my HDD has some bad sectors on it. However, it is showing the disk as passed. I didn't want to wait and take too many chances, so I immediately backed up all my files to another HDD, formated it and attempted to repair it.  However, none of the Linux based instructions that I've come across seem to be working for me. I keep getting errors trying to follow the terminal commands. It appears I'll need a specific command for my particular configuration. 

After not getting on too well with online Linux tutorials, I went and tried to repair it using Windows. I tried the Windows scan disk utility, but it did not fixed the bad sectors. I used a trial version of a Windows program called S.M.A.R.T (or something) to scan it, and it says the health of the disk was 53%.

I know this is a sign that the HDD is on the road to failing. It is the largest HDD I have at the moment (250 GB). I have others in my other computers. Wasn't planning on buying a new one until later this year when I build a new PC after the (financial) pressure of schooling gets lighter. 

I would really appreciate any help with the live cd repair.

---

### Post by taseedorf on 2011-02-02
the disc is failing, and you cannot fix it.  It will just continue to avoid those sectors when writing data to it......you can usually use the check disc utility to fix though.

---

### Post by marl30 on 2011-02-02
> **taseedorf said:**
> the disc is failing, and you cannot fix it.  It will just continue to avoid those sectors when writing data to it......you can usually use the check disc utility to fix though.

Thanks for your replay. 

I found a thread with some instructions for running a read/write fix/test: [http://ubuntuforums.org/showthread.php?t=1416311&page=2](http://ubuntuforums.org/showthread.php?t=1416311&page=2) This test took almost 9 hours to complete.

These are the commands I used:```
sudo fsck -f /dev/sda1 
``` Result```
dev/sda1: ***** FILE SYSTEM WAS MODIFIED *****
/dev/sda1: 11/15269888 files (0.0% non-contiguous), 1006245/61049344 blocks

``` I used the command below because the disk was already formatted, so anyone following this step should use -svn and not -svw if you have data on your disk that you haven't backup. -svw will wipe your disk while testing it.```
sudo badblocks -svw /dev/sda
```I'm assuming that the commands have fixed the issue as this is what the results says: ```
Checking for bad blocks in read-write mode
From block 0 to 244198583
Testing with pattern 0xaa: done                                
Reading and comparing: done                                
Testing with pattern 0x55: done                                
Reading and comparing: done                                
Testing with pattern 0xff: done                                
Reading and comparing: done                                
Testing with pattern 0x00: done                                
Reading and comparing: done                                
Pass completed, 0 bad blocks found.

```Does this means the disk is ok?

---

### Post by srs5694 on 2011-02-02
As taseedorf says, it's impossible to fix bad sectors on a hard disk; the best you can do is attempt to avoid them. There are two ways that this can be done:


[list]
[*]**Automatically in the disk's firmware** -- This is done transparently to the OS. Modern disks can detect bad blocks and map them out, replacing the bad blocks with blocks reserved for this purpose when the disk was manufactured. You can also use a SMART utility to force a thorough (and non-destructive) check of the disk, which might turn (and map out) up additional bad blocks or other problems. There are a limited number of reserved blocks, though, and if this limit is exceeded (or if the disk is old enough to not provide this mechanism), you'll have to go to the next solution....
[*]**Using badblocks or a similar utility** -- You can use OS tools to scan the disk for bad blocks and mark them as such in the filesystem. Note that you must use OS-specific tools to do this; you can't use Windows tools to mark bad blocks for Linux, or vice-versa. Note that badblocks won't mark the bad sectors by itself; you must output its list (using -o) and then feed it into a filesystem check or creation tool (such as e2fsck or mke2fs using their -l option). Of course, if badblocks turns up nothing (as it sounds like it did for you), you don't need to feed its output into e2fsck or mke2fs.
[/list]


Without seeing a detailed SMART report, it's impossible to say whether your disk has yet crossed the threshold where badblocks will be useful. You can get SMART status results in Linux using tools such as GSmartControl or smartctl. The Windows tool you used for this does the same thing, but I'm not sure what that tool means by "53%" health. This doesn't sound good, though, so I'll assume that your disk is starting to fail....

Personally, I'd never continue to use a disk with even slightly flaky SMART status results, except as a "scratch" disk (used to test OS installation procedures without endangering my real OSes, for instance). Sometimes, disks start to go bad and then deteriorate rapidly. If this happens to you, you could end up losing everything on your disk in a matter of seconds. Given that a 1 TB disk costs about $50, the question is: Is your data worth $50? If not, then by all means continue to use your current unreliable disk. If your data is worth $50, though, you should go buy a new disk *now* and replace the old one *immediately*. Power down your computer to minimize the risk of doing further damage just by leaving it running and don't power it up again until you've got the new disk ready to take over.

If cash is so tight that you really can't afford $50 right now, then I can only suggest that you keep good backups, at least of your most critical data.

---

### Post by marl30 on 2011-02-02
> **srs5694 said:**
> As taseedorf says, it's impossible to fix bad sectors on a hard disk; the best you can do is attempt to avoid them. There are two ways that this can be done:


[list]
[*]**Automatically in the disk's firmware** -- This is done transparently to the OS. Modern disks can detect bad blocks and map them out, replacing the bad blocks with blocks reserved for this purpose when the disk was manufactured. You can also use a SMART utility to force a thorough (and non-destructive) check of the disk, which might turn (and map out) up additional bad blocks or other problems. There are a limited number of reserved blocks, though, and if this limit is exceeded (or if the disk is old enough to not provide this mechanism), you'll have to go to the next solution....
[*]**Using badblocks or a similar utility** -- You can use OS tools to scan the disk for bad blocks and mark them as such in the filesystem. Note that you must use OS-specific tools to do this; you can't use Windows tools to mark bad blocks for Linux, or vice-versa. Note that badblocks won't mark the bad sectors by itself; you must output its list (using -o) and then feed it into a filesystem check or creation tool (such as e2fsck or mke2fs using their -l option). Of course, if badblocks turns up nothing (as it sounds like it did for you), you don't need to feed its output into e2fsck or mke2fs.
[/list]


Without seeing a detailed SMART report, it's impossible to say whether your disk has yet crossed the threshold where badblocks will be useful. You can get SMART status results in Linux using tools such as GSmartControl or smartctl. The Windows tool you used for this does the same thing, but I'm not sure what that tool means by "53%" health. This doesn't sound good, though, so I'll assume that your disk is starting to fail....

Personally, I'd never continue to use a disk with even slightly flaky SMART status results, except as a "scratch" disk (used to test OS installation procedures without endangering my real OSes, for instance). Sometimes, disks start to go bad and then deteriorate rapidly. If this happens to you, you could end up losing everything on your disk in a matter of seconds. Given that a 1 TB disk costs about $50, the question is: Is your data worth $50? If not, then by all means continue to use your current unreliable disk. If your data is worth $50, though, you should go buy a new disk *now* and replace the old one *immediately*. Power down your computer to minimize the risk of doing further damage just by leaving it running and don't power it up again until you've got the new disk ready to take over.

If cash is so tight that you really can't afford $50 right now, then I can only suggest that you keep good backups, at least of your most critical data.

After leaving it to run all night, running test, I again installed Windows to try out several other tools. All of which said that the disk is healhy, and I'm now seeing 83% health. Different sector scans are also showing no sector damage. I don't know how that is, but that's what I keep seeing from different tools.

All my most important stuff are already backup to Ubuntu One. And larger important files are saved to another hard drive, though I always copy them to this hard drive on a separate partition as well.

 Hard Drives are not so cheap where live. So I'm hoping it at least keep work until this summer if it really has a problem. Lol

---

### Post by srs5694 on 2011-02-02
As we're largely Ubuntu and other Linux users here, "53% health" or "83% health" from an unspecified Windows program means very little to us. I recommend you run one of the Linux SMART utilities I described earlier and post back with information from that.

Also, if hard disks are pricey where you are, knowing where that is might be helpful; somebody might know of a local deal or be able to offer you a used (but healthy) disk.

---

### Post by marl30 on 2011-02-03
> **srs5694 said:**
> As we're largely Ubuntu and other Linux users here, "53% health" or "83% health" from an unspecified Windows program means very little to us. I recommend you run one of the Linux SMART utilities I described earlier and post back with information from that.

Also, if hard disks are pricey where you are, knowing where that is might be helpful; somebody might know of a local deal or be able to offer you a used (but healthy) disk.
I have already installed it. I'll run it probably while I'm going off to sleep. But probably have to read all those command line instructions that goes along with it first. I hope that answers your question why I opted to use Windows disk tools instead.

 I was also tried to setup Seagate's Disk Diagnostic tool, but for some reason the msi file refused to install on XP. And the other reason why I often resort to seeking out alternative solutions, I noticed that when I ask for help hear it sometimes takes forever to get a response, as well as some of my threads are yet to receive an answer. I guess I should try typing shorter posts...lol

---

