---
title: "removing a os that i put on a flashdrive using image-writer"
date: 2009-07-20
forum: New to Ubuntu
---

### Post by djmh on 2009-07-20
i am unable to remove a moblin image file that was installed to my flash drive using image-writer, i tried just deleting it and it says it cannot be deleted ..so i did sudo nautilus, and tried ...only to get the same error ....

i dont want that os on my drive anymore, could someone instruct me as how to remove it from my drive ? 

thanks for your time and help !

---

### Post by pizza-is-good on 2009-07-20
Use gparted
```
sudo apt-get install gparted
```
and format your flash drive.
 
That should do it.

---

### Post by an93l on 2009-09-21
> **pizza-is-good said:**
> Use gparted
```
sudo apt-get install gparted
```
and format your flash drive.
 
That should do it.
I concur. I just had this issue and I had to boot gparted in a virtual machine to get it removed. I don't have a working linux machine appart from my moblin netbook that can't do anything. I am now trying to boot from a USB key to re install UNR but it won't work. the USB key is bootable and working but it is not working on my moblin netbook. I am doing a search on how to remove moblin in google and yahoo but no articles found. I am looking around in forums but nothing yet.

---

### Post by corncob on 2009-09-21
If you have any problems with gparted and still have a machine running Windows put it in there and format it.  Windows can't see the Linux partition let alone any protections or ownerships that are preventing you from deleting Moblin.

---

### Post by LewRockwell on 2009-09-21
[http://en.wikipedia.org/wiki/Dd_(Unix](http://en.wikipedia.org/wiki/Dd_(Unix))

use with caution

one command can erase your entire drive

.

---

### Post by an93l on 2009-09-21
I managed to get it formated with gparted. But I will advise that when I put the key that had the livecd of moblin on it windows could only see and therefore format only 679MB of the key and it is an 8GB one so that wouldn't work. It worked with all other bootable live cd versions of all the other distros I have tried. I managed to get Moblin of my netbook as well I found out that there was something wrong with the UNR ISO file I had downloaded. I ended puting on the KDE version of the UNR Karmic on the netbook.

---

