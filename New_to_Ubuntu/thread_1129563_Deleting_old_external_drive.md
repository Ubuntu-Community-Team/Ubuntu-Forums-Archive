---
title: "Deleting old external drive"
date: 2009-04-18
forum: New to Ubuntu
---

### Post by Motorhead Kaze on 2009-04-18
More accurate title: **[COLOR="Purple"]"Need to delete a HDD that was my desktop's C drive, and is now attached via USB to my laptop."[/COLOR]**

Howdy.
My desktop's motherboard died and I have just removed the HDD and transferred it into an external drive box and want to delete the contents to use as a backup storage device for use with my laptop. This drive used to be my C drive, and is currently formatted to dual boot Win XP and Ubuntu Hardy. So I need to clear all that stuff out of there. 

I thought I would just go in through ROOT and change permissions to my name and just click "delete" but I cannot change the ownership of the disk to my laptop's name.

When mounted up, I can see the 107.1Gb (windows) and 207.5Gb (Ubuntu) in my "Places" but can only access the 107.1XP partition. When I try to open the Ubuntu side I get a "Unable to mount the volume." "mount: wrong fs type, bad option, bad superblock on/dev/sdc3, missing codepage or helper program, or other error. In some cases useful info is found in syslog - try dmesg tail or so" 


UPDATE for new visitor/helpers: I could not get GParted to delete my disk, nor does testdisk show all of my drive. For details, keep reading please.

---

### Post by supersonicdarky on 2009-04-18
1) open up gparted
2) select appropriate disk in the top right
3) unmout partitions of necessary
4) delete the unwanted partitions
5) create new ext3 partition
6) apply changes

you will may need to update your fstab

---

### Post by Motorhead Kaze on 2009-04-18
Thanks. Apparently I have to open this as ROOT. I opened a gksudo nautilus root window and navigated to usr/bin and just clicked on the program. It has been scanning all devices for a few minutes.

Is there a better way to run this as root? Meaning...can you tell me how to run this as root through the terminal?

---

### Post by supersonicdarky on 2009-04-18
**gksudo gparted** doesn't work?

also scanning may take a while if you have many and/or slow drives and sometimes takes forever if you have floppy enabled in your bios (used to be a bug, not sure if it's been fixed)

note: while it doesn't matter in this case, be sure to prepend the / in 'usr/bin', otherwise it could mean the bin folder in your home folder

---

### Post by Motorhead Kaze on 2009-04-18
Skip that, GParted found it...but not really. It has found the disk but thinks it is sdc (128.00Gb) and that is not true. The disk is 320Gb. Not sure why it says 128... Like I said above, 1 partition is 107.1 and the other is 207.5Gb...

Hmmm. Looks like it means 128Gb is unallocated...

---

### Post by supersonicdarky on 2009-04-18
if there was unallocated space, then it would just show up as a gray area, but still say the capacity of the disk

try pasting output of **sudo fdisk -l**

---

### Post by Motorhead Kaze on 2009-04-18
Ok, there is no option to delete this. 
Under Partition is says "Unallocated" under Filesystem it says "Unallocated" and under Size just reads "128Gb". 

I cannot right click and select delete. Only "New"

Anything else I can do or have missed?

---

### Post by supersonicdarky on 2009-04-18
Are there lock icons on the partitions? if so, unmout them
**sudo umount */path/to/mount***
or
go to nautilus and unmount there

---

### Post by Motorhead Kaze on 2009-04-18
No, no lock icons. All GParted reads out is that SDC has 128Gb unallocated, but does not show that it is a 320Gb drive with 2 partitions. At all. 

Let me make this a bit more clear,

I am currently on my laptop with an external drive attached that I want to clear out. It is connected through USB. When I start up the laptop, only one of the external HDD partitions (107.1Gb XP partition) shows up on my desktop. The other (207.5Gb Hardy) partition does not show up on my desktop and I cannot access it.

I can unmount the 107.1Gb partition, but even when I do that GParted does not show the full HDD and I cannot click delete.

---

### Post by supersonicdarky on 2009-04-18
1) probably a silly question, but are you booting from internal or external
2) are you sure the correct disk is selected in gparted? perhaps its the disk with / that you're looking at

---

### Post by drs305 on 2009-04-18
You can use *testdisk* to wipe out the partition table and create a new one. It's in the universe repository.

