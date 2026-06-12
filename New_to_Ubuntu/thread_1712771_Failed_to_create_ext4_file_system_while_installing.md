---
title: "Failed to create ext4 file system while installing ubuntu desktop 64 bit version on s"
date: 2011-03-23
forum: New to Ubuntu
---

### Post by kamal_hyd on 2011-03-23
Somebody !! Please Help !! Newbee !

I am trying to install Ubuntu 10.10 on Sony Vaio VGN-CS36GJ

I am doing so from a bootable CD created from ubuntu-10.10-desktop-amd64.iso.
Everything started of well, but the installation is still going on after 3 hours.

Problem : 
I got a message that :
Failed to create ext4 file system : The ext4 file system creation in Partition #1 of SCSI1 (0,0,0) (sda) failed.

Q. What has gone wrong ? Any Idea.

My Laptop Specs are as follows :
Hard Disk : 320 GB (SCSI)
RAM         : 4 GB DDR2
Processor : Intel Core 2 Duo P8700 (2.53 Ghz)

---

### Post by fabricator4 on 2011-03-23
> **kamal_hyd said:**
> 

Q. What has gone wrong ? Any Idea.

It's possible that you got a corrupted download, or that the burn was bad.  Even in the worst case Ubuntu only takes 20-30 minutes to install.

Check the iso you dowloaded by testing its [md5sum]("https://help.ubuntu.com/community/HowToMD5SUM") to make sure it is good.

Next, [Check the CD]("https://help.ubuntu.com/community/Installation/CDIntegrityCheck?action=show&redirect=CDIntegrityCheck") for defects.

If the iso is good but the CD is faulty burn another one but make sure you specify the slowest possible burn speed.  Generally, burning at high speed has a much greater chance of burning a faulty CD.

Lastly, I'd really recommend 10.04 LTS release for the first time Ubuntu user.  10.10 seems to be presenting some problems for people, especially problems with the installer when installing a dual boot machine, and later when you want to use the startup disk creator.  The only thing that would make me change this recommendation is if there's support for newer hardware in 10.10 that you really need.

Chris.

---

### Post by Dutch70 on 2011-03-23
Just to add to the info you've gotten. 

Do Not use the side by side installer with 10.10 if you stick with that version. From what I hear, it can trash your windows install. 
Either use manual partitioning or better still is to prepare your disk first, then install.

---

