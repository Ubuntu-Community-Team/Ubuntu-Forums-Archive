---
title: "Buffer I/O error"
date: 2011-04-13
forum: New to Ubuntu
---

### Post by Gr72 on 2011-04-13
Can anyone help me with this problem....

I am a newbie when it comes to linux. About a year ago I installed Ubuntu into a dual boot with winows 7. I accidentally deleted the Ubuntu partition from within windows and left it. After a registry error in the windows partition I re-installed windows over everything and has been working fine. But, now I am getting back into linux and have been trying to install Ubuntu ans use a Backtrack liveCD but I can't and recieve this error:

Buffer I/O error on device sr0, ;ogical block 993427
Buffer I/O error on device sr0, ;ogical block 993428
Buffer I/O error on device sr0, ;ogical block 993427
Buffer I/O error on device sr0, ;ogical block 993428

SQUASHFS error: squashFs_read_data failed to read block 0x7583e78f
SQUASHFS error: unable to read id index table

BusyBox v 1.10.2 (Ubuntu 1:1.10.2-1 Ubuntu7) built in shell (Ash)
Enter 'Help' for list of built in commands




If Any one can help me with this, that would be great, I have been picking my brains over this and have googled it but have come up with nothing. Thanks

---

### Post by rosencrantz on 2011-04-13
sr0 is your optical drive, and buffer I/O suggests data corruption.
Burn another CD and try again.

Good luck,
rosencrantz

---

