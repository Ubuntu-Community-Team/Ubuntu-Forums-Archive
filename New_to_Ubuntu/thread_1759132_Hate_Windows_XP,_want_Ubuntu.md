---
title: "Hate Windows XP, want Ubuntu"
date: 2011-05-15
forum: New to Ubuntu
---

### Post by Jeffrey Kang on 2011-05-15
Here's the situation:
Dell Latitude D610 (laptop) running windows xp home but we don't have the windows cd. I don't even think it's a legal copy because it doesn't have the office programs.

The laptop is infected with 'windows restore' virus and we can't get rid of it. We were going to trash the computer and get a new one, but I think it's time to try linux.

We don't want to use Windows anymore. Is there any way we can delete everything on the hard disk so it's totally clean? Then install ubuntu?

I'm downloading ubuntu 11.04 now.

---

### Post by Frogs Hair on 2011-05-15
When you insert the cd you will have the option to use the entire disk and the disk be formatted and the contents wiped clean prior to installation .

---

### Post by jaut on 2011-05-15
Ubuntu will ask what to do with the installation CD. Select the option to install a fresh copy of Ubuntu, replacing Windows XP. It will then 'clean' Windows XP and all other files off the harddrive, and it will install Ubuntu directly after.

---

### Post by TeoBigusGeekus on 2011-05-15
You don't have to do anything before installing ubuntu - expect from backing up your important files on an external hd/usb/dvd.
The ubuntu installer will take care of everything.

Welcome aboard.

---

### Post by Rex Bouwense on 2011-05-15
Jeffrey, welcome to the forums.  After the download finishess, run an MD5sum check on the downloaded ISO.  
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)
If you have a good download, then burn the ISO to a CD at the lowest speed possible.  That will give you a bootable CD which you may use to boot your computer.  When you boot you can try Ubuntu to see if all of your hardware works with Ubuntu and or install it right over Windows XP.  It will format the drive for you (ex4 I believe) and install Ubuntu.  It will take about 30 minutes.  I must stress one thing, back up any data that you want to retain because it will all be gone when you install.  Many people on the forums will be able to help if you run into problems.  Enjoy you experience.

See there is a lot of help out there.  My two finger typing skills just make me a little late.

---

### Post by egalvan on 2011-05-15
Frogs Hair and jaut have good suggestions.

Another suggestion, if you want to **totally** wipe the drive...

download dban (Darik's Boot and Nuke ("DBAN"))
from dban.org. It's a very small iso.
burn it to cd or USB, boot from it and it will **totally** wipe the drive.
I have used it for over four years. Never failed to wipe a drive it could see.


And that D610 is a good little lappy. The battery may need new cells, and you may want more RAM
(can one ever have too much RAM :)) 512M is a good amount, 1GB even better.
The D610I I used had 1GB, and ran 8.04 (Hardy Heron LTS) for two years before the MB croaked
(the MB had coke spilled on it)
If you want to trash it, there's a handy trashcan right outside my door that you are welcome to toss it into...
I found that last D610 in a trashcan, power supply and all...

---

### Post by Jeffrey Kang on 2011-05-15
I'm confused.
Correct me if I'm wrong, the order of events are as follows:
finish downloading ubuntu 11.04
burn it to CD (1)
put CD into laptop
install fresh copy of ubuntu (2)

1 - do I need to download infra/iso recorder ([http://www.ubuntu.com/download/ubuntu/download)?](http://www.ubuntu.com/download/ubuntu/download)?)

2 - this will delete the virus and windows files on the computer and install ubuntu? (I don't care for the files on the laptop)

---

### Post by TeoBigusGeekus on 2011-05-15
> **Jeffrey Kang said:**
> 
1 - do I need to download infra/iso recorder ([http://www.ubuntu.com/download/ubuntu/download)?](http://www.ubuntu.com/download/ubuntu/download)?)

2 - this will delete the virus and windows files on the computer and install ubuntu? (I don't care for the files on the laptop)

1. Just burn the image with any image burning app in windows: nero, cdburnerxp, etc.

2. Yes.

---

### Post by slooksterpsv on 2011-05-15
> **Jeffrey Kang said:**
> I'm confused.
Correct me if I'm wrong, the order of events are as follows:
finish downloading ubuntu 11.04
burn it to CD (1)
put CD into laptop
install fresh copy of ubuntu (2)

1 - do I need to download infra/iso recorder ([http://www.ubuntu.com/download/ubuntu/download)?](http://www.ubuntu.com/download/ubuntu/download)?)

Yes windows xp doesn't include and ISO Burning Program. Windows 7 is just barely getting caught up with putting in essential user utilities that we as Linux users have had for years. =D

> 
2 - this will delete the virus and windows files on the computer and install ubuntu? (I don't care for the files on the laptop)
[/quote]
Logically - yes

Technically - the data will most likely be overwritten during the installation, even if the data was still present, the filesystem that linux installs has no idea that that data is there and the only way to get that data is to use a recovery program, but even then, Windows viruses don't run on Linux. (Maybe a bit overkill on that one haha)

---

### Post by Jeffrey Kang on 2011-05-15
Thank you everyone for prompt responses and clear explanations. Hopefully, this is the last message I have to write for help.

---

### Post by slooksterpsv on 2011-05-15
> **Jeffrey Kang said:**
> Thank you everyone for prompt responses and clear explanations. Hopefully, this is the last message I have to write for help.

Whether it is or not, we're glad to help you out =D. Linux, especially Ubuntu is a strong community that loves to help others out =D.

---

### Post by Jeffrey Kang on 2011-05-15
> **Rex Bouwense said:**
> 
If you have a good download, then burn the ISO to a CD at the lowest speed possible.

Is there a reason for burning it at the lowest speed? Maybe to decrease the probability of errors while writing the disc?

---

### Post by slooksterpsv on 2011-05-15
> **Jeffrey Kang said:**
> Is there a reason for burning it at the lowest speed? Maybe to decrease the probability of errors while writing the disc?

That's exactly it, reduces the amount of errors. Burning too fast can cause the speed to spin too fast and not get all the data trying to be written to it, especially if the drive is bumped, moved, etc. it basically "corrupts" the data.

---

### Post by Johnley on 2011-05-15
exactly. the slower, the better. i prefer writing to USB drives, but thats a whole other mammal.

---

### Post by Hedgehog1 on 2011-05-15
To keep the size of the install down to a single CD, there is not any fancy error-correction when booting from the CD.  Burning at the slowest speed gives you the best change to read it without errors during boot.

It is a 'better safe than sorry' thing.

The Hedge

:KS

---

