---
title: "Reinstalling Xorg"
date: 2011-01-23
forum: New to Ubuntu
---

### Post by jerrynewt on 2011-01-23
Screwed up xorg by removing xorg video-all via synaptic (trying to follow suggestion for installing nvidia legacy driver, evidently not that adept at it), and was wondering how to reinstall it via the live cd. Any help would be appreciated -- been working on this for two days with no luck. Have a GeForce4 420 Go rev a3 card in my Toshiba Satelliet Pro running 10.10 and can't seem to get the nvidia driver to install at all. Thanks

---

### Post by mikewhatever on 2011-01-23
Hm .., I thought the Geforce4/5/ didn't have drivers for 10.10 - Xserver1.9.
You can add the cdrom to the lost of software sources with the following:
```
sudo apt-cdrom add

```

---

### Post by jerrynewt on 2011-01-24
Yeah no drivers in 10.10 for my card -- trying to figure out the hack for installing the 96 series .run file but keep getting "install script failed" indication. Had the thing working in Intrepid, but since then I have had no nvidia working on this laptop. Anyone with any ideas -- sure would appreciate it. I'm fixing up this laptop for my daughter in law and sure would be nice to have the nvidia driver working. Thanks again

---

### Post by clhsharky on 2011-01-24
jerrynewt

According to here
[https://launchpad.net/~dajhorn/+archive/nvidia-96](https://launchpad.net/~dajhorn/+archive/nvidia-96)
nvidia-96 driver is available in the maverick-proposed repository

I have not tried this, but it might be worth checking out.


Sharky

---

### Post by jerrynewt on 2011-01-24
Yes I installed the 96 driver from synaptic, rebooted and it came up in 640x800 mode. Tried nvidia-xconfig in terminal as suggested and came up to tty login with no x screen. Had to reconfigure xorg to "nv" instead of "nvidia". System>Administration>Hardware Drivers show 96 driver installed but not in use. Any help would be very welcome. Thanks

---

