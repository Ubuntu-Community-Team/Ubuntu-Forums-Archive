---
title: "Treo 700wx (sprint)"
date: 2007-06-01
forum: Networking &amp; Wireless
---

### Post by _DjScrew_ on 2007-06-01
ubuntu 7.04 feisty. I am trying to use my treo as a modem. I have seen various guides around for getting different phones working. I have tried using the sprint connection manager via wine, I have my treo drivers installed, but it still doesn't recognize it. I am now trying wvdial. When I do "lsusb" it sees my phone as:
Bus 002  Device 008:  ID 045e:0079  Microsoft Corp.

But, I don't see the device in /dev as ttyusb(x) ... and I'm a linux newb so I apologize if I mixed some things up..

Thanks guys

---

### Post by _DjScrew_ on 2007-06-03
anyone?

---

### Post by _DjScrew_ on 2007-06-04
results of dmesg .. and that's not me disconnecting it.

```
[ 1216.012000] usb 2-1: new full speed USB device using uhci_hcd and address 2
[ 1216.208000] usb 2-1: configuration #1 chosen from 1 choice
[ 1223.628000] usb 2-1: USB disconnect, address 2
[ 1234.416000] usb 2-1: new full speed USB device using uhci_hcd and address 3
[ 1234.600000] usb 2-1: configuration #1 chosen from 1 choice
[ 1241.788000] usb 2-1: USB disconnect, address 3
[ 1243.572000] usb 2-1: new full speed USB device using uhci_hcd and address 4
[ 1243.756000] usb 2-1: configuration #1 chosen from 1 choice
[ 1255.136000] usb 2-1: USB disconnect, address 4
[ 1261.488000] usb 2-1: new full speed USB device using uhci_hcd and address 5
[ 1261.672000] usb 2-1: configuration #1 chosen from 1 choice
[ 1313.732000] usb 2-1: USB disconnect, address 5
[ 2141.724000] usb 2-1: new full speed USB device using uhci_hcd and address 6
[ 2141.908000] usb 2-1: configuration #1 chosen from 1 choice
[ 2155.324000] usb 2-1: USB disconnect, address 6
[ 2156.324000] usb 2-1: new full speed USB device using uhci_hcd and address 7
[ 2156.496000] usb 2-1: configuration #1 chosen from 1 choice
[ 2197.192000] usb 2-1: USB disconnect, address 7
[ 2203.480000] usb 2-1: new full speed USB device using uhci_hcd and address 8
[ 2203.652000] usb 2-1: configuration #1 chosen from 1 choice
[ 2239.204000] usb 2-1: USB disconnect, address 8
[ 2261.988000] usb 2-1: new full speed USB device using uhci_hcd and address 9
[ 2262.156000] usb 2-1: configuration #1 chosen from 1 choice
[ 2309.052000] usb 2-1: USB disconnect, address 9
[ 2315.292000] usb 2-1: new full speed USB device using uhci_hcd and address 10
[ 2315.464000] usb 2-1: configuration #1 chosen from 1 choice
[ 2334.264000] usb 2-1: USB disconnect, address 10
[ 2340.596000] usb 2-1: new full speed USB device using uhci_hcd and address 11
[ 2340.768000] usb 2-1: configuration #1 chosen from 1 choice
[ 2357.824000] usb 2-1: USB disconnect, address 11
[ 2364.128000] usb 2-1: new full speed USB device using uhci_hcd and address 12
[ 2364.300000] usb 2-1: configuration #1 chosen from 1 choice
[ 2419.840000] usb 2-1: USB disconnect, address 12
[ 3789.712000] usb 2-1: new full speed USB device using uhci_hcd and address 13
[ 3789.884000] usb 2-1: configuration #1 chosen from 1 choice
[ 3791.492000] usb 2-1: USB disconnect, address 13
[ 3925.972000] usb 2-1: new full speed USB device using uhci_hcd and address 14
[ 3926.144000] usb 2-1: configuration #1 chosen from 1 choice
[ 3940.724000] usb 2-1: USB disconnect, address 14
[ 3941.472000] usb 2-1: new full speed USB device using uhci_hcd and address 15
[ 4083.072000] usb 2-1: new full speed USB device using uhci_hcd and address 16
[ 4083.596000] usb 2-1: device not accepting address 16, error -71
[ 4085.092000] usb 2-1: new full speed USB device using uhci_hcd and address 18
[ 4085.264000] usb 2-1: configuration #1 chosen from 1 choice
[ 4099.532000] usb 2-1: USB disconnect, address 18
[ 4217.648000] usb 2-1: new full speed USB device using uhci_hcd and address 19
[ 4217.820000] usb 2-1: configuration #1 chosen from 1 choice
[ 4278.588000] usb 2-1: USB disconnect, address 19
[ 4282.852000] usb 2-1: new full speed USB device using uhci_hcd and address 20
[ 4283.020000] usb 2-1: configuration #1 chosen from 1 choice
[ 4288.084000] usb 2-1: USB disconnect, address 20
[ 4288.832000] usb 2-1: new full speed USB device using uhci_hcd and address 21
[ 4289.004000] usb 2-1: configuration #1 chosen from 1 choice
[ 4299.740000] usb 2-1: USB disconnect, address 21
[ 4304.872000] usb 2-1: new full speed USB device using uhci_hcd and address 22
[ 4305.048000] usb 2-1: configuration #1 chosen from 1 choice
[ 4310.672000] usb 2-1: USB disconnect, address 22
[ 4340.512000] usb 2-1: new full speed USB device using uhci_hcd and address 23
[ 4340.680000] usb 2-1: configuration #1 chosen from 1 choice
[ 4348.340000] usb 2-1: USB disconnect, address 23
[ 4349.592000] usb 2-1: new full speed USB device using uhci_hcd and address 24
[ 4349.764000] usb 2-1: configuration #1 chosen from 1 choice
[ 4374.348000] usb 2-1: USB disconnect, address 24
[ 4567.220000] usb 2-1: new full speed USB device using uhci_hcd and address 25
[ 4567.392000] usb 2-1: configuration #1 chosen from 1 choice
[ 4581.336000] usb 2-1: USB disconnect, address 25
[ 4590.168000] usb 2-1: new full speed USB device using uhci_hcd and address 26
[ 4590.340000] usb 2-1: configuration #1 chosen from 1 choice
[ 4603.576000] usb 2-1: USB disconnect, address 26
[ 4608.344000] usb 2-1: new full speed USB device using uhci_hcd and address 27
[ 4608.516000] usb 2-1: configuration #1 chosen from 1 choice
[ 4621.712000] usb 2-1: USB disconnect, address 27
[ 4719.280000] usb 2-1: new full speed USB device using uhci_hcd and address 28
[ 4719.456000] usb 2-1: configuration #1 chosen from 1 choice
[ 4728.400000] usb 2-1: USB disconnect, address 28
[ 4732.100000] usb 2-1: new full speed USB device using uhci_hcd and address 29
[ 4732.272000] usb 2-1: configuration #1 chosen from 1 choice
[ 4733.880000] usb 2-1: USB disconnect, address 29
[ 4739.432000] usb 2-1: new full speed USB device using uhci_hcd and address 30
[ 4739.604000] usb 2-1: configuration #1 chosen from 1 choice
[ 4741.212000] usb 2-1: USB disconnect, address 30
[ 4742.460000] usb 2-1: new full speed USB device using uhci_hcd and address 31
[ 4742.632000] usb 2-1: configuration #1 chosen from 1 choice
[ 4744.236000] usb 2-1: USB disconnect, address 31
[ 4747.952000] usb 2-1: new full speed USB device using uhci_hcd and address 32
[ 4748.120000] usb 2-1: configuration #1 chosen from 1 choice
[ 4749.480000] usb 2-1: USB disconnect, address 32
[ 4780.288000] usb 2-1: new full speed USB device using uhci_hcd and address 33
[ 4780.460000] usb 2-1: configuration #1 chosen from 1 choice
[ 4782.068000] usb 2-1: USB disconnect, address 33
[ 4821.020000] usb 2-1: new full speed USB device using uhci_hcd and address 34
[ 4821.248000] usb 2-1: configuration #1 chosen from 1 choice
[ 4930.620000] usb 2-1: USB disconnect, address 34
[ 4982.016000] usb 2-1: new full speed USB device using uhci_hcd and address 35
[ 4982.188000] usb 2-1: configuration #1 chosen from 1 choice
[ 4998.516000] usb 2-1: USB disconnect, address 35
[ 5004.956000] usb 2-1: new full speed USB device using uhci_hcd and address 36
[ 5005.124000] usb 2-1: configuration #1 chosen from 1 choice
[ 5027.900000] usb 2-1: USB disconnect, address 36
[ 5034.152000] usb 2-1: new full speed USB device using uhci_hcd and address 37
[ 5034.324000] usb 2-1: configuration #1 chosen from 1 choice
[ 5042.988000] usb 2-1: USB disconnect, address 37
[ 5092.804000] usb 2-1: new full speed USB device using uhci_hcd and address 38
[ 5092.972000] usb 2-1: configuration #1 chosen from 1 choice
[ 5102.748000] usb 2-1: USB disconnect, address 38
[ 5109.184000] usb 2-1: new full speed USB device using uhci_hcd and address 39
[ 5109.352000] usb 2-1: configuration #1 chosen from 1 choice
[ 5142.188000] usb 2-1: USB disconnect, address 39
[ 5195.512000] usb 2-1: new full speed USB device using uhci_hcd and address 40
[ 5195.684000] usb 2-1: configuration #1 chosen from 1 choice

```

---

