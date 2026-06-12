---
title: "View drives in Places &gt; Computer"
date: 2009-02-26
forum: New to Ubuntu
---

### Post by Al Fischer on 2009-02-26
Made a dual boot - same drive - both intrepid.

Booting from first partition I see and mount the second artition.
Booting from second partition I do not see the first partition.
Both are ext3. I expected to be able to see the first partition.

Is this normal? What controls whether another partition shows?

---

### Post by tarps87 on 2009-02-26
Can you post the output of
```
sudo fdisk -l
```
(l = lower case L)
and the contents of you fstab file from both. /etc/fstab
The fstab file handles mounting of devices but they should both be visible in the places menu with a default install, as far as I know

---

### Post by Al Fischer on 2009-02-26
How do I poct the output? Keep in mind that this Linux world is new to me.

---

### Post by Jeroen Vernooij on 2009-02-26
Hi, Go to Applications --> Accessories --> Terminal 
and copy and past that command into the Terminal.

Then copy and paste its output to this forum.

---

### Post by orethrius on 2009-02-26
You can just try holding Alt and hitting F2, then entering:
```
cat /etc/fstab > ~/Desktop/fstab.log
```

Then post the contents of fstab.log from your Desktop.

Or what Jeroen Vernooij said, my way is GUI, his is CLI.  Take your pick of which you like better.  :)

As for copy-pasting results from fdisk, the easiest way would be Jeroen's method of using gnome-terminal (xterm can do the task as well, but gnome-terminal has an actual menu-driven option for copy-paste operations).

---

### Post by Al Fischer on 2009-02-26
Output when booted from Partition 1

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sde1
UUID=1e22d298-38b4-48e2-b69e-d15c04458b1b /               ext3    relatime,errors=remount-ro 0       1
# /dev/sde5
UUID=0f1cc51d-7712-4420-8863-d27f87710e2a none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/mnt/2024Mb.swap            none    swap    sw   0  0


Output when booted from Partition 2
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sde1
UUID=1e22d298-38b4-48e2-b69e-d15c04458b1b /               ext3    relatime,errors=remount-ro 0       1
# /dev/sde5
UUID=0f1cc51d-7712-4420-8863-d27f87710e2a none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/mnt/2024Mb.swap            none    swap    sw   0  0



The fdisk -l shows the same in both with partition 1 showing an asterisk in the boot column.

I am on a Windows laptop now and make a file of the fstabs and copy-paste to this screen. No idea how to capture fdisk to this machine!

---

### Post by Jeroen Vernooij on 2009-02-26
Are you sure you have 2 partitions on that computer?

It just shows 1 ext3 partition and 1 swap partition, so to me it seems impossible that when booted into the "first partition" you also see a second partition mounted.

---

