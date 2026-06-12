---
title: "HDD--Few bad sectors, passed, ridiculous Reallocated Sector Count... Fix?"
date: 2011-08-02
forum: New to Ubuntu
---

### Post by Baniita on 2011-08-02
**I've looked on other threads already, but none of them really gave a proper answer as to how to deal with it. Or nothing worked for me.** RMA takes too long--and I don't even know if I still have warranty. I also can't afford taking it in since I'm asq poor.

_**(I talk a lot, so I bolded the important stuff in the case you just want to skim.) Also, I'm a programming and ubuntu noob. Like, I'm not even in the area of relevance, really.)**_ 

The hard drive still functions alright--it's just that some folders take forever to load, and files have corrupted. **Thus the Reallocated Sector Count being some crazy number--18678160 sectors.** Apparently SMART has this glitch where it gives too many false positives but I doubt finding out the real number would help much. The Current Pending Sector count is at 195 in value.** It has passed the self-assessment and labelled itself as having "a few bad sectors".**

Results of a failed attempt at ntfsfix:
```
root@ubuntu:/home/ubuntu# ntfsfix /dev/sda
Mounting volume... Failed to startup volume: Invalid argument.
FAILED
Attempting to correct errors... FAILED
Failed to startup volume: Invalid argument.
Volume is corrupt. You should run chkdsk.

```Results of a failed zero-ing:
```
root@ubuntu:/home/ubuntu# dd if=/dev/zero of=/dev/sda
dd: writing to `/dev/sda': Input/output error
2350073+0 records in
2350072+0 records out
1203236864 bytes (1.2 GB) copied, 81.3818 s, 14.8 MB/s

```[B]
What happened is that the partitions on the disk became all screwy after an interrupted defrag.[/B] Windows 7 wouldn't boot properly after that, and chkdsk and system restore didn't work (just stayed on those screens endlessly without progressing). (Maybe it no longer knew how to access the files?)

**And what I want to do is clean the drive/fix it completely, then re-install Windows 7. If possible.** When I tried to install it before I did all this--I was kind of clueless since it asked me which partition I wanted to install it on, and I'm like, "partitions? Do not want--". And then so I tried formatting and deleting the partitions, but it was all "lololol, i dun no wut2 do so wait a sec" and proceeds to make me wait /forever/. Like an incompetent substitute teacher with no idea what it's doing. Or the result of sexual confusion due to a really hot buff chick. ANYWAY.

[SIZE=3]**DEAR LORDS OF UBUNTU, please *(with an organic cherry on top and a mutilated maraschino)* provide me with assistance and answers to my query. ; v;)/ **[/SIZE]

---

### Post by Hakunka-Matata on 2011-08-02
post the output of```

sudo fdisk -lu
```

please

---

### Post by Baniita on 2011-08-02
sudo fdisk -lu output:
```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0008551e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63   976768064   488384001    c  W95 FAT32 (LBA)

Disk /dev/sdb: 4013 MB, 4013948928 bytes
25 heads, 25 sectors/track, 12543 cylinders, total 7839744 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        8064     7839743     3915840    c  W95 FAT32 (LBA)

Disk /dev/sdc: 2040 MB, 2040528896 bytes
29 heads, 28 sectors/track, 4908 cylinders, total 3985408 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1             247     3985407     1992580+   b  W95 FAT32

