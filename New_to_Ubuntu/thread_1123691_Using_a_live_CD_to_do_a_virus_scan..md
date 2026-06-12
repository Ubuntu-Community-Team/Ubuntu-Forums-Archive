---
title: "Using a live CD to do a virus scan."
date: 2009-04-12
forum: New to Ubuntu
---

### Post by InfectedWithDrew on 2009-04-12
I've been trying to use a live CD to scan an entire hard drive but I've had very little luck.  I boot the CD, then download Clamtk, and then when I try to do a recursive scan on the entire drive, Clamtk turns grey and stops responding.

Any suggestions?  I really just need a live CD that will let me do a virus scan, preferably with an updated virus database via the internet.  I've only used Ubuntu before but I'm open to other distros provided I can get an ethernet connection working on the live CD.

---

### Post by MrWES on 2009-04-12
Maybe PuppyLinux, I believe it comes with AV intalled.

Bill

---

### Post by InfectedWithDrew on 2009-04-12
I'd like to have an up-to-date database and I'm not skilled enough to manually set up the internet connection on Puppy.

----------------
Now playing: [Switchfoot - C'mon, C'mon](http://www.foxytunes.com/artist/switchfoot/track/cmon%2c+cmon)

---

### Post by MrWES on 2009-04-12
> **InfectedWithDrew said:**
> I'd like to have an up-to-date database and I'm not skilled enough to manually set up the internet connection on Puppy.

----------------
Now playing: [Switchfoot - C'mon, C'mon](http://www.foxytunes.com/artist/switchfoot/track/cmon%2c+cmon)

Hrmm...most times the wireless with Puppy 4.2 works Out Of the Box. The download normally takes more time than to setup :)

Good Luck,
Bill

And if you're hardwired, it'll take you 10 seconds to setup :)

---

### Post by Yvan300 on 2009-04-12
Yeah puppy linux really has great out of the box compatibility, but i don't think you can download and install programs while using the live cd in ubuntu. Last time i used it and downloaded the restricted codecs, they were installed, but when i tried to play my movie, totem reported that the codecs were not installed. You could try running ubuntu from a flash drive, that would be a more probable avenue, don't you think :)

---

### Post by MrWES on 2009-04-12
> **Yvan300 said:**
> Yeah puppy linux really has great out of the box compatibility, but i don't think you can download and install programs while using the live cd in ubuntu. Last time i used it and downloaded the restricted codecs, they were installed, but when i tried to play my movie, totem reported that the codecs were not installed. You could try running ubuntu from a flash drive, that would be a more probable avenue, don't you think :)


I believe the @'s original question was concerning virus scanning. Burn puppy to a CD, boot it, mount the drive you want to scan, run F-Prot (already on utility menu) update the defs, point F-Prot to your mounted drive and scan.

Bill

---

### Post by InfectedWithDrew on 2009-04-12
> **MrWES said:**
> I believe the @'s original question was concerning virus scanning. Burn puppy to a CD, boot it, mount the drive you want to scan, run F-Prot (already on utility menu) update the defs, point F-Prot to your mounted drive and scan.

Bill

The manual said, in order to set up a connection, you had to do some ifconfig-ing.

Also, you can install to RAM on a live CD.  How else would I actually *run* Clamtk?  It just stops responding when recursively scanning an entire drive...

----------------
Now playing: [Long Since Forgotten - 06 1018, Press Return](http://www.foxytunes.com/artist/long+since+forgotten/track/06+1018%2c+press+return)

---

### Post by MrWES on 2009-04-12
> **InfectedWithDrew said:**
> The manual said, in order to set up a connection, you had to do some ifconfig-ing.

Also, you can install to RAM on a live CD.  How else would I actually *run* Clamtk?  It just stops responding when recursively scanning an entire drive...

----------------
Now playing: [Long Since Forgotten - 06 1018, Press Return](http://www.foxytunes.com/artist/long+since+forgotten/track/06+1018%2c+press+return)


Puppy has a connection wizard, which is pretty is to run and setup. Also, you wouldn't run Clamtk, you would run F-Prot, the default AV in Puppy -- already installed.

Drive on kiddo!

---

### Post by InfectedWithDrew on 2009-04-12
> **MrWES said:**
> Puppy has a connection wizard, which is pretty is to run and setup. Also, you wouldn't run Clamtk, you would run F-Prot, the default AV in Puppy -- already installed.

Drive on kiddo!

Ah, sounds nice.  I'll check it out, then.  Maybe I misunderstood the manual pages?

----------------
Now playing: [Kutless - All The Words (Sea Of Faces Album Version)](http://www.foxytunes.com/artist/kutless/track/all+the+words+(sea+of+faces+album+version))

---

### Post by connorh123 on 2009-04-12
You don't need a virus scanner, Linux doesn't get viruses. However, feel free to type virus in add/remove, there's a program there.

---

### Post by juancarlospaco on 2009-04-12
Sorry, the Description is on Spanish, but im finishing this one :
[URL="http://ubuntuforums.org/showthread.php?t=1123829"]
http://ubuntuforums.org/showthread.php?t=1123829[/URL]

[IMG]http://img152.imageshack.us/img152/7996/tempipb.jpg[/IMG]


[IMG]http://img261.imageshack.us/img261/1616/temp2h.jpg[/IMG]

Jaunty based, made with VM-Builder from Canonical, avaliable soon *(when i find a File Host)*.

---

### Post by InfectedWithDrew on 2009-04-12
> **connorh123 said:**
> You don't need a virus scanner, Linux doesn't get viruses. However, feel free to type virus in add/remove, there's a program there.

However using a LiveCD to do scans on Windows machines helps me keep from using my flash drive with ClamWin portable (which helps prevent viruses from spreading).

----------------
Now playing: [Fenix TX - something bad is going to happ](http://www.foxytunes.com/artist/fenix+tx/track/something+bad+is+going+to+happ)

---

### Post by MrWES on 2009-04-12
You can run, and I do now, Puppy Linux from a 2gb flash drive. :)

Bill

---

### Post by M4rotku on 2009-04-12
you could use the Ubuntu live cd and use clamav via the command line.

the command that I prefer to use is:

> sudo clamscan -ri /

The -r option tells it to scan folders recursively and the -i tells it to only report infected files instead of listing every file it scans.  If you use a 'clamscan --help', then it will tell you how to enable support for archive formats if you need them.

I'm not an expert on this by any means, but I hope this helps. :p

---

### Post by Yvan300 on 2009-04-13
Most likely he isn't talking about linux man, he must want to scan a windows partition on his pc or wants to boot from the live cd to fix someone's virus problem :)

---

### Post by MrWES on 2009-04-13
> **Yvan300 said:**
> Most likely he isn't talking about linux man, he must want to scan a windows partition on his pc or wants to boot from the live cd to fix someone's virus problem :)

That how I took the original post; thus the reason I suggested using Puppy Linux, either from a Live CD or flash drive.

Bill

---

