---
title: "Mobile Modem hangs up and won't reconnect"
date: 2018-06-02
forum: Networking &amp; Wireless
---

### Post by dazz100 on 2018-06-02
Hi

I have a problem with a remote wireless modem running on a headless server.  I use wvdial.  Occasionally the modem hangs up and won't reconnect without a reboot.
After a boot, the server sets up a ssh tunnel to my home firewall.   It also uploads webcam images you can see on this website [http://kartsportwellington.nz/track-cams/#single/0]("http://kartsportwellington.nz/track-cams/#single/0")
This system actually runs on Raspbian but I had exactly the same problem when it was running on Ubuntu, so I think this is a problem with wvdial and/or the modem, not the OS. 

```

Jun  2 02:15:02 trackcam3 /home/darren/network_alive.pl: [   OK   ]: Network connection ppp0 is confirmed OK
Jun  2 02:27:26 trackcam3 kernel: [661969.228858] option 1-1.4:1.0: device disconnected
Jun  2 02:27:26 trackcam3 kernel: [661969.229022] option 1-1.4:1.1: device disconnected
Jun  2 02:27:26 trackcam3 pppd[4787]: Modem hangup
Jun  2 02:27:26 trackcam3 pppd[4787]: Connect time 951.4 minutes.
Jun  2 02:27:26 trackcam3 pppd[4787]: Sent 27770982 bytes, received 1232910 bytes.
Jun  2 02:27:26 trackcam3 pppd[4787]: restoring old default route to eth0 [172.30.21.1]
Jun  2 02:27:26 trackcam3 pppd[4787]: Connection terminated.
Jun  2 02:27:31 trackcam3 pppd[4787]: Exit.
Jun  2 02:27:31 trackcam3 kernel: [661974.249050] option1 ttyUSB2: GSM modem (1-port) converter now disconnected from ttyUSB2
Jun  2 02:27:31 trackcam3 kernel: [661974.249135] option 1-1.4:1.3: device disconnected
Jun  2 02:27:31 trackcam3 kernel: [661974.348661] usb 1-1.4: reset high-speed USB device number 5 using dwc_otg
Jun  2 02:27:51 trackcam3 kernel: [661995.048841] usb 1-1.4: reset high-speed USB device number 5 using dwc_otg
Jun  2 02:28:12 trackcam3 kernel: [662015.769003] usb 1-1.4: reset high-speed USB device number 5 using dwc_otg
Jun  2 02:28:23 trackcam3 kernel: [662026.409121] usb 1-1.4: reset high-speed USB device number 5 using dwc_otg
Jun  2 02:28:33 trackcam3 kernel: [662036.949714] option 1-1.4:1.0: GSM modem (1-port) converter detected
Jun  2 02:28:33 trackcam3 kernel: [662036.950202] option 1-1.4:1.1: GSM modem (1-port) converter detected
Jun  2 02:28:33 trackcam3 kernel: [662036.950637] option 1-1.4:1.3: GSM modem (1-port) converter detected
Jun  2 02:28:33 trackcam3 kernel: [662036.951016] usb 1-1.4: GSM modem (1-port) converter now attached to ttyUSB2
Jun  2 02:28:33 trackcam3 kernel: [662036.951184] usb 1-1.4: USB disconnect, device number 5
Jun  2 02:28:33 trackcam3 kernel: [662036.951391] option 1-1.4:1.0: device disconnected
Jun  2 02:28:33 trackcam3 kernel: [662036.951728] option 1-1.4:1.1: device disconnected
Jun  2 02:28:33 trackcam3 kernel: [662037.090079] option1 ttyUSB2: GSM modem (1-port) converter now disconnected from ttyUSB2
Jun  2 02:28:33 trackcam3 kernel: [662037.090163] option 1-1.4:1.3: device disconnected
Jun  2 02:28:34 trackcam3 kernel: [662037.189208] usb 1-1.4: new high-speed USB device number 6 using dwc_otg
Jun  2 02:28:54 trackcam3 kernel: [662057.929352] usb 1-1.4: new high-speed USB device number 7 using dwc_otg
Jun  2 02:29:15 trackcam3 kernel: [662078.549636] usb 1-1-port4: attempt power cycle
Jun  2 02:29:16 trackcam3 kernel: [662079.209536] usb 1-1.4: new high-speed USB device number 8 using dwc_otg
Jun  2 02:29:26 trackcam3 kernel: [662089.849682] usb 1-1.4: new high-speed USB device number 9 using dwc_otg
Jun  2 02:30:01 trackcam3 root: Running auto_ssh_running.sh to test if autossh is running.
Jun  2 02:30:01 trackcam3 /home/darren/network_alive.pl: [ Warning! ]: ppp0 not running.  Attempting to restart ppp0 with wvdial
Jun  2 02:30:06 trackcam3 /home/darren/network_alive.pl: [ Warning! ]: wvdial failed to restart ppp0. Restarting network
Jun  2 02:30:11 trackcam3 /home/darren/network_alive.pl: [ Warning! ]: Restarting network failed to restart ppp0!
Jun  2 02:30:11 trackcam3 /home/darren/network_alive.pl: Ping external servers to test network
Jun  2 02:30:51 trackcam3 /home/darren/network_alive.pl: [ Warning! ]: No ppp0 network connection to www.webdrive.co.nz
Jun  2 02:31:31 trackcam3 /home/darren/network_alive.pl: [ Warning! ]: No ppp0 network connection to www.maxnet.co.nz
Jun  2 02:32:11 trackcam3 /home/darren/network_alive.pl: [ Warning! ]: No ppp0 network connection to www.datacentre.co.nz
Jun  2 02:34:11 trackcam3 /home/darren/network_alive.pl: [ WARNING! ]: Rebooting server to restore ppp0 network connection !

```
The system periodically runs a script called network_alive that tests if wvdial is running.  If not, it restarts wvdial.  It then tries to ping multiple websites.  If it can't ping any of them, it reboots the system.

After reboot the modem is detected normally.
```

...
Jun  2 02:34:18 trackcam3 kernel: [    7.433451] usb 1-1.4: New USB device found, idVendor=19d2, idProduct=0031
Jun  2 02:34:18 trackcam3 kernel: [    7.433464] usb 1-1.4: New USB device strings: Mfr=2, Product=1, SerialNumber=3
Jun  2 02:34:18 trackcam3 kernel: [    7.433473] usb 1-1.4: Product: ZTE CDMA Technologies MSM
Jun  2 02:34:18 trackcam3 kernel: [    7.433481] usb 1-1.4: Manufacturer: ZTE, Incorporated
Jun  2 02:34:18 trackcam3 kernel: [    7.433490] usb 1-1.4: SerialNumber: 1234567890ABCDEF
Jun  2 02:34:20 trackcam3 kernel: [    9.579946] Bluetooth: Core ver 2.22
Jun  2 02:34:20 trackcam3 kernel: [    9.580030] NET: Registered protocol family 31

Jun  2 02:34:23 trackcam3 kernel: [   12.040799] usb-storage 1-1.4:1.2: USB Mass Storage device detected
Jun  2 02:34:23 trackcam3 kernel: [   12.043447] scsi host1: usb-storage 1-1.4:1.2
Jun  2 02:34:23 trackcam3 mtp-probe: checking bus 1, device 5: "/sys/devices/platform/soc/3f980000.usb/usb1/1-1/1-1.4"
Jun  2 02:34:23 trackcam3 mtp-probe: bus: 1, device: 5 was not an MTP device
Jun  2 02:34:23 trackcam3 kernel: [   12.170720] usbcore: registered new interface driver usbserial
Jun  2 02:34:23 trackcam3 kernel: [   12.170791] usbcore: registered new interface driver usbserial_generic
Jun  2 02:34:23 trackcam3 kernel: [   12.170855] usbserial: USB Serial support registered for generic
Jun  2 02:34:23 trackcam3 kernel: [   12.209455] usbcore: registered new interface driver option
Jun  2 02:34:23 trackcam3 kernel: [   12.209510] usbserial: USB Serial support registered for GSM modem (1-port)
Jun  2 02:34:23 trackcam3 kernel: [   12.209879] option 1-1.4:1.0: GSM modem (1-port) converter detected
Jun  2 02:34:23 trackcam3 kernel: [   12.211881] option 1-1.4:1.1: GSM modem (1-port) converter detected
Jun  2 02:34:23 trackcam3 kernel: [   12.212180] option 1-1.4:1.3: GSM modem (1-port) converter detected
Jun  2 02:34:23 trackcam3 kernel: [   12.213522] usb 1-1.4: GSM modem (1-port) converter now attached to ttyUSB2
Jun  2 02:34:23 trackcam3 autossh[509]: port set to 0, monitoring disabled
Jun  2 02:34:23 trackcam3 autossh[509]: starting ssh (count 1)
Jun  2 02:34:23 trackcam3 autossh[509]: ssh child pid is 526
Jun  2 02:34:24 trackcam3 kernel: [   13.112547] scsi 1:0:0:0: Direct-Access     ZTE      MMC Storage      322  PQ: 0 ANSI: 2
Jun  2 02:34:24 trackcam3 kernel: [   13.113450] sd 1:0:0:0: Attached scsi generic sg1 type 0
Jun  2 02:34:24 trackcam3 kernel: [   13.119201] sd 1:0:0:0: [sdb] Attached SCSI removable disk
Jun  2 02:34:25 trackcam3 pppd[554]: pppd 2.4.7 started by root, uid 0
Jun  2 02:34:25 trackcam3 kernel: [   14.123060] PPP generic driver version 2.4.2
Jun  2 02:34:25 trackcam3 pppd[554]: Using interface ppp0
Jun  2 02:34:25 trackcam3 pppd[554]: Connect: ppp0 <--> /dev/ttyUSB2
Jun  2 02:34:25 trackcam3 pppd[554]: CHAP authentication succeeded
Jun  2 02:34:25 trackcam3 pppd[554]: CHAP authentication succeeded
Jun  2 02:34:25 trackcam3 kernel: [   14.161863] PPP BSD Compression module registered
Jun  2 02:34:25 trackcam3 kernel: [   14.175809] PPP Deflate Compression module registered
Jun  2 02:34:34 trackcam3 pppd[554]: Could not determine remote IP address: defaulting to 10.64.64.64
Jun  2 02:34:34 trackcam3 pppd[554]: replacing old default route to eth0 [172.30.21.1]
Jun  2 02:34:34 trackcam3 pppd[554]: local  IP address 100.118.107.72
Jun  2 02:34:34 trackcam3 pppd[554]: remote IP address 10.64.64.64
Jun  2 02:34:34 trackcam3 pppd[554]: primary   DNS address 210.55.111.1
Jun  2 02:34:34 trackcam3 pppd[554]: secondary DNS address 122.56.237.1
Jun  2 02:45:02 trackcam3 /home/darren/network_alive.pl: [   OK   ] ppp0 network is running.
Jun  2 02:45:02 trackcam3 /home/darren/network_alive.pl: Ping external servers to test network
Jun  2 02:45:03 trackcam3 /home/darren/network_alive.pl: [   OK   ]: Network connection ppp0 is confirmed OK
Jun  2 03:00:01 trackcam3 root: Running auto_ssh_running.sh to test if autossh is running.
Jun  2 03:00:01 trackcam3 root: autossh is not running. Wait 12min and test again.
Jun  2 03:00:01 trackcam3 /home/darren/network_alive.pl: [   OK   ] ppp0 network is running.
Jun  2 03:00:01 trackcam3 /home/darren/network_alive.pl: Ping external servers to test network
Jun  2 03:00:01 trackcam3 /home/darren/network_alive.pl: [   OK   ]: Network connection ppp0 is confirmed OK
Jun  2 03:12:01 trackcam3 root: Test again if autossh is running
Jun  2 03:12:01 trackcam3 root: autossh is definitely not running.  Restarting autossh
...

```
After rebooting, the connection is remade without any problems.

Does anyone know how to restart the modem after a modem hangup without rebooting the system??

---

