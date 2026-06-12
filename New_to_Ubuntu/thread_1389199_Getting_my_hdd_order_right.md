---
title: "Getting my hdd order right"
date: 2010-01-24
forum: New to Ubuntu
---

### Post by mbzn on 2010-01-24
Hi, this isn't a life/death situation but i would like to fix it.
I have 5 hard drives...
1. internal SATA with (/; /home; swap; and xp)
2. internal SCSI mounted as /media/docs(ntfs)
3. internal SCSI mounted as /media/music(ntfs)
4. external SATA for storage
5. external SATA for storage

now drives 4 & 5 is storage and backup so i don't use them often and are usually switched off so:

sda is hdd 1; sdb is hdd 2 and sdc is hdd 3 (1,2 & 3 as above)
and sdd&sde my e-SATA's(backups)

however wile booting with my e-SATA turned on, i have it that my e-SATA drives are sdb & sdc and my SCSI's is now sdd & sde. 
Which lead to the wrong partitions being mounted in /media/docks and /media/music.

So booting with the e-SATA's off works fine but when turned on they cause trouble.
Can i make Ubuntu see the SCSI's before seeing the e-SATA's

Thanks for any advice

---

### Post by PenguinInside on 2010-01-24
Sorry this doesn't answer your question, but how are the SCSI's working for you?

Faster than the SATA's?

---

