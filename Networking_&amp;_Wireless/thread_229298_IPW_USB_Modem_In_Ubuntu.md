---
title: "IPW USB Modem In Ubuntu"
date: 2006-08-04
forum: Networking &amp; Wireless
---

### Post by ozux on 2006-08-04
Hi,
 I have an USB IPWireless modem, It have a driver in Window$, I try to use this in my Ubuntu Box but It can't connect to interbet, When I conect it to my Ubuntu ipwtty driver is load and /dev/tyUSB0 is created.
it's All thinng :

```

dmesg | tail
[4342172.348000] usb 4-2: configuration #1 chosen from 2 choices
[4342172.837000] usbcore: registered new driver usbserial
[4342172.838000] drivers/usb/serial/usb-serial.c: USB Serial support registered for generic
[4342172.838000] usbcore: registered new driver usbserial_generic
[4342172.839000] drivers/usb/serial/usb-serial.c: USB Serial Driver core
[4342172.865000] drivers/usb/serial/usb-serial.c: USB Serial support registered for IPWireless converter
[4342172.866000] ipwtty 4-2:1.0: IPWireless converter converter detected
[4342172.866000] usb 4-2: IPWireless converter converter now attached to ttyUSB0[4342172.867000] usbcore: registered new driver ipwtty
[4342172.867000] drivers/usb/serial/ipw.c: IPWireless tty driver v0.3
```

And in Wvdial :
```

wvdial
--> WvDial: Internet dialer version 1.55
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
--> Sending: ATQ0
--> Re-Sending: ATZ
--> Modem not responding.

```


I think it's connected truely because when I send ATZ with [ echo "ATZ" > /dev/ttyUSB0  ] Tx and Rx LEDs are blanking.

Any body have suggestion,solution?

---

