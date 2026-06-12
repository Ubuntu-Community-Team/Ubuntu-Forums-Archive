---
title: "Installing jaunty from an USB drive on an old laptop"
date: 2009-05-12
forum: New to Ubuntu
---

### Post by Edgewalker_001 on 2009-05-12
I already have a prepared version of Jaunty jackalope on my USB drive (written using unetbootin, the windows version) but my problem is that my old computer refuses to boot from the drive (It goes straight to the list instead)

The computer in question is an old compaq presario 2800 that I bought cheap to use as a travel computer, it has a floppy drive instead of its CD reader for some unfathomable reason... 
It is currently running ubuntu (the hardy heron distro) and I managed to install that by borrowing an USB DVD drive, however, this time I tried to install it using my own USB drive instead.

Anyhow, the computer obviously can boot from USB devices (since I managed to do so last time) so is there any way to tell the already existing GRUB that it can boot from the USB drive using the command line?

---

### Post by Jazzy_Jeff on 2009-05-12
With the usb device plugged into the computer go into the bios when the computer starts and see if you can find the boot sequence. See if it shows the usb drive. If so move it to the top of the list. If it is not there you may be out of luck without a bios update.

---

### Post by SunnyRabbiera on 2009-05-12
The older the machine the less likely it will boot from a USB, this is why the Live CD is still viable.
But this computer sounds ancient if its using a floppy, too bad you cant use Wubi.

---

### Post by Edgewalker_001 on 2009-05-12
XD the bios is old enough to not even list USB devices as being a valid boot source, all it has is a switch reading "USB legacy" enable/disable...

Last time it somehow autodetected the DVD drive and ran it by default, but this time I don't have that one...

So,how can I update my bios in that case? I mean, can I somehow upload a new version to the chip containing the new options?

---

### Post by Jazzy_Jeff on 2009-05-12
You can check with the manufacturer but I doubt you will be able to find an update. I would recommend trying to get that DVD drive back and use it.

---

### Post by Edgewalker_001 on 2009-05-12
I discovered another option while looking through the BIOS settings, apparently it supports network boot... Can I somehow set up a copy of the boot information on one of my other computers in the network and boot from there to upgrade it?

I mean, despite the computer being old I have a fully working copy of ubuntu 8.04 on it at the moment, and all I really want to do is upgrade it, while preferably formatting the hard drive as well.

---

### Post by Jazzy_Jeff on 2009-05-12
Someone else may have to answer this for you. I am not too good with networking. You may have to download the alternate install cd. Not sure though.

---

### Post by Edgewalker_001 on 2009-05-12
Well, the BIOS update is not possible anyhow,the manufacturer still lists it on their webpage,but the file isn't in their register...

I guess I'll have to try and get a hold of that USB DVD drive again...

---

### Post by Jazzy_Jeff on 2009-05-12
> **Edgewalker_001 said:**
> Well, the BIOS update is not possible anyhow,the manufacturer still lists it on their webpage,but the file isn't in their register...

I guess I'll have to try and get a hold of that USB DVD drive again...

I purchased a USB DVD drive a couple of years ago and it was the best purchase I ever made. I have used it on countless computers.

---

### Post by Edgewalker_001 on 2009-05-12
I guess the easiest and most painless way to upgrade is to just download the new versions...

---

### Post by MontelEdwards on 2009-05-12
> **Jazzy_Jeff said:**
> I purchased a USB DVD drive a couple of years ago and it was the best purchase I ever made. I have used it on countless computers.
yeah, look on eBay. 
but anyways.. uh, i think that the alternate install should work pretty good. are you sure that you set up ur USB drive correct? there is absolutely nothing in the boot menu? sometimes it will not show the device if it cannot be loaded.
How did you make the USB drive?

---

### Post by Edgewalker_001 on 2009-05-12
You know, I'm starting to wonder about this as well...

I made the USB by using the program ubootin for windows (I think it's a port of the same program for ubuntu)

But I tried to boot from the USB drive using one of my other computers, and it didn't boot from it either (with the BIOS set to boot from removable drives first)

The image seems to be ok, and everything's there from what I can tell, it just seems that computers absolutely refuse to boot from the drive...

I might need to get a new USB stick as well....

---

### Post by raymondh on 2009-05-12
Hi edgewalker,

Is a network upgrade possible from 8.04 to 8.10 and then 9.04?

Also, my experience on thumbs have been more favorable using ubuntu's imagewriter.  YMMV


Good luck

---

### Post by Edgewalker_001 on 2009-05-12
I tried imagewriter before I used ubootin, so my guess would be that it has something to do with the actual USB drive

---

### Post by MontelEdwards on 2009-05-12
> **Edgewalker_001 said:**
> You know, I'm starting to wonder about this as well...

I made the USB by using the program ubootin for windows (I think it's a port of the same program for ubuntu)

But I tried to boot from the USB drive using one of my other computers, and it didn't boot from it either (with the BIOS set to boot from removable drives first)

The image seems to be ok, and everything's there from what I can tell, it just seems that computers absolutely refuse to boot from the drive...

I might need to get a new USB stick as well....

ok, well i have never heard of that program
uh, why dont you try unetbootin?
[here]("http://unetbootin.sourceforge.net/")
its nice.

---

### Post by Edgewalker_001 on 2009-05-12
That's the one I used XD

I must've remembered the name wrong.

Anyhow, I'm trying the net upgrade chain right now, it seems to work flawlessly

---

### Post by lazyart on 2009-05-12
Once you make it to Intrepid there is an option in System>Administration to create a USB bootable.  Heck, you could download a live CD, and use it to create a bootable USB installation from another machine.

Options... Options...

---

