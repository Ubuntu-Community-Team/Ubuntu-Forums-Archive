---
title: "slow ethernet speeds, burst peaks"
date: 2007-06-27
forum: Networking &amp; Wireless
---

### Post by mats.lundqvist on 2007-06-27
I've been having really bad network performance on my laptop.

My hardware running feisty:
IBM Thinkpad X40
Ext3fs, Intel 1000MT, 1gb ram and a bit slow 1.8" 4200rpm hdd.

And I get about 5.8MB/s, but only in bursts (shown in the wavelike patterns in the attached screenshot), which I find very peculiar. The harddrive can sustain 10MB/s at _least_, in windows. And besides, I've got enough ram to cache some of those writes I think.

With Feisty, my PATA hdd get recognized as a scsi/sata device so I can't set multicount or other parameters.

/dev/sda:
 IO_support   =  0 (default 16-bit)
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 4864/255/63, sectors = 78140160, start = 0

Any ideas as to the problem?

---

### Post by MightyMag on 2008-02-12
Same here for me and a friend of mine.
I get pretty good performance when I test my SATA-drives with "hdparm -t /dev/sda1" (45-60MB/s)
But when I try moving stuff over my LAN I get terrible performance. And when I transfer stuff from my PATA-drive I get much better performance over LAN. Very strange. I have a SIL3112 chipset on my controller and my friend has a SIL3114 chipset.

---