```

---

### Post by Paqman on 2011-08-02
> **Baniita said:**
> 
**And what I want to do is clean the drive/fix it completely, then re-install Windows 7. If possible.**

You're probably out of luck. What SMART reports on is the state of the disk at the hardware level. There's no much you can do about that by messing around with the filesystems and partitions on that.

You Reallocated Sector Count is nonsense, which should ring alarm bells. It looks like either the firmware on the drive or the disk control hardware are on their last legs. Either way, your Pending Sector Count (if it's accurate) would be cause for concern on its own.

Looks like you disk is kaput. **Back up your important data pronto**, and get yourself a new disk.

---

### Post by Baniita on 2011-08-02
...Teaaaars, man. Tears. ; v;

/Laughs hysterically. I've always had bad luck, though, ne?

I find it strange though, that other people with the same ridiculous sector counts get warnings and have their disks not pass self-assessment. Mine does, and only says it's a "few". (I'm currently running sudo badblocks -sv /dev/sda >> badblocks.report). Am I fooling myself with false hope? . _.

Is there any way I can figure out if the issue is in the hardware or because of that defrag interuption?

I'll head to the store tomorrow and see what they can do and if I still have my warranty. The problem is that I don't think they'll provide me with a new one since it got screwed up from a defrag error.

Anyone know a good place online to get 500GB hard drives?

---

### Post by Paqman on 2011-08-02
> **Baniita said:**
> 
I'll head to the store tomorrow and see what they can do and if I still have my warranty. The problem is that I don't think they'll provide me with a new one since it got screwed up from a defrag error.


Don't mention the defrag thing, because it's probably not relevant anyway. All defragging does is shift data around on the filesystem, it can't kill disk sectors any more than normal everyday read and write operations. Interrupting it might risk corrupting some data, but it's not going to kill the hardware.

Just say that the SMART data shows horrendous numbers of bad sectors. If the drive is still under warranty then the manufacturer has to take it back, no questions asked. I'd go straight to the manufacturer of the drive myself, it'd be quicker.

---

### Post by Baniita on 2011-08-02
Anyway--I'm not going anywhere today, so I'd like to at least try to see what I can do at all.

So... chkdsk. Can anyone help me figure out how to run that on my hard drive? Even though I'm on ubuntu... (I'm on a live USB.)

---

### Post by nerdy_kid on 2011-08-02
first thing I would do is ddrescue (sudo apt-get install gddrescue) the entire disk onto another bigger drive, and then try to recover the files.

---

### Post by psusi on 2011-08-02
The drive is toast; you need to replace it.  If it isn't still under warranty ( and it should be ), then you'll need to buy a new one.  newegg.com is a good place to do so.

---

### Post by Hakunka-Matata on 2011-08-02
Thanks for running fdisk -lu, I wanted to see how it reported on a drive that is apparently failing badly.  
It shows a:

[LIST]
[*]500GB drive sda
[*]4GB drive      sdb
[*]2gb drive       sdc
[/LIST]
are you running on a couple of USB sticks?  
I guess the 500GB drive is the one that  SMART reports all the errors on?

tigerdirect has low prices.  Shipping time and money can be a problem if you need it fast, they are located in South Florida and ship from there. 

I've had two brand new 250GB drives recently that started reported bad sectors right away, I watch (check) new drives frequently now, if the bad sector  count increases/changes, quickly (a week), they tend to continue downhill.  they were all replaced without resistance at no cost, so that part is good.

Thanks, and good luck

---

### Post by Wim Sturkenboom on 2011-08-03
Maybe it's only me but why do you run a *ntfsfix* on a FAT32 partition ?

And if you don't trust the Linux tools, you can use the diagnostic tools from the manufacturer.

---

### Post by Baniita on 2011-08-03
I don't need to recover any files. Everything is backed up. Thanks, though. :3

@your signature: Hey, hey! My data is my /LIFE/. :C The only reason I had no updated back up on it was because I was still organizing everything... And, well, there was too much data and I didn't have the money for storage. . u.)" It's like saying "if it was important to you, you wouldn't have lost it"--which was completely false for me. I lose everything from gaming consoles to /entire bags/ to keys to... Well, that's just because I'm a scatter brain. = v=)'

---

### Post by Baniita on 2011-08-03
Because apparently that ntfsfix was some sort of chkdsk equivalent. = v=)" And I don't know what I'm doing, remember? /Ahahaha...!! Ha.. Ha... (Teaaars.)

There's fruit flies in my room and it's like they're mocking me: "your hard drive is tooooaaast. :D Friiiied. It's rotten and we can smell itttt."

The bad sector count is increasing... It's obviously untrue, but that command I tried from the terminal didn't work (to calculate the real bad sectors). It's in the 23mil count now. And it's still labelling itself as having only "a few bad sectors". Yeah, pretty sure it'll fail in a few weeks or so. = __x)

I installed ubuntu on it, by the way. So far, everything works fine. . _.

ONLY DOWNHILL FROM NOW! YAAY. :'D

Ffff. *Tears intensify.*

Thanks for all the replies, people. Even though it seems that nothing but an RMA can be done. :C

---

