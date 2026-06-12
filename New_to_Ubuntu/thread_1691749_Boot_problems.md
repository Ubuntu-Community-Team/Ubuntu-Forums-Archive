---
title: "Boot problems"
date: 2011-02-20
forum: New to Ubuntu
---

### Post by TriBlox6432 on 2011-02-20
I downloaded Ubuntu 10.10 64-bit and installed to a flash drive following canonicals commands.  When it boots, I get a black screen with options.  I click on Boot from USB (as opposed to install ubuntu to hard drive) and then I get a black screen with white text . . . .

Any ideas?

P.S. Is there any advantage to using 64-bit with only 3GB of RAM, or should I just use the 32-bit?

---

### Post by corncob on 2011-02-20
Now that you have it downloaded you might try using  System>Administration>Startup Disk Creator to install it to the pen drive.  If that doesn't work check the download for errors:
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
and download again if needed.
I never tried installing 64 bit to a pen drive.  I do have trouble with 64 bit on some things like my Canon MP640 printer.

---

### Post by Heliguy on 2011-02-20
> **TriBlox6432 said:**
> I downloaded Ubuntu 10.10 64-bit and installed to a flash drive following canonicals commands.  When it boots, I get a black screen with options.  I click on Boot from USB (as opposed to install ubuntu to hard drive) and then I get a black screen with white text . . . .
Please quote what Linux Ubuntu Distro your using because the Ubuntu Server dosent come with a GUI. Also when a Linux Distro boots up it flashes code like the matrix for a few seconds this is just the normal Linux boot up process and you should leave it to do its thing. IF it stops for a considerable amount of time then you may post the error in this thread and me or others will do the best to help you :)

> **TriBlox6432 said:**
> P.S. Is there any advantage to using 64-bit with only 3GB of RAM, or should I just use the 32-bit?
64-Bit is only useful when you have more then 4GB of RAM as it can address more then the limit of 4GB. So no you only need 32-bit

Good Luck :)

---

### Post by oldfred on 2011-02-20
Even with 3GB of RAM, 64 bit will be slightly better. But the more memory you have the better it is. I am running 64bit on my laptop with only 1.5GB without problems. That may be too small that the larger address size offsets the 64bit advantages, so I may not be ahead. But I boot 64 on my Desktop and I want the same configuration.

You may have video issues. If you hit a key as soon as it starts while the stick figure & keyboard are at the bottom, you should get a menu. Then try f6 and nomodeset.

---

### Post by Heliguy on 2011-02-20
Well i would argue about the compatibility of certain things aswell :)

---

### Post by mn_voyageur on 2011-02-20
> **Heliguy said:**
> Ubuntu Server dosent come with a GUI.

Am I missing something?  I did not read "server" in the OP.

I had a similar problem with an ATI video card.  My entire system would freeze. ([Start with #13]("http://ubuntuforums.org/showpost.php?p=10469514&postcount=13"))

As for 64-bit ... If you have a 64-bit processor ... Why would you load 32-bit OS?  (I don't have an answer, that's why I am asking.)

---

