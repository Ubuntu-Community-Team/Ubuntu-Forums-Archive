---
title: "GPRS Connection problems"
date: 2007-02-17
forum: Networking &amp; Wireless
---

### Post by dodgy_devil on 2007-02-17
I am trying to connect to the internet from my Sony Ericsson W800i using a data cable. I was able to connect through wvdial using the following wvdial config file
/**
[Dialer Defaults]
Phone = *99***1#
#Phone = *99#
Username = anything
Password = anything
Stupid Mode = 1
Dial Command = ATDT

[Dialer pin]
Init1 = AT+CPIN=1234

[Dialer gprs] Modem = /dev/ttyACM0
Baud = 115200
Init2 = ATZ
Init3 = ATE0V1&D2&C1S0=0+IFC=2,2
ISDN = 0
Modem
Type = Analog Modem
*/

then, connect with


"sudo wvdial gprs"

I can see on the phones display that it connects as well as in the terminal but when i browse the internet i get no response. Is there any way i can see what is my connection status or it might even be that the OS are still using my ethernet connection settings althought it is unplugged. OS = Ubuntu edgy

Would really appreciate help!
Thanks

---

### Post by srangelov on 2007-07-03
Hi, dodgy_devil!
Did you find a way to handle this? I f yes, please post it here. There are a lot o people here in the forum with the same problem, including me :)

---

### Post by aquavitae on 2007-07-03
For your phone you don't need to use wvdial.  Follow the guide at [http://ubuntuforums.org/showthread.php?t=487838]("http://ubuntuforums.org/showthread.php?t=487838").

---

