---
title: "Got desktop to boot from live CD and then ..."
date: 2009-01-05
forum: New to Ubuntu
---

### Post by sssbobbyr on 2009-01-05
I got the machine to boot from the live CD
it starts loading and eventually goes back to BIOS looking commands with errors

If i just run the start or install we end up with infinite:
ata1: translated ata stat/err blah blah blah
buffer I/O error on device hdd, logical block 178797

I have tried the f6 options all end up at infinite series of something like this:

ata1 status=0x51 {driveready seekcomplete error}
ata1 error=0x40 {incorrectable error}

anybody got any ideas?

---

### Post by jiangshi on 2009-01-05
Sounds like hard disk drive problems. Do you or have you ever had another OS on the machine? Can the machine currently be booted to another OS? Are the hard drives SCSI, SATA or IDE? Does the CD you are using to boot to, work on another computer? You might try that to make sure the CD isn't corrupt. More detailed information about you computer would also be helpful, although it can be difficult to troubleshoot hardware problems over the Internet.

---

### Post by sssbobbyr on 2009-01-05
Yeah the computer is now running vista

The live cd gets closer to running on an xp machine i have

and it gets all the way to the X not working on my vista laptop

I am checking on the hard drive for the vista machine

---

### Post by sssbobbyr on 2009-01-05
the hard drive is sata

the disk drive is ide

---

### Post by jiangshi on 2009-01-05
> **sssbobbyr said:**
> Yeah the computer is now running vista

The live cd gets closer to running on an xp machine i have

and it gets all the way to the X not working on my vista laptop

I am checking on the hard drive for the vista machine

Ok, it could be SATA related, but the first order of business is to make sure your CD is good. If the live CD does not boot you all the way into the desktop on two different machines, it is likely that the CD itself is the problem, unless the two machines are very much alike.

What version of Ubuntu are you using? If it is 8.10, you might try the 8.04 or even the 7.10 version. I've had some problems getting 8.10 to work on all my machines. Yet these same machines would run 7.10 just fine.

Also, make sure you are not trying to run a 64 bit version of Ubuntu on a 32 bit machine. The model number of your CPU will tell you if it is 64 bit. Although this is unlikely since you can get part way to the desktop.

---

### Post by supererki on 2009-01-05
yea i guess i had the same problem... was looking for an answer for weeks... anyways... i managed to solve it by turning on AHCI in BIOS...
it had something to do with the 2.24 kernel not recognizing SATA.... well :D fck im also N00b with computers.

yo, help me with my problem somebody please.

[http://ubuntuforums.org/showthread.php?t=1031267](http://ubuntuforums.org/showthread.php?t=1031267)

---

### Post by sssbobbyr on 2009-01-05
thanks will try it

I am using ubuntu 6.06

it was recommended to me

---

