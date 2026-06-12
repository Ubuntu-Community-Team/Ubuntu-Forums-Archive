---
title: "wwan0 interface disappear till reboot - Ubuntu 20.04"
date: 2020-10-30
forum: Networking &amp; Wireless
---

### Post by eby on 2020-10-30
I have a huawei 3g hotspot device connected over usb, upon plugging-in it registers as wwan0 (renamed with GRUB_CMDLINE_LINUX="net.ifnames=0 biosdevname=0" in grub) and i connect to internet using "sudo dhclient -v wwan0".

The hotspot gets switched off randomly and after turning it on/re-plugging/etc... wwan0 (net) port is not registered till the computer is restarted, i did not had this issue with Ubuntu 14.04.

I'm not sure if this is ubuntu related or usb_modeswitch related. Any help to resolve this is appreciated.

thanks,



**First time when the hotspot is plugged.**

dmesg
```

 usb 2-2: USB disconnect, device number 2
 usb 2-2: new high-speed USB device number 6 using xhci_hcd
 usb 2-2: New USB device found, idVendor=12d1, idProduct=14fe, bcdDevice= 1.02
 usb 2-2: New USB device strings: Mfr=2, Product=1, SerialNumber=0
 usb 2-2: Product: HUAWEI Mobile
 usb 2-2: Manufacturer: HUAWEI
 usb-storage 2-2:1.0: USB Mass Storage device detected
 scsi host3: usb-storage 2-2:1.0
 scsi 3:0:0:0: CD-ROM            HUAWEI   Mass Storage     2.31 PQ: 0 ANSI: 2
 sr 3:0:0:0: [sr0] scsi-1 drive
 sr 3:0:0:0: Attached scsi CD-ROM sr0
 sr 3:0:0:0: Attached scsi generic sg1 type 5
 usb 2-2: USB disconnect, device number 6
 usb 2-2: new high-speed USB device number 7 using xhci_hcd
 usb 2-2: New USB device found, idVendor=12d1, idProduct=1506, bcdDevice= 1.02
 usb 2-2: New USB device strings: Mfr=2, Product=1, SerialNumber=0
 usb 2-2: Product: HUAWEI Mobile
 usb 2-2: Manufacturer: HUAWEI
 usb-storage 2-2:1.3: USB Mass Storage device detected
 scsi host3: usb-storage 2-2:1.3
 usbcore: registered new interface driver usbserial_generic
 usbserial: USB Serial support registered for generic
 usbcore: registered new interface driver option
 usbserial: USB Serial support registered for GSM modem (1-port)
 usbcore: registered new interface driver cdc_ncm
 option 2-2:1.1: GSM modem (1-port) converter detected
 usb 2-2: GSM modem (1-port) converter now attached to ttyUSB0
 option 2-2:1.2: GSM modem (1-port) converter detected
 usb 2-2: GSM modem (1-port) converter now attached to ttyUSB1
 usbcore: registered new interface driver cdc_wdm
 huawei_cdc_ncm 2-2:1.0: MAC-Address: 0c:5b:8f:27:9a:64
 huawei_cdc_ncm 2-2:1.0: setting tx_max = 16384
 huawei_cdc_ncm 2-2:1.0: NDP will be placed at end of frame for this device.
 huawei_cdc_ncm 2-2:1.0: cdc-wdm0: USB WDM device
 huawei_cdc_ncm 2-2:1.0 wwan0: register 'huawei_cdc_ncm' at usb-0000:00:14.0-2, Huawei CDC NCM device, <<mac-address>>
 usbcore: registered new interface driver huawei_cdc_ncm
 scsi 3:0:0:0: CD-ROM            HUAWEI   Mass Storage     2.31 PQ: 0 ANSI: 2

```

mmcli
```

:~$ mmcli -L
    /org/freedesktop/ModemManager1/Modem/0 [huawei] E5220

:~$ mmcli -m 0
  -----------------------------
  General  |         dbus path: /org/freedesktop/ModemManager1/Modem/0
           |         device id: 356b3d6e47fdd8458667ff98c08fa68c370e8717
  -----------------------------
  Hardware |      manufacturer: huawei
           |             model: E5220
           | firmware revision: 21.143.17.00.910
           |         supported: gsm-umts
           |           current: gsm-umts
           |      equipment id: ******************
  -----------------------------
  System   |            device: /sys/devices/pci0000:00/0000:00:14.0/usb2/2-2
           |           drivers: huawei_cdc_ncm, option1
           |            plugin: Huawei
           |      primary port: ttyUSB1
           |             ports: wwan0 (net), ttyUSB1 (at)
  -----------------------------
  Status   |    unlock retries: sim-pin (3), sim-puk (10), sim-pin2 (3), sim-puk2 (10)
           |             state: disabled
           |       power state: on
           |    signal quality: 0% (cached)
  -----------------------------
  Modes    |         supported: allowed: 2g, 3g; preferred: none
           |                    allowed: 2g, 3g; preferred: 2g
           |                    allowed: 2g, 3g; preferred: 3g
           |                    allowed: 2g; preferred: none
           |                    allowed: 3g; preferred: none
           |           current: allowed: 3g; preferred: none
  -----------------------------
  IP       |         supported: ipv4, ipv6, ipv4v6
  -----------------------------
  3GPP     |              imei: ******************
  -----------------------------
  SIM      |         dbus path: /org/freedesktop/ModemManager1/SIM/0

```


