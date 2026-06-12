---
title: "Unable to mount DVD &quot;Unknown filesystem type&quot;"
date: 2010-03-05
forum: New to Ubuntu
---

### Post by kulmacet on 2010-03-05
Greetings,

I am currently running Ubuntu 9.10 64 Bit the specs of my machine are:

uname -r 2.6.31-20-generic
AMD Turion 64bit x2 (Dual Core)
4GB RAM
160GB Hdd

When I put a DVD in the reader I get this error:

Unable to mount <DVD TITLE>
Error Mounting: mount exited
with exit code 1: helper failed
with:
mount: unknown filesystem type ''

I don't believe this issue to be hardware related as I can boot to a knoppix dvd and the reader acts and works as expected. 

An external (usb) dvd reader works with no issues.

I have been fighting this issue for some time and any support is appreciated.

Thanks in Advance,
Kulmacet

---

### Post by skymera on 2010-03-05
What DVD is it?

Did you make it?
Try reburning it at a slow speed, i generally use 4x for DVD.

---

### Post by kulmacet on 2010-03-05
Skymera,

Thanks for the quick reply.

It does not seem to matter weather the DVD is burned or not, I get this error with any DVD with the on board reader.

It is interesting that CD's mount with no issue.

Thanks,
Kulmacet

---

### Post by halitech on 2010-03-05
can you open a terminal and run
```
sudo lshw -C disk
```
and post the output here

---

### Post by kulmacet on 2010-03-05
Thank you for the help.

sudo lshw -C disk
 
*-disk                  
       description: ATA Disk
       product: WDC WD1600BEVE-0
       vendor: Western Digital
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: 01.0
       serial: WD-WX30A79D6900
       size: 149GiB (160GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=0002465d
  *-cdrom
       description: DVD-RAM writer
       product: DVD-RAM UJ-850S
       vendor: MATSHITA
       physical id: 0.1.0
       bus info: scsi@0:0.1.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: 1.50
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom

---

### Post by halitech on 2010-03-05
ok, so the drive is being seen properly so its not an issue where it thinks its only a cdrom and not a dvd. Has it ever worked before? Are the dvd's you are trying video dvds or data dvds?

---

### Post by kulmacet on 2010-03-05
Halitech,

The DVD reader has never worked using Ubuntu. It does work with Windows, Knoppix, and PCLOS.

It does not matter if the DVD is data or video DVD's I get the unknown files system error. :-(

---

### Post by bart.vanaudenhove on 2010-05-01
I had a similar problem on my HP Laptop, with me any data cd or DVD would read  and write fine, but audio cds and movie dvds would not be recognized.

For me the solution was to physically slip the optical drive out of the  computer (unscrew a vise in the back and push the drive a bit out) =  unplugged and power off off course =, plug it back in, and at next  startup everything was fine. (I found it in another post somewhere)

From time to time the same problem reappears and the same solutions  works for a while...

This is in Ubuntu 9.10.

---

