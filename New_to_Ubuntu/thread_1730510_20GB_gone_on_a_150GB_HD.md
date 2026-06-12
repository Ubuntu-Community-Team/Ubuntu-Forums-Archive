---
title: "20GB gone on a 150GB HD"
date: 2011-04-16
forum: New to Ubuntu
---

### Post by Vallar on 2011-04-16
Hello everyone, 

I recently decided to abandon Windows and switch over to Ubuntu fully. I originally had Windows 7 Ultimate installed; downloaded the Ubuntu 10.10 64bit version and inserted the CD on startup. I chose the install-Ubuntu-alone-on-entire-disk option. 
After the installation was done and through the update, I managed to notice that I only had 130 GB free space from a 150 GB HD. Last time I installed Ubuntu along side Windows 7 (same version of Ubuntu) it only required max 5 GB. So I right clicked on my File System folder and chose properties to find that it took about 8.3 GB. 
Now, why did it take so much space this time? Also, if it took 8.3 GB then there is about 10.7 GB that are lost in dead space; where did they go to? After installation I didn't even copy a single file or download anything, it is just fresh...

Anyway to know what happened here?

---

### Post by r-senior on 2011-04-16
As a start, could you run "Disk Utility", select your disk in the left pane and take a screenshot? Make sure all the contents of the window are visible and post it here.

---

### Post by Vallar on 2011-04-16
Thank you very much for the fast reply. 

Here is the screen shot:

[[IMG]http://img546.imageshack.us/img546/5026/screenshotkp.png[/IMG]]("http://img546.imageshack.us/i/screenshotkp.png/")

Uploaded with [ImageShack.us]("http://imageshack.us")

---

### Post by Drenriza on 2011-04-16
The way HDD are manufactured. You lose 20MB pr 1 GB. Since manufactures sees 1GB as 1000mb but in reality 1GB is = 1020MB. So if you buy a 150GB it will never be on exactly 150GB. Your system sees it as less.

This is not equal to all the disk space you've "lost" but it adds to it.
So on a 150GB disk you lose 3GB.

---

### Post by Vallar on 2011-04-16
Yeah, but that is a 160 GB HD which means it only has 150 GB. So if we do the math... Ubuntu took 8.3 GB on installation 150 - 130 = 20 GB. Yet, what I have is 8.3 GB when I look into the properties of the System Folder; where is the rest?

---

### Post by MrEgg on 2011-04-16
Here's my 2 cents :

1. don't forget that ext4 filesystems by default reserve 5% of total space for root. That's again space you won't see available.

2. you do seem to have bad sectors on your drive as it shows on the SMART status on the screenshot you posted. That could also account for your difference.

---

### Post by r-senior on 2011-04-16
Sorry, should have asked this before, but could you also do this in a terminal:

```

df -B1

```

and post the output?

---

### Post by Vallar on 2011-04-16
Yeah, I have noticed the bad sectors. Should I use the Disk Utility to try and fix them?

vallar@Neverland:~$ df -Bl
df: invalid -B argument `l'
vallar@Neverland:~$ df -Bi
df: invalid -B argument `i'
vallar@Neverland:~$ ^C
vallar@Neverland:~$

---

### Post by r-senior on 2011-04-16
It's a 1 (one). Meaning show usage and space in bytes.

---

### Post by Dayofswords on 2011-04-16
> **Vallar said:**
> 

vallar@Neverland:~$ df -Bl
df: invalid -B argument `l'
vallar@Neverland:~$ df -Bi
df: invalid -B argument `i'
vallar@Neverland:~$ ^C
vallar@Neverland:~$

it's a 1(one)

anyway, where it missing? you have your 154GBext4 and 6.5gb swap

---

### Post by Vallar on 2011-04-16
vallar@Neverland:~$ df -B1
Filesystem           1B-blocks      Used Available Use% Mounted on
/dev/sda1            151091912704 11969495040 131447365632   9% /
none                 1305456640    331776 1305124864   1% /dev
none                 1312477184    233472 1312243712   1% /dev/shm
none                 1312477184     90112 1312387072   1% /var/run
none                 1312477184         0 1312477184   0% /var/lock
none                 151091912704 11969495040 131447365632   9% /var/lib/ureadahead/debugfs
/dev/sdc1            15726702592 11579199488 4147503104  74% /media/76B01838B017FD75
/dev/sdc5            24280993792 17687531520 6593462272  73% /media/8A00C6CF00C6C205
vallar@Neverland:~$ 


Oh, sorry, I am new; I didn't know that is a one. It displays on the screen the same way an "l" does with this font.

Edit:
Sorry, but can I ask another question please? Kind of related to the HD too; I have just noticed.

---

### Post by MrEgg on 2011-04-16
> **Vallar said:**
> Yeah, I have noticed the bad sectors. Should I use the Disk Utility to try and fix them?


It wouldn't hurt trying - if it doesn't work, then you'll want keep a close eye on that, and make sure you have working backup strategy!

---

### Post by Sidewinder1 on 2011-04-16
Vallar, somewhat OT but pertinent to the 1 vs l vs I situation with fonts, I have found it easier, when requested to input a command from here to my terminal, to simply copy from here and paste into my terminal; this method also solves many syntax and space issues. Example:

```
copy and paste this into your terminal
```

HTH,
Side

---

### Post by grahammechanical on 2011-04-16
Hi Vallar

Windows on installation creates a swap file. Linux installations create swap partitions. As an aside, my sister has a 160 GB hard disk in her laptop but only half of it is available for use in Vista as the rest is partitioned into another drive (partition in Linux). I am guessing that this is for Windows system restore points storage. Which, in my opinion, is a waste of space which does not happen in Linux.

Regards.

---

### Post by Vallar on 2011-04-16
I would be a liar to say I knew about C&P working in terminal. I thought it was like CMD, there was no C&P. 
From now on I will do that; though typing makes it easier to memorize the commands. Dare I ask what does df -B1 means? 

Grahammechanical, I always make sure to disable the restore points in Windows and delete them. 

Just one question before I mark the thread solved; when I copy from a HD that is connected through USB to my laptop a couple of files I see that the copy dialog displays the speed 8.6 MB, then all of a sudden it goes down to 700 KB and goes up again to 980ish KB and stops there... what may cause this problem? The files are 4.5 - 9.5 GB in size.

---

### Post by r-senior on 2011-04-16
Nobody done the adding up then? ;)

