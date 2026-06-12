---
title: "wwan card N5321 gw USB disconnect"
date: 2014-04-19
forum: Networking &amp; Wireless
---

### Post by kuku2 on 2014-04-19
Hello,

I recently bought a lenovo t450p with integrated wwan card n5321 gw. everything worked nearly out of the box on installation including the wwan card. I can connect the wwan card to vodafone and everything works ok for a period of time  20 - 30 minutes or less  but then it disconnects. The message i get in the log is USB disconnect.

Here is an example: 

Apr 17 12:13:44 kuku-laptop kernel: [14017.635975] usb 3-10: USB disconnect, device number 3
Apr 17 12:13:45 kuku-laptop kernel: [14018.776205] usb 3-10: new high-speed USB device number 8 using xhci_hcd
Apr 17 12:13:45 kuku-laptop kernel: [14018.795849] usb 3-10: New USB device found, idVendor=0bdb, idProduct=193e
Apr 17 12:13:45 kuku-laptop kernel: [14018.795860] usb 3-10: New USB device strings: Mfr=1, Product=2, SerialNumber=3
Apr 17 12:13:45 kuku-laptop kernel: [14018.830342] cdc_acm 3-10:1.1: ttyACM0: USB ACM device
Apr 17 12:13:45 kuku-laptop kernel: [14018.834767] cdc_acm 3-10:1.3: ttyACM1: USB ACM device
Apr 17 12:13:45 kuku-laptop kernel: [14018.842562] cdc_wdm 3-10:1.5: cdc-wdm0: USB WDM device
Apr 17 12:13:45 kuku-laptop kernel: [14018.858875] cdc_wdm 3-10:1.8: cdc-wdm1: USB WDM device
Apr 17 12:13:45 kuku-laptop kernel: [14018.859329] cdc_acm 3-10:1.9: ttyACM2: USB ACM device



After debugging modem-manager and ppp i found that just before "USB disconnect" and  "pppd hangup" i get from modem-manager debuging this :

 modem-manager[6076]: <debug> [1397911530.868536] [mm-at-serial-port.c:333] debug_log(): (ttyACM1): <-- '<CR><LF>+CIEV: 2,3<CR><LF>'

It seems to me that the +CIEV: 2,3 command initiates disconnection. 

Does anyone know what that command is or anything related ? I searched the net but could not find anything about that command.

Thanks in advance.

---

### Post by praseodym on 2014-04-19
Hi,

which Ubuntu version is it? In 13.xx there was a buggy modemmanager file, try the one from 12.04 instead, it also works without additional dependencies:

[http://packages.ubuntu.com/precise/modemmanager](http://packages.ubuntu.com/precise/modemmanager)

and prevent it from being updated by the file /etc/apt/preferences.d/modemmanager with
```

Package: modemmanager
Pin: version 0.5.2.0*
Pin-Priority: 1000
```

---

### Post by kuku2 on 2014-04-21
Thanks for the reply.
I am running 12.04. My modemanager version is 0.5.2.0

Package: modemmanager                    
State: installed
Automatically installed: yes
Version: 0.5.2.0-0ubuntu2

---

### Post by praseodym on 2014-04-21
Please check these steps:

[http://ubuntuforums.org/showthread.php?t=1831649&highlight=umts+checklist](http://ubuntuforums.org/showthread.php?t=1831649&highlight=umts+checklist)

---

### Post by kuku2 on 2014-05-27
Thanks for the link. I got it to work with wvdial. It seems there is an issue with modem manager. This is the /etc/wvdial.conf in case somebody finds it useful:

[Dialer Defaults]
Init1 = ATZ
Init2 = ATE0V1&D2&C1S0=0+IFC=2,2
Modem Type = USB Modem
New PPPD = yes
Modem = /dev/ttyACM1
Init3 = AT+CGDCONT=1,"IP","internet.vodafone.ro","0.0.0.0",0,0
Phone = *99#
Password = vodafone
Username = internet.vodafone.ro


You have to enable the card first with: nmcli nm wwan on

---

