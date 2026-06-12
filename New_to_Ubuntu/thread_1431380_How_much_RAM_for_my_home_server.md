---
title: "How much RAM for my home server?"
date: 2010-03-16
forum: New to Ubuntu
---

### Post by busydoingnothing on 2010-03-16
I'm buying parts to rebuild my server. I was initially going to use old hardware but ran into some issues, so I'm starting fresh with an AMD II X2 240, GIGABYTE GA-770TA-UD3 mobo, and Asus EN8400GS vid. I'm going to be running a software RAID-1 (2x 500GB) and RAID-5 (3x 1TB).

This system will serve as a backup server, media host, file storage, video encoding, DVD burning/ripping. I'll be running Ubuntu 9.10 Desktop. It'll be installed to a CompactFlash card with the temp space stored on ramdisk.

Will 1GB RAM be enough? I'm trying to be cheap. 2GB will obviously double the RAM cost.

---

### Post by LowSky on 2010-03-16
you want to use it for video encoding, get 4GB. 
DDR3 1600 @4GB is about $110

Sad because 6 months ago is was under $80

---

### Post by QIII on 2010-03-16
32 or 64 bit?

If you are doing video encoding and the like, you need as much memory and CPU power (your x2 should suffice, although a x4 might do better...)

If you are going to use a 32 bit OS, remember that you are limited to 4GB of memory (of which only ~3.27 will be usable).  With a 64 bit OS, you can address 16 exabytes of memory, but good luck trying to even find that much at all Office Depots within a 30 mile radius ;)

In fact, I wouldn't recommend a 32 bit OS for video encoding unless you like a lot of coffee.  You'll be drinking several cups while you wait.

---

### Post by Baneblade on 2010-03-16
1GB will be just fine for everything except your video encoding. If you can offload that process to another machine and then transfer the files over that will work. Otherwise if you must use that machine for encoding, either give it more RAM, or be prepared to wait a LONG time.

---

### Post by busydoingnothing on 2010-03-16
Ah, 4GB! I understand the-more-the-better, but is 4GB absolutely necessary? I have 2GB on my E6600 desktop that I currently use for video encoding, and that seems to be fine (eh, it takes about 6 hours to encode a 1hr30min AVCHD file from my camcorder to either a h264 or DVD video). Encoding will mostly be an overnight/lower priority process anyhow. So the processor will be okay...I know I can get more if I spend more, but I'm not that hard-up for the extra performance.

I guess the price for 4GB isn't *too* bad. [TigerDirect]("http://www.tigerdirect.com/applications/SearchTools/item-details.asp?Sku=O261-6258&SRCCODE=LINKSHARE&cm_mmc_o=-ddCjC1bELltzywCjC-d2CjCdwwp&AffiliateID=Es5Ekr9eEBk-keGLOH4Cjmc63kjiTfjkZA") has a 4GB DDR3-1333 for $79 after rebate.

32bit versus 64bit is the other question...should I go 64bit then? I came across [this thread]("http://ubuntuforums.org/showthread.php?t=368607"). Looks like I have some reading to do.

---

### Post by mcduck on 2010-03-16
> **busydoingnothing said:**
> Ah, 4GB! I understand the-more-the-better, but is 4GB absolutely necessary? I have 2GB on my E6600 desktop that I currently use for video encoding, and that seems to be fine (eh, it takes about 6 hours to encode a 1hr30min AVCHD file from my camcorder to either a h264 or DVD video). Encoding will mostly be an overnight/lower priority process anyhow. So the processor will be okay...I know I can get more if I spend more, but I'm not that hard-up for the extra performance.

I guess the price for 4GB isn't *too* bad. [TigerDirect]("http://www.tigerdirect.com/applications/SearchTools/item-details.asp?Sku=O261-6258&SRCCODE=LINKSHARE&cm_mmc_o=-ddCjC1bELltzywCjC-d2CjCdwwp&AffiliateID=Es5Ekr9eEBk-keGLOH4Cjmc63kjiTfjkZA") has a 4GB DDR3-1333 for $79 after rebate.

32bit versus 64bit is the other question...should I go 64bit then? I came across [this thread]("http://ubuntuforums.org/showthread.php?t=368607"). Looks like I have some reading to do.

If you are happy with encoding the files overnight then 1GB of RAM will definitely be enough for your purposes. Besides, you can always add more at later time if you feel like you need it.

64-bit version would still be a good option, you are not really losing anything if you go for the 64-bit version but it will definitely give you a nice speed boost when encoding video.

---

### Post by busydoingnothing on 2010-03-16
Thanks for the input guys. I'll go with 1GB for now and upgrade later if I need more.

---

### Post by egalvan on 2010-03-16
> **QIII said:**
> 32 or 64 bit?
**If you are going to use a 32 bit OS, remember that you are limited to 4GB of memory (of which only ~3.27 will be usable).**
With a 64 bit OS, you can address 16 exabytes of memory, but good luck trying to even find that much at all Office Depots within a 30 mile radius ;)

Such a new set-up is almost certain to be PAE-enabled, so using a PAE-enabled 32bit kernel will eliminate this "limit".

I use Hardy 8.04 **Server**, 32bit software, on 64bit hardware,
PAE-enabled, and it "sees" 8GB just fine.
Installed the Gnome suite. No problems.
Learned this trick form the Hardy Server Community Pages.



> In fact, I wouldn't recommend a 32 bit OS for video encoding unless you like a lot of coffee.  You'll be drinking several cups while you wait.


Agreed. The few tests that I have seen and consider reliable all gave a big thumbs-up to such tasks as encoding, as far as gaining performance with 64bit.

---

### Post by QIII on 2010-03-16
With PAE enabled, 64GB is addressable.

PAE takes a performance hit, however.

---

### Post by The Real Dave on 2010-03-16
Try it with 1Gb. You'll soon see if you need more or not ;) My server has only 384Mb of RAM, with a media server, LAMP stack, NFS, rTorrent, Samba, Squid and some monitoring software for 4 computers, and Apt-Cacher-NG. It only ever uses around 260Mb, with 60-80Mb of that being swap :)

I'd go 64bit, seeing as your hardware supports it. There's no real reason not to. It'll be quicker, albeight with using slightly more RAM.

---

