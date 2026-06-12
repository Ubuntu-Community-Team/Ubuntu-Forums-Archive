---
title: "Dell XPS 13 wireless not working. Panda PAU03 bought to replace it also working"
date: 2018-10-14
forum: Networking &amp; Wireless
---

### Post by moultano on 2018-10-14
Since I bought this machine a few years ago I've never succeeded at getting the wireless to work with any recent version of Ubuntu. I finally gave up and bought a USB wireless card, Panda Wireless PAU03, and it also isn't working.

Both cards are listed as "off" and clicking the button to turn them on has no effect.

Currently running 18.04.1. Please help!

---

### Post by praseodym on 2018-10-14
Please run the wireless script from the sticky thread and show the outputs. Does LAN work?

---

### Post by moultano on 2018-10-14
Thanks. LAN works. Here's the script output. [http://paste.ubuntu.com/p/D6hSqgZ373/](http://paste.ubuntu.com/p/D6hSqgZ373/)

---

### Post by praseodym on 2018-10-14
Try
```

sudo apt-get remove --purge bcmwl-kernel-source
wget http://de.archive.ubuntu.com/ubuntu/pool/multiverse/b/broadcom-sta/broadcom-sta-dkms_6.30.223.271-8_all.deb
sudo dpkg -i *.deb
```
Reboot and show
```

lsmod
iwconfig
rfkill list
```

---

### Post by moultano on 2018-10-15
Thanks. Here's the output of those three.
[https://paste.ubuntu.com/p/DZbQytD3Fk/](https://paste.ubuntu.com/p/DZbQytD3Fk/)

---

### Post by chili555 on 2018-10-15
Please do:```
sudo modprobe -r dell_laptop
sudo rfkill unblock all
```Any improvement?

---

### Post by moultano on 2019-01-20
After running
 [FONT=Courier New]sudo modprobe -r dell_laptop[/FONT]
I get
 [FONT=Courier New]modprobe: FATAL: Module dell_laptop is in use.[/FONT] 
No change to wifi or any other behavior.

---

### Post by chili555 on 2019-01-20
Please blacklist it and reboot:```
sudo -i
echo "blacklist dell_laptop"  >>  /etc/modprobe.d/blacklist.conf
exit
```Reboot and show us:```
rfkill list all
```

---

### Post by moultano on 2019-01-21
```

0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: brcmwl-0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
2: phy1: Wireless LAN
	Soft blocked: no
	Hard blocked: no

```

---

### Post by chili555 on 2019-01-22
You have two conflicting wireless devices running. Frankly, I'd rather troubleshoot the internal Broadcom than the twitchy USB. Please detach the USB and the ethernet and reboot. Next, run:```
rfkill list all
dmesg | grep wl
```Attach the ethernet and post the result.

---

