---
title: "Foreign DVDs"
date: 2010-11-04
forum: New to Ubuntu
---

### Post by tikitikimaji on 2010-11-04
I'm running Ubuntu 10.4 on a Compaq netbook.  I bought an external DVD player here in Kenya, which works just fine for any DVDs I buy in Kenya, but it won't play my American DVDs that I brought over with me.  I tried installing the libdvdcss, but that didn't change anything, I still get "Could not read from source" when I try to play the DVD.

---

### Post by migs73 on 2010-11-04
Where did you buy the PC?
This will set what region DVD's you will be able to play. This is a hardware issue, I believe this can be overidden, but only so many times before the drive becomes unusable.

---

### Post by wojox on 2010-11-04
Try this [How-To: Play DVD under Ubuntu]("http://www.debuntu.org/how-to-play-dvd-under-ubuntu-linux")

---

### Post by cascade9 on 2010-11-04
Thats because of 'region zoning' 

[http://en.wikipedia.org/wiki/DVD_region_code](http://en.wikipedia.org/wiki/DVD_region_code)

Somen DVD players allow to you reset the region code, but be warned- there is a limit to how many times you can do that (normally 5). 

There might be a software hack around region coding, I dont know myself. I dont have any imported DVDs, so I've never tried to find out.

---

### Post by lisati on 2010-11-04
Sounds like a region code issue, which, as migs73 suggests, often requires changing a setting in the hardware itself. There is usually a limit to the number of times you can do this.

---

### Post by arochester on 2010-11-04
You need to add the Medibuntu Repository and install the package libdvdcss2. Look at [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu) and scroll down to "Playing Encrypted DVDs" you can either install the entire Medibuntu repository or use the commands there(- either 32bit or 64bit as appropriate.)

---

### Post by lisati on 2010-11-04
If it's the wrong region code, installing the "libdvdcss" stuff won't help. See here: [http://en.wikipedia.org/wiki/DVD_region_code](http://en.wikipedia.org/wiki/DVD_region_code)

---

### Post by tikitikimaji on 2010-11-04
The pc was also bought in Kenya.  I already have libdvdread4 and also tried the ubuntu-restriced-extras stuff, which I think installed the css you mentioned.

(sudo apt-get install ubuntu-restricted-extras
sudo /usr/share/doc/libdvdread4/install-css.sh )

I guess I can wait another year before I can watch Ghostbusters 2.

---

### Post by arochester on 2010-11-04
Quote from "[SOLVED] DVD howto" - [http://ubuntuforums.org/archive/index.php/t-1298674.html](http://ubuntuforums.org/archive/index.php/t-1298674.html)

"Players/drives often have a region code built into them - so a region 4 drive will play region 4 DVDs. I'm really impressed by Medibuntu getting around that headache!

I think you're confusing using consumer DVD players with using an optical data drive on a computer to do the same job. In the latter case it's entirely down to the software what it does with the data it reads from the DVD."

and...

"I don't think your problem had anything to do with regionalisation; how could your computer know where you were when you played a DVD? ;-)"

---

### Post by migs73 on 2010-11-04
> **arochester said:**
> Quote from "[SOLVED] DVD howto" - [http://ubuntuforums.org/archive/index.php/t-1298674.html](http://ubuntuforums.org/archive/index.php/t-1298674.html)

"Players/drives often have a region code built into them - so a region 4 drive will play region 4 DVDs. I'm really impressed by Medibuntu getting around that headache!

I think you're confusing using consumer DVD players with using an optical data drive on a computer to do the same job. In the latter case it's entirely down to the software what it does with the data it reads from the DVD."

and...

"I don't think your problem had anything to do with regionalisation; how could your computer know where you were when you played a DVD? ;-)"

To qoute the Wiipedia page linked to by lisati above;

> Computer DVD drives

Older DVD drives use RPC-1 ("Regional Playback Control") firmware, which means the drive allows DVDs from any region to play. Newer drives use RPC-2 firmware, which enforces the DVD region coding at the hardware level. These drives can often be reflashed or hacked with RPC-1 firmware, effectively making the drive region-free. However, this usually voids the warranty.[10]

In most computer drives, users are allowed to change the region code up to five times.[11] However, if the number of allowances reaches zero, the region last used will be permanent even if the drive is transferred to another computer. This limit is built into the drive's controller software, called firmware. Resetting the firmware count can be done with first- or third-party software tools, or by reflashing (see above) to RPC-1 firmware
No, your computer doesn't know where you are when you watch a DVD, but it does know where its original region was when it was made. :)

---

### Post by cascade9 on 2010-11-05
> **migs73 said:**
> To qoute the Wiipedia page linked to by lisati above;

Hey, that was MY link! Lisati just nicked it :lolflag:

---

