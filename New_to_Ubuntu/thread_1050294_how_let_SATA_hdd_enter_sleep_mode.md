---
title: "how let SATA hdd enter sleep mode"
date: 2009-01-25
forum: New to Ubuntu
---

### Post by say2sky on 2009-01-25
for IDE hdd

```

hdparm -Y /dev/hd*
hdparm -S8 /dev/hd*

```
can be used to let PATA hdd enter sleep mode for power saving.

Now I use SATA hdd, I also hope to let them sleep for power saving. 
sdparm is for SATA hdd parameter adjustment, but I cannot find a switch for sleep mode.
any suggestion?

---

### Post by say2sky on 2009-01-26
need help.

---

### Post by sdennie on 2009-01-26
The command is the same except instead of /dev/hd* you need to use /dev/sd*.  If you are using ext3 it probably won't keep your drive asleep for more than 5 or 10 seconds with -Y though because the journal commit will wake it back up (and the -S8 will probably never happen).  You can get it to sleep better with this guide: [  HOWTO: Decrease disk activity]("http://ubuntuforums.org/showthread.php?t=839998") but, if you are using a desktop machine, I believe that most are only rated to about 20,000 sleep/wakeup cycles so, it can be dangerous to use this.

---

### Post by say2sky on 2009-01-26
> **sdennie said:**
> I believe that most are only rated to about 20,000 sleep/wakeup cycles so, it can be dangerous to use this

thanks a lot for your help.

about the sleep/wakeup cycles, I wonder if wakeup can be forbid through removing hdd device file, such as 
```

echo "scsi remove-single-device host channel ID LUN " > /proc/scsi/scsi

```

I notice smartd daemon wake up hdd for checking hdd status, but I am not sure if removing hdd device file can keep hdd all time sleep.  I hope anyone can clear if it is a reliable solution. I googled a lot but can not found an answer to this.

---

### Post by sdennie on 2009-01-26
> **say2sky said:**
> thanks a lot for your help.

about the sleep/wakeup cycles, I wonder if wakeup can be forbid through removing hdd device file, such as 
```

echo "scsi remove-single-device host channel ID LUN " > /proc/scsi/scsi

```

I notice smartd daemon wake up hdd for checking hdd status, but I am not sure if removing hdd device file can keep hdd all time sleep.  I hope anyone can clear if it is a reliable solution. I googled a lot but can not found an answer to this.

I doubt it.  The disk will wakeup very, very often if you are using ext3.  Without going to extreme measures it's not possible to keep an ext3 partition from writing to the disk.  I already provided once such link but, "idle machine != idle disk".  It's always going to be written to.

---

### Post by say2sky on 2009-01-26
> **sdennie said:**
> it's not possible to keep an ext3 partition from writing to the disk. I already provided once such link but, "idle machine != idle disk". It's always going to be written to.

if all partitions on one hdd are umount from directory tree and device file for all partitions is removed,  no filesystem from this hdd can be accessed from os again.

Perhaps this problem need more clear thinking and explanation about how hdd works when no device file for all partitions on it.

---

