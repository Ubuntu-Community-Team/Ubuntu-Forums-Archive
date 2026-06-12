---
title: "Boot/install problem"
date: 2009-07-11
forum: New to Ubuntu
---

### Post by madurst on 2009-07-11
I am a new user to linux, coming from windows. I dowloaded the iso for 9.04 and burt it onto a cd-rw fine. The files come up when i look into the cdrw through windows, not just the iso file.
 
on startup, i get to the graphics ubuntu screen, select my language (which after the 30 second timer i have to alt control delete to restart my computer cause it freezes), but the only options that work are the "test memory" and the "boot from first hard disk" options. The three other options i select result in my cd disc reading light comes on, but i can hear and feel that the cd isnt spinning after a few seconds, and eventually the keyboard locks up and makes the beeping noise when i push on any key other than alt control delete to restart. I have tried to play around with the boot parameters wiht no luck. I tried to reburn the iso once, but I guess I'll try again and check back. My current system is:
 
Gateway laptop
Mobile AMD athlon 64
processor 4000+
2.59 GHz, 1GB ram
ATI mobility radeon X600 graphics card
 
I've looked around these forums for a while and not many people seemed to get snagged on this issue, so I dont know if I overlooked something simple or not. Any ideas? Thanks.

---

### Post by egalvan on 2009-07-11
Does the "test memory" option work?
have you run it for an hour or so?

Can you run the "test media" option?
This will test the file integrity of the CD.

CD-RW are not always the best to use.

Make SURE is is completely erased.

And try a CD-R if possible, burned at 8-12x max speed.

And your drive may be defective...
try the media on another computer...

---

### Post by boblemur on 2009-07-11
hey check your ISO first:

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)


then if that comes up clear, burn the iso again at low speed, and you may need the amd64 ISO so download and try with that.

---

### Post by madurst on 2009-07-12
I did the test memory option and it  took about 30 minutes to go through the 8ish different tests of memory... I'm traveling and have a slow internet connection, so i'll look for and download a windows checksum for the file i downloaded. anything from the boot screen past the language screen that seems to require the cd to run fails, so ill get a cd r when i get in and re-download and burn the image. I was using the generic CDburner xp program to wipe the cd-rw, not just window's cd-rw cleaner. Hopefully next time i post here ill be doing so off the ubuntu platform.

If my drive is defective, is there a way to boot and install off a flash drive?

---

### Post by madurst on 2009-07-13
Just got it working :). I redownloaded the iso and burnt it to a cdr at 2x speed and then it worked fine. Thanks for your help

Matt

---

### Post by LewRockwell on 2009-07-13
> **madurst said:**
> Just got it working :). I redownloaded the iso and burnt it to a cdr at 2x speed and then it worked fine. Thanks for your help

Matt

yes, you've got to have a good MD5 checksum and it's a must to burn it slow and on a clean blank CD (non-rewritable)

even then sometimes the original blank is just not right somehow and we still have to burn them again...

.

---

### Post by mikechant on 2009-07-14
Given the problems that people frequently have with CDs, I'd say that everyone whose hardware supports boot from flash devices (USB key, SD card etc.) should be installing from these instead of CD. It should be faster as well as more reliable.

---

### Post by LewRockwell on 2009-07-14
> **mikechant said:**
> Given the problems that people frequently have with CDs, I'd say that everyone whose hardware supports boot from flash devices (USB key, SD card etc.) should be installing from these instead of CD. It should be faster as well as more reliable.

How would you know if your data on the thumb drive became corrupted?

Once I have a known good CD/DVD I feel most secure that it's data will not be altered.

.

---

### Post by mikechant on 2009-07-15
> How would you know if your data on the thumb drive became corrupted?
I guess you could checksum it, I haven't tried. I'm happy from my experience that if the flash device writes OK (see below) then it'll read back OK.

> Once I have a known good CD/DVD I feel most secure that it's data will not be altered.

CDs and DVDs go bad in various ways. I've got commercially pressed CDs which were OK and are now totally unreadable - when you hold them up to the light you can see tiny holes in the recording medium ('CD rot'). They can get scratched and the chemical dyes in recordable CDs/DVDs can deteriorate.

Flash devices wear out eventually but their most common failure mode is to become unwritable - but still readable without errors/corruption.

My experience having used both (good quality) CDs and SD cards is that the CDs are a lot more trouble. Also, installing from and running from LiveCDs seems to put a lot of stress on the CD/DVD drive - I want to save my optical drive for when I actually need to use it - ripping CDs/DVDs and writing DVDs for my standalone DVD players.

Also, a lot of laptops and all netbooks (as far as I know) don't have built-in optical drives but they do all have USB slots and lots have SD slots as well.

And it's a lot more convienient to carry a flash device around with a Live version of Ubuntu than to carry a CD around. And you can get whatever capacity you need - you're not limited to 700Mb or 4.7Gb etc.

---

### Post by carml on 2009-07-15
@ mikechant
Not all Pc can start from a thumb drive ;) The better solution to follow your idea wuold be to carry a cd and a thumb drive. ):P

---

