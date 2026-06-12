---
title: "Firmware-b43-installer ERROR!! :c HELP"
date: 2014-03-16
forum: Networking &amp; Wireless
---

### Post by rlinsenbach96 on 2014-03-16
Im new to Ubuntu and i recently installed Ubuntu 13.10 Saucy Salamander but my wireless card wasn't working. I successfully installed b43-fwcutter i386 achetype.
I went to install firmware-b43-installer. the package wasn't installed. It Ubuntu software center said  Error and that the package was not dependable. Help me get a successful install of firmware-b43-installer on my computer so i can use wifi on ubuntu. By the way I run on 32bit Ubuntu 13.10 and my network card is the broadcom b4311

---

### Post by Whoopie on 2014-03-16
Just install the linux-firmware-nonfree package. That should do the trick.

---

### Post by rlinsenbach96 on 2014-03-16
Could you leave a link for it?

---

### Post by westie457 on 2014-03-16
```
sudo apt-get install linux-firmware-nonfree
``` should get it.

Any problems  post back here.

---

### Post by Hadaka on 2014-03-16
Hi, let's varify your wifi card....please do
```
lspci -n | grep 280
```
*If the result of above is  ->  [14e4:4311] then
you do indeed  have a 4311 card...the brcm4311 means nothing
your driver is selected by the [14e4:4311]. Sometimes brcm4311
cards have a 14e4:4312 this requires a different driver than the 4311.
I suspect ..like many others you have attempted to load the suggested
proprietary driver as well. so *If indeed your card is [14e4:4311] then
please do...
*ignore any not loaded or errors
```
sudo modprobe -rf wl
sudo rm /etc/modprobe.d/blacklist-bcm43.conf
sudo apt-get remove --purge bcmwl-kernel-source
```
then do.
```
sudo apt-get install linux-firmware-nonfree
sudo modprobe b43
```
westie is correct the linux-firmware-nonfree works best with [14e4:4311]
report back any problems
thanks.

---

### Post by westie457 on 2014-03-16
@ Hadaka and whoever else reads this.
A small tip: 'linux-firmware-nonfree' does not usually work on a Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01) chip. For a 'rev 01' chip the one that works (at least for me) is 'firmware-b43-installer' and 'b43-fwcutter and has done since about the release of 10.04.

IIRC this particular thread was started for a [14e4:4311] (rev 02) chip which uses the nonfree driver previously mentioned.

---

