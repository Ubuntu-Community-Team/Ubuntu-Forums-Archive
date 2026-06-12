---
title: "Linux equivalent Autobackup"
date: 2009-01-22
forum: New to Ubuntu
---

### Post by paulchinnz on 2009-01-22
Hi looking for the above.  For those not familiar, in Windows, it does incremental backups of selected folders, **and you can put a password on the backup**.  It also has the handy feature of being able to restore the files to any location, including another computer.

Thanks in advance.

---

### Post by hyper_ch on 2009-01-22
rsync could be an option
maybe rsync + hardlinks if you want to have snapshots.

---

### Post by 5BallJuggler on 2009-01-22
Try "Remastersys Backup" It's not so much as an Autobackup but it does save everything you have into an ISO, you can then burn this to a DVD and use it on any machine. I added it last night, follow the instructions on the Website

[http://www.remastersys.klikit-linux.com/](http://www.remastersys.klikit-linux.com/)

Hope this is of some use.

---

### Post by paulchinnz on 2009-01-22
Thanks.  Had noted rsync/grsync (I really would prefer something with GUI) but no passworded option as far as I can tell, which is essential for my needs.

I backup on to an external HDD, which is house-bound, but have really important - both in terms of sensitivity and usefulness - files on a USB flash drive that I carry around constantly, and this is where I need the password, in case I lose the flash drive.

---

### Post by linux6994 on 2009-01-22
I use sbackup it installs and gives a backup and restore option under System > Administration

The backup can be scheduled easily and the restore can be chosen just as easy.

---

### Post by Temposs on 2009-01-22
You might look at Simple Backup(it's in the repositories). It does a pretty decent job with incremental automatic backups, and has a lot of different options to fit your needs, although it's certainly not perfect yet.

---

### Post by paulchinnz on 2009-01-22
Thanks.  Simple Linux Backup looks promising, but lack off a security feature is a showstopper for me.

---

### Post by hyper_ch on 2009-01-22
what security feature?

---

### Post by meho_r on 2009-01-22
Maybe [Areca?]("http://areca.sourceforge.net/")

EDIT: Just played a little bit with Areca. Seems pretty powerful. I noticed two things that may be some kind of "spoiler" (although for me it's OK): No direct backup on CD/DVD, just local and FTP, and encrypted archives can be read only by Areca. Still, very nice piece of software. It's written in Java, it's cross-platform, no installation needed and one can put it on USB stick and carry with him/her.

---

### Post by ComputerHQ-UK on 2009-01-22
How about Flyback?

When used correctly you can mirror you whole system to a external drive and keep existing permissions.  Works kind of live Apples time machine.

[http://code.google.com/p/flyback/](http://code.google.com/p/flyback/)

---

### Post by paulchinnz on 2009-01-22
Thanks, especially meho_r for suggeting Areca.  Hadn't come across that and ability to encrypt archives (aka 'security feature') is exactly what I want.  Will let you know how I get along.

---

