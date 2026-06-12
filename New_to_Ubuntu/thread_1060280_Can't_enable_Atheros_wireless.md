---
title: "Can't enable Atheros wireless"
date: 2009-02-04
forum: New to Ubuntu
---

### Post by robbyappleton on 2009-02-04
I just installed 8.10 on a Toshiba Satellite P205d laptop, with Atheros wireless. Ubuntu detected and installed drivers for my wireless card right away, but I've been unable to use it. The network manager connects to wired networks without any problem, but I can't connect to or see wireless networks. 

I can't find an option in any of the menus to enable wireless, and I don't really know my way around the terminal yet, so any help on this would be appreciated.

---

### Post by LowSky on 2009-02-04
did you reboot?

---

### Post by 5BallJuggler on 2009-02-04
The latest Linux kernel as a few is issues both with wired and wireless connections, try this ->

[http://ubuntuforums.org/showthread.php?t=1054629](http://ubuntuforums.org/showthread.php?t=1054629)

Hopefully it will solve your problems

---

### Post by jerome1232 on 2009-02-04
Personally the only thing that worked for my lappy with an atheros chipset was madwifi.

[http://madwifi.org/](http://madwifi.org/)

---

### Post by stchman on 2009-02-04
> **robbyappleton said:**
> I just installed 8.10 on a Toshiba Satellite P205d laptop, with Atheros wireless. Ubuntu detected and installed drivers for my wireless card right away, but I've been unable to use it. The network manager connects to wired networks without any problem, but I can't connect to or see wireless networks. 

I can't find an option in any of the menus to enable wireless, and I don't really know my way around the terminal yet, so any help on this would be appreciated.

Please post an lspci output here in this thread.

---

### Post by nothingspecial on 2009-02-04
Go to system > administration > hardware drivers then disable anything in there.

Then

```
sudo apt-get install linux-backports-modules-intrepid-generic
```

To load the driver

```
sudo modprobe ath5k
```

To make it load everytime you boot

```
gksudo gedit /etc/modules
```

and add

```
ath5k
```

To the end of the file

save
close
reboot


_______

---

### Post by Mriswithe on 2009-02-04
If the result of running ```
lspci
``` returns something like the following:
```

02:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
```

key info in that is the ar242x part, then this link should make your wifi work. 

[http://madberry.org/2008/11/how-to-get-atheros-ar242x-to-work-on-810-intrepid-ibex/]("http://madberry.org/2008/11/how-to-get-atheros-ar242x-to-work-on-810-intrepid-ibex/")

---

### Post by robbyappleton on 2009-02-06
Thanks for all the ideas, everyone. Mriswithe nailed it. I followed the steps on the link you posted before trying anything else, and that fixed my problem.

---

### Post by robino on 2009-02-06
> **nothingspecial said:**
> 
```
sudo modprobe ath5k
``` 

which gives me 

```
 WARNING: Error inserting lbm_cw_mac80211 (/lib/modules/2.6.27-11-generic/updates/lbm_cw-mac80211.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting ath5k (/lib/modules/2.6.27-11-generic/updates/ath5k.ko): Unknown symbol in module, or unknown parameter (see dmesg)
```

:/

anyone has any suggestions?

---

### Post by carml on 2009-02-06
Did you try to use Ndiswrapper and load so the driver for Windows?
It works for me. :)

---

### Post by robino on 2009-02-06
> **carml said:**
> Did you try to use Ndiswrapper and load so the driver for Windows?
It works for me. :)

Just got it working actually. Had to blacklist 2 other modules and reboot.

 ```
sudo nano /etc/modprobe.d/blacklist 
```

and add these lines

```
#blacklist to make ath5k wifi work
blacklist ath_hal
blacklist ath_pci

```

---

### Post by carml on 2009-02-06
Glad to know that,actually you had had to disable these driver also with Ndiswrapper.

---

