---
title: "Strange problem with AR5007EG"
date: 2008-06-06
forum: Networking &amp; Wireless
---

### Post by thebeak on 2008-06-06
I finally have partially got my AR5007EG wireless card working.

The only thing is that I need to re submit SUDO MODPROBE ATH_PCI every time it boots up, but it connects fine.

I've tried adding ATH_PCI to /ETC/MODULES.

when I look to see if it's successful, it appears to be, but there is no connection???????

Why????

The strang ething is that I also uninstalled network manager but it connects the first way. wi-fi rader doesnt work!

Is there some kind of conflict???

any ideas anyone plese - I've been at this for hours now.

---

### Post by thebeak on 2008-06-06
forgot to add that im using madwifi to get the card to work

---

### Post by daRealScanMan on 2008-06-06
What brand/model laptop are you using?  Which madwifi driver version, 3366?  Did you follow nicedude's HOWTO?  I, with some others, would recommend wicd to manage the wireless interface and connections.  Did it ever work?  Did you take any updates?  Post the output of:
```
sudo lshw -C network
```
```
sudo iwconfig
```
Sorry for all the questions, but more info needed...

---

### Post by manis on 2008-06-07
Please add module ath_pci in /etc/modules

command is: #sudo modprobe ath_pci ( small letter pls)

edit file /etc/modules

command si #sudo geedit /etc/modules.

add in the last line ath_pci

Hopefullly from now on no need to add ath_pci everytime.

I using toshiba L200-N402 with Antheros AR5007EG.

tk

---

