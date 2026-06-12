---
title: "Using Scalpel and storing results to network drive"
date: 2011-07-03
forum: New to Ubuntu
---

### Post by Dammerl on 2011-07-03
Dear All,

Hoping this is the right forum ...

I recently have decided to switch to Ubuntu (11.04) and doing this in the early hours, missed to back-up my Thunderbird folders ...

After searching and giving myself a Linux crash-course, I have decided on using scalpel to possibly recover some emails - it just doesn't work for me. I am getting an error message during the second pass:

[B]  Image file pass 2/2.
  /dev/sda1:   0.1% |                                                                                           |   40.0 MB --:--ETAError opening file: /media/Recovery/Hope/&#65533;-0-0/00000345 -- Is a directory
  Scalpel was unable to write output files and will abort.
  This error generally indicates that disk space is exhausted.[/B]

The mount I am (intending) to write to has 2 TB, whilst the scanned drive is 80 GB, so there should be enough space. This is what I am doing:

downloand and install scalpel (1.60) and smbfs

  **$ sudo mount -t cifs -o username=XYZ //192.168.1.1/Harddisk/Ubuntu_Recovery /media/Recovery**

Whereby the drive on the IP address (actually, it's a dreambox with Enigma 2) has 2 TB free. The remote folder (Recovery) has my edited scalpel.conf (to search for Thunderbird email files without extension).

Then I evoke the programme:

  **$ sudo scalpel -b -c /media/Recovery/scalpel.conf /dev/sda1 -o /media/\recovery/Hope**

I new folder Hope is created, contains the audit.txt file, but nothing else. After the first scalpel pass, a large number if identified files is shown (> 700,000), so there should be at least a couple of files, one might think.

I am sure it is something really silly I don't see, so hopefully one of you out there knows the trick!!!!


Best wishes
Tom

---

### Post by overdrank on 2011-07-04
Moved and bump to Absolute Beginner Talk

---

### Post by HermanAB on 2011-07-04
Maybe this will help:
[http://www.howtoforge.com/recover-deleted-files-with-scalpel](http://www.howtoforge.com/recover-deleted-files-with-scalpel)

---

### Post by Dammerl on 2011-07-04
HermanAB,

many thanks! This web page certainly offers more information on the usage of scalpel. But I still do not quite understand the error message about the disk space being exhausted. Is there an intrinsic limit of folder size that each mount has by default? It appears that my laptop does not see the whole mounted harddrive with its 2 TB ...

@ overdrank - many thanksfor moving me to the right spot. It dawned on me today that I may have ended up in the wrong forum ...


Best wishes
Tom

---

### Post by DunZH on 2011-07-23
I got similar results with Scalpel.  It filled up my recovery disc that was larger than the disc with the problem.

I copied my bad drive with dd and am using another disk to hold that. Its 250 gigs.  Then the recovery disk has like 320 gigs free.

What I got was the same file, over and over.  Well, different pieces of the same video file.  Each folder had one thousand files in it, all basically the same.

Then, after about 10 or so of these folders, all with parts of the same file, the program stopped because the disk was full.

Its too bad because the program seemed to work.  I might try again but I guess this will just happen again.  The only thing I can think is the maybe the disk shouldn't be mounted.

---

