---
title: "Have I destroyed my computer?"
date: 2010-01-07
forum: New to Ubuntu
---

### Post by marcusesses on 2010-01-07
Last night before I went to bed, my laptop worked just fine. I se my alarm (which is on my laptop), as usual. I slept through it a bit and when I woke up, when I tried to unlock the screen , I was met with a black screen. I restarted the computer (using the power button).

When restarting, it gets through BIOS, and gets to the screen with the sma Ubuntu logo with a black background. I then get a black screen of death, with nothing happening.

When I restart i'm recovery mode, I receive a number of errors that look like

```
ata1.00:  status :{DRDY ERR}
ata1.00: error: {UNC} 
```

I then get errors like ...
```
mount: mounting /sys on /root/sys failed: No such file or directory
```

I get this for sys,dev, and process. Then
```
Target filesystem doesn't have /sbin/initial.
No initial found.Try passing init = bootarg
```

When I ls in the terminal (whose prompt says initramfs) ,the only directories I see are 

dev root scripts conf lib etc initial bin use sbin sys proc tmp var.

So what the heck is going on?

Sorry if this is sloppy, I had to write it using a handheld device.

---

### Post by bodhi.zazen on 2010-01-07
Boot a live CD and run fsck on your Ubuntu partition.

---

### Post by marcusesses on 2010-01-07
I (potentially?) solved the problem. 

After leaving it alone for 2 hours, I started the laptop up and Ubuntu booted up without problems.

So why did it muck up? What would the previous suggestion (I.e. run liveboot and run fsck) do to fix it?

---

### Post by llawwehttam on 2010-01-07
I have seen similar things happen when computers overheat. Sometimes when a computer overheats the BIOS disables bits of it untill its cooled down.

Could this be the answer?

FSCK wound have fixed file system errors ( a bit like chkdsk in windows) but if it booted later this is unlikely to have been the problem.

---

### Post by achase79 on 2010-01-07
I have this problem with my daughter's computer.  All I have to do to fix this is try to mount the hard drive (even if it fails) then restart.  Something gets weird with the ext3 journal and somehow this fixes it for me.

---

### Post by skatinjj on 2010-01-07
> **marcusesses said:**
> I (potentially?) solved the problem. 

After leaving it alone for 2 hours, I started the laptop up and Ubuntu booted up without problems.

So why did it muck up? What would the previous suggestion (I.e. run liveboot and run fsck) do to fix it?

fsck checks your file system and attempts to fix errors that are detected.

---

