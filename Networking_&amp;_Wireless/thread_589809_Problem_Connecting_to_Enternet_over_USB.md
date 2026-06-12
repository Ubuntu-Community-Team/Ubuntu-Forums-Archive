---
title: "Problem Connecting to Enternet over USB"
date: 2007-10-24
forum: Networking &amp; Wireless
---

### Post by applegrew on 2007-10-24
I want to connect to my Huawei SmartAX MT882 ADSL router via the USB because I have already connect the other (only) ethernet port to my other computer. According to the router's manual the cdc_ether and usbnet modules must be loaded. Since they automatically get loaded hence I think it should work. Below I am posting some informations that could be hepfull in spoting the problem. I have bolded the lines that seems to be realted to this connection.

**uname -a**
Linux applegrew 2.6.20-16-generic #2 SMP Sun Sep 23 19:50:39 UTC 2007 i686 GNU/Linux

**ifconfig -a**
eth0      Link encap:Ethernet  HWaddr 00:16:D4:0B:61:AE
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:125398 errors:0 dropped:0 overruns:0 frame:0
          TX packets:107449 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:156048097 (148.8 MiB)  TX bytes:14121693 (13.4 MiB)
[B]
eth1      Link encap:Ethernet  HWaddr 00:0F:A3:55:9F:7C
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)[/B]

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:98 errors:0 dropped:0 overruns:0 frame:0
          TX packets:98 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:8500 (8.3 KiB)  TX bytes:8500 (8.3 KiB)

**lsusb**
Bus 005 Device 001: ID 0000:0000
Bus 003 Device 002: ID 046d:c016 Logitech, Inc. M-UV69a Optical Wheel Mouse
Bus 003 Device 001: ID 0000:0000
**Bus 002 Device 005: ID 1110:5c01 Analog Devices Canada, Ltd (Allied Telesyn)**
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000

**dmesg**
[25897.292000] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
**[26054.196000] usb 2-2: USB disconnect, address 4**
**[26054.196000] eth1: unregister 'cdc_ether' usb-0000:00:1d.1-2, CDC Ethernet Device**
[26181.292000] e100: eth0: e100_watchdog: link down
[26183.292000] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[28661.292000] e100: eth0: e100_watchdog: link down
[28665.292000] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[28677.292000] e100: eth0: e100_watchdog: link down
[28679.292000] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[B][34831.860000] usb 2-2: new full speed USB device using uhci_hcd and address 5
[34832.068000] usb 2-2: configuration #2 chosen from 2 choices
[34832.072000] eth1: register 'cdc_ether' at usb-0000:00:1d.1-2, CDC Ethernet Device, 00:0f:a3:55:9f:7c[/B]

Is there a problem with the current kernel?

---

### Post by applegrew on 2007-10-24
Bump.

---

### Post by froy02 on 2007-10-24
I think you  can not use the usb and ethernet port at the time.  Check your documentation for your ADSL modem just to be sure.

 What you need is a router that will be connected to the ether port and will provide you with 4 ethernet ports and also wireless connections.  they sell from $20 to $40.

If you do get a router,  disconnect the adsl cable from your computer then  connect it  to wan port on the router.  Then connect your computers to the  ethernet ports of the router.

Hope this helps.
Froy

---

### Post by applegrew on 2007-10-24
> I think you can not use the usb and ethernet port at the time. Check your documentation for your ADSL modem just to be sure.
I have tried with both the Ethernet cable connected and disconnected. This didn't help.

> What you need is a router that will be connected to the ether port and will provide you with 4 ethernet ports and also wireless connections. they sell from $20 to $40.
My dad is not allowing me to buy any router or switches. If had been given the option then I would have definitely bought an ADSL router with an ethernet port and a Wifi.

---

### Post by applegrew on 2007-10-25
bump

---

### Post by applegrew on 2007-10-26
can somebody help?

---

