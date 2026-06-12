---
title: "Ubuntu bluetooth disabled(Qualcomm Atheros AR3012 Bluetooth 4.0 QS)"
date: 2014-12-18
forum: Networking &amp; Wireless
---

### Post by DongHyun_Hong on 2014-12-18
I'm noob in Ubuntu. I'm using Ubuntu 14.04.01 LTS and my laptop is samsung ATIV 9 Lite(NT910S3T-K81S) (Intel i3 4020Y)
My laptop use Qualcomm Atheros AR3012 bluetooth chipset and ubuntu can't find it.
when i first format and install it, bluetooth is working, but when i reboot, it becomes disabled. i've tried Blueman Bluetooth manager, but it doesn't work. I've tried
$ rfkill list
but all was unblocked. 
i've also tried sudo aptitude install firmware-atheros. How can i make my bluetooth work? I'm using samsun's Bluetooth Mouse:S Action Mouse. Plus, how can i autoconnect mouse when i reboot my laptop or my laptop goes to sleep mode?

---

### Post by jeremy31 on 2014-12-18
What is the result of ```
lsusb
```
The firmware is part of linux-firmware and should be in /lib/firmware/ar3k/
These chips do have some issues with xhci and do not work everytime after a reboot.  The solution to the xhci is to compile a kernel with xhci built as a module so it can be blacklisted or it may be possible in some BIOS to not support xhci
[http://permalink.gmane.org/gmane.linux.bluez.kernel/50372](http://permalink.gmane.org/gmane.linux.bluez.kernel/50372)

---

### Post by DongHyun_Hong on 2014-12-19
> **jeremy31 said:**
> What is the result of ```
lsusb
```
The firmware is part of linux-firmware and should be in /lib/firmware/ar3k/
These chips do have some issues with xhci and do not work everytime after a reboot.  The solution to the xhci is to compile a kernel with xhci built as a module so it can be blacklisted or it may be possible in some BIOS to not support xhci
[http://permalink.gmane.org/gmane.linux.bluez.kernel/50372](http://permalink.gmane.org/gmane.linux.bluez.kernel/50372)

kitakami@kitakami-910S3G-910S3T:~$ lsusb
Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 004: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 002 Device 003: ID 2232:1054  
Bus 002 Device 007: ID 0cf3:3004 Atheros Communications, Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

this is what i lsusb my Laptop

---

### Post by jeremy31 on 2014-12-19
How about the result of ```
ls /lib/firmware/ar3k
``` and ```
dmesg | grep firmware
```

---

### Post by DongHyun_Hong on 2014-12-19
> **jeremy31 said:**
> How about the result of ```
ls /lib/firmware/ar3k
``` and ```
dmesg | grep firmware
```

kitakami@kitakami-910S3G-910S3T:~$ ls /lib/firmware/ar3k
AthrBT_0x01020001.dfu  AthrBT_0x41020000.dfu    ramps_0x01020201_40.dfu
AthrBT_0x01020200.dfu  ramps_0x01020001_26.dfu  ramps_0x11020000_40.dfu
AthrBT_0x01020201.dfu  ramps_0x01020200_26.dfu  ramps_0x31010000_40.dfu
AthrBT_0x11020000.dfu  ramps_0x01020200_40.dfu  ramps_0x41020000_40.dfu
AthrBT_0x31010000.dfu  ramps_0x01020201_26.dfu

kitakami@kitakami-910S3G-910S3T:~$ dmesg | grep firmware
[    1.741516] psmouse serio1: elantech: assuming hardware version 4 (with firmware version 0x575f05)
[ 5472.461954] usb 2-4: device firmware changed
[ 5477.856026] Bluetooth: Error in firmware loading err = -110,len = 448, size = 4096

---

### Post by Pilot6 on 2014-12-19
This module  [COLOR=#000000] 0cf3:3004 is listed in the kernel as AR3011, not 3012.
This may be wrong.[/COLOR]

---

### Post by Pilot6 on 2014-12-19
This is definitely an error.
[https://www.atheros.cz/atheros-inf-file.php?inf=365&chipset=77&system=7](https://www.atheros.cz/atheros-inf-file.php?inf=365&chipset=77&system=7)

I can fix it, but you need to create a bugreport.
Please run

ubuntu-bug linux

in terminal. Then give description of this bug there.
Then post here URL of this bugreport.

---

### Post by jeremy31 on 2014-12-19
> **Pilot6 said:**
> This module  [COLOR=#000000] 0cf3:3004 is listed in the kernel as AR3011, not 3012.
This may be wrong.[/COLOR]

I can get mine to work ```
[  103.412065] usb 3-8: New USB device found, idVendor=0cf3, idProduct=3004[  103.412074] usb 3-8: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[  103.412080] usb 3-8: Product: Bluetooth USB Host Controller
[  103.412084] usb 3-8: Manufacturer: Atheros Communications
[  103.412087] usb 3-8: SerialNumber: Alaska Day 2006
jeremy@jeremy-Lenovo-G710 ~ $ lsusb | grep Atheros
Bus 003 Device 010: ID 0cf3:3004 Atheros Communications, Inc. AR3012 Bluetooth 4.0

```

It has been posted that the firmware upload is attempted too early and fails, so I just blacklisted btusb and ath3k and used /etc/rc.local to modprobe them in and with 5 shutdown/reboot cycles it has worked everytime.  Before doing that, bluetooth might have worked once every 5-7 restarts

---

### Post by Pilot6 on 2014-12-19
But still did you look into kernel source?

---

### Post by Pilot6 on 2014-12-19
And did you try to change it to AR3012?

---

### Post by jeremy31 on 2014-12-19
> **Pilot6 said:**
> And did you try to change it to AR3012?

I didn't have to and I just installed 3.13.0-43 on this machine today

---

### Post by DongHyun_Hong on 2014-12-20
what do you mean? can you say it more easier? i'm really noob

---

### Post by jeremy31 on 2014-12-20
So far, what has worked for me, in terminal ```
echo "blacklist ath3k" | sudo tee /etc/modprobe.d/ath3k.conf
```
Then edit rc.local ```
gksudo gedit /etc/rc.local
``` 
Now just above the line that says ```
exit 0
``` put ```
modprobe ath3k
``` save, exit program and reboot

---

### Post by wijit on 2015-04-03
This seems to be very similar to my Bluetooth headset problem. Would you please advice on blacklisting and modprobing for I really don't know how to do it?

---

### Post by jeremy31 on 2015-04-03
> **wijit said:**
> This seems to be very similar to my Bluetooth headset problem. Would you please advice on blacklisting and modprobing for I really don't know how to do it?

What is the result of ```
lspci -nnk | grep 280; lsusb; uname -a; lsmod | grep bluetooth; dmesg | grep -i firmware
```

Are you using Blueman?  There is a known bug in it that unloads module-bluetooth-discover and you need to load it for audio devices to work with ```
sudo pactl load-module module-bluetooth-discover
```

---

