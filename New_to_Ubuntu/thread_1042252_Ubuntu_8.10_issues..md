---
title: "Ubuntu 8.10 issues."
date: 2009-01-17
forum: New to Ubuntu
---

### Post by melrokz on 2009-01-17
I got Ubuntu 8.10 up and running!
T'was a small error in the bios which showed the 'graphics aperture' size as 128MB when it is actually 64MB.
Once corrected and rebooted, it got past the login screen and displayed the desktop.

1. I'm not able to get desktop effects working (with Intel 845GL videocard, 64MB video memory, 740MB RAM, 7.7GB free space, ext3fs)

2. I'm going to buy a new motherboard with integrated graphics and amd processor, is it a good idea?
   What are the graphics cards (nVIDEA and ATI) supported by Ubuntu 8.10?

3. My ntfs partitions are not mounting by default. When i mount them in nautilus, they show an error 'no mount object for mounted volume'. What could be wrong?

4. When i restart my pc, when i open windows in ubuntu 8.10, they only cover half the screen. Why?

---

### Post by abn91c on 2009-01-17
#1. check here for only solution, bottom line compiz is a no-go with i845 cards, look at posting #26 [http://ubuntuforums.org/showthread.php?t=966436&page=3](http://ubuntuforums.org/showthread.php?t=966436&page=3)

---

### Post by mrjohnston on 2009-01-17
I think your graphic card is too old to support 3d.  The 9XX generation of intel and the newer 3100 and 4500 both do however.  Nvidia offers excellent driver support for linux in my experience, and AMD/ATI offers decent drivers that are getting much better.  So as long as its a decent video card you should be ok regardless of brand, though Nvidia is probably the best at the moment (though closed source if that is an issue for you). 

For your mount error you might not have created the directory you are trying to mount them to.  So if you want to mount them to /media/win you need to:
sudo mkdir /media/win
So the directory is present to mount the partition to.  Thats my guess for your issue at least.  Anything you mount outside of during the install will need to have the directory created where you are mounting it to.

As for the windows thing, many windows like nautilus are only intended to cover part of the screen so you can view multiple windows at once.  Just resize them.  Many also remember the size you had them last so you won't have to keep resizing IIRC.

---

### Post by LowSky on 2009-01-17
your biggest issue is graphics... looks like your best option is to reconfigure your xorg file. Boot into recovery mode. choose xfix and go through the steps it should fix things. To get desktop effects working you need to install ccsm.
Why are you getting a new motherboard? If you do that you should get a new processor too. but if not then dont was money on a new motherboard, just buy a graphics card. Nvidia is the best choice.

---

### Post by melrokz on 2009-01-19
1. When i restart my pc, when i open windows in Ubuntu 8.10, they only cover half the screen. I'ts not a window resizing problem. I'll have to run 'monitor resolution settings' to correct the display. Why?

2. Why is openoffice 3 missing from the repos?

---

