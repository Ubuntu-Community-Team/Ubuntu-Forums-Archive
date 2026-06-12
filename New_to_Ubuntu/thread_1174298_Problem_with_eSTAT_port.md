---
title: "Problem with eSTAT port"
date: 2009-05-30
forum: New to Ubuntu
---

### Post by DSClear on 2009-05-30
My laptop has eSATA port, I connected with a backup HD. Strange thing is, during install ubuntu I can still see it from the location box in the partition process. But now after installed the system, I cannot find it anymore. The backup HD is WD 160g in NTFS. I input lspci in the terminal and it report the SATA controller is recognized, like below:

04:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)

I don't think I have to format the disk to be ext3 or ext4 to let linux to recognize it, right?

---

### Post by LeSaint on 2009-05-30
No, you dont have to format it.

You most probably need to mount it.  You can from the command line, the easiest though is to look under the places menu if you are running gnome, and you might see it there.  Clicking it will mount it for you.

If not, you may have to mount it as follows

mount /dev/sdb1 /media/backup

If you dont have permission, do it as a sudo command.  Also you will need to make sure that the directory: /media/backup exists, and also that /dev/sdb1 is the right device.

---

