---
title: "[Ubuntu 13.04] Huawei E303 stopped working"
date: 2013-09-25
forum: Networking &amp; Wireless
---

### Post by dshgna on 2013-09-25
Hi,

I've previously used Ubuntu 12.04 and yesterday installed 13.04. I usually use an Ethernet connection at home and a Mobile Broadband connection through the Huawei E303 dongle elsewhere.

The dongle worked erratically in Ubuntu 12.04. At times it worked fine, other times network manager would be unable to detect it and/or there would be error messages complaining that it was unable to mount Mobile Partner. The newbie workaround I used was unplugging/replugging into different ports, which at times resolved the issue.

Now with Ubuntu 13.04, the dongle worked perfectly yesterday, but today network manager does not detect it. I tried googling on the issue and discovered that it was due to the fact that the modem was detected as a storage device. The guide I used was [http://ubuntuforums.org/showthread.php?t=2028061](http://ubuntuforums.org/showthread.php?t=2028061)

So far, so good till Step 2.
```
[COLOR=#000000][FONT=Ubuntu Mono]$ cat /etc/usb_modeswitch.d/[vendor code]\:[product code] | grep MessageContent[/FONT][/COLOR]
```

This simple gives the output
```
[COLOR=#000000][FONT=Ubuntu Mono]/etc/usb_modeswitch.d/12d1:i4fe: No such file or directory[/FONT][/COLOR]
```

I may be buggling up some step. So all help is greatly appreciated:). Thank you:)

---

### Post by varunendra on 2013-09-25
Please unplug the modem, re-plug it and post the outputs of the following -
```
dmesg | tail -20
lsusb
ls /etc/usb_modeswitch.d
```

---

### Post by dshgna on 2013-09-25
Hi...

dmesg | tail -20

```
[12523.608875] usb 1-1.2: New USB device found, idVendor=0cf3, idProduct=3004[12523.608882] usb 1-1.2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[12523.608886] usb 1-1.2: Product: Bluetooth USB Host Controller
[12523.608889] usb 1-1.2: Manufacturer: Atheros Communications
[12523.608892] usb 1-1.2: SerialNumber: Alaska Day 2006
[13592.810444] usb 3-3: USB disconnect, device number 16
[13601.134675] usb 3-3: new high-speed USB device number 17 using xhci_hcd
[13601.151591] usb 3-3: New USB device found, idVendor=12d1, idProduct=14fe
[13601.151599] usb 3-3: New USB device strings: Mfr=2, Product=1, SerialNumber=0
[13601.151603] usb 3-3: Product: HUAWEI Mobile
[13601.151606] usb 3-3: Manufacturer: HUAWEI
[13601.153497] scsi37 : usb-storage 3-3:1.0
[13601.153978] scsi38 : usb-storage 3-3:1.1
[13602.149971] scsi 37:0:0:0: CD-ROM            HUAWEI   Mass Storage     2.31 PQ: 0 ANSI: 2
[13602.149981] scsi 38:0:0:0: Direct-Access     HUAWEI   SD Storage       2.31 PQ: 0 ANSI: 2
[13602.151839] sr1: scsi-1 drive
[13602.152108] sr 37:0:0:0: Attached scsi CD-ROM sr1
[13602.152257] sr 37:0:0:0: Attached scsi generic sg3 type 5
[13602.152646] sd 38:0:0:0: Attached scsi generic sg4 type 0
[13602.154340] sd 38:0:0:0: [sdc] Attached SCSI removable disk
```

lsusb

```
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching HubBus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 017: ID 12d1:14fe Huawei Technologies Co., Ltd. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 0bda:0129 Realtek Semiconductor Corp. 
Bus 001 Device 010: ID 0cf3:3004 Atheros Communications, Inc. 
Bus 001 Device 005: ID 2232:1029  
```

ls /etc/usb_modeswitch.d
Returns no output

---

### Post by varunendra on 2013-09-25
> **dshgna said:**
> 
ls /etc/usb_modeswitch.d
Returns no output

..because that directory is empty by default, unless you create a file in it.

