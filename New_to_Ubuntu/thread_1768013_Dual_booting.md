---
title: "Dual booting"
date: 2011-05-26
forum: New to Ubuntu
---

### Post by Gax63 on 2011-05-26
I downloaded and and install wubi so that I could dual boot ubuntu.
I am running Win7 64 bit on and AMD 64 bit processor.
My C drive only has 10 gig available so I chose to install it on my D drive with 107g available.
After following the install instructions I rebooted had a boot selection of Windows and Ubuntu.
When I choose Ubuntu I get the following:
[B]Windows failed to start
[COLOR=black]File: \ubuntu\winboot\wubildr.mbr 
status: 0xc000000e 
Info: The selected entry could not be loaded because the application is missing or corrupt.[/COLOR]

[/B]If I choose windows, windows will boot normally.

Any know what I can do to fix it.
Thanks
Tim

---

### Post by Rubi1200 on 2011-05-26
Hi and welcome to the forums :-)

Please boot into Windows and check if the following files are at the root of the C drive;
wubildr and wubildr.mbr

If they are not, copy them over from the D drive and place them at the root of the C drive then reboot and see if Ubuntu starts.

---

### Post by Gax63 on 2011-05-26
> **Rubi1200 said:**
> Hi and welcome to the forums :-)

Please boot into Windows and check if the following files are at the root of the C drive;
wubildr and wubildr.mbr


If they are not, copy them over from the D drive and place them at the root of the C drive then reboot and see if Ubuntu starts.

Thanks for the fast response!

Just checked and both are in the root of C:

---

### Post by Rubi1200 on 2011-05-26
Okay, next thing to check is this:

In Windows use the following link (Option One) and check if there is an entry for Ubuntu in the boot configuration for System Startup:
[http://www.sevenforums.com/tutorials/2282-default-operating-system-change-default-boot-os.html](http://www.sevenforums.com/tutorials/2282-default-operating-system-change-default-boot-os.html)

---

### Post by Gax63 on 2011-05-26
> **Rubi1200 said:**
> Okay, next thing to check is this:

In Windows use the following link (Option One) and check if there is an entry for Ubuntu in the boot configuration for System Startup:
[http://www.sevenforums.com/tutorials/2282-default-operating-system-change-default-boot-os.html](http://www.sevenforums.com/tutorials/2282-default-operating-system-change-default-boot-os.html)

It is showing in the start up and recovery drop down list, but does not show up in the system configuration: "Boot" Tab os list.

---

### Post by Rubi1200 on 2011-05-26
Gax63,

it doesn't really help us if you start a new thread on the same subject in another sub-forum.

I have sent a message to bcbc, a Wubi expert, about this problem.

Hopefully he will answer soon, so please be patient.

---

### Post by bcbc on 2011-05-26
> **Gax63 said:**
> I downloaded and and install wubi so that I could dual boot ubuntu.
I am running Win7 64 bit on and AMD 64 bit processor.
My C drive only has 10 gig available so I chose to install it on my D drive with 107g available.
After following the install instructions I rebooted had a boot selection of Windows and Ubuntu.
When I choose Ubuntu I get the following:
[B]Windows failed to start
[COLOR=black]File: \ubuntu\winboot\wubildr.mbr 
status: 0xc000000e 
Info: The selected entry could not be loaded because the application is missing or corrupt.[/COLOR]

[/B]If I choose windows, windows will boot normally.

Any know what I can do to fix it.
Thanks
Tim

Windows boot manager is trying to call: D:\ubuntu\winboot\wubildr.mbr

It's unlikely that wubildr.mbr is not there. But you should check.

There is a bug report about incompatibility with a full uefi system. Not sure whether this applies to you: [https://bugs.launchpad.net/wubi/+bug/694242](https://bugs.launchpad.net/wubi/+bug/694242)

---

### Post by Gax63 on 2011-05-31
> **bcbc said:**
> Windows boot manager is trying to call: D:\ubuntu\winboot\wubildr.mbr

It's unlikely that wubildr.mbr is not there. But you should check.

There is a bug report about incompatibility with a full uefi system. Not sure whether this applies to you: [https://bugs.launchpad.net/wubi/+bug/694242](https://bugs.launchpad.net/wubi/+bug/694242)

I have checked again is without a doubt the file wubildr.mbr is in fact in the root of C and in D:\ubuntu\winboot. both are 8k files

I will check out the bug report.

---

### Post by Rubi1200 on 2011-05-31
Can you also please go to the Disk Management utility in Windows and take a screenshot to post here.

Perhaps there is something there that will give us a clue as to what is going on.

Thanks.

---

### Post by bcbc on 2011-05-31
Also you could use diskpart from a CMD prompt (right click and select Run as Administrator):

```
diskpart
list disk
select disk 0
list partition
exit
```

e.g. see attached

---

### Post by Gax63 on 2011-05-31
> **Rubi1200 said:**
> Can you also please go to the Disk Management utility in Windows and take a screenshot to post here.

Perhaps there is something there that will give us a clue as to what is going on.

Thanks.

[IMG]http://farm6.static.flickr.com/5226/5784169022_b17a6caac2_z.jpg[/IMG]

---

### Post by Gax63 on 2011-06-20
So, no other help? :(

---

### Post by Gawains Green Knight on 2011-06-20
I've had success with uninstalling and re-installing wubi when it hasn't worked... never played around with different disks though.

---

### Post by Rubi1200 on 2011-06-20
> **Gax63 said:**
> So, no other help? :(
Can you please supply the information bcbc asked for in the post after mine. He has a lot of knowledge about Wubi installs and I am sure there is a good reason for wanting to see that output.

Thanks.

---

### Post by bcbc on 2011-06-20
Wubi requires bios functions to boot. If you install to a drive that is not visible to the BIOS then it won't work. It's a little strange that drive D: is on disk 0 and drive C: is on disk 2.
How is this drive (hd0) attached?

Anyway the more information you can provide might give a solution. Maybe boot an ubuntu cd and run the [bootinfoscript]("http://bootinfoscript.sourceforge.net/") as well

---

### Post by Gax63 on 2011-06-20
> **Rubi1200 said:**
> Can you please supply the information bcbc asked for in the post after mine. He has a lot of knowledge about Wubi installs and I am sure there is a good reason for wanting to see that output.

Thanks.

  Disk ###  Status         Size     Free     Dyn  Gpt
  --------  -------------  -------  -------  ---  ---
  Disk 0    Online          232 GB      0 B
  Disk 1    Online          232 GB  7168 KB
  Disk 2    Online           74 GB      0 B

Disk 0 is now the selected disk.
  Partition ###  Type              Size     Offset
  -------------  ----------------  -------  -------
* Partition 1    Primary            232 GB      0 B
~~~~~~
Disk 1 is now the selected disk.
  Partition ###  Type              Size     Offset
  -------------  ----------------  -------  -------
  Partition 1    Primary            232 GB    31 KB
~~~~~

Disk 2 is now the selected disk.
  Partition ###  Type              Size     Offset
  -------------  ----------------  -------  -------
  Partition 1    Primary            100 MB  1024 KB
  Partition 2    Primary             74 GB   101 MB

Strange..... Disk 0 (D:- is showing as primary Active and Disk 2/p2 is showing as Boot in windows disk management. And p1 on disk 2 is system reserved
Disk 0 actually has 147 GB free
Disk 1 actually has 124 GB free

I am pretty sure sometime in the past I have used partition magic to move my OS off of the 74 GB (Disk 2) drive.

Much Thanks.:)

---