> **supersonicdarky said:**
> also scanning may take a while if you have many and/or slow drives and sometimes takes forever if you have floppy enabled in your bios (used to be a bug, not sure if it's been fixed)

Just a tip, especially for older versions of gparted or for huge disks and/or lots of partitions. It can significantly speed up opening and refreshes:
If you are only going to work on one disk, gparted will often open much more quickly (and refresh faster) if you open it like this:
```

gksu gparted /dev/sdX

```
Example: gksu gparted /dev/sda

That way it won't spend time reading devices you don't plan on changing. Note if you do want to look at another you would have to restart gparted.

---

### Post by Motorhead Kaze on 2009-04-18
I booted from the laptop. The external drive USED to be my desktop's C drive. (Desktop's motherboard died, so I am planning to use the drive as an external drive now).

Right now, there are only two drives connected. The internal laptop C drive, and the external drive. The laptop's HDD shows up as "SDA" and the external as "SDC". I think that since the external drive is formated with Hardy, somehow the laptop is not letting me deal with it at all.

---

### Post by supersonicdarky on 2009-04-18
gparted doesn't care what's on the drive. The fact that its hardy doesn't change anything.

---

### Post by Motorhead Kaze on 2009-04-18
Hi again.

Tried using GParted again, but cannot do anything with it. 

I am kaze750 on YM and csjamesson on Skype if anyone has some free time.

Opened gksu testdisk and got this 
"Use arrow keys to select, then press Enter key:
[ Create ]  Create a new log file
[ Append ]  Append information to log file
[ No Log ]  Don't record anything
"
Tried to do [No log] but when I got in, only 130Gb or so were listed as the drive. The drive is 320Gb with 2 partitions. I got a message about needing LBA48 support. My laptop is a compaq nc6000 (1011.MiB, Intel Pentium M 1400MHz processor with 10.7Gb free) is this laptop incapable of handling the job? That would be odd...

---

### Post by Motorhead Kaze on 2009-04-18
If it was not clear before, the only way I can access this HDD right now is externally through USB. The drive itself is IDE and I am using a laptop. The old computer which the HDD came from is dead.

The drive I am attempting to clear out ran XP/Ubuntu and my Ubuntu home folder was named "Kaze". The laptop which I am attempting to use to access this hdd with, is also Ubuntu but uses a different user name. Thus, the computer thinks I do not "Own" the other drive.

---

### Post by Motorhead Kaze on 2009-04-19
Just reading my own writing here and I am concerned that my title and explanation may not get my message across. 

I had a desktop that ran both XP and Hardy. The motherboard died, but the internal HDD from that computer is still very useful and grand. I am now using my laptop which runs Hardy only. I took my old HDD out of the desktop case and put it into an external drive type case and plugged it into my laptop via USB.

To avoid any confusion, at no time will I be talking about my laptop's HDD. Any mention of a hard drive will be the one I pulled from my old desktop. That desktop is currently MIA.

From my laptop, I can access the old XP partition of this HDD (107.1Gb) but when I try to access the partition that was Hardy (207Gb), I am denied. Even from Root.

I have tried "testdisk" and it showed my external drive as sdc with 137Gb. That is untrue, the disk I am trying to delete is a 320Gb drive.

I tried GParted too. It shows my sdc external disk as having an unallocated 120Gb but does not offer me the option to delete anything, and doesn't show the disk for what it really is.

This HDD was formatted as my C drive and uses a different "home" name than my laptop, so I may not have permissions needed to access it, but cannot make my laptop name the owner. (Old desktop was "kaze" whereas laptop is "jamesson") Even so, there must be a work around.

I just want to wipe the entire 320Gb hdd and use it as my external backup now. No intention of putting it back in a desktop for now.

PS When I try to open the 207Gb partition that has Hardy formatted on it, I get an error message which reads, "Unable to mount the volume." "mount: wrong fs type, bad option, bad superblock on/dev/sdc3, missing codepage or helper program, or other error. In some cases useful info is found in syslog - try dmesg tail or so" Which I have no idea what means other than "No, you cannot do this".

---

### Post by muted1987 on 2009-04-19
i dont know if this will work but have you booted to a live CD to use g parted and try formatting the harddrive that way, Ive found form my experience with g parted live CD's always work fa more effectively

---

### Post by aaronp on 2009-04-19
> **Motorhead Kaze said:**
> Hi. Already posted this but I think my title and explanation did not get my message across. 

