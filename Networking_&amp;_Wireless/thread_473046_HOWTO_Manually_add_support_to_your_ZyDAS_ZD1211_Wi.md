---
title: "HOWTO Manually add support to your ZyDAS ZD1211 Wifi USB dongle - ZD1211rw driver"
date: 2007-06-13
forum: Networking &amp; Wireless
---

### Post by Deben_69 on 2007-06-13
I have an currently unsupported ZyDAS ZD1211B chip Wifi USB adapter - Planex Comm. GW-US54GD and this is how you can add support to this an other ZD1211 / ZD1211B devices:

WARNING: THIS PROCESS IS RISKY SO DONT BLAME ME IF ANYTHING GOES WRONG!!!
                    ALWAYS BACKUP YOUR FILES TO BE MODIFIED FIRST !

1-  in Terminal type: "lsusb" (without cuotes of course!)
     then connect your USB device and type: "lsusb"   (again!) 
    take note of the new device #. ( The result for my GW-US54GD was  2019:ed01 )

2- type: "cd /usr/src/linux/drivers/net/wireless/zd1211rw"
   (to change to the source directory of the zd1211rw driver)

3- type: "sudo nano zd_usb.c"
    (I used nano, but you can use your favorite text editor)

4- inside ls_usb.c add the following line in the USB_devices_id area: 
   { USB_DEVICE(0x2019, 0xed01), .driver_info = DEVICE_ZD1211B },
   (Change it accordingly to your usb_device_number)

5- SAVE [ctrl+o] the file and EXIT [ctrl+x] the editor.

6- To compile (make) the modified Kernel extension driver type:
     "sudo make -C /lib/modules/2.6.20-16-generic/build/ M=`pwd` modules "

(NOTE: the folder inside /lib/modules/ varies according to your kernel version # mine is 2.6.20-16-generic
type: "uname -r "  if you are not sure) 

7- then to COPY it to the running .ko folder - type: "sudo cp /usr/src/linux/drivers/net/wireless/zd1211rw/zd1211rw.ko  /lib/modules/2.6.20-16-generic/kernel/drivers/net/wireless/zd1211rw/zd1211rw.ko"

(NOTE: REBOOT RECOMMENDED at this point!)

8- then to activate type: "sudo modprobe zd1211rw"

9- CONNECT your USB Dongle and verify with: "iwconfig" and "sudo ifup eth1" (or the equivalent for your device) and "dmesg" (to check for errors).

10- If everything SUCCESSFULL configure your network (Wifi LAN) as usual.

---

