---
title: "[SOLVED] Option HSDPA USB modem"
date: 2008-11-23
forum: Networking &amp; Wireless
---

### Post by beauman on 2008-11-23
Hi! I am trying to get my Option HSDPA USB modem to work. I followed
the instructions from [http://tennessee.ubuntuforums.com/showthread.php?p=6019157](http://tennessee.ubuntuforums.com/showthread.php?p=6019157). But it doesn't work.

In the first moment, everything looks alright. But when
I try to connect, the driver crashes.


Any help appreciated,
Beauman

I wrote everything in one file:

```



 uname -r
2.6.27-7-generic



4-files_for_HSO.tar.gz: 
hsoconnect-py2.5_1.1.83_all.deb  
udev.tar.gz
hsolink_1.0.46-1_i386.deb
hso-1.6.tar.gz


ls /dev/ttyH*
/dev/ttyHS0  /dev/ttyHS1  /dev/ttyHS2  /dev/ttyHS3


[  542.288178] usb 1-2: new full speed USB device using uhci_hcd and address 5
[  542.447345] usb 1-2: configuration #1 chosen from 1 choice
[  542.451243] hso 1-2:1.0: Not our interface
[  542.451511] scsi5 : SCSI emulation for USB Mass Storage devices
[  542.453522] usb-storage: device found at 5
[  542.453538] usb-storage: waiting for device to settle before scanning
[  543.784234] usb 1-2: USB disconnect, address 5
[  546.060169] usb 1-2: new full speed USB device using uhci_hcd and address 6
[  546.220472] usb 1-2: configuration #1 chosen from 1 choice
[  546.226219] hso0: Disabled Privacy Extensions



Modem blinking slowly with long fading time.


The Debug Window
Init serPort /dev/ttyHS1Detected
Port open
'AT'
'OK
''AT+CFUN?'
'+CFUN: 1
'
'
'
'OK
''AT+CLCK="SC",2'
'+CLCK: 0
'
'
'
'OK
''AT+cpin?'
'+CPIN: READY
'
'
'
'OK
''AT_OBLS'
'_OBLS: 1,1,1
'
'
'
'OK
''AT_OWANCALL=1,0,0'
'OK
'(1, 'OK')'AT_OSQI=1'
'OK
'(1, 'OK')'AT_OCTI=1'
'OK
'(1, 'OK')'AT+CNMI=2,1,0,1,0'
'OK
'(1, 'OK')'AT+CREG=1'
'OK
'(1, 'OK')'AT+CGREG=1'
'OK
'(1, 'OK')'AT+COPS=3,0'
'OK
'(1, 'OK')'AT_OSSYS=1'
'OK
'(1, 'OK')'AT+CPMS="SM"'
'+CPMS: 0,25,0,25,0,25
'
'
'
'OK
'(1, '+CPMS: 0,25,0,25,0,25')'AT+CMGF=0'
'OK
'(1, 'OK')'AT+CPMS?'
'+CPMS: "SM",0,25,"SM",0,25,"SM",0,25
'
'
'
'OK
'(1, '+CPMS: "SM",0,25,"SM",0,25,"SM",0,25')'ATI'
'Manufacturer: Option N.V.
'
'Model: GlobeTrotter HSDPA Modem
'
'Revision: 2.5.21Hd (Date: Jun 17 2008, Time: 11:14:20)
''OK''AT+CGMI'
'Option N.V.
'
'
'
'OK
''AT+GMR'
'2.5.21Hd (Date: Jun 17 2008, Time: 11:14:20)
'
'
'
'OK
''AT+CGSN'
'354505025289620,DR2988582N
'
'
'
'OK
''AT_OPSYS=3,2'
'OK
'(1, 'OK')'+CREG: 2''+CGREG: 2''_OSSYSI: 3''+CREG: 1''+CGREG: 1'DUff response'+CGREG: 1''_OSSYSI: 2''AT+csq''+CSQ: 23,99''OK''AT+cgreg?'
'+CGREG: 1,1
'
'
'
'OK
''AT+COPS?'
'+COPS: 0,0,"tele.ring",2
'
'
'
'OK
'end of pre
'AT_OPSYS?'
'_OPSYS: 3,2
'
'
'
'OK
'Sending ->AT_OWCTI?<<AT_OWCTI?>>
<<_OWCTI: 2>>
<<OK>>
Sending ->AT+CSQ<<AT+CSQ>>
<<+CSQ: 23,99>>
<<OK>>
Sending ->AT+CGREG?<<AT+CGREG?>>
<<+CGREG: 1,1>>
<<OK>>
Sending ->AT+cops?<<AT+cops?>>
<<+COPS: 0,0,"tele.ring",2>>
<<OK>>
Sending ->AT_OWCTI?<<AT_OWCTI?>>
<<_OWCTI: 2>>
<<OK>>


The tick counter is running, HSOconnect says:
Tele.Ring Registered HSDPA


so far, so good.

I press "Connect"

After a while (15 sec.) the modem will blink very fast. After another 30 sec.
a window pops up:

ERROR: Problem talking to modem

dmesg:
[  546.226219] hso0: Disabled Privacy Extensions
[  738.196187] usb 1-2: reset full speed USB device using uhci_hcd and address 6
[  738.316188] usb 1-2: device descriptor read/64, error -71
[  738.540203] usb 1-2: device descriptor read/64, error -71
[  738.756188] usb 1-2: reset full speed USB device using uhci_hcd and address 6
[  738.876155] usb 1-2: device descriptor read/64, error -71
[  739.100188] usb 1-2: device descriptor read/64, error -71
[  739.316183] usb 1-2: reset full speed USB device using uhci_hcd and address 6
[  739.724177] usb 1-2: device not accepting address 6, error -71
[  739.836190] usb 1-2: reset full speed USB device using uhci_hcd and address 6
[  740.248174] usb 1-2: device not accepting address 6, error -71
[  740.248813] usb 1-2: USB disconnect, address 6
[  740.416133] usb 1-2: new full speed USB device using uhci_hcd and address 7
[  740.536179] usb 1-2: device descriptor read/64, error -71
[  740.760181] usb 1-2: device descriptor read/64, error -71
[  740.976185] usb 1-2: new full speed USB device using uhci_hcd and address 8
[  741.152184] usb 1-2: device descriptor read/64, error -71
[  741.432187] usb 1-2: device descriptor read/64, error -71
[  741.648203] usb 1-2: new full speed USB device using uhci_hcd and address 9
[  742.060188] usb 1-2: device not accepting address 9, error -71
[  742.172182] usb 1-2: new full speed USB device using uhci_hcd and address 10
[  742.580205] usb 1-2: device not accepting address 10, error -71
[  742.580252] hub 1-0:1.0: unable to enumerate USB device on port 2

yo@LosBastardos:~/hso$ ls /dev/ttyH*
/dev/ttyHS1



Clicked Connect'AT+CGDCONT=1,"IP","web"
'OK
"AT$QCPDPP=1,1"web","web@telering.at"
'OK
"AT_OWANCALL=1,1,1'
'OK
"AT_OWANDATA=1'
'ERROR
'DUff responseDUff response

```

---

### Post by beauman on 2008-11-23
It works now.

[http://www.pharscape.org/component/option,com_forum/Itemid,68/page,posting/](http://www.pharscape.org/component/option,com_forum/Itemid,68/page,posting/)

This site provides a [tutorial]("http://doc.ubuntu-fr.org/tutoriel/icon225 i") in french :D

---

