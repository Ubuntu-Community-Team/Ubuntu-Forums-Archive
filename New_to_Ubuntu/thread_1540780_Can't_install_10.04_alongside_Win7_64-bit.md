---
title: "Can't install 10.04 alongside Win7 64-bit"
date: 2010-07-28
forum: New to Ubuntu
---

### Post by Echoes1313 on 2010-07-28
(Had this in the installation forum, but no one responded, leading me to think it belongs in the beginner forum).     

Hello Ubuntu community,  

This is my first foray into Ubuntu. I am trying to install 10.04 on my machine that has two hard drives. One is a 250gig with Windows Vista 64-bit. The other is a 1TB with Windows 7 (500gig partition), Windows Vista 32-bit (150gig partition), and ~300gig unallocated space. 

I would like to install Ubuntu 10.04 onto the unallocated space. I burned a DVD with the latest iso from the Ubuntu site. I made sure to verify disc image after burning, and it is successful. When I boot from the disc, I open the installer menu and choose Select Disc for Defects. It says there are 0 errors. Then I chose Install Ubuntu, and I receive an error saying Installation Failed and it will now load into the cd boot mode. No description of the error is given. 

So I go into cd mode, and choose Install Ubuntu 10.04. I go through the screens and select Use Unallocated Space (which is the 300gigs). I go through the rest of the steps and begin installation. 

It fails at 15% and give an error message titled ERROR!!!. The description is: &quot;end of file while reading No such file or directory&quot; 

I have no other Linux experience to even begin to know how to fix this error. If I choose Retry, it simply pops up again. Ignore gives me another error &quot;Invalid argument during seek for read on /dev/sda. Hitting ignore again gives me the same error. Same for the next 3 times. Lastly, it says &quot;No space left on device during write on /dva/sda. Then a red error box comes up saying &quot;The creation of swap space in partition #6 of SCSI1 (0,0,0) (sda) failed.&quot; Another red error pops up titled &quot;Unable to mount floopy disc&quot; with the description: &quot;Error mounting: mount: block device /dev/fd0 is write-protected, mounting read-only mount: /dev/fd0: can't read superblock&quot; 

It appears either files or missing or something is write-protected. But, I have no idea what. I thank you for any advice you can give me, and your patience in helping a wannabe convert.    

Computer specs:  
Asus P5K-VM mobo  
Intel E8500 3.16 Core 2 Duo processor 
 nVidia 9800GTX  
A samsung 1TB hard drive,  
and a 250gig hard drive 4gigs of DDR21000 ram

---

### Post by stoogiebuncho on 2010-07-28
Can't say I've ever encountered this error before, but what happens if you open up GParted and try to format the unallocated space to ext3 or ext4?

---

### Post by Echoes1313 on 2010-07-28
Hmm, I didn't try that. I'll do it when I get home. Will I also have to manually create partitions for the OS?

---

### Post by stoogiebuncho on 2010-07-28
> **Echoes1313 said:**
> Hmm, I didn't try that. I'll do it when I get home. Will I also have to manually create partitions for the OS?

You can if you want to.  I guess you might as well since you'll be in there anyway.  But you could also just format the whole thing and then split it up when you install.

---

### Post by Echoes1313 on 2010-07-28
I tried using GParted to format the empty space as ext 4, and I got an error. It said to look at the detail, which I did:

"/dev/sda: unrecognised-disk label"

Unfortunately, I have no idea what this means or what it is really looking for. Any help would be greatly appreciated!

---

### Post by Mark Phelps on 2010-07-29
To be safe, I would disconnect the drive with Vista on it, boot from the CD with only the other drive connected, startup Ubuntu in the trial mode, open Partition Editor -- and see if it detects the partitions on this other drive.

IF it can't, you would need to download the alternate CD and try using it.  I've had instances where the desktop CD couldn't see the partitions but the alternate CD could.

---

### Post by Echoes1313 on 2010-07-29
O,  I tried what you said, unplugged the first hard drive, booted into cd, and it installed without any errors. Though, there was no confirmation screen or anything. Now, I don't know how to boot into Ubunutu.

I am using EasyBCD on both hard drives (on my Windows OS's) and tried adding a Linux entry, but it hasn't seemed to work. I think I need to install GRUB onto Ubuntu, but will this clash with EasyBCD or the Windows boot loader?

---

### Post by S.R on 2010-07-29
I had to use the alternate install method. [http://www.ubuntu.com/desktop/get-ubuntu/alternative-download](http://www.ubuntu.com/desktop/get-ubuntu/alternative-download)

---

### Post by Echoes1313 on 2010-07-30
Ok, I guess I'll try that but what do I do with the partition that seems to have Ubuntu installed on it now? Wipe it and delete the partition? Also, should I do anything in EasyBCD?

---

### Post by Mark Phelps on 2010-07-30
> **Echoes1313 said:**
> O,  I tried what you said, unplugged the first hard drive, booted into cd, and it installed without any errors. Though, there was no confirmation screen or anything. Now, I don't know how to boot into Ubunutu.
If you had only the one drive connected, installed Ubuntu on it, when you rebooted with only that drive, you should have gone straight into Ubuntu.  Using the new GRUB2, if it detects only one OS on the system (which it would with only the one drive connected), it does not present a menu but instead, boots right into the default GRUB entry.

> I am using EasyBCD on both hard drives (on my Windows OS's) and tried adding a Linux entry, but it hasn't seemed to work. I think I need to install GRUB onto Ubuntu, but will this clash with EasyBCD or the Windows boot loader?

This is not really an EasyBCD forum.  Most folks here will tell you to use GRUB.  If you want details on configuring EasyBCD, you would better going to their forums at NeoSmart Technologies website.

As to using GRUB, it needs to be installed on your boot drive, which in this case, would be the drive on which you installed Ubuntu.  Do NOT install GRUB to the windows drive or you will only have to go through the pain of removing it.

Once you can boot from the Ubuntu drive, reconnect the other drive, continuing to boot from the Ubuntu drive, and run "sudo update-grub" in a terminal.  The will regenerate the GRUB2 menu and should add an entry for MS Windows.  The next time you boot, since you will then have multiple OSs, the GRUB menu will automatically display.

---

