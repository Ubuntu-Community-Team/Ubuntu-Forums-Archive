---
title: "Idea for my netbook, will it work?"
date: 2009-11-19
forum: New to Ubuntu
---

### Post by mvdoso on 2009-11-19
Hello, recently I have been introduced to puppy Linux and I love it!!  And I have an idea for my netbook, but I want to make sure it will work and work well before I go buy the parts.

(Dell Mini 10v)

I plan on removing the hard drive completely and keep it as an extra.  

I will have Puppy Linux on my flash drive (4-8GB)

I will have all my files on an SDHC Card (16GB)

IS it resonable?  Is it possible to set up, so every time I save something it automatically goes to the SDHC card?

---

### Post by damis648 on 2009-11-19
See if maybe you can get an internal SD-SATA adapter (or something similar) so that you don't have to have that flash drive hanging out all the time...

---

### Post by s3a on 2009-11-19
I think so if you format your SDHC card as the **/home** partition and the flash drive as your **/** partition then I believe that you could do that however I should warn you that an OS off a flash drive will be significantly slower than regular speed but if you insist, do sudo apt-get install preload and there are other configuration changes you can do to improve speed as well.

---

### Post by mvdoso on 2009-11-19
Thanks for the help!

Does anyone know how I can get my wireless working in Puppy Linux?

---

### Post by sgosnell on 2009-11-19
Put everything on the SDHC card.  It fits inside the slot, and can be left in all the time.  You don't want to use the USB drive for the OS.  I've run several distros off SDHC cards, and that works pretty well.  16GB is plenty of room for running any distro, and if you need more space you can store some files on the USB stick.  The SDHC card won't be significantly slower than the HDD, IME.

---

