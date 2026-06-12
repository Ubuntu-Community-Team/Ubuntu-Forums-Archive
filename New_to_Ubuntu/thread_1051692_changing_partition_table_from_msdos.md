---
title: "changing partition table from msdos?"
date: 2009-01-27
forum: New to Ubuntu
---

### Post by minsf on 2009-01-27
i want to format an entire external HD as ext3. 
do i have to choose msdos partition table in gpart(Device>CreatePartitionTable)? 
is there something that is more native to ext3?
(rather than having my ext3 sitting in a disk with "capabilities: partitioned partitioned:dos")
my options (in gpart>Device>Create Partition Table) are: msdos, aix, amiga, bsd, dvh, gpt, mac, pc98, sun, loop

---

### Post by theozzlives on 2009-01-27
In Gparted, go to the partition menu. You'll have to unmount > delete > new, then select ext3.

---

### Post by Boomhauer on 2009-01-27
once you create the partitions and apply the changes, it should create the partition table for you.

---

### Post by minsf on 2009-01-27
> **theozzlives said:**
> In Gparted, go to the partition menu. You'll have to unmount > delete > new, then select ext3.
then the ext3 will sit in a dos partition table. is this really necessary?

---

### Post by minsf on 2009-01-27
> **Boomhauer said:**
> once you create the partitions and apply the changes, it should create the partition table for you.
i have already done this one time. the partition table remained msdos (framing the ext3 primary partition).

---

### Post by caljohnsmith on 2009-01-27
Normally you should use the standard "MS-DOS" partition table, unless you have an Apple computer, because they typically use a GPT (GUID Partition Table) instead. Don't worry, an MS-DOS partition table is fully compatible and supported by Linux. :)

---

### Post by minsf on 2009-01-30
What if I want to break it into 10 ext3 partitions or more (because the drive is big=1TB), should i still use msdos partition table (=disk label)?
can i boot from a partition which is in an extended partition? i would love to try 5 other distributions- will they boot if they are not primary partitions?

---

### Post by Cypher on 2009-01-30
You can only have 4 primary partitions, but you can have a lot of logical partitions. So you 'd create up to 3 primary partitions and then the 4th should be an extended partition that spans the rest of the HD. Within that extended partition you can create lots of logical partitions.

Linux can definitely boot from logical partitions no problem.

---

### Post by minsf on 2009-01-31
> **Cypher said:**
> You can only have 4 primary partitions, but you can have a lot of logical partitions. So you 'd create up to 3 primary partitions and then the 4th should be an extended partition that spans the rest of the HD. Within that extended partition you can create lots of logical partitions.

Linux can definitely boot from logical partitions no problem.

thanks! this was helpful.

isnt there a more modern partition table that works better with ext3 and huge external HD than msdos partition table, given that i will never need any fat or ntfs on this drive?

---