I had a desktop that ran both XP and Hardy. The motherboard died, but the internal HDD from that computer is still very useful and grand. I am now using my laptop. I took my old HDD out of the desktop case and put it into an external drive type case and plugged it into my laptop via USB.

To avoid any confusion, at no time will I be talking about my laptop's HDD. Any mention of a hard drive will be the one I pulled from my old desktop.

From my laptop, I can access the old XP partition of this HDD (107.1Gb) but when I try to access the partition that was Hardy (207Gb), I am denied. Even from Root.

I have tried "testdisk" and it showed my external drive as sdc with 137Gb. That is untrue, the disk I am trying to delete is a 320Gb drive.

I tried GParted too. It shows my sdc external disk as having an unallocated 120Gb but does not offer me the option to delete anything, and doesn't show the disk for what it really is.

I am guessing that because this HDD was formatted as my C drive and uses a different "home" name than my laptop, that I may not have permissions needed, but cannot make my laptop name the owner. (Old desktop was "kaze" whereas laptop is "jamesson")

Please help me with this. I just want to wipe the entire 320Gb hdd and use it as my external backup now. No intention of putting it back in a desktop for now.

PS When I try to open the 207Gb partition that has Hardy formatted on it, I get an error message which reads, "Unable to mount the volume." "mount: wrong fs type, bad option, bad superblock on/dev/sdc3, missing codepage or helper program, or other error. In some cases useful info is found in syslog - try dmesg tail or so" Which I have no idea what means other than "No, you cannot do this".

I've had a similar problem with superblocks and the good news is that there are backups at specific other places on the disk.
You could try following these instructions to see if it helps:

