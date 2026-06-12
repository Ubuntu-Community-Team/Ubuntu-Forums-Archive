---
title: "Unable to mount USB Data Modem"
date: 2014-05-30
forum: Networking &amp; Wireless
---

### Post by vipin_john_wilson on 2014-05-30
Hi,

   I am an **ubuntu** user and using the version **13.10**. I have a USB Data Modem of D-Link which I recently purchased. For first time I tried to connect it to my ubuntu laptop two days ago and it was detected as medium **/dev/sr1** , but I did not mount it then and thought of doing it some other day.

Product url is [http://www.dlink.co.in/products/?pid=654](http://www.dlink.co.in/products/?pid=654)

   And today again, I connected the device to USB port and there are no files showing in **/dev/sr***

   But still the device is showing in **lsusb** and **usb-devices** commands

=======================
[B]# lsusb | grep -i d-link
Bus 003 Device 024: ID 2001:7d01 D-Link Corp.

# usb-devices | grep -i d-link
S:  Manufacturer=D-Link,Inc  
S:  Product=D-Link DWP-156


root@vaiocyber:~# ll /dev/ | grep sr
lrwxrwxrwx   1 root root           3 May 30 21:06 cdrom -> sr0
srw-rw-rw-   1 root root           0 May 30 20:36 log=
brw-rw----+  1 root cdrom    11,   0 May 30 21:06 sr0

I already tried to mount /dev/sr0 but no medium found 

# mount /dev/sr0 /media/john
mount: no medium found on /dev/sr0[/B]
=======================

I am pasting the syslog while this device was connected to USB port. Do you have any work around to fix it. Please check and shed some light to fix the issue :( Thank you....

==========================================================================
May 30 21:23:30 vaiocyber kernel: [ 2850.293293] usb 3-1: new high-speed USB device number 23 using xhci_hcd
May 30 21:23:30 vaiocyber kernel: [ 2850.310239] usb 3-1: New USB device found, idVendor=2001, idProduct=a706
May 30 21:23:30 vaiocyber kernel: [ 2850.310246] usb 3-1: New USB device strings: Mfr=2, Product=3, SerialNumber=4
May 30 21:23:30 vaiocyber kernel: [ 2850.310250] usb 3-1: Product: D-Link DWP-156
May 30 21:23:30 vaiocyber kernel: [ 2850.310253] usb 3-1: Manufacturer: D-Link,Inc  
May 30 21:23:30 vaiocyber kernel: [ 2850.310256] usb 3-1: SerialNumber: 536591501771340
May 30 21:23:30 vaiocyber kernel: [ 2850.311842] usb-storage 3-1:1.0: USB Mass Storage device detected
May 30 21:23:30 vaiocyber kernel: [ 2850.312602] scsi20 : usb-storage 3-1:1.0
May 30 21:23:30 vaiocyber mtp-probe: checking bus 3, device 23: "/sys/devices/pci0000:00/0000:00:14.0/usb3/3-1"
May 30 21:23:30 vaiocyber mtp-probe: bus: 3, device: 23 was not an MTP device
May 30 21:23:31 vaiocyber kernel: [ 2851.311093] scsi 20:0:0:0: CD-ROM            HSPA USB SCSI CD-ROM      6225 PQ: 0 ANSI: 0 CCS
May 30 21:23:31 vaiocyber kernel: [ 2851.312022] sr1: scsi3-mmc drive: 0x/0x caddy
May 30 21:23:31 vaiocyber kernel: [ 2851.312272] sr 20:0:0:0: Attached scsi CD-ROM sr1
May 30 21:23:31 vaiocyber kernel: [ 2851.312415] sr 20:0:0:0: Attached scsi generic sg2 type 5
May 30 21:23:31 vaiocyber kernel: [ 2851.370568] usbserial: USB Serial deregistering driver generic
May 30 21:23:31 vaiocyber kernel: [ 2851.370633] usbcore: deregistering interface driver usbserial_generic
May 30 21:23:31 vaiocyber kernel: [ 2851.370658] usbcore: deregistering interface driver usbserial
May 30 21:23:31 vaiocyber kernel: [ 2851.378641] usbcore: registered new interface driver usbserial
May 30 21:23:31 vaiocyber kernel: [ 2851.378657] usbcore: registered new interface driver usbserial_generic
May 30 21:23:31 vaiocyber kernel: [ 2851.378668] usbserial: USB Serial support registered for generic
May 30 21:23:32 vaiocyber kernel: [ 2851.446591] usb 3-1: USB disconnect, device number 23
May 30 21:23:32 vaiocyber kernel: [ 2852.183437] usb 3-1: new high-speed USB device number 24 using xhci_hcd
May 30 21:23:32 vaiocyber kernel: [ 2852.200327] usb 3-1: New USB device found, idVendor=2001, idProduct=7d01
May 30 21:23:32 vaiocyber kernel: [ 2852.200336] usb 3-1: New USB device strings: Mfr=9, Product=10, SerialNumber=0
May 30 21:23:32 vaiocyber kernel: [ 2852.200339] usb 3-1: Product: D-Link DWP-156
May 30 21:23:32 vaiocyber kernel: [ 2852.200343] usb 3-1: Manufacturer: D-Link,Inc  
May 30 21:23:32 vaiocyber kernel: [ 2852.201586] cdc_mbim 3-1:1.0: cdc-wdm0: USB WDM device
May 30 21:23:32 vaiocyber kernel: [ 2852.201826] cdc_mbim 3-1:1.0 wwan0: register 'cdc_mbim' at usb-0000:00:14.0-1, CDC MBIM, 46:ab:2c:e3:1b:4d
May 30 21:23:32 vaiocyber kernel: [ 2852.202090] usbserial_generic 3-1:1.2: The "generic" usb-serial driver is only for testing and one-off prototypes.
May 30 21:23:32 vaiocyber kernel: [ 2852.202094] usbserial_generic 3-1:1.2: Tell [email]linux-usb@vger.kernel.org[/email] to add your device to a proper driver.
May 30 21:23:32 vaiocyber kernel: [ 2852.202097] usbserial_generic 3-1:1.2: generic converter detected
May 30 21:23:32 vaiocyber kernel: [ 2852.202232] usb 3-1: generic converter now attached to ttyUSB0
May 30 21:23:32 vaiocyber kernel: [ 2852.202443] usbserial_generic 3-1:1.3: The "generic" usb-serial driver is only for testing and one-off prototypes.
May 30 21:23:32 vaiocyber kernel: [ 2852.202449] usbserial_generic 3-1:1.3: Tell [email]linux-usb@vger.kernel.org[/email] to add your device to a proper driver.
May 30 21:23:32 vaiocyber kernel: [ 2852.202454] usbserial_generic 3-1:1.3: generic converter detected
May 30 21:23:32 vaiocyber kernel: [ 2852.202577] usb 3-1: generic converter now attached to ttyUSB1
May 30 21:23:32 vaiocyber kernel: [ 2852.202767] usbserial_generic 3-1:1.4: The "generic" usb-serial driver is only for testing and one-off prototypes.
May 30 21:23:32 vaiocyber kernel: [ 2852.202773] usbserial_generic 3-1:1.4: Tell [email]linux-usb@vger.kernel.org[/email] to add your device to a proper driver.
May 30 21:23:32 vaiocyber kernel: [ 2852.202778] usbserial_generic 3-1:1.4: generic converter detected
May 30 21:23:32 vaiocyber kernel: [ 2852.202902] usb 3-1: generic converter now attached to ttyUSB2
May 30 21:23:32 vaiocyber kernel: [ 2852.203099] usbserial_generic 3-1:1.5: The "generic" usb-serial driver is only for testing and one-off prototypes.
May 30 21:23:32 vaiocyber kernel: [ 2852.203105] usbserial_generic 3-1:1.5: Tell [email]linux-usb@vger.kernel.org[/email] to add your device to a proper driver.
May 30 21:23:32 vaiocyber kernel: [ 2852.203108] usbserial_generic 3-1:1.5: generic converter detected
May 30 21:23:32 vaiocyber kernel: [ 2852.203235] usb 3-1: generic converter now attached to ttyUSB3
May 30 21:23:32 vaiocyber kernel: [ 2852.203446] usb-storage 3-1:1.6: USB Mass Storage device detected
May 30 21:23:32 vaiocyber kernel: [ 2852.204169] scsi21 : usb-storage 3-1:1.6
May 30 21:23:32 vaiocyber mtp-probe: checking bus 3, device 24: "/sys/devices/pci0000:00/0000:00:14.0/usb3/3-1"
May 30 21:23:32 vaiocyber mtp-probe: bus: 3, device: 24 was not an MTP device
May 30 21:23:32 vaiocyber kernel: [ 2852.247568] usbserial: USB Serial deregistering driver generic
May 30 21:23:32 vaiocyber kernel: [ 2852.247792] generic ttyUSB3: generic converter now disconnected from ttyUSB3
May 30 21:23:32 vaiocyber kernel: [ 2852.248011] generic ttyUSB2: generic converter now disconnected from ttyUSB2
May 30 21:23:32 vaiocyber kernel: [ 2852.248157] generic ttyUSB1: generic converter now disconnected from ttyUSB1
May 30 21:23:32 vaiocyber kernel: [ 2852.248353] generic ttyUSB0: generic converter now disconnected from ttyUSB0
May 30 21:23:32 vaiocyber kernel: [ 2852.248387] usbcore: deregistering interface driver usbserial_generic
May 30 21:23:32 vaiocyber kernel: [ 2852.248436] usbserial_generic 3-1:1.5: device disconnected
May 30 21:23:32 vaiocyber kernel: [ 2852.248468] usbserial_generic 3-1:1.4: device disconnected
May 30 21:23:32 vaiocyber kernel: [ 2852.248502] usbserial_generic 3-1:1.3: device disconnected
May 30 21:23:32 vaiocyber kernel: [ 2852.248542] usbserial_generic 3-1:1.2: device disconnected
May 30 21:23:32 vaiocyber kernel: [ 2852.248570] usbcore: deregistering interface driver usbserial
May 30 21:23:32 vaiocyber kernel: [ 2852.255699] usbcore: registered new interface driver usbserial
May 30 21:23:32 vaiocyber kernel: [ 2852.255714] usbcore: registered new interface driver usbserial_generic
May 30 21:23:32 vaiocyber kernel: [ 2852.255727] usbserial: USB Serial support registered for generic
May 30 21:23:32 vaiocyber kernel: [ 2852.255921] usbserial_generic 3-1:1.2: The "generic" usb-serial driver is only for testing and one-off prototypes.
May 30 21:23:32 vaiocyber kernel: [ 2852.255924] usbserial_generic 3-1:1.2: Tell [email]linux-usb@vger.kernel.org[/email] to add your device to a proper driver.
May 30 21:23:32 vaiocyber kernel: [ 2852.255927] usbserial_generic 3-1:1.2: generic converter detected
May 30 21:23:32 vaiocyber kernel: [ 2852.255998] usb 3-1: generic converter now attached to ttyUSB0
May 30 21:23:32 vaiocyber kernel: [ 2852.256012] usbserial_generic 3-1:1.3: The "generic" usb-serial driver is only for testing and one-off prototypes.
May 30 21:23:32 vaiocyber kernel: [ 2852.256013] usbserial_generic 3-1:1.3: Tell [email]linux-usb@vger.kernel.org[/email] to add your device to a proper driver.
May 30 21:23:32 vaiocyber kernel: [ 2852.256015] usbserial_generic 3-1:1.3: generic converter detected
May 30 21:23:32 vaiocyber kernel: [ 2852.256063] usb 3-1: generic converter now attached to ttyUSB1
May 30 21:23:32 vaiocyber kernel: [ 2852.256070] usbserial_generic 3-1:1.4: The "generic" usb-serial driver is only for testing and one-off prototypes.
May 30 21:23:32 vaiocyber kernel: [ 2852.256072] usbserial_generic 3-1:1.4: Tell [email]linux-usb@vger.kernel.org[/email] to add your device to a proper driver.
May 30 21:23:32 vaiocyber kernel: [ 2852.256073] usbserial_generic 3-1:1.4: generic converter detected
May 30 21:23:32 vaiocyber kernel: [ 2852.256117] usb 3-1: generic converter now attached to ttyUSB2
May 30 21:23:32 vaiocyber kernel: [ 2852.256126] usbserial_generic 3-1:1.5: The "generic" usb-serial driver is only for testing and one-off prototypes.
May 30 21:23:32 vaiocyber kernel: [ 2852.256128] usbserial_generic 3-1:1.5: Tell [email]linux-usb@vger.kernel.org[/email] to add your device to a proper driver.
May 30 21:23:32 vaiocyber kernel: [ 2852.256130] usbserial_generic 3-1:1.5: generic converter detected
May 30 21:23:32 vaiocyber kernel: [ 2852.256730] usb 3-1: generic converter now attached to ttyUSB3
May 30 21:23:32 vaiocyber NetworkManager[772]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:14.0/usb3/3-1/3-1:1.0/net/wwan0, iface: wwan0)
May 30 21:23:32 vaiocyber NetworkManager[772]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:14.0/usb3/3-1/3-1:1.0/net/wwan0, iface: wwan0): no ifupdown configuration found.
May 30 21:23:32 vaiocyber modem-manager[7244]: <info>  (ttyUSB2) opening serial port...
May 30 21:23:32 vaiocyber modem-manager[7244]: <warn>  (ttyUSB2): port attributes not fully set
May 30 21:23:32 vaiocyber modem-manager[7244]: <info>  (ttyUSB2) closing serial port...
May 30 21:23:32 vaiocyber modem-manager[7244]: <info>  (ttyUSB2) serial port closed
May 30 21:23:32 vaiocyber modem-manager[7244]: mm_serial_port_close: assertion 'priv->open_count > 0' failed
May 30 21:23:32 vaiocyber modem-manager[7244]: mm_serial_port_close: assertion 'priv->open_count > 0' failed
May 30 21:23:32 vaiocyber modem-manager[7244]: <info>  (ttyUSB2) opening serial port...
May 30 21:23:32 vaiocyber modem-manager[7244]: <warn>  (ttyUSB2): port attributes not fully set
May 30 21:23:32 vaiocyber modem-manager[7244]: <info>  (ttyUSB1) opening serial port...
May 30 21:23:32 vaiocyber modem-manager[7244]: <warn>  (ttyUSB1): port attributes not fully set
May 30 21:23:32 vaiocyber modem-manager[7244]: <info>  (ttyUSB3) opening serial port...
May 30 21:23:32 vaiocyber modem-manager[7244]: <warn>  (ttyUSB3): port attributes not fully set
May 30 21:23:33 vaiocyber kernel: [ 2853.205123] scsi 21:0:0:0: Direct-Access     HSPA USB SCSI CD-ROM      6225 PQ: 0 ANSI: 0 CCS
May 30 21:23:33 vaiocyber kernel: [ 2853.205577] sd 21:0:0:0: Attached scsi generic sg2 type 0
May 30 21:23:33 vaiocyber kernel: [ 2853.206988] sd 21:0:0:0: [sdb] Attached SCSI removable disk
May 30 21:23:35 vaiocyber modem-manager[7244]: <info>  Caught signal 15, shutting down...
May 30 21:23:35 vaiocyber modem-manager[7244]: <info>  (ttyUSB1) closing serial port...
May 30 21:23:35 vaiocyber modem-manager[7244]: <info>  (ttyUSB1) serial port closed
May 30 21:23:35 vaiocyber modem-manager[7244]: <info>  (ttyUSB2) closing serial port...
May 30 21:23:35 vaiocyber modem-manager[7244]: <info>  (ttyUSB2) serial port closed
May 30 21:23:35 vaiocyber modem-manager[7244]: <info>  (ttyUSB3) closing serial port...
May 30 21:23:35 vaiocyber modem-manager[7244]: <info>  (ttyUSB3) serial port closed
May 30 21:23:35 vaiocyber NetworkManager[772]: <info> ModemManager disappeared
May 30 21:23:35 vaiocyber dbus[710]: [system] Activating service name='org.freedesktop.ModemManager' (using servicehelper)
May 30 21:23:35 vaiocyber modem-manager[7597]: <info>  ModemManager (version 0.6.0.0) starting...
May 30 21:23:35 vaiocyber dbus[710]: [system] Successfully activated service 'org.freedesktop.ModemManager'
May 30 21:23:35 vaiocyber NetworkManager[772]: <info> modem-manager is now available
May 30 21:23:35 vaiocyber modem-manager[7597]: <info>  Loaded plugin 'Ericsson MBM'
May 30 21:23:35 vaiocyber modem-manager[7597]: <info>  Loaded plugin 'Huawei'
May 30 21:23:35 vaiocyber modem-manager[7597]: <info>  Loaded plugin 'ZTE'
May 30 21:23:35 vaiocyber modem-manager[7597]: <info>  Loaded plugin 'Samsung'
May 30 21:23:35 vaiocyber modem-manager[7597]: <info>  Loaded plugin 'Longcheer'
May 30 21:23:35 vaiocyber modem-manager[7597]: <info>  Loaded plugin 'Option High-Speed'
May 30 21:23:35 vaiocyber modem-manager[7597]: <info>  Loaded plugin 'SimTech'
May 30 21:23:35 vaiocyber modem-manager[7597]: <info>  Loaded plugin 'Linktop'
May 30 21:23:35 vaiocyber modem-manager[7597]: <info>  Loaded plugin 'MotoC'
May 30 21:23:35 vaiocyber modem-manager[7597]: <info>  Loaded plugin 'X22X'
May 30 21:23:35 vaiocyber modem-manager[7597]: <info>  Loaded plugin 'Option'
May 30 21:23:35 vaiocyber modem-manager[7597]: <info>  Loaded plugin 'Gobi'
May 30 21:23:35 vaiocyber modem-manager[7597]: <info>  Loaded plugin 'Sierra'
May 30 21:23:35 vaiocyber modem-manager[7597]: <info>  Loaded plugin 'Wavecom'
May 30 21:23:35 vaiocyber modem-manager[7597]: <info>  Loaded plugin 'Nokia'
May 30 21:23:35 vaiocyber modem-manager[7597]: <info>  Loaded plugin 'Novatel'
May 30 21:23:35 vaiocyber modem-manager[7597]: <info>  Loaded plugin 'AnyData'
May 30 21:23:35 vaiocyber modem-manager[7597]: <info>  Loaded plugin 'Cinterion'
May 30 21:23:35 vaiocyber modem-manager[7597]: <info>  Loaded plugin 'Iridium'
May 30 21:23:35 vaiocyber modem-manager[7597]: <info>  Loaded plugin 'Generic'
May 30 21:23:35 vaiocyber modem-manager[7597]: <info>  Successfully loaded 20 plugins
May 30 21:23:35 vaiocyber modem-manager[7597]: <info>  (ttyUSB1) opening serial port...
May 30 21:23:35 vaiocyber modem-manager[7597]: <warn>  (ttyUSB1): port attributes not fully set
May 30 21:23:35 vaiocyber modem-manager[7597]: <info>  (ttyUSB2) opening serial port...
May 30 21:23:35 vaiocyber modem-manager[7597]: <warn>  (ttyUSB2): port attributes not fully set
May 30 21:23:35 vaiocyber modem-manager[7597]: <info>  (ttyUSB3) opening serial port...
May 30 21:23:35 vaiocyber modem-manager[7597]: <warn>  (ttyUSB3): port attributes not fully set
May 30 21:23:46 vaiocyber pppd[7675]: pppd 2.4.5 started by root, uid 0
May 30 21:23:47 vaiocyber chat[7681]: abort on (BUSY)
May 30 21:23:47 vaiocyber chat[7681]: abort on (VOICE)
May 30 21:23:47 vaiocyber chat[7681]: abort on (NO CARRIER)
May 30 21:23:47 vaiocyber chat[7681]: abort on (NO DIALTONE)
May 30 21:23:47 vaiocyber chat[7681]: abort on (NO DIAL TONE)
May 30 21:23:47 vaiocyber chat[7681]: abort on (NO ANSWER)
May 30 21:23:47 vaiocyber chat[7681]: abort on (DELAYED)
May 30 21:23:47 vaiocyber chat[7681]: abort on (ERROR)
May 30 21:23:47 vaiocyber chat[7681]: abort on (+CGATT: 0)
May 30 21:23:47 vaiocyber chat[7681]: send (AT^M)
May 30 21:23:47 vaiocyber chat[7681]: timeout set to 30 seconds
May 30 21:23:47 vaiocyber chat[7681]: expect (OK)
May 30 21:23:47 vaiocyber chat[7681]: AT^M^M
May 30 21:23:47 vaiocyber chat[7681]: OK
May 30 21:23:47 vaiocyber chat[7681]:  -- got it
May 30 21:23:47 vaiocyber chat[7681]: send (ATH^M)
May 30 21:23:47 vaiocyber chat[7681]: expect (OK)
May 30 21:23:47 vaiocyber chat[7681]: ^M
May 30 21:23:47 vaiocyber chat[7681]: ATH^M^M
May 30 21:23:47 vaiocyber chat[7681]: OK
May 30 21:23:47 vaiocyber chat[7681]:  -- got it
May 30 21:23:47 vaiocyber chat[7681]: send (ATE1^M)
May 30 21:23:47 vaiocyber chat[7681]: expect (OK)
May 30 21:23:47 vaiocyber chat[7681]: ^M
May 30 21:23:47 vaiocyber chat[7681]: ATE1^M^M
May 30 21:23:47 vaiocyber chat[7681]: OK
May 30 21:23:47 vaiocyber chat[7681]:  -- got it
May 30 21:23:47 vaiocyber chat[7681]: send (AT+CFUN=1^M)
May 30 21:23:47 vaiocyber chat[7681]: expect (OK)
May 30 21:23:47 vaiocyber chat[7681]: ^M
May 30 21:23:47 vaiocyber chat[7681]: AT+CFUN=1^M^M
May 30 21:23:47 vaiocyber chat[7681]: OK
May 30 21:23:47 vaiocyber chat[7681]:  -- got it
May 30 21:23:47 vaiocyber chat[7681]: send (AT+CGATT?^M)
May 30 21:23:47 vaiocyber chat[7681]: expect (OK)
May 30 21:23:47 vaiocyber chat[7681]: ^M
May 30 21:23:47 vaiocyber chat[7681]: AT+CGATT?^M^M
May 30 21:23:47 vaiocyber chat[7681]: +CGATT: 1^M
May 30 21:23:47 vaiocyber chat[7681]: ^M
May 30 21:23:47 vaiocyber chat[7681]: OK
May 30 21:23:47 vaiocyber chat[7681]:  -- got it
May 30 21:23:47 vaiocyber chat[7681]: send (AT+CGDCONT=1,"IP","internet"^M)
May 30 21:23:47 vaiocyber chat[7681]: expect (OK)
May 30 21:23:47 vaiocyber chat[7681]: ^M
May 30 21:23:47 vaiocyber chat[7681]: AT+CGDCONT=1,"IP","internet"^M^M
May 30 21:23:47 vaiocyber chat[7681]: OK
May 30 21:23:47 vaiocyber chat[7681]:  -- got it
May 30 21:23:47 vaiocyber chat[7681]: send (ATD*99***1#^M)
May 30 21:23:47 vaiocyber chat[7681]: timeout set to 22 seconds
May 30 21:23:47 vaiocyber chat[7681]: expect (CONNECT)
May 30 21:23:47 vaiocyber chat[7681]: ^M
May 30 21:23:47 vaiocyber chat[7681]: ATD*99***1#^M^M
May 30 21:23:47 vaiocyber chat[7681]: CONNECT
May 30 21:23:47 vaiocyber chat[7681]:  -- got it
May 30 21:23:47 vaiocyber chat[7681]: send (^M)
May 30 21:23:47 vaiocyber pppd[7675]: Script /usr/sbin/chat -v -f /etc/3g_modem_connection/3g finished (pid 7680), status = 0x0
May 30 21:23:47 vaiocyber pppd[7675]: Serial connection established.
May 30 21:23:47 vaiocyber pppd[7675]: using channel 15
May 30 21:23:47 vaiocyber pppd[7675]: Using interface ppp0
May 30 21:23:47 vaiocyber pppd[7675]: Connect: ppp0 <--> /dev/ttyUSB0
May 30 21:23:47 vaiocyber NetworkManager[772]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
May 30 21:23:47 vaiocyber NetworkManager[772]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/ppp0, iface: ppp0): no ifupdown configuration found.
May 30 21:23:47 vaiocyber NetworkManager[772]: <warn> /sys/devices/virtual/net/ppp0: couldn't determine device driver; ignoring...
May 30 21:23:47 vaiocyber modem-manager[7597]: <info>  (ttyUSB1) closing serial port...
May 30 21:23:47 vaiocyber modem-manager[7597]: <info>  (ttyUSB1) serial port closed
May 30 21:23:47 vaiocyber modem-manager[7597]: <info>  (ttyUSB1) opening serial port...
May 30 21:23:47 vaiocyber modem-manager[7597]: <info>  (ttyUSB2) closing serial port...
May 30 21:23:47 vaiocyber modem-manager[7597]: <info>  (ttyUSB2) serial port closed
May 30 21:23:47 vaiocyber modem-manager[7597]: <info>  (ttyUSB2) opening serial port...
May 30 21:23:47 vaiocyber modem-manager[7597]: <info>  (ttyUSB3) closing serial port...
May 30 21:23:47 vaiocyber modem-manager[7597]: <info>  (ttyUSB3) serial port closed
May 30 21:23:47 vaiocyber modem-manager[7597]: <info>  (ttyUSB3) opening serial port...
May 30 21:23:48 vaiocyber pppd[7675]: rcvd [LCP ConfReq id=0x1 <asyncmap 0xa0000> <auth pap> <pcomp> <accomp>]
May 30 21:23:48 vaiocyber pppd[7675]: sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x6087f2c5> <pcomp> <accomp>]
May 30 21:23:48 vaiocyber pppd[7675]: sent [LCP ConfAck id=0x1 <asyncmap 0xa0000> <auth pap> <pcomp> <accomp>]
May 30 21:23:48 vaiocyber pppd[7675]: rcvd [LCP ConfNak id=0x1 <asyncmap 0xa0000>]
May 30 21:23:48 vaiocyber pppd[7675]: sent [LCP ConfReq id=0x2 <asyncmap 0xa0000> <magic 0x6087f2c5> <pcomp> <accomp>]
May 30 21:23:48 vaiocyber pppd[7675]: rcvd [LCP ConfAck id=0x2 <asyncmap 0xa0000> <magic 0x6087f2c5> <pcomp> <accomp>]
May 30 21:23:48 vaiocyber pppd[7675]: sent [LCP EchoReq id=0x0 magic=0x6087f2c5]
May 30 21:23:48 vaiocyber pppd[7675]: sent [PAP AuthReq id=0x1 user="" password=<hidden>]
May 30 21:23:48 vaiocyber pppd[7675]: rcvd [LCP EchoRep id=0x0 magic=0x0]
May 30 21:23:48 vaiocyber pppd[7675]: rcvd [PAP AuthAck id=0x1 ""]
May 30 21:23:48 vaiocyber pppd[7675]: PAP authentication succeeded
May 30 21:23:48 vaiocyber pppd[7675]: sent [CCP ConfReq id=0x1 <deflate 15> <deflate(old#) 15> <bsd v1 15>]
May 30 21:23:48 vaiocyber pppd[7675]: sent [IPCP ConfReq id=0x1 <compress VJ 0f 01> <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
May 30 21:23:48 vaiocyber pppd[7675]: rcvd [IPCP ConfReq id=0x1]
May 30 21:23:48 vaiocyber pppd[7675]: sent [IPCP ConfNak id=0x1 <addr 0.0.0.0>]
May 30 21:23:48 vaiocyber pppd[7675]: rcvd [LCP ProtRej id=0x0 80 fd 01 01 00 0f 1a 04 78 00 18 04 78 00 15 03 2f]
May 30 21:23:48 vaiocyber pppd[7675]: Protocol-Reject for 'Compression Control Protocol' (0x80fd) received
May 30 21:23:48 vaiocyber pppd[7675]: rcvd [IPCP ConfRej id=0x1 <compress VJ 0f 01>]
May 30 21:23:48 vaiocyber pppd[7675]: sent [IPCP ConfReq id=0x2 <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
May 30 21:23:48 vaiocyber pppd[7675]: rcvd [IPCP ConfReq id=0x2 <addr 0.0.0.0>]
May 30 21:23:48 vaiocyber pppd[7675]: sent [IPCP ConfRej id=0x2 <addr 0.0.0.0>]
May 30 21:23:48 vaiocyber pppd[7675]: rcvd [IPCP ConfRej id=0x2]
May 30 21:23:48 vaiocyber pppd[7675]: sent [IPCP ConfReq id=0x3 <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
May 30 21:23:48 vaiocyber pppd[7675]: rcvd [IPCP ConfReq id=0x3]
May 30 21:23:48 vaiocyber pppd[7675]: sent [IPCP ConfAck id=0x3]
May 30 21:23:48 vaiocyber pppd[7675]: rcvd [IPCP ConfRej id=0x3]
May 30 21:23:48 vaiocyber pppd[7675]: sent [IPCP ConfReq id=0x4 <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
May 30 21:23:48 vaiocyber pppd[7675]: rcvd [IPCP ConfRej id=0x4]
May 30 21:23:48 vaiocyber pppd[7675]: sent [IPCP ConfReq id=0x5 <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
May 30 21:23:48 vaiocyber pppd[7675]: rcvd [IPCP ConfRej id=0x5]
May 30 21:23:48 vaiocyber pppd[7675]: sent [IPCP ConfReq id=0x6 <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
May 30 21:23:48 vaiocyber pppd[7675]: rcvd [IPCP ConfRej id=0x6]
May 30 21:23:48 vaiocyber pppd[7675]: sent [IPCP ConfReq id=0x7 <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
May 30 21:23:48 vaiocyber pppd[7675]: rcvd [IPCP ConfRej id=0x7]
May 30 21:23:48 vaiocyber pppd[7675]: sent [IPCP ConfReq id=0x8 <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
May 30 21:23:48 vaiocyber pppd[7675]: rcvd [IPCP ConfRej id=0x8]
May 30 21:23:48 vaiocyber pppd[7675]: sent [IPCP ConfReq id=0x9 <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
May 30 21:23:48 vaiocyber pppd[7675]: rcvd [IPCP ConfRej id=0x9]
May 30 21:23:48 vaiocyber pppd[7675]: sent [IPCP ConfReq id=0xa <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
May 30 21:23:48 vaiocyber pppd[7675]: rcvd [IPCP ConfRej id=0xa]
May 30 21:23:48 vaiocyber pppd[7675]: sent [IPCP ConfReq id=0xb <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
May 30 21:23:48 vaiocyber pppd[7675]: rcvd [IPCP ConfRej id=0xb]
May 30 21:23:48 vaiocyber pppd[7675]: sent [IPCP ConfReq id=0xc <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
May 30 21:23:48 vaiocyber pppd[7675]: rcvd [IPCP ConfRej id=0xc]
May 30 21:23:48 vaiocyber pppd[7675]: sent [IPCP ConfReq id=0xd <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
May 30 21:23:48 vaiocyber pppd[7675]: rcvd [IPCP ConfRej id=0xd]
May 30 21:23:48 vaiocyber pppd[7675]: sent [IPCP ConfReq id=0xe <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
May 30 21:23:48 vaiocyber pppd[7675]: rcvd [IPCP ConfRej id=0xe]
May 30 21:23:48 vaiocyber pppd[7675]: sent [IPCP ConfReq id=0xf <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
May 30 21:23:48 vaiocyber pppd[7675]: rcvd [IPCP ConfRej id=0xf]
May 30 21:23:48 vaiocyber pppd[7675]: sent [IPCP ConfReq id=0x10 <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
May 30 21:23:48 vaiocyber pppd[7675]: rcvd [IPCP ConfRej id=0x10]
May 30 21:23:48 vaiocyber pppd[7675]: sent [IPCP ConfReq id=0x11 <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
May 30 21:23:48 vaiocyber pppd[7675]: rcvd [IPCP ConfRej id=0x11]
May 30 21:23:48 vaiocyber pppd[7675]: sent [IPCP ConfReq id=0x12 <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
May 30 21:23:48 vaiocyber pppd[7675]: rcvd [IPCP ConfRej id=0x12]
May 30 21:23:48 vaiocyber pppd[7675]: sent [IPCP ConfReq id=0x13 <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
May 30 21:23:48 vaiocyber pppd[7675]: rcvd [IPCP ConfRej id=0x13]
May 30 21:23:48 vaiocyber pppd[7675]: sent [IPCP ConfReq id=0x14 <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
May 30 21:23:48 vaiocyber pppd[7675]: rcvd [IPCP ConfRej id=0x14]
May 30 21:23:48 vaiocyber pppd[7675]: sent [IPCP ConfReq id=0x15 <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
May 30 21:23:48 vaiocyber pppd[7675]: rcvd [IPCP ConfRej id=0x15]
May 30 21:23:48 vaiocyber pppd[7675]: sent [IPCP ConfReq id=0x16 <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
May 30 21:23:48 vaiocyber pppd[7675]: rcvd [IPCP ConfRej id=0x16]
May 30 21:23:48 vaiocyber pppd[7675]: sent [IPCP ConfReq id=0x17 <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
May 30 21:23:48 vaiocyber pppd[7675]: rcvd [IPCP ConfRej id=0x17]
May 30 21:23:48 vaiocyber pppd[7675]: sent [IPCP ConfReq id=0x18 <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
May 30 21:23:48 vaiocyber pppd[7675]: rcvd [IPCP ConfRej id=0x18]
May 30 21:23:48 vaiocyber pppd[7675]: sent [IPCP ConfReq id=0x19 <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
May 30 21:23:48 vaiocyber pppd[7675]: rcvd [IPCP ConfRej id=0x19]
May 30 21:23:48 vaiocyber pppd[7675]: sent [IPCP ConfReq id=0x1a <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
May 30 21:23:48 vaiocyber pppd[7675]: rcvd [IPCP ConfRej id=0x1a]
May 30 21:23:48 vaiocyber pppd[7675]: sent [IPCP ConfReq id=0x1b <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
May 30 21:23:48 vaiocyber pppd[7675]: rcvd [IPCP ConfRej id=0x1b]
May 30 21:23:48 vaiocyber pppd[7675]: sent [IPCP ConfReq id=0x1c <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
May 30 21:23:48 vaiocyber pppd[7675]: rcvd [IPCP ConfRej id=0x1c]
May 30 21:23:48 vaiocyber pppd[7675]: sent [IPCP ConfReq id=0x1d <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
May 30 21:23:48 vaiocyber pppd[7675]: rcvd [IPCP ConfRej id=0x1d]
May 30 21:23:48 vaiocyber pppd[7675]: sent [IPCP ConfReq id=0x1e <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
May 30 21:23:48 vaiocyber pppd[7675]: rcvd [IPCP ConfRej id=0x1e]
May 30 21:23:48 vaiocyber pppd[7675]: sent [IPCP ConfReq id=0x1f <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
May 30 21:23:48 vaiocyber pppd[7675]: rcvd [IPCP ConfRej id=0x1f]
May 30 21:23:48 vaiocyber pppd[7675]: sent [IPCP ConfReq id=0x20 <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
May 30 21:23:48 vaiocyber pppd[7675]: rcvd [IPCP ConfRej id=0x20]
May 30 21:23:48 vaiocyber pppd[7675]: sent [IPCP ConfReq id=0x21 <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
May 30 21:23:48 vaiocyber pppd[7675]: rcvd [IPCP ConfRej id=0x21]
May 30 21:23:48 vaiocyber pppd[7675]: sent [IPCP ConfReq id=0x22 <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
May 30 21:23:48 vaiocyber pppd[7675]: rcvd [IPCP ConfRej id=0x22]
May 30 21:23:48 vaiocyber pppd[7675]: sent [IPCP ConfReq id=0x23 <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
May 30 21:23:48 vaiocyber pppd[7675]: rcvd [IPCP ConfRej id=0x23]
May 30 21:23:48 vaiocyber pppd[7675]: sent [IPCP ConfReq id=0x24 <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
May 30 21:23:48 vaiocyber pppd[7675]: rcvd [IPCP ConfRej id=0x24]
May 30 21:23:48 vaiocyber pppd[7675]: sent [IPCP ConfReq id=0x25 <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
May 30 21:23:48 vaiocyber pppd[7675]: rcvd [IPCP ConfRej id=0x25]
May 30 21:23:48 vaiocyber pppd[7675]: sent [IPCP ConfReq id=0x26 <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
May 30 21:23:48 vaiocyber pppd[7675]: rcvd [IPCP ConfRej id=0x26]
May 30 21:23:48 vaiocyber pppd[7675]: sent [IPCP ConfReq id=0x27 <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
May 30 21:23:48 vaiocyber pppd[7675]: rcvd [IPCP ConfRej id=0x27]
May 30 21:23:48 vaiocyber pppd[7675]: sent [IPCP ConfReq id=0x28 <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
May 30 21:23:48 vaiocyber pppd[7675]: rcvd [IPCP ConfRej id=0x28]
May 30 21:23:48 vaiocyber pppd[7675]: sent [IPCP ConfReq id=0x29 <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
May 30 21:23:48 vaiocyber pppd[7675]: rcvd [IPCP ConfRej id=0x29]
May 30 21:23:48 vaiocyber pppd[7675]: sent [IPCP ConfReq id=0x2a <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
May 30 21:23:48 vaiocyber pppd[7675]: rcvd [IPCP ConfRej id=0x2a]
May 30 21:23:48 vaiocyber pppd[7675]: sent [IPCP ConfReq id=0x2b <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
May 30 21:23:48 vaiocyber pppd[7675]: rcvd [IPCP ConfRej id=0x2b]
May 30 21:23:48 vaiocyber pppd[7675]: sent [IPCP ConfReq id=0x2c <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
May 30 21:23:48 vaiocyber pppd[7675]: rcvd [IPCP ConfRej id=0x2c]
May 30 21:23:48 vaiocyber pppd[7675]: sent [IPCP ConfReq id=0x2d <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
May 30 21:23:48 vaiocyber pppd[7675]: rcvd [IPCP ConfRej id=0x2d]
May 30 21:23:48 vaiocyber pppd[7675]: sent [IPCP ConfReq id=0x2e <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
May 30 21:23:48 vaiocyber pppd[7675]: rcvd [IPCP ConfRej id=0x2e]
May 30 21:23:48 vaiocyber pppd[7675]: sent [IPCP ConfReq id=0x2f <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
May 30 21:23:48 vaiocyber pppd[7675]: rcvd [IPCP ConfRej id=0x2f]
May 30 21:23:48 vaiocyber pppd[7675]: sent [IPCP ConfReq id=0x30 <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
May 30 21:23:48 vaiocyber pppd[7675]: rcvd [IPCP ConfRej id=0x30]
May 30 21:23:48 vaiocyber pppd[7675]: sent [IPCP ConfReq id=0x31 <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
May 30 21:23:48 vaiocyber pppd[7675]: rcvd [IPCP ConfRej id=0x31]
May 30 21:23:48 vaiocyber pppd[7675]: sent [IPCP ConfReq id=0x32 <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
May 30 21:23:48 vaiocyber pppd[7675]: rcvd [IPCP ConfRej id=0x32]
May 30 21:23:48 vaiocyber pppd[7675]: sent [IPCP ConfReq id=0x33 <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
May 30 21:23:48 vaiocyber pppd[7675]: rcvd [IPCP ConfRej id=0x33]
May 30 21:23:48 vaiocyber pppd[7675]: sent [IPCP ConfReq id=0x34 <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
May 30 21:23:48 vaiocyber pppd[7675]: rcvd [IPCP ConfRej id=0x34]
May 30 21:23:48 vaiocyber pppd[7675]: sent [IPCP ConfReq id=0x35 <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
May 30 21:23:48 vaiocyber pppd[7675]: rcvd [IPCP ConfRej id=0x35]
May 30 21:23:48 vaiocyber pppd[7675]: sent [IPCP ConfReq id=0x36 <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
May 30 21:23:48 vaiocyber pppd[7675]: rcvd [IPCP ConfRej id=0x36]
May 30 21:23:48 vaiocyber pppd[7675]: sent [IPCP ConfReq id=0x37 <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
May 30 21:23:48 vaiocyber pppd[7675]: rcvd [IPCP ConfRej id=0x37]
May 30 21:23:48 vaiocyber pppd[7675]: sent [IPCP ConfReq id=0x38 <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
May 30 21:23:48 vaiocyber pppd[7675]: rcvd [IPCP ConfRej id=0x38]
May 30 21:23:48 vaiocyber pppd[7675]: sent [IPCP ConfReq id=0x39 <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
May 30 21:23:48 vaiocyber pppd[7675]: rcvd [IPCP ConfRej id=0x39]
May 30 21:23:48 vaiocyber pppd[7675]: sent [IPCP ConfReq id=0x3a <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
May 30 21:23:48 vaiocyber pppd[7675]: rcvd [IPCP ConfRej id=0x3a]
May 30 21:23:48 vaiocyber pppd[7675]: sent [IPCP ConfReq id=0x3b <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
May 30 21:23:48 vaiocyber pppd[7675]: rcvd [IPCP ConfRej id=0x3b]
May 30 21:23:48 vaiocyber pppd[7675]: sent [IPCP ConfReq id=0x3c <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
May 30 21:23:48 vaiocyber pppd[7675]: rcvd [IPCP ConfRej id=0x3c]
May 30 21:23:48 vaiocyber pppd[7675]: sent [IPCP ConfReq id=0x3d <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
May 30 21:23:48 vaiocyber pppd[7675]: rcvd [IPCP ConfRej id=0x3d]
May 30 21:23:48 vaiocyber pppd[7675]: sent [IPCP ConfReq id=0x3e <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
May 30 21:23:48 vaiocyber pppd[7675]: rcvd [IPCP ConfRej id=0x3e]
May 30 21:23:48 vaiocyber pppd[7675]: sent [IPCP ConfReq id=0x3f <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
May 30 21:23:48 vaiocyber pppd[7675]: rcvd [IPCP ConfRej id=0x3f]
May 30 21:23:48 vaiocyber pppd[7675]: sent [IPCP ConfReq id=0x40 <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
May 30 21:23:48 vaiocyber pppd[7675]: rcvd [IPCP ConfRej id=0x40]
May 30 21:23:48 vaiocyber pppd[7675]: sent [IPCP ConfReq id=0x41 <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
May 30 21:23:48 vaiocyber pppd[7675]: rcvd [IPCP ConfRej id=0x41]
May 30 21:23:48 vaiocyber pppd[7675]: sent [IPCP ConfReq id=0x42 <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
May 30 21:23:48 vaiocyber pppd[7675]: rcvd [IPCP ConfRej id=0x42]
May 30 21:23:48 vaiocyber pppd[7675]: sent [IPCP ConfReq id=0x43 <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
May 30 21:23:48 vaiocyber pppd[7675]: rcvd [IPCP ConfRej id=0x43]
May 30 21:23:48 vaiocyber pppd[7675]: sent [IPCP ConfReq id=0x44 <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
May 30 21:23:48 vaiocyber pppd[7675]: rcvd [IPCP ConfRej id=0x44]
May 30 21:23:48 vaiocyber pppd[7675]: sent [IPCP ConfReq id=0x45 <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
May 30 21:23:48 vaiocyber pppd[7675]: rcvd [IPCP ConfRej id=0x45]
May 30 21:23:48 vaiocyber pppd[7675]: sent [IPCP ConfReq id=0x46 <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
May 30 21:23:48 vaiocyber pppd[7675]: rcvd [IPCP ConfRej id=0x46]
May 30 21:23:48 vaiocyber pppd[7675]: sent [IPCP ConfReq id=0x47 <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
May 30 21:23:48 vaiocyber pppd[7675]: rcvd [IPCP ConfRej id=0x47]
May 30 21:23:48 vaiocyber pppd[7675]: sent [IPCP ConfReq id=0x48 <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
May 30 21:23:48 vaiocyber pppd[7675]: rcvd [IPCP ConfRej id=0x48]
May 30 21:23:48 vaiocyber pppd[7675]: sent [IPCP ConfReq id=0x49 <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
May 30 21:23:48 vaiocyber pppd[7675]: rcvd [IPCP ConfRej id=0x49]
May 30 21:23:48 vaiocyber pppd[7675]: sent [IPCP ConfReq id=0x4a <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
May 30 21:23:48 vaiocyber pppd[7675]: rcvd [IPCP ConfRej id=0x4a]
May 30 21:23:48 vaiocyber pppd[7675]: sent [IPCP ConfReq id=0x4b <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
May 30 21:23:48 vaiocyber pppd[7675]: rcvd [IPCP ConfRej id=0x4b]
May 30 21:23:48 vaiocyber pppd[7675]: sent [IPCP ConfReq id=0x4c <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
May 30 21:23:48 vaiocyber pppd[7675]: rcvd [IPCP ConfRej id=0x4c]
May 30 21:23:48 vaiocyber pppd[7675]: sent [IPCP ConfReq id=0x4d <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
May 30 21:23:48 vaiocyber pppd[7675]: rcvd [IPCP ConfRej id=0x4d]
May 30 21:23:48 vaiocyber pppd[7675]: sent [IPCP ConfReq id=0x4e <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
May 30 21:23:48 vaiocyber pppd[7675]: rcvd [IPCP ConfRej id=0x4e]
May 30 21:23:48 vaiocyber pppd[7675]: sent [IPCP ConfReq id=0x4f <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
May 30 21:23:48 vaiocyber pppd[7675]: rcvd [IPCP ConfRej id=0x4f]
May 30 21:23:48 vaiocyber pppd[7675]: sent [IPCP ConfReq id=0x50 <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
May 30 21:23:48 vaiocyber pppd[7675]: rcvd [IPCP ConfRej id=0x50]
May 30 21:23:48 vaiocyber pppd[7675]: sent [IPCP ConfReq id=0x51 <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
May 30 21:23:48 vaiocyber pppd[7675]: rcvd [IPCP ConfRej id=0x51]
May 30 21:23:48 vaiocyber pppd[7675]: sent [IPCP ConfReq id=0x52 <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
May 30 21:23:48 vaiocyber pppd[7675]: rcvd [IPCP ConfRej id=0x52]
May 30 21:23:48 vaiocyber pppd[7675]: sent [IPCP ConfReq id=0x53 <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
May 30 21:23:48 vaiocyber pppd[7675]: rcvd [IPCP ConfRej id=0x53]
May 30 21:23:48 vaiocyber pppd[7675]: sent [IPCP ConfReq id=0x54 <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
May 30 21:23:48 vaiocyber pppd[7675]: rcvd [IPCP ConfRej id=0x54]
May 30 21:23:48 vaiocyber pppd[7675]: sent [IPCP ConfReq id=0x55 <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
May 30 21:23:48 vaiocyber pppd[7675]: rcvd [IPCP ConfRej id=0x55]
May 30 21:23:48 vaiocyber pppd[7675]: sent [IPCP ConfReq id=0x56 <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
May 30 21:23:48 vaiocyber pppd[7675]: rcvd [IPCP ConfRej id=0x56]
May 30 21:23:48 vaiocyber pppd[7675]: sent [IPCP ConfReq id=0x57 <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
May 30 21:23:48 vaiocyber pppd[7675]: rcvd [IPCP ConfRej id=0x57]
May 30 21:23:48 vaiocyber rsyslogd-2177: imuxsock begins to drop messages from pid 7675 due to rate-limiting
May 30 21:23:53 vaiocyber modem-manager[7597]: <info>  (ttyUSB1) closing serial port...
May 30 21:23:53 vaiocyber modem-manager[7597]: <info>  (ttyUSB1) serial port closed
May 30 21:23:53 vaiocyber modem-manager[7597]: <info>  (ttyUSB2) closing serial port...
May 30 21:23:53 vaiocyber modem-manager[7597]: <info>  (ttyUSB2) serial port closed
May 30 21:23:53 vaiocyber modem-manager[7597]: <info>  (ttyUSB3) closing serial port...
May 30 21:23:53 vaiocyber modem-manager[7597]: <info>  (ttyUSB3) serial port closed
May 30 21:23:53 vaiocyber modem-manager[7597]: <info>  (ttyUSB1) opening serial port...
May 30 21:23:53 vaiocyber modem-manager[7597]: <warn>  (ttyUSB1): port attributes not fully set
May 30 21:23:53 vaiocyber modem-manager[7597]: <info>  (ttyUSB2) opening serial port...
May 30 21:23:53 vaiocyber modem-manager[7597]: <warn>  (ttyUSB2): port attributes not fully set
May 30 21:23:53 vaiocyber modem-manager[7597]: <info>  (ttyUSB3) opening serial port...
May 30 21:23:53 vaiocyber modem-manager[7597]: <warn>  (ttyUSB3): port attributes not fully set
May 30 21:23:53 vaiocyber rsyslogd-2177: imuxsock lost 14 messages from pid 7675 due to rate-limiting
May 30 21:23:53 vaiocyber pppd[7675]: rcvd [IPCP ConfNak id=0x5e <addr 100.99.57.206> <ms-dns1 112.110.240.5> <ms-dns2 112.110.249.5>]
May 30 21:23:53 vaiocyber pppd[7675]: sent [IPCP ConfReq id=0x5f <addr 100.99.57.206> <ms-dns1 112.110.240.5> <ms-dns2 112.110.249.5>]
May 30 21:23:53 vaiocyber pppd[7675]: rcvd [IPCP ConfAck id=0x5f <addr 100.99.57.206> <ms-dns1 112.110.240.5> <ms-dns2 112.110.249.5>]
May 30 21:23:53 vaiocyber pppd[7675]: Could not determine remote IP address: defaulting to 10.64.64.64
May 30 21:23:53 vaiocyber pppd[7675]: not replacing existing default route via 192.168.1.1
May 30 21:23:53 vaiocyber pppd[7675]: local  IP address 100.99.57.206
May 30 21:23:53 vaiocyber pppd[7675]: remote IP address 10.64.64.64
May 30 21:23:53 vaiocyber pppd[7675]: primary   DNS address 112.110.240.5
May 30 21:23:53 vaiocyber pppd[7675]: secondary DNS address 112.110.249.5
May 30 21:23:53 vaiocyber pppd[7675]: Script /etc/ppp/ip-up started (pid 7716)
May 30 21:23:54 vaiocyber pppd[7675]: Script /etc/ppp/ip-up finished (pid 7716), status = 0x0
May 30 21:23:54 vaiocyber modem-manager[7597]: mm_serial_port_close: assertion 'priv->open_count > 0' failed
May 30 21:23:54 vaiocyber whoopsie[1136]: online
May 30 21:23:54 vaiocyber modem-manager[7597]: <info>  (ttyUSB0) opening serial port...
May 30 21:23:54 vaiocyber modem-manager[7597]: <warn>  (ttyUSB0): port attributes not fully set
May 30 21:23:55 vaiocyber whoopsie[1136]: online
May 30 21:24:05 vaiocyber modem-manager[7597]: <info>  (ttyUSB1) closing serial port...
May 30 21:24:05 vaiocyber modem-manager[7597]: <info>  (ttyUSB1) serial port closed
May 30 21:24:05 vaiocyber modem-manager[7597]: <info>  (ttyUSB1) opening serial port...
May 30 21:24:05 vaiocyber modem-manager[7597]: <info>  (ttyUSB2) closing serial port...
May 30 21:24:05 vaiocyber modem-manager[7597]: <info>  (ttyUSB2) serial port closed
May 30 21:24:05 vaiocyber modem-manager[7597]: <info>  (ttyUSB2) opening serial port...
May 30 21:24:05 vaiocyber modem-manager[7597]: <info>  (ttyUSB3) closing serial port...
May 30 21:24:05 vaiocyber modem-manager[7597]: <info>  (ttyUSB3) serial port closed
May 30 21:24:05 vaiocyber modem-manager[7597]: <info>  (ttyUSB3) opening serial port...
May 30 21:24:11 vaiocyber modem-manager[7597]: <info>  (ttyUSB1) closing serial port...
May 30 21:24:11 vaiocyber modem-manager[7597]: <info>  (ttyUSB1) serial port closed
May 30 21:24:11 vaiocyber modem-manager[7597]: <info>  (ttyUSB2) closing serial port...
May 30 21:24:11 vaiocyber modem-manager[7597]: <info>  (ttyUSB2) serial port closed
May 30 21:24:11 vaiocyber modem-manager[7597]: <info>  (ttyUSB3) closing serial port...
May 30 21:24:11 vaiocyber modem-manager[7597]: <info>  (ttyUSB3) serial port closed
May 30 21:24:12 vaiocyber modem-manager[7597]: <warn>  Couldn't probe for capabilities, probably not a GSM or CDMA modem
May 30 21:24:12 vaiocyber modem-manager[7597]: <info>  (ttyUSB0) closing serial port...
May 30 21:24:12 vaiocyber modem-manager[7597]: <info>  (ttyUSB0) serial port closed
May 30 21:24:12 vaiocyber modem-manager[7597]: <info>  (ttyUSB0) opening serial port...
May 30 21:24:12 vaiocyber modem-manager[7597]: <warn>  (ttyUSB0): port attributes not fully set
May 30 21:24:29 vaiocyber modem-manager[7597]: <warn>  Couldn't probe for capabilities, probably not a GSM or CDMA modem
May 30 21:24:29 vaiocyber modem-manager[7597]: <info>  (ttyUSB0) closing serial port...
May 30 21:24:29 vaiocyber modem-manager[7597]: <info>  (ttyUSB0) serial port closed









May 30 21:39:01 vaiocyber CRON[7834]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -x /usr/lib/php5/sessionclean ] && [ -d /var/lib/php5 ] && /usr/lib/php5/sessionclean /var/lib/php5 $(/usr/lib/php5/maxlifetime))
May 30 21:44:11 vaiocyber pppd[7675]: rcvd [LCP TermReq id=0x2]
May 30 21:44:11 vaiocyber pppd[7675]: LCP terminated by peer
May 30 21:44:11 vaiocyber pppd[7675]: Connect time 20.3 minutes.
May 30 21:44:11 vaiocyber pppd[7675]: Sent 0 bytes, received 40 bytes.
May 30 21:44:11 vaiocyber pppd[7675]: Script /etc/ppp/ip-down started (pid 7868)
May 30 21:44:11 vaiocyber pppd[7675]: sent [LCP TermAck id=0x2]
May 30 21:44:11 vaiocyber pppd[7675]: Terminating on signal 15
May 30 21:44:11 vaiocyber pppd[7675]: Script /etc/ppp/ip-down finished (pid 7868), status = 0x0
May 30 21:44:11 vaiocyber whoopsie[1136]: online
May 30 21:44:12 vaiocyber whoopsie[1136]: online
May 30 21:44:14 vaiocyber pppd[7675]: Connection terminated.
May 30 21:44:14 vaiocyber avahi-daemon[750]: Withdrawing workstation service for ppp0.
May 30 21:44:14 vaiocyber NetworkManager[772]:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
May 30 21:44:15 vaiocyber pppd[7675]: Modem hangup
May 30 21:44:15 vaiocyber pppd[7675]: Exit.
May 30 21:44:41 vaiocyber whoopsie[1136]: online
May 30 21:45:50  whoopsie[1136]: last message repeated 2 times
==========================================================================

---

