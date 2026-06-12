---
title: "Does linux Need Defrag?"
date: 2009-10-22
forum: New to Ubuntu
---

### Post by nakama85 on 2009-10-22
I realise there is somewhat of a debate about this. However, I seem to have noticed a small but steady decline of speed in my computer. So I was wondering if maybe I need to defrag.

Even if it wouldn't help, would it hurt to try? What program should I use?

I do admit I have downloaded a lot of large files lately but I still have plenty of HD space left.

Any thoughts?

---

### Post by zeroseven0183 on 2009-10-22
Linux/Ubuntu has a different file system from Windows. I don't think there's no need for you to defrag.

If you don't mind me asking, what system are you running? What are the specs, I mean?

---

### Post by nakama85 on 2009-10-22
> **zeroseven0183 said:**
> Linux/Ubuntu has a different file system from Windows. I don't think there's no need for you to defrag.

If you don't mind me asking, what system are you running? What are the specs, I mean?

It's a little older. custom built- 3Gh P4, 4g mem, integrated graphics and sound, x1 500gb SATA HD, x1 160gb SATA HD

---

### Post by jbennett on 2009-10-22
The structure of the ext3/ext4 filesystem is vastly different from the ntfs filesystem Windows uses.  The nature of ntfs creates a need for periodic defragmentation, which is why it is not uncommon for users to do that on occasion with their Windows installation.

The ext* filesystem does not have the same inherent fragmentation and therefore does not require defragmentation in the same way Windows does.

There are several possible reasons for a sluggish system.  Try checking out what services are running by default by taking at look at the contents of /etc/rc5.d/.  Also, running Firefox with many tabs open is a good way to slow down your system. 

Hope that helped a bit.

---

### Post by nakama85 on 2009-10-22
> **jbennett said:**
> Try checking out what services are running by default by taking at look at the contents of /etc/rc5.d/.

thanks! how do I know what is running when looking in that folder. Sorry I just don't really know what I am looking for

---

### Post by Psyphre on 2009-10-22
nakama,

I had a similar experience in the past (I think it was with hardy). Over time it became very sluggish and it started when it became very very low on hard drive space. Even when I freed up space it remained sluggish.

In the end I wiped the hard drive clean and reinstalled ubuntu, never had that problem ever again even though many times I've run out of HD space. No idea why, just some wierd one off occurence.


Another possibility could be some program or process using up alot of resources. 

I find it easier to use 'gnome-system-monitor' to check processes.

One that comes to mind is some kind of tracker/indexing process (this is used by search programs like deskbar,tracker,beagle etc), it scans through your computer to update information on your files to make searching faster. On a single core processor I'd imagine this would be quite a burden to have in the background.


Also consider hardware issues. I wonder if heating could be the culprit. Is is faster when you first turn it on after leaving it off overnight?

---

### Post by nakama85 on 2009-10-22
> **Psyphre said:**
> Also consider hardware issues. I wonder if heating could be the culprit. Is is faster when you first turn it on after leaving it off overnight?

My computer is basically always on (except for reboots required by updates - which I just had tonight) I could be wrong but I don't think heat is n issue, I keep my home very cold (around 67deg F).

Perhaps this screenshot will help someone determine if processes are a problem[IMG]http://lh3.ggpht.com/_UC6twPlLo2o/SuEVOZA4_yI/AAAAAAAAAjA/Do-V6uF8yog/process.png[/IMG]

---

### Post by XCan on 2009-10-23
What kind of speed declination are you experiencing? Programs running slower or starting slower? What is your typical output of "free"? EXT does get fragmented, but not noticably unless you're running with an almost full drive all the time.

---

### Post by earthpigg on 2009-10-23
Linux filesystems do indeed need to be defragged -- about once every ten years.

the price we pay is that we can't fill our filesystems up past 95% full without things starting to break.

to see what is eating your CPU cycles, install htop.

```
sudo apt-get install htop
```

then run it, and sort by CPU%:

```
htop
```


also: are you positive this decline in speed you are noticing isn't all in your head? i'm not calling you a liar, but i am sure i am not the only one here that has dreamed up a monster when in reality facing only thin air from time to time...

---

### Post by Paddy Landau on 2009-10-23
I've found that Firefox (and Thunderbird) can lose speed over time as their databases become fragmented or whatever.

It's easy to fix. I forget where I found this, but it sped up my Firefox considerably.