[http://users.bigpond.net.au/hermanzone/p10.htm#superblock_restoration_frombackup](http://users.bigpond.net.au/hermanzone/p10.htm#superblock_restoration_frombackup)

hth
Aaron

---

### Post by theozzlives on 2009-04-19
If you're just wanting to blank the drive, and not recover any files, you don't have to mount the partition to zap it. Just use gparted and delete all partitions.

---

### Post by sim-value on 2009-04-19
You are denied acces as root cause your root UID is different from the one you had on your old computer ... (this is a default security feature from Ubuntu)

---

### Post by aaronp on 2009-04-19
> **sim-value said:**
> You are denied acces as root cause your root UID is different from the one you had on your old computer ... (this is a default security feature from Ubuntu)

Good pick up sim-value

---

### Post by drs305 on 2009-04-19
Just an update. Via IM last evening, we are pretty sure the OP's problem is with LBA48. Since his computer is fairly new and he is not using a very old kernel, either a drive setting or the BIOS is not allowing LBA48 support. He is going to investigate his BIOS settings to determine if LBA48 is not currently enabled for some reason. 

I did find a page which purports to be able to reset LBA48 settings on drives via a Windows freeware app although I have no firsthand knowledge of the app. That link is:
[_http://blog.atola.com/restoring-factory-hard-drive-capacity_/]("http://blog.atola.com/restoring-factory-hard-drive-capacity/")

And as to why the 137GB limit we discussed:
> 48-bit Logical Block Addressing (LBA) extends the capacity of IDE ATA/ATAPI devices beyond the limit of 137.4 GB. This limit applies to IDE ATA/ATAPI devices only and not to SCSI interface devices. The original design specification for the ATA interface only provided 28-bits with which to address the devices. This meant that a hard disk could only have a maximum of 268,435,456 sectors of 512 bytes of data thus limiting the ATA interface to a maximum of 137.4 gigabytes. With 48-bit addressing the limit is 144 petabytes (144,000,000 gigabytes).

Either I or the OP will provide an update once a solution is achieved.

---

### Post by Motorhead Kaze on 2009-04-19
Yes, that is what I meant when I wrote "...this HDD was formatted as my C drive and uses a different "home" name than my laptop". I realize I do not have "ownership" I need the work around.

Also, as I mentioned I tried GParted (with the disk unmounted) but the full disk does not show up and I cannot delete it using GParted.

There was some mention made that my BIOS may be set to limit the usable size of external drives, and that I should look for an "enable LBA" switch under IDE drives so I will try that.

---

### Post by Motorhead Kaze on 2009-04-19
So, what a bummer. BIOS makes no mention whatsoever of external drives. There is only one section on hard drives and it says I have one (the laptop does).

Nothing looked like what I was searching for. I have 4 tabs in BIOS, "**File, security, Tools and Advanced**". File says that I have an HP Compaq nc6000 (knew that much)
Intel Pentium M 1400Mhz processor,
Processor stepping 5
Cache size (L1/L2) 64/1024kb
Memory 1024Mb...

Video revision ATI 2005/06/10
...
**Security** only had 1 thing that looked like it "might" have been what I wanted, but was just "device security" and no mention was made of external drives. Under the **Advanced** tab there was "**Language, Boot options and Device Options**" The latter reads:

Number lock off
Swap FN/...keys disabled
Multiple pointing devices enabled
USB legacy supply disabled
Parallel port mode ECP
Intel speedstep technology auto
Fan always on while on AC power enabled.

Nothing at all about hard drives except what is in the laptop itself. And even with the external drive hooked up, it doesn't come on in BIOS.

Hmmmm...

---

### Post by sgosnell on 2009-04-19
You need to delete the partitions in the correct order, then add a new partition.  You probably need to delete the Windows partition first, but I don't know exactly how you set things up originally.  I would start deleting partitions as permitted, and eventually you should end up with the entire drive space unallocated, whereupon you should be able to add a new partition the size of the drive.

---

### Post by Motorhead Kaze on 2009-04-19
supersonicdarky: I just reread your post. What is Fstab? Maybe I missed that part and it is messing me up?

sgosnell: Hi. Yes, I had XP on the drive and installed Hardy next. So which program do you suggest I use? Fdisk is the only one I have not tried that was listed here so far.

Ok, I went to the terminal and ran a list of my hdds 

```
jamesson@jamesson-laptop:~$ ls /dev/sd*
/dev/sda   /dev/sda2  /dev/sdb   /dev/sdc   /dev/sdc2
/dev/sda1  /dev/sda5  /dev/sdb1  /dev/sdc1  /dev/sdc3
```

SDA is my laptop's hdd, SDB is my 1Tb external, SDC is the 320Gb external.

The disk I am trying to delete is **sdc**, but this is the conversation with the terminal:
```
jamesson@jamesson-laptop:~$ fdisk /dev/sdc
Unable to open /dev/sdc
```

So...hmmm

Took a trip back to **GParted** just in case someone mentions it again. The advice for Gparted was just to delete the drive from there. I don't know what other people get in Gparted, but there are no options for deletion. GParted only lists the drive I want to access/delete as "Unallocated 128Gb" and not what the disk is, not how much is used or unused. Inside the case, it is an IDE type.
In contrast, sdb, the 1Tb drive shows up with exactly how much is used/unused.

The right click options in Gparted for sda and sdb are "unmount" "manage flags" and "information" and for sdc the right click options are "new" and "information". Info gives nothing new. "device information" gives the model number, says the size is 128Gb, heads, sectors, cylinders, etc.

Ok, my mind has sparked and I have a new thought to add here. Previously I hooked up an external 120Gb hdd to this laptop via USB and an identical case. If somehow this computer thinks that my 320 is the 120, then I can see why it only halfway recognizes it, but gets the info wrong...like seeing someone you "think" you recognize but they give you a dirty look like "what are you staring at?"

...maybe just part of the drive is broken? Weird.

---

### Post by supersonicdarky on 2009-04-21
If nothing else works, try **dd**'ing it.
```
sudo dd if=/dev/zero of=/dev/sdc
```
That should completely wipe the drive by writing zeroes. After doing that see if gparted can do anything (create partitions, etc)

***Note***: be careful with dd. One typo and your whole system is screwed.

btw, fdisk should be ran as root

---

fstab is only used for mounting partitions. It should have no effect on being able to see the size of the drive. (see /etc/fstab)

---

### Post by jose187 on 2009-04-21
> **theozzlives said:**
> If you're just wanting to blank the drive, and not recover any files, you don't have to mount the partition to zap it. Just use gparted and delete all partitions.

This.

Do you want to recover information from the HDD, or just clear it and format it?

---

### Post by Motorhead Kaze on 2009-04-21
SSD: &#12354;&#12426;&#12364;&#12392;&#12358;.

I will give that a try.

I am curious about one little thing. The USB external case I put the hdd into usually has a 120Gb drive in it. I see that there is a little chip board inside the case...does that somehow confuse my system into believing that a 320Gb drive is a 120Gb drive?  Just a curiosity.

In other news, when I got my desktop back with a new motherboard and SATA drive I hooked up the funky 320drive via the USB. Again I installed an XP/Hardy double system and XP believed that this 320 drive was actually 127gb and offered to reformat it.  In Ubuntu, Places showed a 207Gb (one partition of the 320) and 107gb (the other partition) but could not access either. I decided to play around and reformat the disc, and ended up with a "127Gb" empty disc.....so now 127Gb external drive shows up in Ubuntu and XP. Freaky weird. So...to quote a tv commercial from the 80's "WHERE'S THE BEEF!?!"

I have decided that since I can get a used 250Gb internal Sata drive for $20 in "Denden town" (Osaka) that I would rather trust that, than a freaky 320 that believes it is a 127. Odd thing.

I am going to write "solved" here, but am still going to try your suggestion for the learning experience. I will come back and post my findings.

Thanks for your time!

---

### Post by sgosnell on 2009-04-22
Gparted doesn't delete drives, it deletes partitions.  You can delete both partitions, but you need to do it in the correct order.  If one partition is a logical partition inside a primary partition, you need to delete it first, then the primary.  I don't know which you have, if either.  You might have two primary partitions, and if so you can delete them in any order.  Just remember, drives and partitions are different things.

---

### Post by -kg- on 2009-04-22
My suggestion would be to read the following Community Wiki page:

[https://help.ubuntu.com/community/HowtoPartition]("https://help.ubuntu.com/community/HowtoPartition")

This will give you a good guide on partitioning operations.

Indeed, if what you click on is "Unallocated Space," then you won't be able to delete it.  There's nothing in unallocated space to delete.  You will need to delete the existing partitions.

> Gparted doesn't delete drives, it deletes partitions. You can delete both partitions, but you need to do it in the correct order. If one partition is a logical partition inside a primary partition, you need to delete it first, then the primary. I don't know which you have, if either. You might have two primary partitions, and if so you can delete them in any order. Just remember, drives and partitions are different things.

Exactly.  The Primary partition that sgosnell is talking about is called an Extended partition.  You cannot delete an Extended partition that contains logical paritions within it...you must delete all the Logical partitions (which are partitions created within it) first.  It is likely that your XP partition is outside of the Extended partition (if one exists), making it a Primary partition as well.  You can delete that at any time.

My further suggestion to you is to download the [GPartEd Live CD]("http://gparted.sourceforge.net/") (found on the last page of the above Wiki page).  This is a live CD that focuses primarily on GPartEd, and I have used it extensively.  GPartEd on the Live CD should work as well, though.

---

### Post by egalvan on 2009-04-23
Since everything seems to see the drive as 127GB,

Maybe the drive is jumpered to limit the size?
(around that 127GB limit, many drives came with the capability to hard-limit the size...)

Maybe the USB adapter used to connect the drive is limited to 127GB?
(older/cheaper chipsets may be limited to the max size they can access... I had one that had this limit...)

I would check the drive label or circuit board for any information regarding LIMIT or CUT-OFF, or something along those lines.

Try to find a computer you could use to test this drive in...
Try to find another adapter/enclosure you could use....

download dban (Darik's Boot and Nuke, dban.org) and run the software to TOTALLY erase that drive.

dban does not mess around with partitions and such...
it just nukes the whole thing from orbit...
it's the only way to be sure...

---

### Post by Motorhead Kaze on 2009-04-23
Wow! Lots of replies. Thank you all. Yes, I did realize that a drive and a partition were 2 different things, my original question was how to delete the hard drive. I wanted to WIPE the hard disc drive completely, not the partitions. I thought there was a "weapon of mass-device destruction" that was a bit less destructive than say...a microwave oven. Heh heh. You all gave me a lot to think about.

127Gb limiting chipset in the CASE?! AH HA! That would SPLAIN it wouldn't it? The case is FIVE years old now, and back then, 120Gb was like...mega...dude. Had I known about this possibility I would have mentioned it earlier. Sorry bout that. But let me retrace my story to see if I have screwed the proverbial pooch yet.

When I formatted this 320Gb drive originally, I put XP in first, then Ubuntu in another partition. Just followed the prompts in the Ubuntu setup, nothing special. I allocated 207Gb or so to Ubuntu, leaving 107Gb to XP. Used it like that for a year or so. My motherboard died a few weeks ago while I was in Ubuntu. Last weekend I got a replacement motherboard, but the drive was IDE and the replacement motherboard was only set up for SATA. So, I put the 320Gb IDE hdd into an external USB case hoping to clear it out and use it as an external drive with my laptop. But when I did that, I could not gain access to the Ubuntu partition, but the XP partition was ok. I deleted the partition that xp was on, and used Gparted to reformat that partition which WAS 107Gb. It was at this point the disc drive claimed to be 127Gb with no other partitions. When I got my desktop set up again, I hooked up this wonky drive to the desktop via that USB case. I checked it in XP and Ubuntu both and both of them say it is an empty 127Gb drive. After reformatting the partition I WAS able to do something with, the 207Gb partition no longer shows up in "Places" at all.

OK, now maybe all that was already clear, but sometimes I am clear in my head and not on the page... 

Since I went ahead and deleted the stuff on the XP partition and reformatted the thing at 127Gb, I wonder if I have messed it up beyond repair. Trying to delete an invisible partition may be challenging.

As the most recent replies suggested I do, I will see if I can find another computer out there to hook this drive up with. That may take more than a day or two, but I will post my findings.

Thanks again for taking the time to educate!

---

### Post by sgosnell on 2009-04-23
To delete the hard drive, just remove it and use a sledgehammer on it.  You do not want to delete the hard drive, you want to delete all the partitions, add one new partition the size of the drive, and format it.  Or at least that's what I understand you want to do.  In order to do that, you have to delete the partitions in the correct order.

---

### Post by Motorhead Kaze on 2009-04-26
The hammer worked. The data is now absolutely irretrievable. Man these things are built tough though.

But before I did that, I purchased a fun little gizmo for plugging in SATA/IDE devices or even floppy drives. Not knowing if the drive was even going to be usable, I didn't want to go to the expense of buying a case for it. Good thing too. It was unreadable in either Hardy or XP, even after reinstalling drivers, playing with this and that. Ubuntu wouldn't even recognize it at all anymore. That is one of the reasons I keep a dual boot like this, double checking. I didn't actually need the drive, but I don't like to just leave things broken if they can be fixed, and like to know "why" things don't work when I can. Probably the most useful bit of info I got this time around was that some old cases actually cannot read more than the amount of storage space they were designed to read. This time it looks like the thing was actually just broken. RIP.

---

### Post by -kg- on 2009-05-07
> I didn't actually need the drive, but I don't like to just leave things broken if they can be fixed, and like to know "why" things don't work when I can.

If you ever read this again, KUDO's to you!  I have been using computers since the early '80s, and fancy myself an old computer hacker, in the old sense of the term.  I also have the same attitude, trying to fix things just to learn why they broke and what happened, and in some cases what I might do to lessen the likelyhood of the same type of breakdown in the future.

> This time it looks like the thing was actually just broken. RIP.

Yes, all components have a "life," and sooner or later they fail.  In a computer, hard drives are especially subject to this, considering that they have moving parts.  The same can be said for printers and case fans.  Electronic parts might last for years and years (except for a few special cases, like electrolytic capacitors that dry out), but anything with moving parts will only last a certain amount of time.

It almost sounds to me like you had a head crash that resulted in a head mis-alignment where it would no longer read the data on the disk.  Nothing you can do about it except what you have done.

It's a real good reason to always have your critical data backed up to another location, preferably on completely separate media.  I learned this a couple years ago, when one of my hard drives started going south.  I had backed it up, but to another partition on the same drive.  Luckily, I got it going long enough to extract my critical data, but if it had completely gone bad a little quicker, I would have lost a whole lot of my archived files, like music, videos, email files, and the like.

Nice to meet you!

---

### Post by kc600 on 2009-10-06
FYI, i was able to wipe a disk through an adapter.

I used a Conceptronic ('Bus 002 Device 008: ID 152d:2338 JMicron Technology Corp. / JMicron USA Technology Corp. JM20337 Hi-Speed USB to SATA & PATA Combo Bridge') "ATA & IDE to USB adapter" to move data from my nearly-deceased harddisk to the new one. After that, i unmounted the drive's partitions. It turned out i had a '/dev/sdb' device, so i was able to run 'sudo shred -vzf -n 14 /dev/sdb'.

---

### Post by kc600 on 2009-10-06
However, i just found out 'shred'ding isn't much use on journaled filesystems, as 'info shred' mentions. And 'dmesg | grep sdb' tells me that this is an ext3 fs, which is journaling.

---

