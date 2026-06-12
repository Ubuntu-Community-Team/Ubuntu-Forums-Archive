---
title: "Issues with Mobile Broadband ZTE MF820 4G LTE with Kubuntu 14.04"
date: 2014-04-20
forum: Networking &amp; Wireless
---

### Post by nibin012 on 2014-04-20
Hi,

I recently upgraded my OS from Kubuntu 13.10 to 14.04 and now my ZTE 4g usb stick is not working. ZTE 4g dongle used to work smoothly in 13.10 Kubuntu. After upgrading my OS to 14.04, these are the logs I see

```

nibin@nibin-ofxlaptop:~$ lsusb
Bus 002 Device 003: ID 5986:02d2 Acer, Inc 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 147e:1002 Upek Biometric Touchchip/Touchstrip Fingerprint Sensor
Bus 001 Device 009: ID 19d2:0167 ZTE WCDMA Technologies MSM MF820 4G LTE
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 002: ID 045e:0084 Microsoft Corp. Basic Optical Mouse
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub



```

Logs from "/var/log/syslog" when the ZTE dongle was connected:
```

Apr 20 15:37:46 nibin-ofxlaptop kernel: [  134.403378] usb 1-1.2: new high-speed USB device number 7 using ehci-pci
Apr 20 15:37:47 nibin-ofxlaptop kernel: [  134.499236] usb 1-1.2: New USB device found, idVendor=19d2, idProduct=0166
Apr 20 15:37:47 nibin-ofxlaptop kernel: [  134.499248] usb 1-1.2: New USB device strings: Mfr=3, Product=2, SerialNumber=4
Apr 20 15:37:47 nibin-ofxlaptop kernel: [  134.499254] usb 1-1.2: Product: ZTE LTE Technologies MSM
Apr 20 15:37:47 nibin-ofxlaptop kernel: [  134.499260] usb 1-1.2: Manufacturer: ZTE,Incorporated
Apr 20 15:37:47 nibin-ofxlaptop kernel: [  134.499264] usb 1-1.2: SerialNumber: MF880TFFFS111111
Apr 20 15:37:47 nibin-ofxlaptop kernel: [  134.500841] usb-storage 1-1.2:1.0: USB Mass Storage device detected
Apr 20 15:37:47 nibin-ofxlaptop kernel: [  134.501800] scsi8 : usb-storage 1-1.2:1.0
Apr 20 15:37:47 nibin-ofxlaptop mtp-probe: checking bus 1, device 7: "/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.2"
Apr 20 15:37:47 nibin-ofxlaptop mtp-probe: bus: 1, device: 7 was not an MTP device
Apr 20 15:37:48 nibin-ofxlaptop usb_modeswitch: switch device 19d2:0166 on 001/007
Apr 20 15:37:50 nibin-ofxlaptop kernel: [  138.049732] usb 1-1.2: USB disconnect, device number 7
Apr 20 15:37:55 nibin-ofxlaptop kernel: [  142.860171] usb 1-1.2: new high-speed USB device number 8 using ehci-pci
Apr 20 15:37:55 nibin-ofxlaptop kernel: [  142.956549] usb 1-1.2: New USB device found, idVendor=19d2, idProduct=0167
Apr 20 15:37:55 nibin-ofxlaptop kernel: [  142.956561] usb 1-1.2: New USB device strings: Mfr=3, Product=2, SerialNumber=4
Apr 20 15:37:55 nibin-ofxlaptop kernel: [  142.956567] usb 1-1.2: Product: ZTE LTE Technologies MSM
Apr 20 15:37:55 nibin-ofxlaptop kernel: [  142.956572] usb 1-1.2: Manufacturer: ZTE,Incorporated
Apr 20 15:37:55 nibin-ofxlaptop kernel: [  142.956577] usb 1-1.2: SerialNumber: MF880TFFFS111111
Apr 20 15:37:55 nibin-ofxlaptop kernel: [  142.959064] option 1-1.2:1.0: GSM modem (1-port) converter detected
Apr 20 15:37:55 nibin-ofxlaptop kernel: [  142.959354] usb 1-1.2: GSM modem (1-port) converter now attached to ttyUSB0
Apr 20 15:37:55 nibin-ofxlaptop kernel: [  142.959672] option 1-1.2:1.1: GSM modem (1-port) converter detected
Apr 20 15:37:55 nibin-ofxlaptop kernel: [  142.959898] usb 1-1.2: GSM modem (1-port) converter now attached to ttyUSB1
Apr 20 15:37:55 nibin-ofxlaptop vmnet-natd: RTM_NEWLINK: name:wwan0 index:7 flags:0x00001002
Apr 20 15:37:55 nibin-ofxlaptop vmnetBridge: RTM_NEWLINK: name:wwan0 index:7 flags:0x00001002
Apr 20 15:37:55 nibin-ofxlaptop kernel: [  142.960271] option 1-1.2:1.2: GSM modem (1-port) converter detected
Apr 20 15:37:55 nibin-ofxlaptop kernel: [  142.960557] usb 1-1.2: GSM modem (1-port) converter now attached to ttyUSB2
Apr 20 15:37:55 nibin-ofxlaptop kernel: [  142.960835] option 1-1.2:1.3: GSM modem (1-port) converter detected
Apr 20 15:37:55 nibin-ofxlaptop kernel: [  142.961032] usb 1-1.2: GSM modem (1-port) converter now attached to ttyUSB3
Apr 20 15:37:55 nibin-ofxlaptop kernel: [  142.962139] qmi_wwan 1-1.2:1.4: cdc-wdm0: USB WDM device
Apr 20 15:37:55 nibin-ofxlaptop kernel: [  142.963038] qmi_wwan 1-1.2:1.4 wwan0: register 'qmi_wwan' at usb-0000:00:1a.0-1.2, WWAN/QMI device, 8a:12:df:a2:fe:48
Apr 20 15:37:55 nibin-ofxlaptop kernel: [  142.963429] usb-storage 1-1.2:1.5: USB Mass Storage device detected
Apr 20 15:37:55 nibin-ofxlaptop kernel: [  142.964146] scsi9 : usb-storage 1-1.2:1.5
Apr 20 15:37:55 nibin-ofxlaptop mtp-probe: checking bus 1, device 8: "/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.2"
Apr 20 15:37:55 nibin-ofxlaptop mtp-probe: bus: 1, device: 8 was not an MTP device
Apr 20 15:37:55 nibin-ofxlaptop ModemManager[802]: [/dev/cdc-wdm0] Checking version info (10 retries)...
Apr 20 15:37:55 nibin-ofxlaptop NetworkManager[1152]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.2/1-1.2:1.4/net/wwan0, iface: wwan0)
Apr 20 15:37:55 nibin-ofxlaptop NetworkManager[1152]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.2/1-1.2:1.4/net/wwan0, iface: wwan0): no ifupdown configuration found.
Apr 20 15:37:55 nibin-ofxlaptop ModemManager[802]: <warn>  (ttyUSB2): port attributes not fully set
Apr 20 15:37:55 nibin-ofxlaptop ModemManager[802]: <warn>  (ttyUSB3): port attributes not fully set
Apr 20 15:37:55 nibin-ofxlaptop ModemManager[802]: <warn>  (ttyUSB1): port attributes not fully set
Apr 20 15:37:55 nibin-ofxlaptop ModemManager[802]: <warn>  (ttyUSB0): port attributes not fully set
Apr 20 15:37:56 nibin-ofxlaptop usb_modeswitch: switched to 19d2:ffffffff on 001/007
Apr 20 15:37:57 nibin-ofxlaptop usb_modeswitch[2806]: usb_modeswitch: switched to 19d2:0167 on 1/8
Apr 20 15:37:58 nibin-ofxlaptop usb_modeswitch[2806]: usb_modeswitch: add device ID 19d2:0167 to driver option
Apr 20 15:37:58 nibin-ofxlaptop usb_modeswitch[2806]: usb_modeswitch: please report the device ID to the Linux USB developers!
Apr 20 15:37:59 nibin-ofxlaptop ModemManager[802]: <warn>  (ttyUSB2): port attributes not fully set
Apr 20 15:37:59 nibin-ofxlaptop ModemManager[802]: <warn>  (ttyUSB3): port attributes not fully set
Apr 20 15:37:59 nibin-ofxlaptop ModemManager[802]: <warn>  (ttyUSB1): port attributes not fully set
Apr 20 15:37:59 nibin-ofxlaptop ModemManager[802]: <warn>  (ttyUSB0): port attributes not fully set
Apr 20 15:38:01 nibin-ofxlaptop kernel: [  148.992284] scsi 9:0:0:0: CD-ROM            L_T_E     USB SCSI CD-ROM  USB PQ: 0 ANSI: 0
Apr 20 15:38:01 nibin-ofxlaptop kernel: [  148.997387] sr1: scsi-1 drive
Apr 20 15:38:01 nibin-ofxlaptop kernel: [  148.998746] sr 9:0:0:0: Attached scsi CD-ROM sr1
Apr 20 15:38:01 nibin-ofxlaptop kernel: [  149.000987] sr 9:0:0:0: Attached scsi generic sg2 type 5
Apr 20 15:38:10 nibin-ofxlaptop ModemManager[802]: <info>  Creating modem with plugin 'Generic' and '6' ports
Apr 20 15:38:10 nibin-ofxlaptop ModemManager[802]: <warn>  Could not grab port (tty/ttyUSB1): 'Cannot add port 'tty/ttyUSB1', unhandled serial type'
Apr 20 15:38:10 nibin-ofxlaptop ModemManager[802]: <warn>  Could not grab port (tty/ttyUSB3): 'Cannot add port 'tty/ttyUSB3', unhandled serial type'
Apr 20 15:38:10 nibin-ofxlaptop ModemManager[802]: <warn>  Could not grab port (tty/ttyUSB2): 'Cannot add port 'tty/ttyUSB2', unhandled serial type'
Apr 20 15:38:10 nibin-ofxlaptop ModemManager[802]: <warn>  Could not grab port (usbmisc/cdc-wdm0): 'Cannot add port 'usbmisc/cdc-wdm0', unsupported'
Apr 20 15:38:10 nibin-ofxlaptop ModemManager[802]: <warn>  Couldn't create modem for device at '/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.2': Failed to find primary AT port


```

