---
title: "USB modem (CDMA) got disconnected regularly"
date: 2007-07-03
forum: Networking &amp; Wireless
---

### Post by alexeya on 2007-07-03
Hi all,

AnyDATA ADU-E100 CDMA/EVDO modem on Kubuntu Feisty is disconnected from USB repeatedly after few minutes of working. It's reconnected again automatically but pppd looses it and breaks the connection. 

I did nothing special for the modem installation (except for pppd configuration). Just plugged it  in and found it as '/dev/ttyUSB0'. Am I missed something?

Messages on start:

```
Jul  3 13:25:51 don-juan kernel: [   14.835662] drivers/usb/serial/usb-serial.c: USB Serial support registered for GSM modem (1-port)
Jul  3 13:25:51 don-juan kernel: [   14.835715] option 2-1:1.0: GSM modem (1-port) converter detected
Jul  3 13:25:51 don-juan kernel: [   14.836101] usb 2-1: GSM modem (1-port) converter now attached to ttyUSB0
Jul  3 13:25:51 don-juan kernel: [   14.836117] option 2-1:1.1: GSM modem (1-port) converter detected
Jul  3 13:25:51 don-juan kernel: [   14.836406] usb 2-1: GSM modem (1-port) converter now attached to ttyUSB1
Jul  3 13:25:51 don-juan kernel: [   14.836432] usbcore: registered new interface driver option
Jul  3 13:25:51 don-juan kernel: [   14.836437] drivers/usb/serial/option.c: USB Driver for GSM modems: v0.7.1
```

Messages when modem got disconnected:

```
Jul  3 13:34:02 don-juan kernel: [  542.957335] usb 2-1: USB disconnect, address 2
Jul  3 13:34:02 don-juan pppd[4540]: Hangup (SIGHUP)
Jul  3 13:34:02 don-juan pppd[4540]: Modem hangup
Jul  3 13:34:02 don-juan pppd[4540]: Connect time 8.2 minutes.
Jul  3 13:34:02 don-juan pppd[4540]: Sent 12763 bytes, received 827 bytes.
Jul  3 13:34:02 don-juan kernel: [  542.963845] option 2-1:1.0: device disconnected
Jul  3 13:34:02 don-juan kernel: [  542.964114] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
Jul  3 13:34:02 don-juan kernel: [  542.964169] option 2-1:1.1: device disconnected
Jul  3 13:34:02 don-juan pppd[4540]: Connection terminated.
Jul  3 13:34:02 don-juan kernel: [  543.139595] usb 2-1: new full speed USB device using ohci_hcd and address 3
Jul  3 13:34:03 don-juan kernel: [  543.352066] usb 2-1: configuration #1 chosen from 1 choice
Jul  3 13:34:03 don-juan kernel: [  543.355032] option 2-1:1.0: GSM modem (1-port) converter detected
Jul  3 13:34:03 don-juan kernel: [  543.355334] usb 2-1: GSM modem (1-port) converter now attached to ttyUSB1
Jul  3 13:34:03 don-juan kernel: [  543.358135] option 2-1:1.1: GSM modem (1-port) converter detected
Jul  3 13:34:03 don-juan kernel: [  543.358417] usb 2-1: GSM modem (1-port) converter now attached to ttyUSB2
Jul  3 13:34:03 don-juan kernel: [  544.051198] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
```

Thanks!

---

