---
title: "How can I backup my Eee PC before installing Ubuntu?"
date: 2009-09-14
forum: New to Ubuntu
---

### Post by learningcurb on 2009-09-14
I'd like to backup the default OS on my Eee PC 901 to an external hard drive before I erase the 4 gig flash drive and install Jaunty over it.  The thing is, the Eee PC has a weird partition layout with 3 small partitions on it.  How would I go about backing this up with dd?  Can I use dd to backup the entire drive (all three partitions) to one file or should I backup each partition to a seperate file?

Or is there another program besides dd that would be better for this task?  Thanks.

---

### Post by ankspo71 on 2009-09-14
Hi,
I use a live cd called Clonezilla and it does a good job. You can download either Debian based or Ubuntu based live CD. If the Ubuntu live CD lets you work with your external drive, then I think Clonezilla will have no problem either. It can back up entire drives (including all the partitions) and place it in your other drive as a set of packages (images). You will be able to keep using your external drive for storage too.

Here is a tutorial for an external drive.
[http://clonezilla.org/clonezilla-live/doc/showcontent.php?topic=03_Disk_to_disk_clone](http://clonezilla.org/clonezilla-live/doc/showcontent.php?topic=03_Disk_to_disk_clone)

Clonezilla site (note the ubuntu based version is called alternate)
[http://clonezilla.org/](http://clonezilla.org/)

PS. I don't know whether or not clonezilla would be better than dd. Sometimes restoring windows partitions can give trouble with the windows MBR. 
See: 
[http://drbl.sourceforge.net/faq/fine-print.php?path=./2_System/23_Missing_OS.faq#23_Missing_OS.faq](http://drbl.sourceforge.net/faq/fine-print.php?path=./2_System/23_Missing_OS.faq#23_Missing_OS.faq)

James

---

### Post by nhasian on 2009-09-14
you can back up the entire device with Clonezilla.  that will keep all the partitions and data intact, just make sure to choose the option Device to Image option so the image is saved to a file.  If you do Device to Device, it will wipe all the data on the target device and replace it with the source data!

---

### Post by ankspo71 on 2009-09-14
Hi,
Yes, be sure to use "device to image", if you plan on using any data on the external drive. The tutorial I linked showed it using "device to device". I use "device to image" and been happy with that ever since.

Thanks to the previous poster for pointing that out.

James

---

### Post by starcannon on 2009-09-14
Be sure to visit [http://array.org/ubuntu/](http://array.org/ubuntu/) and get the very nice custom EeePC kernel; once you have it set up correctly I highly doubt you'll put xandros back on there.

I have several of the little EeePC netbooks, so if I can help lemme know; I'll try to look in on this thread a bit. 

GL and HF

---

### Post by aw4lly on 2009-09-14
Also look at [eeebuntu.org]("http://www.eeebuntu.org/") I have a friend who is enjoying this more than straight ubuntu on his eeepc.

---

### Post by learningcurb on 2009-10-07
Hey again.  I know it's been ages since I started this thread (school took priority over geeking around for a while :)).  Anyhow, I went to download Clonezilla at [http://clonezilla.org/download/sourceforge/](http://clonezilla.org/download/sourceforge/) but I find confusing how there is both an ISO and a ZIP file option to choose from.  If I'm planning to boot my EeePC from a SD card or USB stick, which choice is better?

Also, is the Ubuntu based version of Clonezilla the better choice for an EeePC?  Would it perhaps have better hardware support?

---

