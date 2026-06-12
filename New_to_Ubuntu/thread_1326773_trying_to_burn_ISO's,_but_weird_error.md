---
title: "trying to burn ISO's, but weird error"
date: 2009-11-14
forum: New to Ubuntu
---

### Post by ah pook on 2009-11-14
I keep trying to burn ISO dvd's but keep getting this error:
DBus error org.gtk.Private.RemoteVolumeMonitor.NotFound: The given volume was not found

even though the disk seems done, it's not. any ideas?

thanks in advance

Koala, 64-bit. ran fine before...

---

### Post by Paqman on 2009-11-15
What software are you using for burning the DVD?

---

### Post by ah pook on 2009-11-15
Brasero..but I tried Gnomebaker with the same error..

---

### Post by corncob on 2009-11-15
> **ah pook said:**
> I keep trying to burn ISO dvd's but keep getting this error:
DBus error org.gtk.Private.RemoteVolumeMonitor.NotFound: The given volume was not found

even though the disk seems done, it's not. any ideas?


Koala, 64-bit. ran fine before...

Does the "seemingly done" disk work?  If so, I wouldn't worry about the message.  Are you opening the disc burner automatically by inserting a blank disk?  For some reason Brasero seems to be better behaved if you open it from the applications menu instead.

---

### Post by ah pook on 2009-11-16
no, they don't work. and my dvd player recognizes older dvds, just not ones burned since the upgrade....

---

### Post by ranch hand on 2009-11-16
I feel it incombent on me to ask - did you check the md5sum?

---

### Post by ah pook on 2009-11-17
where would I find that?

---

### Post by ranch hand on 2009-11-17
Go to the download page where you got your ISO and there should be a whole bunch of links on the bottom of the page.

The md5sums are at the top of that list.

Once you have that, you need to see what your ISO comes up with;

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by NightwishFan on 2009-11-17
Hi. I believe this error might be related to the new device manager. I remember seeing an error like this, but my disks worked. I think it just means the disk is still mounted, so it could not mount or unmount it at that time. I am not an expert that is just supposition, however.

Do the disks actually have burned content or are they blank? Check using Ubuntu by ejecting and reloading the disk, and opening them in the file browser. Even a DVD movie will have a VIDEO_TS directory.

---

### Post by ah pook on 2009-11-17
Yes, they have burned content. These ISO's are made by Devede, from avi's I've gotten. If it's simply a matter of unmounting the disks, ok, no problem. Let me try one and try that. For some reason, I don't think thery're finalized. but I could be wrong. Again.

---

### Post by ranch hand on 2009-11-17
Did you check the md5sum?  There is no reason what so ever to burn a bad ISO.

---

### Post by corncob on 2009-11-18
> **ranch hand said:**
> Did you check the md5sum?  There is no reason what so ever to burn a bad ISO.

I think one time I copied the .iso rather than its contents if that makes any sense.  Anyway, it wouldn't boot and I tried something slightly different and the new disk showed the contents (casper, isolinux, install, etc) in file manager and was bootable.  It was a long time ago and I can't remember the details -- used a different program maybe.

---

### Post by jmore9 on 2009-11-18
I always use k3b.  Never have had problem with it.

---

### Post by NightwishFan on 2009-11-18
I think you can manually finalize with one of Ubuntu's command line programs, such as wodim.

---

### Post by ah pook on 2009-12-04
K3B works fine. nothing else works, but that's perfect. 

Thank you all...

---

### Post by daqron on 2010-01-26
I have been having this problem too (and many other annoying issues) since the upgrade to 9.10. 

In my case, the error occurs when Brasero attempts to eject the burned media. It would seem that in 9.10 the way discs are mounted has changed, and I frequently have to click the eject icon in the file browser (like a Mac) in order to get my media out. Previously the hardware eject button worked, and Brasero never had a problem kicking out completed discs. This new behavior is strange and bothersome, but unlike the original poster,  my burned media works fine despite the error.

---

