---
title: "Help, Problem in Partitions."
date: 2011-02-23
forum: New to Ubuntu
---

### Post by Linyx on 2011-02-23
I had just tried to install Backtrack-4 in Extended partition and it install fines ,for some reason i delete it then.

I have attached a Screen-Shot, Now i can't use the Bottom-Unallocated space and it warns me that you can't make primary more.. However, that was a part of extended before installation and now it become primary...!!

Is their any method of moving this partition to Extended..?

thanks,

---

### Post by Linyx on 2011-02-23
I have also Remove XP because i don't need it Anymore...Now my Partitions looks like > **Screen-Shot**.

Any method so that my last Unallocated space move to Extended...? it neither moves, I am from Live-Session.. :(

---

### Post by indytim on 2011-02-23
withdrawn

---

### Post by srs5694 on 2011-02-23
First, unallocated space is by definition not a partition. Think of it like this: Partitions are like chairs and other furniture arranged against a wall. You can move them around, remove them, etc., but the space between the furniture is just empty space, not furniture itself.

There is one partial exception to this rule, and it's part of your problem: Because of the annoying hack known as extended and logical partitions, space that can be used by logical partitions must be enclosed in an extended partition. Thus, some free space (including some in the screen shots you posted) is allocated to the extended partition in the primary partition table, but is unallocated within the extended partition. Going back to the furniture analogy, you can think of an extended partition as being a table on which you place chairs. (Why you'd want to do this is another matter -- but I did say the whole extended/logical partition thing is a hack!)

As to your specific situation, some of your free space is in the primary partition table and part of it is within the extended partition. You can easily adjust which is which by resizing the extended partition (/dev/sda4 in your case). You'll need to do this after disabling swap space, since GParted refuses to resize extended partitions if any of the partitions they contain are in use.

Given that you've deleted /dev/sda1 and /dev/sda2, you've now got two free primary partitions. (You can have at most four primary partitions, and the extended partition counts as one primary partition.) Thus, you have a choice of creating new partitions as either primary or logical, with the caveat that you can't create more than two more primary partitions.

If you want to create one big new partition, you'll need to move and/or resize some of your existing partitions. GParted can do this, but you should be very cautious; partition resizing and moving operations are inherently time-consuming and risky, especially if you move the start point of the partition. GParted refuses to work on any currently mounted partition, so you may need to unmount partitions or even boot using an emergency disc to do the work.

Another point: The whole primary/extended/logical mess is part of the Master Boot Record (MBR) partitioning system. If you don't plan to re-install Windows on this disc, you could convert it from MBR to GUID Partition Table (GPT) form, which does away with this distinction, which can simplify the sorts of manipulations you're facing. (GPT supports up to 128 partitions by default, with no primary/extended/logical distinctions.) Converting from MBR to GPT will require you to re-install GRUB, though, and there's a chance you'll run into other problems, so do this only if you're willing to deal with the consequences. Windows can't boot from a GPT disk on a BIOS-based computer, so this isn't a good option if you plan to re-install Windows on this disk. I recommend GPT for new Linux-only installations, but I suspect the risks are too great for your specific case. I mention the possibility mainly to be complete. If you decide you want to try it, you'll need to use [GPT fdisk (gdisk)](http://www.rodsbooks.com/gdisk/) to do the conversion; GParted and other libparted-based tools will wipe out your existing partitions if you try to convert to GPT, but gdisk will convert without damaging the existing partitions.

One final point: If the computer won't be booting Windows at all, I strongly recommend you convert your two NTFS partitions to use a Linux native filesystem, or move the data from those partitions into other Linux partitions. The reason is that Linux has only very rudimentary NTFS maintenance tools. Thus, if you shut down uncleanly (say, because of a power failure or system crash), or if those partitions develop problems, you'll be unable to access them unless and until you fix them with Windows -- but without Windows installed on the computer, performing such a check will be a hassle at best. Unfortunately, there is (AFAIK) no tool to convert from NTFS to any Linux-native filesystem without data loss. Thus, you'll need to create new partition(s) in a Linux-native format, copy the data, delete the existing partitions, and then re-use that space. Of course, if you plan to re-install Windows, or if it's installed on another disk, using NTFS for shared data space makes sense, so you probably want to keep those partitions as-is.

---

### Post by Linyx on 2011-02-23
> **srs5694 said:**
> 
As to your specific situation, some of your free space is in the primary partition table and part of it is within the extended partition. You can easily adjust which is which by resizing the extended partition (/dev/sda4 in your case). You'll need to do this after disabling swap space, since GParted refuses to resize extended partitions if any of the partitions they contain are in use.


That Worked for me, thanks :P.

> If the computer won't be booting Windows at all, I strongly recommend you convert your two NTFS partitions to use a Linux native filesystem, or move the data from those partitions into other Linux partitions. The reason is that Linux has only very rudimentary NTFS maintenance tools.I Use NTFS because sometimes i need Windows.

> The whole primary/extended/logical mess is part of the Master Boot Record (MBR) partitioning system. If you don't plan to re-install Windows on this disc, you could convert it from MBR to GUID Partition Table (GPT) form, which does away with this distinction.....Didn't get the term **GPT**, may be I could study it sometimes,

Another Question, [SIZE=2]Why PRIMARY Partitions are always four(or less then)[/SIZE]..... :confused:

---

### Post by srs5694 on 2011-02-23
See [this Wikipedia page](http://en.wikipedia.org/wiki/GUID_Partition_Table) for technical details on GPT, [this Web page of mine](http://nessus.rodsbooks.com/gdisk/whatsgpt.html) for a less technical introduction, or [this article I wrote](http://www.ibm.com/developerworks/linux/library/l-gpt/index.html) for IBM developerWorks for another introduction to GPT.

Primary partitions are limited to four because the data structures are designed that way. You can see [this Wikipedia article](http://en.wikipedia.org/wiki/Master_boot_record) for the technical details. If you don't want that level of technical detail, think of it like the physical drawers in a file cabinet: You've only got so many, and short of redesigning the file cabinet, you can't add more drawers. Logical partitions, and partitions in other partitioning systems such as GPT, are not so limited because the data structures are different, like a file cabinet that's designed with many more drawers than the 4-drawer MBR file cabinet.

---

### Post by Linyx on 2011-02-24
Thanks for nice information, I will study it & will post back if i don't understand any point,:popcorn:

---

