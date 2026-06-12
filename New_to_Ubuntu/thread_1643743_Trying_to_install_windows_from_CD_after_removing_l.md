---
title: "Trying to install windows from CD after removing linux"
date: 2010-12-12
forum: New to Ubuntu
---

### Post by nickl1234 on 2010-12-12
I deleted all partitions, combined into free space and then formatted into NTFS. When trying to install windows xp x64 from a CD, a long error "stop" message tells me to make sure that there are no viruses, "run chkdsk /f" and a message such as error code/stop code 00000000x...
There are four codes.

---

### Post by amjjawad on 2010-12-12
> **nickl1234 said:**
> I deleted all partitions, combined into free space and then formatted into NTFS. When trying to install windows xp x64 from a CD, a long error "stop" message tells me to make sure that there are no viruses, "run chkdsk /f" and a message such as error code/stop code 00000000x...
There are four codes.

That's exactly why I don't want to go back to Windows :)

Hmmm, did you try to format and re-partition using Windows CD or GParted?

---

### Post by nickl1234 on 2010-12-12
> **amjjawad said:**
> That's exactly why I don't want to go back to Windows :)
 
Hmmm, did you try to format and re-partition using Windows CD or GParted?
 
I used GParted to format the hard drive to NTFS, using ubuntu CD to boot off of. I then removed the Ubuntu CD and put windows xp64 in, restarted off of internal cd/rom and got the stop message. HALLLLP

---

### Post by amjjawad on 2010-12-12
> **nickl1234 said:**
> I used GParted to format the hard drive to NTFS, using ubuntu CD to boot off of. I then removed the Ubuntu CD and put windows xp64 in, restarted off of internal cd/rom and got the stop message. HALLLLP

Can you re-format it using Windows CD or you can't get to that step? I mean you get that error once you boot from the CD or at what step exactly?

---

### Post by nickl1234 on 2010-12-12
> **amjjawad said:**
> Can you re-format it using Windows CD or you can't get to that step? I mean you get that error once you boot from the CD or at what step exactly?
 
I get the error before I even get to the formatting step. After the CD loads all of its "Setup is loading___" the stop message shows up.

---

### Post by amjjawad on 2010-12-12
> **nickl1234 said:**
> I get the error before I even get to the formatting step. After the CD loads all of its "Setup is loading___" the stop message shows up.

Don't get me wrong but are you trying to get rid of Ubuntu permanently? I don't think it's a Linux issue.
However, try another CD if you have one or try to re-format with GParted but I doubt it could fix it. The message that you get from Windows CD not from Linux so Linux/Ubuntu has nothing to do with it.

---

### Post by HermanAB on 2010-12-12
Howdy,

One solution is to overwrite the first chunk of the disk with zeroes.  Windoze will then think that the disk is new and unformatted and will then proceed to install:
$ sudo dd if=/dev/zero of=/dev/sda bs=1000 count=10000

---

### Post by amjjawad on 2010-12-12
> **HermanAB said:**
> Howdy,

One solution is to overwrite the first chunk of the disk with zeroes.  Windoze will then think that the disk is new and unformatted and will then proceed to install:
$ sudo dd if=/dev/zero of=/dev/sda bs=1000 count=10000

Last time I posted the same command, one of the moderator asked me NOT to suggested even though it solved my problem once.

Anyway, never mind.

---

### Post by nickl1234 on 2010-12-12
> **HermanAB said:**
> Howdy,
 
One solution is to overwrite the first chunk of the disk with zeroes. Windoze will then think that the disk is new and unformatted and will then proceed to install:
$ sudo dd if=/dev/zero of=/dev/sda bs=1000 count=10000
 Is that in Terminal? 
and word for word, "$ sudo dd if=/dev/zero of =/dev/sda bs=1000 count=10000"?

---

### Post by nickl1234 on 2010-12-12
> **HermanAB said:**
> Howdy,
 
One solution is to overwrite the first chunk of the disk with zeroes. Windoze will then think that the disk is new and unformatted and will then proceed to install:
$ sudo dd if=/dev/zero of=/dev/sda bs=1000 count=10000
 Hey, I ran the command and still got the stop message. Would this help any?
 
Technical information: *** STOP: 0x0000007B (and in parentheses behind that, 4 strings of 0xFFFFFADF or FFFC with many more zeroes.)

