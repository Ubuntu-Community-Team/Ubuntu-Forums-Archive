---
title: "Modem E220 Huawei  Error"
date: 2011-07-30
forum: New to Ubuntu
---

### Post by xerife on 2011-07-30
Hi,
I´m getting this error:
[COLOR="Red"]The PPP daemon has died: A modem hung up the phone (exit code = 16)[/COLOR]

This is my Console log:
```
martinho@martinho-PC:~$ sudo wvdial
--> WvDial: Internet dialer version 1.61
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT*99#
--> Waiting for carrier.
ATDT*99#
CONNECT
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Sat Jul 30 20:02:24 2011
--> Pid of pppd: 2639
--> Using interface ppp0
--> pppd: &#65533;[7f]
--> pppd: &#65533;[7f]
--> pppd: &#65533;[7f]
--> pppd: &#65533;[7f]
--> pppd: &#65533;[7f]
--> pppd: &#65533;[7f]
--> Disconnecting at Sat Jul 30 20:02:25 2011
--> The PPP daemon has died: A modem hung up the phone (exit code = 16)
--> man pppd explains pppd error codes in more detail.
--> Try again and look into /var/log/messages and the wvdial and pppd man pages for more information.
--> Auto Reconnect will be attempted in 5 seconds
```

This is my wvdial:
```
[Dialer kanguru]
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = Analog Modem
ISDN = 0
Username = myconnection
Password = k771u3
Init1 = ATZ
Modem = /dev/ttyUSB0
Baud = 460800
Phone = *99#
Stupid Mode = 1
Dial Command = ATDT
Auto DNS = on
```

