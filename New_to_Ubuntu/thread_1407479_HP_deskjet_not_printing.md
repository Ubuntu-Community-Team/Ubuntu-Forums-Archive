---
title: "HP deskjet not printing"
date: 2010-02-15
forum: New to Ubuntu
---

### Post by dotborg on 2010-02-15
Hi,
I have an ancient HP Deskjet 550C parallel port printer that I'm trying to get working with Ubuntu 9.10.
So far I've followed the advice I've found elsewhere in the forums and have been able to determine that everything seems to be ok except actually being able to print!
 
The printer is detected by system>admin>printing as being attached to the parallel port, and I have a choice of several possible drivers for my particular model but none of them have successfully printed a page for me so far.
 
I've tried downloading the latest hplip 3.9.12 but this doesn't work either.
 
I can get this printer to work when I run Puppy Linux, it says it's using CUPS+Gutenprint v5.2.3.99.1 so I know it CAN work, it's just that karmic isn't playing.
 
Any pointers would be much appreciated.

---

### Post by cariboo on 2010-02-16
Have you tried using the cups interface? Access it from:

[http://localhost:631]("http://localhost:631")

---

### Post by oldsoundguy on 2010-02-16
you can also give installing hplip (the hp utility package) from the package manager.

I have an old 3 in 1 1150c that went right out of the box after the cups drivers and hplip were installed.  (and xsane for the scanner)

---

### Post by dotborg on 2010-02-17
Just had a go with the cups interface, and still no luck I'm afraid.
Is there a way to go back a version on Gutenprint to the one that puppy is using just in case that helps?

---

### Post by dotborg on 2010-03-03
Well, I've had no positive results from anything I've tried from the various tips I found on this forum. Hplip / hp-setup doesn't work at all and HP don't provide suppport for the deskjet 550C so I have to assume this is a dead end.
 
CUPS still looks like the best option as at least it finds my printer but just doesn't get as far as printing. 
 
Here's the error lines from the cups log:
E [28/Feb/2010:12:32:10 +0000] Unable to remove temporary file "/var/spool/cups/tmp/.hplip" - Is a directory
E [28/Feb/2010:12:41:03 +0000] cupsdReadClient: 14 IPP Read Error!
E [28/Feb/2010:12:42:26 +0000] [cups-driverd] Bad driver information file "/usr/share/cups/drv/sample.drv"!
E [28/Feb/2010:12:43:23 +0000] [Job 23] Aborting job because it has no files.
E [28/Feb/2010:12:44:00 +0000] Unable to remove temporary file "/var/spool/cups/tmp/.hplip" - Is a directory
E [28/Feb/2010:12:45:03 +0000] cupsdReadClient: 14 IPP Read Error!
E [28/Feb/2010:13:06:30 +0000] [Job 18] Unable to queue job for destination "HP-Deskjet-550c"!
E [28/Feb/2010:13:06:30 +0000] [Job 19] Unable to queue job for destination "HP-Deskjet-550c"!
E [28/Feb/2010:13:06:30 +0000] [Job 21] Unable to queue job for destination "deskjet550c"!
E [28/Feb/2010:13:06:36 +0000] [Job 18] Unable to open job control file "/var/spool/cups/c00018" - No such file or directory!
E [28/Feb/2010:13:06:36 +0000] [Job 19] Unable to open job control file "/var/spool/cups/c00019" - No such file or directory!
E [28/Feb/2010:13:06:36 +0000] [Job 21] Unable to open job control file "/var/spool/cups/c00021" - No such file or directory!
 
If anyone can help decipher it maybe I can get to the bottom of this.
 
The .hplip directory is owned exclusively by lp so may be a permissions issue?
The missing files listed in /var/spool/cups/ appear to be the wrong numbers - where it was looking for jobs 18 - 21, the files in the directory were numbered 22-25 so I'm really not sure what's going on there.
 
I really appreciate everyone's help, this forum is a great resource for people like me.
The rest of the CUPS debug log is attached (although it covers quite a few re-tries at activating the printer so the name changes a few times..)

---

### Post by Jared Norris on 2010-03-03
If you're keen on trying the old Gutenprint drivers have a look at[http://sourceforge.net/projects/gimp-print/files/]("http://sourceforge.net/projects/gimp-print/files/") as I can see there is a folder for version 5.2.3 so that might be what you are looking for.

Hope you have some luck with that, HP printers are normally the easiest of all to install on any linux.

---

