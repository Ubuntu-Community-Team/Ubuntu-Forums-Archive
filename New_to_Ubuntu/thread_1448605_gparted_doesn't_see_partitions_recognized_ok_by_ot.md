---
title: "gparted doesn't see partitions recognized ok by other aps"
date: 2010-04-06
forum: New to Ubuntu
---

### Post by LewRockwellFAN on 2010-04-06
I've tried booting from another HD and from the karmic livedisk. Either way, Gparted sees my 500 GB Seagate as a diskfull of unpartitioned space. Nautilus and the native search ap don't seem to have any problems seeing the partitions on this disk or reading the files in them.  I'm pretty sure the partitions were made with Gparted run from the same karmic 32 livedisk. I COULD just repartition and start over as the data on them has one (count em, 1) backup copy on another HD, but 

A- I get nervous having only one copy of my data, even if it is only for a short while and on a unconnected disk. 

&

B- I'd really like to UNDERSTAND this. Even if I can get around it now, I always suspect things I don't understand of planning to bite me when I least expect it.

I saw the thread where a chap had similar problems after cloning partitions to smaller partitions but that doesn't seem applicable. The partitions in question were created de novo where they are and filled with data in situ. Clonezilla hasn't touched them.

I want to use Gparted to resize the partitions before installing Sabayon and Ubuntu 64 on the first two partitons. I'm comfortable with that level of risk to my data since 1) I DO have the aforementioned 1 copy and 2)I've never lost data from resizing with Gparted before (of course it has never refiused to see my partitions before either).

---

### Post by louieb on 2010-04-06
Probably a non-standard partition table. For example a primary partition inside an extended partition - not suppose to happen - but some partition software will do it anyway. (Disk Drake and some Windows software)   

Gparted see that and show the disk a being un-formatted  Post the output of
```
sudo fdisk -l 
```( lowercase L at the end)

---

### Post by LewRockwellFAN on 2010-04-06
*Thanks, louieb.*


ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9ffddd40

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4569    36700461    7  HPFS/NTFS
/dev/sda2            4570        6609    16384000   83  Linux
/dev/sda3            6610        7377     6168928    c  W95 FAT32 (LBA)
/dev/sda4            7378       60802   429136312+   f  W95 Ext'd (LBA)
/dev/sda5            7378       10185    22555228    c  W95 FAT32 (LBA)
/dev/sda6           10186       35492   203278446    c  W95 FAT32 (LBA)
/dev/sda7           35493       60801   203289600    7  HPFS/NTFS
ubuntu@ubuntu:~$ 

[I]I don't recall doing anything that struck me as weird when I partitioned that drive. The first was a Windows 7 beta partition (now to be deleted), the second was, I think, a karmic 64 bit partition, and the others were for data. Perhaps W7 did something odd. Come to think of it, I'm pretty sure W7 creates a small partition that doesn't show here and also uses some unpartitioned space for some mysterious purpose. I'd like to hang on to the stuff in the data partitions if possible without moving heaven and earth. But mainly, I'd like to understand it.
[/I]

---

### Post by srs5694 on 2010-04-06
> **LewRockwellFAN said:**
> [I]I don't recall doing anything that struck me as weird when I partitioned that drive. The first was a Windows 7 beta partition (now to be deleted), the second was, I think, a karmic 64 bit partition, and the others were for data. Perhaps W7 did something odd. Come to think of it, I'm pretty sure W7 creates a small partition that doesn't show here and also uses some unpartitioned space for some mysterious purpose. I'd like to hang on to the stuff in the data partitions if possible without moving heaven and earth. But mainly, I'd like to understand it.
[/I]

At first glance, your fdisk output looks OK to me. Some comments on your above paragraph:


