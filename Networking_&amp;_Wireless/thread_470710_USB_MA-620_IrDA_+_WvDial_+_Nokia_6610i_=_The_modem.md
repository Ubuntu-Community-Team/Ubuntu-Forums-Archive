---
title: "USB MA-620 IrDA + WvDial + Nokia 6610i = The modem device is busy?!"
date: 2007-06-11
forum: Networking &amp; Wireless
---

### Post by srangelov on 2007-06-11
Hi All!
It is now one whole week I am trying to get a mobile internet on my PC :(
The results so far are:
I use these commands to set up the Irda connection and get Nokia connected to the PC:
```

modprobe uhci_hcd
modprobe pl2303
modprobe irda
echo 9600 > /proc/sys/net/irda/max_baud_rate
modprobe ma600-sir
modprobe ircomm-tty
irattach /dev/ttyUSB0 -d ma600 -s
rm -rf /dev/modem
ln -s /dev/ircomm0 /dev/modem

```

Irdadump shows:
```

13:26:31.250437 xid:cmd 9e23329d > ffffffff S=6 s=0 (14)
13:26:31.338315 xid:cmd 9e23329d > ffffffff S=6 s=1 (14)
13:26:31.418316 xid:rsp 9e23329d < 00007d8b S=6 s=1 Nokia 6610i hint=b125 [ PnP Modem Fax Telephony IrCOMM IrOBEX ] (28)

```

Then I run "wvdialconf" and the result is:
```


Scanning your serial ports for a modem.

Modem Port Scan<*1>: Scanning ircomm0 first, /dev/modem is a link to it.
ircomm0<*1>: ATQ0 V1 E1 -- OK
ircomm0<*1>: ATQ0 V1 E1 Z -- OK
ircomm0<*1>: ATQ0 V1 E1 S0=0 -- OK
ircomm0<*1>: ATQ0 V1 E1 S0=0 &C1 -- OK
ircomm0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 -- OK
ircomm0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
ircomm0<*1>: Modem Identifier: ATI -- Nokia
ircomm0<*1>: Speed 19200: AT -- OK
ircomm0<*1>: Speed 38400: AT -- OK
ircomm0<*1>: Speed 57600: AT -- OK
ircomm0<*1>: Speed 115200: AT -- OK
ircomm0<*1>: Speed 230400: AT -- OK
ircomm0<*1>: Speed 460800: AT -- OK
ircomm0<*1>: Max speed is 460800; that should be safe.
ircomm0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
ttyS0<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS0<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS0<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
ttyS1<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS1<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS1<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
Modem Port Scan<*1>: S2   S3   S4   S5   S6   S7   S8   S9
Modem Port Scan<*1>: S10  S11  S12  S13  S14  S15  S16  S17
Modem Port Scan<*1>: S18  S19  S20  S21  S22  S23  S24  S25
Modem Port Scan<*1>: S26  S27  S28  S29  S30  S31  S32  S33
Modem Port Scan<*1>: S34  S35  S36  S37  S38  S39  S40  S41
Modem Port Scan<*1>: S42  S43  S44  S45  S46  S47
WvModem<*1>: Cannot get information for serial port.
Modem Port Scan<*1>: USB0
ircomm1<*1>: ATQ0 V1 E1 -- failed at 9600 and 19200 baud.
ircomm2<*1>: ATQ0 V1 E1 -- failed at 9600 and 19200 baud.
.....
ircomm30<*1>: ATQ0 V1 E1 -- failed at 9600 and 19200 baud.
ircomm31<*1>: ATQ0 V1 E1 -- failed at 9600 and 19200 baud.

Found a modem on /dev/ircomm0, using link /dev/modem in config.
Modem configuration written to /etc/wvdial.conf.
ircomm0<Info>: Speed 9600; init "ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0"


```

My wvdial.conf file is:

```


Modem = /dev/modem
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Stupid Mode = 1
Modem Type = Analog Modem
Phone = *99***1#
New PPPD = yes
ISDN = 0
Username = globul
Password = <Password>
Baud = 9600

```

When I try to connect by the command "wvdial" I get:

```


--> WvDial: Internet dialer version 1.55
--> Initializing modem.
--> Sending: ATZ
--> Sending: ATQ0
--> Re-Sending: ATZ
--> Modem not responding.


```

From this moment when I try again "wvdialconf" the system says:

```


Modem Port Scan<*1>: Scanning ircomm0 first, /dev/modem is a link to it.
ircomm0<*1>: ATQ0 V1 E1 -- failed at 9600 and 19200 baud.
ttyS0<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS0<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS0<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
ttyS1<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS1<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS1<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
Modem Port Scan<*1>: S2   S3   S4   S5   S6   S7   S8   S9
Modem Port Scan<*1>: S10  S11  S12  S13  S14  S15  S16  S17
Modem Port Scan<*1>: S18  S19  S20  S21  S22  S23  S24  S25
Modem Port Scan<*1>: S26  S27  S28  S29  S30  S31  S32  S33
Modem Port Scan<*1>: S34  S35  S36  S37  S38  S39  S40  S41
Modem Port Scan<*1>: S42  S43  S44  S45  S46  S47
WvModem<*1>: Cannot get information for serial port.
Modem Port Scan<*1>: USB0
ircomm1<*1>: ATQ0 V1 E1 -- failed at 9600 and 19200 baud.
ircomm2<*1>: ATQ0 V1 E1 -- failed at 9600 and 19200 baud.
.....
ircomm30<*1>: ATQ0 V1 E1 -- failed at 9600 and 19200 baud.
ircomm31<*1>: ATQ0 V1 E1 -- failed at 9600 and 19200 baud.


Sorry, no modem was detected!  Is it in use by another program?
Did you configure it properly with setserial?


```

Or it says that the modem device is busy?!

Now, I have to restart the PC and do all this again so that "wvdialconf" can find the modem, but it will continue saying that the device is busy.

Any help will be appreciated. Thank you!

P.S. When I first created the wvdial.conf file I even succeedded to connect to internet - I got an IP address! Since then I have no success :(

---

### Post by srangelov on 2007-06-14
After several restarts and same result every time, today I hust started the PC, connected the phone and started the "wvdial" - and it works!!! I got a local IP, remote IP, Primary DNS and secondary DNS.
But although I have Internet connection - I still cannot open any page. I read somewhere in this forum that I should point the browser to use /dev/ircomm0 for Internet connection.
Can any one tell me how to do this?

---

