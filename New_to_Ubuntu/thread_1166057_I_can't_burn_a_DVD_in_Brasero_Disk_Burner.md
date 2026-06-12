---
title: "I can't burn a DVD in Brasero Disk Burner"
date: 2009-05-21
forum: New to Ubuntu
---

### Post by st4 on 2009-05-21
I keep getting an error message saying that my blank cd or dvd is unsupported. Has anybody found a solution this problem?

---

### Post by DLG102282 on 2009-05-21
Have you filed a bug report?

---

### Post by st4 on 2009-05-21
> **DLG102282 said:**
> Have you filed a bug report?Uh, I hate to sound st00pid, but how do you do that?:o

---

### Post by Sidewinder1 on 2009-05-21
If it's truely a bug and not some other problem, start here:
[http://mdzlog.wordpress.com/2009/03/31/please-dont-report-ubuntu-bugs-directly-to-launchpad/](http://mdzlog.wordpress.com/2009/03/31/please-dont-report-ubuntu-bugs-directly-to-launchpad/)

---

### Post by st4 on 2009-05-21
Okay, I filed a bug report, thanks for all of the help.

---

### Post by MrWES on 2009-05-21
> **st4 said:**
> I keep getting an error message saying that my blank cd or dvd is unsupported. Has anybody found a solution this problem?


Are you using DVR+R or DVD-R media? Some burners only use DVD+R.

---

### Post by rob2uk on 2009-05-21
> **st4 said:**
> Okay, I filed a bug report, thanks for all of the help.

Got a link?

---

### Post by ghostborg on 2009-05-21
Install K3b or use Nero Linux $20

For DVD's if you are using DVD shrink under Wine you could change
the output from a folder to and ISO file. then anything under Linux should burn it.
I use Nero for a UDF compatibiliy problem between Winblows and Linux.
K3b should do the trick for ya though.

Also checkout DVDfab HD Decrypter free under Wine for those problematic discs.
Use your arrow keys and mouse together to navigate the preferences to turn off auto playback settings.

Good Luck.

---

### Post by Salomonis on 2009-05-21
I'm having a related problem, but it's because the option for properties and for burning is grayed out so I can't click it.  Also the type of dvd-r that I'm using is not selectable at the bottom left.  I simply use the single layer 8 hours and remind myself not to go over 2 hours.  I have a screen of what I'm talking about.

---

### Post by MrWES on 2009-05-21
> **Salomonis said:**
> I'm having a related problem, but it's because the option for properties and for burning is grayed out so I can't click it.  Also the type of dvd-r that I'm using is not selectable at the bottom left.  I simply use the single layer 8 hours and remind myself not to go over 2 hours.  I have a screen of what I'm talking about.

I have an older HP Pavillion, and I can only use DVD+R, but on my Dell D600 I can use either. Get a single or five pack of DVD+R and try them out.

~Bill

---

### Post by Salomonis on 2009-05-21
I was hoping it wasn't that.  Bought A lot of these kinds of DVD.  They're DVD-R instead of DVD+R.  I'll have to read up to find out the difference.  I can always use them for data storage, but it would be nice to see these movies on a home dvd player.  My one wish in life would be becoming computer efficient.  That seems to be more difficult as time goes on.

---

### Post by MrWES on 2009-05-22
> **Salomonis said:**
> I was hoping it wasn't that.  Bought A lot of these kinds of DVD.  They're DVD-R instead of DVD+R.  I'll have to read up to find out the difference.  I can always use them for data storage, but it would be nice to see these movies on a home dvd player.  My one wish in life would be becoming computer efficient.  That seems to be more difficult as time goes on.

From the terminal, type:
```
sudo lshw -C Disk
```
Look for an output something like this:
```
 *-cdrom
       description: DVD writer
       product: DVD+-RW ND-6500A
       vendor: _NEC
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: 202C
       serial: [_NEC    DVD+-RW ND-6500A202C04081200
       capabilities: removable audio cd-r cd-rw dvd dvd-r
       configuration: ansiversion=5 status=nodisc

```
Look at the 'product' response area and see if it lists DVD-+ or just DVD-. That will let you know for sure which DVD media you can use in that drive.

Bill

---

### Post by Salomonis on 2009-05-27
*-disk:0                
       description: ATA Disk
       product: WDC WD400BB-00DE
       vendor: Western Digital
       physical id: 0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: 05.0
       serial: WD-WMAD13119387
       size: 37GiB (40GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=e2f5e2f5
  *-disk:1
       description: ATA Disk
       product: QUANTUM FIREBALL
       vendor: Quantum
       physical id: 0.1.0
       bus info: scsi@0:0.1.0
       logical name: /dev/sdb
       version: A01.
       serial: 314015817349
       size: 27GiB (30GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=fa6a6868
  *-cdrom
       description: CD-R/CD-RW writer
       product: CW058D CD-R/RW
       vendor: CyberDrv
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: 100D
       serial: 3CyberDrvCW058D CD-R/RW  100D
       capabilities: removable audio cd-r cd-rw
       configuration: ansiversion=5 status=nodisc
  *-cdrom
       description: DVD-RAM writer
       product: DVD Writer 1040r
       vendor: HP
       physical id: 0.0.0
       bus info: scsi@2:0.0.0
       logical name: /dev/cdrom1
       logical name: /dev/cdrom2
       logical name: /dev/cdrw1
       logical name: /dev/cdrw2
       logical name: /dev/dvd1
       logical name: /dev/dvd2
       logical name: /dev/dvdrw1
       logical name: /dev/dvdrw2
       logical name: /dev/scd1
       logical name: /dev/sr1
       version: MH21
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: status=nodisc

It shows dvd-r, and understand I don't have problems turning the disks into data storage, but I want the disks to be readable on home dvd players.

---

### Post by crazypeppo on 2009-05-28
If you are burning an .iso make sure you manually select .iso image instead of letting brassero "choose best option".

---

### Post by Mark Phelps on 2009-05-28
Hate to break the news but some DVD burners simply can't burn DVD+RW DVDs.

I had a new Plextor burner (have been buying Plextors for YEARS) and, upon inserting a DVD+RW disc, was informed that it could not format the media!

Tried several disks and brands, results were always the same.

Tried the same disks on another machine with a Sony burner -- worked fine.

Swapped out the EXPENSIVE Plextor (which, it turned out, was a rebadged Opti-Arc) with a cheapo Samsung -- and all the disks burned just fine.

So, my $12 Samsung outperforms the $80 Plextor -- who'd have guessed that.

---

### Post by Salomonis on 2009-05-29
It worked with NERO, but I haven't tried installing that software on to ubuntu cause I hate wine.  I'm trying to take .avi files and burn them on a dvd-r so that the format can be read on a home dvd player.  I think it's a software problem.  I have been able to burn .iso on these dvd-r using cd/dvd creator.  Problem with this software(cd/dvd creator) is that it can't convert .avi into .iso.  If you know of a means to convert .avi to .iso that'd work.  Then I could just forget about Brasero.  I wanted it to work with Brasero cause it has that option(video project) to work for home dvd players.  So I have 3 choices:
This Brasero problem is fixed.
I install NERO using wine.(not guaranteed to work cause wine can be buggy)
There is a software package that converts .avi and other formats like .mp4 .mpeg(etc.) to .iso.  
I have tried under add/remove to find this kind of software but didn't have any luck.  Maybe I'm focusing on the wrong thing.

---

### Post by Salomonis on 2009-05-29
I'm going to "tinker" with DeVeDe and video converter(winff)
to see if they can work.

---

### Post by mikechant on 2009-05-29
I'd recommend DeVeDe - it seems to happily convert every video file type I throw at it.

---

### Post by Tholley on 2009-05-29
Had same problem with Brasero. Nixed that, now I use DeVeDe to convert/transcode, and K3B to burn to DVD. Works very well that way, and you can actually get 2 movies to fit on 1 dvd. So far works in all my standalone dvd players.

---

### Post by Salomonis on 2009-05-30
Woot! DeVeDe works like a charm.  Not exactly the most user-friendly gui, but once I got it, I was able to convert everything.  Makes me feel like a media god!!!:D Thanks for all the help.

---