This is my syslog:
```

Jul 31 00:23:32 martinho-PC kernel: [ 5078.003250] sr 30:0:0:0: Attached scsi generic sg3 type 5
Jul 31 00:23:33 martinho-PC modem-manager[990]: <info>  (ttyUSB0) closing serial port...
Jul 31 00:23:33 martinho-PC modem-manager[990]: <info>  (ttyUSB0) serial port closed
Jul 31 00:23:34 martinho-PC modem-manager[990]: <info>  (ttyUSB1) opening serial port...
Jul 31 00:23:35 martinho-PC modem-manager[990]: <info>  (ttyUSB1) closing serial port...
Jul 31 00:23:35 martinho-PC modem-manager[990]: <info>  (ttyUSB1) serial port closed
Jul 31 00:23:35 martinho-PC modem-manager[990]: <info>  (Huawei): GSM modem /sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2 claimed port ttyUSB1
Jul 31 00:23:35 martinho-PC NetworkManager[982]: <warn> (ttyUSB0): failed to look up interface index
Jul 31 00:23:35 martinho-PC NetworkManager[982]: <info> (ttyUSB0): new GSM device (driver: 'option1' ifindex: -1)
Jul 31 00:23:35 martinho-PC NetworkManager[982]: <info> (ttyUSB0): exported as /org/freedesktop/NetworkManager/Devices/7
Jul 31 00:23:35 martinho-PC NetworkManager[982]: <info> (ttyUSB0): now managed
Jul 31 00:23:35 martinho-PC NetworkManager[982]: <info> (ttyUSB0): device state change: 1 -> 2 (reason 2)
Jul 31 00:23:35 martinho-PC NetworkManager[982]: <info> (ttyUSB0): deactivating device (reason: 2).
Jul 31 00:23:35 martinho-PC NetworkManager[982]: <info> (ttyUSB0): device state change: 2 -> 3 (reason 0)
Jul 31 00:25:18 martinho-PC modem-manager[990]: <info>  (tty/ttyUSB1): released by modem /sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2
Jul 31 00:25:18 martinho-PC modem-manager[990]: <info>  (tty/ttyUSB0): released by modem /sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2
Jul 31 00:25:18 martinho-PC NetworkManager[982]: <info> (ttyUSB0): now unmanaged
Jul 31 00:25:18 martinho-PC NetworkManager[982]: <info> (ttyUSB0): device state change: 3 -> 1 (reason 36)
Jul 31 00:25:18 martinho-PC NetworkManager[982]: <info> (ttyUSB0): cleaning up...
Jul 31 00:25:18 martinho-PC NetworkManager[982]: <info> (ttyUSB0): taking down device.
Jul 31 00:25:18 martinho-PC kernel: [ 5183.308403] usb 2-1.2: USB disconnect, address 18
Jul 31 00:25:18 martinho-PC kernel: [ 5183.308507] option: option_instat_callback: error -108
Jul 31 00:25:18 martinho-PC kernel: [ 5183.308650] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
Jul 31 00:25:18 martinho-PC kernel: [ 5183.308689] option 2-1.2:1.0: device disconnected
Jul 31 00:25:18 martinho-PC kernel: [ 5183.308938] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
Jul 31 00:25:18 martinho-PC kernel: [ 5183.308976] option 2-1.2:1.1: device disconnected
Jul 31 00:25:18 martinho-PC NetworkManager[982]: <info> Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Jul 31 00:25:18 martinho-PC NetworkManager[982]: <info> Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Jul 31 00:25:31 martinho-PC kernel: [ 5196.335476] usb 2-1.2: new full speed USB device using ehci_hcd and address 19
Jul 31 00:25:31 martinho-PC kernel: [ 5196.458394] scsi31 : usb-storage 2-1.2:1.0
Jul 31 00:25:31 martinho-PC kernel: [ 5196.608656] usb 2-1.2: USB disconnect, address 19
Jul 31 00:25:32 martinho-PC kernel: [ 5197.864204] usb 2-1.2: new full speed USB device using ehci_hcd and address 20
Jul 31 00:25:32 martinho-PC kernel: [ 5197.976726] option 2-1.2:1.0: GSM modem (1-port) converter detected
Jul 31 00:25:32 martinho-PC kernel: [ 5197.976940] usb 2-1.2: GSM modem (1-port) converter now attached to ttyUSB0
Jul 31 00:25:32 martinho-PC kernel: [ 5197.977653] option 2-1.2:1.1: GSM modem (1-port) converter detected
Jul 31 00:25:32 martinho-PC kernel: [ 5197.977828] usb 2-1.2: GSM modem (1-port) converter now attached to ttyUSB1
Jul 31 00:25:32 martinho-PC kernel: [ 5197.978554] scsi34 : usb-storage 2-1.2:1.2
Jul 31 00:25:32 martinho-PC modem-manager[990]: <info>  (ttyUSB0) opening serial port...
Jul 31 00:25:33 martinho-PC modem-manager[990]: <info>  (ttyUSB0) closing serial port...
Jul 31 00:25:33 martinho-PC modem-manager[990]: <info>  (ttyUSB0) serial port closed
Jul 31 00:25:33 martinho-PC modem-manager[990]: <info>  (ttyUSB0) opening serial port...
Jul 31 00:25:33 martinho-PC modem-manager[990]: <info>  (Huawei): GSM modem /sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2 claimed port ttyUSB0
Jul 31 00:25:33 martinho-PC kernel: [ 5198.975519] scsi 34:0:0:0: CD-ROM            HUAWEI   Mass Storage     2.31 PQ: 0 ANSI: 2
Jul 31 00:25:33 martinho-PC kernel: [ 5198.982498] sr1: scsi-1 drive
Jul 31 00:25:33 martinho-PC kernel: [ 5198.982921] sr 34:0:0:0: Attached scsi CD-ROM sr1
Jul 31 00:25:33 martinho-PC kernel: [ 5198.983812] sr 34:0:0:0: Attached scsi generic sg3 type 5
Jul 31 00:25:34 martinho-PC modem-manager[990]: <info>  (ttyUSB0) closing serial port...
Jul 31 00:25:34 martinho-PC modem-manager[990]: <info>  (ttyUSB0) serial port closed
Jul 31 00:25:35 martinho-PC modem-manager[990]: <info>  (ttyUSB1) opening serial port...
Jul 31 00:25:39 martinho-PC modem-manager[990]: <info>  (ttyUSB1) closing serial port...
Jul 31 00:25:39 martinho-PC modem-manager[990]: <info>  (ttyUSB1) serial port closed
Jul 31 00:25:39 martinho-PC modem-manager[990]: <info>  (Huawei): GSM modem /sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2 claimed port ttyUSB1
Jul 31 00:25:39 martinho-PC NetworkManager[982]: <warn> (ttyUSB0): failed to look up interface index
Jul 31 00:25:39 martinho-PC NetworkManager[982]: <info> (ttyUSB0): new GSM device (driver: 'option1' ifindex: -1)
Jul 31 00:25:39 martinho-PC NetworkManager[982]: <info> (ttyUSB0): exported as /org/freedesktop/NetworkManager/Devices/8
Jul 31 00:25:39 martinho-PC NetworkManager[982]: <info> (ttyUSB0): now managed
Jul 31 00:25:39 martinho-PC NetworkManager[982]: <info> (ttyUSB0): device state change: 1 -> 2 (reason 2)
Jul 31 00:25:39 martinho-PC NetworkManager[982]: <info> (ttyUSB0): deactivating device (reason: 2).
Jul 31 00:25:39 martinho-PC NetworkManager[982]: <info> (ttyUSB0): device state change: 2 -> 3 (reason 0)

```

