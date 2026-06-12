---
title: "Partimage guidance needed"
date: 2008-12-13
forum: New to Ubuntu
---

### Post by martynmoore on 2008-12-13
I've had Ubuntu installed on a Toshiba laptop for two weeks and have ironed out many glitches and configured lots of apps and services.

It works a treat.

I've been told that Partimage will allow me to create an image of my installation, including all settings, but the interface is a little daunting.

I've booted from SystemRecoveryCD and made my way to Partimage, but am struggling with the method, what to call things and how to specify paths to save to.

I want to create an image file of my install, save it to this laptop's hard drive to then burn to a bootable installation CD to replicate my current set up.

Is there an easy step-by-step anybody can point me to?

---

### Post by logos34 on 2008-12-13
I think what you're looking for is remastersys:

[http://www.remastersys.klikit-linux.com/](http://www.remastersys.klikit-linux.com/)
[http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html](http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html)

You can't make a live bootable backup CD with Partimage, but it's good and fast for just cloning / (because it copies only the used sectors of the partition, resulting in a very small .gz file).  It's what I use.  Getting the paths right takes a little practice.  But remember you need to first mount the destination, while the source (what you're copying) should be unmounted.

[http://ubuntuforums.org/showthread.php?t=287522](http://ubuntuforums.org/showthread.php?t=287522)
[http://www.partimage.org/Partimage-manual_Usage#How_to_save_a_partition_into_an_image_file](http://www.partimage.org/Partimage-manual_Usage#How_to_save_a_partition_into_an_image_file)
[http://www.digitalissues.co.uk/html/os/misc/partimage.html#9](http://www.digitalissues.co.uk/html/os/misc/partimage.html#9)

good luck

---

### Post by martynmoore on 2008-12-13
Plenty to read up about there. Remastersys looks exactly what I need. Thanks very much indeed.

---

### Post by theozzlives on 2008-12-13
I didn't know remastersys existed, I think I'll try it, thank You

---