### Post by orethrius on 2009-02-26
Right, got it, Alt+F2 and the following (' is a single-quote, not a backtick):

```
xterm -e 'sudo fdisk -l > ~/Desktop/fdisk.log'
```

Then just open fdisk.log with your favorite text editor.

---

### Post by tarps87 on 2009-02-26
> **Al Fischer said:**
> How do I poct the output? Keep in mind that this Linux world is new to me.

> **Al Fischer said:**
> I am on a Windows laptop now and make a file of the fstabs and copy-paste to this screen. No idea how to capture fdisk to this machine!

Apologises
In a terminal type
```
sudo fdisk -l > ~/Desktop/fdiskout.txt
```

From what you have posted and said it sounds like it should work, if you can post the output of the above command from the one that can't see the first drive we can test if it can access the hard drive

---

### Post by Al Fischer on 2009-02-26
Got the fdisk copied!

Output from partition 1

ot@server1:~# fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd970a3ce

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2055    16506756   83  Linux
/dev/sda2            2056        4605    20482875   83  Linux
/dev/sda3            4606        7792    25599577+  83  Linux
root@server1:~# 


Output from partition 2

oot@server1:~# fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd970a3ce

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2055    16506756   83  Linux
/dev/sda2            2056        4605    20482875   83  Linux
/dev/sda3            4606        7792    25599577+  83  Linux

Disk /dev/sdb: 131 MB, 131072000 bytes
16 heads, 63 sectors/track, 253 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0xddafbdd6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         254      128000    b  W95 FAT32
root@server1:~#

---

### Post by Al Fischer on 2009-02-26
the additional drive is my usb key that I didn't have installed on the first example.

---

### Post by tarps87 on 2009-02-26
On the second partition did you have a usb drive or something plugged in that you didn't when on partition 1? Edit: Just see your last post

In a terminal try
```
sudo mkdir /media/partition1
```
This will make a directory in the /media directory
```
sudo mount /dev/sda1 /media/partition1
```
This should mount the first partition
```
nautilus /media/partition1/
```
This should open the browser in the first patition, if this all works it will prove that the first partition can be read.
If you see any error messages you can either highlight the message right click, copy and then past it into a text editor or run the command with **> ~/Desktop/textfilel.txt** on the end
e.g
```
sudo mount /dev/sda1 /media/partition1 > ~/Desktop/textfiel.txt
```

I hope this makes sense, if not post back and I will explain the bit you don't understand

---

### Post by Al Fischer on 2009-02-26
Actually on this drive are 3 partitions. The 2nd and third are copies made with gparted. I am attempting to create at lease one totally separate copy for backu up purposes (not IF but WHEN I do something wrong and can't fix it!!)

I have several removeable drives each with 2-4 partions of the same. This one happened to have 3.

The drives are on removeable carriers.

---

### Post by Al Fischer on 2009-02-26
I used the terminal window and doing what you said it mounted and now I can see it in Places > Computer. Shows mounted and can be read.

---

### Post by Al Fischer on 2009-02-26
I rebooted and it did not come up mounted. I mounted it but cannot un mount.

---

### Post by Al Fischer on 2009-02-26
It did not show in Computer when I reboooted untill I mounted it.

---

### Post by tarps87 on 2009-02-26
It may be as it is a bootable partition although it is unlikely to be the cause.
A solution would be to add it to the fstab file.
You can do this using a GUI although I can't remember the programs name, you can read the documentation here:
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
or you can post the output of the following command and I can guide you through it
```
sudo blkid > ~/Desktop/bikidout.txt
```

---

### Post by Al Fischer on 2009-02-26
I will definitely follow the link but for now would you please explain what this is and then guide.

Here is the output::

/dev/sda1: UUID="1e22d298-38b4-48e2-b69e-d15c04458b1b" TYPE="ext3" SEC_TYPE="ext2" 
/dev/sdb1: UUID="1e22d298-38b4-48e2-b69e-d15c04458b1b" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdc1: UUID="52A49A14A499FAA5" LABEL="Disc 3" TYPE="ntfs" 
/dev/sdd1: UUID="0880AC1380AC08F0" LABEL="Disc 4" TYPE="ntfs" 
/dev/sde1: UUID="1e22d298-38b4-48e2-b69e-d15c04458b1b" TYPE="ext3" 
/dev/sdb2: LABEL="5 GB MAX" UUID="0f14fd11-e27c-973f-66d7-3cca9a8d8752" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb3: LABEL="SWAP" UUID="feaeef72-ed4d-c584-3c71-296093392e41" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb: SEC_TYPE="msdos" UUID="DC9A-6605" TYPE="vfat" 
/dev/sda5: TYPE="swap" 
/dev/sda3: UUID="3be4c576-e0ed-4112-9c32-2e67c53e6ba9" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda2: UUID="937f8395-5f20-4734-a857-6e1a17d3200a" SEC_TYPE="ext2" TYPE="ext3"

---

### Post by Al Fischer on 2009-02-26
Remember, that I started abt 2 weeks ago. Have a background of CPM - DOS - OS2 - Windows with a bit of IBM mainframe and AS400. But I am now starting new!!

---

### Post by tarps87 on 2009-02-26
> **Al Fischer said:**
> /dev/sda1: UUID="1e22d298-38b4-48e2-b69e-d15c04458b1b" TYPE="ext3" SEC_TYPE="ext2" 
/dev/sdb1: UUID="1e22d298-38b4-48e2-b69e-d15c04458b1b" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sde1: UUID="1e22d298-38b4-48e2-b69e-d15c04458b1b" TYPE="ext3" 


That is strange, you have three partitions with the same UUID (Universally Unique Identifier)
When you ran this command what devices did you have plugged in and what should there partitions look like?

I will assume that the three partitions are
sda1
sda2
sda3

If I post anything that you don't understand let me know and I will explain

First run these commands
```
sudo mkdir /media/partition1
sudo mkdir /media/partition2
```
(note you can change partition1 and partition2 to whatever you want)
```
sudo gedit /etc/fstab
```

add the following lines to the end

#/dev/sda2
UUID=937f8395-5f20-4734-a857-6e1a17d3200a  /media/partition1 ext3  relatime,noexec  0  2
#/dev/sda3
UUID=be4c576-e0ed-4112-9c32-2e67c53e6ba9  /media/partition2 ext3  relatime,noexec  0  2

```
sudo mount -a
```
This will mount all the drives/partitions in the fstab file

---

### Post by Al Fischer on 2009-02-26
The system has 1 120g drive. It has 3 partitions. sad1 sda2 sda3

Also a CDRW and a DVDRW.

No additional drives.

The initial build of 1 partition was on another drive cloned to this one using Acronis True Imagee 11. It booted without issue.

I then use GPARTED Live CD to boot and copied Partition 1 to Partition 2 and Again Partition 1 to Partition 3,

I then edited menu.lst on Partition 1 to allow 3 menu entries. I can select the desired partition from the menu and it boots it OK.

I did make all 3 partitions different sizes to make sure I was looking at the right partition. 

The fstab is identical on all 3 partitions, however, when booting to Partition 2 I can see Partition 3 and when booting to Partition 3 I can see Partition 2. They are in both cases mountable. Partition 1 is not show on Places > Computer. Filesystem also shows in both cases.

Booting to Partition 1 does show both Partition 2 and 3 also Filesystem. I can mount Partition 2 and 3 without issue.

This seems wrong.

So, what did I do wrong?

---

### Post by Al Fischer on 2009-02-26
I just finished reading the link on fstab and think I understand that we a allowing the Patiotions to me mounted in a folder in media, and then saying mount all.

How come then with  fstabs identical and none of them referring to Partioion 2 or 3 I can see them but not see Partition 1?

Was copying the partition an un-natural act to Linux? There is considerable talk on the forums about backing up and restoring to another drive via command line but I think it may be the same a copying via GPARTED. 

Coming from Windows background backups are almost a daily necessity! Also cloning for me is common and I have done it literally thousands of times to a variety of desktops. (I'm retired and frequently get a call from IBM to replace a major installation of HDs - sometimes 1000 at a time)

---

### Post by tarps87 on 2009-02-26
I think some of the previous partition tables have been copied, I may be worth rebuilding the partition table, unfortunately I can't remember how to do this. My previous post should get it set up so that the drive appear in the places menu.
I will post back if I remember how to rebuild the partition table.

I believe the UUID's and partition info is interfering with loading the first partition. Usually you can see an mount all the internal drives without having them if fstab

---

### Post by Al Fischer on 2009-02-26
Yes, what you said to try should work. I think my next step is to format this drive and re-clone the original partition. Then try adding another partition. Then redo grub.  I just found another thread on completely reinstalling grub that I will try.

It includes steps I did not perform. Yesterday I downloaded and studied the GRUB manual as I am completely unfsmilar with the entire process. I plan to re-read the book soas to understand what these additional steps are. I feel it more important to understand this than to just get it working and move on.

Looks like having all 3 fstabs the same and none showing all drives is basically wrong. Hard to mount a drive you don't have!

Many thanks for the help. I have a better understanding of fstab now and have a plan to continue. Lots to learn!

---

### Post by unutbu on 2009-02-26
You can use the command
```

sudo tune2fs -U random /dev/sdaX
```

to change the UUID of /dev/sdaX. (Change X in sdaX to the appropriate number.)

Give each of your partitions a unique UUID.

You can use the command
```
sudo blkid -c /dev/null
```
to find the new UUIDs of the partitions.

You will have to edit your /etc/fstabs on each Linux partition to reflect this change.

I think this is the only change that is needed, but I am not sure. 
Please keep us posted if you run into trouble or have success. I am interested either way.

---

### Post by Al Fischer on 2009-02-26
That sound logical. Right now I am rebuilding  the drive but with only two copies of the partition. It will probably take a couple hrs then I will try that.

I was wondering about the 'non-unique' UUIDs but thought it came from the HD. Sounds like the UUID identifies the PARTITION and not the physical HD. Makes more sense.

---

### Post by unutbu on 2009-02-26
That's correct. The UUID is tied to the partition.

---

### Post by Al Fischer on 2009-02-26
So, in the case of a system with two identical partitions, set up with a menu allowing booting from either partition,  both fstabs would be the same showing the UUID of both partitions. Additionally each fstab could contain additional UUIDs for any additional drives allowed to be mounted.

For exampe partition1 and partition2 fstab would show sda1 and sda2 and would be added after the two original entries for the CD and DVD. I could tthen add another physical drive UUID to either fstab and be able to mount it if booted to that partition.

The boot/grub/menu.lst would be read by grub at initial startup and hold the actual menu info for booting. Only the menu.lst for the first partition would need to be set.

Do I understand this or is there something I am missing?

How would I indicate that a drive or partition should be mounted at boot?

---

### Post by unutbu on 2009-02-26
The /etc/fstabs for sda1 and sda2 should not be the same.

Suppose your UUIDs look like this
```

/dev/sda1: UUID="AAAAAAAA-AAAA-AAAA-AAAA-AAAAAAAAAAAA" TYPE="ext3" 
/dev/sda2: UUID="BBBBBBBB-BBBB-BBBB-BBBB-BBBBBBBBBBBB" TYPE="ext3" 
```

Then your /etc/fstab on sda1 should contains this:
```

UUID=AAAAAAAA-AAAA-AAAA-AAAA-AAAAAAAAAAAA [COLOR="Red"]/[/COLOR] ext3 relatime,errors=remount-ro 0 1
UUID=BBBBBBBB-BBBB-BBBB-BBBB-BBBBBBBBBBBB [COLOR="Red"]/OS2[/COLOR] ext3 relatime,errors=remount-ro 0 2

```
This tells Linux to mount sda1 at [COLOR="Red"]/[/COLOR] (your root partition), and sda2 at /OS2.

And your /etc/fstab on sda2 should contain this:
```

UUID=BBBBBBBB-BBBB-BBBB-BBBB-BBBBBBBBBBBB [COLOR="Red"]/[/COLOR] ext3 relatime,errors=remount-ro 0 1
UUID=AAAAAAAA-AAAA-AAAA-AAAA-AAAAAAAAAAAA [COLOR="Red"]/OS1[/COLOR] ext3 relatime,errors=remount-ro 0 2

```
Using this /etc/fstab, Linux will mount sda2 at / and mount sda1 at /OS1.

After booting sda1, run
```

sudo mkdir /OS2
sudo mount /dev/sda2 /OS2
sudo mkdir /OS2/OS1
```

You can change OS1 and OS2 to be whatever you like, you just need to define a mount point for the partitions.

/OS2/OS1 looks weird, but if you do as described above, when booted into Linux on sda1, your other Linux (sda2) will be mounted at /OS2, and when booted into Linux on sda2, your other Linux (now sda1) will be mounted at /OS1.


Regarding GRUB and /boot/grub/menu.lst: It sounds like your GRUB is currently booting sda and probably looking in sda1 for menu.lst. If so, you only need to edit the menu.lst on sda1 for this to work. If I'm correct that GRUB is reading the menu.lst on sda1, then

On sda1 edit /boot/grub/menu.lst to contain boot stanzas that looks something like this:```


title		Ubuntu 8.10, sda1
uuid		AAAAAAAA-AAAA-AAAA-AAAA-AAAAAAAAAAAA
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=AAAAAAAA-AAAA-AAAA-AAAA-AAAAAAAAAAAA ro quiet 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet


title		Ubuntu 8.10, sda2
uuid		BBBBBBBB-BBBB-BBBB-BBBB-BBBBBBBBBBBB
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=BBBBBBBB-BBBB-BBBB-BBBB-BBBBBBBBBBBB ro quiet 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet
```

How about try that and see how it goes. If you run into trouble, post back here and we'll work from there.

---

### Post by Al Fischer on 2009-02-26
Thanks. Will digest it and then try it.

I REALLY appreciate your help.

---

### Post by Al Fischer on 2009-02-26
SUCCESS!!!!!
Well, at least 99%

I was unable to do this from the Live CD so I created a single partition drive and used it to boot with the other drive in the system. In the meantime, I had rewritten the folders twice due to not getting it straight. Used GPARTED to do this. Copied from my 'master image' and made 2 partitions of different sizes to eliminate confusion.

What I did was make a listing of the UUIDs and make the fstabs in each partition right. Then edited the boot/grub/menu.lst properly. (only partition 1)

At this point I was able to boot into either of the partitions. However neither partition showed up in Places > Computer. Googled it and it appears this is a known issue or a 'feature'.  I changed the mount point to /media/PART1 and /media/PART2 as suggested and now the partitions show up properly in Computer as well on the desktop. (mounted)

However, when when booted to partition 2, browsing partition 1
all folders are GRAY. The other way around they appear the normal orange color. Not a big deal, as everything else seems to be normal. However things like this mean something is not quite right.

Any ideas?

This has been a real learning experience and I THINK I am starting to understand it. Tomorrow morning I will add another partition just to prove my understanding the process. Then a weekend off to go play with some model trains. When I come back I will add some drives and try using it as a http server. 

Again, I really appreciate your sticking with me on this.

---

### Post by Al Fischer on 2009-03-07
Well, I gave my mind a break and went back after a couple days. Came back and now had a basic understanding of what I had to do.

After several days of study, I now have a good understanding of UUID and fstab as well as GRUB. managed to create a drive with 3 copies of Ubuntu and a Windows XP partition. All boot right and work 100%. 

I have many years in the IT industry and have never seen such quality help freely given to a learner. 

Looks like you have created another Linux convert! Looks like something I can deal with and actually use. I am impressed!

So, thanks to you folks on this forum I can continue on!

---

### Post by unutbu on 2009-03-07
Excellent news! Enjoy Ubuntu :D

---

