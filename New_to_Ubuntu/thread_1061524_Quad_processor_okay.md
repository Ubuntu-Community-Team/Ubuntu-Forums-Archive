---
title: "Quad processor okay?"
date: 2009-02-05
forum: New to Ubuntu
---

### Post by paker on 2009-02-05
Is quad processor working well in Ubuntu?
Specifically, I plan to buy AMD X4 920 and Asus M3N72D (onboard nvidia video). I checked this forum but there was only one problem thread on M3N72D and no AMD Quad CPU problem threads.

Just want to make sure I am not buying a known problem. 

Also, if you have a different quad processor setup (CPU + mobo) that is working well in ubuntu, please let me know. I will gladly switch. 
Thanks.

---

### Post by steveneddy on 2009-02-05
Should work well.

Try Googling for your board for hardware compatibility.

I would run a 64 bit version of Ubuntu with that set up.

---

### Post by Kellemora on 2009-02-06
Hi Paker

I have the M2N68-AM Asus MOBO

I had to load windows xp to install the Bios and Bios update function so just went ahead and made the machine a dual boot, even though I intended for it to be Ubuntu only.

The only thing you will need to do right away is to install the Nvidia hardware drivers.  Do this from System/Administration/HardwareDrivers.  Ubuntu will use the VESA driver until you do this.  The 128 driver don't work it's the new one listed there.

After that you should be home free!

The ONLY thing I've noticed with the 64 bit version of Ubuntu that I don't really like is that it will not show all the files possible to create using Ubuntu 32 bit.  Namely if you have used illegal characters in your file names.  We have like 150,000 files that will have to have the file names changed by hand one at a time, as we find them, because you cannot do a search for an illegal character in a file name either.
Our ENTIRE Question Answer Database will not show ANY of the Question files in Ubuntu 64 even though they are there as indicated by checking PROPERTIES of the Folder they are in.

We are PRAYING that some upgrade or update to Ubuntu 32 does not render them invisible before we locate and change all of them!

What's odd is, if it's an illegal character, WHY can we open, edit and resave the files using that character from almost any program?  Create new files and save those using that illegal character, all with no problems?  Makes no sense to me!

TTUL
Gary

---

### Post by paker on 2009-02-07
Thank you for the mobo suggestion. I haven't made the purchase yet but will consider it.

---

### Post by 3rdalbum on 2009-02-08
I would strongly recommend an Intel Core 2 Quad. The performance is better and the pricing on these is still pretty good! You can overclock the Quad to 3GHz easily if your motherboard supports changing the FSB frequency and if you have a reasonable aftermarket cooler (I have a Noctua and I love it), and at 3GHz the Core 2 Quad will be much better than the best Phenom 2 that AMD has.

I'm using an Asus P5K Premium motherboard, but these are no longer being made. Get something with all solid capacitors and you'll be laughing. They're not cheap but they last a long time. Also, buy a cheap discrete graphics card rather than use onboard video, as onboard video is pretty terrible.

---

### Post by paker on 2009-02-23
Bought intel quad Q9300 + intel P45 mobo. I am posting with the new build. The only problem I had was the native ALSA audio driver for ubuntu 8.10 32 bit did not support intel ICH10R (south bridge I suppose) well, and I had to download and install the most recent ALSA audio driver. But this forum had a thread on the subject, and the update went well. 

Apparently, the mobo can run 400 MHz fsb, but I still don't know how to adjust memory timing. 

I am still staying away from 64 bit. I have had enough headache with previous releases, and am going to stay with 32 bit a while longer.

---

