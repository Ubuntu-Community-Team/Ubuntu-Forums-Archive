---
title: "syslog fills with bluetooth messages on Toshiba"
date: 2016-07-27
forum: Networking &amp; Wireless
---

### Post by mathog on 2016-07-27
Ubuntu 14.04.4 on Toshiba PORTEGE R500/Portable PC, BIOS Version 1.60.
Patches are current.

Every 5 seconds one of these shows up in /var/log/syslog

```
Jul 27 14:36:12 porthog kernel: [  770.020267] toshiba_bluetooth: Re-enabling Toshiba Bluetooth
Jul 27 14:36:12 porthog bluetoothd[596]: Unregister path: /org/bluez/596/hci0
Jul 27 14:36:12 porthog bluetoothd[596]: Endpoint unregistered: sender=:1.36 path=/MediaEndpoint/A2DPSink
Jul 27 14:36:12 porthog bluetoothd[596]: Endpoint unregistered: sender=:1.36 path=/MediaEndpoint/A2DPSource
Jul 27 14:36:12 porthog bluetoothd[596]: Endpoint unregistered: sender=:1.36 path=/MediaEndpoint/HFPAG
Jul 27 14:36:12 porthog bluetoothd[596]: Endpoint unregistered: sender=:1.36 path=/MediaEndpoint/HFPHS
Jul 27 14:36:12 porthog kernel: [  770.464577] usb 5-2: USB disconnect, device number 24
Jul 27 14:36:12 porthog bluetoothd[596]: hci0: Set IO Capability (0x0018) failed: Invalid Index (0x11)
Jul 27 14:36:12 porthog kernel: [  770.712210] usb 5-2: new full-speed USB device number 25 using uhci_hcd
Jul 27 14:36:13 porthog kernel: [  770.893260] usb 5-2: New USB device found, idVendor=0930, idProduct=0508
Jul 27 14:36:13 porthog kernel: [  770.893273] usb 5-2: New USB device strings: Mfr=0, Product=0, SerialNumber=0
Jul 27 14:36:13 porthog bluetoothd[596]: hci0: Load Long Term Keys (0x0013) failed: Not Supported (0x0c)
Jul 27 14:36:13 porthog bluetoothd[596]: hci0: Set Powered (0x0005) failed: <unknown status> (0x12)
Jul 27 14:36:13 porthog bluetoothd[596]: Endpoint registered: sender=:1.36 path=/MediaEndpoint/HFPAG
Jul 27 14:36:13 porthog bluetoothd[596]: Endpoint registered: sender=:1.36 path=/MediaEndpoint/HFPHS
Jul 27 14:36:13 porthog bluetoothd[596]: Endpoint registered: sender=:1.36 path=/MediaEndpoint/A2DPSource
Jul 27 14:36:13 porthog bluetoothd[596]: Endpoint registered: sender=:1.36 path=/MediaEndpoint/A2DPSink

```

There are a fair number of threads on this in various other forums and they say to put this in /etc/rc.local

rfkill block bluetooth

but it makes no difference.  There is bug filed in launchpad here:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/750428](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/750428)

