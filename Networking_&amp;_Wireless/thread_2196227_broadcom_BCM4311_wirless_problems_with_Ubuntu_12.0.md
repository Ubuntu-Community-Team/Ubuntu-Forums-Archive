---
title: "broadcom BCM4311 wirless problems with Ubuntu 12.04 LTS"
date: 2013-12-28
forum: Networking &amp; Wireless
---

### Post by superryanthompson on 2013-12-28
Good afternoon,

I recently installed Ubuntu 12.04 LTS on my Dell D430 to replace an old version of Ubuntu. Now the wireless is not working. I have looked at a lot of the posts on here and tried the suggestions to no avail. Can anyone give me a start? I tried using Synaptic and by using the help on the following links

[http://askubuntu.com/questions/55868/how-to-install-broadcom-wireless-drivers-bcm43xx](http://askubuntu.com/questions/55868/how-to-install-broadcom-wireless-drivers-bcm43xx)

and also looking at the blacklist. 

Any help would be appreciated!

Cheers!

Ryan

---

### Post by coldraven on 2013-12-28
The following works for me, I'm using 12.04 on a HP laptop with the BCM4311 card

```
sudo apt-get remove bcmwl-kernel-source
```
```
sudo apt-get install firmware-b43-installer b43-fwcutter
```

Then Reboot

From: [http://ubuntuforums.org/showthread.php?t=2072887](http://ubuntuforums.org/showthread.php?t=2072887)

---

### Post by superryanthompson on 2013-12-28
First off, thanks for the response. I tried your suggestion and it didn't work. I then tried the following code from the link you pasted

```
sudo modprobe -r b43 ssb wl
sudo apt-get remove bcmwl-kernel-source 
sudo apt-get install build-essential dkms linux-headers-generic
sudo apt-get install bcmwl-kernel-source
```

*I got FATAL: module ssb is in use.*

Is there a way to turn ssb off?

Also, what should the blacklist be reading in regards to this driver?

---

### Post by superryanthompson on 2013-12-28
So, I ended up installing the KDE Wicd and that got the wireless working. Not sure why. Maybe someone on here can explain it.

Ryan

---

### Post by tgalati4 on 2013-12-28
So the driver may have been working but Network Manager was not working correctly but wicd did work to get you connectivity.  You might try digging into Network Manager and see what was going on.

[https://help.ubuntu.com/community/NetworkManager](https://help.ubuntu.com/community/NetworkManager)

---

### Post by superryanthompson on 2013-12-30
I looked at the NetworkManager link and also these

[https://wiki.archlinux.org/index.php/wicd](https://wiki.archlinux.org/index.php/wicd)
[https://wiki.archlinux.org/index.php/NetworkManager](https://wiki.archlinux.org/index.php/NetworkManager)

Wicd is supposed to disable NetworkManager but I can run it just fine and it shows a connection with Wicd running as well.

---

