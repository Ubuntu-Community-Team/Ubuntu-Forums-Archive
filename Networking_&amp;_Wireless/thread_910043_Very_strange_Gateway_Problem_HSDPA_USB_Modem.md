---
title: "Very strange Gateway Problem HSDPA USB Modem"
date: 2008-09-04
forum: Networking &amp; Wireless
---

### Post by e-dard on 2008-09-04
Hi all,

I have the Huawei e220 usb modem, which I use through the service 3 in the UK.

I am running Hardy.  Basically, I can connect fine using either NetManager 0.7, wvdial or the vmc software, but I get no actual internet access.  I get given an IP address by the service provider, as well as the **correct nameservers** but when I ping anything I get 'unknown host'. I have all the settings correctly configured in wvdial and the other applications.  This has worked in the past no problems.  I thought it may be a problem with airprime, so I blacklisted it and now I get the modem recognised as it used to (with the three ttyUSB bits) I think using usb_serial.

Here is dmesg on connection of the modem:

```
[  410.680498] usb 4-1: new full speed USB device using uhci_hcd and address 2
[  410.842046] usb 4-1: configuration #1 chosen from 1 choice
[  408.779905] usbcore: registered new interface driver libusual
[  411.199050] Initializing USB Mass Storage driver...
[  411.202647] scsi2 : SCSI emulation for USB Mass Storage devices
[  411.204936] usbcore: registered new interface driver usb-storage
[  411.204948] USB Mass Storage support registered.
[  411.205158] usb-storage: device found at 2
[  411.205161] usb-storage: waiting for device to settle before scanning
[  411.224232] usb 4-1: USB disconnect, address 2
[  411.958754] usb 4-1: new full speed USB device using uhci_hcd and address 3
[  409.751394] usb 4-1: configuration #1 chosen from 1 choice
[  409.754675] usb-storage: probe of 4-1:1.0 failed with error -5
[  409.758241] usb-storage: probe of 4-1:1.1 failed with error -5
[  409.788765] scsi5 : SCSI emulation for USB Mass Storage devices
[  409.799121] usb-storage: device found at 3
[  409.799129] usb-storage: waiting for device to settle before scanning
[  410.029413] usbcore: registered new interface driver usbserial
[  410.029889] /build/buildd/linux-2.6.24/drivers/usb/serial/usb-serial.c: USB Serial support registered for generic
[  410.030505] usbcore: registered new interface driver usbserial_generic
[  410.030514] /build/buildd/linux-2.6.24/drivers/usb/serial/usb-serial.c: USB Serial Driver core
[  412.581789] /build/buildd/linux-2.6.24/drivers/usb/serial/usb-serial.c: USB Serial support registered for GSM modem (1-port)
[  412.581861] option 4-1:1.0: GSM modem (1-port) converter detected
[  412.582052] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB0
[  412.582073] option 4-1:1.1: GSM modem (1-port) converter detected
[  412.582199] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB1
[  412.582223] usbcore: registered new interface driver option
[  412.582229] /build/buildd/linux-2.6.24/drivers/usb/serial/option.c: USB Driver for GSM modems: v0.7.1
[  411.607513] usb-storage: device scan complete
[  413.970413] scsi 5:0:0:0: CD-ROM HUAWEI Mass Storage 2.31 PQ: 0 ANSI: 2
[  413.971820] scsi 5:0:0:0: Attached scsi generic sg1 type 5
[  411.708260] Driver 'sr' needs updating - please use bus_type methods
[  414.108256] sr0: scsi-1 drive
[  414.108268] Uniform CD-ROM driver Revision: 3.20
[  414.108386] sr 5:0:0:0: Attached scsi CD-ROM sr0

```

Then if I do:
```
sudo ls -l /dev/ttyUSB*
```

the system returns:
```
crw-rw---- 1 root dialout 188, 0 2008-09-04 10:14 /dev/ttyUSB0
crw-rw---- 1 root dialout 188, 1 2008-09-04 10:14 /dev/ttyUSB1
```

Everything looks rosy.  I can then connect to my provider using any methods out there, it connects fine and I get all the settings from my provider.  For example, here is wvdial connecting with the modem:

