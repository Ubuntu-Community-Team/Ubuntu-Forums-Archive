---
title: "HDD gone missing"
date: 2010-02-26
forum: New to Ubuntu
---

### Post by expatCM on 2010-02-26
I have three hard drives and one has gone missing.  It used to work but simply fell off the planet. Any ideas how to find it?

The drive is listed correctly in Bios.

If I run sudo blkid, the UUID does not show.

If I look with gparted the drive is not listed.

I do not quite understand how it can be showing in Bios but not then generating a UUID.

---

### Post by Peter09 on 2010-02-26
Try looking in syslog - I had a drive which failed - it was seen by the bios but when any attemot to mount it was made an interface failure (electronic not S/W) produced fatal errors - these showed in syslog.

---

### Post by Kakers on 2010-02-26
Type 'mount' in the terminal and see if it is listed there, should be the ones starting with /dev/

---

### Post by spectralblue on 2010-02-26
Happened to me as well. Probably a failed hard drive. Otherwise check the cables perhaps?

---

### Post by expatCM on 2010-02-26
Thanks for all the suggestions.

The cables are fine.  I plugged a different drive in and Bios reported the difference correctly.

Mount lists all the drives except this missing drive.

syslog ....well not sure ....   I do get errors reported about sr0 but I do not know what that is.  Example line "end_request: I/O error, dev sr0, sector 0".

Perhaps it is a hdd failure.  If it is that would be VERY annoying since this is a warranty replacement drive from Seagate.  They are normally quite good with their quality standards ....   

The next step ....  probably need to pull the drive and put it in an external housing and then see if the volume can be seen......  unless there are any other ideas?

---

### Post by expatCM on 2010-02-26
Sadly this is more curious than appears at first glance.

I took out the hdd and put it in a USB housing.  Perfect.  The volume shows, no issues at all.

I then put a new drive into the machine.

The UUID showed up and I set it in the fstab.  Rebooted and the volume was there.  Tested with a write and delete.  No issues.

Rebooted.

No more drive.  Gone again.

So I changed the SATA port.

No change in status.  Drive apparently awol.

---

### Post by Kakers on 2010-02-26
This may seem like a silly question but have you formatted the hard drive? you did say it was new...

---

### Post by expatCM on 2010-02-26
Yes, no doubt about that.  I was able to read and write to the drive on my first attempt.

I have just rebooted and the drive is back again.

To me this sounds like a defective data cable (since I have reallocated SATA ports), but whilst that sounds possible it really also sounds more to be improbable.  But if that is the case then I am a bit stuck to know what the problem really is ....

---

### Post by Kakers on 2010-02-26
Well could swap some of the SATA cables about and see if it does it to another drive

---

### Post by expatCM on 2010-02-26
This is annoying really.  Waiting now to see if the system "settles down".

I have replaced the data cable and the drive volume is seen.  What I do not know is whether or not it will continue to be seen.  

My reservation is that one one reboot the system went straight into a grub terminal.  ls listed all the drives (and nothing else) but I could not quite see what to do there so I rebooted and the system then loaded normally.

---

