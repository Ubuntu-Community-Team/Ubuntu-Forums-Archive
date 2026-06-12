---
title: "[kubuntu] Specify preferred wifi adapter"
date: 2019-10-07
forum: Networking &amp; Wireless
---

### Post by SeijiSensei on 2019-10-07
Kubuntu 19.10

I have two wifi adapters in this laptop, one a built-in Intel Centrino and the other an Edimax USB adapter. I would like to use the Edimax by default, but Kubuntu always chooses the Centrino.  I don't want to turn off the adapter in the BIOS since I believe that would also turn off Bluetooth.  Is there a way to specify a preference between the adapters in the OS?  The standard network configuration tool doesn't even mention the adapters.

---

### Post by praseodym on 2019-10-07
What about an udev rule? Don't know if it still works:

```
kdesudo kate /etc/udev/rules.d/10-wlan-stick.rules 
```
Add
```

ACTION=="add", GOTO="device_check"
ACTION=="remove", GOTO="onboard_load"

LABEL="device_check"

SUBSYSTEM=="net", KERNEL=="[COLOR="#FF0000"]wlan1[/COLOR]", RUN+="/sbin/modprobe -rf [COLOR="#FF0000"]ipw2200[/COLOR]"

GOTO="rules_end"

LABEL="onboard_load"

SUBSYSTEM=="net", KERNEL=="[COLOR="#FF0000"]wlan[/COLOR]*", RUN+="/sbin/modprobe [COLOR="#FF0000"]ipw2200[/COLOR]"

LABEL="rules_end"
```
Change the module and interface names of the internal card! Then reboot.

---

