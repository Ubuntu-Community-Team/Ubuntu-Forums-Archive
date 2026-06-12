---
title: "Atheros 5007eg Toshiba Satellite A215-S4817 On Hardy 64bit"
date: 2008-06-16
forum: Networking &amp; Wireless
---

### Post by Jgrant05 on 2008-06-16
This is what worked on my Toshiba Satellite A215-S4817 with the ATHEROS 5007EG. Give it try.  At this point what do ya got to loose.

Download this 64-bits driver:
```
wget [http://blakecmartin.googlepages.com/ar5007eg-64-0.2.tar.gz](http://blakecmartin.googlepages.com/ar5007eg-64-0.2.tar.gz)
```

Extract the archives:
```
tar xvf ar5007eg-*.tar.gz
```

Make sure you have your kernel headers and the build essential package.(I just used Synaptic.)
```
sudo aptitude update && sudo aptitude install linux-headers-$(uname -r) build-essential

```
Blacklist the ath_pci kernel module (it doesn't support the chipset).
```
echo "blacklist ath_pci" | sudo tee -a /etc/modprobe.d/blacklist
```

Download ndiswrapper with synaptic.

Install the Windows drivers (using ndiswrapper):
```
pushd */ar5007eg/
sudo ndiswrapper -i net5211.inf
popd
```

Make sure ndiswrapper loads up every time we start Linux:
```
sudo modprobe ndiswrapper
echo "ndiswrapper" | sudo tee -a /etc/modules
```


Use idea #1 for the quote. If the ath_pci has been blacklisted you will more than likely not need the line (sudo modeprobe -r ath_pci)

> **lswest said:**
> i assume you're running on 8.04?
idea #1: make a script like this: right-click anywhere, desktop will probably be your first choice, choose "new file" and "empty document" then enter this into the file: ```
#!/bin/bash
sudo modprobe -r ath_pci
sudo modprobe -r ndiswrapper
sudo modprobe ndiswrapper
``` when saving, make sure that it ends in ".sh" and make it executable (by going to properties and under "permissions" check the "allow executing as a binary file" option.  Then run it to see if it gets your wireless working.  If it does do this:```
sudo cp /path/to/script /etc/init.d/wireless.sh #you can call it anything, i called it wireless.sh for simplicity's sake
sudo chmod 755 /etc/init.d/wireless.sh
sudo update-rc.d wireless.sh defaults #this will make it run at boot
```  Hope it helps (don't have an atheros card, so i can't test it)

idea #2: otherwise you can set a script to install the drivers, such as ```
#!/bin/bash
sudo ndiswrapper -i /path/to/driver/
sudo modprobe ndiswrapper
``` and save it in a script, then make it run at boot like i listed above.

idea #3: Also, check to see if you blacklisted the ath_pci driver by doing ```
sudo gedit /etc/modprobe.d/blacklist
``` and seeing if there is a line that read "blacklist ath_pci" if it doesn't exist, add it.

good luck,
Lswest

**Note** the ideas are numbered according to when i thought of them, not in what order you should try them.

I did this as well. (Not sure if this step is needed so included it anyways.)

> **Aearenda said:**
> It seems to me that if the blacklist entry is right, the rest of lswest's steps are unnecessary. However, I have seen a problem with some wireless cards such that they only start up on the second attempt - so 
```
ifdown wlan0
ifup wlan0
```
added to /etc/rc.local will make it work.

I used gedit.
```
sudo gedit /etc/rc.local
```

Restart or power off & power on the computer. (I did both this several times to check for working consistence.)

Put the BIG @$&%#! HAMMER back in the toolbox.  Smoke if you got a good one. Then go out to your favorite wifi spot get your internet there. Show the world the greatness of UBUNTU! Ooh yeah the best part no more @$&%#! wires.

---

### Post by mbarvian on 2008-06-30
Nice post!  I don't have this laptop, but this looks pretty useful if I did :D

---

