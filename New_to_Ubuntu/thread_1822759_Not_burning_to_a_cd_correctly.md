---
title: "Not burning to a cd correctly"
date: 2011-08-11
forum: New to Ubuntu
---

### Post by chantendo on 2011-08-11
Whenever I burn Ubuntu to a cd, not all the files burn to the disk. I don't know what I'm doing wrong, please help

---

### Post by amjjawad on 2011-08-11
> **chantendo said:**
> Whenever I burn Ubuntu to a cd, not all the files burn to the disk. I don't know what I'm doing wrong, please help

Are you trying to create Ubuntu LiveCD???
[https://help.ubuntu.com/community/LiveCD](https://help.ubuntu.com/community/LiveCD)

Or 

you are trying to do this:[https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization)

Please be more specific :)

---

### Post by Dright on 2011-08-11
I don't exactly know what I'm doing yet, but I know that when I was making my livecd I accidentally burnt the .iso to my disk instead of writing the image to the disk (which are in fact two different things).

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
should help you with that if that truly was your problem.

Use the part with InfraRecorder.

---

### Post by nomko on 2011-08-11
> **chantendo said:**
> Whenever I burn Ubuntu to a cd, not all the files burn to the disk. I don't know what I'm doing wrong, please help
 
Which burning application are you using? And which Ubuntu version you're using??

---

### Post by Chopped on 2011-08-11
> **Dright said:**
> I don't exactly know what I'm doing yet, but I know that when I was making my livecd I accidentally burnt the .iso to my disk instead of writing the image to the disk (which are in fact two different things).

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
should help you with that if that truly was your problem.

Use the part with InfraRecorder.


Then all you should have to do is make another disc, but instead write the image to the disc. Once it is done then click on your CD drive and it should show a bunch of files on the CD, instead of just the iso. My recommendations to burn your disc is either Roxio or IMG Burn.

---

### Post by chantendo on 2011-08-11
I'm not sure if I'm making a live cd, I just followed the tutorial on the download page and this page: [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto). I'm using Infrarecorder and Ubuntu 10.04

---

### Post by x-D on 2011-08-11
> **chantendo said:**
> I'm not sure if I'm making a live cd, I just followed the tutorial on the download page and this page: [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto). I'm using Infrarecorder and Ubuntu 10.04

If you're trying to download Ubuntu? And if you're trying to burn an ISO, I can say you're definitely trying to make a Live CD/DVD/Disk :)

:guitar:

---

### Post by Rex Bouwense on 2011-08-11
Yes you are making a live CD.  Can you boot from it? Change the boot sequence in your BIOS to boot from the CD before your hard drive.  If you cannot then you probably had a bad download (did you run an md5sum on the download?) or a bad burn (try it again and this time at the slowest speed).
Here are a few sites that may be of interest:
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

---

### Post by chantendo on 2011-08-11
Oh and I've tried this quite a few times and have checked the hash code each time. The disk is RW and has been erased before, could that be the problem?

---

### Post by chantendo on 2011-08-11
My enter key's broken, so I can't change the boot order, but I've tried the boot from cd option and it always says there's an error

---

### Post by Rex Bouwense on 2011-08-11
The disk being RW should have no bearing but go ahead and try a different CD.  I use the cheapest ones that I can find and they work great.  Can you boot from the one that you have created?  If not how far in the sequence does it get before it fails?  Are you getting a failure code or message?

---

### Post by chantendo on 2011-08-11
When the computer starts it just goes straight to Windows, but from the boot cd option on the disk in Wubi, it gets about 1/4 of the way before it says to read wubi-10.04.3-rev192.log, which is in my local temp folder

---

### Post by amjjawad on 2011-08-11
> **chantendo said:**
> When the computer starts it just goes straight to Windows

If you are booting from a CD then you need to check your BIOS and make sure your CD-DRIVE is the first device to boot from.

---

### Post by cgroza on 2011-08-11
> **amjjawad said:**
> If you are booting from a CD then you need to check your BIOS and make sure your CD-DRIVE is the first device to boot from.
On many computers, Del, F11, F10, F12 bring up a boot menu at the BIOS screen. Just another way to do it.

---

### Post by amjjawad on 2011-08-12
> **cgroza said:**
> On many computers, Del, F11, F10, F12 bring up a boot menu at the BIOS screen. Just another way to do it.

Or F2 ;)

---

