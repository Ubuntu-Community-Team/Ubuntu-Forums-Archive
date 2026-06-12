---
title: "Configuring HUAWEI EG162G modem in Ubuntu 9.10..."
date: 2009-11-09
forum: New to Ubuntu
---

### Post by vikaskumargdra on 2009-11-09
Hi!
I hv Huawei EG162G modem(Idea Net Setter).I configured it,but when i run wvdial it shows the following error:-

vikas@R0x0r-Desktop:~$ sudo wvdial
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
OK
--> Sending: ATE0V1
ATE0V1
OK
--> Modem initialized.
--> Sending: ATDT#777
--> Waiting for carrier.
NO CARRIER
--> No Carrier! Trying again.
--> Sending: ATDT#777
--> Waiting for carrier.
^CCaught signal 2: Attempting to exit gracefully...
--> Disconnecting at Tue Nov 10 02:09:57 2009



My wvdialconf file is:-

[Dialer Defaults]
Init1 = ATZ
Init2 = ATE0V1
Stupid Mode = Yes
Modem Type = Analog Modem
Baud = 115200
New PPPD = yes
Modem = /dev/ttyUSB0
ISDN = 0
Phone = "#777"
Password = idea
Username = idea Init1 changed to ATZ and 'Stupid mode = Yes' added to skip 'prompt at login'

Can anybody tell me what is wrong & Also please share correct wvdialconf configuration.
Thanks

---

### Post by Vishnu V on 2009-11-09
check this link here is the correct wvdial [http://technolark.blogspot.com/2009/05/idea-netsetter-on-ubuntu-jaunty.html]("http://technolark.blogspot.com/2009/05/idea-netsetter-on-ubuntu-jaunty.html")

---