I also enabled USB_Modeswitch logging in "/etc/usb_modeswitch.conf". The logs printed are given below

```





USB_ModeSwitch log from Sun Apr 20 15:37:47 2014


Use global config file: /etc/usb_modeswitch.conf




Started via upstart
Adjust delay for USB storage devices ...
 Current value is higher or equal to 10. Leave it alone
Raw args from udev: /1-1.2


Bus ID for device not given by udev.
 Trying to determine it from kernel name (1-1.2) ...
Use top device dir /sys/bus/usb/devices/1-1.2


USB dir exists: /sys/bus/usb/devices/1-1.2


SCSI dir exists: /sys/bus/usb/devices/1-1.2
Warning: SCSI attribute "vendor" not readable.
Warning: SCSI attribute "model" not readable.
Warning: SCSI attribute "rev" not readable.
Check class of first interface ...
 Device is in install mode.
Use interface (null)
----------------
USB values from sysfs:
  idVendor    19d2
  idProduct    0166
  manufacturer    ZTE,Incorporated
  product    ZTE LTE Technologies MSM
  serial    MF880TFFFS111111
  bNumConfigurations    1
----------------
bNumConfigurations is 1 - don't check for active configuration
Found packed config collection /usr/share/usb_modeswitch/configPack.tar.gz
Searching entries named: /usr/share/usb_modeswitch/19d2:0166*
Searching overriding entries named: /etc/usb_modeswitch.d/19d2:0166*
SCSI attributes not needed, move on.


Extract config 19d2:0166 from collection /usr/share/usb_modeswitch/configPack.tar.gz
config: TargetVendor set to 19d2
config: TargetProduct set to 0167
Driver module is "option", ID path is /sys/bus/usb-serial/drivers/option1
! matched, now switching
Command to be run:
/usr/sbin/usb_modeswitch -W -D -s 20 -c /run/usb_modeswitch/current_cfg -u -1   -v 19d2 -p 0166 2>&1


Verbose debug output of usb_modeswitch and libusb follows
(Note that some USB errors are expected in the process)
--------------------------------


Read config file: /run/usb_modeswitch/current_cfg


 * usb_modeswitch: handle USB devices with multiple modes
 * Version 2.1.1 (C) Josua Dietze 2014
 * Based on libusb1/libusbx


 ! PLEASE REPORT NEW CONFIGURATIONS !


DefaultVendor=  0x19d2
DefaultProduct= 0x0166
TargetVendor=   0x19d2
TargetProduct=  0x0167
MessageContent="55534243123456782400000080000685000000240000000000000000000000"
NeedResponse=0
Success check enabled, max. wait time 20 seconds
System integration mode enabled


Look for target devices ...
  found USB ID 5986:02d2
  found USB ID 8087:0024
  found USB ID 1d6b:0002
  found USB ID 147e:1002
  found USB ID 19d2:0166
   vendor ID matched
  found USB ID 8087:0024
  found USB ID 1d6b:0002
  found USB ID 1d6b:0003
  found USB ID 045e:0084
  found USB ID 1d6b:0002
 No devices in target mode or class found
Look for default devices ...
  found USB ID 5986:02d2
  found USB ID 8087:0024
  found USB ID 1d6b:0002
  found USB ID 147e:1002
  found USB ID 19d2:0166
   vendor ID matched
   product ID matched
  found USB ID 8087:0024
  found USB ID 1d6b:0002
  found USB ID 1d6b:0003
  found USB ID 045e:0084
  found USB ID 1d6b:0002
 Found devices in default mode (1)
Access device 007 on bus 001
Use interface number 0
Use endpoints 0x01 (out) and 0x81 (in)


USB description data (for identification)
-------------------------
Manufacturer: ZTE,Incorporated
     Product: ZTE LTE Technologies MSM
  Serial No.: MF880TFFFS111111
-------------------------
Looking for active driver ...
 OK, driver detached
Set up interface 0
Use endpoint 0x01 for message sending ...
Trying to send message 1 to endpoint 0x01 ...
 OK, message successfully sent
Reset response endpoint 0x81
Reset message endpoint 0x01


Check for mode switch (max. 20 times, once per second) ...
 Search for target devices ...
  found USB ID 5986:02d2
  found USB ID 8087:0024
  found USB ID 1d6b:0002
  found USB ID 147e:1002
  found USB ID 19d2:0166
   vendor ID matched
  found USB ID 8087:0024
  found USB ID 1d6b:0002
  found USB ID 1d6b:0003
  found USB ID 045e:0084
  found USB ID 1d6b:0002
 Search for target devices ...
  found USB ID 5986:02d2
  found USB ID 8087:0024
  found USB ID 1d6b:0002
  found USB ID 147e:1002
  found USB ID 19d2:0166
   vendor ID matched
  found USB ID 8087:0024
  found USB ID 1d6b:0002
  found USB ID 1d6b:0003
  found USB ID 045e:0084
  found USB ID 1d6b:0002
 Search for target devices ...
  found USB ID 5986:02d2
  found USB ID 8087:0024
  found USB ID 1d6b:0002
  found USB ID 147e:1002
  found USB ID 8087:0024
  found USB ID 1d6b:0002
  found USB ID 1d6b:0003
  found USB ID 045e:0084
  found USB ID 1d6b:0002
 Search for target devices ...
  found USB ID 5986:02d2
  found USB ID 8087:0024
  found USB ID 1d6b:0002
  found USB ID 147e:1002
  found USB ID 8087:0024
  found USB ID 1d6b:0002
  found USB ID 1d6b:0003
  found USB ID 045e:0084
  found USB ID 1d6b:0002
 Search for target devices ...
  found USB ID 5986:02d2
  found USB ID 8087:0024
  found USB ID 1d6b:0002
  found USB ID 147e:1002
  found USB ID 8087:0024
  found USB ID 1d6b:0002
  found USB ID 1d6b:0003
  found USB ID 045e:0084
  found USB ID 1d6b:0002
 Search for target devices ...
  found USB ID 5986:02d2
  found USB ID 8087:0024
  found USB ID 1d6b:0002
  found USB ID 147e:1002
  found USB ID 8087:0024
  found USB ID 1d6b:0002
  found USB ID 1d6b:0003
  found USB ID 045e:0084
  found USB ID 1d6b:0002
 Search for target devices ...
  found USB ID 5986:02d2
  found USB ID 8087:0024
  found USB ID 1d6b:0002
  found USB ID 147e:1002
  found USB ID 8087:0024
  found USB ID 1d6b:0002
  found USB ID 1d6b:0003
  found USB ID 045e:0084
  found USB ID 1d6b:0002
 Search for target devices ...
  found USB ID 19d2:0167
   vendor ID matched
   product ID matched
  found USB ID 5986:02d2
  found USB ID 8087:0024
  found USB ID 1d6b:0002
  found USB ID 147e:1002
  found USB ID 8087:0024
  found USB ID 1d6b:0002
  found USB ID 1d6b:0003
  found USB ID 045e:0084
  found USB ID 1d6b:0002


Found target device, open it


Found target device 008 on bus 001


Target device description data
-------------------------
Manufacturer: ZTE,Incorporated
     Product: ZTE LTE Technologies MSM
  Serial No.: MF880TFFFS111111
-------------------------
 Found correct target device


Mode switch succeeded. Bye!


ok:no_data
--------------------------------
(end of usb_modeswitch output)
Check success of mode switch for max. 20 seconds ... Read attributes ...
USB dir exists: /sys/bus/usb/devices/1-1.2
 All attributes matched
Mode switching was successful, found 19d2:0167 (ZTE,Incorporated: ZTE LTE Technologies MSM)Now check for bound driver ...
 no driver has bound to interface 0 yet
Device not in "bind_list" yet, bind it now
Module loader is /sbin/modprobe
Module is active already
Try to add ID to driver "option"
 ID added to driver; check for new devices in /dev
 driver binding failed
Check for AVOID_RESET_QUIRK kernel attribute
 AVOID_RESET_QUIRK activated


All done, exit

```

After a lot of googling, I found this [post]("http://ubuntuforums.org/showthread.php?t=2074518"). I gave my wvdial.conf for my provider (Airtel, india) and used wvdial to connect now. It is now connecting using wvdial.
```

nibin@nibin-ofxlaptop:~$ sudo cat /etc/wvdial.conf 
[sudo] password for nibin: 
[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = Analog Modem
New PPPD = yes
Modem = /dev/ttyUSB2
ISDN = 0
Baud = 57600
Ask Password = 0
Dial Command = ATDT
Stupid Mode = 1
Compuserve = 0
Idle Seconds = 0
Init3 = AT+CGDCONT=1,"IP","airtelgprs.com"
Phone = *99#
Password = internet
Username = o2
Auto DNS = 0



```

Eventhough it is now connecting using wvdial, I would like to use the NetworkManager support from Kubuntu for the same. Is this a NetworkManager problem or USB_Modeswitch problem ?

let me know if any additional details are required.

---

