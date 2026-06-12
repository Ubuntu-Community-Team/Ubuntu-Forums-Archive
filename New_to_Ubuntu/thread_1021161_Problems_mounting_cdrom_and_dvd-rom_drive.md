---
title: "Problems mounting cdrom and dvd-rom drive"
date: 2008-12-25
forum: New to Ubuntu
---

### Post by cnaqe1 on 2008-12-25
I've tried to play and burn cd's and dvd's but i can't cause it's not mounted. i also tried mounting it in the terminal but there are some things i don't understand.  i typed sudo lshw -C disk and got this:

 *-cdrom:0
       description: CD-R/CD-RW writer
       product: CD-RW  CW-7585
       vendor: MATSHITA
       physical id: 2
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: 1.04
       serial: [MATSHITACD-RW  CW-7585  1.040
       capabilities: removable audio cd-r cd-rw
       configuration: ansiversion=5 status=nodisc


the dvd-rom drive says:

 *-cdrom:1
 description: DVD reader
       physical id: 3
       bus info: scsi@1:0.1.0
       logical name: /dev/cdrom1
       logical name: /dev/dvd1
       logical name: /dev/scd1
       logical name: /dev/sr1
       capabilities: audio dvd
       configuration: status=nodisc

at this poin i am really getting fustrated because i can't do anything with any one of the drives. Can anyone help? please.

---

### Post by Landra on 2008-12-25
I am having the same problem (I did not try typing anything in Terminal though, scared I will mess up something).  

I need help, this is my first time using Ubuntu. I have a used Dell Inspiron 8200 with 2ghz 512mb RAM 70g hdd. I am able to play audio CDs (doesn't include burned CDs) but not a DVD movie (including burned DVDs). I receive an error message (for thr CD) that read,"unable to mount local disk,No media in drive". When I try to play a DVD, the message reads,"an error occurred could not open location: you might not have permission to open file". Please help me to utilize my CD-RW/DVD Rom drive. Ubuntu wasn't pre-installed. The laptop came with Windows XP Home (which I have the license for), looks like the HDD was formatted and Ubuntu was installed. I was able to purchased a burned XP Home CD (since the previous owner lost the original) from a pc/laptop fix it establishment. I am trying to install XP but since the CD drive will does not read the CD, how can I resolve this without purchasing another DVD drive licence? This there a way I can find out if a license was already used/assigned to his laptop? 

I want to run both Ubuntu and XP so I can accomplish what I need to as well as learn more about Ubuntu.

Take me slow, I am a newbie.

---

### Post by Landra on 2008-12-30
My isse was resoled under thread "No media in drive, unable to mount local disk".  My optical drive does not work.

---

### Post by balloooza on 2008-12-30
> but not a DVD movie (including burned DVDs)
that would be because playing region encrypted (what you buy, with actors and ratings, not home movies) is COMPLEATLY ILLEGAL (unless you bought the dell with ubuntu preinstalled, but you say you have xp, so that seems wrong)

---

