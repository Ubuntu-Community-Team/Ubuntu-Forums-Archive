---
title: "Qs re: I/O error after install + partitions"
date: 2011-02-04
forum: New to Ubuntu
---

### Post by Nico-dk on 2011-02-04
I really shouldn't be posting this in the beginner forum. I installed my first ubuntu distro a few years ago, but must admit, I've been neglecting it :oops:

So after doing a clean install of 10.10 on a T43, I have a few questions, I hoipe someone will be kind enough to answer.

**1) I/O Error dev sr0**
After installation during clean-up, I suddenly got a screeen full of the abovementioned error. Then I noticed the disc had popped out, so I assume sr0 must be the dvd drive, correct?

Afterwards everything seems to work just fine (except I forgot my keyring password :oops: (don't laugh :mrgreen: )
[COLOR="Red"]Seems this is related to my cd popping out
Take out the discm close the tray and type return.
Ubuntu will restart as expected[/COLOR]


**2) Partitions**
Maybe I'm just too windows struck, but when a new version is released, I'd like to keep photos, music, docs etc. so I was thinking of creating 3 partitions.

sda0/ for the OS (to update)
sda1/ for music, docs, etc
swp/

Sda0 should be primary, but what about sda1 and swp?
Both logical or?
[COLOR="Red"]Found the answer

sda1 should be ext4 and have mountpoint / (primary)
sda2 should be ext3 and have mounpoint Home (logical)
swp (logical)
[/COLOR]

**3) fdisk -l**
Only useable as root?
I did a fdisk -l several times w/o any result returned at all. sudo fdisk -l worked though
[COLOR="Red"]Because that's how it works[/COLOR]

which leads to my 4th and final question

**4) sda1 - 5 bytes**
When doing fdisk as described above, I noticed sda0 was alocated most of the diskspace, sda1 was alocated 5 bytes (?), and swp 200MB.
I did an autoinstall (ie. not advanced disk partitioning). Does anyone know why such a small second partition was created?


Thanks for you time

---

### Post by Dutch70 on 2011-02-04
Open Gparted & take a pic of it, add it to your post as an attachment instead of "insert image" and you may get more responses.

Also, in order to keep your photos & such when you upgrade to a new distro, you simply have to create a separate /home partition. That would be /dev/sda7 in my example pic below.

[COLOR="Red"]***EXAMPLE PIC...***[/COLOR]

---

### Post by Nico-dk on 2011-02-04
Thanks :)

Couldn't take a screenshot, as the I/O error occurred after installing during the forced restart.
I'm reinstalling anyway (since I forgot the keyring password), so no further help is needed on the partition questions

I had some time to search, and it seems it could be related to this: [http://ubuntuforums.org/showthread.php?t=1015569](http://ubuntuforums.org/showthread.php?t=1015569) or at least to the fact that the disc was ejected.

I also found some answers to some of my other questions (apparently (re-) learning is fun)

---

### Post by Dutch70 on 2011-02-04
Great, glad you got it worked out.

ps. for the record, I meant for you to take a pic "of" Gparted, so we could see your partitions. btw, I have reinstalled Ubuntu several times since 8.04 Hardy & I've never lost my pics, music, not even my settings. As a matter of fact, it even kept my bookmarks in Firefox.

Good luck
Dave

---

