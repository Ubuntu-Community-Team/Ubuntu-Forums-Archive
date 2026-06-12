---
title: "problems with my ipw3945 card"
date: 2006-09-20
forum: Networking &amp; Wireless
---

### Post by tek03 on 2006-09-20
Hi

seems that a lot of persons have had problems with this card. I recently installd ubuntu 6.06 LTS and suprisingly the card was not recognised. I've tried the tips in thread [http://ubuntuforums.org/showthread.php?t=244814](http://ubuntuforums.org/showthread.php?t=244814) but with no luck. 

My kernel version is 2.6.15-26-383 and the ipw3945-2.6.15-26-383 package is installed.

I tried to update my kernel to 2.6.15.26-686 through synaptic and the terminal but I just receiv error messages like

"W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.15/linux-image-2.6.15-26-686_2.6.15-26.46_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.15/linux-image-2.6.15-26-686_2.6.15-26.46_i386.deb)
  404 Not Found"

Any help would be good!!

Thanks

---

### Post by ltmon on 2006-09-20
Hi,

Install the packages "linux-image-686" and "linux-restricted-modules-686".  Having these packages installed makes sure you always have the latest kernel and wireless drivers for the 686 architecture.

L.

---

### Post by tek03 on 2006-09-21
I installed automatix and updated my kernel to 2.6.15-27-383. After the reboot the card works flawlessly.

---