### Post by perkhouse on 2009-03-13
> **minsf said:**
> 
isnt there a more modern partition table that works better with ext3 and huge external HD than msdos partition table, given that i will never need any fat or ntfs on this drive?
Good question! (I'd like to know the answer as well.)

---

### Post by Intrepid Ibex on 2010-03-21
> **minsf said:**
> thanks! this was helpful.

isnt there a more modern partition table that works better with ext3 and huge external HD than msdos partition table, given that i will never need any fat or ntfs on this drive?
I usually don't bump a year old thread but in this case somebody probably wants to know the answer.

The answer is: no. They  are just different formats of how the beginning of your hard disk is organized. The partition table only needs to be changed when some of the OSses you have on your HD doesn't understand the default MSDOS partition table. There is no "new linux table", though.

---

### Post by JKyleOKC on 2010-03-21
> **Intrepid Ibex said:**
> They  are just different formats of how the beginning of your hard disk is organized.Perhaps a little more detail will help remove some of the confusion about partitioning...

Somewhere back in the dark days before personal computers existed, a sector size of 512 bytes became the industry standard for floppy disks. It probably originated at IBM, and since in those times IBM and computers were essentially synonymous, took over the world.

Incidentally, a "sector" is the smallest unit of data that can be moved onto or off of a disk. Each disk surface is divided into sectors, in a somewhat arbitrary fashion, and the controller hardware moves data a full sector at a time.

When hard disks came into use, it became necessary to have a standard way for machines to determine where on the disk the sectors that contained the boot-up program were located. The standard that emerged was that this information would be placed in the first sector of the first track (in geek-speak, at cylinder 0, track 0, head 0, since at power-up all the address variables were already set to zero), which became known as the "Master Boot Record" or MBR.

Consequently the BIOS chip on any IBM-compatible (that is, just about all except Apple these days) machine will go to this standard MBR location to load the actual boot code at power-up time. But 512 bytes is not very much space, so the MBR contains only enough code to grab the actual boot program from elsewhere on the drive.

Still, the disks even in the earliest times had too many sectors to deal with easily, so the partition table was born. Its purpose is to divide the total disk capacity into parts that are smaller; the reason smaller sizes were needed is a bit technical: earlier (16-bit) systems couldn't handle address values greater than 32,767 so without partitioning, a drive's size would be extremely limited. By dividing the drive into partitions, and then subdividing each partition into cylinders, heads, and tracks, it became possible to deal with drives as large as 8.3 GB. For anything larger, additional disk manager programs had to be installed -- and this was still the case as recently as 1995!

However the table identifying the partitions had to be made part of the MBR, where space was already at a premium. Consequently table has only enough space to describe four partitions. Each entry contains a byte identifying its type, plus a starting location and an ending location. The locations include the cylinder, head, and sector addresses, which the controller uses. Modern BIOS code also allows other address conventions, which allow the disk capacity to go into the terabyte region.

To permit more partitions, as drive sizes increased, the "extended" partition was invented. Its table entry is exactly like that for a primary, except that its "type" byte marks it as extended. Such a partition starts with its own "boot record" that doesn't need to be read by BIOS and as a result can contain many more table entries. Disk management programs know how to use these extended partitions and do so automagically.

The code that BIOS reads from the MBR can be anything at all; it doesn't depend on the type of operating system to be loaded, because it runs before any system at all is in place. Some types of viruses replace the MBR code with their own, so that they can do their dirty work undetected by the system. The "normal" (IBM compatible, now known as the MS-DOS table) code simply goes to a defined disk address, loads the data found there into a defined area of RAM, and jumps to the newly loaded code to continue booting. If GRUB is installed into the MBR, it does much the same thing but the defined address and area are different.

---

### Post by srs5694 on 2010-03-21
> **Intrepid Ibex said:**
> [quote=minsf]isnt there a more modern partition table that works better with ext3 and huge external HD than msdos partition table, given that i will never need any fat or ntfs on this drive?I usually don't bump a year old thread but in this case somebody probably wants to know the answer.

The answer is: no.[/QUOTE]

Actually, the answer is "yes." It's called the [GUID Partition Table (GPT).](http://en.wikipedia.org/wiki/GUID_Partition_Table) It's used by default on all Intel-based Macintoshes and can be used on other computers. Linux, FreeBSD, and even Windows can read and write GPT disks; however, Windows can't boot from them on BIOS-based computers.

In fact, you should get familiar with GPT, because it's coming to your own computer before too long. The reason is that MBR uses 32-bit sector pointers. Combine that with a 512-byte sector size and you get a 2TiB size limit. With drives just under that size already available, the limits of MBR are about to be tested. GPT, by contrast, uses 64-bit sector pointers, so GPT can handle much bigger hard disks. (Drives with 4096-byte sectors are now available, but they present the illusion of 512-byte sectors for compatibility purposes. Your guess is as good as mine as to how drive manufacturers will handle over-2TiB drives -- present a true 4096-byte sector size to extend the utility of MBR or tell users to partition their disks with GPT.)

To use GPT, you need support in the OS kernel (already present in all recent Ubuntu kernels), in disk utilities (already present in libparted-based tools, or you can use my [GPT fdisk](http://www.rodsbooks.com/gdisk/)), and in a boot loader (for boot disks only; GRUB 2 supports GPT, as do some patched versions of GRUB Legacy). Thus, Linux is well-prepared for GPT.

---

### Post by Intrepid Ibex on 2010-03-30
Well if you wanna count GPT, I don't disagree with you ;).

---