First, install [sqlite3]("apt:sqlite3") if not already installed (you can just click that link, or use System > Administration > Synaptic Package Manager).

Then, on a regular basis (say, once a month):

[LIST=1]
[*]Close all instances of Firefox, Thunderbird, Seamonkey. Possibly Camino, but I don't know about that.
[*]Just in case, double-check:
```
sudo killall firefox thunderbird thunderbird-bin seamonkey
```
[*]Reorganise the Mozilla databases:
```
sudo find /home -xdev \( -name '*.sqlite' \) -exec sqlite3 {} 'vacuum' \;
```This command finds every file [FONT=Courier New]*.sqlite[/FONT] in all [FONT=Courier New]/home[/FONT] subfolders and runs [FONT=Courier New]sqlite3 vacuum[/FONT] on each. It takes a few minutes to run, so be patient.
[/LIST]
HTH

---

### Post by nakama85 on 2009-10-25
Thanks Everyone! So Far Paddy Landau's solution seemed to help a bit.
I am thinking though, to get everything back to normal I will need to reinstall.
Thanks again everyone for your help!

---

### Post by admelfo on 2009-10-25
Starting to think that my old Pentium III Coppermine processor just can't handle it anymore.

---

### Post by fluxlizard on 2009-10-26
> Starting to think that my old Pentium III Coppermine processor just can't handle it anymore. 

try pclinuxos gnome edition for p3 processor. I have that for my old p3 700 mhz laptop with 256 mb ram and it runs just fine...

---

### Post by irne.barnard on 2009-10-26
I'd actually strongly suggest **not** defraging ... the reason behind this? Even on windows most defraggers have 2 options, 1 Defragment, 2 Compact ... sometimes called something different, but the end result's the same.

The "defragment" is supposed to make all files into contiguous blocks. The "compact" is supposed to defragment **and** make the free space into a contiguous block. Now while this *sounds* nice, the reality is quite different:

Fragmentation does cause productivity loss as each file access now could become hundreds of HDD reads / writes. The file system makes all the difference:

[LIST=1]
[*]FAT based file systems save each file directly following each other. So if you later edit / add to this file, the added portion needs to be saved somewhere else. This **will** create a fragment (or more than one). A new file is saved starting from the 1st blank spot, even if that blank spot is too small to contain the entire file.
[*]NTFS is a bit better in theory, it allows some free space around each file. Then if it notices that the file will become fragmented, it "attempts" to save the entire file in a new location. The caveat to this is "efficiency": if it would not take too much time to save the entire file over again it will be done, otherwise just create a new fragment. Just how it determines "too much time" is up for grabs ... and like most M$ ideas also a secret!
[*]Ext3/4 also generates blank spaces "around" each file. Where it differs significantly from NTFS is that it'll only fragment when it's impossible to keep the file as one single fragment ... that (usually) only happens when the disk becomes too full.
[/LIST]
**_Why defrag utilities don't work:_**

_Defragment:_
All this really does is what ext3/4 already does ... but after the fact. It checks all the files on the HDD, then for all those with more than one fragment it "tries" to move them to an empty space which is large enough. After a while you end up with lots and lots of small bits and pieces of empty space throughout the HDD. With Linux's ext3/4 these are actually designed to prevent fragmentation, they're given a size by ratio and each time the file grows beyond that space it's moved somewhere else and given a larger "buffer zone". With a windows defrag they happen per accident and the size can be anything from one allocation unit (usually 4096 bytes) to may gigs. There's no real "plan" behind it, and it doesn't matter how many times the file's grown or what its size is. It's even possible to have absolutely no space between files, so you end up with a FAT like scenario.

_Compact:_
This is the worst thing you could do to your HDD. Apart from the fact that you're diminishing the mechanical life by overworking it, compacting **will** cause fragmentation in the future. This is because it literally rearranges files to match that found on FAT systems. So the very first edit after a compact will create extra fragments (at least one extra). Some defragers (like Norton Speed Disc) allows for "smart" rearrangement of files. All they basically do is move files which are changed a lot (like documents) to the end of the disk, and all non-changing files (like programs) to the start. They still remove the buffer zones between files. The only time I'd even consider something like this is when the HDD will only be used for read access, but even then there's sometimes better arrangements performance wise.

