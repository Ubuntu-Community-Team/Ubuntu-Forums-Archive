---
title: "Ubuntu 10.10 boot loader installed in wrong partition. Help!"
date: 2010-11-02
forum: New to Ubuntu
---

### Post by Boblicol on 2010-11-02
Hi all,

I have Windows 7 installed and I'm trying to install Ubuntu 10.10 to dual-boot only i think i've installed the boot loader in the wrong partition as I have no option to boot Ubuntu.                    

RESULTS.txt should be attached.

from what is on the forums just now this may work:

sudo grub-install --recheck /dev/sda


although this returns:

/usr/sbin/grub-probe: error: cannot find a device for /boot/grub (is /dev mounted?).

All wisdom welcome!

Cheers.

Rob

---

### Post by oldfred on 2010-11-02
You have to tell the grub installer which partition to use, in your case sda6

Install MBR from LiveCD, Ubuntu install on sda6 and want grub2 in drive sda's MBR:
Find linux partition, change sda6 if not correct, and/or even sda if sdb wanted:
sudo fdisk -l
sudo mount /dev/sda6 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sda

It looks like you installed to sda1 not sda. Not sure if it will cause any issues with the utility partition. It would cause issues if it was an NTFS partition.

---

### Post by Boblicol on 2010-11-02
Oldfred! thank you. Problem solved.

---

### Post by anawim on 2010-11-02
I believe I have a similar problem. I installed Ubuntu 10.10 in a dual-boot configuration and I think I followed the instructions in the documentation correctly, but when I choose to try to boot Windows Vista, it takes me to the recovery partition. I'm not a programmer - just a guitar player who seems to have wandered above his pay grade. I don't even know how to output the boot_info_script055, so if someone could walk me through these steps, I'd greatly appreciate it. I'm using an eMachines D620 laptop with an AMD Athlon 2650e, 4MB RAM. Thanks in advance.

---

### Post by Quackers on 2010-11-02
anawim, welcome to UF.
Do you have an option in the grub menu which says Windows Recovery (loader). If you do try booting that. It may well boot your Windows installation. Sometimes grub labels them wrongly (usually Vista, it seems).

---

### Post by anawim on 2010-11-02
That did it, Quackers. That's awesome. Now, when I booted Vista (besides remembering why I was looking for an alternative), there was an error message that Rundll32 was not loading and the Windows host was shutting down. I hit the "close program" button, and so far everything is cool. Is this something I should be worried about?

And thanks for the superfast response.

---

### Post by Quackers on 2010-11-03
Glad about the first bit! Not so happy about the last bit though. I'm afraid that's a Windows problem. It's a looooooooong time since I had a Rundll32 error. Perhaps a look at a Windows forum would be a better idea, or try Googling, you'll get a million hits!

---

### Post by Clever_Username on 2010-11-03
I really just wanted to say that this thread is a prime example of one of the reasons why Ubuntu has become so popular. A new guy can come on this forum and ask questions, and get real help from nice people who really know what they're talking about.

---

### Post by Quackers on 2010-11-03
> **Clever_Username said:**
> I really just wanted to say that this thread is a prime example of one of the reasons why Ubuntu has become so popular. A new guy can come on this forum and ask questions, and get real help from nice people who really know what they're talking about.

It's very nice of you to say that. There are many good people on this forum with lots of knowledge. I know, because I've asked most of them for help! :-)

---

### Post by anawim on 2010-11-03
Quackers - I googled it, and it seems to be a shared driver from way back in the NT days; so far no ill effects, and I just need it to hold out long enough to make sure all of my stuff transferred. Thanks again for the help.

Clever - You absolutely read my mind. I'm an Ubuntu convert now, and a lot of it has to do with just browsing the forums and seeing the awesome folks that give advice. You guys are awesome.

---

### Post by Ignrnt on 2012-01-01
Hi all,

I believe I have a similar problem, but could not solve it in the way discussed above.
I'm really a rookie in most things unix. Here's my situation:

Bought  a new laptop: Sony Vaio VPCSA with 4x 64 GB SSDs as one hardware RAID 0  and a pre-installed recovery version of Windows 7 Pro. I'd like to dual boot Windows 7 with Ubuntu 11.10. I think my  problem may have to do with the RAID.
My drive was partitioned into  these partitions: 14 GB Windows recovery, 100 MB Win System, 224 GB  boot. I resized the latter to 104 GB using Windows' own fdisk tool.

Then,  using the ubuntu 11.10 live CD, I created an extended partition in the  last 128 GB with GParted which splits into (1) swap, (2) 16 GB root, and  (3) 100 GB home.
Then I installed ubuntu 11.10 (I only got the  options to either install it instead of Windows or "do something else",  which I did) with these 3 latter partitions as the swap, / and /home.

When  I boot, I drop to the BusyBox. I assumed that maybe the boot loader may  be installed at the wrong place, so I tried to install it as indicated  in this thread. What confuses me a bit is the naming of my partitions.  When I look in fdisk, they are called:

/dev/mapper/isw_cjgadbeaia_Volume0 (the volume)
/dev/mapper/isw_cjgadbeaia_Volume0p1 to Volume0p3 (the primary partitions for Win)
/dev/mapper/isw_cjgadbeaia_Volume0p4 (extended partition)
/dev/mapper/isw_cjgadbeaia_Volume0p5, 6 and 7 (swap, root and home, resp.)

However,  when I look in the disk utility from the live CD, they are all called  /dev/dm-0 (volume) and /dev/dm-1 to dm-6 (the various partitions).  Remember that this is a RAID 0; the physical drives are still called  /dev/sda to sdd.
I can read the partition table using both:
sudo fdisk -l /dev/mapper/isw_cjgadbeaia_Volume0
or
sudo fdisk -l /dev/dm-0
and I get the corresponding entries, same sizes and all, but different names.

I then wanted to fix the boot loader like this:
sudo mount /dev/mapper/isw_cjgadbeaia_Volume0p5 /mnt # where 0p5 should be my root.
sudo grub-install --root-directory=/mnt/ /dev/mapper/isw_cjgadbeaia_Volume0
That proceeded without errors. However, so it did when using the alternative /dev/dm-# designations.

And still, re-booting lands me in the BusyBox. Any hints are appreciated, especially if they are in a "for-dummies" style...

Cheers,
Ignrnt

---

### Post by Quackers on 2012-01-02
Raid can be quite involved. 
However, if your Ubuntu root partition is 
/dev/mapper/isw_cjgadbeaia_Volume0p6, as you seem to indicate that it is, then your first line is wrong.
Try these from the live cd desktop terminal ```
sudo mount /dev/mapper/isw_cjgadbeaia_Volume0p6 /mnt
sudo grub-install --boot-directory=/mnt /dev/mapper/isw_cjgadbeaia_Volume0
```
Note the change in the second line too ie "--boot-directory" rather than "--root-directory". Ubuntu 11-10 can sometimes insist on this, though the original should normally be expected to work.

---