There's always the confusion between dividing between 1000 or 1024 for GB, so I've listed both.

```

Bytes              Gb      GB   Description
--------------- ----- -------   --------------------
160041885696	149.1	160.0	Total drive (a)
  6540845056	  6.1	  6.5	Swap partition (b)
			
153501040640	143.0	153.5	Root filesystem (c = a - b)
			
 11969495040	 11.1	 12.0	Used (d)
131447365632	122.4	131.4	Available (e)
  7675052032	  7.1	  7.7	Reserved root (f = 5% x c)
151091912704	140.7	151.1	Total usable (g = d + e + f)

Therefore ...

  2409127936	  2.2	  2.4	presumably ext4 overhead (h = c - g)

```

Presumably any bad blocks count in 'h', along with formatting. You could consider that lost, but it's unavoidable. The discrepancy between what you thought and what is actually unavailable is the reserved space for root and that you have actually used 12GB, not 8.3GB.

---

### Post by Vallar on 2011-04-16
Ehmm... why can't it be obvious like Windows? <.<  I see now... which to be honest makes me feel I troubled you guys for nothing; sorry :/

---

### Post by richaoj on 2011-04-16
fyi shift + ctrl + v to paste in terminal and command prompt (in windows).

also, windows 7 basic installation requires 16-20 gigs hdd space, so this is not that bad in comparison.

---

### Post by srs5694 on 2011-04-16
> **Drenriza said:**
> The way HDD are manufactured. You lose 20MB pr 1 GB. Since manufactures sees 1GB as 1000mb but in reality 1GB is = 1020MB.

You've got the right basic concept but the details are off.

Disk manufacturers have long used power-of-ten units, so that 1 gigabyte (GB) = 10^9 bytes = 1,000,000,000 bytes. This is in conformance with the official [International System of Units (SI) prefixes.](http://physics.nist.gov/cuu/Units/prefixes.html) Many computer units, though (including disks, actually) are more precisely measured using power-of-2 units. Thus, many moons ago, people in the computer field began mis-using the SI units, applying "k" to 1024 (2^10), "M" to 1,048,576 (2^20), "G" to 1,073,741,824, etc. This violates the SI meaning, but was considered "close enough." Unfortunately, with each increase in units, it gets less and less close -- for instance, the power-of-2 version of k is just 2.4% more than a true k, whereas for M it's 4.9% off, and for G is 7.4% off.

Thus, a new standard of naming was invented for computers: [IEEE-1541.](http://en.wikipedia.org/wiki/IEEE_1541-2002) In this standard, new names and prefixes have been adopted: kibi (Ki), mebi (Mi), gibi (Gi), tebi (Ti), and so on. The computer industry is *slowly* shifting to using these new values (or using the old ones with proper SI meanings). This is true of the major Linux partitioning software -- for instance, fdisk and parted use true SI units, while gdisk and GParted use IEEE-1541 units.

The bottom line of all this is that you're not "losing" anything, any more than you lose volume in a bottle of soda when you convert its measurement from quarts to liters. You're just measuring in different units. There's great potential for confusion, though, particularly if you don't understand these units or if whatever software or spec sheet you're using misapplies them. I've bothered to write this message in the hope of clearing up the first potential problem, but of course it's up to software authors and manufacturers to deal with the second.

Oh, and a related issue: "B" means "bytes," whereas "b" means "bits". Thus, you'd normally measure disk space in KiB, MiB, GiB, etc, not Mib, Mb, or other such units. The lowercase "b" is often used in measuring transmissions speeds over modems, network protocols, etc.

[quote=MrEgg]you do seem to have bad sectors on your drive as it shows on the SMART status on the screenshot you posted.[/url]

I recommend replacing the drive. Bad sectors are *not* a good sign. Drives that develop bad sectors that SMART reports sometimes start getting much worse very quickly.

---

### Post by Vallar on 2011-04-16
Hmm... that was a bit confusing to be honest. Though now I finally understand what is going on, specially with MiB and Mib, it confused me for a long time.

Thank you very much :D

---

### Post by Sidewinder1 on 2011-04-16
Vallar, one thing you can rest assured upon; the more you learn about Linux (Ubuntu), the less sense Winbloze makes...
Does the above sound weird or is it me?
Well, you guys/gals know what I mean.  ;)

---

### Post by Vallar on 2011-04-16
Yeah, I hope one day I have as much understanding of Ubuntu as I have with Windows; soon would be nice too.

---

### Post by Sidewinder1 on 2011-04-16
Don't worry, it'll happen.
I just managed to connect my Ubuntu box to the upstairs windows, network printer; it's a brand new Brother color laser printer and it works {Sidewinder is beating on his chest yelling "I am the greatest!!!"}
With all things, there is a first time...

Side

---

### Post by Vallar on 2011-04-16
Congratulations!!!! :D

---

### Post by the-ridikulus-rat on 2011-04-17
[http://stopabusingsiprefixes.org/stopabusing.html](http://stopabusingsiprefixes.org/stopabusing.html)

---