If anyone  could please point me in right direction, i´d be very apreciated.
Please note: I have no linux experience
Thanks

---

### Post by jtarin on 2011-07-30
I'm assuming your using a wireless USB modem? Unfortunately these have a bad habit of disconnecting intermittently......it's not Ubuntu only, as it happens to me in Win too.Are you saying you cannot connect at all?

Have you done as suggested?
> The PPP daemon has died: A modem hung up the phone (exit code = 16)
--> _man pppd explains pppd error codes in more detail._
--> Try again and look into _/var/log/messages and the wvdial and pppd man pages for more information._

---

### Post by jtarin on 2011-07-30
**Exit code 16**:The link was terminated because the peer is not responding to echo requests.

---

### Post by gandaran on 2011-07-31
> **xerife said:**
> Hi,
I´m getting this error:
[COLOR="Red"]The PPP daemon has died: A modem hung up the phone (exit code = 16)[/COLOR]

This is my Console log:
```
martinho@martinho-PC:~$ sudo wvdial
--> WvDial: Internet dialer version 1.61
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT*99#
--> Waiting for carrier.
ATDT*99#
CONNECT
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Sat Jul 30 20:02:24 2011
--> Pid of pppd: 2639
--> Using interface ppp0
--> pppd: &#65533;[7f]
--> pppd: &#65533;[7f]
--> pppd: &#65533;[7f]
--> pppd: &#65533;[7f]
--> pppd: &#65533;[7f]
--> pppd: &#65533;[7f]
--> Disconnecting at Sat Jul 30 20:02:25 2011
--> The PPP daemon has died: A modem hung up the phone (exit code = 16)
--> man pppd explains pppd error codes in more detail.
--> Try again and look into /var/log/messages and the wvdial and pppd man pages for more information.
--> Auto Reconnect will be attempted in 5 seconds
```

This is my wvdial:
```
[Dialer kanguru]
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = Analog Modem
ISDN = 0
Username = myconnection
Password = k771u3
Init1 = ATZ
Modem = /dev/ttyUSB0
Baud = 460800
Phone = *99#
Stupid Mode = 1
Dial Command = ATDT
Auto DNS = on
```

