---
title: "Run script at boot"
date: 2009-04-13
forum: New to Ubuntu
---

### Post by beetlejuice_masterson on 2009-04-13
Hi all-

This probably isn't very sophisticated but i'm having some issues running a few commands at boot.  Here they are:

sudo modprobe -r ath_pci
sudo modprobe -r ath_rate_sample
sudo modprobe -r ath_hal
sudo modprobe ndiswrapper

I have to run this jazz to get my wireless working.  I tried going into modprobe.d/blacklist and adding 
blacklist ath_pci
blacklist ath_rate_sample
blacklist ath_hal

but my computer locked up at the login screen.  maybe i needed a blank line at the end of the file? idk - luckily i backed up the file.

so what's the best way to run these 4 commands?  thanks for the help!

---

### Post by tjwoosta on 2009-04-13
hmm..   i dont really know if this is of any help or not but i just found this

[http://ubuntuforums.org/showthread.php?t=95568]("http://ubuntuforums.org/showthread.php?t=95568")

so according to that it says use /etc/hotplug/blacklist

[https://help.ubuntu.com/community/BootHotPlugErrors]("https://help.ubuntu.com/community/BootHotPlugErrors")

---

