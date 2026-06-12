---
title: "Backup Ubuntu along with Softwares Installed"
date: 2010-03-22
forum: New to Ubuntu
---

### Post by ranktip on 2010-03-22
Hi,

I installed Ubuntu on my machine and configured the system accordingly. I also installed quite a few new software programs and configured them too according to my choice.

I want to take a backup of the entire system along with the software programs installed and the configurations so that if my system crashes or if I want to boot up a new machine, I can install from my backup get everything similar to what I have now instantly.

Is this possible? Any help would be much appreciated.

Thanks.

---

### Post by phidia on 2010-03-22
Your might want to check out ghost4linux (g4l) there's an older tutorial [here]("http://www.howtoforge.com/back_up_restore_harddrives_partitions_with_ghost4linux").

---

### Post by walt.smith1960 on 2010-03-22
I don't have first hand experience with Clonezilla  [http://clonezilla.org/](http://clonezilla.org/) but have read some good reviews. I use a shareware solution 'Image for Linux' from [http://www.terabyteunlimited.com/index.htm](http://www.terabyteunlimited.com/index.htm)  It will do incremental backups and files can be extracted individually. I've used it to move partitions to new hard drives and have had good success with it. Get everything the way you want it then create an image. That way, if things fail you can restore a known-good system.

Unsolicited plug though I have no relationship to Terabyte or its' principles. 

I also use BootIt NG from the same publisher. The useful thing about BootIt NG is that I can have 200+ primary partitions if I want, and can let different operating systems access different partitions in addition to the O.S's partition. BootIt NG has a peculiar interface but does seem to work well.  The biggest trap with Ubuntu & Bootit NG is when installing, be sure to specify placing grub in the partition, not in the MBR.  If Grub overwrites BootIt NG's Extended MBR, it gets ugly.:oops:

---

### Post by sq7bti on 2010-03-28
In such case I wonder if a tool that does this exist:
- create a complete list of installed packages (e.g. dpkg --get-selections)
- checks for any file that was modified with respect to the its default contents (repository content) : (e.g. debsums)
- checks for any other file that might have been added manually to an usual configuration, log and cache location (e.g. /etc, /var etc.)

Backup created this way would be way smaller than verbatim copy of existing installation. It might help also to find problems with a working system, it would allow for a quick comparison between a working and non-working configuration.

Any thoughts?

s.

---

### Post by nitstorm on 2010-03-28
> **ranktip said:**
> Hi,

I installed Ubuntu on my machine and configured the system accordingly. I also installed quite a few new software programs and configured them too according to my choice.

I want to take a backup of the entire system along with the software programs installed and the configurations so that if my system crashes or if I want to boot up a new machine, I can install from my backup get everything similar to what I have now instantly.

Is this possible? Any help would be much appreciated.

Thanks.


Tried remastersys??? [http://www.psychocats.net/ubuntu/remastersys](http://www.psychocats.net/ubuntu/remastersys)

---

