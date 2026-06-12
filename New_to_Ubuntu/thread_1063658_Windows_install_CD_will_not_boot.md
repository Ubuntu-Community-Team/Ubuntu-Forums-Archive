---
title: "Windows install CD will not boot"
date: 2009-02-08
forum: New to Ubuntu
---

### Post by Ade_Grub on 2009-02-08
Hi all,

I have a desktop (HP XW8000) running Ubuntu Server 8.10. I decided this morning to install XP over the top. I changed the primary boot device to CD-ROM in the bios and selected CD-ROM in the boot options when presented. However the Windows install CD will not boot. I get a black screen for a couple of seconds and then GRUB starts. Before I know it I'm looking at the terminal asking me to login.

I know it is not an issue with the CD because I tried it in another box that already had XP installed and the PC happily booted from the CD-ROM drive.

Any ideas for how I can boot from the CD?

Thanks

---

### Post by ikisham on 2009-02-08
Did you try to boot with anything else through the CD-ROM?

---

### Post by kestrel1 on 2009-02-08
I think you will find it is because the Windows CD cannot see any partitions on the hard drive that it can use.
Run the Ubuntu Live CD & create an NTFS partition at the beginning of the hard drive using gparted.
You should then be able to boot withe the Windows CD, but be aware that once Windows is installed you will no longer have access to Ubuntu until you re-enable Grub.
Take a look at this to help with that:
[http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/](http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/)

---

### Post by Ade_Grub on 2009-02-08
Thanks for the speedy replies.

I have tried the Ubuntu boot CD and it works so I know it's not that.

I'll have a crack at making an NTFS partition and let you know how I go. Stay tuned.

Thanks guys.

---

### Post by kestrel1 on 2009-02-08
You should just need to free enough space for Windows. I would use a minimum of 20GB for XP, more if you have the room.

---

### Post by Ade_Grub on 2009-02-09
OK I created a 10GB primary NTFS partion at the beginning of the disk with gparted. I booted up and selected boot from the CD-ROM with bios settings. Once again I had black screen for about 3 secs and then GRUB booted and started up Ubuntu again :(

I also had a look around in the bios settings and found a setting that says:

Installed OS: Windows/Linux

I tried both settings when booting from the CD-ROM and still no love. Just to be thorough I also tried booting from CD-ROM with Ubuntu Desktop edition and it worked fine. So it seems like any linux bootable CD will work but just not Windows.

I also have an option in the boot menu to boot from the network. I tried this but received an error saying that the operating system could not be found (Ubuntu was installed at this time).

I'm thinking about flashing the bios with the most recent version and seeing if this makes a difference.

---

### Post by kestrel1 on 2009-02-09
Make sure that the Windows CD is clean. If there are any dirty marks, finger prints etc, this could cause the disk to not boot correctly. Maybe the CD drive is a bit fussy.
I wouldn't flash the BIOS unless you have a real need to. If this goes wrong, your system will be unusable.

---

### Post by Ade_Grub on 2009-02-10
Meh, didn't work anyway. I created a 3 1/2 disc to flash the bios and it wouldn't work because the system refused to boot from the floppy drive!

CD is working fine in a PC with WIndows already installed. That particular system has no worries at all when it comes to booting from CD-ROM with that same Windows boot CD. I'm stumped.

I guess the only thing left is to download a program that will do a low-level format and completely wipe the hard drive. Perhaps then it will boot from CD.

---

### Post by kestrel1 on 2009-02-10
If you have access to another CD-Rom drive, I would put that in the system, just to make sure that the drive already in the system doesn't have some sort of fault. I know you can boot from the Ubuntu live CD, but there could be an abnormality with the drive reading certain disk's.

---

### Post by Ade_Grub on 2009-02-10
I'm up for anything at this stage. I'll give it a try and let you know.

---

### Post by kestrel1 on 2009-02-10
I know what you mean :lolflag:

---

### Post by Ade_Grub on 2009-02-11
OK guys prepare for the height of stupidity.

I took your advice and swapped over the drives. I swapped over what I thought was a DVD-ROM drive for another DVD-ROM drive and BAM straight away it booted from the windows CD. Dumbfounded by this I inspected the two drives more closely. I noticed that the drive that came out of the XW8000 was a CD-ROM drive. I thought this was strange because I have primarily mucked around with the XW8200 which has a DVD-ROM drive. But that was besides the point... right? Wrong!

On closer inspection of what I thought was a windows boot CD I found that it was a windows boot DVD! I had been trying all this time to boot a windows DVD in a CD-ROM drive! And the reason it worked with Ubuntu is because the live CD is indeed a CD.

Thanks for everyone's suggestions and apologies for wasting your time.

Cheers

---

### Post by kestrel1 on 2009-02-11
Not come across a Win XP DVD, so it never even crossed my mind. Mine have always been CD's.
Even if mine was a DVD I shouldn't have a problem as both drives are DVD.
Anyway, at least you managed to get it sorted.

---