All that said ... absolutely nothing is ever perfect. :rolleyes: Even ext4 systems do become fragmented (but very seldom such that performance is lost). Main culprits of causing fragmentation on ext3/4 are database systems. These have multiple read & writes in concurrent environments, thus rearrangement to remove fragmentation could actually damage performance. In such cases it's usually a good idea to "now and again" copy the fragmented file off to an external HDD, delete the original & copy it back. This method lets the ext file system "decide for itself" where to best place the previously fragmented file. And then of course don't over fill your HDD, a good limit is around 50%. But absolutely **never** fill it above 80-90%, that's just asking for trouble (no matter what OS / File System you have)!

Some DBMS's have ways of getting around this. E.g. Interbase (or Firebird) makes one file for its database which has exactly a specified size, if the data grows beyond this filesize a 2nd new file is created instead of just growing the 1st. This ensures that each file is only one fragment - but obviously the file may contain quite a lot of wasted space. This is not the default, but for serious DB's it's recommended.

---

### Post by Paddy Landau on 2009-10-26
> **irne.barnard said:**
> I'd actually strongly suggest **not** defraging...
Thank you for a clear explanation. I'll certainly keep these ideas in mind next time I work on Windows!

---

### Post by ndefontenay on 2009-10-26
Excellent explanation of what happens to files on a disk.

Being a Database Administrator, I have to plus what has been said above. Databases are big fragment generators... IF you don't do a little planning before hand.

If anyone is planning on creating a production database be it for a home business or something bigger, don't let the database manage its data file growth. Try to plan ahead by allocating the amount of disk space you think the related database will take in the coming 2 years. This will create a big empty file and the DB will manage its data inside the empty file. This will create less fragmentation in the long run.

This is a very summarize explanation. Best practices are a bit more extensive than that but this is the idea.

The worst case is usually the default scenario. A database is created with a default tablespace of say 100 MB then it increases by 2MB when full. This is a highway to hell.

---

### Post by irne.barnard on 2009-10-26
Thanks, I did my own googling about this. Seeing as I've been on the dark side since the DOS days (only recently coming to the light :lol:) ... I've also been missing Defrag. Yet even in DOS (FAT) I noticed the utter uselessness of a full Compact Defragmentation, as described in my previous post.

Ext file system is not absolutely perfect as yet. :idea: I'd like to see something which "learns" which files usually grow by how much, so that the more you use the system the larger those files' buffer zones become (and the smaller those which don't change).

@ndefontenay: What DBMS do you generally use? As per my explanation I prefer Firebird as much of that pre-planning becomes automatic, but that's only one of the reasons.

---

### Post by lasleym on 2009-10-26
Paddy - this seemingly tiny little fix did noticeable wonders to my FF.  Our system is about 26 days old, so just about the month you suggested.

Thanks for the 'speedy' fix.  
:)

> **Paddy Landau said:**
> I've found that Firefox (and Thunderbird) can lose speed over time as their databases become fragmented or whatever.

It's easy to fix. I forget where I found this, but it sped up my Firefox considerably.

First, install [sqlite3]("apt:sqlite3") if not already installed (you can just click that link, or use System > Administration > Synaptic Package Manager).

Then, on a regular basis (say, once a month):

[LIST=1]
[*]Close all instances of Firefox, Thunderbird, Seamonkey. Possibly Camino, but I don't know about that.
[*]Just in case, double-check:
```
sudo killall firefox thunderbird thunderbird-bin seamonkey
```
[*]Reorganise the Mozilla databases:
```
sudo find /home -xdev \( -name '*.sqlite' \) -exec sqlite3 {} 'vacuum' \;
```This command finds every file [FONT=Courier New]*.sqlite[/FONT] in all [FONT=Courier New]/home[/FONT] subfolders and runs [FONT=Courier New]sqlite3 vacuum[/FONT] on each. It takes a few minutes to run, so be patient.
[/LIST]
HTH

---

### Post by Ozitraveller on 2009-10-26
FYI Ubuntu will defrag itself every 25 (I think, maybe 30) starts, ans fragmentation is usually around 3 - 5%

---

### Post by alphaniner on 2009-10-26
> **Ozitraveller said:**
> FYI Ubuntu will defrag itself every 25 (I think, maybe 30) starts, ans fragmentation is usually around 3 - 5%

That's the automatic file system check (**fsck**), not a defrag.  It does report the fragmentation though.

---

### Post by abcuser on 2009-10-26
Paddy, I suggest to install BleachBit program.
```
sudo apt-get install bleachbit
```

