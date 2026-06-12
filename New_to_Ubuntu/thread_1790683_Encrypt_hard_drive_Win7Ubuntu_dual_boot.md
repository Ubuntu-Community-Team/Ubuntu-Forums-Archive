---
title: "Encrypt hard drive: Win7/Ubuntu dual boot"
date: 2011-06-25
forum: New to Ubuntu
---

### Post by llmunro on 2011-06-25
Hi,

I recently had my Ubuntu netbook stolen out of my car.  Obviously, its too late to do anything about it now, but I'm interested in using TrueCrypt to encrypt another laptop I own.  My remaining laptop dual boots Ubuntu and Win 7.  I'm just not sure how to go about encrypting it with the two operating systems...do I have to encrypt the partitions or can I encrypt the entire hard drive?  Does anyone have experience with this?

Any ideas and suggestions appreciated.

Best,
Lisa

---

### Post by Paqman on 2011-06-25
I believe some of the higher end versions of Win 7 support full system encryption natively (called Bitlocker I think?). If you've not got a version that supports this then you may need Truecrypt after all.

As for Ubuntu encrypting your home folder is an option during installation. I have the home folder on my netbook encrypted, and it's completely hassle free. Definitely recommended.

---

### Post by gordintoronto on 2011-06-25
You encrypt partitions. (Or create Truecrypt "volumes," which are files which act like a folder. Just be sure you unmount the volume before you shut down.

---

