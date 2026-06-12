---
title: "Is it possible to have a local Ubuntu mirror automatically fetch missing files..."
date: 2008-04-18
forum: Networking &amp; Wireless
---

### Post by Slavens on 2008-04-18
Hello all, I have a quick but hairy question:

Is it possible to have a local Ubuntu mirror automatically fetch missing files? 

Let me explain the situation.  We have a small network at home which consists of assorted servers, laptops, and a "cluster".  

I just finished getting a PXE boot system running on a Windows computer using tftpd32, EasyPhp2, and a few other misc tools. The local mirror was created by extracting the files from the 7.10 alternate dvd iso file directly to disk, then shared through Apache. It works and is currently loading Ubuntu 7.10 on my IBM TransNote.

Here's the catch: once I finally got the PXE setup up and running and had the install rolling on the TransNote, it would periodically error with a "file not found" but with no elaboration about which file. I tracked the file names down in the Apache error log and discovered that the install was requesting files that were newer versions than those on the 'alternate dvd'.

First, why is the install requesting newer files than the ones located on the dvd?  Second, is there a way to automatically retrieve the needed files from an official mirror and store them in the local mirror without having to copy the entire mirror or retrieve all the files by hand (as I have already done)?  It's fine if the solution is linux based instead of windows, I have several machines with various distros of linux installed, I just haven't had time to 'properly' set up a PXE boot environment.

This all came about because I wanted to load Linux on the TransNote, which has no built in optical or floppy drives, and it does not support booting USB.  The only external drives it can boot from (that I own) are a proprietary IBM external Multibay and a USB floppy.  the catch is that once either one is past the initail load of initrd, loading fails on the need for special drivers for the external drives. Also, the cluster I mentioned is a wooden case housing five athlon/PIII motherboards mounted on backplanes.  Each has a harddrive with a complete installation of Gentoo linux. If I can get a PXE environment running and set them up diskless, I can save on a lot of noise and heat in the cluster.

Thanks,
Slavens

---

### Post by jeffus_il on 2008-04-18
Is this what you want?
[http://popey.com/Creating_an_Ubuntu_repository_mirror_with_apt-mirror](http://popey.com/Creating_an_Ubuntu_repository_mirror_with_apt-mirror)

To automate it, you just cron (batch) the command.

---

### Post by Slavens on 2008-04-18
I'd rather it fetched the files as soon as it discovers it doesn't have them locally as opposed to waiting on a cron job.  I've got soem programming skills, just nothing approaching what I would need to create an app to do it for me.  

Ideally, what I'm looking for is something to monitor the apache error log for 'file not found' errors and immediately ftp them from an official server to the local mirror.  Of course, this isn't what it *has* to do, it's just the first method that came to mind.

I'm reading through the stuff in the link you posted to see if it will do what I'd like, or something acceptably close.  

Thanks!

---

### Post by odin1965 on 2008-04-18
The problem with fetching only 'missing' files is that you may have all the files but they may be out of date. You need to keep your local repository synced to the main ones to get program updates. For that you need something like debmirror. see the first part of this tutorial, [http://ubuntuforums.org/showthread.php?t=352460&highlight=debmirror](http://ubuntuforums.org/showthread.php?t=352460&highlight=debmirror).

then you can run a cron job every night or how ever often you want to keep you repo up to date. Or you can just run debmirror manually to update.

---

### Post by greentree-sa on 2008-06-13
Hi Slavens, Please help if you can.

You say you extracted your DVD iso to disk to create a local mirror yes?

I have al 6 repo dvd/cd from hardy 8.04. How would I extract this, considering the package.gz etc, file on each dvd...?
Thanks in advance!
Christiaan

---

