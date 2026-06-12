---
title: "HP Stream - Wireless problem."
date: 2016-03-12
forum: Networking &amp; Wireless
---

### Post by gackthugo on 2016-03-12
Hello community,

I'm having a huge network problem in my HP Stream with an RTL8723BE.
It works for 5 minutes and then i loose connection to the network although it shows an active icon.

Before this i switched the antenna wire to the 2nd pin 'cause in the first one i couldn't catch any networks. This HP has only one network wire...

Hope that the info in the attachment helps.

Thank you all for the help...

---

### Post by Hadaka on 2016-03-12
Hi, try this..
[http://askubuntu.com/questions/717685/realtek-wifi-card-rtl8723be-not-working-properly/722904#722904](http://askubuntu.com/questions/717685/realtek-wifi-card-rtl8723be-not-working-properly/722904#722904)
also please open a terminal ctrl/alt/t then copy and paste
```
sudo iw reg set PT
sudo sed -i 's/^REG.*=$/&PT/' /etc/default/crda
```
thanks.

---

### Post by gackthugo on 2016-03-13
Hi there,

I did the process that you posted but not like it's in the page. First "rtlwifi-new-dkms" was not installed so it was no removed.

After that, i installed "git" but "build-essentials" was "build-essential" in my system (Mint17.3). Then i installed "rtlwifi_new".

[FONT=arial]The funny part was here. The antenna was moved to the second pin in the wireless connector like i said before, but after[/FONT] "sudo modprobe -rv rtl8723be & sudo modprobe -v rtl8723be ant_sel=X" [FONT=arial]the best result was with[/FONT] "ant_sel=1"! [FONT=arial]After that i did the other commands and the region one you provided[/FONT].

[FONT=arial]After testing a bit, the connection was not lost like i explained in the first post but now, after awhile it disconnects and shows the disconnect icon and my home network disappears.
I need to deactivate/activate the wireless to work again...

Is something missing?

Thank you...[/FONT]

---

### Post by jeremy31 on 2016-03-13
Post the result of ```
modinfo -p rtl8723be
``` and ```
for i in /sys/module/rtl8723be/parameters/*; do echo $i; cat $i; done
```

I edited the askubuntu answer to fix the typo on build-essential, thanks

---

### Post by gackthugo on 2016-03-13
Hope it helps. (modinfo cat $i showed no results)

**modinfo -p rtl8723be**
swlps: (bool)
swenc:using hardware crypto (default 0 [hardware])
 (bool)
ips:using no link power save (default 1 is open)
 (bool)
fwlps:using linked fw control power save (default 1 is open)
 (bool)
msi:Set to 1 to use MSI interrupts mode (default 0)
 (bool)
debug:Set debug level (0-5) (default 0) (int)
disable_watchdog:Set to 1 to disable the watchdog (default 0)
 (bool)
ant_sel:Set to 1 or 2 to force antenna number (default 0)
 (int)
-----------------------------------------------------------------------------
**modinfo i in /sys/module/rtl8723be/parameters/***
modinfo: ERROR: Module i not found.
modinfo: ERROR: Module in not found.
modinfo: ERROR: Module /sys/module/rtl8723be/parameters/ant_sel not found.
modinfo: ERROR: Module /sys/module/rtl8723be/parameters/debug not found.
modinfo: ERROR: Module /sys/module/rtl8723be/parameters/disable_watchdog not found.
modinfo: ERROR: Module /sys/module/rtl8723be/parameters/fwlps not found.
modinfo: ERROR: Module /sys/module/rtl8723be/parameters/ips not found.
modinfo: ERROR: Module /sys/module/rtl8723be/parameters/msi not found.
modinfo: ERROR: Module /sys/module/rtl8723be/parameters/swenc not found.
modinfo: ERROR: Module /sys/module/rtl8723be/parameters/swlps not found.
-----------------------------------------------------------------------------
**modinfo echo $i**
filename:       /lib/modules/3.19.0-32-generic/kernel/drivers/misc/echo/echo.ko
version:        0.3.0
description:    Open Source Line Echo Canceller
author:         David Rowe
license:        GPL
srcversion:     2DF0B5CFC61215C2D89C7B4
depends:        
intree:         Y
vermagic:       3.19.0-32-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        0C:8B:EF:E0:C1:E2:89:E4:D8:99:09:26:11:7A:DA:3B:DF:EB:41:9C
sig_hashalgo:   sha512
-----------------------------------------------------------------------------

---

### Post by jeremy31 on 2016-03-13
You just might need to use ```
echo "options rtl8723be fwlps=N" | sudo tee /etc/modprobe.d/rtl8723be.conf
```

Reboot

You may have installed an earlier version of rtlwifi_new that prevented the new one from downloading as the modprobe -p results do not show that option

---

### Post by gackthugo on 2016-03-13
Ok done.

As for now it is still working 'cause before in 10 minutes the connection would disconect.

I'll post more info after testing a bit more time.

Thanks a lot.

---