[list]
[*]Linux's fdisk is very good about showing all partitions; there should be no partitions that don't show up unless the partition table is damaged (lost logical partition links, say), but nothing jumps out at me as likely in that respect.
[*]Many boot loaders, including GRUB Legacy in some cases, do place code in the unpartitioned space between the MBR and the start of the first partition. Some viruses also use this space. It's an ugly and dangerous practice.
[/list]


There was another thread here a while ago about GParted not showing partitions, and that problem was solved by the person launching fdisk and using it to re-save the partitions. That is, type "sudo fdisk /dev/sda", type "p" to verify you're working on the correct disk, and then type "w" to save the partition table. The problem was a subtle error in the logical partition definitions. This error caused GParted to flake out completely, whereas fdisk produced an error message when launched but corrected the problem on save. OTOH, I can't guarantee this will solve the problem, and there's a slim chance that it'll actually make matters worse. The odds of this are very small, though, if fdisk displays the partitions you know to be present when you type "p" at its main menu, so I'd say it's worth taking the very minor risk.

---

### Post by LewRockwellFAN on 2010-04-06
Thanks, [srs5694]("http://ubuntuforums.org/member.php?u=1032238"). OK, I did that, just as you suggest. Output indicated the kernel would continue to use the old partition table until I rebooted so I rebooted. Nothing seems to have changed. Nautilus and Search have no problems finding data on the HD and see the partitions expected. Gparted sees only unallocated space. There is no possibility of it looking at the wrong drive as I only have the one connected now. I'd think Gparted was corrupted if it weren't for the fact I got the same results running it from another HD that I'm now getting running it from the LiveCD. And also that it saw the partitions in the other disk just fine. I'm mystified.

---

### Post by louieb on 2010-04-07
like srs5694 - don't see anything wrong - no partitions out of place - no overlapping partitions.  May be a Gparted problem - would like to take another look at the sector level. Post the output of  

Just make sure the /dev/sd@ part is pointing to the right hard drive. 

```
sudo sfdisk -d /dev/sd[COLOR=Red]a[/COLOR]
```

Don't think there is partition table problem but - [sfdisk to fix partition table problems]("http://ubuntuforums.org/showthread.php?t=1192598")

---

### Post by LewRockwellFAN on 2010-04-07
Thanks, louieb.
As you directed:

ubuntu@ubuntu:~$ sudo sfdisk -d /dev/sda
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size= 73400922, Id= 7, bootable
/dev/sda2 : start= 73401111, size= 32768000, Id=83
/dev/sda3 : start=106173648, size= 12337856, Id= c
/dev/sda4 : start=118511505, size=858272625, Id= f
/dev/sda5 : start=118511568, size= 45110456, Id= c
/dev/sda6 : start=163622088, size=406556892, Id= c
/dev/sda7 : start=570187776, size=406579200, Id= 7
ubuntu@ubuntu:~$ 

I can add one new datum. When I boot with a Sabayon live DVD the symptoms are exactly the same. I can browse and search all partitions, read and write files, etc. No ap but Gparted sees any problem. So, yes, almost certainly a Gparted issue.

Perhaps I'll try booting from that W7 beta partition and see if I can do anything with the W7 partitioner. Or from a W2k IDE I could hook up. But even if that works, I'm not sure I'd be any closer to understanding WHY Gparted is playing dumb.

Hmmm ... Texas, 4 hours ago ... no wonder this place has a coffee theme.

---

### Post by LewRockwellFAN on 2010-04-07
More info:

I got the latest Gparted livedisk, 0.5.2-1 and tried with it. Still the same story.

After trying and failing to boot from the W7 partition I thought hard about the history of this drive. It was working fine as far as I knew (but then, if I weren't trying to resize the partitions, but merely read and write data from/to it I probably wouldn't suspect a problem now) up until I tried to install FreeDOS over the W7 in the first primary (oh yeah, guess that's why W7 doesn't boot, duh). The FreeDOS installation failed complaining of unsupported hardware and then I couldn't access ANY of the drive. I used testdisk to restore the partitions and it seemed to work fine. So the present partition table was created by testdisk.