**Connecting after the device get switched off, have tried plugging-in to other usb ports also.**

dmesg
```

 usb 2-2: USB disconnect, device number 7
 huawei_cdc_ncm 2-2:1.0 wwan0: unregister 'huawei_cdc_ncm' usb-0000:00:14.0-2, Huawei CDC NCM device
 option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
 option 2-2:1.1: device disconnected
 option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
 option 2-2:1.2: device disconnected
 usb 2-2: new high-speed USB device number 8 using xhci_hcd
 usb 2-2: New USB device found, idVendor=12d1, idProduct=1c20, bcdDevice= 1.02
 usb 2-2: New USB device strings: Mfr=2, Product=1, SerialNumber=0
 usb 2-2: Product: HUAWEI Mobile
 usb 2-2: Manufacturer: HUAWEI
 usb-storage 2-2:1.0: USB Mass Storage device detected
 scsi host3: usb-storage 2-2:1.0
 scsi 3:0:0:0: CD-ROM            HUAWEI   Mass Storage     2.31 PQ: 0 ANSI: 2
 sr 3:0:0:0: [sr0] scsi-1 drive
 sr 3:0:0:0: Attached scsi CD-ROM sr0
 sr 3:0:0:0: Attached scsi generic sg1 type 5
 usb 2-2: USB disconnect, device number 8

 usb 2-2: new high-speed USB device number 9 using xhci_hcd
 usb 2-2: New USB device found, idVendor=12d1, idProduct=14fe, bcdDevice= 1.02
 usb 2-2: New USB device strings: Mfr=2, Product=1, SerialNumber=0
 usb 2-2: Product: HUAWEI Mobile
 usb 2-2: Manufacturer: HUAWEI
 usb-storage 2-2:1.0: USB Mass Storage device detected
 scsi host3: usb-storage 2-2:1.0
 scsi 3:0:0:0: CD-ROM            HUAWEI   Mass Storage     2.31 PQ: 0 ANSI: 2
 sr 3:0:0:0: [sr0] scsi-1 drive
 sr 3:0:0:0: Attached scsi CD-ROM sr0
 sr 3:0:0:0: Attached scsi generic sg1 type 5
 usb 2-2: USB disconnect, device number 9

 usb 2-2: new high-speed USB device number 10 using xhci_hcd
 usb 2-2: New USB device found, idVendor=12d1, idProduct=1506, bcdDevice= 1.02
 usb 2-2: New USB device strings: Mfr=2, Product=1, SerialNumber=0
 usb 2-2: Product: HUAWEI Mobile
 usb 2-2: Manufacturer: HUAWEI
 option 2-2:1.0: GSM modem (1-port) converter detected
 option 2-2:1.1: GSM modem (1-port) converter detected
 usb 2-2: GSM modem (1-port) converter now attached to ttyUSB1
 option 2-2:1.2: GSM modem (1-port) converter detected
 usb 2-2: GSM modem (1-port) converter now attached to ttyUSB2
 usb-storage 2-2:1.3: USB Mass Storage device detected
 scsi host3: usb-storage 2-2:1.3
 scsi 3:0:0:0: CD-ROM            HUAWEI   Mass Storage     2.31 PQ: 0 ANSI: 2

```


mmcli
```

:~$ mmcli -L
    /org/freedesktop/ModemManager1/Modem/1 [huawei] E5220

:~$ mmcli -m 1
  -----------------------------
  General  |         dbus path: /org/freedesktop/ModemManager1/Modem/1
           |         device id: 356b3d6e47fdd8458667ff98c08fa68c370e8717
  -----------------------------
  Hardware |      manufacturer: huawei
           |             model: E5220
           | firmware revision: 21.143.17.00.910
           |         supported: gsm-umts
           |           current: gsm-umts
           |      equipment id: ******************
  -----------------------------
  System   |            device: /sys/devices/pci0000:00/0000:00:14.0/usb2/2-2
           |           drivers: option1
           |            plugin: Huawei
           |      primary port: ttyUSB2
           |             ports: ttyUSB2 (at)
  -----------------------------
  Status   |    unlock retries: sim-pin (3), sim-puk (10), sim-pin2 (3), sim-puk2 (10)
           |             state: registered
           |       power state: on
           |       access tech: umts
           |    signal quality: 51% (recent)
  -----------------------------
  Modes    |         supported: allowed: 2g, 3g; preferred: none
           |                    allowed: 2g, 3g; preferred: 2g
           |                    allowed: 2g, 3g; preferred: 3g
           |                    allowed: 2g; preferred: none
           |                    allowed: 3g; preferred: none
           |           current: allowed: 3g; preferred: none
  -----------------------------
  IP       |         supported: ipv4, ipv6, ipv4v6
  -----------------------------
  3GPP     |              imei: ******************
           |       operator id: ******************
           |     operator name: ******************
           |      registration: roaming
  -----------------------------
  SIM      |         dbus path: /org/freedesktop/ModemManager1/SIM/1

```

---

