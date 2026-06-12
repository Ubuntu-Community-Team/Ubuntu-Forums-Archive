---
title: "Mobile Broadband problem"
date: 2010-01-16
forum: New to Ubuntu
---

### Post by mvalviar on 2010-01-16
I'm trying get a modem connected via usb. I works as expected initially. I just plug it in and I can find it in network manager. I just tweak a few settings and it connects. However it seem ubuntu keeps on connecting and disconnecting the device rendering the connection useless. Here's the log if it helps.```
Jan 16 15:35:38 mumee kernel: [ 3342.808025] usb 1-6: new high speed USB device using ehci_hcd and address 27
Jan 16 15:35:43 mumee kernel: [ 3347.951930] usb 1-6: configuration #1 chosen from 1 choice
Jan 16 15:35:43 mumee kernel: [ 3347.957469] scsi425 : SCSI emulation for USB Mass Storage devices
Jan 16 15:35:43 mumee kernel: [ 3347.957811] scsi426 : SCSI emulation for USB Mass Storage devices
Jan 16 15:35:48 mumee kernel: [ 3352.959476] scsi 426:0:0:0: Direct-Access     HUAWEI   MMC Storage      2.31 PQ: 0 ANSI: 2
Jan 16 15:35:48 mumee kernel: [ 3352.960170] sd 426:0:0:0: Attached scsi generic sg2 type 0
Jan 16 15:35:49 mumee kernel: [ 3354.078164] usb 1-6: USB disconnect, address 27
Jan 16 15:35:49 mumee kernel: [ 3354.078708] sd 426:0:0:0: [sdb] READ CAPACITY failed
Jan 16 15:35:49 mumee kernel: [ 3354.078712] sd 426:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
Jan 16 15:35:49 mumee kernel: [ 3354.078718] sd 426:0:0:0: [sdb] Sense not available.
Jan 16 15:35:49 mumee kernel: [ 3354.078743] sd 426:0:0:0: [sdb] Write Protect is off
Jan 16 15:35:49 mumee kernel: [ 3354.078988] sd 426:0:0:0: [sdb] READ CAPACITY failed
Jan 16 15:35:49 mumee kernel: [ 3354.078992] sd 426:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
Jan 16 15:35:49 mumee kernel: [ 3354.078997] sd 426:0:0:0: [sdb] Sense not available.
Jan 16 15:35:49 mumee kernel: [ 3354.079025] sd 426:0:0:0: [sdb] Attached SCSI removable disk
Jan 16 15:35:55 mumee kernel: [ 3360.492031] usb 1-6: new high speed USB device using ehci_hcd and address 28
Jan 16 15:35:56 mumee kernel: [ 3360.635498] usb 1-6: configuration #1 chosen from 1 choice
Jan 16 15:35:56 mumee kernel: [ 3360.640650] option 1-6:1.0: GSM modem (1-port) converter detected
Jan 16 15:35:56 mumee kernel: [ 3360.640805] usb 1-6: GSM modem (1-port) converter now attached to ttyUSB0
Jan 16 15:35:56 mumee kernel: [ 3360.645587] option 1-6:1.1: GSM modem (1-port) converter detected
Jan 16 15:35:56 mumee kernel: [ 3360.645706] usb 1-6: GSM modem (1-port) converter now attached to ttyUSB1
Jan 16 15:35:56 mumee kernel: [ 3360.648029] option 1-6:1.2: GSM modem (1-port) converter detected
Jan 16 15:35:56 mumee kernel: [ 3360.648157] usb 1-6: GSM modem (1-port) converter now attached to ttyUSB2
Jan 16 15:35:56 mumee kernel: [ 3360.657056] scsi430 : SCSI emulation for USB Mass Storage devices
Jan 16 15:35:56 mumee kernel: [ 3360.658638] scsi431 : SCSI emulation for USB Mass Storage devices
Jan 16 15:36:01 mumee kernel: [ 3365.659418] scsi 430:0:0:0: CD-ROM            HUAWEI   Mass Storage     2.31 PQ: 0 ANSI: 2
Jan 16 15:36:01 mumee kernel: [ 3365.661401] scsi 431:0:0:0: Direct-Access     HUAWEI   MMC Storage      2.31 PQ: 0 ANSI: 2
Jan 16 15:36:01 mumee kernel: [ 3365.685639] sr1: scsi-1 drive
Jan 16 15:36:01 mumee kernel: [ 3365.685904] sr 430:0:0:0: Attached scsi generic sg2 type 5
Jan 16 15:36:01 mumee kernel: [ 3365.686134] sd 431:0:0:0: Attached scsi generic sg3 type 0
Jan 16 15:36:08 mumee kernel: [ 3373.000341] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
Jan 16 15:36:08 mumee kernel: [ 3373.000378] option 1-6:1.0: device disconnected
Jan 16 15:36:08 mumee kernel: [ 3373.002253] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
Jan 16 15:36:08 mumee kernel: [ 3373.002279] option 1-6:1.1: device disconnected
Jan 16 15:36:08 mumee kernel: [ 3373.002389] option1 ttyUSB2: GSM modem (1-port) converter now disconnected from ttyUSB2
Jan 16 15:36:08 mumee kernel: [ 3373.002428] option 1-6:1.2: device disconnected
Jan 16 15:36:31 mumee kernel: [ 3396.100028] usb 1-6: reset high speed USB device using ehci_hcd and address 28
Jan 16 15:36:31 mumee kernel: [ 3396.237584] option 1-6:1.2: GSM modem (1-port) converter detected
Jan 16 15:36:31 mumee kernel: [ 3396.237715] usb 1-6: GSM modem (1-port) converter now attached to ttyUSB0
Jan 16 15:36:31 mumee kernel: [ 3396.243326] option 1-6:1.1: GSM modem (1-port) converter detected
Jan 16 15:36:31 mumee kernel: [ 3396.243447] usb 1-6: GSM modem (1-port) converter now attached to ttyUSB1
Jan 16 15:36:31 mumee kernel: [ 3396.245772] option 1-6:1.0: GSM modem (1-port) converter detected
Jan 16 15:36:31 mumee kernel: [ 3396.245924] usb 1-6: GSM modem (1-port) converter now attached to ttyUSB2
Jan 16 15:36:31 mumee kernel: [ 3396.248791] option1 ttyUSB2: GSM modem (1-port) converter now disconnected from ttyUSB2
Jan 16 15:36:31 mumee kernel: [ 3396.248826] option 1-6:1.0: device disconnected
Jan 16 15:36:31 mumee kernel: [ 3396.248933] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
Jan 16 15:36:31 mumee kernel: [ 3396.248963] option 1-6:1.1: device disconnected
Jan 16 15:36:31 mumee kernel: [ 3396.249061] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
Jan 16 15:36:31 mumee kernel: [ 3396.249091] option 1-6:1.2: device disconnected
Jan 16 15:36:31 mumee kernel: [ 3396.372032] usb 1-6: reset high speed USB device using ehci_hcd and address 28
Jan 16 15:36:31 mumee kernel: [ 3396.509938] option 1-6:1.2: GSM modem (1-port) converter detected
Jan 16 15:36:31 mumee kernel: [ 3396.510064] usb 1-6: GSM modem (1-port) converter now attached to ttyUSB0
Jan 16 15:36:31 mumee kernel: [ 3396.512926] option 1-6:1.1: GSM modem (1-port) converter detected
Jan 16 15:36:31 mumee kernel: [ 3396.513029] usb 1-6: GSM modem (1-port) converter now attached to ttyUSB1
Jan 16 15:36:31 mumee kernel: [ 3396.516597] option 1-6:1.0: GSM modem (1-port) converter detected
Jan 16 15:36:31 mumee kernel: [ 3396.516787] usb 1-6: GSM modem (1-port) converter now attached to ttyUSB2
Jan 16 15:36:32 mumee kernel: [ 3396.547110] sd 431:0:0:0: [sdb] Attached SCSI removable disk
Jan 16 15:36:42 mumee pppd[11814]: Plugin /usr/lib/pppd/2.4.4/nm-pppd-plugin.so loaded.
Jan 16 15:36:42 mumee pppd[11814]: pppd 2.4.5 started by root, uid 0
Jan 16 15:36:42 mumee pppd[11814]: Using interface ppp0
Jan 16 15:36:42 mumee pppd[11814]: Connect: ppp0 <--> /dev/ttyUSB2
Jan 16 15:36:42 mumee pppd[11814]: CHAP authentication succeeded
Jan 16 15:36:42 mumee pppd[11814]: CHAP authentication succeeded
Jan 16 15:36:48 mumee pppd[11814]: Could not determine remote IP address: defaulting to 10.64.64.64
Jan 16 15:36:48 mumee pppd[11814]: local  IP address 10.31.2.112
Jan 16 15:36:48 mumee pppd[11814]: remote IP address 10.64.64.64
Jan 16 15:36:48 mumee pppd[11814]: primary   DNS address 202.126.40.5
Jan 16 15:36:48 mumee pppd[11814]: secondary DNS address 222.127.143.5
Jan 16 15:37:03 mumee pppd[11814]: Modem hangup
Jan 16 15:37:03 mumee pppd[11814]: Connect time 0.3 minutes.
Jan 16 15:37:03 mumee pppd[11814]: Sent 6826 bytes, received 4655 bytes.
Jan 16 15:37:03 mumee kernel: [ 3428.051003] option1 ttyUSB2: GSM modem (1-port) converter now disconnected from ttyUSB2
Jan 16 15:37:03 mumee kernel: [ 3428.051029] option 1-6:1.0: device disconnected
Jan 16 15:37:03 mumee kernel: [ 3428.051139] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
Jan 16 15:37:03 mumee kernel: [ 3428.051173] option 1-6:1.1: device disconnected
Jan 16 15:37:03 mumee kernel: [ 3428.051279] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
Jan 16 15:37:03 mumee kernel: [ 3428.051316] option 1-6:1.2: device disconnected
Jan 16 15:37:03 mumee pppd[11814]: Connection terminated.
Jan 16 15:37:03 mumee pppd[11814]: Exit.
Jan 16 15:37:03 mumee kernel: [ 3428.161225] usb 1-6: reset high speed USB device using ehci_hcd and address 28
Jan 16 15:37:03 mumee kernel: [ 3428.298248] option 1-6:1.2: GSM modem (1-port) converter detected
Jan 16 15:37:03 mumee kernel: [ 3428.298381] usb 1-6: GSM modem (1-port) converter now attached to ttyUSB0
Jan 16 15:37:03 mumee kernel: [ 3428.298618] option 1-6:1.1: GSM modem (1-port) converter detected
Jan 16 15:37:03 mumee kernel: [ 3428.298707] usb 1-6: GSM modem (1-port) converter now attached to ttyUSB1
Jan 16 15:37:03 mumee kernel: [ 3428.298911] option 1-6:1.0: GSM modem (1-port) converter detected
Jan 16 15:37:03 mumee kernel: [ 3428.299044] usb 1-6: GSM modem (1-port) converter now attached to ttyUSB2
Jan 16 15:37:14 mumee kernel: [ 3438.988892] option1 ttyUSB2: GSM modem (1-port) converter now disconnected from ttyUSB2
Jan 16 15:37:14 mumee kernel: [ 3438.988928] option 1-6:1.0: device disconnected
Jan 16 15:37:14 mumee kernel: [ 3438.990220] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
Jan 16 15:37:14 mumee kernel: [ 3438.990245] option 1-6:1.1: device disconnected
Jan 16 15:37:14 mumee kernel: [ 3438.990353] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
Jan 16 15:37:14 mumee kernel: [ 3438.990386] option 1-6:1.2: device disconnected
Jan 16 15:37:14 mumee kernel: [ 3439.100031] usb 1-6: reset high speed USB device using ehci_hcd and address 28
Jan 16 15:37:14 mumee kernel: [ 3439.276735] option 1-6:1.2: GSM modem (1-port) converter detected
Jan 16 15:37:14 mumee kernel: [ 3439.276862] usb 1-6: GSM modem (1-port) converter now attached to ttyUSB0
Jan 16 15:37:14 mumee kernel: [ 3439.276956] option 1-6:1.1: GSM modem (1-port) converter detected
Jan 16 15:37:14 mumee kernel: [ 3439.277026] usb 1-6: GSM modem (1-port) converter now attached to ttyUSB1
Jan 16 15:37:14 mumee kernel: [ 3439.289389] option 1-6:1.0: GSM modem (1-port) converter detected
Jan 16 15:37:14 mumee kernel: [ 3439.289578] usb 1-6: GSM modem (1-port) converter now attached to ttyUSB2

```