Now when I use testdisk, run from another HD under Karmic, before checking for partitions it claims it sees "hidden sectors" (or maybe it was singular "sector", I forget) and asks if I want to continue DESPITE [emphasis mine] the hidden sector(s). Not sure if "despite" was the actual word but that was clearly the sense, as if to implicitly warn that hidden sectors might screw things up. Anyway I chose to continue and it saw my partitions just fine. I quit without making any changes. Now, I'll go try to find out something about "hidden sectors" and testdisk.

---

### Post by J V on 2010-04-07
This might be a stupid question but, did you switch hard-drive (Upper right hand corner) to the correct HD? It won't show anything but the current HD...

---

### Post by LewRockwellFAN on 2010-04-07
JV, thanks for the response.

Not a stupid QUESTION at all. I am quite capable of doing stupid THINGS but that was not one of them this time. :)
Yes, I realize how it defaults and I did change drives.  I also have the same problems when I boot from Ubuntu 9.1 32 bit, Sabayon 5.1 64 bit, or Gparted's standalone live CDs, all the most current versions.

There are apparently some problems with the version of Gparted in Ubuntu and the 
Gparted people are plastering big warnings on their site about using less than current versions. When I saw that I figured that was it, but apparently not.

 Currently I'm reading about compatibility weirdness that MS introduced to their partitioner with Vista, on the assumption it still persists in W7 as the partitions in question may well have been created in the W7 installation process. At the very least I suspect it modified the first one by splitting it into two thingamabobs kinda like logical partitions inside a primary (I may be way off base here, but MS does seem to love to thumb their nose at accepted standard practices and the more basic the level, and the more trouble it can cause people using non MS software or less than the latest and most expensive VERSION of MS software, the better. They have a history of this that goes back at least to the days of the struggle between MS DOS and DR DOS).

---

### Post by srs5694 on 2010-04-07
According to fdisk, your disk is 500107862016 bytes, or 978726293 sectors, in size. According to sfdisk, your partition #4 begins at sector 118511505 and is 858272625 sectors long, meaning it ends at sector 978784129 -- 1942164 sectors (close to 1GB) *after* the end of the disk! Fortunately, the last logical partition ends at sector 976766975, so you should be able to correct the problem. There is some risk in what I'm about to suggest, so proceed with caution and check my arithmetic:


[LIST=1]
[*]Put your sfdisk output in a text file (say, parts-sda.txt).
[*]Back up the text file and store the backup on a removable disk (floppy, USB flash drive, CD-R, whatever).
[*]Load the text file into an editor.
[*]Change the length of /dev/sda4 from 858272625 to 858255471. (That is, long enough to cover the last logical partition but no more. Alternatively, you could make it extend to the last sector of the disk, or any sector in-between the two.) This is where you should check my arithmetic.
[*]Save the changes and exit from the text editor.
[*]Type "sudo sfdisk --force /dev/sda < parts-sda.txt". (Change the filename if necessary.)
[/LIST]


When I did this in a QEMU session with a simulated disk of exactly the correct size, the text-mode GNU Parted in Ubuntu 9.04 was happy with the resulting disk. (For some reason X didn't start on this system, so I couldn't test GParted.)

This is a potentially risky operation; a mistake could create a very flaky partition table. If you have problems, use the sfdisk command to restore the original partition table.

