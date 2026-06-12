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
--> No Carrier!  Trying again.
--> Sending: ATDT#777
--> Waiting for carrier.
^CCaught signal 2:  Attempting to exit gracefully...
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

### Post by redbook4574 on 2009-11-09
Sorry but unless it's been fixed there are real problems with 9.10 and mobile broadband, thats why I have dumped ubuntu on my laptop for suse 11.2, although I still have 9.10 on my desktop.

---

### Post by biker_boy on 2009-11-28
It is very simple in Karmic. Just plug in the device. Go to network in the top right panel, You can see unknown device in the drop down menu in menu under mobile broadband.  just configure it by following the wizard. Choose the country, then choose the Service provider, ie., Idea Cellular then let the plan be Default. then Finish it... Simple... when ever you want to connect again. just plug in the device. wait for 10 seconds approx, go the Network in top right panel, there under the mobile broadband option there will be Idea cellular default, just click on it. after a while you can see the message connection establiched.. that is all...  actually i am a Newbee in Linux.. i beg your pardon for my language..

---