---

### Post by prshah on 2010-01-16
> **mvalviar said:**
> connecting and disconnecting the device

It looks to me like the "modem" is not getting enough power; does it have a single USB cable or a "Y" cable (2 + 1 USB)? If it is a Y-cable, you need to plug both ends of the Y to your computer and the single end to the "modem".

If not that, maybe you are using a "usb hub"? Try plugging it directly into your computer, or using a externally powered hub.

---

### Post by 3rdalbum on 2010-01-16
If there is a virtual CD-ROM (you get an icon on the desktop as though you'd plugged in a disk or flash drive), then try Ejecting the disk before connecting.

---

### Post by mvalviar on 2010-01-16
It's this product. [http://tattoo.globe.com.ph/product/kits-and-new-skin-packs](http://tattoo.globe.com.ph/product/kits-and-new-skin-packs). It's the doggle with the cap on. Its a single usb plug. I don't have a hub. I'm using the usb ports in the front and back panel of my computer. There doesn't seem to be a difference. 

Well I just loaded credits worth an hour to test if I can get it to work on ubuntu. Unfortunately though I wasn't able to use it in ubuntu, when I booted to windows my browser says my credits ran out. 

I should still be able to see that same info page on ubuntu if I get the modem connected properly even without credits right?

---

### Post by mvalviar on 2010-01-17
up

---

### Post by mvalviar on 2010-01-17
I just solved it. I seems that the from panel usb ports aren't supplying the dongle with enough power. I plugged the dongle at the usb ports in the rear panel and it works. 

Thank you for pointing out that possibility.

---