Purpose of this program is to clean-up temporally files from Ubuntu. One of the thinks is to compact Firefox sql-lite database (see attached picture of GUI program).

Idea is to clean-up hard disk from unnecessary files and so free up disk space.

---

### Post by Paddy Landau on 2009-10-26
> **lasleym said:**
> Thanks for the 'speedy' fix.
Pleasure!

> **abcuser said:**
> Paddy, I suggest to install BleachBit program.
I'll have a look at that. It's a bit like CCleaner on Windows, it seems.

---

### Post by delphiexile on 2009-10-26
Under ext3/4 filesystems , we do not need to defrag partitions , because these filesystems need only 5% of free space to work great its architecture permits that.

---

### Post by dE_logics on 2009-10-26
It just came to my mind...you're using gnome...add the CPU frequency applet and set it to userspace and then set it to the full core frequency, if it steps down automatically or even does not step up, it most probably means - 

1)CPU fan/ventilation in general is bad
2)Your system is dirty...open it up and clean it.

Also check in the resources tab of your system monitor if the memory consumption is high and/or CPU utilization is high.

---

### Post by dE_logics on 2009-10-26
> **abcuser said:**
> Paddy, I suggest to install BleachBit program.
```
sudo apt-get install bleachbit
```

Purpose of this program is to clean-up temporally files from Ubuntu. One of the thinks is to compact Firefox sql-lite database (see attached picture of GUI program).

Idea is to clean-up hard disk from unnecessary files and so free up disk space.

At one point I had 1.1 GB free space in the whole of my system!...that pendrive where I installed Gentoo had 860kb of free space and did not even give a glimpse of slowing down.

So the speed in general for all Linux distros does not have to do with free space.

---

### Post by H3l0 on 2009-10-26
BleachBit FTW!!! 

Thx for the suggestion!

---

### Post by sliketymo on 2009-10-26
> **nakama85 said:**
> I realise there is somewhat of a debate about this. However, I seem to have noticed a small but steady decline of speed in my computer. So I was wondering if maybe I need to defrag.

Even if it wouldn't help, would it hurt to try? What program should I use?

I do admit I have downloaded a lot of large files lately but I still have plenty of HD space left.

Any thoughts?

Just a thought.What is your swap situation?:popcorn:

---

### Post by lavinog on 2009-10-26
Another thing to think about:
Hard drives will degrade over time.  Bad sectors are transparently remapped to a different physical location.  This remapping can fragment a file without the OS knowing the file is actually fragmented.  Modern hardrives have algorithims in place to minimize head movement by retrieving data out of order, so defragging may not even offer much benefit anyway.

The best thing I would recommend is to keep plenty of free space.  The less free space you have, the more abuse your drive has to endure.

---

### Post by nakama85 on 2009-10-26
> **sliketymo said:**
> Just a thought.What is your swap situation?:popcorn:

Swap is set to 3.91 Gb

---

