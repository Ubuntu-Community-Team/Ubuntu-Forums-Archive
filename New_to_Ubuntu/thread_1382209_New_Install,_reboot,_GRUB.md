---
title: "New Install, reboot, GRUB"
date: 2010-01-15
forum: New to Ubuntu
---

### Post by Pelgar on 2010-01-15
I am brand new to Ubuntu, Linux and this forum. I just installed Ubuntu from the Live CD to a 40 gig Segate HD. I chose to install using the entire HD, no dual-boot. The computer is an older system, Intel Celeron, 1.8 GHZ. with 512 MB memory. The install seemed to have gone well but when the system boots all I see is a black screen with the word GRUB and a flashing cursor. Is this what I'm supposed to see? If so what do I do now, it will not take KB input? 
I've searched enough to learn that GRUB is the boot loader but I cannot seem to find out what to do with it. The installation guide says I should see a menu on reboot!

Thanks for any help you can give me.

---

### Post by minsf on 2010-01-15
does it really not take any keyboard input?
do you see a grub prompt like "grub>" or something else?

---

### Post by k64 on 2010-01-15
The problem may be a 1024-cylinder breach, and the only thing you can do is reinstall Linux.

Another possibility: The hard drive which Linux is installed on MUST be formatted in Ext3, or it won't work.

---

### Post by Pelgar on 2010-01-15
No it does not take KB input and it is not really a prompt. Just the word GRUB (all caps), a space and a flashing _ i.e. GRUB _
The KB is not locked, I can toggle caps, num locks, scroll lock but no other key does anything. If I reboot I just get the same thing again.

The hard drive did have Fedora installed on it. I decided to give Ubuntu another try after I could not get networking to work with Fedora. I don't know if the previous install of Fedora makes a difference but thought I'd mention it. The hard drive originally had Win XP installed. The use entire hard drive option was used with both the Fedora and Ubuntu installs.

Thanks

---

### Post by Pelgar on 2010-01-15
Hi Kenny, Hopefully you have me started in the right direction. I noted the following from the install:

The partition tables of the following devices are changed:
SCSI1 (0,0,0)(sda)

The following partitions are going to be formated:
partition #1 of SCSI1(0,0,0)(sda) as ext4
partition #5 of SCSI1(0,0,0)(sda) as swap


I guess I need to reinstall using the manual format option?

Thanks

Dale

---

### Post by warfacegod on 2010-01-15
I'm thinking failing hard drive.

---

### Post by Pelgar on 2010-01-16
Thanks for your help. I reinstalled and chose the manual format to Ext3. The install went well but still same problem at boot.
I am a bit confused, nothing new there, with the original Segate drive I could start up with the Live CD then boot to first HD and it loaded fine. If there was a boot sector problem with the HD would it do that?


I'm using an old Maxtor 20 gig HD now. This one still had Win2k on it and it would boot into it. Hopefully it will work out this time.

---

### Post by Pelgar on 2010-01-16
Flashing the bios fixed this problem. This is an old Asus P4B MB. If anyone else has a similar problem with an Asus board you can get the flash program and bios update here:

[http://support.asus.com/download/download.aspx?SLanguage=en-us](http://support.asus.com/download/download.aspx?SLanguage=en-us)


I'll see what other trouble I can get into now!

Thanks for your help,

Dale

---

