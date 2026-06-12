---
title: "'Fake RAID' Configuration"
date: 2009-01-19
forum: New to Ubuntu
---

### Post by Paul_WB5AGF on 2009-01-19
Greetings;

I have an Intel DG965WH motherboard which has an on-board 'fake RAID' capability and I have been running Windows XP with two drives in a RAID 1 configuration ('mirroring').

For awhile I thought that I was going to have to add a third hard drive for UBUNTU but then I stumbled across an article that led me to the 'alternate' installation disk as it provides access to the 'dmraid' software.

Using the 'alternate' UBUNTU installation disk got UBUNTU 8.10 installed and running but I cannot figure out how to 'tell' dmraid that a FAT32 drive partition, on both drives A and B, should be treated as a single drive in RAID 1. When I 'look' at the FAT32 partitions from within UBUNTU it sees two drives instead of just one.

Is there a configuration file that tells dmraid what partitions should be treated as a single RAID 1 partition ?

One of the problems that I have had, in researching this situation, is that doing a 'Google search' finds everything and it is very difficult for me to know what is still valid information. Apparently, in an earlier distribution of UBUNTU, 'fake RAID' configurations were not supported and it is not clear how stable support for 'fake RAID' is even now with UBUNTU version 8.10. If this is an ongoing problem then I can live with it but not knowing if I have done something wrong, or if a bit more work is needed and then all will work, that is the most bothersome part of this problem.

Is what I have run into a common problem ? Is there a solution ?

Thanks;

Paul (WB5AGF to other Amateur Radio Operators)

---

### Post by Kellemora on 2009-01-19
Hi Paul

As one Ham to another, dump the RAID system and just run independent mirror for backup!

TTUL - 73+ de Gary - KG0ZP

---

