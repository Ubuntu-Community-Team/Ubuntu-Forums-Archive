---
title: "Can using dual OS corrupt hard disk?"
date: 2010-12-29
forum: New to Ubuntu
---

### Post by manuganji on 2010-12-29
I have been getting this "reallocated sector count" error in my SMART status for some time now. That Dell says it's because I'm using dual OS (Win7 64-bit and Ubuntu 32-bit). Is this true? If yes, will using Ubuntu 64-bit instead of 32-bit solve my problem? As per that Dell guy's advice I have erased ( over written with random data for 3 cycles and then with '0's for 1 cycle ) the whole Disk and reinstalled Win7 with my recovery disks. Please tell me if i can go for a 64-bit Ubuntu on a separate partition. Currently it shows these values in SMART data - ```
Normalised:100,
Worst:100,
Threshold:50
Value:32 sectors
```

Thanks in advance! 

---------------------------------------------------------------------------
product: Inspiron N5010
vendor: Dell Inc.
version: A04
width: 64 bits
capabilities:
    SMBIOS version 2.6,
    DMI version 2.6,
    64-bit processes,
    32-bit processes
configuration:
	boot: normal
	chassis: portable

---

### Post by audiomick on 2010-12-29
> **manuganji said:**
> I have been getting this "reallocated sector count" error in my SMART status for some time now. That Dell says it's because I'm using dual OS (Win7 64-bit and Ubuntu 32-bit). Is this true?...
I have to admit that I don't know for sure, but I don't see how it could be true... :confused:

---

### Post by matt_symes on 2010-12-29
Hi

```
That Dell says it's because I'm using dual OS (Win7 64-bit and Ubuntu 32-bit).
```I find that very hard to believe (although i might be wrong). I have been multi-booting for years and i have not had any smart errors i could definitively pin on multi-booting.

Did you ask Dell what supporting evidence they had for their assertion?

How old is the drive?

Is the "reallocated sector count" increasing over time, or did  they all appear when you partitioned the disc for dual boot?

Kind regards

---

### Post by mcduck on 2010-12-29
No, it can't. And that's for *sure*.

Any reallocated bad sectors are always a sign of actual physical damage of the disk surface. And that's a pure hardware problem, not something any software could cause to your hard drive.

If the reallocated sector count doesn't increase, you are probably safe for now as the count is still pretty low. but if it starts to increase, even slightly, that's a sign of the hard disc dying. Either way, this would be a good time to make sure you have proper backups of all your important files.

..and if the computer is recently new, even a single bad sector is good enough reason to send it back to manufacturer for repairs (of course unless it's a laptop and you have dropped it at some point, in which case the bad sectors would be your own fault.)

---

### Post by Mark Phelps on 2010-12-29
Actually ... YES .. it can -- but only in rare circumstances such as the following:
1) You mount an MS Window OS partition read/write in Ubuntu
2) You write to that partition
3) You disconnect that partition without doing a clean unmount

This will leave the NTFS partition in a "dirty" state -- and when you try to access it again, Ubuntu will refuse to mount it.

So, while it is possible, it's not something that is routinely going to happen -- as long as you refrain from mounting MS Windows OS partitions read/write and doing unclean removals.

---

### Post by The Cog on 2010-12-29
> **Mark Phelps said:**
> Actually ... YES .. it can -- but only in rare circumstances such as the following:
1) You mount an MS Window OS partition read/write in Ubuntu
2) You write to that partition
3) You disconnect that partition without doing a clean unmount

This will leave the NTFS partition in a "dirty" state -- and when you try to access it again, Ubuntu will refuse to mount it.

So, while it is possible, it's not something that is routinely going to happen -- as long as you refrain from mounting MS Windows OS partitions read/write and doing unclean removals.
This has nothing to do with the hard drive reallocating sectors. Hard drive sector reallocation happens when the disk controller gets errors using a disk sector - it re-maps that sector to a different (spare) one on the disk. The reallocation is a hardware/disk controller issue only, and entirely independent of the operating system that is using the disk.

---

### Post by _0R10N on 2010-12-29
I must agree with mcduck, it looks like a physical damage. Try running some disk analysis tool .

---

### Post by manuganji on 2010-12-30
They have already replaced the disk once. Just before replacement, I had that Reallocated Sector Count Error 'Value'  close to 300 sectors. Then I was using the same dual boot configuration. This disk, hence, is pretty new. Some 2 to 3 months old. 
That Dell guy didn't give a clear reason but said that research was still going on and the issue is debatable ( may be, he was unaware himself and was just trying to talk 'some'thing )
Now this is a Toshiba disk ( Model: ATA TOSHIBA MK5056GSYF ). What disk analysis tools are available? I ran the short Self-test in Disk Utility and it says > Self-Assessment: Passed
Overall Assessment: Disk has a few bad sectors
Bad Sectors: 32 bad sectors
Power Cycles: 136
Powered On: 4.6 years
Temperature: 47 C/ 117 F 

So what do you people suggest? Should I ask for a replacement? Or should I install Ubuntu-64bit hoping it might solve the problem?

---

### Post by stmiller on 2010-12-30
That many bad sectors can be a bad sign. I wouldn't use that drive if I were you,

---

### Post by VonSpyder on 2010-12-30
Thats a failing disk drive. get new one stat.

---

### Post by msandoy on 2010-12-30
> **manuganji said:**
> They have already replaced the disk once. Just before replacement, I had that Reallocated Sector Count Error 'Value'  close to 300 sectors. Then I was using the same dual boot configuration. This disk, hence, is pretty new. Some 2 to 3 months old. 
That Dell guy didn't give a clear reason but said that research was still going on and the issue is debatable ( may be, he was unaware himself and was just trying to talk 'some'thing )
Now this is a Toshiba disk ( Model: ATA TOSHIBA MK5056GSYF ). What disk analysis tools are available? I ran the short Self-test in Disk Utility and it says 

So what do you people suggest? Should I ask for a replacement? Or should I install Ubuntu-64bit hoping it might solve the problem?

You say that the disk is 2-3 months old, and the disk test you ran tells you it has been powered on for over 4 years. You have been given an old damaged disk. A trip back to the service shop is in place.

---

### Post by mcduck on 2010-12-30
> **manuganji said:**
> They have already replaced the disk once. Just before replacement, I had that Reallocated Sector Count Error 'Value'  close to 300 sectors. Then I was using the same dual boot configuration. This disk, hence, is pretty new. Some 2 to 3 months old. 
That Dell guy didn't give a clear reason but said that research was still going on and the issue is debatable ( may be, he was unaware himself and was just trying to talk 'some'thing )
Now this is a Toshiba disk ( Model: ATA TOSHIBA MK5056GSYF ). What disk analysis tools are available? I ran the short Self-test in Disk Utility and it says 

So what do you people suggest? Should I ask for a replacement? Or should I install Ubuntu-64bit hoping it might solve the problem?
That look like a couple of months old drive, with SMART data reporting it being powered on for 4,6 years... :)

So it seems they gave you used drive as replacement.

(it's of course always also possible that there's a design flaw on the system, causing damage over time. I recently helped a friend with a netbook that had a broken hard drive, and in the end the problem was the structure of the netbook, loud sounds from right speaker causing the hard drive to vibrate, making the disc heads hit the disk surface and creating bad sectors. In the end the manufacturer admitted that they were indeed aware that the model had such problem and replaced the machine with another one. Although that kind of stuff really isn't very common. Luckily. :D)

---

