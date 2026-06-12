---
title: "ASUS RT-AC66W attached USB disk will not share"
date: 2021-10-12
forum: Networking &amp; Wireless
---

### Post by nrossi on 2021-10-12
Okay, color me stumped.  I have a new (to me) wireless router, an ASUS RT-AC66W, with 2 USB ports running off an Ubuntu 20.04 desktop (though that shouldn't matter).  Wireless works correctly.

Into one of the USB ports I have plugged a 1 TB Seagate BUP Slim BK, formatted as NTFS.  I have gone through the ASUS setup (correctly, I assume) and am able to transfer files to and from the disk via FTP, even via an FTP wireless connection to a different machine.  In the ASUS setup interface I have also marked the disk as a shared LAN disk.

I can see this disk appear in the file browser under Network, and can navigate to its subdirectories. If, however, I try to open one of the subdirectories I get a popup message "Unable to mount location. Failed to mount Windows share. Software caused connection abort."

I have created an entry in etc/fstab as follows:
//192.168.1.1/Seagate\40BUP\40Slim\40BK/File-xfer /media/public/File-xfer cifs rw,auto,vers=1.0,username=<router-admin-name>,password=<router-admin-password> 0 0 

Running "sudo mount -a" in a terminal gives me a mount-cifs error "Permission denied".  Yes, CIFS is installed.

I have tried all the cifs options I can think of with no luck.  I would REALLY like to have this drive as a shared resource that I can use for backup, file-swapping, etc., and not have to load an FTP client each time I need to do that.  Can anyone offer any advice?  Am I missing something obvious to everyone but me?

---

### Post by axelmasok on 2021-10-13
FTP works but SMB/CIFS not working from Ubuntu to ASUS router?
This looks like an ASUS issue you're chasing more than Ubuntu/Linux....

Have you proved the Asus works using SMB/CIFS with that other "treacherous" OS?  ([https://www.fsf.org/news/lifes-better-together-when-you-avoid-windows-11](https://www.fsf.org/news/lifes-better-together-when-you-avoid-windows-11)) Cracks me up.
Without me Internet searching this for you, are you able to paste what this router supports from the manual?

---

### Post by nrossi on 2021-10-14
Some experimentation and some hints from other router threads has me working now, mostly.

In the ASUS setup menu, choose Network Map, then make sure your USB drive is set up as the fastest it's capable of. In my setup, the router only supports USB 2.0, so that's what I selected.  NTFS (the current formatting of the attached disk) works for me.  Anything smaller than 1 TB you may want to format it as FAT32.

Select USB Application in the menu, then click Servers Center.  There are multiple tabs, the first being Media Server.  I didn't intend to use this as a media server but I had it selected anyway, figuring it couldn't hurt.  Turns out that, yes, it does.  At least on my system I couldn't choose both Media Server and Network Share.  So turn it off.

Click on the second tab, Network Place.  Click Enable Share.  I also decided to Allow Guest Login  (which is less secure, but it's a home server, and I'm the only user).  Make sure you click Apply once done.  Below this button, there's a panel where you may click down through the directory structure and add and remove directories.  I cannot do that from my desktop, but I don't really need to, so if I need to add a directory I'll do it through the interface.

The default seems to be to set the attached disk to R/W once you have shared it.  There is a method to choose specific subdirectories and change permissions.

The drive is now accessible to me under Network in Files.  I can add and delete files, and move between directories on the attached drive.  I will test my laptop later, but it should work the same.

---