Of course, this leaves the question: How did you get an extended partition on the disk bigger than the disk? It could have been a phenomenally buggy program (it could be a fairly simple bug, of course, but it's obviously a really *bad* bug); or it could be that the disk was a direct dd copy from a disk that was actually slightly larger than the original. That's one of the dangers of a direct dd copy of a disk.

---

### Post by psusi on 2010-04-07
What does fdisk -lu /dev/sda say?  Also try the command line parted: parted /dev/sda then print.

---

### Post by LewRockwellFAN on 2010-04-07
> **srs5694 said:**
>  ... Of course, this leaves the question: How did you get an extended partition on the disk bigger than the disk? It could have been a phenomenally buggy program (it could be a fairly simple bug, of course, but it's obviously a really *bad* bug); or it could be that the disk was a direct dd copy from a disk that was actually slightly larger than the original. That's one of the dangers of a direct dd copy of a disk.

Thanks, srs5694.

I will study your procedure and the method you used to reach your conclusion and report back. Sounds like the answer.

As to the origin, no dd or clone tools or any such were used. The partitions were created from scratch on that drive, originally by either gparted or the W7 installer, I forget which. Then presumably borked by the FreeDOS installer and fixed (kinda, sorta) by testdisk. I'm thinking this may have something to do with changes in the Windows installer partitioning setup that began with Vista, with further small changes in W7 in addition I understand. Possibly either FreeDOS or testdisk or both doesn't understand the new MS approach.

---

### Post by srs5694 on 2010-04-07
> **LewRockwellFAN said:**
> As to the origin, no dd or clone tools or any such were used. The partitions were created from scratch on that drive, originally by either gparted or the W7 installer, I forget which. Then presumably borked by the FreeDOS installer and fixed (kinda, sorta) by testdisk. I'm thinking this may have something to do with changes in the Windows installer partitioning setup that began with Vista, with further small changes in W7 in addition I understand. Possibly either FreeDOS or testdisk or both doesn't understand the new MS approach.

Possibly, but I doubt it. The old MBR partitioning method paid a lot of attention to cylinders, aligning partitions to begin on cylinder boundaries. This made sense back in the 1980s, but cylinder boundaries have been entirely fictitious for about fifteen or twenty years. The new method makes more sense with RAID arrays and the new disks with 4096-byte physical sectors. With such systems, you need to align partitions on 4KB to 256KB boundaries for optimal performance. Microsoft therefore began aligning partitions on 1MB boundaries, presumably just to play it safe, and Linux tools are beginning to follow suit. Some very old OSes and tools, such as DOS, get confused by this, but Linux is certainly fine with it.

It's hard to imagine how such a change to partition alignment policy would cause any disk utility to push the *end* of a partition out nearly 1GB beyond the end of the disk. It's more likely that a utility would balk at the disk or shift the start and/or end of a partition to align to the nearest cylinder boundary (not nearly 1GB). That said, I've encountered weirder bugs so I can't really rule out the hypothesis entirely. If this hypothesis is correct, then it was most likely FreeDOS that did the deed.

If I had to place a bet, though, it would be testdisk; it may have misinterpreted some random data as a logical partition definition and extended the extended partition definition to include it, then deleted the faux logical partition without reversing the incorrect extended partition resize. I'm far from certain of this hypothesis, though. If nothing else, I'd expect its error to be far worse in this case; errors caused by interpreting random data tend to be huge, although they *can* be small. Certainly you've used enough partitioning tools to make for plenty of suspects.

---

### Post by LewRockwellFAN on 2010-04-07
> **psusi said:**
> What does fdisk -lu /dev/sda say?  Also try the command line parted: parted /dev/sda then print.

psusi (psilent p, I assume? :) ), thanks for you attention.

It says very little:

[I]ubuntu@ubuntu:~$ fdisk -lu /dev/sda
Cannot open /dev/sda
ubuntu@ubuntu:~$ [/I]

I thought perhaps the "/sd**a**" was being so designated by virtue of which SATA cable was attached despite the fact there is only one HD connected atm. So, since I have it on the second cable I tried:

[I]ubuntu@ubuntu:~$ fdisk -lu /dev/sd**b**
ubuntu@ubuntu:~$ [/I]

and, as you can see, just got a return of the prompt.

I don't know what to make of either.

I checked with Gparted again and it still reports /sd**a** as 465.76 GiB of unallocated space. /sd**a** is the only drive it sees. The drop down drive selector in the upper right shows no other choice, as, of course, is proper, since it is the only drive connected. I explicitly mention it because it was questioned earlier and because I hadn't changed to the 1st cable.

As for the second suggestion:

[I]ubuntu@ubuntu:~$ parted: parted /dev/sda
No command 'parted:' found, did you mean:
 Command 'parted' from package 'parted' (main)
parted:: command not found
ubuntu@ubuntu:~$[/I]

hmmm ... I guess that was dumb of me. Second try:

[I]ubuntu@ubuntu:~$ sudo gparted
======================
libparted : 1.8.8.1.159-1e0e
======================
Can't have a partition outside the disk!
[/I]
which started the gui for gparted and did NOT return a prompt. The GUI Gparted still showed the same thing.

Still not sure if that is what you had in mind. Maybe this:

[I]ubuntu@ubuntu:~$ sudo parted /dev/sda
GNU Parted 1.8.8.1.159-1e0e
Using /dev/sda
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted)[/I]

