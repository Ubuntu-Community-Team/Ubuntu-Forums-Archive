---
title: "Files from a broken MacMini..."
date: 2009-05-15
forum: New to Ubuntu
---

### Post by ElmerFishpaw on 2009-05-15
Just curious if anyone has moved files from a Mac Mini (ppc4) to an a machine running Ubuntu? 
I did a search and really didn't find anyone with a similar problem. I love to learn new things and hope this will be more of an adventure than a pain in the neck to do...
So, I have a PPC4 Mac Mini with a dead optical drive (I believe). I can boot it to Target mode....I get a yellow firewire symbol on the screen. I have a Firewire cable and have it connected to the Ubuntu machine. 
OK...what happen is I get a "Paragon" (I think...at work at the momemnt)file browser. It goes away in a short while. The files I see make no sense....All I want to retrieve are some .avi/.jpg/.mp3
So....I'm lost. How do I access the stuff I want. I'm not frightened of the Terminal (just tell what to cut/copy/paste LOL).
I'm loving Ubunutu, open source, the spirit of this community!

---

### Post by louieb on 2009-05-15
Don't do MAC but if I had a drive in a non working PC I wanted to get data off. I'd take the drive out> put it in a USB enclosure> plug it in a working machine > and see what I can get. 

Good luck.

---

### Post by nothingspecial on 2009-05-15
I know nothing of macs but if I wanted to get data off a broken system I would boot a live usb stick (Ubuntu of course but any will do) mount the internal drive if possible and copy my stuff that way.

Can macmini`s boot from usb?

I`m not sure I understand what you`re trying to achieve but if this sounds like it might work I`ll tell you in detail. If I've misunderstood then sorry.

---

### Post by ElmerFishpaw on 2009-05-15
Thank You for the responses! Physically taking apart the MacMini to get at the drive is really beyond me. I think the USB with Ubuntu for mac ppc4 may be the way to go.....I'm pretty certain the optical drive is shot, but the booting from the USB would not involve the optical drive....I hope....

---

### Post by nothingspecial on 2009-05-15
Okay assuming you are using Ubuntu 9.04

```
sudo apt-get install unetbootin
```

If you are using an earlier version of Ubuntu then get it from [[COLOR="Magenta"]here[/COLOR]]("http://unetbootin.sourceforge.net/")

Plug a usb drive in and launch unetbootin.

Select your distribution. Use whatever you like but be aware that some don`t have a live environment (zenwalk is one), I`d go with Ubuntu.

At the bottom make sure you select the correct usb drive. If you have any other usb storage devices plugged in other than the one you want to use and your not sure which to select then unmount and unplug all the others.

When you hit ok or apply (whatever it is) be aware that anything on your data stick will be lost.

Go have a beer (or coke).......fruit juice would be healthier. (Although it can have a high sugar content) so maybe water would be best (although theres no nutritional benefit in water) but there is in beer.

After it finishes reboot and hope that your macmini can boot from the usb stick. You`ll have to select this option how ever it`s done on a mac.

If it works post back and we`ll go from there.

If it doesn`t post back and we`ll try something else.

---

### Post by ElmerFishpaw on 2009-05-15
NothingSpecial....Thank you very kindly!! I will get setup and try it after work tomorrow....with a Dunkin Donuts Coffee...till then I'll research how to boot a mac mini via USB start up disc. 
I'm hoping the mac ppc4 is a choice that I get to put on the USB start up disc.

---

### Post by 3rdalbum on 2009-05-15
> **nothingspecial said:**
> Okay assuming you are using Ubuntu 9.04

```
sudo apt-get install unetbootin
```

No. Unetbootin will not work for a PowerPC-based Macintosh. It's a completely different instruction set and completely different method of booting from PCs.

Besides which, most PPC Macintoshes can't boot from USB - as far as I know, the Mini can't boot from USB. That's one of Apple's restrictions.

You could get an external DVD drive that connects through Firewire to boot up an Ubuntu live CD and mount your old hard disk. You could actually buy a Firewire 5.25 inch drive enclosure and an ordinary SATA internal DVD drive and hook up the two and it might end off cheaper.

The best option really is to open up the Mini and take out the hard disk, and then connect it to a PC by use of a 2.5 inch drive enclosure.

---

### Post by ElmerFishpaw on 2009-05-15
Ok.....I'm curious why I can't get to my mp3s and jpgs with a firewire between the two computers and the mac mini in target mode...I get data, but nothing having mp3s and jpgs.....

---

### Post by nothingspecial on 2009-05-15
> **3rdalbum said:**
> No. Unetbootin will not work for a PowerPC-based Macintosh. It's a completely different instruction set and completely different method of booting from PCs.

Besides which, most PPC Macintoshes can't boot from USB - as far as I know, the Mini can't boot from USB. That's one of Apple's restrictions.

You could get an external DVD drive that connects through Firewire to boot up an Ubuntu live CD and mount your old hard disk. You could actually buy a Firewire 5.25 inch drive enclosure and an ordinary SATA internal DVD drive and hook up the two and it might end off cheaper.

The best option really is to open up the Mini and take out the hard disk, and then connect it to a PC by use of a 2.5 inch drive enclosure.

Ok cool, now I know.

---

### Post by ElmerFishpaw on 2009-05-15
Ok.....I'm curious why I can't get to my mp3s and jpgs with a firewire between the two computers and the mac mini in target mode...I get data, but nothing having mp3s and jpgs.....

---

### Post by ElmerFishpaw on 2009-05-19
I think I need to find where the mac hard drive appears in Ubuntu. I just want the mp3/jpg/avi and itunes songs from my mac hard drive. Everyone I know who knows computers is stumped by this...

---

### Post by ElmerFishpaw on 2009-05-22
OK....the drive "firewire drive" is there. It won't mount. I downloaded HFSExplorer...ran the file I was supposed to run (..something.sb) and nothing...it won't run. I'm thinking the Mac's Hard drive is crashed and damaged.

---

