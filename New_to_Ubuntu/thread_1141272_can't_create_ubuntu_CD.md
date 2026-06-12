---
title: "can't create ubuntu CD"
date: 2009-04-28
forum: New to Ubuntu
---

### Post by al.adab on 2009-04-28
hello

I've been trying to burn the downloaded ISO image of Ubuntu 9.04 on a CD
for the past hour. Tried Brasero, GnomeBaker, and the simple right-click + "write to disc" option (as at the Ubuntu website. The CD's brand is Memorex, if that helps. 

None of them works. The CD/DVD drive works otherwise. Brasero gives me an (unknown) error message + an endless log file (which I don't manage to attach here). 

Any idea/suggestions? Thanks!

---

### Post by Tibuda on 2009-04-28
Have you checked the md5 sum?

---

### Post by al.adab on 2009-04-28
sorry I don't know what the "md5 sum" is or where to find it...can you please expand on this?

---

### Post by Tibuda on 2009-04-28
You can use the md5 sum to verify if a file you download is corrupted. What ubuntu version, edition and architeture image have you downloaded? The 9.04 version desktop edition for i386 arch md5 sum is 66fa77789c7b8ff63130e5d5a272d67b

To check your file md5 sum, you can run this in the terminal:```
md5sum filename.iso
```

There's a way to check the sum in Brasero, but I can't remember it.

---

### Post by 3rdalbum on 2009-04-28
I know this sounds like a dumb question... but did you try a different blank CD? In the past I've had a failed burn that's failed enough to make the system think it's still a blank disc, but just good enough to prevent any further burning.

---

### Post by al.adab on 2009-04-28
This cost me about 15 cd roms. I eventually got rid of Brasero, re-booted the machine, and it worked. Must've been some kind of bug, as whatever burning software I'd tried to use didn't work...and gave me a Brasero error message...
Thanks anyway.

---

### Post by NightwishFan on 2009-04-28
Sometimes burner programs can be iffy. For instance, in the Jaunty alphas, k3b would fail to burn my DVDrw disks. I found out I had to set them to use dao, and on auto it was doing something else. Brasero has always worked fine, it would simply just not do a disk write if it couldn't.

---

### Post by logos34 on 2009-04-28
> **al.adab said:**
> This cost me about 15 cd roms. 

Do yourself a favor: get some +/-RW rewritable discs and prevent future waste!

---

### Post by Ralphie on 2009-05-02
I am having this same issue burning an iso in 9.04

```

BraseroGrowisofs Launching command
BraseroGrowisofs called brasero_job_get_fd_out
BraseroGrowisofs stdout: Executing 'builtin_dd if=/home/XXXX/Desktop/MyFile.iso of=/dev/sr0 obs=32k seek=0'
BraseroGrowisofs called brasero_job_set_dangerous
BraseroGrowisofs stderr: /dev/sr0: "Current Write Speed" is 4.1x1352KBps.
BraseroGrowisofs stdout:           0/4617052160 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
BraseroGrowisofs stdout:           0/4617052160 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
BraseroGrowisofs stdout:           0/4617052160 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
BraseroGrowisofs stdout:           0/4617052160 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
BraseroGrowisofs stdout:           0/4617052160 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
BraseroGrowisofs stdout:           0/4617052160 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
BraseroGrowisofs stderr: :-[ WRITE@LBA=0h failed with SK=3h/POWER CALIBRATION AREA ERROR]: Input/output error
BraseroGrowisofs stderr: :-( write failed: Input/output error
BraseroGrowisofs stderr: HUP
BraseroGrowisofs stdout: HUP
BraseroGrowisofs process finished with status 5
BraseroGrowisofs called brasero_job_error
BraseroGrowisofs finished with an error
BraseroGrowisofs asked to stop because of an error
	error		= 0
	message	= "no message"
BraseroGrowisofs stopping
BraseroGrowisofs got killed
Session error : unknown (brasero_burn_record burn.c:2602)

```

This is the relevant error section of the log. 
I have tried multiple disks (different brands even), the md5 matches, so I really don't know what is going on.

I guess I will try to remove brasero, like al.adab and see what happens.

---

### Post by Ralphie on 2009-05-02
No luck. 
Removed Brasero, restarted, installed K3B, heres the error:

```

Executing 'builtin_dd if=/dev/fd/0 of=/dev/sr0 obs=32k seek=0'
/dev/sr0: "Current Write Speed" is 2.5x1352KBps.
          0/4617052160 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
          0/4617052160 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
          0/4617052160 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
          0/4617052160 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
          0/4617052160 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
:-[ WRITE@LBA=0h failed with SK=3h/POWER CALIBRATION AREA ERROR]: Input/output error
:-( write failed: Input/output error

```

"Power calibration area error" hmm
I'll look into it, but does anyone have any ideas?

[COLOR="Red"]*EDIT*[/COLOR]
Well I looked up the error and it seems most people just tried different programs, so I removed K3B, installed Gnomebaker and it did the job.

So for future people with problems burning iso's _or anything_ try different programs and hopefully get lucky on one?

---

### Post by NightwishFan on 2009-05-02
I think you would be better suited perhaps report that as a bug. The use a different program mentality seems like an embarrassment to desktop Linux, and should not be the case for new users.

---

### Post by philinux on 2009-05-02
> **logos34 said:**
> Do yourself a favor: get some +/-RW rewritable discs and prevent future waste!

+1

I now only use cdrw's for burning iso's. These are the cheapest I can get from pcworld or asda. Not had many problems at all.

---

### Post by zeroseven0183 on 2009-05-02
> **logos34 said:**
> Do yourself a favor: get some +/-RW rewritable discs and prevent future waste!

The idea is simple yet profound.

Aside from burning the updated Ubuntu version to RW disks, I'm collecting also free CDs of Ubuntu.

---

### Post by An85Zk9tc8rfjV8i on 2009-09-30
try this :
[Workaround for k3b ISO verify failure]("http://ubuntuforums.org/showpost.php?p=8029528&postcount=29")

---

### Post by genie555m on 2009-12-24
Got the same message. I turned off the option to "burn disk without first writing to disk" and changed my temp folder from /tmp to a folder that I know I have full rights too. /home/genie555m/Desktop/tmp

This worked for me, but your mileage will very. Goodluck - G.

---

