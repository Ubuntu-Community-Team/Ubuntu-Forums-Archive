---
title: "Brasero in Ubuntu 9.10 has made me waste 4 CD-Rs it never finishes burning"
date: 2009-11-21
forum: New to Ubuntu
---

### Post by samsamros on 2009-11-21
They should get brasero off ubuntu it sucks so bad now... I burned a music CD once it didn't finish burning although it said it had already finished and it was 100% done but the CD was still spinning I could hear it.. I waited nothing happened so I decided to eject the CD, it was damaged nothing could read the piece of crap. I did it 4 times thinking it was an error... first i tried with the upgrade (9.10) but because the upgrade was one of the mos horrible things i have done to my computer i decided to go fresh. now I HAVE THE SAME PROBLEM the cd does not eject when finished and does not finish the project... HELP!!!! thank you in advance.

---

### Post by camaron1 on 2009-11-21
This is why I now use K3b

---

### Post by samsamros on 2009-11-21
> **camaron1 said:**
> This is why I now use K3b

I started using it to burn dvds but also gave me a problem it said something like no support for that option.... but i haven't tried to burn an audio CD i'll keep you posted on that one

---

### Post by Muskegman on 2009-11-21
I also tried Brasero and never had any luck with it. I also use K3b, I have used it to burn iso images with no problems at all and I have also burnt music cd's with it, without any problems what so ever.

K3b is definatley the way to go.;)

---

### Post by mvalviar on 2009-11-21
Experienced problems with brasero too in JJ and KK. I'm using k3b too.

---

### Post by samsamros on 2009-11-21
well i've also experienced problems with k3b: when burning a video dvd this appears:
Devices
-----------------------
HL-DT-ST DVD+-RW GSA-S10N A103 (/dev/sr0, CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD-R DL, DVD+R, DVD+RW, DVD+R DL) [DVD-ROM, DVD-R Sequential, DVD-R Dual Layer Sequential, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R, Restricted Overwrite] [%7]

K3b::IsoImager
-----------------------
mkisofs print size result: 0 (0 bytes)

System
-----------------------
K3b Version: 1.68.0
KDE Version: 4.3.2 (KDE 4.3.2)
QT Version:  4.5.2
Kernel:      2.6.31-14-generic

Used versions
-----------------------
mkisofs: 1.1.9

mkisofs
-----------------------
/usr/bin/genisoimage: No such file or directory. Failed to open VIDEO_TS.IFO
/usr/bin/genisoimage: Can't open VMG info for '/tmp/kde-samuel/k3bVideoDvd0/'.
/usr/bin/genisoimage: Unable to parse DVD-Video structures.
/usr/bin/genisoimage: Could not find correct 'VIDEO_TS' directory.
Possible reasons:
  - VIDEO_TS subdirectory was not found on specified location
  - VIDEO_TS has invalid contents

mkisofs calculate size command:
-----------------------
/usr/bin/genisoimage -gui -graft-points -print-size -quiet -volid Two.For.The.Money[2005]DvDrip[En -volset  -appid K3B THE CD KREATOR (C) 1998-2007 SEBASTIAN TRUEG -publisher  -preparer  -sysid LINUX -volset-size 1 -volset-seqno 1 -sort /tmp/kde-samuel/k3bS11198.tmp -no-cache-inodes -udf -iso-level 1 -path-list /tmp/kde-samuel/k3bs11198.tmp -dvd-video -f /tmp/kde-samuel/k3bVideoDvd0

also:
[IMG]http://i705.photobucket.com/albums/ww59/samsamros/Screenshot-1-3.png[/IMG]

---

### Post by Hairy_Palms on 2009-11-26
i gave up on brasero about 3 releases ago, i quickly learnt it made more coasters than i could find uses for.

---

### Post by beast2k on 2009-11-26
At least yours will start mine cant even get started. I had to install K3B

---

### Post by lotharmat on 2009-11-26
n00b question:

Is K3d for KDE or GNOME or both

Please can someone explain what the ramifications are of installing KDE apps on a gnome system.

Cheers

---

### Post by MelDJ on 2009-11-26
> **lotharmat said:**
> n00b question:

Is K3d for KDE or GNOME or both

Please can someone explain what the ramifications are of installing KDE apps on a gnome system.

Cheers

you can use it for both. if you are using gnome, you can install k3b but must install some kde libraries too

---

### Post by lotharmat on 2009-11-26
> **MelDJ said:**
> you can use it for both. if you are using gnome, you can install k3b but must install some kde libraries too

So it won't install the whole of KDE and the libraries will be installed as dependencies?

---

### Post by Shazaam on 2009-11-26
Did everyone forget Gnomebaker?
I have a couple of old cd/rw's that Brasero refuses to blank/write to but Gnomebaker works fine.

---

### Post by Bartender on 2009-11-26
> **lotharmat said:**
> So it won't install the whole of KDE and the libraries will be installed as dependencies?

No, you won't get the entire KDE GUI.  Just the necessary bits and pieces.  I don't know if that means 1% of the entire KDE package or 10% or what...  

I don't like installing bits and pieces of KDE.  I cringe at the idea of installing WINE.  

But AFAIK no problems have resulted from doing these things, and sometimes you just need to take the chance to get the tool you want.

EDIT: Brasero has been pretty trustworthy for me.  Must be my clean living ;)

---

### Post by JohnnyVW on 2009-11-26
> **Shazaam said:**
> Did everyone forget Gnomebaker?
I have a couple of old cd/rw's that Brasero refuses to blank/write to but Gnomebaker works fine.

+1

Like others here, Brasero makes great coasters for me.  I use Gnomebaker with no problems.

---

