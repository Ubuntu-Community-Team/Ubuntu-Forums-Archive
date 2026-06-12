---
title: "Safe &amp; Fast file transfers with... WFT!!! Windows?!"
date: 2009-06-04
forum: New to Ubuntu
---

### Post by wwwwolf on 2009-06-04
Hello, Community;

Before anything else, please allow me to state:

This is not flame bait and I am not trying to cause any ruckus.

I'm an old guy. Perhaps not THAT old in years, but considering I started playing with computers when:

- M$ DOS 2.1 had just been released;
- floppy disks were floppy had been just shrunk to 5 1/2";
- a 360K disk contained both Lotus 1-2-3 AND heaps of spreadsheets and;
- 5Mb hard disks were outrageously large in capacity!

Well, I guess I *am* old.

I have been using Linux for a couple of years. Started with Knoppix (Oh, wasn't that THE revolutionary system? Danke schön, Herr Knopper!) and have been playing with different distros ever since.

I am, notwithstanding, a newbie. Sure, I am not a complete beginner: I can read some logs, browse the net for answers, tweak things here and there and perhaps even ask 'the right questions' from time to time. Heck, I *did* develop stuff with Borland's Turbo Pascal, coded a bit in Assembly and created countless DBase apps before getting fancy and compiling stuff with Clipper... But I *AM* a newbie.

At best, I am a "Newbie++". And I will consider myself one until I feel completely at ease dealing with Slackware and/or compiling the kernel.

I have a couple of laptops at home which I use as 'servers'. You know, the machine gets a bit old for the heavy jobs, instead of throwing it away I turn it into an FTP server, or a Web Server, or a test-bed for Asterisk... Things like that. Nothing too serious, mind you. I just enjoy the learning process. It's a hobby, I could say.

I also have Macs (which I use for work) and two Windoze machines running. And that brings me to the point of the thread.

I bought a 2TB WD 'My Book' to backup two other WD's I have. (I know, I know... RAID would be better but bear with me).

I plugged all three drives into a Xubuntu 9.04 box and started transferring files. The process was really slow, though. Tranferring 700Mb, 900Mb, 1Gb files would take 15, 20, 30 over minutes per file! I have been copying files for 3 days now!

I experienced some disconnections (USB problems, maybe?) and some weird 'permissions' problems (perhaps because I had used the drives on Windoze as well) but the most pesky problem I had was not being able to copy some directories and their contents because of an I/O error.

A bit of investigation showed the folders had been created by a previous attempt but something went wrong and they just got 'stuck' in the file system.

ls -l showed the permission setting of the folders as "d?????????" belonging to user "????????" and group "????????". Seriously! The question marks are not being used to mask information. They showed like that!

I could not delete the damn things. I could not overwrite 'em. I could not chmod or chown 'em... I, too, was stuck. And I had a couple of those.

So I started checking things. The drives were 'auto-mounted' in two different ways. One was set as 'fuseblk', the other as 'vfat'. Since I had been accessing both remotely using 'cifs', I tried to mount them manually like that.

Got all sorts of errors. Either invalid blocks, or error codes -22 and -6. RTFM-ing did not help me much and frustration started setting in.

I am positive that someone with more experience would be able to figure the issue out and fix it with a command or two, but that was certainly not my case and when I started finding answers in Google that suggested completely erasing my data, I panicked.

That's when that little voice whispered in my ears: Were these drives not originally formatted for Windoze? Linux is probably translating NTFS the best way it can but... Why don't you try plugging them to that old XP laptop?

So I did.

The laptop recognized the drives with the usual "Tu-duh" sound and from the console prompt I issued the old friend 'chkdsk /f'. (Well, I tried 'ScanDisk' first but seems that does not exist anymore.)

The proggie found errors in the drive, fixed them and in 3min I was good to go again. I looked for the bad directory entries and they were gone. I created the new one with the same name, it was fine. Then I thought: Hmmm... Since I am already plugged and fixed, maybe I will transfer that file to the folder before returning to my Linux box.

And that's when I got baffled! The copy process took 29 seconds. No kidding! I thought there was something wrong. Maybe the file was corrupted or something. Opened it and there it was, intact.

So I tried another folder with another file. Again, 30 seconds or so. Then another. And another... Heck, I thought, I have been copying files for 3 freaking days and this thing is transferring them in seconds?! What gives?

So... THAT - oh, enlightened ones - THAT is my question:

What gives?!?

Why was it so painfully slow in Linux? It it the process of reading the 'undocumented' file structure? Is there any transformation involved? Why would a file take 25 minutes to copy on a Linux box and 30 seconds on a windoze machine? I am perplexed!

Granted, that specific Linux machine is a Pentium III whereas XP is on a Centrino but... From 25min to 30secs???

And if you, dear reader, can indeed explain where does the bottleneck lie, perhaps you would also be capable to answer the following:

- Why wouldn't CIFS mount my drives locally if remotely it worked?
- Why even the root user could delete, chmod, chown those naughty bad directory entries?
- How could I have fixed them in Linux if I had completely abandoned M$?

Anyone willing to share the knowledge?

Thanks in advance.

Cheers

---

### Post by billgoldberg on 2009-06-04
> **wwwwolf said:**
> Hello, Community;

Before anything else, please allow me to state:

This is not flame bait and I am not trying to cause any ruckus.

I'm an old guy. Perhaps not THAT old in years, but considering I started playing with computers when:

- M$ DOS 2.1 had just been released;
- floppy disks were floppy had been just shrunk to 5 1/2";
- a 360K disk contained both Lotus 1-2-3 AND heaps of spreadsheets and;
- 5Mb hard disks were outrageously large in capacity!

Well, I guess I *am* old.

I have been using Linux for a couple of years. Started with Knoppix (Oh, wasn't that THE revolutionary system? Danke schön, Herr Knopper!) and have been playing with different distros ever since.

I am, notwithstanding, a newbie. Sure, I am not a complete beginner: I can read some logs, browse the net for answers, tweak things here and there and perhaps even ask 'the right questions' from time to time. Heck, I *did* develop stuff with Borland's Turbo Pascal, coded a bit in Assembly and created countless DBase apps before getting fancy and compiling stuff with Clipper... But I *AM* a newbie.

At best, I am a "Newbie++". And I will consider myself one until I feel completely at ease dealing with Slackware and/or compiling the kernel.

I have a couple of laptops at home which I use as 'servers'. You know, the machine gets a bit old for the heavy jobs, instead of throwing it away I turn it into an FTP server, or a Web Server, or a test-bed for Asterisk... Things like that. Nothing too serious, mind you. I just enjoy the learning process. It's a hobby, I could say.

I also have Macs (which I use for work) and two Windoze machines running. And that brings me to the point of the thread.

I bought a 2TB WD 'My Book' to backup two other WD's I have. (I know, I know... RAID would be better but bear with me).

I plugged all three drives into a Xubuntu 9.04 box and started transferring files. The process was really slow, though. Tranferring 700Mb, 900Mb, 1Gb files would take 15, 20, 30 over minutes per file! I have been copying files for 3 days now!

I experienced some disconnections (USB problems, maybe?) and some weird 'permissions' problems (perhaps because I had used the drives on Windoze as well) but the most pesky problem I had was not being able to copy some directories and their contents because of an I/O error.

A bit of investigation showed the folders had been created by a previous attempt but something went wrong and they just got 'stuck' in the file system.

ls -l showed the permission setting of the folders as "d?????????" belonging to user "????????" and group "????????". Seriously! The question marks are not being used to mask information. They showed like that!

I could not delete the damn things. I could not overwrite 'em. I could not chmod or chown 'em... I, too, was stuck. And I had a couple of those.

So I started checking things. The drives were 'auto-mounted' in two different ways. One was set as 'fuseblk', the other as 'vfat'. Since I had been accessing both remotely using 'cifs', I tried to mount them manually like that.

Got all sorts of errors. Either invalid blocks, or error codes -22 and -6. RTFM-ing did not help me much and frustration started setting in.

I am positive that someone with more experience would be able to figure the issue out and fix it with a command or two, but that was certainly not my case and when I started finding answers in Google that suggested completely erasing my data, I panicked.

That's when that little voice whispered in my ears: Were these drives not originally formatted for Windoze? Linux is probably translating NTFS the best way it can but... Why don't you try plugging them to that old XP laptop?

So I did.

The laptop recognized the drives with the usual "Tu-duh" sound and from the console prompt I issued the old friend 'chkdsk /f'. (Well, I tried 'ScanDisk' first but seems that does not exist anymore.)

The proggie found errors in the drive, fixed them and in 3min I was good to go again. I looked for the bad directory entries and they were gone. I created the new one with the same name, it was fine. Then I thought: Hmmm... Since I am already plugged and fixed, maybe I will transfer that file to the folder before returning to my Linux box.

And that's when I got baffled! The copy process took 29 seconds. No kidding! I thought there was something wrong. Maybe the file was corrupted or something. Opened it and there it was, intact.

So I tried another folder with another file. Again, 30 seconds or so. Then another. And another... Heck, I thought, I have been copying files for 3 freaking days and this thing is transferring them in seconds?! What gives?

So... THAT - oh, enlightened ones - THAT is my question:

What gives?!?

Why was it so painfully slow in Linux? It it the process of reading the 'undocumented' file structure? Is there any transformation involved? Why would a file take 25 minutes to copy on a Linux box and 30 seconds on a windoze machine? I am perplexed!

Granted, that specific Linux machine is a Pentium III whereas XP is on a Centrino but... From 25min to 30secs???

And if you, dear reader, can indeed explain where does the bottleneck lie, perhaps you would also be capable to answer the following:

- Why wouldn't CIFS mount my drives locally if remotely it worked?
- Why even the root user could delete, chmod, chown those naughty bad directory entries?
- How could I have fixed them in Linux if I had completely abandoned M$?

Anyone willing to share the knowledge?

Thanks in advance.

Cheers

You should post this on Launchpad as a bug.

That's all I can say about it.

If could be ntfs-3g related.

---

### Post by LowSky on 2009-06-04
google "Linux USB transfer slow" for more informaiton

Basically the Linux drivers for USB dont work very well with large file transfer and will often stall a transfer (at least in my experience). Its been an issue for over a year or so now. The community as a whole hasn't taken notice becuase transfer of large GB size files isn't a supposedly normal thing to do. I guess they dont use video media player like iPods... I don't know? Its one of those things that really irks me but I dont know enough to go fixing the driver.

hopefully someone knows more than I do, my soluiton is to boot into Windows and transfer files, as Windows is usually faster and doesnt fail  at USB transfers.

see my thread form earlier this year
[http://ubuntuforums.org/showthread.php?t=1112701](http://ubuntuforums.org/showthread.php?t=1112701)

---

### Post by freakyruft on 2009-06-04
I experienced the same when transfering much data to (or from) a ntfs - I think it's ntfs-3g related, but I submitted a bug report ca. 1 year ago, don't think they will fix it.
The CPU runs to 50% (1 core 100%) during this process and the tranfer rate gets slower and slower, right?

---

### Post by Jerry N on 2009-06-04
Possibly your old machine only supports USB 1, not USB 2?

BTW, the 5mb drive you mentioned was not only outrageously big, it was also outrageously expensive!  My first HD was 10mb and cost me $500 with the controller card.  That was a special price - it had originally been $1000.  

What's a Windoze?

Jerry

---

### Post by Celauran on 2009-06-04
I think LowSky is probably on to something. I've all but given up on using USB drives for backups after bricking two of them.

---

### Post by LowSky on 2009-06-04
Oh I am and so is Launchpad
[https://bugs.launchpad.net/gvfs/+bug/197762](https://bugs.launchpad.net/gvfs/+bug/197762)

---

### Post by Astarroth on 2009-06-04
One thing that I can think of right off is that the p3 box would be using usb 1.0 transfer speed where as the mybook is usb 2.0.
The xp box is most likely using usb 2.0. That may account for some of the increase in speed. Other then that :confused:

Slow on the post I see Jerry N had the same thought.

---

### Post by bacardiandwatermelon on 2009-06-04
Quick question. Did you try the linux box again after the chkdsk? You could always try to run a livecd on the Centrino to rule out hardware stuff...

---

### Post by LowSky on 2009-06-04
Here is the thing, for using my Less than 6 month old PCs (the ones in my sig) speeds are faster than USB 1.1, but nowhere near USB 2.0 rates. 
A 300MB file under linux takes almost 2 minutes, Same file off the same partition under Windows transfers in under 10 seconds

The same issue could be effecting USB printers and other devices like cameras. Because many noob Linux users just accept that some devices might not work... we really dont know how far this rabbit hole goes.

what are we going to do when USB 3.0 comes out in 2010? Its supposed to reach 600MB/s.

---

### Post by The Cog on 2009-06-04
The LInux equivalent of chkdisk is fsck.vfat (there isn't an fsck.ntfs). You could have tried that. A bad disk can really slow down transfers in either OS.

---

### Post by M4rotku on 2009-06-04
This seems odd to me.  I can transfer files to my external HDD faster than a mac and windows.  I can transfer about 4 gigs in around 15 minutes.

---

### Post by wwwwolf on 2009-06-05
> **billgoldberg said:**
> You should post this on Launchpad [...] It could be ntfs-3g related.

Indeed, I noticed the ntfs-3g process was using a lot of CPU but never getting to 100%. I wouldn't dare posting on Launchpad when I can't even explain the problem in proper terms. But thanks for tipping in. :)

> **LowSky said:**
> Google "Linux USB transfer slow" for more information [...] See my thread form earlier this year
[http://ubuntuforums.org/showthread.php?t=1112701](http://ubuntuforums.org/showthread.php?t=1112701)

Ha! I knew I would not be the first to have this problem. Thanks for the links.

> **freakyruft said:**
> I experienced the same [...] The CPU runs to 50% (1 core 100%) during this process and the transfer rate gets slower and slower, right?

Yeah! That's exactly it. Until it's dragging, slowly dripping bytes to the device. :(

> **Jerry N said:**
> Possibly your old machine only supports USB 1, not USB 2?

That did not cross my mind. Since others had the same problem, I think it might not be the case, though. At least not entirely. Perhaps one of the factors slowing things down. Worth checking anyway. Thanks for the tip!

> **Jerry N said:**
> BTW, the 5mb drive you mentioned was not only outrageously big, it was also outrageously expensive!

Geez, that is also very true! Ha! To think my mobile phone has (lots) more memory built-in makes me chuckle! :)

> **Jerry N said:**
> What's a Windoze?

Oh, that's the Voldemort of OS's. Murphy's Operating System. It's the explanation I give my customers every time something goes terribly wrong in their systems and I don't know the actual reason. <grin>

> **Celauran said:**
> I've all but given up on using USB drives for backups after bricking two of them.

Damn! Now you made me worry even more. I am definitely getting a RAID...

> **Astarroth said:**
> One thing that I can think of [...] usb 1.0 transfer speed [...] That may account for some of the increase in speed. [...] Slow on the post I see Jerry N had the same thought.

Valid nonetheless. Thanks for sharing, Astarroth. USD 1.0 could be hell! ;)

> **bacardiandwatermelon said:**
> [...] You could always try to run a livecd on the Centrino to rule out hardware stuff...

You're right. That's worth trying too. Just to see how it performs and check what is the processor impact on the equation. Thanks, Bacardi.

> **LowSky said:**
> Here is the thing [...] speeds are faster than USB 1.1, but nowhere near USB 2.0 rates. The same issue could be effecting USB printers and other devices like cameras. [...] What are we going to do when USB 3.0 comes out in 2010? Its supposed to reach 600MB/s.

Wouldn't it be great if these issues were ironed out before that? Transferring large amounts of files would require seat-belts!!! :)

> **The Cog said:**
> The LInux equivalent of chkdisk is fsck.vfat (there isn't an fsck.ntfs) [...].

Ah-ha! I knew there would be something! I will RTFM on this one. Thanks, Cog.

> **M4rotku said:**
> This seems odd to me. I can transfer files to my external HDD faster than a mac and windows. I can transfer about 4 gigs in around 15 minutes.

Can you elaborate on config, file system etc?

Thanks to all.

---

### Post by anewguy on 2009-06-05
You had DOS?  I had "stuff" pre-CP/M days and was elated when CP/M came out.  Dos by the way, was based off of CP/M.  A lot of the original calls were pretty much the same as in CP/M.

Old?  Nah.....you're just a kid!!

Dave :)

---

### Post by The Cog on 2009-06-05
I seem to remember that my first stab at programming involved writing the octal for the instructions on a bit of paper, then repeatedly setting the number on the switches and pressing Deposit. An age putting it all in, and a fraction of a second for it to go horribly wrong. So don't go feeling too old and sorry for yourself - you don't have a monopoly on it.

---

### Post by anewguy on 2009-06-05
> **The Cog said:**
> I seem to remember that my first stab at programming involved writing the octal for the instructions on a bit of paper, then repeatedly setting the number on the switches and pressing Deposit. An age putting it all in, and a fraction of a second for it to go horribly wrong. So don't go feeling too old and sorry for yourself - you don't have a monopoly on it.

Yeah - remember those old days very well back with the 1st "personal" computer.  For some reason the name escapes me right now, but I know we still did the same thing on the old S100 bus machines until CP/M matured enough that all you had to do was rewrite the BIOS to work with your hardware.  I should add we didn't have paper tape either - manually write up the machine code, flip the address bits, flip the data bits, press store, then on to the next byte.  One mistake normally meant hours of work.

Many years of hand "assembly" and loading in octal codes for everything.  One of the first more "modern" personal computers (name escapes me now - was a little tiny thing that was popular for a year or 2 due to very low cost) I still did that on since the Basic was very limited and didn't really have much hardware support of any kind built in.

Back in those days that's what a hacker was.  Now that term seems to be directed at those who try to bad things with computers.  It's a shame - as advanced as everything is now, I still miss those old days. You had to really know every piece of your hardware at a very low level.  I remember writing a floppy disk "driver" when they were first available using some main controller chip from Western Digital.  Had to step, allow for head settling time, read again, step if needed, wait for head settling time, etc..  That was the stuff that was fun.  Now they are "just" a tool to do things with but not really know how they actually work at the lowest levels.  No pre-delivered drivers, no file type support - you had to write everything you wanted yourself, and do it in such a small amount of memory that most people today think you are bs'ing them.


Dave :)

---

### Post by mgmiller on 2009-06-05
To work with and fix NTFS HDD's in Linux install the package ntfsprogs.
```
sudo apt-get install ntfsprogs
```I have used this to fix drives that I used to have to plug into XP machines and run chkdisk on.

It has a lot of command line stuff as well as adding full NTFS support to the gparted gui.

ntfsfix - Fix common filesystem errors and force Windows to check NTFS.

mkntfs - Format a partition with an NTFS filesystem, optionally bootable.

ntfsinfo - Show some information about an NTFS partition or one of the
files or directories within it.

ntfslabel - Show, or set, an NTFS partition's volume label.

ntfsresize - Resize an NTFS partition without losing data.

ntfsundelete - Recover deleted files from an NTFS partition.

ntfscluster - Locate the owner of any given sector or cluster on an NTFS
partition.

ntfscat - Concatenate files and print them on the standard output
(without mounting the partition).

ntfsls - List directory contents on an NTFS filesystem (without
mounting).

ntfscp - Overwrite files on an NTFS partition.

ntfsclone - Efficiently clone an NTFS filesystem or a part of it.

ntfsmount - Mount an NTFS partition from user-space using libntfs and FUSE.

ntfsdecrypt - Decrypt NTFS-encrypted files (NOT INCLUDED).

ntfscmp - Compare two NTFS volumes and tell the differences.
 command line stuff, like:

---

### Post by mc4man on 2009-06-05
this is clearly a hardware issue, not linux per se. Whether it's the transferring from, transferring to, or combo of hardware I wouldn't know, but certainly linux has no  usb transfer issue itself.

I can transfer large files (.99Gb) and large numbers of them at a fairly decent and consistent pace.

While overall the speed is a tad disappointing, a 7.6 Gb transfer of mainly .99Gb files takes slightly less than 8 min. to a WD drive, around 7:15 to a Seagate (the speeds  fluctuate from 16.5 - 17.2 MB/sec

---

### Post by anewguy on 2009-06-08
> **wwwwolf said:**
> Hello, Community;

Before anything else, please allow me to state:

This is not flame bait and I am not trying to cause any ruckus.

I'm an old guy. Perhaps not THAT old in years, but considering I started playing with computers when:

- M$ DOS 2.1 had just been released;
- floppy disks were floppy had been just shrunk to 5 1/2";
- a 360K disk contained both Lotus 1-2-3 AND heaps of spreadsheets and;
- 5Mb hard disks were outrageously large in capacity!

Well, I guess I *am* old.

I have been using Linux for a couple of years. Started with Knoppix (Oh, wasn't that THE revolutionary system? Danke schön, Herr Knopper!) and have been playing with different distros ever since.

I am, notwithstanding, a newbie. Sure, I am not a complete beginner: I can read some logs, browse the net for answers, tweak things here and there and perhaps even ask 'the right questions' from time to time. Heck, I *did* develop stuff with Borland's Turbo Pascal, coded a bit in Assembly and created countless DBase apps before getting fancy and compiling stuff with Clipper... But I *AM* a newbie.

At best, I am a "Newbie++". And I will consider myself one until I feel completely at ease dealing with Slackware and/or compiling the kernel.

I have a couple of laptops at home which I use as 'servers'. You know, the machine gets a bit old for the heavy jobs, instead of throwing it away I turn it into an FTP server, or a Web Server, or a test-bed for Asterisk... Things like that. Nothing too serious, mind you. I just enjoy the learning process. It's a hobby, I could say.

I also have Macs (which I use for work) and two Windoze machines running. And that brings me to the point of the thread.

I bought a 2TB WD 'My Book' to backup two other WD's I have. (I know, I know... RAID would be better but bear with me).

I plugged all three drives into a Xubuntu 9.04 box and started transferring files. The process was really slow, though. Tranferring 700Mb, 900Mb, 1Gb files would take 15, 20, 30 over minutes per file! I have been copying files for 3 days now!

I experienced some disconnections (USB problems, maybe?) and some weird 'permissions' problems (perhaps because I had used the drives on Windoze as well) but the most pesky problem I had was not being able to copy some directories and their contents because of an I/O error.

A bit of investigation showed the folders had been created by a previous attempt but something went wrong and they just got 'stuck' in the file system.

ls -l showed the permission setting of the folders as "d?????????" belonging to user "????????" and group "????????". Seriously! The question marks are not being used to mask information. They showed like that!

I could not delete the damn things. I could not overwrite 'em. I could not chmod or chown 'em... I, too, was stuck. And I had a couple of those.

So I started checking things. The drives were 'auto-mounted' in two different ways. One was set as 'fuseblk', the other as 'vfat'. Since I had been accessing both remotely using 'cifs', I tried to mount them manually like that.

Got all sorts of errors. Either invalid blocks, or error codes -22 and -6. RTFM-ing did not help me much and frustration started setting in.

I am positive that someone with more experience would be able to figure the issue out and fix it with a command or two, but that was certainly not my case and when I started finding answers in Google that suggested completely erasing my data, I panicked.

That's when that little voice whispered in my ears: Were these drives not originally formatted for Windoze? Linux is probably translating NTFS the best way it can but... Why don't you try plugging them to that old XP laptop?

So I did.

The laptop recognized the drives with the usual "Tu-duh" sound and from the console prompt I issued the old friend 'chkdsk /f'. (Well, I tried 'ScanDisk' first but seems that does not exist anymore.)

The proggie found errors in the drive, fixed them and in 3min I was good to go again. I looked for the bad directory entries and they were gone. I created the new one with the same name, it was fine. Then I thought: Hmmm... Since I am already plugged and fixed, maybe I will transfer that file to the folder before returning to my Linux box.

And that's when I got baffled! The copy process took 29 seconds. No kidding! I thought there was something wrong. Maybe the file was corrupted or something. Opened it and there it was, intact.

So I tried another folder with another file. Again, 30 seconds or so. Then another. And another... Heck, I thought, I have been copying files for 3 freaking days and this thing is transferring them in seconds?! What gives?

So... THAT - oh, enlightened ones - THAT is my question:

What gives?!?

Why was it so painfully slow in Linux? It it the process of reading the 'undocumented' file structure? Is there any transformation involved? Why would a file take 25 minutes to copy on a Linux box and 30 seconds on a windoze machine? I am perplexed!

Granted, that specific Linux machine is a Pentium III whereas XP is on a Centrino but... From 25min to 30secs???

And if you, dear reader, can indeed explain where does the bottleneck lie, perhaps you would also be capable to answer the following:

- Why wouldn't CIFS mount my drives locally if remotely it worked?
- Why even the root user could delete, chmod, chown those naughty bad directory entries?
- How could I have fixed them in Linux if I had completely abandoned M$?

Anyone willing to share the knowledge?

Thanks in advance.

Cheers

As an add-on thought, is this old computer by chance using USB 1, not USB 2?  The transfer rate on the old USB was extremely slow compared to USB 2.

Dave :)

---

### Post by Bradtek on 2009-06-08
In my experience files copy/move to and from my NTFS formatted External USB
500GB WD My Book, faster in Ubuntu than they ever did in Windoze.

I am inclined to think (like a few others here) that your older machine
probably has USB v1 / 1.1

> 
USB 2.0 has a raw data rate at 480Mbps, and it is rated 40 times faster than its predecessor interface, USB 1.1, which tops at 12Mbps
[http://www.everythingusb.com/usb2/faq.htm](http://www.everythingusb.com/usb2/faq.htm)

---

