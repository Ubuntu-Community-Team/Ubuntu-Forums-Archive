---
title: "D-link dongle wont install + minor wifi problem ubuntu 16.04"
date: 2016-12-11
forum: Networking &amp; Wireless
---

### Post by mogglesson on 2016-12-11
Just installed ubuntu on my laptop and I just cant get things working. 
There are essentially two problems,
Wifi wont work whatever I do, there is nothing wrong with the device itself and correct drivers are installed, problem is that when i log on to a network I still cand use the web and no pings get returned despite full bars.

Other problem is that I dont Always have access to wifi so i use a usb dongel for internet nost of the time.
It installs just like it should, but then refuses to be recognised properly.

Any and all input you guys can give is worth gold! And any info you need i will do my best to give you

---

### Post by howefield on 2016-12-11
Thread moved to the "*Networking & Wireless*" forum for a better fit.

It would most likely help others to help you if you post the wireless script info as described in [this thread]("https://ubuntuforums.org/showthread.php?t=370108").

---

### Post by mogglesson on 2016-12-11
Thank you and sorry for not complying to forum rules and etiquette[ATTACH]272663[/ATTACH]!

I have managed to get wifi partly working.
When first starting up the computer wifi works just fine, but if disconnecting and reconnecting or plug in the dongle internet (including the wired kind) stops working completely. In the end I have to restart the computer to get connectivity back.


The dongle i use is a D-link DMW-157 revision C
Have tried installing it using this Russian guide: [http://ftp.dlink.ru/pub/usb/DWM-157/Description/D-Link%20DWM-157%20Linux%20guide.pdf](http://ftp.dlink.ru/pub/usb/DWM-157/Description/D-Link%20DWM-157%20Linux%20guide.pdf)

---

### Post by praseodym on 2016-12-12
Well: For the internal card the Broadcom STA is too old:
```

sudo modprobe -rfv wl
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install linux-headers-$(uname -r) build-essential dkms
wget http://de.archive.ubuntu.com/ubuntu/pool/multiverse/b/broadcom-sta/broadcom-sta-dkms_6.30.223.271-3_all.deb
sudo dpkg -i broadcom-sta-dkms_6.30.223.271-3_all.deb 
```

For LAN: Change the driver:

```
sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms
wget http://de.archive.ubuntu.com/ubuntu/pool/universe/r/r8168/r8168-dkms_8.043.02-1_all.deb
sudo dpkg -i r8168-dkms_8.043.02-1_all.deb
echo "blacklist r8169" | sudo tee -a /etc/modprobe.d/blacklist.conf 
```
Reboot.

For WWAN: Check:
```
lsmod
usb-devices
```

---

