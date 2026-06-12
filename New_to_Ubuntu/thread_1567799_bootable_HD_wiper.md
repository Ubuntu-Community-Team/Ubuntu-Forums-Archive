---
title: "bootable HD wiper"
date: 2010-09-04
forum: New to Ubuntu
---

### Post by Someone uk on 2010-09-04
2 questions
1) is there a bootable programme that i can download  that will wipe my hard drive from the first bit to last bit
2) can an ubuntu cd be safly removed whist in a live session?

---

### Post by andrewthomas on 2010-09-04
> **Someone uk said:**
> 2 questions

2) can i burn CD-R whist ubuntu is in a live session?
Yes

---

### Post by jroa on 2010-09-04
For the first question, just boot up a gparted CD and format the whole drive.

---

### Post by da burger on 2010-09-04
[http://www.dban.org/](http://www.dban.org/) I'm fairly sure that's what your looking for. Also, regarding you second question, I don't think you can remove the live cd whilst in a live session so if you want to burn a cd whilst in a live session I recommend you run the ubuntu live cd from a USB stick.

---

### Post by kwacka on 2010-09-04
Darik's Boot & Nuke will boot from CD, and over-write everything on your harddrive with zeroes.

Run it three or 4 times and it will take a forensic lab to recover anything on the drive.

[http://www.dban.org/](http://www.dban.org/)

---

### Post by Someone uk on 2010-09-04
i have an unusual contradiction here
gparted recognises a 232 GB unallocated space on my hard drive
and the ubuntu disk untility recognises 3 partitions on my disk that adds up to 250 gb and that it refuses to format the drive to a "master boot record" saying > Error creating partition table: helper exited with exit code 1: In part_create_partition_table: device_file=/dev/sda, scheme=0
got it
got disk
committed to disk
BLKRRPART ioctl failed for /dev/sda: Device or resource busy
(i did/ do have a an encrypted home directory if that makes a difference)

---

