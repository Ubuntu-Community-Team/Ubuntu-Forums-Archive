---
title: "Detect Hard Drive EXTERNAL"
date: 2009-04-12
forum: New to Ubuntu
---

### Post by nevinalex1234 on 2009-04-12
Pls help i m a newcommer .i want to detect my external Harddrive on Ubuntu
But it is not detecting


root@nevinalex-myworld:/home/nevinalex# dmesg|tail
[ 4746.722808] sd 12:0:0:0: [sdc] Write Protect is off
[ 4746.722817] sd 12:0:0:0: [sdc] Mode Sense: 00 38 00 00
[ 4746.722822] sd 12:0:0:0: [sdc] Assuming drive cache: write through
[ 4746.724307] sd 12:0:0:0: [sdc] 312581808 512-byte hardware sectors (160042 MB)
[ 4746.725060] sd 12:0:0:0: [sdc] Write Protect is off
[ 4746.725067] sd 12:0:0:0: [sdc] Mode Sense: 00 38 00 00
[ 4746.725072] sd 12:0:0:0: [sdc] Assuming drive cache: write through
[ 4746.725081]  sdc: sdc1 sdc2
[ 4746.752403] sd 12:0:0:0: [sdc] Attached SCSI disk
[ 4746.752490] sd 12:0:0:0: Attached scsi generic sg2 type 0

I TRIED THE COMMAND 

sudo mount /dev/sdc /home/nevinalex/Desktop/tarun


bUT IT DID NOT work
PLSS HELP ME...i installed linux only yesterday

---

### Post by MrWES on 2009-04-12
> **nevinalex1234 said:**
> Pls help i m a newcommer .i want to detect my external Harddrive on Ubuntu
But it is not detecting


root@nevinalex-myworld:/home/nevinalex# dmesg|tail
[ 4746.722808] sd 12:0:0:0: [sdc] Write Protect is off
[ 4746.722817] sd 12:0:0:0: [sdc] Mode Sense: 00 38 00 00
[ 4746.722822] sd 12:0:0:0: [sdc] Assuming drive cache: write through
[ 4746.724307] sd 12:0:0:0: [sdc] 312581808 512-byte hardware sectors (160042 MB)
[ 4746.725060] sd 12:0:0:0: [sdc] Write Protect is off
[ 4746.725067] sd 12:0:0:0: [sdc] Mode Sense: 00 38 00 00
[ 4746.725072] sd 12:0:0:0: [sdc] Assuming drive cache: write through
[ 4746.725081]  sdc: sdc1 sdc2
[ 4746.752403] sd 12:0:0:0: [sdc] Attached SCSI disk
[ 4746.752490] sd 12:0:0:0: Attached scsi generic sg2 type 0

I TRIED THE COMMAND 

sudo mount /dev/sdc /home/nevinalex/Desktop/tarun


bUT IT DID NOT work
PLSS HELP ME...i installed linux only yesterday

I'm assuming your did a mkdir for the mount point tarun.

What file system is on the external drive? And did you try /sdc1 ?

Bill

---

### Post by drowner on 2009-04-12
> **nevinalex1234 said:**
> Pls help i m a newcommer .i want to detect my external Harddrive on Ubuntu
But it is not detecting


root@nevinalex-myworld:/home/nevinalex# dmesg|tail
[ 4746.722808] sd 12:0:0:0: [sdc] Write Protect is off
[ 4746.722817] sd 12:0:0:0: [sdc] Mode Sense: 00 38 00 00
[ 4746.722822] sd 12:0:0:0: [sdc] Assuming drive cache: write through
[ 4746.724307] sd 12:0:0:0: [sdc] 312581808 512-byte hardware sectors (160042 MB)
[ 4746.725060] sd 12:0:0:0: [sdc] Write Protect is off
[ 4746.725067] sd 12:0:0:0: [sdc] Mode Sense: 00 38 00 00
[ 4746.725072] sd 12:0:0:0: [sdc] Assuming drive cache: write through
[ 4746.725081]  sdc: sdc1 sdc2
[ 4746.752403] sd 12:0:0:0: [sdc] Attached SCSI disk
[ 4746.752490] sd 12:0:0:0: Attached scsi generic sg2 type 0

I TRIED THE COMMAND 

sudo mount /dev/sdc /home/nevinalex/Desktop/tarun


bUT IT DID NOT work
PLSS HELP ME...i installed linux only yesterday

External hard drives are usually mounted automatically.

perhaps you could post the output of 

> sudo fdisk -l

I guess its connected via USB. If that's the case, also show us

> lsusbquote


And, your command to mount it was incorrect, so I'm not surprised it didn't work. But we can work it out.

---

### Post by drowner on 2009-04-12
And, are you logged in as root? That is generally a very bad idea. I strongly recommend not doing that.

---

