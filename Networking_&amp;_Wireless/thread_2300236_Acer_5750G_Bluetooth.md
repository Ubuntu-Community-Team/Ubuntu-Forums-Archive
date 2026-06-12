---
title: "Acer 5750G Bluetooth"
date: 2015-10-24
forum: Networking &amp; Wireless
---

### Post by ddgdflog on 2015-10-24
ubuntu@ubuntu:/home$ dmesg|tail
[  181.966636] usb 1-1.6: USB disconnect, device number 4
[  183.510571] usb 1-1.6: new full-speed USB device number 5 using ehci-pci
[  183.607237] usb 1-1.6: New USB device found, idVendor=0489, idProduct=e033
[  183.607248] usb 1-1.6: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[  183.607253] usb 1-1.6: Product: Acer Module
[  183.607257] usb 1-1.6: Manufacturer: Broadcom Corp
[  183.607261] usb 1-1.6: SerialNumber: E4D53DD09C46
[  183.608630] bluetooth hci0: Direct firmware load for brcm/Acer Module-0489-e033.hcd failed with error -2
[  183.608642] Bluetooth: hci0: BCM: patch brcm/Acer Module-0489-e033.hcd not found
[  183.881982] usb 1-1.6: USB disconnect, device number 5

Where to I get this file 'Acer Module-0489-e033.hcd' ?

---

### Post by jeremy31 on 2015-10-24
Look at the answer [http://askubuntu.com/questions/632336/bluetooth-broadcom-43142-isnt-working-on-ubuntu-15-04](http://askubuntu.com/questions/632336/bluetooth-broadcom-43142-isnt-working-on-ubuntu-15-04) to see where to get the file from, with the exception that you are searching for 0489:e033 instead of 0a5c:21d7 and after you find the correct hex file you need the second part of the ./hex2hcd command to be 'Acer Module-0489-e033.hcd'.  

For example, searching the bcbtums file for e033 leads you to a file named BCM20702A1_001.002.014.1443.1457.hex then the hex2hcd command needs to be

```
./hex2hcd BCM20702A1_001.002.014.1443.1457.hex 'Acer Module-0489-e033.hcd'
```
Then you need to copy the file to the firmware directory
```
sudo cp 'Acer Module-0489-e033.hcd' /lib/firmware/brcm/
```

Then remove and reload the btusb module
```
sudo modprobe -r btusb
sudo modprobe btusb
```

And bluetooth should work if the firmware file is correct

---

### Post by ddgdflog on 2015-10-24
ubuntu@ubuntu:~$ dmesg|tail
[   19.083368] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
[   19.083370] cfg80211:   (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
[   19.083372] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
[   19.083373] cfg80211:   (5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A, 2000 mBm), (0 s)
[   19.083374] cfg80211:   (5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A, 2700 mBm), (0 s)
[   19.083376] cfg80211:   (57240000 KHz - 65880000 KHz @ 2160000 KHz), (N/A, 4000 mBm), (N/A)
[   19.725412] Bluetooth: hci0 command 0x0c03 tx timeout
[   20.429404] init: plymouth-upstart-bridge main process ended, respawning
[   20.442429] init: plymouth-upstart-bridge main process ended, respawning
[   27.730260] Bluetooth: hci0: HCI_OP_RESET failed (-110)

---

### Post by ddgdflog on 2015-10-24
BCM20702A0_001.001.024.0156.0204.hex

ubuntu@ubuntu:~$ dmesg|tail
[   61.506689] usb 1-1.6: USB disconnect, device number 6
[   61.707478] usb 1-1.6: new full-speed USB device number 7 using ehci-pci
[   61.804085] usb 1-1.6: New USB device found, idVendor=0489, idProduct=e033
[   61.804090] usb 1-1.6: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[   61.804093] usb 1-1.6: Product: Acer Module
[   61.804095] usb 1-1.6: Manufacturer: Broadcom Corp
[   61.804097] usb 1-1.6: SerialNumber: E4D53DD09C46
[   61.808851] Bluetooth: hci0: BCM: patching hci_ver=06 hci_rev=10e5 lmp_ver=06 lmp_subver=220e
[   64.402482] Bluetooth: hci0 command 0x0c03 tx timeout
[   72.407679] Bluetooth: hci0: HCI_OP_RESET failed (-110)

---

### Post by jeremy31 on 2015-10-24
Shutdown the computer and do a cold boot and see if that works

---

### Post by ddgdflog on 2015-10-24
The same

---

### Post by ddgdflog on 2015-10-24
%BtUSB.DeviceDesc%=BlueBCBTUsbDriverInstall,    USB\VID_0489&Pid_E033       ; Acer 20702 Serial FLASH

According to this: [http://askubuntu.com/questions/632336/bluetooth-broadcom-43142-isnt-working-on-ubuntu-15-04](http://askubuntu.com/questions/632336/bluetooth-broadcom-43142-isnt-working-on-ubuntu-15-04)
I need to search for: [BlueBCBTUsbDriverInstall.CopyList]
Which is not there, so how do I know what hex file to use ?

---

### Post by jeremy31 on 2015-10-24
Are you dual booted with windows?

Then again this could be an odd one that asks for firmware it doesn't need, I could make a btusb module that won't try to load firmware but need to know what kernel you have ```
uname -a
```

---

### Post by ddgdflog on 2015-10-24
ubuntu@ubuntu:~/hex2hcd$ uname -a
Linux ubuntu 3.19.0-25-generic #26~14.04.1-Ubuntu SMP Fri Jul 24 21:16:20 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

I have installed ubuntu in usb stick

---

### Post by ddgdflog on 2015-10-24
Now its working for no reason, I don't get it ?!?!?!!

---

### Post by jeremy31 on 2015-10-24
Download the attached file, it should go to Downloads
```
cd Downloads
mv btusb.ko.zip btusb.ko
sudo modprobe -r btusb
sudo modprobe ./btusb.ko
```

See if it works

I would recommend deleting the other firmware file with
```
sudo rm [COLOR=#000000][FONT=Ubuntu Mono]'/lib/firmware/brcm/Acer Module-0489-e033.hcd'
```

Reboot and then try the new file[/FONT][/COLOR]

---

