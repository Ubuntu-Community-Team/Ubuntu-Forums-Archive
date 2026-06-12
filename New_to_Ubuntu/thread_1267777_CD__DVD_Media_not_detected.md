---
title: "CD / DVD Media not detected"
date: 2009-09-16
forum: New to Ubuntu
---

### Post by expatCM on 2009-09-16
I am finding that CD-R and DVD-R media is no longer detected.  Not sure how long this has been but it may have been since I upgraded to 9.04.

The drive is detected in both BIOS and lshw.  It used to work. It is just that the physical media is not detected.

This is what I have done to test ...

swapped out the drive with another.  New drive out of the box. Same result.

swapped the SATA cable.

tested with both K3B and Brasero.

swapped out power supply.


As a result I get the idea that this is probably something specific to Ubuntu rather than the applications or hardware.

The extract from lshw showing the present installed drive is as follows

 ```
 *-cdrom
             description: DVD-RAM writer
             product: iHAS324   A
             vendor: ATAPI
             physical id: 1
             bus info: scsi@3:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/scd0
             logical name: /dev/sr0
             version: BL1D
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
```

Any ideas?

---

### Post by nhasian on 2009-09-16
if you put a regular factory pressed cd in the drive, is it accessable?  also can you boot off a liveCD?

---

### Post by expatCM on 2009-09-16
Good questions .....

No the system will not boot from the live CD.  I did check the boot order and as the system loads I can see the CD listed and then it immediately moves to grub.  Bit of a puzzle there since I installed from the CD.

No a factory pressed CD is not detected.

---

### Post by nhasian on 2009-09-17
wow that is perplexing.  i would say you have a bad cd-rom drive, but you said you swapped it and also the sata cable.  can you try a different sata channel on your motherboard?  my next steps would be to see if there is a newer bios for your motherboard that may resolve the issue, or try a new motherboard.

---

### Post by expatCM on 2009-09-19
I find it hard to believe that there are two bad drives.  I thought the first one was bad and took it out.  I replaced with a new drive from another manufacturer.  They cannot both be bad .....  I hope....

I have just swapped the SATA channel but the same thing happens.

This link sadly sounds very similar in some respects but the kernel version is no where close
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/397906](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/397906)

---

### Post by seshomaru samma on 2009-09-19
can you boot from usb and see if something like puppy linux sees your cd?

---

### Post by nhasian on 2009-09-20
if your cdrom is unable to read media, and your unable to boot from a cd-rom, i dont think its a linux issue at all.  its definitely a hardware issue.  I dont know how old your motherboard is, but now might be a good time to upgrade to a new Intel i5/i7 Core system :)

---

### Post by expatCM on 2009-09-20
nhasian, you make an interesting observation.

The BIOS boot order is 1. CD 2. HDD 3. Disabled.  I just modified this to  1.CD. 2. Disabled 3. Disabled.  Then put in the Ubuntu CD and power cycle.

What happened is that the boot paused briefly at the CD and then skipped and loaded from the (disabled) HDD.

To me that was a bit strange and said either the BIOS settings are partially corrupted or there is a hardware problem with the motherboard.  The motherboard is only 1 - 2 years old but I know it is possible that it is on the way out.  The BIOS does report the CD drive properly though so I really do wonder .......

I think the next step must be to remove the CMOS battery and then see what happens when the default settings are reloaded.

---

### Post by Cresho on 2009-09-20
I ran into this problem.  I use to use emprex dvd burner to burn all my videos such as weddings, partyies, they no longer work on the pioneer one.  THis was all in windows xp.  I tried using linux but it doesnt work.  In my case, the burn from the emprex burner is specific to its design and technology and probably the same goes for yours.

When I stick the emprex back into my system, my dvd's are fine.  I can read them.

---

