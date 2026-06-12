---
title: "Lenovo g710 and Ubuntu 14.04 Bluetooth not working"
date: 2015-12-07
forum: Networking &amp; Wireless
---

### Post by petarivanov1985 on 2015-12-07
Hello all,

I have Lenovo G710 and Ubuntu 14.04 installed on it. My Wireless is working ok, but Bluetooth - not. When I go to system settings I can`t turn on my bluetooth. Attached is what I see when open Bluetooth settings. Any help is appreciated. 

Thanks in advance!

---

### Post by jeremy31 on 2015-12-07
Open a terminal window and enter the following command and post the output
```
lspci -nnk | grep -iA2 net; lsusb; rfkill list all; lsmod | grep bluetooth; dmesg | egrep -i 'blue|firm'; uname -a
```

---

### Post by petarivanov1985 on 2015-12-08
This is the result of the commands.

> 07:00.0 Network controller [0280]: Broadcom Corporation BCM43142 802.11b/g/n [14e4:4365] (rev 01)    Subsystem: Lenovo Device [17aa:0611]
    Kernel driver in use: wl
08:00.0 Ethernet controller [0200]: Qualcomm Atheros QCA8172 Fast Ethernet [1969:10a0] (rev 10)
    Subsystem: Qualcomm Atheros Device [1969:1090]
    Kernel driver in use: alx
Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 005: ID 105b:e065  
Bus 003 Device 004: ID 0e8f:00a5 GreenAsia Inc. 
Bus 003 Device 003: ID 5986:0295 Acer, Inc 
Bus 003 Device 002: ID 058f:6366 Alcor Micro Corp. Multi Flash Reader
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: ideapad_bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: ideapad_3g: Wireless WAN
    Soft blocked: no
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
4: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
bluetooth             446409  10 bnep,rfcomm
6lowpan_iphc           18702  1 bluetooth
[    0.131120] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[   13.744240] [Firmware Bug]: ACPI(PEGP) defines _DOD but not _DOS
[   19.007984] Bluetooth: Core ver 2.19
[   19.007999] Bluetooth: HCI device and connection manager initialized
[   19.008006] Bluetooth: HCI socket layer initialized
[   19.008008] Bluetooth: L2CAP socket layer initialized
[   19.008016] Bluetooth: SCO socket layer initialized
[   19.011435] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   19.011438] Bluetooth: BNEP filters: protocol multicast
[   19.011444] Bluetooth: BNEP socket layer initialized
[   19.027318] Bluetooth: RFCOMM TTY layer initialized
[   19.027327] Bluetooth: RFCOMM socket layer initialized
[   19.027331] Bluetooth: RFCOMM ver 1.11
Linux petar-Lenovo-G710 3.16.0-45-generic #60~14.04.1-Ubuntu SMP Fri Jul 24 21:16:23 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux




---

### Post by jeremy31 on 2015-12-08
Since this device is supported in the Ubuntu kernel, I would suggest filing a bug report, start at [https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

It is fixed in the upstream Linux kernels and the patch that fixed it was [http://git.kernel.org/cgit/linux/kernel/git/bluetooth/bluetooth-next.git/commit/drivers/bluetooth/btusb.c?id=2faf71ce90782d02e1710c12a19a2084fbbec5cc](http://git.kernel.org/cgit/linux/kernel/git/bluetooth/bluetooth-next.git/commit/drivers/bluetooth/btusb.c?id=2faf71ce90782d02e1710c12a19a2084fbbec5cc)

My answer [http://askubuntu.com/questions/606608/bluetooth-cant-be-enabled-in-ubuntu-14-10](http://askubuntu.com/questions/606608/bluetooth-cant-be-enabled-in-ubuntu-14-10) includes the fix

---

### Post by petarivanov1985 on 2015-12-08
Thank you very much. That fixed the problem.

Now I have another problem - I connect my bluetooth headset to my laptop, but the sound is awful. It is like - croaking sound. Is there a way that I can improve this quality?

---

### Post by jeremy31 on 2015-12-08
What does ```
pactl list short | grep bluetooth
``` result with

---

### Post by petarivanov1985 on 2015-12-08
This is the result
> 8    module-bluetooth-policy        
24    module-bluetooth-discover    

This is the result when my headset is connected:

8	module-bluetooth-policy		
24	module-bluetooth-discover		
26	module-bluetooth-device	address="00:1B:B8:33:05:C9" path="/org/bluez/1684/hci0/dev_00_1B_B8_33_05_C9"	
3	bluez_card.00_1B_B8_33_05_C9	module-bluetooth-device.c

---

### Post by jeremy31 on 2015-12-08
Check in Sound Settings to see if the headset is using HSP/HFP instead of A2DP, the A2DP should have better quality

---

### Post by petarivanov1985 on 2015-12-08
It is using [COLOR=#000000]A2DP[/COLOR]

---

### Post by jeremy31 on 2015-12-08
I would look at this youtube video and see if it helps with the audio quality
[https://www.youtube.com/watch?v=4fZVdBIf7uM](https://www.youtube.com/watch?v=4fZVdBIf7uM)

---

