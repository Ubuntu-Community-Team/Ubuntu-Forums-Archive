---
title: "someone will answer this fast"
date: 2011-01-28
forum: New to Ubuntu
---

### Post by slixz85 on 2011-01-28
hi i am setting up a live usb drive operating system for a friend. the hard drive in their laptop is out but they mostly use it for only internet. it is only a 3gb flash thumb drive. so my problem is i need to know how or what tool can be used to make it be able to have changes made to it. so when the live usb is booted up and some documents and such are saved that after shutdown, everything is there, not deleted by default when it boots again from the usb

need to have this done somehow especially to install wireless drivers so they can even get on the net while looking for a new hard drive ( they wont be able to get one for 2months at least ) (thats why settin somethin this lame up)

i use unetbootin only right now

---

### Post by AvoidedRider on 2011-01-28
On mine I go to System -> Administration -> Startup Disk Creator then just select the cd image you want to use the device you want to put it on and how much space you want to use for storage. Only time it ever gave me problems was when I tried to install software to configure a RAID.

---

### Post by slixz85 on 2011-01-28
> **AvoidedRider said:**
> On mine I go to System -> Administration -> Startup Disk Creator then just select the cd image you want to use the device you want to put it on and how much space you want to use for storage. Only time it ever gave me problems was when I tried to install software to configure a RAID.

yeah it actually gave me problems with not letting the isos boot but unetbootin always has worked unless the iso itself was short in size or somethin

there aren't any kind of terminal commands i could type in when using there laptop for live session to tell it to save everything to the usb?  (<i know u do this with the default disk creator but it dont work right for me)

---

### Post by fabricator4 on 2011-01-28
Google.  The keyword here is "persistance", as in it remembers your data instead of starting from scratch each time.  It _should_ be possible to partition the USB memory with a persistant data partition:

[Google Hits]("http://www.google.com.au/#hl=en&source=hp&biw=1024&bih=464&q=ubuntu+live+cd+persistent&aq=1m&aqi=g1g-m1g-v2&aql=&oq=live+CD+persistent&fp=e82ce623fc56ad5b")

Chris

---

### Post by slixz85 on 2011-01-28
> **fabricator4 said:**
> Google.  The keyword here is "persistance", as in it remembers your data instead of starting from scratch each time.  It _should_ be possible to partition the USB memory with a persistant data partition:

[Google]("http://www.google.com.au/#hl=en&source=hp&biw=1024&bih=464&q=ubuntu+live+cd+persistent&aq=1m&aqi=g1g-m1g-v2&aql=&oq=live+CD+persistent&fp=e82ce623fc56ad5b")

Chris

ok thanks i will do my best

---

### Post by AvoidedRider on 2011-01-28
Sorry I am not familiar with that program. When the startup disk creator didn't boot did you use something like disk utility to check the flags and make sure it was set to bootable?

---

### Post by fabricator4 on 2011-01-28
> **slixz85 said:**
> ok thanks i will do my best

I'm sure you'll do it.  BTW it's not a "lame" solution, it's a great Linux solution that will put a working computer in the hands of someone who really needs it.  Plus you'll probably get an Ubuntu convert who will really want to see how fast it runs off their new hard drive.  Just be sure and tell them it will be very slow working off the USB memory - some patience is required.

I often do a full install of a new distro to a USB memory for testing purposes.  I currently have one each for 10.10 and 11.04 alpha 1. A four GB USB is generally usable, if you delete any unwanted programs and get rid of surplus kernal and .deb files.

Chris

---

### Post by MartyBuntu on 2011-01-28
> **slixz85 said:**
> ...they mostly use it for only internet.

 ...it is only a 3gb flash thumb drive.


 ...so my problem is i need to know how or what tool can be used to make it be able to have changes made to it.

Honestly, this sounds like a candidate for my second favourite Linux distro, Puppy Linux.

---