This is my syslog:
```

Jul 31 00:23:32 martinho-PC kernel: [ 5078.003250] sr 30:0:0:0: Attached scsi generic sg3 type 5
Jul 31 00:23:33 martinho-PC modem-manager[990]: <info>  (ttyUSB0) closing serial port...
Jul 31 00:23:33 martinho-PC modem-manager[990]: <info>  (ttyUSB0) serial port closed
Jul 31 00:23:34 martinho-PC modem-manager[990]: <info>  (ttyUSB1) opening serial port...
Jul 31 00:23:35 martinho-PC modem-manager[990]: <info>  (ttyUSB1) closing serial port...
Jul 31 00:23:35 martinho-PC modem-manager[990]: <info>  (ttyUSB1) serial port closed
Jul 31 00:23:35 martinho-PC modem-manager[990]: <info>  (Huawei): GSM modem /sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2 claimed port ttyUSB1
Jul 31 00:23:35 martinho-PC NetworkManager[982]: <warn> (ttyUSB0): failed to look up interface index
Jul 31 00:23:35 martinho-PC NetworkManager[982]: <info> (ttyUSB0): new GSM device (driver: 'option1' ifindex: -1)
Jul 31 00:23:35 martinho-PC NetworkManager[982]: <info> (ttyUSB0): exported as /org/freedesktop/NetworkManager/Devices/7
Jul 31 00:23:35 martinho-PC NetworkManager[982]: <info> (ttyUSB0): now managed
Jul 31 00:23:35 martinho-PC NetworkManager[982]: <info> (ttyUSB0): device state change: 1 -> 2 (reason 2)
Jul 31 00:23:35 martinho-PC NetworkManager[982]: <info> (ttyUSB0): deactivating device (reason: 2).
Jul 31 00:23:35 martinho-PC NetworkManager[982]: <info> (ttyUSB0): device state change: 2 -> 3 (reason 0)
Jul 31 00:25:18 martinho-PC modem-manager[990]: <info>  (tty/ttyUSB1): released by modem /sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2
Jul 31 00:25:18 martinho-PC modem-manager[990]: <info>  (tty/ttyUSB0): released by modem /sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2
Jul 31 00:25:18 martinho-PC NetworkManager[982]: <info> (ttyUSB0): now unmanaged
Jul 31 00:25:18 martinho-PC NetworkManager[982]: <info> (ttyUSB0): device state change: 3 -> 1 (reason 36)
Jul 31 00:25:18 martinho-PC NetworkManager[982]: <info> (ttyUSB0): cleaning up...
Jul 31 00:25:18 martinho-PC NetworkManager[982]: <info> (ttyUSB0): taking down device.
Jul 31 00:25:18 martinho-PC kernel: [ 5183.308403] usb 2-1.2: USB disconnect, address 18
Jul 31 00:25:18 martinho-PC kernel: [ 5183.308507] option: option_instat_callback: error -108
Jul 31 00:25:18 martinho-PC kernel: [ 5183.308650] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
Jul 31 00:25:18 martinho-PC kernel: [ 5183.308689] option 2-1.2:1.0: device disconnected
Jul 31 00:25:18 martinho-PC kernel: [ 5183.308938] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
Jul 31 00:25:18 martinho-PC kernel: [ 5183.308976] option 2-1.2:1.1: device disconnected
Jul 31 00:25:18 martinho-PC NetworkManager[982]: <info> Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Jul 31 00:25:18 martinho-PC NetworkManager[982]: <info> Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Jul 31 00:25:31 martinho-PC kernel: [ 5196.335476] usb 2-1.2: new full speed USB device using ehci_hcd and address 19
Jul 31 00:25:31 martinho-PC kernel: [ 5196.458394] scsi31 : usb-storage 2-1.2:1.0
Jul 31 00:25:31 martinho-PC kernel: [ 5196.608656] usb 2-1.2: USB disconnect, address 19
Jul 31 00:25:32 martinho-PC kernel: [ 5197.864204] usb 2-1.2: new full speed USB device using ehci_hcd and address 20
Jul 31 00:25:32 martinho-PC kernel: [ 5197.976726] option 2-1.2:1.0: GSM modem (1-port) converter detected
Jul 31 00:25:32 martinho-PC kernel: [ 5197.976940] usb 2-1.2: GSM modem (1-port) converter now attached to ttyUSB0
Jul 31 00:25:32 martinho-PC kernel: [ 5197.977653] option 2-1.2:1.1: GSM modem (1-port) converter detected
Jul 31 00:25:32 martinho-PC kernel: [ 5197.977828] usb 2-1.2: GSM modem (1-port) converter now attached to ttyUSB1
Jul 31 00:25:32 martinho-PC kernel: [ 5197.978554] scsi34 : usb-storage 2-1.2:1.2
Jul 31 00:25:32 martinho-PC modem-manager[990]: <info>  (ttyUSB0) opening serial port...
Jul 31 00:25:33 martinho-PC modem-manager[990]: <info>  (ttyUSB0) closing serial port...
Jul 31 00:25:33 martinho-PC modem-manager[990]: <info>  (ttyUSB0) serial port closed
Jul 31 00:25:33 martinho-PC modem-manager[990]: <info>  (ttyUSB0) opening serial port...
Jul 31 00:25:33 martinho-PC modem-manager[990]: <info>  (Huawei): GSM modem /sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2 claimed port ttyUSB0
Jul 31 00:25:33 martinho-PC kernel: [ 5198.975519] scsi 34:0:0:0: CD-ROM            HUAWEI   Mass Storage     2.31 PQ: 0 ANSI: 2
Jul 31 00:25:33 martinho-PC kernel: [ 5198.982498] sr1: scsi-1 drive
Jul 31 00:25:33 martinho-PC kernel: [ 5198.982921] sr 34:0:0:0: Attached scsi CD-ROM sr1
Jul 31 00:25:33 martinho-PC kernel: [ 5198.983812] sr 34:0:0:0: Attached scsi generic sg3 type 5
Jul 31 00:25:34 martinho-PC modem-manager[990]: <info>  (ttyUSB0) closing serial port...
Jul 31 00:25:34 martinho-PC modem-manager[990]: <info>  (ttyUSB0) serial port closed
Jul 31 00:25:35 martinho-PC modem-manager[990]: <info>  (ttyUSB1) opening serial port...
Jul 31 00:25:39 martinho-PC modem-manager[990]: <info>  (ttyUSB1) closing serial port...
Jul 31 00:25:39 martinho-PC modem-manager[990]: <info>  (ttyUSB1) serial port closed
Jul 31 00:25:39 martinho-PC modem-manager[990]: <info>  (Huawei): GSM modem /sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2 claimed port ttyUSB1
Jul 31 00:25:39 martinho-PC NetworkManager[982]: <warn> (ttyUSB0): failed to look up interface index
Jul 31 00:25:39 martinho-PC NetworkManager[982]: <info> (ttyUSB0): new GSM device (driver: 'option1' ifindex: -1)
Jul 31 00:25:39 martinho-PC NetworkManager[982]: <info> (ttyUSB0): exported as /org/freedesktop/NetworkManager/Devices/8
Jul 31 00:25:39 martinho-PC NetworkManager[982]: <info> (ttyUSB0): now managed
Jul 31 00:25:39 martinho-PC NetworkManager[982]: <info> (ttyUSB0): device state change: 1 -> 2 (reason 2)
Jul 31 00:25:39 martinho-PC NetworkManager[982]: <info> (ttyUSB0): deactivating device (reason: 2).
Jul 31 00:25:39 martinho-PC NetworkManager[982]: <info> (ttyUSB0): device state change: 2 -> 3 (reason 0)

```

