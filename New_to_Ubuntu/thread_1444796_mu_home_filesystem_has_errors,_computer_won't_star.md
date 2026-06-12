---
title: "mu /home filesystem has errors, computer won't start up"
date: 2010-04-01
forum: New to Ubuntu
---

### Post by Djalmahal on 2010-04-01
Hi,

I bought this new computer 2 weeks ago, worked fine with Karmic, now when I boot up it check the filesystem and return in the text interface

/dev/sda7: UNEXCPTECTED INCONSISENCY:RUN fsck manually
mountall: fsck /home has errors 
init: mounall main process (480) terminated with status 2
filesystem check failed
A mainenance shell will now be started

So I'm not able to boot up Ubuntu.

What should I do? Never saw this in 2 years of Ubuntu with my old computer, even though Diskutility on my old computer says DISK HAS MANY BAD SECTORS.

Help me out.

Thanks
Andreas

P.S.: I'm now running fsck and afer saying now to e2fsck it goes through Pass 1-4, then saying Connect to /lost+found I say yes it's comes up wih Inode 4391140 ref count is 2, should be 1 Fix<y> I type y it comes up with more messages like that.

I went through that once before a couple of days ago saying yes to everything, it fixed it for then, but how can I make it totally right?

---

### Post by louieb on 2010-04-01
Sounds like failure of the hard drive is close. Its giving you warning - Time to get your data copied off and time to replace the drive.

You get a lemon evey now and then.

---

### Post by Djalmahal on 2010-04-01
The computer is 2 weeks old, and the hard drive is about to fail, sounds bad. Is there any more information I can get from a command line etc?

The setup is as follows:

Partition #1 Windows Recovery
#2 Windows 7 
#3 ext4 root
#4 /home in ext2 (I wanted to get Windows to read it and heard that ext2 functionality can be achieved in Windows)
#5 /swap

Is there a point in redoing /home (that's the one that seems to make problems), reformatting it in ext4 or such?
I'm in town right now, once I get home (no Internet) I will boot from a USB and run Palimpset, see if that comes up with more.

Thanks for all your replies
Andreas

---

### Post by uRock on 2010-04-01
It is possible the HDD is bad and you will have to send in for warranty work. If this is the case, you will need to get Linux off of it and restore NTFS to the rest of the disk, so they will honor the warranty.

Good luck,
Ronnie

PS I hope I am wrong.:neutral:

---

### Post by Djalmahal on 2010-04-01
Sure, I could clean up the linux partitions but Windows never complained about it. Now I could see that Linux warns you about problems whereas Windows just keeps going till it goes belly up, but as long as that doesn't happen I couldn't send it in, right?
When I run Disk Utility a can run Filesystemcheck on the Recovery Partition of Windows with comes back "clean", funny enough I can't do the same check on the NTFS Windows 7 partition, it just doesn't let me do it. When I come home I'll boot it up from USB and try to check all the Partitions with the Disk Utility, see what comes back.

Andreas

---

### Post by louieb on 2010-04-01
The [PartedMagicCD]("http://partedmagic.com/wiki/PartedMagic.php?n=Main.PartedMagic")
has smartmon tools  - it can check the smart status of the drive. Smart (a hard drive diagnostic) is built in to almost every hdd built in the last 10-15 years.

---

### Post by Djalmahal on 2010-04-03
So I ran Gparted on  a live USB Ubuntu Version, as attachment is the output.
Any feedback on that?

Andreas

---

### Post by uRock on 2010-04-03
Attachment isn't showing.

---

### Post by Djalmahal on 2010-04-03
Sorry, I just realized it's said invalid file, here it comes:\

GParted 0.5.1

Libparted 2.2
Check and repair file system (ext2) on /dev/sda7  00:07:08    ( SUCCESS )
     	
calibrate /dev/sda7  00:00:00    ( SUCCESS )
     	
path: /dev/sda7
start: 306504198
end: 976768064
size: 670263867 (319.61 GiB)
check file system on /dev/sda7 for errors and (if possible) fix them  00:07:07    ( SUCCESS )
     	
e2fsck -f -y -v /dev/sda7
     	
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

52254 inodes used (0.12%)
2267 non-contiguous files (4.3%)
54 non-contiguous directories (0.1%)
# of inodes with ind/dind/tind blocks: 24791/4755/3
31750417 blocks used (37.90%)
0 bad blocks
5 large files

47976 regular files
4221 directories
0 character device files
0 block device files
0 fifos
3 links
45 symbolic links (27 fast symbolic links)
3 sockets
--------
52248 files
e2fsck 1.41.10 (10-Feb-2009)
grow file system to fill the partition  00:00:01    ( SUCCESS )
     	
resize2fs /dev/sda7
     	
resize2fs 1.41.10 (10-Feb-2009)
The filesystem is already 83782983 blocks long. Nothing to do!

---

### Post by Jahmon on 2010-04-04
I'm having the same error. 

I upgraded my Karmic to Lucid yesterday and rebooted serveral times yesterday with no problems.

This morning when I started my computer it said the same error as you.
I haven't been able to solve it yet.

---

