---
title: "Which version will be installed?"
date: 2009-12-18
forum: New to Ubuntu
---

### Post by racie on 2009-12-18
I've recently done a re-install of my laptop to get the new Windows 7 (my brother bought it and let me install it).  Now, my laptop has a 64-bit motherboard, BUT I installed the 32-bit version of Windows 7 onto my laptop (for various reasons).

Now, my question is: If I use Wubi to install Ubuntu, will it install the 32-bit version to match that of the OS I'm currently running, or will it install the 64-bit version to match my motherboard.  Is there a way I can choose?  I'd really prefer the 32-bit version because of compatibility issues.

Thanks.

---

### Post by Extract_Here on 2009-12-18
well you should use the 64bit to match the mother board i would imagine maybe im wrong.

---

### Post by marshmallow1304 on 2009-12-18
> **racie said:**
> I'd really prefer the 32-bit version because of compatibility issues.

Which would be?

---

### Post by themusicalduck on 2009-12-18
I imagine if you download the 64 bit iso then it'll install the 64 bit version, pick the standard x86 iso and it'll install 32 bit.

---

### Post by racie on 2009-12-18
> **marshmallow1304 said:**
> Which would be?

Well, Google Chrome is one example, but that's a minor issue.  I'm not that great at Ubuntu, so I get really confused when a file I want to download is for the 32-bit instead.

I really don't mind getting the 64-bit version.  And it seems like that might be a good idea.  HOWEVER, I do not know which version **Wubi** is going to install on my laptop.  Right now, I am running 32-bit Windows on a 64-bit laptop.

---

### Post by themusicalduck on 2009-12-18
Are you installing with wubi using a CD? So which iso file did you burn to the CD? Or did you order the CD by mail or get it from somewhere else?

---

### Post by sailthesea on 2009-12-18
You can pick and choose which version of ubuntu you want Wubi to install here:

[http://sourceforge.net/projects/wubi/files/](http://sourceforge.net/projects/wubi/files/)

Do a little back reading for the hardware support and try it out 

 I have had great success with Wubi in the past:)

---

### Post by ezsit on 2009-12-19
Unless you have more than 4GB of ram and use a virtual machine to run other operating systems, sticking with the 32bit version is just fine, you won't gain all that much with 64bit versions other than a very slight speed boost on memory intensive operations. 

As for the version of Wubi, it depends on the cd version of ubuntu you downloaded, the desktop version is available in 32 and 64 bit versions and the one you download will be the one used.

---

### Post by racie on 2009-12-19
> **ezsit said:**
> Unless you have more than 4GB of ram and use a virtual machine to run other operating systems, sticking with the 32bit version is just fine, you won't gain all that much with 64bit versions other than a very slight speed boost on memory intensive operations. 

As for the version of Wubi, it depends on the cd version of ubuntu you downloaded, the desktop version is available in 32 and 64 bit versions and the one you download will be the one used.

Yeah, but I don't know which one I downloaded.  I just clicked on the first download link on this website: [http://wubi-installer.org/](http://wubi-installer.org/)

& thanks for the bit of info on the 32-bit vs 64-bit

---

### Post by themusicalduck on 2009-12-19
I'm not sure if the exe of that site will download the files or something, but either way you'll need more than that file to install Ubuntu with wubi.

What most people do to install with wubi, is to download the .iso file from [http://www.ubuntu.com/](http://www.ubuntu.com/) then either burn it onto a CD, load the CD and run the wubi.exe file on there, or you could just mount the iso as a virtual drive on windows. Everything you need to install with wubi will be on that iso file. Remember you need to burn it as an iso and not just copy the iso file onto the CD like a data disc.

If you download the default version that it gives you on that website, it will be 32 bit. Click on the Alternative download options link and it'll let you get 64.

---

### Post by Marvin666 on 2009-12-19
If you get a default download it would be 32bit. You should try and get a 32 bit version since you have 32 bit windows installed. In the future, you might wanna look into a dual boot.

---

### Post by Old_Grey_Wolf on 2009-12-19
> **racie said:**
> Yeah, but I don't know which one I downloaded.  I just clicked on the first download link on this website: [http://wubi-installer.org/](http://wubi-installer.org/)

& thanks for the bit of info on the 32-bit vs 64-bit

By clicking that link you will get the 64-bit version because of your 64-bit processor.

From the Wubi FAQ ([http://wubi-installer.org/faq.php](http://wubi-installer.org/faq.php)):

> 

Why is the AMD64 version of Ubuntu getting downloaded and installed?

[INDENT][/INDENT]You probably have a 64 bit machine, the 64AMD installation is appropriate for all 64 bit architectures whether AMD or Intel.

Can I force Wubi to download and install a 32 bit version of Ubuntu?

[INDENT][/INDENT]Yes, either pre-download the appropriate 32 bit ISO manually and place it in the same folder as Wubi.exe or start Wubi with the "--32bit" argument.


---

