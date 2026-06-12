---
title: "NTLDR is missing"
date: 2009-08-07
forum: New to Ubuntu
---

### Post by P235 on 2009-08-07
Hello again,

To sum up my problem, I think I messed up my MBR for my laptop.  When I first installed 8.0.4.1, I followed a set of procedures for a dual boot with Vista first and Linux second:

[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm)

My success then led me to try the same set of instructions again after my very recent upgrade to 9.04.  However, my problems began at page 4 as I wanted to keep Vista in charge of things through EasyBCD.  For whatever reason, the Linux boot options I saved over to my Vista partition did not work, essentially locking me out of my Ubuntu partition.  I am guessing that my menu.list file did not have the accurate Linux boot options listed inside.  I continued to tinker with EasyBCD until I received the NTLDR is missing, hit ctrl-alt-del to restart.  

This was probably the worst case scenario where I was unable to access both Windows and Linux.  As I only recently installed 9.04, I popped the disk back in and reinstalled the / partition.  Now I can access Ubuntu with grub, but Windows continues to give the NTLDR is missing notice.  I have found a set of instructions here:

[http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD]("http://http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD")

After getting burned once playing with MBRs, grubs, and whatnot, I am reluctant to just go head long into this.  I am about to go on a trip and I need my laptop.  But preferably with both Windows and Linux easily accessible.  Any advice will be greatly appreciated.

---

### Post by LewRockwell on 2009-08-07
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

.

---

### Post by philcamlin on 2009-08-07
> **LewRockwell said:**
> [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

.

+1 on that 

its a good idea to keep that disk incase of emergency :popcorn:

---

### Post by P235 on 2009-08-07
Thank you for the link.  When I visited the site I found it a bit bare of instruction, but the gist is that I need to burn the .iso and hope that the contents can somehow restore my Windows partition's MBR?

---

### Post by P235 on 2009-08-07
After having a chance to use this Supergrubdisk I can say that it is a useful, but rather bare tool one can use to fix the mbr.  However, my Windows partition is indeed missing its NTLDR.  It will have to be restored in some way before I can load my Windows partition properly as it cannot even boot up at this point.  When I have the chance I will follow the procedures I found above with the Windows Vista Recovery Disk and hope that the automated step will solve my problems.  

If that does not work, I may have to use the restore disks to bring my laptop to factory settings, then set up the dual boot on the fresh install as I did with Vista and Ubuntu 8.0.4.1.  I hesitate to do this as I am guessing it will take a lot of time, but I may have to resort to that without any other alternatives.  My only regret is that I still do not really understand what exactly went wrong.

I followed the procedures to set up my laptop to dual boot with Vista first and Ubuntu second.  But, for whatever reason, the Linux boot options from the menu.lst file did not load my Ubuntu partition.  EasyBCD indeed changed the MBR to load the Linux boot options as I found them from the menu.lst file, but the options simply did not load.  This is a mystery.  I then, for the worse, tinkered with EasyBCD, ticking something like clearing the MBR for Windows XP?  I suspect I wiped the MBR out completely, which forced me to install 9.04 a second time.  

Now, after tinkering with the Supergrubdisk with no success, I will follow the recovery procedures with the Vista Recovery Disk.  I am generally thankful that modifying the MBR to allow Ubuntu to load up is so easy.  I can only hope that restoring this NTLDR is just as painless.

---

### Post by x33a on 2009-08-08
if actually the NTLDR file is missing, you can either copy that file from the windows installer disc to C: or download the file from here:

[http://tinyempire.com/notes/ntldrismissing.htm](http://tinyempire.com/notes/ntldrismissing.htm)

and copy the NTLDR file to windows C:

---

### Post by P235 on 2009-08-08
Thank you for that, x33.  In fact, that page was where I found the procedures for the Vista Recovery Disk.  The Disk did the trick, but it required a few restarts before it restored the NTLDR.  This is not a problem save for the time it takes for the Disk to load, but the important thing is that I now have access to both OS.  On top of that, I am now armed with Supergrubdisk, Vista Recovery Disk, and the ever useful 9.04 on disk.  EasyBCD for Windows is useful, but my recent experience makes me prefer Grub over leaving Vista in control of the MBR.  

Now I can confidently trample over my MBR with impunity!  Afterall, Grub can be modified by merely changing the text in the menu.lst file.  The ease of doing this just boggles my mind compared to the mystery of how EasyBCD works.

---

