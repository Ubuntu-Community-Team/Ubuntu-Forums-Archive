---
title: "tata photon whiz"
date: 2009-09-17
forum: New to Ubuntu
---

### Post by ankit_kohli on 2009-09-17
i am unable to connect net with tata photon whiz 
in ubuntu 8.04 i took help of a friend (ubuntu user)
he tried wvdial and mode probe but no result
help me please

---

### Post by LewRockwell on 2009-09-17
friend should give you a fresh copy of Ubuntu 9.04 Jaunty Jackalope

.

---

### Post by ankit_kohli on 2009-09-17
will it help

---

### Post by LewRockwell on 2009-09-17
tata even references Ubuntu...

[http://www.tataindicom.com/print-t-personal-internet-photon-whiz.aspx](http://www.tataindicom.com/print-t-personal-internet-photon-whiz.aspx)

.

---

### Post by ankit_kohli on 2009-09-17
how to connect in ubuntu 8.04

---

### Post by LewRockwell on 2009-09-17
[http://www.tataindicom.com/download/dialers/dialup-internet-on-linux.pdf](http://www.tataindicom.com/download/dialers/dialup-internet-on-linux.pdf)

.

---

### Post by ankit_kohli on 2009-09-17
i tried the procedure but it says

ankit@SaNg-FrOiD:~$ sudo wvdialconf /etc/wvdial.conf
Editing `/etc/wvdial.conf'.

Scanning your serial ports for a modem.

Modem Port Scan<*1>: S0   S1   S2   S3   


Sorry, no modem was detected!  Is it in use by another program?
Did you configure it properly with setserial?

Please read the FAQ at [http://open.nit.ca/wiki/?WvDial](http://open.nit.ca/wiki/?WvDial)

If you still have problems, send mail to <wvdial-list@lists.nit.ca>.

---

### Post by ankit_kohli on 2009-09-17
device is ec121

---

### Post by ankit_kohli on 2009-09-18
guus please help me out compaq v6000 6409tu series tata photon whiz ec121 ubuntu 8.04

---

### Post by ankit_kohli on 2009-09-21
can anyone help

---

### Post by ujjwalkanth on 2009-10-11
Same Problem with ubuntu 9.04

---

### Post by mulvila on 2009-11-13
I got mine working on Ubuntu 9.10 fine with the following instructions:

[http://blog.harshas.net/2009/10/using-tata-indicom-photon-whiz-huawei_19.html](http://blog.harshas.net/2009/10/using-tata-indicom-photon-whiz-huawei_19.html)

Had to replace the device with Modem = /dev/ttyUSB0

If wvdialconf does not recognise the usb modem, then perhaps the only way is upregre to new version of ubuntu as older kernel's might not recognise this new device.

Write dmesg and see what kind of info is there after you instert the USB modem.

---

### Post by dr_smit on 2009-12-09
My ubuntu Netbook Remix 9.10 on Acer Aspire one ZGS with TATA Phton Whiz
 [COLOR="Red"]on sudo wvdial[/COLOR]

WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Sending: AT+CRM=1
AT+CRM=1
OK
--> Modem initialized.
--> Sending: ATDT#777
--> Waiting for carrier.
ATDT#777
CONNECT 153600
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Thu Dec 10 06:37:34 2009
--> Pid of pppd: 3714
--> Using interface ppp0
--> pppd: `&#65533;_ [10]&#65533;_ [08]&#65533;_ 
--> pppd: `&#65533;_ [10]&#65533;_ [08]&#65533;_ 
--> pppd: `&#65533;_ [10]&#65533;_ [08]&#65533;_ 
--> pppd: `&#65533;_ [10]&#65533;_ [08]&#65533;_ 
--> pppd: `&#65533;_ [10]&#65533;_ [08]&#65533;_ 
--> local  IP address 121.245.181.167
--> pppd: `&#65533;_ [10]&#65533;_ [08]&#65533;_ 
--> remote IP address 172.23.119.14
--> pppd: `&#65533;_ [10]&#65533;_ [08]&#65533;_ 
--> primary   DNS address 202.54.29.5
--> pppd: `&#65533;_ [10]&#65533;_ [08]&#65533;_ 
--> secondary DNS address 202.54.10.2
--> pppd: `&#65533;_ [10]&#65533;_ [08]&#65533;_ 
 And the cursor keeps blinking here

the /etc/wvdial.conf has

[Dialer Defaults]
Modem = /dev/ttyUSB0
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Init3 = AT+CRM=1
Stupid Mode = 1
Modem Type = Analog Modem
Phone = #777
New PPPD = yes
ISDN = 0
Username = internet
Password = internet
Baud = 9600

Is the fault in the BAUD :confused: should that be some higher value,
I am planning to travel, so an early help will be appreciated

---

### Post by dr_smit on 2009-12-09
[http://www.tataindicom.com/download/dialers/dialup-internet-on-linux.pdf](http://www.tataindicom.com/download/dialers/dialup-internet-on-linux.pdf)

The step 10 helped me in getting connected, posted via TATA Photon Whiz to help some one else like me..:popcorn:

10. If not able to browse run this command in the terminal once and the system is ready for
browsing. cp /etc/ppp/resolv.conf /etc/ this copy the file, it will ask for conformation to
overwrite say Y to overwrite.

---

### Post by dr_smit on 2009-12-09
Warning: the network manager shows the TataIndicom connection but clicking it does not connect, so try browsing in a browser to know whether connection is alve.. I am able to browse without network manager showing any connection to TataIndicom!

---