If anyone  could please point me in right direction, i´d be very apreciated.
Please note: I have no linux experience
Thanks
any reason why you are using wvdial? the Huawei E220 is one of the best supported modems and works very well with network manager and very easy to set up the kanguru internet provider on network manager, no need to go the wvdial way.

---

### Post by xerife on 2011-07-31
hi,
Thanks a lot for your reply.
I´m using wvdial because i tried with NetworkManager and couldn´t configure it.
I saw other tutorials both with NetworkManager and wvdial configuration.
Example: if i try with NetworkManager it prompts an error message "GSM disconnected".

---

### Post by gandaran on 2011-07-31
> **xerife said:**
> hi,
Thanks a lot for your reply.
I´m using wvdial because i tried with NetworkManager and couldn´t configure it.
I saw other tutorials both with NetworkManager and wvdial configuration.
Example: if i try with NetworkManager it prompts an error message "GSM disconnected".
which ubuntu release do you have? I think your problem is that you have the wrong APN selected, for Kanguru it's best to just use a blank APN, it will work with all Kanguru internet plans mobile, temporary or fixed internet.
try to follow my network manager setup guide here
[http://gandaran.blogspot.com/2010/07/internet-kanguru-no-ubuntu-1004.html](http://gandaran.blogspot.com/2010/07/internet-kanguru-no-ubuntu-1004.html)

---

### Post by jtarin on 2011-07-31
> **xerife said:**
> hi,
Example: if i try with NetworkManager it prompts an error message "GSM disconnected".This is basically the same error as wvdial...
"Exit code 16:The link was terminated because the peer is not responding to echo requests".
Does your modem work in windows?

---

### Post by xerife on 2011-08-01
> **gandaran said:**
> which ubuntu release do you have? I think your problem is that you have the wrong APN selected, for Kanguru it's best to just use a blank APN, it will work with all Kanguru internet plans mobile, temporary or fixed internet.
try to follow my network manager setup guide here
[http://gandaran.blogspot.com/2010/07/internet-kanguru-no-ubuntu-1004.html](http://gandaran.blogspot.com/2010/07/internet-kanguru-no-ubuntu-1004.html)

Ola Gandaran 
Já tinha visto o teu link anteriormente.
Não funciona no meu Ubuntu.
Agora instalei o Kubuntu para experimentar e testar.

---

### Post by gandaran on 2011-08-01
> **xerife said:**
> Ola Gandaran 
Já tinha visto o teu link anteriormente.
Não funciona no meu Ubuntu.
Agora instalei o Kubuntu para experimentar e testar.
ola
qual e a versão do ubuntu? o ubuntu 11.04 e o único que tem o APN dos tarifários kanguru correctos, basta simplesmente correr o ajudante do network manager, escolher o pais e operadora e tarifário depois fechar e meter a pen no PC, e só! deve ligar automaticamente se marcastes a opção "ligar automaticamente"
se não funciona assim eu não sei mais qual será o problema.
quanto ao kubuntu penso que não deve funcionar a partida por falta do pacote usb-modeswitch, se eu não estou enganado terás que o instalar primeiro.
bem espero que resolvas o problema, boa sorte.

---

