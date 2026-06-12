---
title: "Brasero Blanking Blanks! &gt;_&lt;"
date: 2010-09-21
forum: New to Ubuntu
---

### Post by zer010 on 2010-09-21
Ubuntu 10.04
I am trying to blank some DVD-RWs and DVD+RWs. I insert the disk, open Brasero, go to "Tools", and select "Blank Disk".  Everything seems to go fine, it says the disc has been blanked. Apparently, it's blanked TOO well because now Ubuntu doesn't even recognize the disk being re-inserted! WTF!? I've tried to find a fix for this, but everyone just says to just get a new app to handle burn/blank operations. Is there no fix? No one has worked on this problem? Is it standard operation to just pass the buck onto another app? If I get another app, should I even keep Brasero around? The thing that bugs me the most is that I've had VERY few problems with Ubuntu. Most things JUST WORK. Burn/Blank is a basic and standard operation in home computing, and I hope this can be rectified. 
Thanks in advance for any real help.

---

### Post by CFury on 2010-09-21
Looks like this has effected others as well.  Check this thread out, seems to have a solution there.

[http://ubuntuforums.org/showthread.php?t=1323930](http://ubuntuforums.org/showthread.php?t=1323930)

---

### Post by zer010 on 2010-09-21
I've read about this happening since Hardy. This has been an ongoing problem. I personally had no problems in Jaunty, but that is besides the point. I can't believe this problem has never been addressed. I guess a new app to deal with burn/blank jobs is in order. Should I keep Brasero around or is it safe to remove it?

I'm glad I ran into this problem before any of the many people I've told about Ubuntu have actually tried Ubuntu.  I think I should keep my mouth shut for a while. This is only one of a VERY, VERY few problems that I've had. Damn shame really.  Especially, since burn/blank jobs are essential to basic computing.

---

### Post by jtarin on 2010-09-21
> **zer010 said:**
> I've read about this happening since Hardy. This has been an ongoing problem. I personally had no problems in Jaunty, but that is besides the point. I can't believe this problem has never been addressed. I guess a new app to deal with burn/blank jobs is in order. Should I keep Brasero around or is it safe to remove it?

I'm glad I ran into this problem before any of the many people I've told about Ubuntu have actually tried Ubuntu.  I think I should keep my mouth shut for a while. This is only one of a VERY, VERY few problems that I've had. Damn shame really.  Especially, since burn/blank jobs are essential to basic computing.
I've used Brasero, K3B and Gnome Baker in that order....I have never been satisfied with Brasero...it doesn't fit my needs.K3B I have used before on Slackware 13 and PCBSD with not one problem however on Ubuntu...not satisfactorly. I have finally settled on Gnome Baker to fulfill what needs I have for burning and copying in Ubuntu 10.04. (All these have been used and teted on the same equipment.)

---

### Post by JustinR on 2010-09-21
Hi,

Going to **Applications > Accessories > Terminal**:

```

sudo apt-get install dvd+rw-tools
dvd+rw-format -force 'CDROMDEVICE'

```

This should reformat your CD to the point of it being readable again.

'CDROMDEVICE' should be something like '/dev/sr0' without the quotes.

Good Luck!

---

### Post by zer010 on 2010-09-21
I have just installed both K3b and Gnomebaker. So far, I'm pleased with K3b because of it's speed at blanking. Gnomebaker was taking forever just to get to 4%!  I might re-evaluate Gnomebaker...

---

### Post by zer010 on 2010-09-21
Thanks Justin, I will try that.

---

### Post by zer010 on 2010-09-21
Using the terminal command, it says: 4.7GB DVD-RW media in Restricted Overwrite mode detected.
Will that cause a problem?

---

### Post by zer010 on 2010-09-21
I just used my Magnavox DVD recorder to blank a disc and it was recognized in Ubuntu as a "DVD Video Recording" disk. Retrying the terminal command: dvd+rw-format -force /dev/sr0, makes the disk undetectable again! WTF is wrong with this?! I hate to think I'll have to use Nero in Win to do my work... smh

---

### Post by zer010 on 2010-09-21
I just feel like such a fool telling everyone how great Ubuntu is, when it can't even properly format a disk! Damn! K3b didn't do it, terminal commands didn't even do it. Maybe I should wait the 3 hrs for Gnomebaker....if that even works?  I doubt it will, after what I've seen.

---

### Post by jtarin on 2010-09-22
There could be something wrong with your media.

---

### Post by zer010 on 2010-09-22
Media? As in the disk itself?

---

### Post by jtarin on 2010-09-22
> **zer010 said:**
> Media? As in the disk itself?Yes. Try to format and burn in Windows if you think its good media. I have problems with certain media at times working neither in Linux or Windows.

---

### Post by migs73 on 2010-09-22
> **CFury said:**
> Looks like this has effected others as well.  Check this thread out, seems to have a solution there.

[http://ubuntuforums.org/showthread.php?t=1323930](http://ubuntuforums.org/showthread.php?t=1323930)

Did you try this?

I assume you do this alot? As for it being a 'standard operation in home computing', I've never had to do it in my life!?!

---

### Post by zer010 on 2010-09-22
Yeas I have tried that. I will see if this disk cannot be formatted in WinXP using Nero. I just got a 30-day trial for Nero-Linux4 as well. I'll post back with the results.

---

### Post by gordintoronto on 2010-09-22
I'm with Migs73. I just throw in a RW disc with old stuff on it, and write new stuff on it. I don't see the point of blanking it.

---

### Post by Land Rover Series 3 on 2010-09-22
Hi,

I had exactly the same problem some time ago - you try to blank a dvd using Brasero and you end up with a blank dvd that is no longer recognised whatsoever! I spent a LONG time trawling through the forums without ever finding a solution that worked. I tried GnomeBaker but that didn't seem to be much better in my view.

Eventually I found that the easiest and most reliable thing to do was simply NEVER to manually blank a dvd. I found that Brasero works a treat if you just put in a dvd that already has something on it, and tell Brasero to copy your selected files to it. Brasero will then automatically erase the dvd before continuing, but it WILL continue and produce the finished dvd.

Hope that helps

---

### Post by zer010 on 2010-09-22
OK, so apparently there is no need to blank discs.  Maybe I'm just overly particular? Like always formating a HDD when installing a new OS. 
I gave my disks a second look over and I have found their condition unsatisfactory. I have found some that are 'like new'. I will start my testing all over again. I will say that Nero has been doing well, even if the disk is not in 'like new' condition.  

    On a side note: Why hasn't non-scratch technology transfered to optical disk media?  It's used extensively in touchscreen devices and sunglasses, but not for optical disks that can hold important data. Smells fishy to me.

---

### Post by Land Rover Series 3 on 2010-09-22
> **zer010 said:**
> OK, so apparently there is no need to blank discs.  Maybe I'm just overly particular? Like always formating a HDD when installing a new OS. 
I gave my disks a second look over and I have found their condition unsatisfactory. I have found some that are 'like new'. I will start my testing all over again. I will say that Nero has been doing well, even if the disk is not in 'like new' condition.  

    On a side note: Why hasn't non-scratch technology transfered to optical disk media?  It's used extensively in touchscreen devices and sunglasses, but not for optical disks that can hold important data. Smells fishy to me.

I'm not saying it's not a good idea to blank a cd/dvd before using it for something else. In fact, normally I would always do this as a matter of course. But in Ubuntu this can cause problems, so I don't do it. I don't think there's any real need to blank a cd/dvd before reusing it anyway, since the previous contents always seem to be gone and completely inaccessible once it's been written to. I trashed a whole series of brand new (only ever used once) dvds until I discovered how to overcome the problem, so I don't think it's anything to do with the surface quality. But if you want to start testing again please be prepared to possibly trash a few. Best of luck.

---

### Post by DavePlummer on 2010-09-22
I have seen a series of problems with Brasero over the past three releases. The situation is now so bad that I have removed Brasero in 10.04, using command line tools (wodim and genisoimage) for my disc burning needs. The situation is not much better in Maverick Meerkat.

---

### Post by blur xc on 2010-09-22
> **migs73 said:**
> 
I assume you do this alot? As for it being a 'standard operation in home computing', I've never had to do it in my life!?!

Me neither.  I've never even heard of "blanking disks" before.  The last time I formatted removable medial like that was WAY back in the dark ages of floppy disks.

To be honest, I didn't even know it was possible.  I always assumed optical disks were write once, toss it in the trash when you are done, ordeals (unless you set it up as a multi-session disk when burning, which never worked for me).

BM

---

### Post by CFury on 2010-09-22
Non-scratch tech isn't worth the cost for something produced on such a massive scale as optical media.  As a result it would drive up the price, apart from the fact I believe it's more effective on glass then plastics.  I don't know about you but I buy my media in spindles by the hundreds, not my iPhones.

---

### Post by cariboo on 2010-09-22
> **blur xc said:**
> Me neither.  I've never even heard of "blanking disks" before.  The last time I formatted removable medial like that was WAY back in the dark ages of floppy disks.

To be honest, I didn't even know it was possible.  I always assumed optical disks were write once, toss it in the trash when you are done, ordeals (unless you set it up as a multi-session disk when burning, which never worked for me).

BM

I do it all the time with CDR/W, especially seeing as CD media is getting hard to come by where I live.

---

### Post by jtarin on 2010-09-22
> **blur xc said:**
>  I always assumed optical disks were write once, toss it in the trash when you are done, ordeals (unless you set it up as a multi-session disk when burning, which never worked for me).

BMWhere is that pile of write-once-throw-away-disks at?:)

---

### Post by jtarin on 2010-09-22
> I do it all the time with CDR/W, especially seeing as CD media is getting hard to come by where I live.

I do too....in fact if it is only a CD-R....I will write on it with a Marks-A-Lot just to get an extra write out of it.

---

### Post by blur xc on 2010-09-23
> **jtarin said:**
> Where is that pile of write-once-throw-away-disks at?:)

