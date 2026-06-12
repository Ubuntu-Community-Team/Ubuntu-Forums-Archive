---
title: "Wifi not working on Ubuntu 16.04 LTS on HP envy 14t 2015 with BCM43142"
date: 2016-06-04
forum: Networking &amp; Wireless
---

### Post by chinmay_kulkarni on 2016-06-04
I recently installed ubuntu 16.04 LTS as dualboot with windows 10. But I am nit able to connect to the wifi router.Basically it is not detecting wifi router on my laptop.
I have tried everything on previous threads with same problem but I am not able to fix it.

Below is the link to my Wireless-info.txt:

[http://paste.ubuntu.com/17011916/](http://paste.ubuntu.com/17011916/)

Please Help!!!

---

### Post by jeremy31 on 2016-06-04
Is Secure boot enabled in BIOS?  What does ```
sudo modprobe -v wl
``` result with?

---

### Post by chinmay_kulkarni on 2016-06-04
I have disabled secure boot in BIOS.

Result for the code is:

modprobe: FATAL: Module wl not found in directory /lib/modules/4.4.0-22-generic

---

### Post by jeremy31 on 2016-06-04
You might want to try ```
sudo apt-get install --reinstall bcmwl-kernel-source
``` and see what happens

---

### Post by chinmay_kulkarni on 2016-06-04
I ran the code for reinstallation.

It prompted to ask for disabling secure boot via creating a password. I did it

when i again ran the code for "sudo modprobe -v wl":

The output was:

insmod /lib/modules/4.4.0-22-generic/updates/dkms/wl.ko 
modprobe: ERROR: could not insert 'wl': Required key not available

---

### Post by jeremy31 on 2016-06-04
Then it must be that secure boot is enabled somehow otherwise you would not see that error.

This post by Wild Man may help you [http://ubuntuforums.org/showthread.php?t=2304607&p=13498349#post13498349](http://ubuntuforums.org/showthread.php?t=2304607&p=13498349#post13498349)

---

### Post by chinmay_kulkarni on 2016-06-04
I tried wild man's method via enrolling MOK. But it still gives the same output

---