---

### Post by coffeecat on 2010-12-12
> **nickl1234 said:**
> Is that in Terminal? 
and word for word, "$ sudo dd if=/dev/zero of =/dev/sda bs=1000 count=10000"?

Leave out the '$' - that's the terminal prompt.

If that doesn't work for you, using Gparted from the live CD - go to Device > Create Partition Table. Then create a NTFS partition in the unallocated space. There may be a partition table issue that's confusing the XP installer. HermanAB's suggestion is to zero out the partition table so that the Windows installer creates a new one. Using Gparted to recreate the partition table might also work.

But there's one other thing to check. Is your drive one of these new 'advanced format' ones? XP has problems with them, but there are workarounds.

> **amjjawad said:**
> Last time I posted the same command, one of the moderator asked me NOT to suggested even though it solved my problem once.

I would hope that was a misunderstanding. The staff are, quite rightly, on the lookout for destructive commands posted maliciously. This happens occasionally. Zeroing out the partition table is certainly destructive but it is a valid thing to do on occasion. I had a completely different need from the OP for zeroing the partition table.

---

### Post by coffeecat on 2010-12-12
> **nickl1234 said:**
> Hey, I ran the command and still got the stop message. Would this help any?
 
Technical information: *** STOP: 0x0000007B (and in parentheses behind that, 4 strings of 0xFFFFFADF or FFFC with many more zeroes.)

@nickl1234, is this a Microsoft install CD, an OEM manufacturer's restore CD or some other source of Windows CD?

---

### Post by amjjawad on 2010-12-12
> **coffeecat said:**
> I would hope that was a misunderstanding. The staff are, quite rightly, on the lookout for destructive commands posted maliciously. This happens occasionally. Zeroing out the partition table is certainly destructive but it is a valid thing to do on occasion. **I had a completely different need from the OP for zeroing the partition table.**

The command I suggested was a bit different and for another issue, not similar to this one. It was on another thread. I suggested it because the OP of that thread and from what he wrote, his issue looked so much like mine I had with an antique laptop. After a month of trying, zeroing the whole HDD was the only way to fix everything. Anyway, that's totally different and I don't want to go off topic :)

I'm trying to use to it. I mean when someone disagree with you and ask you NOT to do something. Anyway, I'm still new and still learning so will choose to be silent but that won't last for too long :D

---

### Post by nickl1234 on 2010-12-12
> **coffeecat said:**
> @nickl1234, is this a Microsoft install CD, an OEM manufacturer's restore CD or some other source of Windows CD?
 Its a genuine install CD-xp x64 professional

---

### Post by JustinR on 2010-12-12
Hi, Windows XP doesn't include drivers for SATA Hard Disk Controllers, in your BIOS you will have to change the Hard Disk Controller from 'AHCI' (SATA), to IDE and install Windows XP that way. After that, you can install the drivers for it and change your hard disk controller back to SATA. Thats what the STOP error means.

---

### Post by nickl1234 on 2010-12-12
> **JustinR said:**
> Hi, Windows XP doesn't include drivers for SATA Hard Disk Controllers, in your BIOS you will have to change the Hard Disk Controller from 'AHCI' (SATA), to IDE and install Windows XP that way. After that, you can install the drivers for it and change your hard disk controller back to SATA. Thats what the STOP error means.
 
How do I get to that screen? The top of the BIOS is "Insyde H20 setup utility" if that helps any.

---

### Post by JustinR on 2010-12-12
Hi,

When your computer turns on and flashes your OEM name and logo (eg. HP/Dell/Acer), in one of the four corners of the screen should be keys that tell you 'BIOS'/'Setup', etc.

But if you can't find that, it could also be under 'Boot Up Menu'/'One Time  Boot Menu' > and then BIOS Setup.

----

Actually, sorry If I misread your post - it looks like you already made it to the BIOS screen?

If so, just cycle through the tabs until you find similar wording to Hard Disk Controller.

Edit: If you do reach the BIOS, it could also be under 'SATA Operation'

---

### Post by amjjawad on 2010-12-12
[http://support.microsoft.com/kb/324103](http://support.microsoft.com/kb/324103)


Use Google to find more if the above link doesn't help.

---

