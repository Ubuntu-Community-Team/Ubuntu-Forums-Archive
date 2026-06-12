---
title: "RFCOMM connection but no commands possible ?"
date: 2015-10-14
forum: Networking &amp; Wireless
---

### Post by tmt4 on 2015-10-14
Hello,

I am trying to make a connection between my Samsung Galaxy S4 and my Linux Ubuntu 14.04 system via bluetooth dongle. 
I want to access the hands-free profile to make a laptop initialized call from my phone to another phone without special programs (it's about the know how about the profile, not the actual call). The hands-free devices in cars are able to do this. I want to reproduce this. 

I connected my phone via rfcomm, but while connected, no possible command seems to work. I tested some AT commands in different forms.

> 
Service Name: Handsfree Gateway
Service RecHandle: 0x1000d
Service Class ID List:
  "Handsfree Audio Gateway" (0x111f)
  "Generic Audio" (0x1203)
Protocol Descriptor List:
  "L2CAP" (0x0100)
  "RFCOMM" (0x0003)
    Channel: 3
Profile Descriptor List:
  "Handsfree" (0x111e)
    Version: 0x0106


> 
minicom:

A - Serial Device : /dev/rfcomm0

> 
$ sudo rfcomm connect /dev/rfcomm0 C8:14:79:B4:27:67 3
Connected /dev/rfcomm0 to C8:14:79:B4:27:67 on channel 3
Press CTRL-C for hangup
AT
<AT<>cr>
AT=?
AT?
Disconnected
$ AT
AT: command not found
$ <AT<>cr>
bash: syntax error near unexpected token `newline'
$ AT=?
$ AT?
AT?: command not found


The AT commands were performed automatically after the disconnect.

 I followed the bluetooth hands-free pdf to this step but now AT commands should be possible.

I hope you can help me.

---

