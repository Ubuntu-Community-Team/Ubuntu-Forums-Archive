---
title: "Next Step in Modem Installation"
date: 2007-02-19
forum: Networking &amp; Wireless
---

### Post by thorosius on 2007-02-19
I have successfully installed my modem driver for Intel 537 under ubuntu 6.10 but there is some problem dialing out can any one please help? I hear a click sound when dialing out this means wvdial does interact with my modem (right?) but then no dial tone error shows up. Related command outputs are given below:

************************************************** 
fahd@fahd-desktop:~/home/philippe/intel-537EP_secure-2.60.80.1$ sudo wvdialconf
Editing `/etc/wvdial.conf'.

Scanning your serial ports for a modem.

ttyS0<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS0<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS0<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
Modem Port Scan<*1>: S1 S2 S3 


Sorry, no modem was detected! Is it in use by another program?
Did you configure it properly with setserial?

Please read the FAQ at [http://open.nit.ca/wiki/?WvDial](http://open.nit.ca/wiki/?WvDial)

If you still have problems, send mail to <wvdial-list@lists.nit.ca>.
************************************************** 
WVDIAL.CONF CONTENTS
************************************************** 
[Dialer Defaults]
Modem = /dev/modem
Baud = 57600
SetVolume = 3
Dial Command = ATDT
Init1 = ATZ
Init2 = AT+GCI=84
Init3 = ATM1L3
Carrier Check = no
Phone = 13198765
Username = cstb
Password = cstb

************************************************** 
WVDIAL OUTPUT
************************************************** 
fahd@fahd-desktop:~/home/philippe/intel-537EP_secure-2.60.80.1$ sudo wvdial
--> WvDial: Internet dialer version 1.56
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: AT+GCI=84
AT+GCI=84
OK
--> Sending: ATM1L3
ATM1L3
OK
--> Modem initialized.
--> Sending: ATDT13198765
--> Waiting for carrier.
ATDT13198765
NO DIALTONE
--> No dial tone.
--> Disconnecting at Sat Feb 3 15:14:26 2007


Please please can anyone help?

---

