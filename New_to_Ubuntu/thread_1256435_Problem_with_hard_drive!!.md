---
title: "Problem with hard drive!?!"
date: 2009-09-02
forum: New to Ubuntu
---

### Post by fjordanrr on 2009-09-02
I'm an newbie to Ubuntu 9.04 and I have a problem!?!:confused:
 

 First my machine (my older machine, that is)  
 

 Pentium III running @ 733 MHz (ancient)
 Tyan Trinity 400 (S1854) motherboard (ditto)
 1.5 GB memory
 Nvidia GeForce FX-5200 video
 CD_ROM drive
 80 GB HD (where the Ubuntu presently resides)
 500 GB HD on a PCI to PATA interface card (SYBA Ultra-ATA SIL-680)
 

 ----------------  
 

 I first tried to install Ubuntu on the 500 GB drive in the IDE slot of the motherboard, but then I found out since the BIOS was dated 2000 (as I said ancient) it would support HDs only up to 137 GB.  So I put the 80 GB back in the machine that was in the machine originally and did the install again.  I purchased the PCI to ATA card to use for the 500 GB drive and tried to install Ubuntu a third time, this time on the 500 GB HD.  When I rebooted after the install I kept getting ERROR 2 which from what I've been able to read means that the GRUB loader expected one boot location, but found another which it could not use (right – wrong).  After several tries to rectify this, I put the 80 GB drive back, installed Ubuntu a fourth time.  Ubuntu boots ok to the desktop(Gnome) with the 80 GB drive at the boot disk, but I still have problems with the 500 GB drive.  
 

 Ubuntu sees the 500 GB drive, but only as a mountable(?!?) drive, but I cannot use it even after it's been mounted.  I cannot get permission to use it at all.  I've determined that the owner is /root so I cannot change any of the permissions.
 

 My question are as follows:
 

 1 – what could I do (or what could I have done) to avoid the ERROR 2 when booting from the 500 GB drive.  I would like to have it as the 'primary' if possible.
 

 2 – if I can't make the 500 GB drive the primary, how can I wrest the ownership of the drive from /root to my 'account' so I can change the permissions to access the drive
 

 ------------------------  
 

 My only other option to purchase a newer motherboard with a PATA slot that will accommodate the 500 GB drive, but I live on Social Security Disability and would like to avoid that if possible.
 

 

 What I've seen of Ubuntu so far I like and I want and need to learn more about it, so any help would be appreciated!!:razz:

---

### Post by zephyrcat on 2009-09-02
I have no idea about your first question, but you can change the owner of files/folders using the chown command.

1) Mount the drive

2) Open terminal (Applications -> Accessories -> Terminal)

3) Navigate to the 500GB drive (probably something like cd /dev/sdb but you should make sure you have the correct drive by typing ls to list the files)

4) Type this command in (then press enter):

sudo chown -r *username* .

Replace username with your username.

That should work. Always be sure you are working with the correct files.

---

### Post by Whiffle on 2009-09-02
I think you're running into a bios issue for the first question, and I really don't know how to solve it.  What I would do is install grub to the MBR of your 80GB drive, and put ubuntu on the 500 GB drive.  Then, setup grub to point to Ubuntu on the 500 GB.  That should make it boot nice and smoothly (its what I'm doing on another computeR I have).

For the second question, how is the 500gb hard drive formatted?

---

### Post by fjordanrr on 2009-09-08
First, I was off the air for a bit.  I somehow screwed up the networking on my installation of Ubuntu and could not determine how to restore it, so I decided to re-install the OS and in doing so , I've somewhat solved the problem I was having with the 500 GB drive.

I re-installed the OS and it first 'went' to the 500 GB drive, I then forced it a re-install on the 80 GB drive where it had been originally.  So when I rebooted the system, a menu appeared that had not been there before asking which version of Ubuntu did I wish to boot from and one of the version was the one on the 500 GB drive!?!! So I used that option - 'problem'' solved!?!?!

That's the way I usually solve my problems sometimes by blundering around until the situation corrects itself!!   :confused:


Thanks for the help, people!! :razz:

Frank Jordan

---

