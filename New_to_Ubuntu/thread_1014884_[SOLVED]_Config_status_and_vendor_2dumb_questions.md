---
title: "[SOLVED] Config: status and vendor: 2dumb questions"
date: 2008-12-18
forum: New to Ubuntu
---

### Post by vikigal on 2008-12-18
I have been having cd reading problems since I upgraded to 8.04. I am working through them but I think I need to check the drive update or info for the drive or something. How do I find the information I am looking for?  I am worried about updating the driver. Can I do it through the terminal or synaptic?

Next question, which is really dumb: I have an external samsung cdrom and an internal cdrom. The internal is the one that is giving me fits. How do I tell which is which?

Last question: Are the status readings ok? There is a disk in the internal drive, does that make a difference?

lshw -c disk (snipped)

 *-cdrom
       description: DVD reader
       product: RW/DVD GCC-4320B
       vendor: HL-DT-ST
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom1
       logical name: /dev/dvd1
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: 1.11
       capabilities: removable audio cd-r cd-rw dvd
       configuration: ansiversion=5 status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom1
  *-cdrom
       description: DVD-RAM writer
       product: CDDVDW SE-S204N
       vendor: TSSTcorp
       physical id: 0.0.0
       bus info: scsi@2:0.0.0
       logical name: /dev/scd1
       logical name: /dev/sr1
       version: TS01
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: status=open

Thanks for any help. I have been at trying to fix this for a week and I am getting a little nuts, not to mention a lot confused. It is all starting to look like gibberish to me.

---

