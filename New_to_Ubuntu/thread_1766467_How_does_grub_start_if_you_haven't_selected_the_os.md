---
title: "How does grub start if you haven't selected the os yet?"
date: 2011-05-24
forum: New to Ubuntu
---

### Post by Phil Stone on 2011-05-24
If you haven't already selected the os to boot into, how come programs can run already?

or

Which 'scripts' run, from when you turn on the pc to when you can see your desktop ready to go? 
(I assume differences in set up ocur but what is the generic file run order?)

---

### Post by compmodder26 on 2011-05-24
Grub knows which OS to boot without you selecting one because there is default kernel/OS selected already.  This can be adjusted by editing /etc/default/grub.  There should be a line that says "GRUB_DEFAULT=0" (it may be a different number for you).  That number represents the menu entry to boot by default (0 being the first, 1 the second, and so on).

If you edit that number, you'll need to run "sudo update-grub" afterwards for the changes to be saved to grub.

---

### Post by Prince Valiant on 2011-05-24
I'm not exactly sure what you mean, so could you clarify what programs you're referring to?

I'm only partly knowledgeable, so take this with a grain of salt:

The HDD contains partitions (sda1, sda2 on linux and C:, E:, etc on Windows), and the Master Boot Loader (MBR).  The MBR resides on the first 512 KB of the HDD, and the partitions follow it.  

The BIOS of the computer (which is located in a flash-based chip on the motherboard) knows how to read the MBR, and runs the software on it.  That software (After you installed Ubuntu--not through Wubi) is Grub.  Some windows antivirus programs install antivirus software to the MBR to do their scanning *before* Windows boots and the viruses can 'turn on' and avoid detection.

I hope that helps; I'm afraid it may have been totally irrelevant to your question.

Have fun!

-Val

---

### Post by Phil Stone on 2011-05-24
Not quite what I was asking compmodder26, but a little more grub know (:)).  I ask how does the program 'grub' run, being that you have not actually selected the OS to boot into yet. That is, the pc is running programs without the kernel having booted yet?

Ah, thats very helpful Prince Valiant. 

So to extend the question, from grub which files are executed to 'start up' ubuntu, does it just execute the kernel and leave the kernel to do the rest?
or does it execute a list of programs starting with the kernel before goin on to other programs such as services set up and ending with desktop Environment?

---

### Post by Skaggz on 2011-05-24
GRUB isn't part of any OS.  It's all by itself at the beginning of your hard drive.  The BIOS is set to boot from different hardware in a specific order.  If it doesn't find a boot loader then it moves on to the next one.  When it finds a boot loader, it runs that program.  The boot loader is then what loads the operating system.

Even when you only have Windows loaded on your computer, it still looks for and runs the boot loader first.  You just don't see it because there is only one OS option to load.

The reason we use GRUB is because the Windows boot loader doesn't play well with other (non-Microsoft) operating systems.

---

### Post by oldfred on 2011-05-24
While it primarily is discussing windows, the process applies to all BIOS/MBR based PCs.

Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)

Macs & some new PCs with EFI and gpt work somewhat differently.
[http://en.wikipedia.org/wiki/UEFI](http://en.wikipedia.org/wiki/UEFI)
[http://en.wikipedia.org/wiki/GUID_Partition_Table](http://en.wikipedia.org/wiki/GUID_Partition_Table)

---

### Post by compmodder26 on 2011-05-24
> **Phil Stone said:**
> So to extend the question, from grub which files are executed to 'start up' ubuntu, does it just execute the kernel and leave the kernel to do the rest?
or does it execute a list of programs starting with the kernel before goin on to other programs such as services set up and ending with desktop Environment?

Once grub loads and either an entry is selected by you or it is run automatically, it will start the kernel in the location that is specified for that menu entry.  Once the kernel is loaded then the init scripts start to load.  This page gives some good information on how the init script process works:

[http://www.marzocca.net/linux/bumdocs.html](http://www.marzocca.net/linux/bumdocs.html)

---

### Post by Phil Stone on 2011-05-24
great stuff oldfred. I didn't know there was a Partition Boot Loader and this makes more sense about why partition resizing is so complicated.

Thanks compmodder thats kinda what I was after too.

Phil :)

---

### Post by compmodder26 on 2011-05-24
Wiki has an overview for you on the linux boot process:

[http://en.wikipedia.org/wiki/Linux_startup_process](http://en.wikipedia.org/wiki/Linux_startup_process)

---

### Post by srs5694 on 2011-05-24
> **Prince Valiant said:**
> I'm only partly knowledgeable, so take this with a grain of salt:

The HDD contains partitions (sda1, sda2 on linux and C:, E:, etc on Windows), and the Master Boot Loader (MBR).  The MBR resides on the first 512 KB of the HDD, and the partitions follow it.

A couple of corrections. First, "MBR" stands for "Master Boot Record," not "Master Boot Loader." The MBR contains both the first boot loader code and the partition table (on disks that use the old MBR partitioning system).

Second, the MBR is *one sector* in size, which is normally 512 *bytes*, not 512 KB -- that's 1,000 times smaller. Very little code can fit in the MBR, especially with the partition table also crammed in there. The authors of boot loaders, and especially complex ones like GRUB, have had to jump through quite a few awkward hoops to get it all to work. (See below.)

> The BIOS of the computer (which is located in a flash-based chip on the motherboard) knows how to read the MBR, and runs the software on it.  That software (After you installed Ubuntu--not through Wubi) is Grub.

Because of the size limits of the MBR, GRUB actually installs bits of itself all over the place. On an MBR disk, these can include the MBR itself, some officially-unallocated sectors immediately after the MBR, code in the boot sectors of Linux partitions, and files in Linux filesystems. It's the same with the GUID Partition Table (GPT) disks that oldfred mentioned, at least when the computer is based on BIOS, except that a special BIOS Boot Partition substitutes for the unallocated space following the MBR.

EFI-based systems are different; their firmware is more complex and can read boot loader code from a filesystem in an EFI System Partition. This simplifies boot loader installation and maintenance, at least from a theoretical perspective. With EFI, there's no need for code in the MBR, in the sectors following the MBR, or in partition boot sectors; instead, a complete EFI boot loader application is dropped in the EFI System Partition and the EFI can then run it. This makes for less inter-OS conflict over boot loaders and it simplifies certain types of system recovery (such as copying an installation to a new disk).

---

### Post by Prince Valiant on 2011-05-25
Thanks, srs5694.  Always glad to understand things a bit better.  :-D

-Val

---

