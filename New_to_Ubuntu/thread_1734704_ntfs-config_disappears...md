---
title: "ntfs-config disappears.."
date: 2011-04-20
forum: New to Ubuntu
---

### Post by M-Crew on 2011-04-20
Hello everyone!

I decided to take the Ubuntu (Maverick) plunge a couple of weeks ago and so far everything was going relatively smooth (Well.. configuring dial-up was a accomplishment for me; as was getting a working e-mail client.. ended up using Thunderbird).

My basic set up is as follows:

3 internal hard drives.. all SATA.
2 are identical 250 Gb Seagates formatted w/2 partitions each (OS & storage).
One has XP in a 50Gb partition and the other has Vista in the same size, rest of each drive is partitioned for storage.
Ubuntu 10.10 is installed to my third.. largest HD (640 Gb). IT is installed to a 10 Gb Ext4 formatted partition. There are 3 separate partitions on this drive. The largest (NTFS) being used for game and app installs out of the two Windows OS and the remaining one being used for back-up images of ALL operating systems.

In other words.. I have a tri-boot system with each OS on a separate hard drive/partition.. works nice.

Oddly enough though.. it seems that back in the days when I would boot of the Ubuntu 8.10 live CD (It saved my hiney more than once.) I could see all of my drives in Ubuntu. Now that I have a current solid static install though.. it seems that I could only see the HD that Ubuntu is installed to (including it's two NTFS partitions.. go figure) and any external drives I plug in.

So I did some researching and decided to install ntfs-config. I don't want to necessarily see all of my NTFS partitions all the time.. nor do I want/need them to auto-mount at start up in Ubuntu so FStab is unnecessary.

I installed ntfs-config through the software center using psychocat's tutorials. I was doing some multi-tasking at the time it was installing and I "may" have inadvertently closed a config window after set up.. but I doubt it.. point is anyways.. I still can see no other partitions and whenever I bring up NTFS configuration tool from System>Administration I seem to see a dialog pop up very quickly/briefly.. it appears to minimze to the taskbar.. but then disappears altogether and I still see no other drives in the exploration window, under "places".. or anywhere.

Running sudo fdisk -l in the terminal DOES list all of my internal HDs properly and with the partitions described.. but that hardly affords me an easy interface for disk interaction.

BTW.. I tried uninstalling the app via the software center.. adding it back through the Synaptic Manager (along with a few other semi-related libraries/files I thought might be connected) and I still get the same behavior.

Aside from the dial-up debacle, my e-mail woes.. and getting the clock to sync up (..don't ask) this is my last major hurdle to get over so I can start enjoying my new install. Any ideas as to what's happening?

I have many other questions I would like help with.. but for now.. this is the problem that has me stumped.

My thanks to all for your time & attention.

---

### Post by Foxheadz on 2011-04-20
Are you mounting the drives with the mount command?

---

### Post by M-Crew on 2011-04-20
Uhm no.. do I need to first?

An update.. I got ntfs-config up and running by actually making the empty dir it's error in terminal refers to as per here: [http://ubuntuforums.org/showthread.php?t=1644874](http://ubuntuforums.org/showthread.php?t=1644874) .

So now I get nts-cofig to come up.. but the only two partitions it sees under "new partitions detected" are the backup partition and the install one (in other words the two ntfs ones that are on the 640 Gb hard drive with Ubuntu).

Reading the afore-mentioned thread made me a little wary of using ntfs-config but let me stipulate that I really don't want to access EITHER of my Windows OS install partitions anyway during a regular session (It would maybe be helpful someday if it was the only way to save files off of a non-accessible OS anyway.. as it Ubuntu has in the past). All I really want to do is have access to the two additional storage partitions on those two drives. Even write access is not that important.

Here's what sudo fdisk -l brings up:


Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x4565b461

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        7521    60403430    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2   *        7521       30402   183792807    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0a1b54d3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        7520    60404368+   7  HPFS/NTFS
/dev/sdb2            7521       30401   183791632+   7  HPFS/NTFS

Disk /dev/sdc: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xb17b7d0c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       71390   573440143+   7  HPFS/NTFS
/dev/sdc2           71391       76612    41945715    7  HPFS/NTFS
/dev/sdc3           76613       77826     9744384   83  Linux

Disk /dev/dm-0: 500.1 GB, 500118585344 bytes
255 heads, 63 sectors/track, 60802 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 65536 bytes / 131072 bytes
Disk identifier: 0x0a1b54d3

     Device Boot      Start         End      Blocks   Id  System
/dev/dm-0p1   *           1        7520    60404368+   7  HPFS/NTFS
Partition 1 does not start on physical sector boundary.
/dev/dm-0p2            7521       30401   183791632+   7  HPFS/NTFS
Partition 2 does not start on physical sector boundary.

Disk /dev/dm-1: 61.9 GB, 61854073344 bytes
255 heads, 63 sectors/track, 7519 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 65536 bytes / 131072 bytes
Alignment offset: 33280 bytes
Disk identifier: 0x2052474d

This doesn't look like a partition table
Probably you selected the wrong device.

     Device Boot      Start         End      Blocks   Id  System
/dev/dm-1p1   ?         410      119791   958924038+  70  DiskSecure Multi-Boot
Partition 1 does not end on cylinder boundary.
Partition 1 does not start on physical sector boundary.
/dev/dm-1p2   ?      121585      234786   909287957+  43  Unknown
Partition 2 does not end on cylinder boundary.
Partition 2 does not start on physical sector boundary.
/dev/dm-1p3   ?       14052       14052           5   72  Unknown
Partition 3 does not end on cylinder boundary.
Partition 3 does not start on physical sector boundary.
/dev/dm-1p4          164483      164486       25945    0  Empty
Partition 4 does not end on cylinder boundary.
Partition 4 does not start on physical sector boundary.

Partition table entries are not in disk order

Disk /dev/dm-2: 188.2 GB, 188202631680 bytes
255 heads, 63 sectors/track, 22881 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 65536 bytes / 131072 bytes
Alignment offset: 16384 bytes
Disk identifier: 0x5900003b

Disk /dev/dm-2 doesn't contain a valid partition table


Since both the disks I'm trying to get to show up/mount are the exact same size/models I realise that picking the right partitions may be a problem.. but from what I can see.. basically I want to mount 
/dev/sda2  and  /dev/sdb2  .. but they can't be detected in ntfs-config. Do I have to mount them first? Isn't that what the tool does in the first place?


Hehe.. tried this:

sudo mount /dev/sdb2

got back this:

can't find /dev/sdb2 in /etc/fstab or /etc/mtab 

..<sigh>

I really don't want to try and edit my fstab.. I barely understand commands in Ubuntu as it is and would really hate to muck anything up. Which is why I want to use the GUI for now.

---

### Post by Foxheadz on 2011-04-20
I would try just using this guide [http://www.arsgeek.com/2006/09/25/ubuntu-tricks-how-to-mount-your-windows-partition-and-make-it-readwritable/](http://www.arsgeek.com/2006/09/25/ubuntu-tricks-how-to-mount-your-windows-partition-and-make-it-readwritable/)

---

### Post by M-Crew on 2011-04-20
Well.. while I appreciate your help (and I really do).. and after having already perused many other "guides" pertaining to this subject.. the one you referred me to was new to me.

Sooo... I read it (both of them including the one referred to off the page that uses ntfs-3g) and I edited my fstab.. and almost locked myself out of my entire system. After carefully making sure I created a dir to mount to.. and carefully inserting MY own /dev configuration into the worded commands the author uses.. I rebooted like he said and was immediately informed the partition didn't exist.. the command was bad.. or something to that effect. I almost soiled my britches so you have to forgive me if I seem a bit confused right now. I was given several options to either skip the mounting.. wait longer.. or something else I don't recall. After a reboot I was presented with the GRUB screen.. which I've never even seen on account of I've used EasyBCD Menu in XP to set up my tri-boot.

Once I finally got back into Ubuntu and figured out how to restore my backup of fstab.. I'm seemingly OK again.

Can someone explain to me either how to make ntfs-config work? Or see these partitions? And if it can't.. why? While I appreciate referrals to "guides" that hand-hold and simply say "type this in terminal and substitute "this for this"".. save; reboot & pray. If there's a graphical GUI that supposedly works.. and if it doesn't.. then why distribute it.

I apologise if I I'm coming off sounding a little crass; but I don't mean to. It's just that I'm a 53 year old guy who really wants to learn Ubuntu/Linux AS well as command line functions.. and at the rate I've been going for the last few weeks.. I don't have much time left ;) .

---

### Post by M-Crew on 2011-04-21
Well.. I think I found a solution to all of my problems. I remembered a while ago that I still had my Ubuntu 8.10 live CD lying around (Which is what got me interested in it in the first place.). I booted off of it and immediately noticed that, as I remembered. I can automatically see ALL of my partitions in it. 8.10 also came with a PPP dial-up app already installed. It had gparted in it as well. My clock syncs up to the hw clock withOUT having to log onto the internet first.. and MANY more "trials & tribulations" I'm having with 10.10 simply don't exist in 8.10. So this weekend I'll be formatting my 10.10 install and installing 8.10.

I seriously doubt I'll ever go near 11.04. I'm not forlorn though.. in a life where it seems that for every step forward I usually take two steps back.. it actually feels good to take two steps forward and only one step back.. for a change.. so to speak.

Also found that I still had an ISO of something called "SuperUbuntu" 8.10 archived away. Burnt it and checked it out.. I like.

Thanks again for everyone's help.

Just curious.. as most of the "guides" & tutorials I see around the net are still written on, or for the 8.10 build.. is 8.10 considered by many the same way some of us old Windows dinosaurs feel about W98SE or even XP by some? ;)

---