which refers to a kernel patch from a year and a half ago that solves this.  However, this patch never seems to make it into the kernel
updates for this release.  (Or if it did, it doesn't work for some reason.)  

Anybody have a solution for this that does not require building and installing a custom kernel?
I do not use bluetooth at all, but I do use wifi, so shutting off the radio with the switch on the
side of the laptop is not going to do it.

Thanks.

---

### Post by jeremy31 on 2016-07-27
Please post the result of ```
lspci -nnk | grep -iA2 net; lsusb
```

---

### Post by mathog on 2016-07-27
> **jeremy31 said:**
> Please post the result of ```
lspci -nnk | grep -iA2 net; lsusb
```

```
01:00.0 Ethernet controller [0200]: Intel Corporation 82573L Gigabit Ethernet Controller [8086:109a]
        Subsystem: Toshiba America Info Systems Device [1179:0001]
        Kernel driver in use: e1000e
02:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection [8086:4229] (rev 61)
        Subsystem: Intel Corporation Vaio VGN-SZ79SN_C [8086:1100]
        Kernel driver in use: iwl4965
Bus 001 Device 003: ID 0930:0c05 Toshiba Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 021: ID 0930:0508 Toshiba Corp. Integrated Bluetooth HCI
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 08ff:1600 AuthenTec, Inc. AES1600
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

Thanks.

---

### Post by jeremy31 on 2016-07-28
This usually works ```
gksudo gedit /etc/udev/rules.d/81-bluetooth-hci.rules
```
Paste this as a single line into the file
```
SUBSYSTEM=="usb", ATTRS{idVendor}=="0930", ATTRS{idProduct}=="0508", ATTR{authorized}="0"
```
Save, exit gedit and reboot

---

### Post by mathog on 2016-07-29
Well, the messages changed, but they are still coming at the same frequency:

```
Jul 29 08:35:52 porthog kernel: [  239.844127] toshiba_bluetooth: Re-enabling Toshiba Bluetooth
Jul 29 08:35:52 porthog kernel: [  240.284549] usb 5-2: USB disconnect, device number 45
Jul 29 08:35:52 porthog kernel: [  240.524142] usb 5-2: new full-speed USB device number 46 using uhci_hcd
Jul 29 08:35:52 porthog kernel: [  240.703022] usb 5-2: New USB device found, idVendor=0930, idProduct=0508
Jul 29 08:35:52 porthog kernel: [  240.703038] usb 5-2: New USB device strings: Mfr=0, Product=0, SerialNumber=0
Jul 29 08:35:52 porthog kernel: [  240.710983] Bluetooth: hci0 urb eb8e6840 failed to resubmit (2)

```

There were also 6 or so lines of error messages at boot which were new.  Unfortunately they flew by so fast that I couldn't read them.

At the most recent boot these are the messages into kern.log that are bluetooth/wifi related:
```

Jul 29 08:27:59 porthog kernel: [   25.993829] Bluetooth: Core ver 2.17
Jul 29 08:27:59 porthog kernel: [   25.996814] NET: Registered protocol family 31
Jul 29 08:27:59 porthog kernel: [   25.996820] Bluetooth: HCI device and connection manager initialized
Jul 29 08:27:59 porthog kernel: [   25.996834] Bluetooth: HCI socket layer initialized
Jul 29 08:27:59 porthog kernel: [   25.996840] Bluetooth: L2CAP socket layer initialized
Jul 29 08:27:59 porthog kernel: [   25.996860] Bluetooth: SCO socket layer initialized
Jul 29 08:27:59 porthog kernel: [   26.026020] [drm] initialized overlay support
Jul 29 08:28:00 porthog kernel: [   26.131656] fbcon: inteldrmfb (fb0) is primary device
Jul 29 08:28:00 porthog kernel: [   26.138982] iwl4965: Intel(R) Wireless WiFi 4965 driver for Linux, in-tree:
Jul 29 08:28:00 porthog kernel: [   26.138984] iwl4965: Copyright(c) 2003-2011 Intel Corporation
Jul 29 08:28:00 porthog kernel: [   26.139052] iwl4965 0000:02:00.0: can't disable ASPM; OS doesn't have ASPM control
Jul 29 08:28:00 porthog kernel: [   26.139283] iwl4965 0000:02:00.0: Detected Intel(R) Wireless WiFi Link 4965AGN, REV=0x4
Jul 29 08:28:00 porthog kernel: [   26.184441] iwl4965 0000:02:00.0: device EEPROM VER=0x36, CALIB=0x5
Jul 29 08:28:00 porthog kernel: [   26.292862] Bluetooth: RFCOMM TTY layer initialized
Jul 29 08:28:00 porthog kernel: [   26.292874] Bluetooth: RFCOMM socket layer initialized
Jul 29 08:28:00 porthog kernel: [   26.292883] Bluetooth: RFCOMM ver 1.11
Jul 29 08:28:00 porthog kernel: [   26.293931] iwl4965 0000:02:00.0: Tunable channels: 11 802.11bg, 13 802.11a channels
Jul 29 08:28:00 porthog kernel: [   26.294050] iwl4965 0000:02:00.0: irq 44 for MSI/MSI-X
Jul 29 08:28:00 porthog kernel: [   26.412354] usbcore: registered new interface driver btusb
Jul 29 08:28:00 porthog kernel: [   26.445994] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Jul 29 08:28:00 porthog kernel: [   26.445996] Bluetooth: BNEP filters: protocol multicast
Jul 29 08:28:00 porthog kernel: [   26.446008] Bluetooth: BNEP socket layer initialized
Jul 29 08:28:00 porthog kernel: [   26.525525] iwl4965 0000:02:00.0: loaded firmware version 228.61.2.24
Jul 29 08:28:00 porthog kernel: [   26.628287] ieee80211 phy0: Selected rate control algorithm 'iwl-4965-rs'

```

Thanks.

---

### Post by jeremy31 on 2016-07-29
I would look in BIOS to see if there is an option to disable bluetooth.  Some of the errors you have with USB devices disconnecting and reconnecting happen to me when I have a few things plugged into my USB hub but looking at a diagram of that computer the internal bluetooth is connected by a cable to a USB bus

---

### Post by mathog on 2016-07-30
> **jeremy31 said:**
> I would look in BIOS to see if there is an option to disable bluetooth.  Some of the errors you have with USB devices disconnecting and reconnecting happen to me when I have a few things plugged into my USB hub but looking at a diagram of that computer the internal bluetooth is connected by a cable to a USB bus

No such option.

Let me see if I understand this.  Every 5 seconds the system scans the USB for new devices.  It sees the bluetooth and tries to load the driver or in some way enable it.  This fails.  The udev file you suggested prevents it from loading the bluetooth - but it does not stop the USB scan.  Is there a command to make it ignore that USB device, or is that what the udev file is supposed to do?

Even though I have tried to kill bluetooth, lsmod still shows:

bluetooth             342208  11 bnep,btusb,rfcomm
toshiba_bluetooth      12748  0 

If the bluetooth module was blacklisted would that help at all?

---

### Post by jeremy31 on 2016-07-30
Blacklisting the bluetooth module wouldn't change this, removing the bluetooth module should stop it.

The udev command when used on my Ubuntu 14.04 laptop would keep the bluetooth from working when putting rfkill block bluetooth in rc.local didn't work

---

### Post by mathog on 2016-07-31
> **jeremy31 said:**
> Blacklisting the bluetooth module wouldn't change this, removing the bluetooth module should stop it.

Really, how do those approaches differ?  Either way no module should load.  Does the USB scan look around to see what modules exist, rather than to see which modules are loadable?

There are 5 modules listed two posts up.  Remove which of the corresponding ko files from /lib/modules/(current_kernel) ?

Even if this works it is not an ideal solution since the software updates install new kernels pretty frequently, and the fix will fall away after a couple of updates.

Thanks.

---

### Post by jeremy31 on 2016-08-01
If you blacklisted the bluetooth module you would still have
```
Jul 29 08:35:52 porthog kernel: [  240.284549] usb 5-2: USB disconnect, device number 45
Jul 29 08:35:52 porthog kernel: [  240.524142] usb 5-2: new full-speed USB device number 46 using uhci_hcd
Jul 29 08:35:52 porthog kernel: [  240.703022] usb 5-2: New USB device found, idVendor=0930, idProduct=0508
Jul 29 08:35:52 porthog kernel: [  240.703038] usb 5-2: New USB device strings: Mfr=0, Product=0, SerialNumber=0
```

If the module is removed then there is nothing to be discovered

---

### Post by mathog on 2016-08-02
Disabled modules by renaming them from .ko to .ko disabled, in this order, cumulatively, rebooting at each step:

bluetooth
btusb
toshiba_bluetooth

On the 3rd step it finally stopped logging messages.  With just the 1st, or 1st and 2nd it was still logging messages (different ones, but still) every 5 seconds.  This with the udev rules file still in place and the changes to rc.local.

Anyway, with all 3 renamed the messages go away finally, but it really shouldn't be necessary to go this far.  If a system cannot be fully shut down without resorting to hiding modules from the kernel something is broken somewhere.   I guess what is going on here is that with all 3 of these modules not loaded it doesn't create /sys/class/bluetooth, which cuts in before the /etc/udev/rules.d/ file, which must be consulted only after the USB scan sees the USB bluetooth device.  Currently "lsusb" does not show the bluetooth device.  There are many posts claiming that the udev file alone should be sufficient, as in:

[https://projectgus.com/2014/09/blacklisting-a-single-usb-device-from-linux/](https://projectgus.com/2014/09/blacklisting-a-single-usb-device-from-linux/)

but it doesn't do the trick.  

No way to tell the USB scan not to look at a particular address, rather than to let it look and then tell it after the fact "don't touch that"?

Thanks.

---

### Post by jeremy31 on 2016-08-02
What kernel are you using ```
uname -a
```
It seems that the patch mentioned in the bug report is in the Ubuntu 4.4 kernel
You should be able to blacklist toshiba_bluetooth with ```
echo "blacklist toshiba_bluetooth" | sudo tee /etc/modprobe.d/tosh-blue.conf
``` instead of renaming kernel modules
When I have access to my other laptop I will see if the 4.4 kernel source for the toshiba_bluetooth module will compile in older kernels as it may be possible to make a fix using DKMS

---

### Post by mathog on 2016-08-03
> **jeremy31 said:**
> 
If the module is removed then there is nothing to be discovered

I get how it works now, I'm just saying that it would be better if there was, for instance something along
these lines (made up command)

    udev_config module=bluetooth discover=no

or something like that, so that the solution didn't come down to hiding driver modules be renaming or removing them.  Especially better if the command stayed active over a kernel upgrade, which on this machine is likely some time in the next couple of weeks, with the usual Ubuntu updates.

---

### Post by jeremy31 on 2016-08-03
Blacklisting toshiba_bluetooth should prevent the kernel from loading the module and it will work after kernel updates.  You could try 16.04 as it's kernel has the fix or wait until [https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack) shows how to update to the xenial HWE

---

### Post by mathog on 2016-08-04
Everything was reset to the original state (no change to rc.local, no bluetooth file in /etc/udev.d, modules back to original names) and then blacklisted just the toshiba_bluetooth module using the command you supplied.  Rebooted.  No messages in /var/log/syslog.  Some bluetooth modules do load

```
bluetooth             342208  22 bnep,btusb,rfcomm

```
but these do not trigger the syslog messages.

Since I never use bluetooth this seems like the best fix for me.

The system is a 14.04 LTS system, current kernel is 3.13.0-92-generic. 

Thanks.

---

