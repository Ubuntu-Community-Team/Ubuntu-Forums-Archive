---
title: "No cd/dvd driver detected"
date: 2010-10-02
forum: New to Ubuntu
---

### Post by llamaboy on 2010-10-02
I am trying to get my lightscribe cd/dvd burner driver installed on my laptop. I just switched over from Windows and don't know how to get it working. I have a hp dv2815nr with a lightscribe cd/dvd reader/burner. 
I visited the following website:
[http://principialabs.com/lightscribe-on-ubuntu/](http://principialabs.com/lightscribe-on-ubuntu/)
and did according to the instructions exactly, but that doesn't seem to have helped.
When I put a cd or dvd in it acts like it's reading it, making sounds and flashing the light, but I don't see it showing up anywhere on my computer. Please help.

---

### Post by Hippytaff on 2010-10-02
does

```

ls /dev/sr0

```
return anything (maybe try with a disc in)

---

### Post by llamaboy on 2010-10-02
all it comes up with is a dark highlighted: /dev/sr0
tried it with a disc in as well and same thing.

---

### Post by llamaboy on 2010-10-02
I just checked, my hardware is detected somehow, but nothing is responding. If I go to System/Administration/disk utility, it shows up. 
Here's the info that shows up for it:

Model- HL-DT-ST DVDRAM GSA-T20L
Firmware Version- NC08
Location- Port 1  of PATA Host Adapter
Write Cache- -
Capacity- No Media Detected
Partitioning- -
Serial Number- -
World Wide Name- -
Device- /dev/sr-
Rotation Rate- -
Connection- SCSI
SMART Status- Not Supported


And if I try ejecting my cd through the computer it says:

Error ejecting medium:
An error occured while performing an operation on "CD/DVD Drive" (HL-DT-ST DVDRAM GSA-T20L). The operation failed."
It won't detect any media.

---

### Post by andrewthomas on 2010-10-02
post the output of ```
 cat /etc/fstab
```

---

### Post by ankspo71 on 2010-10-02
Hi,
If you are using Ubuntu 10.04, there are a small number of us that have problems mounting cds in our optical drives. I had this trouble too. It is a bug for some of us that makes ubuntu have trouble reading the optical drive entries in the BIOS. A user here suggested a workaround and it was to boot into the BIOS, and tell your BIOS to re-detect your cd and dvd burners. This might be effecting you too so it might be worth a try.

On my computer it is as follows: (Phoenix Award BIOS)

Restart the computer.

At the bottom of my computer's initial boot screen there is a message to "Press Del to enter Setup". The setup is the BIOS, so I press the Delete key to enter it. It then boots into the BIOS.

Next I go into the "Standard CMOS Features". Here you should see all of your hard drives and CD drives.

I look for my optical DVD Burner and select it.

Next I Select "IDE HDD Auto Detection". It asks me if I am sure and I say yes. It then re-detects my drive.

Then I press F10 to save and Exit. After confirming yes, the BIOS saves and the computer automatically reboots, and then I have a working DVD Burner in Ubuntu/Kubuntu 10.04.

---

### Post by llamaboy on 2010-10-03
I will try the BIOS in a little bit. Here is what I got for inputting cat /etc/fstab


~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=33df9076-ddb6-4ca8-905c-4d365da84d17 none            swap    sw              0       0

---

### Post by llamaboy on 2010-10-03
ok, perhaps it's because i don't know what i'm doing, but i looked into my bios and didn't really see anything relating to my cd/dvd drive like you suggested that i could change. i'm at  a loss now. i am waiting to move up to 10.10 and hoping that will help take care of it, at least a little bit.

---