my local landfill...

Does this mean that when a write fails, I can blank it and try again on the same disk?

BM

---

### Post by jtarin on 2010-09-23
> **blur xc said:**
> my local landfill...

Does this mean that when a write fails, I can blank it and try again on the same disk?

BM
The possibility exist. It's difficult to determine why a write failed sometimes.

---

### Post by zer010 on 2010-09-23
I just found this golden nugget of info in man growisofs: 

"Note that DVD+RW re-formatting procedure does not substitute for blank&#8208;
       ing. If you want to nullify the media, e.g. for privacy reasons, do  it
       explicitly with 'growisofs -Z /dev/dvd=/dev/zero'."

---

### Post by ragnaroek-hh on 2010-10-31
Do not worry about Brasero destroying your DVD-RW once you have used this tool for blanking the DVD.

If this has happend, you might check the dvd media information with

 ```
$ dvd+rw-mediainfo /dev/sr0
INQUIRY:                [your drive type]
GET [CURRENT] CONFIGURATION:
 Mounted Media:         13h, DVD-RW Restricted Overwrite

```you may change the restricted overwrite into the proper mode again with

```
$ dvd+rw-format -blank /dev/sr0

```and than you will read:

```
$ dvd+rw-mediainfo /dev/sr0
INQUIRY:                [xx]
GET [CURRENT] CONFIGURATION:
 Mounted Media:         14h, DVD-RW Sequential

```Afterwards, brasero will be able to process the DVD-RW again properly.

---