```
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Sending: AT+CGDCONT=1,"IP","three.co.uk"
AT+CGDCONT=1,"IP","three.co.uk"
OK
--> Modem initialized.
--> Sending: ATDT*99#
--> Waiting for carrier.
ATDT*99#
CONNECT
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Thu Sep  4 10:18:02 2008
--> Pid of pppd: 7560
--> Using interface ppp0
--> local  IP address 10.116.35.126
--> remote IP address 10.64.64.64
--> primary   DNS address 172.31.76.69
--> secondary DNS address 172.31.140.69

```

This looks as it should look, if I do:

```
~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.64.64.64     *               255.255.255.255 UH    0      0        0 ppp0

```

I am not sure if this is correct.  Finally, non of the internet works, if I ping anything I get unknown host. Does anyone have any advice??

Cheers,

e-dard

---

### Post by TDFlanders on 2008-09-05
Hi there,

I have absolutely no time right now. Could you first take a look at these?



[http://wwwu.uni-klu.ac.at/agebhard/HuaweiE220/](http://wwwu.uni-klu.ac.at/agebhard/HuaweiE220/)
[http://ske.sourceforge.net/html/projects/huawei/huawei_tre.html](http://ske.sourceforge.net/html/projects/huawei/huawei_tre.html)
[http://joergweis.wordpress.com/2007/01/03/huawei-e220-and-ubuntu-610/](http://joergweis.wordpress.com/2007/01/03/huawei-e220-and-ubuntu-610/)
[http://www.kanoistika.sk/bobovsky/archiv/umts/](http://www.kanoistika.sk/bobovsky/archiv/umts/)
[http://forum.ubuntuusers.de/viewtopic.php?p=677729#677729](http://forum.ubuntuusers.de/viewtopic.php?p=677729#677729)
[http://ubuntuforums.org/showthread.php?t=843973&highlight=huawei+e220](http://ubuntuforums.org/showthread.php?t=843973&highlight=huawei+e220)
[http://ubuntuforums.org/showpost.php?p=5176814&postcount=7](http://ubuntuforums.org/showpost.php?p=5176814&postcount=7)
[http://ubuntuforums.org/showthread.php?t=609534&highlight=Mobile+Broadband+USB+Modem](http://ubuntuforums.org/showthread.php?t=609534&highlight=Mobile+Broadband+USB+Modem)
[https://help.ubuntu.com/community/DialupModemHowto/Huawei/E220](https://help.ubuntu.com/community/DialupModemHowto/Huawei/E220)
[http://linux.die.net/man/1/minicom](http://linux.die.net/man/1/minicom)
[http://www.telix.com/](http://www.telix.com/)
[http://ubuntu.frankenberger.at/Huawei_E220.html](http://ubuntu.frankenberger.at/Huawei_E220.html)

I read in the German script about "APN". According to 3 Phone support their APN is 3internet. Could you try and replace three.co.uk with 3 internet? 

Please try out George Vista's post as well, I have not had time to do so. 

[http://ubuntuforums.org/showthread.php?t=897695&highlight=huawei](http://ubuntuforums.org/showthread.php?t=897695&highlight=huawei)

I hope to provide you with more info soon (couple of days).

---

### Post by spynappels on 2008-09-09
you can also try 3netaccess as the APN as per [http://ask3.three.co.uk/SRVS/Data/Hutch/KnowledgeBases/Ask3/document/web/USB_modem/windows_trouble_installing.htm](http://ask3.three.co.uk/SRVS/Data/Hutch/KnowledgeBases/Ask3/document/web/USB_modem/windows_trouble_installing.htm)

Stefan.

---

### Post by e-dard on 2008-09-10
Dear all,

thanks for the replies.  

For anyone who sees this and is on Three in the UK, 3internet will not work as an APN, three.co.uk works fine (have not tried 3netaccess).

Anyway, it turns out it was me being a complete idiot.  I forgot that I had moblock running and it was  blocking communication between the computer and the name server that the modem wanted to use (no idea why).

Something became fishy when I realised that I could ping google's ip but not google.com.

Anyway, all solved now!

Cheers.

---