Or maybe I'm to treat that last line as a prompt and enter "[I]/dev/sda" thus:

(parted) /dev/sda
  check NUMBER                             do a simple check on the file system
  cp [FROM-DEVICE] FROM-NUMBER TO-NUMBER   copy file system to another partition
  help [COMMAND]                           print general help, or help on COMMAND
 ...
  unit UNIT                                set the default unit to UNIT
  version                                  display the version number and copyright information of GNU Parted

[/I]That looks like a help page. I edited out the middle as I presume that is not what you want.

Entering "parted /dev/sda " (sans "") and ENTER after the (parted) prompt gets me the same help file.

I think I must be missing something. Sorry.

---

### Post by LewRockwellFAN on 2010-04-07
> **srs5694 said:**
> Put your sfdisk output in a text file (say, parts-sda.txt).me 

Should this include the prefatory lines as follows?

[I]# partition table of /dev/sda
unit: sectors

/dev/sda1 : start= 63, size= 73400922, Id= 7, bootable
/dev/sda2 : start= 73401111, size= 32768000, Id=83
/dev/sda3 : start=106173648, size= 12337856, Id= c
/dev/sda4 : start=118511505, size=858272625, Id= f
/dev/sda5 : start=118511568, size= 45110456, Id= c
/dev/sda6 : start=163622088, size=406556892, Id= c
/dev/sda7 : start=570187776, size=406579200, Id= 7
[/I]

---

### Post by LewRockwellFAN on 2010-04-07
> **srs5694 said:**
>  ...

[LIST=1]
[*]Change the length of /dev/sda4 from 858272625 to 858255471. (That is, long enough to cover the last logical partition but no more. Alternatively, you could make it extend to the last sector of the disk, or any sector in-between the two.) This is where you should check my arithmetic.
[*]Save the changes and exit from the text editor.
[*]Type "sudo fdisk --force /dev/sda < parts-sda.txt". (Change the filename if necessary.) ...
[/LIST]


I like your arithmetic and your logic fine. Both make sense to me. But fdisk doesn't like your syntax. As you can see I also tried it with a single dash with the same result:

ubuntu@ubuntu:/media/DAT 1 BL-A9/0_new_stuff_notonWDyet$ sudo fdisk --force /dev/sda < newtable.txt
fdisk: invalid option -- '-'

Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors
ubuntu@ubuntu:/media/DAT 1 BL-A9/0_new_stuff_notonWDyet$ sudo fdisk -force /dev/sda < newtable.txt
fdisk: invalid option -- 'f'

Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors
ubuntu@ubuntu:/media/DAT 1 BL-A9/0_new_stuff_notonWDyet$

---

### Post by LewRockwellFAN on 2010-04-07
> **LewRockwellFAN said:**
>  ... But fdisk doesn't like your syntax.  ... 

AHAAAAA!!!!!!!
Stupid me. Of COURSE you meant[SIZE=3]_** S**_[/SIZE]fdisk. Context should have made that clear. 
Worked like a charm. Thanks srs, et al, for your wisdom. :P

