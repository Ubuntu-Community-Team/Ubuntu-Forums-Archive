---
title: "Solve A Problem , Spawn More"
date: 2006-11-29
forum: Networking &amp; Wireless
---

### Post by AnthonyG on 2006-11-29
I successfully installed the SmartLink drivers , It works with my Agere Systems PCI Soft Modem.

However , Even though I have wvdial.conf's "Carrier Check=no" , I get "No carrier" errors over and over, In a seemingly infinite loop.

---

### Post by AnthonyG on 2006-11-30
I know the modem is being correctly symlinked:

```

symbolic link `/dev/ttySL64' -> `/dev/pts/1' created.
modem `ttyS0' created. TTY is `/dev/pts/1'
Use `/dev/ttySL64' as modem device, Ctrl+C for termination.


```

I know it is being correctly driven, And detected:

```

Scanning your serial ports for a modem.

ttyS0<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 
baud
ttyS0<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 
baud
ttyS0<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
Modem Port Scan<*1>: S1   S2   S3   
WvModem<*1>: Cannot get information for serial port.
ttySL64<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 
baud
ttySL64<*1>: ATQ0 V1 E1 -- OK
ttySL64<*1>: ATQ0 V1 E1 Z -- OK
ttySL64<*1>: ATQ0 V1 E1 S0=0 -- OK
ttySL64<*1>: ATQ0 V1 E1 S0=0 &C1 -- OK
ttySL64<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 -- OK
ttySL64<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
ttySL64<*1>: Modem Identifier: ATI -- SmartLink Soft Modem
ttySL64<*1>: Speed 19200: AT -- OK
ttySL64<*1>: Speed 38400: AT -- OK
ttySL64<*1>: Speed 57600: AT -- OK
ttySL64<*1>: Speed 115200: AT -- OK
ttySL64<*1>: Speed 230400: AT -- OK
ttySL64<*1>: Speed 460800: AT -- OK
ttySL64<*1>: Max speed is 460800; that should be safe.
ttySL64<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK

Found a modem on /dev/ttySL64.
Modem configuration written to /etc/wvdial.conf.
ttySL64<Info>: Speed 460800; init "ATQ0 V1 E1 S0=0 &C1 &D2 
+FCLASS=0"
Editing 
`/etc/wvdial.conf'.

Scanning your serial ports for a modem.


Found a modem on /dev/ttySL64.
Modem configuration written to /etc/wvdial.conf.

```

However, WvDial returns the following; Remember I specified Carrier Check=no, And the error would have infinitely looped if I hadn't specified Dial Attempts=1.

```

--> WvDial: Internet dialer version 1.56
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT[SNIP]
--> Waiting for carrier.
ATDT[SNIP]
NO CARRIER
ERROR
--> No Carrier!  Trying again.
--> Maximum Attempts Exceeded..Aborting!!
--> Disconnecting at Thu Nov 30 09:56:43 2006


```

---

### Post by AnthonyG on 2006-11-30
There must be a solution to this , My mind is so exhausted it can't compute what it is :(. I would be eternally greatful for any assistance with this, I'm so close to getting the modem functional.

---

### Post by AnthonyG on 2006-11-30
This problem seems so trivial , There is likely a simple solution I'm missing here, But no one wants to point it out.

---

### Post by AnthonyG on 2006-12-01
I apologize to bump this but I have attempted absolutely every solution possible, And I still cannot dial.

---

### Post by AnthonyG on 2006-12-01
70 views yet no comments, There must be a solution to such a repetitive error.

---

### Post by AnthonyG on 2006-12-04
Hmph... A day and a half of trying to no avail, I have no where else to turn but here :(.

---

### Post by RJARRRPCGP on 2006-12-04
Never mind. Please delete.

---

