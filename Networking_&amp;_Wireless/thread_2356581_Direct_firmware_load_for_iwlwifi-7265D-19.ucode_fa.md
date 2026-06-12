---
title: "Direct firmware load for iwlwifi-7265D-19.ucode failed with error -2"
date: 2017-03-24
forum: Networking &amp; Wireless
---

### Post by vidar-vidnes on 2017-03-24
Hello

I have a Intel NUC mini PC which has stopped working.
The dmesg reflects the error message

Direct firmware load for iwlwifi-7265D-19.ucode failed with error -2

I also see the following record.:

```
[   21.551629] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   21.551637] Bluetooth: BNEP filters: protocol multicast
[   21.551649] Bluetooth: BNEP socket layer initialized
[   29.308165] IPv6: ADDRCONF(NETDEV_UP): enp3s0: link is not ready
[   29.308484] r8169 0000:03:00.0: Direct firmware load for rtl_nic/rtl8168h-2.fw failed with error -2
[   29.308492] r8169 0000:03:00.0 enp3s0: unable to load firmware patch rtl_nic/rtl8168h-2.fw (-2)
[   29.316625] r8169 0000:03:00.0 enp3s0: link down
[   29.316719] IPv6: ADDRCONF(NETDEV_UP): enp3s0: link is not ready
[   66.386004] Bluetooth: RFCOMM TTY layer initialized
[   66.386083] Bluetooth: RFCOMM socket layer initialized
[   66.386096] Bluetooth: RFCOMM ver 1.11
[10447.996323] IPv6: ADDRCONF(NETDEV_UP): enp3s0: link is not ready
[10448.006129] r8169 0000:03:00.0 enp3s0: link down
```

This has been working well before and lately I have had no new installations or anything that could cause this error. However, I have been using blue-toot for a week or so, something which I have not done before on this device. I guess it is a combined wireless module (rtl8168h) and wonder if the device has some weakness with the wireless module that comes with the NUC devices or if this is some update that has broken connectivity to wifi,  I have seen that mentioned by others some years ago in other forums.

I am not able to connect or see any wifi 


Please see attached file for the complete dmesg output

[ATTACH]274293[/ATTACH]

---

### Post by jeremy31 on 2017-03-24
If you have a connection over ethernet ```
sudo apt-get install --reinstall linux-firmware
```
Reboot

---

