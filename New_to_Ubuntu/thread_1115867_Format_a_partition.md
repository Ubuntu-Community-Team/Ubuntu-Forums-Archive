---
title: "Format a partition?"
date: 2009-04-04
forum: New to Ubuntu
---

### Post by mmitt on 2009-04-04
I have windows 7 installed on one partition, and windows vista installed on another partition on the same HD. If I wanted to format the Windows 7 partition by itself and not touch the Vista partition, would that be possible? If so, how could I do this?

---

### Post by damis648 on 2009-04-04
From Windows:

Boot up in Vista
Head to My Computer
Right click the Windows 7 drive > Format

From an Ubuntu LiveCD

System>Administration>Partition Managaer
Right click the Windows 7 Partition > Format

:-)

**_[COLOR="Red"]WARNING![/COLOR]_**
If the bootloader for Windows is installed on the Windows 7 Partition, you may not be able to boot Vista again. You will need to boot up the Vista install CD and choose Recovery Console and then type
```
fixmbr
```

---

### Post by mmitt on 2009-04-04
> **damis648 said:**
> From Windows:

Boot up in Vista
Head to My Computer
Right click the Windows 7 drive > Format

From an Ubuntu LiveCD

System>Administration>Partition Managaer
Right click the Windows 7 Partition > Format
Thank you! I figured that's what I had to do, but I wasn't sure if it was safe...
> **_[COLOR="Red"]WARNING![/COLOR]_**
If the bootloader for Windows is installed on the Windows 7 Partition, you may not be able to boot Vista again. You will need to boot up the Vista install CD and choose Recovery Console and then type
```
fixmbr
```
The bootloader would be on Vista if it was installed on my laptop when I got it, right? It was the first OS installed on the HD. But I don't have a Vista install CD, could I use the recovery partition if the bootloader is on W7?

---

### Post by BoogeyOfTheMan on 2009-04-04
Search around in Vista to see if there is a way to make a recovery disk. Or see if you can borrow a disk from a friend. 

If Vista came pre-installed on C: and you installed W7 on D, E, F, etc, then you SHOULD have no problems with just reformatting the W7 drive. If W7 is on C, then you will MOST LIKELY run into problems if you reformat.

---

### Post by mmitt on 2009-04-05
> **BoogeyOfTheMan said:**
> Search around in Vista to see if there is a way to make a recovery disk. Or see if you can borrow a disk from a friend. 

If Vista came pre-installed on C: and you installed W7 on D, E, F, etc, then you SHOULD have no problems with just reformatting the W7 drive. If W7 is on C, then you will MOST LIKELY run into problems if you reformat.
I have a recovery partition. Would that fix Vista for me?

---

### Post by BoogeyOfTheMan on 2009-04-05
I really have no clue. I never used that feature becuase I hated having it use my disk space. From what I remember, its supposed to be able to recover, but I'm not sure. I beilieve it can also vary from manufacturer to manufacturer. My Dell didnt come with a Vista restore partition, it came with a proprietary driver install partition of about 10mb or so.

---

### Post by ShaunG on 2009-04-05
I recently screwed up my mbr on a pc. I used the restore feature...pressed f10 just after power up and the pc reset itself to factory settings. 

That is to say that the pc went back to a 2004 install of windows and the hard drive was re formatted back to just c:/ for windows and d:/ for recovery.

So restore may work, but boot into a live cd and copy off all important data to a flash stick or external hard drive first.

---

### Post by keypox on 2009-04-05
if you format the w7 partition i think you will lose boot for vista.  

Because you installed w7 and w7 used its bootloader... i wouldnt do it like that

I would just use the vista disc but since ytou dont have it.  Maybe use easybcd in vista and get rid of win7 from vista.

---