Now to figure out how to  mark this solved ...

---

### Post by srs5694 on 2010-04-07
Sorry about the mistake in the command name. I've corrected it in my original post in case anybody runs across this thread in the future and needs to try something similar.

Incidentally, most of psusi's commands just needed to be preceded by "sudo" to work (although they wouldn't really solve the problem or provide information you didn't already have). Disk manipulation commands (fdisk, sfdisk, parted, gparted, etc.) all require root privileges, and as such must normally be launched via sudo in Ubuntu. (The alternative is logging in as root, but Ubuntu's design makes this impossible by default. This can be changed, but I believe doing so is officially discouraged by the Ubuntu developers.) It looks like you don't have GNU Parted (command name "parted") installed. You can install it by typing "sudo apt-get install parted" or by using Synaptic to locate and install it. GNU Parted is a text-mode tool that's closely related to the GUI GParted.

---

### Post by psusi on 2010-04-07
Yes, you needed a sudo for the fdisk and you wanted to enter the print command to the parted prompt.  It looked to me like the problem was the partition extending beyond the end of the drive, but I am not familiar with sfdisk so I wanted to make sure with fdisk.

---

### Post by louieb on 2010-04-07
Glad someone has better eyes than me - just did not see the extended partition going past the end of disk. 
Probably had a brain fart and forgot to look.

---

### Post by LewRockwellFAN on 2010-04-08
srs5694, psusi - Thank you, both.

srs5694, No problem. I was being dumb. Context made it obvious what you meant after a moments thought.

> **srs5694 said:**
> The alternative is logging in as root, but Ubuntu's design makes this impossible by default. This can be changed, but I believe doing so is officially discouraged by the Ubuntu developers.)

Want to point me toward a link on this subject? I thought Linuxes were about freeing me to do dumb things and learn from my mistakes. I'm getting increasingly annoyed by permission hell. Find myself wanting to scream "It's MY @!#!@!!! data! If I wanna bend, fold, mutilate, and overwrite it, I WILL!"

---

### Post by srs5694 on 2010-04-08
> **LewRockwellFAN said:**
> Want to point me toward a link on this subject? I thought Linuxes were about freeing me to do dumb things and learn from my mistakes. I'm getting increasingly annoyed by permission hell. Find myself wanting to scream "It's MY @!#!@!!! data! If I wanna bend, fold, mutilate, and overwrite it, I WILL!"

Here's an official page on the topic:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Note that if you're having problems accessing your *user* data (word processing documents, MP3s, etc.), chances are you can correct the problem with a single use of chown or chmod (if it's a Linux filesystem) or by altering mount options in /etc/fstab (if it's a Windows filesystem). If you need to frequently mess with *system* data (files in /etc, for instance), then chances are your system is configured sub-optimally in some way or you don't understand how to set user-level options. In either case, creating a new thread to ask about the problem is in order. With few exceptions (people writing low-level utilities or servers, for instance), you shouldn't need to use root privileges very often.

---

### Post by LewRockwellFAN on 2010-04-11
> **srs5694 said:**
> Here's an official page on the topic:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Note that if you're having problems accessing your *user* data (word processing documents, MP3s, etc.), chances are you can correct the problem with a single use of chown or chmod (if it's a Linux filesystem) or by altering mount options in /etc/fstab (if it's a Windows filesystem). If you need to frequently mess with *system* data (files in /etc, for instance), then chances are your system is configured sub-optimally in some way or you don't understand how to set user-level options. In either case, creating a new thread to ask about the problem is in order. With few exceptions (people writing low-level utilities or servers, for instance), you shouldn't need to use root privileges very often.

Thanks, srs5694. I've cottoned on to the fact I need to study fstab editing and use of chmod and chown. But now I'll study this link also. Maybe I don't need it but it sounds like fun.

---

