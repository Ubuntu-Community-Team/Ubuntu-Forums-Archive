---
title: "HELP..10.04 issue with kernel"
date: 2010-09-13
forum: New to Ubuntu
---

### Post by sn00kst3r on 2010-09-13
****I am having an issue after trying to change my wireless settings and keyring security.  This is now showing up in my syslog and continually loops. My wired connection is still working fine but I can no longer get any wireless networks.  Any help would be greatly appreciated.

This is what I am seeing in the syslog:

ep 12 16:46:26 UBUT60 wpa_supplicant[783]: Association request to the driver failed
Sep 12 16:46:26 UBUT60 wpa_supplicant[783]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Sep 12 16:46:27 UBUT60 kernel: [ 1103.153787] end_request: I/O error, dev fd0, sector 0
Sep 12 16:46:27 UBUT60 kernel: [ 1103.153801] Buffer I/O error on device fd0, logical block 0

---

### Post by philinux on 2010-09-13
Not sure about your wireless but device fd0 is the floppy drive. If you haven't got one the disable it in the bios.

---

### Post by ibuclaw on 2010-09-13
It would help if you told us what wireless device / driver you are using.

If you are unsure, the entire output of:
```
lspci -k
```
and
```
iwconfig
```
should suffice.

Logging of wireless events would also greatly help. If the wireless device is a USB dongle, remove it, and run:
```
iw event -t
```
You may need to install iw first...

While that is running, insert / activate the device and try to connect to the AP you want to connect to. As this is going, you should see log messages being outputted from the window where you ran 'iw'.

This information may also help tell us what is going on.

Also, have you tried disabling NetworkManager and connecting manually via wpa_supplicant? Incase the issue isn't a kernel issue at all - but a problem with NM.

Regards

---

### Post by sn00kst3r on 2010-09-20
> **philinux said:**
> Not sure about your wireless but device fd0 is the floppy drive. If you haven't got one the disable it in the bios.

Thanks for the help very much.  Turns out that disabling the floppy drive in the bios, since I don't have one anyway, was the correct thing to do and it resolved the revolving log error.  I was able to connect to another wireless point and once I was able to prove it worked outside of my network, well then it was just a matter of getting it resolved in my network. Turns out the wireless access point that I have connected to my firewall/router has an issue and is not authenticating properly. Thanks again for the reply!

---

### Post by sn00kst3r on 2010-09-20
> **ibuclaw said:**
> It would help if you told us what wireless device / driver you are using.

If you are unsure, the entire output of:
```
lspci -k
```
and
```
iwconfig
```
should suffice.

Logging of wireless events would also greatly help. If the wireless device is a USB dongle, remove it, and run:
```
iw event -t
```
You may need to install iw first...

While that is running, insert / activate the device and try to connect to the AP you want to connect to. As this is going, you should see log messages being outputted from the window where you ran 'iw'.

This information may also help tell us what is going on.

Also, have you tried disabling NetworkManager and connecting manually via wpa_supplicant? Incase the issue isn't a kernel issue at all - but a problem with NM.

Regards


Thank you for the support and assistance. I was finally able to try my system on another wireless network and had no issues connecting.  Turns out my wireless access point is going bad and will only authenticate for a few minutes and then shuts down.  I will try to re-flash it and if that does not work, then back to the store for a new one!

Thanks again for the help!:guitar:

---