However, the file you are looking for is now placed in an archive "/usr/share/usb_modeswitch/configPack.tar.gz" along with other similar files, and the Hex code you are looking for is -
```
55534243123456780000000000000011062000000100000000000000000000
```
(copied from the file "12d1:14fe in the archive)

Anyway, it seems that just copying that file in the /etc/usb_modeswitch.d directory should do the trick. So before trying anything else, I would suggest you try the following -
```
sudo tar xf /usr/share/usb_modeswitch/configPack.tar.gz -C /etc/usb_modeswitch.d 12d1:14fe
```
This will extract only the **12d1:14fe** file from the archive into /etc/usb_modeswitch.d directory.

After doing this, unplug and replug your modem and see if its ID gets changed in lsusb -
```
lsusb | grep 12d1
```
Instead of **12d1:[COLOR="#FF0000"]14fe[/COLOR]**, you should get **12d1:[COLOR="#006400"]1506[/COLOR]** this time. If not, do a reboot and try again. If it still doesn't change its ID **Only then**, try the following -
```
sudo usb_modeswitch --default-vendor 0x12d1 --default-product 0x14fe --message-content 55534243123456780000000000000011062000000100000000000000000000
```
Then check lsusb again. Does its id get changed? Moreover, does it get recognized by Network Manager?

**PS:**
The guide you are following suggests using usbserial which can not give you high speed performance like 3g. So if you wish, we can take a slightly different approach with the optimal speed driver called "option". If after copying the above file, or after reboot it automatically got recognized, it will already be using the "option" driver then, no need to try anything else.

---

### Post by dshgna on 2013-09-25
I followed the steps exactly in sequence, but the output of lsusb is the same, and the modem is not detected by Network Manager.

---

### Post by varunendra on 2013-09-25
Hmm.. please unplug --> wait for 20 seconds --> replug the modem, then post back the full outputs of all of these -
```
sudo usb_modeswitch --default-vendor 0x12d1 --default-product 0x14fe --message-content 55534243123456780000000000000011062000000100000000000000000000
lsusb
dmesg | tail -40
```

---

### Post by dshgna on 2013-09-26
At the moment it functions properly after rebooting twice. Will post the output when it dis-functions again. A thing I noticed was that this problem occurs immediately after I use my ethernet connection. Would there be some link?

---

### Post by varunendra on 2013-09-26
> **dshgna said:**
> At the moment it functions properly after rebooting twice.
So is the device ID 12d1:1506 in lsusb now?

> A thing I noticed was that this problem occurs immediately after I use my ethernet connection. Would there be some link?
Not sure but there maybe. Keep a gap of at least 20 seconds between unplugging the ethernet and plugging the modem. The network manager or modemmanager does get confused sometimes.

One more thing I have personally noticed (although can't explain why it happens) - The modemmanager or the system gets confused too often (not detecting it as modem) whenever I'm using a service that is too crappy (Tata Docomo for example). In that case, whenever a connection breaks, I have to unplug-replug the modem too many times to make it detected as a modem again. But when I'm on some decent service (e.g. Airtel), I don't get these frequent disconnections and the modem is immediately detected.

So it seem to me that probably the modem does something internally as soon as it gets power, and replies to system accordingly. If the reception is confusing, maybe it somehow confuses the system too.

But the above explanation is a pure guess based on my personal experience, and it may not be applicable to others. I'm using both services alternately, and always get the same behaviour depending upon which one I'm using.

---

### Post by dshgna on 2013-09-29
Had the same lovely problem. This time took 5-6 reboots. Could there be a connection between the mouse and dongle. I had unpluggesd the mouse and the modem worked when I replugged it...

I have a feeling there may be a connection between the connection quality. 

**usb_modeswitch output**
```
Looking for default devices ...   found matching product ID
   adding device
 Found device in default mode, class or configuration (1)
Accessing device 002 on bus 003 ...
Getting the current device configuration ...
 OK, got current device configuration (1)
Using first interface: 0x00
Using endpoints 0x01 (out) and 0x81 (in)
Inquiring device details; driver will be detached ...
Looking for active driver ...
 No driver found. Either detached before or never attached


SCSI inquiry data (for identification)
-------------------------
  Vendor String: HUAWEI  
   Model String: Mass Storage    
Revision String: 2.31
-------------------------


USB description data (for identification)
-------------------------
Manufacturer: HUAWEI
     Product: HUAWEI Mobile
  Serial No.: not provided
-------------------------
Setting up communication with interface 0
Using endpoint 0x01 for message sending ...
Trying to send message 1 to endpoint 0x01 ...
 OK, message successfully sent
Resetting response endpoint 0x81
Resetting message endpoint 0x01
-> Run lsusb to note any changes. Bye.
```

**lsusb**
```
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching HubBus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 002: ID 12d1:14fe Huawei Technologies Co., Ltd. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 0bda:0129 Realtek Semiconductor Corp. 
Bus 001 Device 004: ID 0cf3:3004 Atheros Communications, Inc. 
Bus 001 Device 005: ID 2232:1029  
```

**dmesg**
```
[   21.345544] type=1400 audit(1380507073.729:14): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=1225 comm="apparmor_parser"[   21.345833] type=1400 audit(1380507073.729:15): apparmor="STATUS" operation="profile_load" name="/usr/lib/x86_64-linux-gnu/lightdm-remote-session-freerdp/freerdp-session-wrapper" pid=1223 comm="apparmor_parser"
[   21.345845] type=1400 audit(1380507073.729:16): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=1222 comm="apparmor_parser"
[   21.345864] type=1400 audit(1380507073.729:17): apparmor="STATUS" operation="profile_load" name="/usr/lib/x86_64-linux-gnu/lightdm-remote-session-uccsconfigure/uccsconfigure-session-wrapper" pid=1224 comm="apparmor_parser"
[   21.345871] type=1400 audit(1380507073.729:18): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1225 comm="apparmor_parser"
[   21.346035] type=1400 audit(1380507073.729:19): apparmor="STATUS" operation="profile_load" name="/usr/lib/x86_64-linux-gnu/lightdm-remote-session-freerdp/freerdp-session-wrapper//chromium_browser" pid=1223 comm="apparmor_parser"
[   21.346048] type=1400 audit(1380507073.729:20): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1225 comm="apparmor_parser"
[   21.346079] type=1400 audit(1380507073.729:21): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=1229 comm="apparmor_parser"
[   21.346105] type=1400 audit(1380507073.729:22): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper//chromium_browser" pid=1222 comm="apparmor_parser"
[   22.033821] vboxdrv: Found 8 processor cores.
[   22.033944] vboxdrv: fAsync=0 offMin=0x183 offMax=0x10bc
[   22.033990] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   22.033991] vboxdrv: Successfully loaded version 4.2.10_Ubuntu (interface 0x001a0004).
[   22.050410] vboxpci: IOMMU not found (not registered)
[   24.321420] Ebtables v2.0 registered
[   24.492067] ip_tables: (C) 2000-2006 Netfilter Core Team
[   24.495771] ip6_tables: (C) 2000-2006 Netfilter Core Team
[   24.531403] cgroup: libvirtd (1662) created nested cgroup for controller "memory" which has incomplete hierarchy support. Nested cgroups may change behavior in the future.
[   24.531405] cgroup: "memory" requires setting use_hierarchy to 1 on the root.
[   24.531436] cgroup: libvirtd (1662) created nested cgroup for controller "devices" which has incomplete hierarchy support. Nested cgroups may change behavior in the future.
[   24.531463] cgroup: libvirtd (1662) created nested cgroup for controller "blkio" which has incomplete hierarchy support. Nested cgroups may change behavior in the future.
[   64.065928] usb 3-3: new high-speed USB device number 2 using xhci_hcd
[   64.082445] usb 3-3: New USB device found, idVendor=12d1, idProduct=14fe
[   64.082452] usb 3-3: New USB device strings: Mfr=2, Product=1, SerialNumber=0
[   64.082455] usb 3-3: Product: HUAWEI Mobile
[   64.082458] usb 3-3: Manufacturer: HUAWEI
[   64.199648] Initializing USB Mass Storage driver...
[   64.199745] scsi7 : usb-storage 3-3:1.0
[   64.200023] scsi8 : usb-storage 3-3:1.1
[   64.200078] usbcore: registered new interface driver usb-storage
[   64.200080] USB Mass Storage support registered.
[   65.197126] scsi 7:0:0:0: CD-ROM            HUAWEI   Mass Storage     2.31 PQ: 0 ANSI: 2
[   65.197141] scsi 8:0:0:0: Direct-Access     HUAWEI   SD Storage       2.31 PQ: 0 ANSI: 2
[   65.198375] sr1: scsi-1 drive
[   65.198474] sr 7:0:0:0: Attached scsi CD-ROM sr1
[   65.198550] sr 7:0:0:0: Attached scsi generic sg3 type 5
[   65.199116] sd 8:0:0:0: Attached scsi generic sg4 type 0
[   65.201066] sd 8:0:0:0: [sdc] Attached SCSI removable disk
[  680.512483] usb 3-3: usbfs: process 2784 (usb_modeswitch) did not claim interface 0 before use
[  700.274734] usb 3-3: usbfs: process 2794 (usb_modeswitch) did not claim interface 0 before use
```

---

### Post by dshgna on 2013-09-29
> **varunendra said:**
> So is the device ID 12d1:1506 in lsusb now?

Yes. Here's the output line with lsusb

```
Bus 003 Device 004: ID 12d1:1506 Huawei Technologies Co., Ltd. E398 LTE/UMTS/GSM Modem/Networkcard

```

---

### Post by varunendra on 2013-09-30
> **dshgna said:**
> 
```

Looking for active driver ...
 No driver found. Either detached before or never attached
```
That ^ indicates that there was possibly a problem in the modem itself. Otherwise, the usb-storage driver must have been associated.

When sometimes my modem disappears, I need to unplug-replug it several times too (usually 4-6 times), but I never need to reboot. I don't think you need to reboot either. It is just a usb device, if it really needs reboot, then the whole system is broken, not just modem functionality.

When this happens again, please try just unplugging - wait - replugging the modem, may require several cycles if it is in 'stuck' mode (happens even on windows). If its initial mode is properly initiated, then I believe the config file in /etc/usb_modeswitch.d directory should take care of the rest and you shouldn't need to manually do anything.

But if you are sure the storage mode is detected properly (dmesg shows that and you will probably see a "USB modem disk" in the "Computer" location) you may try these to see if any of them works (try one, if lsusb doesn't show the change in PID, try the next) -

1) Normal command (same previous one, just in a shorter form) -
```
sudo usb_modeswitch -v 0x12d1 -p 0x14fe -M "55534243123456780000000000000011062000000100000000000000000000"
```

2) To also tell usb_modeswitch which target vid/pid to switch to (I've never tried it myself, and the description is not very clear, so not sure if this even makes any sense) -
```
sudo usb_modeswitch -v 0x12d1 -p 0x14fe -V 0x12d1 -P 0x1506 -M "55534243123456780000000000000011062000000100000000000000000000"
```

3) Some devices need to be reset to complete the switching, this one is for that -
```
sudo usb_modeswitch -v 0x12d1 -p 0x14fe -M "55534243123456780000000000000011062000000100000000000000000000" -R
```

4) To try manually using the conf file (in case automatic trigger of usb_modswitch used it too early or not at all. This is almost the same thing as option 2 above) -
```
sudo usb_modeswitch -v 0x12d1 -p 0x14fe -c "/etc/usb_modeswitch.d/12d1:14fe"
```

The bottomline is - if we have both default and target vid/pid and message hex code too, and still can't switch the device to modem mode, there is not much that can be done. In such case, you may (probably should) post the problem in USB_ModeSwitch forum to get a more precise answer to 'Why' and 'How's : [http://www.draisberghof.de/usb_modeswitch/bb/](http://www.draisberghof.de/usb_modeswitch/bb/)

---

