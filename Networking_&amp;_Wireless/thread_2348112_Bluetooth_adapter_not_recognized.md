---
title: "Bluetooth adapter not recognized"
date: 2016-12-31
forum: Networking &amp; Wireless
---

### Post by Tarhawk on 2016-12-31
Trying to figure out how to get bluetooth adapter recognized in Ubuntu 16.04.

Toshiba Satellite c55 b 5196

Blueman is in the system tray but does not find adapters when trying to setup new device.

lsusb output:
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 1a40:0101 Terminus Technology Inc. Hub
Bus 001 Device 002: ID 13d3:5652 IMC Networks 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


Not sure where to go from here, tried a couple of workarounds for the problem with no result.  Any help is greatly appreciated.

---

### Post by jeremy31 on 2017-01-01
What are the results from ```
dmesg | egrep -i 'blue|firm'
```

---

### Post by Tarhawk on 2017-01-02
Thanks for the reply, 

When I plug that code into terminal it gives no output at all, just goes back to the user name prompt.  I just plugged that exact code in, not sure if it needs a sudo or other suffix behind it.

---

### Post by jeremy31 on 2017-01-02
It should have had some output even without a bluetooth adapter
```
dpkg -l | grep bluez
```

---

### Post by Tarhawk on 2017-01-02
This one did provide output:

```
ii  bluez                                                5.37-0ubuntu5                                 amd64        Bluetooth tools and daemonsii  bluez-cups                                           5.37-0ubuntu5                                 amd64        Bluetooth printer driver for CUPS
ii  bluez-obexd                                          5.37-0ubuntu5                                 amd64        bluez obex daemon
ii  python-bluez                                         0.22-1                                        amd64        Python wrappers around BlueZ for rapid bluetooth development



```

---

### Post by jeremy31 on 2017-01-02
Did you get it working?  I see it is marked Solved

---

