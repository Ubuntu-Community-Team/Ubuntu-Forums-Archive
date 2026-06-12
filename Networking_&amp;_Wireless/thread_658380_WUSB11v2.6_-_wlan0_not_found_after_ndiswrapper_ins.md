---
title: "WUSB11v2.6 - wlan0 not found after ndiswrapper installed and hard crash"
date: 2008-01-04
forum: Networking &amp; Wireless
---

### Post by cifdtruckie on 2008-01-04
I installed ndiswrapper, added netusb.inf, and blacklisted at76_usb.  I ran ndiswrapper-m.  I rebooted, and it seemed to find the adapter and everything worked fine for about 30 seconds, when the system hard-crashed (I'm assuming everything worked fine, as Network Manager had "wireless connection" as an option - it's all I was able to check before the crash.

When I attempted a hard reboot, the system hung on the boot screen.  I hard rebooted again, and now it cannot find my wireless adapter.

ndiswrapper -l returns the following:
```
netusb : driver installed
        device (077B:2219) present (alternate driver: at76_usb)

```
... even though I blacklisted at76_usb.

I found the following entries in the system log:
```
Jan  4 14:15:51 chris-desktop kernel: [  325.725035] ndiswrapper (mp_init:216): couldn't initialize device: C0000001
Jan  4 14:15:51 chris-desktop kernel: [  325.725044] ndiswrapper (pnp_start_device:439): Windows driver couldn't initialize the device (C0000001)
Jan  4 14:15:51 chris-desktop kernel: [  325.725057] ndiswrapper (mp_halt:259): device efae0500 is not initialized - not halting
Jan  4 14:15:51 chris-desktop kernel: [  325.725060] ndiswrapper: device eth%%d removed
Jan  4 14:15:51 chris-desktop kernel: [  325.725078] ndiswrapper: probe of 3-2:1.0 failed with error -22
```

Any suggestions?

---

### Post by Teronap on 2008-01-05
I had the same problem with exactly the same card, and you don't need ndiswrapper as it has a builtin driver, so uninstall ndiswrapper(synaptic, apt-get, aptitude, whichever you prefer) 
I also found that network manager couldn't see my wireless card.
Check what encryption you have, if you have anything other than WEP, sorry, I can't help you, but if you have WEP, check on your router whether it is set to anything called shared mode or something like that, and then type in 
```

sudo ifdown wlan0
sudo iwconfig wlan0 essid <you network name>
sudo iwconfig wlan0 channel <your network channel here>
sudo iwconfig wlan0 enc <your WEP key here>
sudo iwconfig wlan0 enc <restricted if it is in shared mode, open otherwise>
sudo ifup wlan0

```
Sorry about all the code, but i'm more comfortable with the terminal.  You can find the WEP key, the mode and the channel in the configuration of your router
Hope this helps!

---

