---
title: "Help resolving installation issues with Broadcom WIFI adapter?"
date: 2019-02-04
forum: Networking &amp; Wireless
---

### Post by shulist on 2019-02-04
I am an absolute newbie in Ubuntu but am willing to learn how to do this properly. 

I am attempting to run Ubuntu 18.04 from a (live) USB on a **Dell Studio Hybrid 140g** to determine its compatibility and ultimately replace the current OS (Win7). I do have access to a wired ethernet connection but the final state of this computer with Ubuntu installed will have to use WIFI so I need to get this adapter to work.

The Broadcom WIFI adapter details:
```
ubuntu@ubuntu:~$ lspci -vnn -d 14e4:
04:00.0 Network controller [0280]: Broadcom Limited BCM4321 802.11a/b/g/n [14e4:4328] (rev 03)
	Subsystem: Dell Wireless 1500 Draft 802.11n WLAN Mini-card [1028:000a]
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at febfc000 (64-bit, non-prefetchable) [size=16K]
	Memory at fdf00000 (64-bit, prefetchable) [size=1M]
	Capabilities: <access denied>
	Kernel driver in use: b43-pci-bridge
	Kernel modules: ssb
```
What I have encountered is that the kernel does not load the correct drivers and when looking a the boot log I see the following errors:
```
[   26.771018] b43-phy0: Broadcom 4321 WLAN found (core revision 12)
[   26.821059] b43-phy0: Found PHY: Analog 5, Type 4 (N), Revision 2
[   26.821070] b43-phy0: Found Radio: Manuf 0x17F, ID 0x2055, Revision 4, Version 0
[   26.857243] b43 ssb0:0: Direct firmware load for b43/ucode11.fw failed with error -2
[   26.857263] b43 ssb0:0: Direct firmware load for b43/ucode11.fw failed with error -2
[   26.857292] b43 ssb0:0: Direct firmware load for b43-open/ucode11.fw failed with error -2
[   26.857306] b43 ssb0:0: Direct firmware load for b43-open/ucode11.fw failed with error -2
[   26.857309] b43-phy0 [COLOR="#FF0000"]ERROR: Firmware file "b43/ucode11.fw" not found[/COLOR]
[   26.858145] b43-phy0 [COLOR="#FF0000"]ERROR: Firmware file "b43-open/ucode11.fw" not found[/COLOR]
[   26.858968] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[   26.864704] Broadcom 43xx driver loaded [ Features: PNL ]
```

I presume the significant information is:
```
[   26.857309] b43-phy0 ERROR: Firmware file "b43/ucode11.fw" not found
[   26.858145] b43-phy0 ERROR: Firmware file "b43-open/ucode11.fw" not found
```
I have read everything at [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) but I am no closer to an answer for the following:

[LIST=1]
[*]I want to prove that Ubuntu can run correctly on this PC from the USB (this is a constraint)
[*]The missing files (per the boot log) need to be placed on the USB in the correct location to allow a proper boot.
[LIST=1]
[*]Where does one get these missing files?
[*]Where are they to be placed in the USB file structure?
[*]Will Ubuntu 18.04 kernel then correctly use these drivers?
[/LIST]
[*]I want to test all PC functions from a fully functioning live version of Ubuntu before a complete conversion.
[*]Upon a successful test of the item above I want to banish Win7 to the seventh circle of hell.
[/LIST]

---

### Post by jeremy31 on 2019-02-04
In the live version, try the Broadcom Proprietary module available in Additional Drivers, or in terminal do ```
sudo apt update && sudo apt install bcmwl-kernel-source
```
Your wifi card only has partial support from the open source b43 module.  Secure Boot will need to be disabled in BIOS, do not remove or delete any Secure Boot keys

Moved to Networking and Wireless

---

### Post by shulist on 2019-02-05
> **jeremy31 said:**
> Secure Boot will need to be disabled in BIOS, do not remove or delete any Secure Boot keys

Checked all through the BIOS settings and found no entry for Secure Boot so could not change that.

> **jeremy31 said:**
>  ```
sudo apt update && sudo apt install bcmwl-kernel-source
```

Restarted and ran the above command and nothing happened. Restarted the Network Manager and still no change. BTW this change does not get saved on the USB and as such must be done after each reboot. Is there something else I have to do after the **apt install** to activate those drivers?

Is there no way to place these two files: ```
b43/ucode11.fw
b43-open/ucode11.fw 
``` (Which seem like the same file?) on the USB to see if that resolves the problem?

---

### Post by jeremy31 on 2019-02-05
If the wifi isn't showing networks available after ```
sudo apt install bcmwl-kernel-source
```
Then check ```
rfkill list
```
If that shows wifi soft blocked do ```
rfkill unblock all
```

If you want to try the firmware reboot and ```
sudo apt install firmware-b43-installer
sudo modprobe -r b43
sudo modprobe -r ssb
sudo modprobe b43
```

See if that works

---

### Post by shulist on 2019-02-06
So Jeremy31 the results are:
```
**sudo apt install bcmwl-kernel-source**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
bcmwl-kernel-source is already the newest version (6.30.223.271+bdcom-0ubuntu4).
0 upgraded, 0 newly installed, 0 to remove and 481 not upgraded.
```

```
**rfkill list** displays nothing
```

```
**sudo apt install firmware-b43-installer**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package firmware-b43-installer
```

```
**sudo modprobe -r b43** displays nothing
```

```
**sudo modprobe -r ssb**
modprobe: FATAL: Module ssb is in use.
```
```
**sudo modprobe b43** displays nothing
```

So in summary there is completely no change to the WIFI adapter status.

So while I appreciate your advice and blindly followed your instructions it would be helpful to know just exactly what we are doing and what the results indicate so that I learn something from this exercise.

---

### Post by jeremy31 on 2019-02-06
I would reboot and try the ```
sudo apt-get install firmware-b43-installer
sudo modprobe -r b43
```
Then we need to see why ssb can't be removed so check ```
lsmod | grep ssb
```
Post results as that should tell us why it is still in use, but it may work after doing the sudo modprobe -r command to do
```
sudo modprobe b43
```
But I think that didn't work in the past on Live USB/DVD

---

### Post by shulist on 2019-02-06
```
**sudo apt-get install firmware-b43-installer**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package firmware-b43-installer
```
Does this seem weird to you that it cannot find the package?
```
**sudo modprobe -r b43** displays nothing
```
```
**lsmod | grep ssb**
ssb_hcd                16384  0
ssb                    57344  1 ssb_hcd
```
```
**sudo modprobe b43** displays nothing
```
Also here's a bit of new information from the boot log:
```
b43-phy0 ERROR: Firmware file "b43/ucode11.fw" not found
[   27.066649] b43-phy0 ERROR: Firmware file "b43-open/ucode11.fw" not found
[   27.066651] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.
...removed some non-relevant stuff here
[  523.966704] b43-wlan ERROR: Dual-core devices are not supported
[  523.966714] b43: probe of ssb0:0 failed with error -524
```

FYI the Dell Studio Hybrid is an "Intel® Core&#8482;2 Duo CPU T5850 @ 2.16GHz × 2 "
Again no change to the status of the WIFI adapter.

---

