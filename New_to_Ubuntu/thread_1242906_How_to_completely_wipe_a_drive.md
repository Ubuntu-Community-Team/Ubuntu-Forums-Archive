---
title: "How to completely wipe a drive?"
date: 2009-08-17
forum: New to Ubuntu
---

### Post by bettyhills on 2009-08-17
Is there a way in Ubuntu to completely wipe a drive of all information so that it cannot be restored before removing the drive from a linux system?

---

### Post by Bachstelze on 2009-08-17
```
sudo dd if=/dev/zero of=/dev/sda
```

Use with care. ;)

---

### Post by thomz92 on 2009-08-17
are you talking about an external hardrive? internal? flash drive? what do you want to do with it, format it?

---

### Post by Technoviking on 2009-08-17
I use DBAN ([http://www.dban.org/](http://www.dban.org/)) to wipe hard drives before donating or trashing them. Last I heard it was the suggested disk wipe tool of the U.S. Dept. of Defense.

T-V

---

### Post by egalvan on 2009-08-17
+1 for DBAN.

I've used it for almost three years.

Works great.

---

### Post by mcduck on 2009-08-17
I'd go for this instead of using /dev/zero:

```
sudo dd if=/dev/urandom of=/dev/sda bs=1k
```

Writing zeroes to drive doesn't empty it very well, writing random data produces better results. Although even with random data most instances that handle confidential data have policies that require you to do this several times..

Also it's nicer to use higher block size, speeds up the process quite a lot..


..although DBAN is a good choice as well. :)

---

### Post by bettyhills on 2009-08-17
I want to replace the second hard drive in the system with a larger one.  It is a 10gb HDD.  Before doing so I would like to wipe it totally so that data cannot be retrieved and then give it away on the local FreeCycle.

Can you give me the exact command to use so that I do not wipe my primary 80gb Ubuntu system drive, just the secondary 10gb HDD?

TIA

---

### Post by egalvan on 2009-08-17
> **bettyhills said:**
> I want to replace the second hard drive in the system with a larger one...
I would like to wipe it totally so that data cannot be retrieved...

Can you give me the exact command to use so that I do not wipe my primary 80gb Ubuntu system drive, just the secondary 10gb HDD?

TIA

The most secure way is to leave only the drive you want to wipe/erase connected...

use something such as DBAN

dban.org

disconnect (power and data) the drive  you want to save (80GB primary)
leave just the drive you want to wipe/erase (10GB secondary)

use dban to wipe the drive

or use a Linux LiveCD, such as the one you used to install Linux originally.

---

### Post by MrWES on 2009-08-17
> **egalvan said:**
> +1 for DBAN.

I've used it for almost three years.

Works great.


Which version are you using? Also, it that automatic, that is once the DBan CD boots, it'll wipe the drive. Or does it ask you which drive or drives you want to wipe?

Bill

---

### Post by coldReactive on 2009-08-17
+1 again for DBAN

---

### Post by Technoviking on 2009-08-17
> **MrWES said:**
> Which version are you using? Also, it that automatic, that is once the DBan CD boots, it'll wipe the drive. Or does it ask you which drive or drives you want to wipe?

Bill

I will ask you which drive to wipe. 

T-V

---

### Post by misswham on 2009-08-17
I always used d-ban also.

---

### Post by red_spyder on 2009-08-17
Definately DBAN. I use it on all my hard disks before I trash them. Do they really use it in U.S. Defense Department?

---

### Post by HermanAB on 2009-08-17
Howdy,

If you want to erase most data from a disk then dban or dd are good.  If you want to erase the space between the tracks and bad sectors as well, then you need to activate the erase routine that is built into the drive controller.  That can be done with hdparm.

The DOD erase thing is kinda mythical, but for reuse at the same classification level, you need to overwrite the media three times.

If you need to sanitize secret media, then you need to destroy the disk with a metal shredder or a sledge hammer.  The defence department collects the destroyed disks and throws them into a blast furnace for good measure.

---

### Post by H2SO_four on 2009-08-18
+1 for DBAN.   Or if you are really nuts you can try thermite!

[http://www.youtube.com/watch?v=k-ckechIqW0](http://www.youtube.com/watch?v=k-ckechIqW0)

---

### Post by MrWES on 2009-08-18
> **HermanAB said:**
> Howdy,

If you want to erase most data from a disk then dban or dd are good.  If you want to erase the space between the tracks and bad sectors as well, then you need to activate the erase routine that is built into the drive controller.  That can be done with hdparm.

The DOD erase thing is kinda mythical, but for reuse at the same classification level, you need to overwrite the media three times.

If you need to sanitize secret media, then you need to destroy the disk with a metal shredder or a sledge hammer.  The defence department collects the destroyed disks and throws them into a blast furnace for good measure.

+1 for the 5 pound sledge hammer -- free and open source :)

---

### Post by LewRockwell on 2009-08-18
> **HermanAB said:**
> Howdy,

If you want to erase most data from a disk then dban or dd are good.  If you want to erase the space between the tracks and bad sectors as well, then you need to activate the erase routine that is built into the drive controller.  That can be done with hdparm.

The DOD erase thing is kinda mythical, but for reuse at the same classification level, you need to overwrite the media three times.

If you need to sanitize secret media, then you need to destroy the disk with a metal shredder or a sledge hammer.  The defence department collects the destroyed disks and throws them into a blast furnace for good measure.

one may also procure a copy of Parted Magic which contains the "Secure Erase" function amongst it's utility offerings

[http://partedmagic.com/](http://partedmagic.com/)

You can learn more about this function here:
[http://cmrr.ucsd.edu/people/Hughes/SecureErase.shtml](http://cmrr.ucsd.edu/people/Hughes/SecureErase.shtml)

Older Article About Secure Erase(beware: with some bad info and links)
[http://blogs.zdnet.com/storage/?p=129](http://blogs.zdnet.com/storage/?p=129)

More information regarding using "Secure Erase" with caution:
[http://forum.piriform.com/index.php?showtopic=22055&st=0&p=136595&#entry136595](http://forum.piriform.com/index.php?showtopic=22055&st=0&p=136595&#entry136595)

This topic is so important that the above link, to a public statement on a public forum is being quoted here for duplicity, simplicity, and longevity.> Fact is that Secure Erase is in face a component of the ATA specification and is integrated into all standards compliant ATA devices in production since 2001. This is not just for SSD technology but also applies to all ATA, IDE, PATA, and SATA magnetic media based hard drive devices as well.

Created by IBM in 1994 as a feature for the TravelStar line of drives, the Center for Magnetic Recording Research at the University of California San Diego had at the insistence of the NSA developed the current version of the Secure Erase technology.

Secure Erase is embedded in the drive controller microcode and is initiated by an externally issued command sequence. Once initiated, SE uses an optimized single pass process that addresses all regions of the storage media, including the Protected Service Areas (when properly launched using compatible hardware). Protected service areas include G-List, Host Protected Area, and the Device Control Overlay (search Wikipedia for a detailed description of the role of each component of the PSA).

Despite the fact that it is launched by external command, and is a highly effective PURGE level sanitization technology it can not be reliably launched in on most host equipment due to host controller protection of the HPA, and the fact that many BIOS manufacturers inhibit SE from being launched due to security concerns. The issue being that if virus or malware were to initiate SE, the target computer would be purged rapidly, and with no hope for recovery.

It is for this reason that Secure Erase is not being exploited en masse by every software vendor. Effectively, the only truly effective means to purge using SE is by using purpose built hardware such as the Digital Shredder manufactured by Ensconce Data Technology ([www.deadondemand.com](www.deadondemand.com)) or other dedicated appliance based solution.

For more information on SSD performance issues, an excellent paper can be found at [www.anandtech.com](www.anandtech.com) under the storage heading. The comments are well informed, and from the hip.. truly an excellent read.

If you want accurate and up to date guidance on developing policy for the destruction of digital data, I had co-authored a guide with Dr. gordon Hughes of the CMRR titled 'The best Practices for the Destruction of Digital Data' which is based on a review of all available guidance collected from Government, Academic, and vendor sources, as well as, input by industry and security experts. In this guide we present hardware considerations, classification concerns, and review acceptable (and unacceptable) practice... essentially all the tools one needs to create accurate and reliable data destruction policy.

The paper is available as a no charge download at [www.converge-net.com](www.converge-net.com), select English, and go to the news page to link to the download request form.

One last comment:

Don't be afraid to search "secure erase" to see the most current and up-to-date information

.

---

### Post by cascade9 on 2009-08-18
> **H2SO_four said:**
> +1 for DBAN.   Or if you are really nuts you can try thermite!

[http://www.youtube.com/watch?v=k-ckechIqW0](http://www.youtube.com/watch?v=k-ckechIqW0)

A really really big magnet works as well, but is slightly less fun than thermite.

---

### Post by raymondh on 2009-08-18
Counting all the dban recommendations ...... +10 for dban ;)

---

### Post by Bartender on 2009-08-18
If it's a 10GB HDD, it's probably noisy, slow, and very close to being worthless, even to a group that recycles PC's.

I vote hammer.

---

### Post by cascade9 on 2009-08-18
When I was working at a PC recyclers, they would use hdds down to 1-2GB (it fits win95/98, and thats typically what they put in the old 586 bangers) 

10GB isnt that bad at all...well, unless your used to SATA speeds and capacity

---

### Post by gpw1 on 2009-11-06
What are the steps for secure erasing/wiping an Intel SSD  using Ubuntu.

---

### Post by Paqman on 2009-11-06
AFAIK files on SSD's can't be totally securely wiped using any of the tools we currently have. The wear-leveling algorithms in the on-drive electronics mean that the OS can't write to any specific location.

Luckily however, they also don't require multiple-pass writes like magnetic drives might. A single pass write across the whole drive should nuke pretty much everything you've got on there.

---

