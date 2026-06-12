---
title: "Just burned Ubuntu onto a disc from Infra recorder"
date: 2009-09-18
forum: New to Ubuntu
---

### Post by LeopardGecko on 2009-09-18
I changed my BIOS so it boots my disc drive before the hard drive. I insert my CD containing Ubuntu, it asks me to select a language, I choose English. Then a list of options come up after this, I choose "Install Ubuntu" as soon as I do this though my screen freezes and I can no longer complete any task besides restarting. I thought it might just be taking a little bit longer and left it sitting like this for 45 minutes, but the screen had not changed. Any help? Or advice on what I should do?:confused::confused::confused::confused::confused::popcorn:

---

### Post by freak42 on 2009-09-18
Hi

can you give us your computer name/type and hardware specs (as good as possible?

---

### Post by zvacet on 2009-09-18
Did you check [md5sum]("https://help.ubuntu.com/community/HowToMD5SUM") before you burn iso and [disc integrity ]("https://help.ubuntu.com/community/Installation/CDIntegrityCheck?action=show&redirect=CDIntegrityCheck") after you burn iso?Do you get any errors?

---

### Post by mike555 on 2009-09-18
sounds like you don't have enough RAM ... if you have less then 512 you should use the text install cd ..

---

### Post by LeopardGecko on 2009-09-18
Oh, right, of course. I have an Hp Dv6000 120Gb hard drive and 958Mb of RAM. My current windows Vista is a 32 bit system. (I also have Ubuntu 32 bit on disk)

I downloaded the winMd5sum program, I transfer (I can't "send to" like they ask in the tutorial, it doesn't come up as an option) the Ubuntu 9.04 file to the program (in the tutorial it also says there should be a "compare" file, but that doesn't show up when I do this) and click compare and calculate and it says that the "Md check sums are different".

---

### Post by zvacet on 2009-09-20
You can try [this]("https://help.ubuntu.com/community/VerifyIsoHowto") under **While booting**.If md5sum is not correct download same iso with torrent and point download where your existing iso is.Torrent will just check iso for bad files i any and replace them with good ones.so you will not download all iso.After that burn it again and try with above link.

---

### Post by Paqman on 2009-09-20
> **zvacet said:**
> After that burn it again

Make sure you do this at the slowest speed possible to reduce errors.

---

### Post by MrWES on 2009-09-20
Absolutely great advice! I continually tell people to download the iso file via torrent, as the hash checking will ensure you get a good iso. uTorrent is readily available for users migrating from Windows, and it's an extremely small footprint.

`Bill

---

