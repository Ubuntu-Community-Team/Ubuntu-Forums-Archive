---
title: "partitioning /home"
date: 2009-03-27
forum: New to Ubuntu
---

### Post by raymondh on 2009-03-27
'Apologize if I'm in the wrong forum.

I've read, printed and gathered materials from the forums, ubuntu guides and google.  Am about 90% ready to learn and do this.  Would like to throw a few questions to the group for further guidance.

My goal is to have /home in a separate partition.  There are many advantages to do this but mine is simply just "to learn how to do it". That said, "no harm" if I mess up this re-partion effort as I can always do a fresh install.

Using GParted in the live CD, I have this.... (Dual boot with win7)

Unallocated                      1 Mib
sda1               NTFS        200 Mib (that's win7's doing, not mine)
sda2               NTFS         75 Gib  (Win7)
sda3              EXTENDED     623 Gib
    sda5            Ext3       613 Gib
    sda6          Linux-Swap     9 Gib

*visually, sda5 and sda6 are wrapped inside sda3 ... sorry, am using another pc to write this otherwise I would have offered screenshots

1.  /home currently is at sda5, am I right?  Just wanted to verify for later "terminal" use.
2.  Do I resize sda5, putting the "new" home partition in between the OS and swap?  Or do I resize sda3 hence making the new home partition after the OS and Swap?
3.  Playing with gparted a while ago, I noticed that when I shrunk sda5, I could not make the unallocated space a primary partition.  All I was offered was "logical" partition.  Would this matter?  I have a feeling it's got to be primary hence the thinking that I maybe need to resize sda3.

Of course, I clicked "undo" before I learned something wrong.

Any other inputs/thoughts much appreciated.

Thanks .... Raymond

---

### Post by perrti-y02 on 2009-03-27
I suspect sda5 is in fact /root which will have as a directory in it /home. to have it as a separate partition you would need to resize sda5 and put it somewhere in there.

As I understand the structure of partitioning you may only have 4 "real" partitions on a disk. i.e the 2 that windoze 7 wants plus your extended partition and one other. Within an extended partition you may have some more partitions that aren't true partitions. These are logical partitions.

I may be talking total crap but that is how I understand it.

---

### Post by raymondh on 2009-03-27
> **perrti-y02 said:**
> 
As I understand the structure of partitioning you may only have 4 "real" partitions on a disk. i.e the 2 that windoze 7 wants plus your extended partition and one other. Within an extended partition you may have some more partitions that aren't true partitions. These are logical partitions.

You're right on the 4 max PRIMARY partitions per HD.  From my count (and I may be wrong), I have NTSF + NTSF + EXTENDED = 3.  Sda 5 & 6 are inside sda3 EXTENDED.  I think that's the reason why when I was playing with resizing sda5, I was only given the "logical" partition option and not primary.  Hence, I was thinking that maybe I should resize sda3 extended.

Am I right in this assumption?

Also, does the unallocated 1Mib (in front of win7) count as a PRIMARY?  If so, what can anyone reco to keep this HDD within 4 partitions?


Thanks for your input.

raymond

---

### Post by louieb on 2009-03-27
> **raymondhenson said:**
> Y I was only given the "logical" partition option and not primary.

Extended and logical partitions inside are how you get around the 4 primary partition limit. :)Good news, unlike Widows; Linux does not care if its installed in a logical or primary partition. 
The [Psychocats]("http://www.psychocats.net/ubuntu/index.php") link in my signature has a page on creating a separated /home partition.
[Nuts n Boldt: Partitions 101]("http://louboldt.com/ilinuxpart.htm")

---

### Post by raymondh on 2009-03-27
Thanks LouieB ... I do have psychocats' guide.  In fact, his tutorial did resize EXT3 instead of EXTENDED.  I just wanted to make sure.

Thanks again.

---

### Post by raymondh on 2009-03-27
here's the gparted screenshot

---

### Post by SuperSonic4 on 2009-03-27
Yeah, shrink sda5 and put in the home partition there

---

