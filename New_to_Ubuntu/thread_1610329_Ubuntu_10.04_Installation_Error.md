---
title: "Ubuntu 10.04 Installation Error"
date: 2010-10-31
forum: New to Ubuntu
---

### Post by D3SI on 2010-10-31
Burned the Image on DVD-RW

(Max Speed for DVD-RW 4x)
Software used: ImgBurn

booted it from DVD and got this error

(See Attachment)

what do i need to do?

---

### Post by Rex Bouwense on 2010-10-31
First, did you get a good md5sum from the download?  Did you burn the ISO at the lowest speed possible?  You may have got a bad burn.  If the md5sum was good, try another burn at a lower speed.

---

### Post by D3SI on 2010-10-31
i burned it at Max Speed  :|

should i select x1 speed?

---

### Post by Rex Bouwense on 2010-10-31
If you had a good md5sum, yes burn it at a lower speed.

---

### Post by D3SI on 2010-10-31
downloaing the Image again just to make sure..

How do I check md5sum?

---

### Post by Rex Bouwense on 2010-10-31
Check here, [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM) for how to do it and here, [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes) to compare the hashes.

---

### Post by andymorton on 2010-10-31
I got the 'unknown keyword in configuration file' error a short time ago. I solved it by opening the syslinux.cfg file and deleting the letters 'ui' from one of the lines of text. I can't remember which one it was but it wasn't hard to find. I'm sorry I can't be specific

I'm not sure whether this solve your problem but it might be worth a try.  

andy

---

### Post by D3SI on 2010-10-31
Thank You.

checked it and its same...

Burning Disc now..

---

### Post by D3SI on 2010-10-31
tried installing... when DVD booted all i got was this.. (See Atatchment)

and after that Windows loaded up (after like 2 minutes)

---

### Post by Rex Bouwense on 2010-10-31
Sorry it so long to get back to you.  I was trying to locate some information on using DVDs instead of CDs.  I could not find anything.  That may be the problem but I doubt it.  Booting from a live CD should get you further than the purple screen unless you got a bad burn.  You already know that you got a good download so perhaps it was a bad burn.  That's all I got.  At least you get a bump out of this.

---

### Post by D3SI on 2010-10-31
Thanks for getting back...

tried USB Flash Drive but it didn't show up in BIOS

burning it on DVD-R now instead of RW @ x2.4 speed

---

### Post by amjjawad on 2010-10-31
IMHO, I'd recommend to use a Flash USB/Pendrive instead.
I see you tried to make many copies so far and nothing happened, same result.

From Ubuntu's website, there's a HOWTO create LiveUSB. It's faster than CD/DVD.

If you don't have a Flash USB/Pendrive, I suggest to use CD.

Just double check the MD5SUM once more. I'm sure you have set the BIOS to boot from your CD/DVD so we shouldn't worry about that.

Good luck!

---

### Post by amjjawad on 2010-10-31
> **D3SI said:**
> Thanks for getting back...

tried USB Flash Drive but it didn't show up in BIOS



I saw this after posting mine.

Is it an old machine? does your BIOS have the option to boot from USB anyway? if not, there's always plan B

[http://blog.brothersoft.com/2008/12/09/boot-computer-from-usb-or-cdrom-even-if-bios-not-supported-using-plop/](http://blog.brothersoft.com/2008/12/09/boot-computer-from-usb-or-cdrom-even-if-bios-not-supported-using-plop/)

---

### Post by Rex Bouwense on 2010-10-31
> **D3SI said:**
> Thanks for getting back...

tried USB Flash Drive but it didn't show up in BIOS

burning it on DVD-R now instead of RW @ x2.4 speed

Sometimes, I don't know why, the flash drive shows up as another hard drive.  Check that.  I guess it depends upon BIOS, the computer, and the type of flash drive, because if your computer is relatively new it should have the capability of booting from a flash drive.

---

### Post by Rex Bouwense on 2010-10-31
Is there a reason that you are not using CDs to burn this ISO?  They are really cheap and make great sun-catchers when I screw up a burn.  I read or thought I read somewhere that it is harder to install from a DVD but I cannot find it now.

---

### Post by D3SI on 2010-10-31
i ran out of CDs and cant get them until end of the week (Shopping Day)

BIOS does have load from removable device but Flash Drive just doesn't show up there.

---

