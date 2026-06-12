---
title: "need some HDD diagnostic tools"
date: 2009-03-15
forum: New to Ubuntu
---

### Post by bigmonmulgrew on 2009-03-15
Hi guys
I have had a drive in a raid array come up failed.
Its a mirrored array running windows XP.
The drive is a western digital caviar  WD2500AAJS 250GB SATA
Running on a gigabyte motherboard (not sure of the model but its AM2+)

I want to run some diagnostics on the drive to see if its just corrupt out of bad luck or its a hardware fault. I think its relevant that I have little experience with HDD diagnostic so any tips would be appreciated.

NOW FINALLY to the point.
I have no HDD diagnostic tools for ubuntu, that I'm aware of. I expect there are some included with the OS.
Could some one recommend me some good tools to use. I would like to avoid the command line if possibly but will use it if necessary.

Thanks for your time guys.

---

### Post by kanikilu on 2009-03-15
[The Ultimate Boot CD](http://www.ultimatebootcd.com/) has a lot of useful tools, including a couple hard drive diagnostic tools for Western Digital (which it appears you have).

When in doubt, you can always use the tools provided by your hard drive manufacturer. In your case:

[http://support.wdc.com/product/download.asp?modelno=WD2500AAJS&x=13&y=14](http://support.wdc.com/product/download.asp?modelno=WD2500AAJS&x=13&y=14)

Either of those should tell you if you have a hardware problem.

If you want to check the filesystem, you can use this to force a check on the next reboot: ```
sudo touch /forcefsck
``` This is assuming that the root partition (/) is on the drive you want to check.

// Edit - Just saw that you said this is running XP, is that right :?: I think you can run chkdsk from a recovery console with the XP install disc, but I'm not really sure...

---

### Post by bigmonmulgrew on 2009-03-15
thanks for the tips.
Is there anything I can use under ubuntu.
The WD tools are all windows and dos

---

### Post by gtfourdreams on 2009-03-24
Try this thread. I used these diagnostic tools for SCSI, but maybe it might work for IDE
[ hard drive utilities (from remote ssh)]("http://ubuntuforums.org/showthread.php?t=1051565")

---

### Post by chili555 on 2009-03-24
You might install ```
smartctl
``` through Synaptic. Then do:```
man smartctl
```

---