### Post by aysiu on 2009-10-26
I'm surprised no one has linked to this yet:
[Why doesn't Linux need defragmenting?](http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting)

It's a pretty thorough explanation.

I've been using Windows for decades, and I've never found defragmentation to actually enhance performance. Seems like a placebo.

---

### Post by irne.barnard on 2009-10-27
> **aysiu said:**
> I'm surprised no one has linked to this yet:
[Why doesn't Linux need defragmenting?]("http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting")

It's a pretty thorough explanation.

I've been using Windows for decades, and I've never found defragmentation to actually enhance performance. Seems like a placebo.That was my whole point: defrag on windows could even degrade the system ... because it causes worse fragmentation.

But it's a lot like a placebo which is also addictive. Once you've used it, you need to keep on using it to fix what it's broken. ](*,)

---

### Post by jrusso2 on 2009-10-27
All file systems fragment and will need to be defragmented under heavy use or limited free space.

When NTFS came out it was said it did not need defragmenting.  OS X they are finding fragments now and Linux does also.

---

### Post by renkinjutsu on 2009-10-27
for me, ext4 fragmentation maxes at around 2% of my total files.. that's pretty good.. but that means linux filesystems DO fragment, but not enough to actually notice a performance difference.. That being said, i don't think fragmentation is the OP's problem (already stated)

could be that firefox is using up too much RAM and ended up pushing everything into swap though... i remember having this problem with evolution-data-server until i uninstalled it... phew!

---

### Post by earthpigg on 2009-10-27
> # NTFS is a bit better in theory, it allows some free space around each file. Then if it notices that the file will become fragmented, it "attempts" to save the entire file in a new location. The caveat to this is "efficiency": if it would not take too much time to save the entire file over again it will be done, otherwise just create a new fragment. Just how it determines "too much time" is up for grabs ... and like most M$ ideas also a secret!
# Ext3/4 also generates blank spaces "around" each file. Where it differs significantly from NTFS is that it'll only fragment when it's impossible to keep the file as one single fragment ... that (usually) only happens when the disk becomes too full.

could this difference have anything to do with percieved slower USB write times in ubuntu and/or linux in general?

trying to treat the USB thumb drive or hard drive (typically formatted FAT32) as if it where an ext3/4 filesystem on a conventional (is "radial" the word?) hard drive?

since this thread is already so full of awesome information, ill ask this too:

exactly how does fragmentation and filesystems 'designed' with traditional hard drives in mind work with flash storage (thumb drives, SD cards, SSD, etc)?

---

### Post by irne.barnard on 2009-10-27
> **earthpigg said:**
> could this difference have anything to do with percieved slower USB write times in ubuntu and/or linux in general?

trying to treat the USB thumb drive or hard drive (typically formatted FAT32) as if it where an ext3/4 filesystem on a conventional (is "radial" the word?) hard drive?

since this thread is already so full of awesome information, ill ask this too:

exactly how does fragmentation and filesystems 'designed' with traditional hard drives in mind work with flash storage (thumb drives, SD cards, SSD, etc)?Again "in theory" a usb flash disk (or solid state disk) "should" not matter about fragmentation since there's "no seektime" as with a revolving disk. Yet still you find that fragmentation causes some delays as the filesystem (which is usually FAT32 for compatibility over different OS's) would follow this procedure:

[LIST=1]
[*]Read FAT (File Allocation Table) to get the address number for the start of the file.
[*]Read the start of the file until the end of the 1st fragment.
[*]Read the FAT for the next fragment's address.
[*]Read the next fragment's data.
[*]Repeat 4 & 5 until all fragments are read. Edit sorry - 3 to 5
[/LIST]
So (although not as bad as with spinning disks) fragmentation still causes speed degradations on flash disks & solid states.

BTW, I've hinted at a FAT like file system being only efficient for a read-only disks. Yet, it's not the most efficient: Due to most spinning disks having more than one disk & 2 sides per disk, fragmenting the file in the same positions across the sides of the disk would be a lot more efficient. Seeing as in this case 8, 16, or even more fragments could be read at once ... although then the disk's controller needs to be able to handle this, as well as the connection to the CPU.

As for writing to SSD: again theoretically it should not matter - comparing to radial disks, the same "work" is performed. Though it "should" be more efficient to write to SSD without rearranging to avoid fragmentation - this may be the "perceived" Linux slowness to USB, but I think there's probably other causes to this.

I know in windows I need to reboot the PC after connecting my external HDD, otherwise it uses it as a USB1 disk and I get about 1MB/sec ... after the reboot it reads as USB2 and throughput averages at about 30MB/sec. I don't have this problem when connecting it to Ubuntu though, always uses at USB2-like speeds.

---

### Post by Andrew.Z on 2009-10-27
> **abcuser said:**
> Paddy, I suggest to install BleachBit program.
```
sudo apt-get install bleachbit
```


Please don't use the ancient, buggy BleachBit version 0.3.1 in the Ubuntu 9.04 repo.  There are new .deb's (version 0.7.0) on the [BleachBit web site](http://bleachbit.sourceforge.net/).  


> **delphiexile said:**
> Under ext3/4 filesystems , we do not need to defrag partitions , because these filesystems need only 5% of free space to work great its architecture permits that.

Yes, but the Mozilla Firefox version 3.x databases *do* become fragmented, and BleachBit defragments them (the 'vacuum' option).  Heavy web surfers should notice an immediate improvement in the performance of the Firefox  Awesomebar (the feature for searching in the URL bar), savings of a few megabytes, and possibility an improvement in Firefox start-up speed.

---

### Post by calc on 2009-12-07
I don't think this has been mentioned yet but using Tranmission (bittorrent) to download files can cause severe filesystem fragmentation at least on ext3. Severe to the point you can't burn a cd iso on a drive that can do 120MB/s sequential without first defragmenting the file. ext4 is supposed to be a bit better about fragmentation problems due to having prealloc. However even it is not perfect and tytso is working on an ext4 defrag utility.

filefrag (filename) will tell you how many extents are in your file and thus to what extent a particular file is fragmented. I don't know if there is a tool that will tell you this for the whole filesystem, but I think fsck might tell you at the end of a run.

---

### Post by Locke_99GS on 2009-12-07
If the drive is rather old, or has sat unused for an extended period of time:

```
dd if=/dev/sda of=/dev/sda
```

As drives get old, or sit unsused for some time, the magnetic imprints on the drive can become weakened, or one bit will begin to alter neighbouring bits, if they're magnetically different. This can lead to a difficult to read drive, and error correction will make it appear slow. Rewriting the drive over itself will make every bit nice, tight, and fresh.

Using *dcfldd* rather than *dd* will provide a progress indicator.

---

### Post by lavinog on 2009-12-07
> **calc said:**
> I don't think this has been mentioned yet but using Tranmission (bittorrent) to download files can cause severe filesystem fragmentation at least on ext3. Severe to the point you can't burn a cd iso on a drive that can do 120MB/s sequential without first defragmenting the file. ext4 is supposed to be a bit better about fragmentation problems due to having prealloc. However even it is not perfect and tytso is working on an ext4 defrag utility.

filefrag (filename) will tell you how many extents are in your file and thus to what extent a particular file is fragmented. I don't know if there is a tool that will tell you this for the whole filesystem, but I think fsck might tell you at the end of a run.

deluge and many others can allocate space for the files before downloading.  Maybe transmission needs to adopt this behavior.

@Locke_99GS:  Interesting info.  Of course don't do this on a mounted disk (sda is likely to be mounted.)  I would backup the drive before doing this also.

---

### Post by seenthelite on 2009-12-07
> **Locke_99GS said:**
> If the drive is rather old, or has sat unused for an extended period of time:

```
dd if=/dev/sda of=/dev/sda
```As drives get old, or sit unsused for some time, the magnetic imprints on the drive can become weakened, or one bit will begin to alter neighbouring bits, if they're magnetically different. This can lead to a difficult to read drive, and error correction will make it appear slow. Rewriting the drive over itself will make every bit nice, tight, and fresh.

Using *dcfldd* rather than *dd* will provide a progress indicator.


A very interesting thread, some different points of view, so what is the answer should people reinstall their OS,s from time to time.

---

### Post by irne.barnard on 2009-12-08
> **calc said:**
> I don't think this has been mentioned yet but using Tranmission (bittorrent) to download files can cause severe filesystem fragmentation at least on ext3. Severe to the point you can't burn a cd iso on a drive that can do 120MB/s sequential without first defragmenting the file. ext4 is supposed to be a bit better about fragmentation problems due to having prealloc. However even it is not perfect and tytso is working on an ext4 defrag utility.

filefrag (filename) will tell you how many extents are in your file and thus to what extent a particular file is fragmented. I don't know if there is a tool that will tell you this for the whole filesystem, but I think fsck might tell you at the end of a run.That's very similar to the problems with databases. It's a large file which gets added to over time. Thus a contiguous space is allocated to it, but once it grows larger a new fragment is created.

Not using torrents, I'm not sure if there's one which would work the following way. Most of the download managers first create a file of the size they're downloading. The content is garble at first, which simply gets filled in as more data is downloaded. This way fragmentation is kept to a minimum in this case. Maybe there's a torrent client which does the same?

---

### Post by irne.barnard on 2009-12-08
> **seenthelite said:**
> A very interesting thread, some different points of view, so what is the answer should people reinstall their OS,s from time to time.Only if you want to. It should be sufficient to remove old files (which you don't need anymore) - of course after backup / archive ;)

Only in the "strange" cases would fragmentation become a problem. Unfortunately you do find some programs which use database like files, and then they don't follow the previously mentioned database pre-allocated file method. One I found cause enormous amounts of fragmentation on Windows is Revit. These files tend to grow (over time) from 50k to 200MB+. I've not tried them on Ubuntu yet, as it doesn't work under Wine.

---

### Post by calc on 2009-12-10
Here is a new comment by Theodore Ts'o about the status of e2defrag.

[https://bugs.launchpad.net/ubuntu/+bug/321528/comments/22](https://bugs.launchpad.net/ubuntu/+bug/321528/comments/22)

---

