---
title: "Huawei E220 Needs reboot to work, why"
date: 2008-03-13
forum: Networking &amp; Wireless
---

### Post by xet on 2008-03-13
Hi!

I have a Huawei E220 USB 3G modem, and it worked great on my laptop until I reinstalled it. It also works great in debian on an old laptop.
But now, it works first after a reboot.

dmesg shows only /dev/ttyUSB0, and if I try to connect using wvdial, I get no answer from the port (time out)

after reboot with the modem still plugged in:
[   15.852000] usb 1-1: GSM modem (1-port) converter now attached to ttyUSB0
[   15.852000] usb 1-1: GSM modem (1-port) converter now attached to ttyUSB1
[   15.852000] usb 1-1: GSM modem (1-port) converter now attached to ttyUSB2
And finaly I connect using wvdial.
I have tried to start up my laptop with the modem plug/unplug to the computer, but it doesnt change the fact that it doesnt work the first time I start up the computer.

Any idea how to fix this?


Per

---

### Post by Paul Weaver on 2008-03-13
What do you mean by "reinstall it". 

I have a E220 and it's usually recognised, although sometimes I need to unplug/replug in dodgy signal areas, especially when I've suspended/resumed and either plugged or unplugged the modem while suspended.

Did you have the vodafone-mobile-connect-card-driver-for-linux package installed before? It includes some udev rules including:

/etc/udev/rules.d/99-huawei-e220.rules
# From [http://www.kanoistika.sk/bobovsky/archiv/umts/](http://www.kanoistika.sk/bobovsky/archiv/umts/)
SYSFS{idVendor}=="12d1", SYSFS{idProduct}=="1003", RUN+="/usr/sbin/huaweiAktBbo"
SYSFS{idVendor}=="12d1", SYSFS{idProduct}=="1001", RUN+="/usr/sbin/huaweiAktBbo"

I think you might be snagging on the built-in "cd" that the modem has -- it presents itself as a usbstorage device, with windows drivers on it, until you install the drivers.

When I plug the device in I get the following. Note the 3 USB ttys created. kppp (which seems the best program I've tried for my train journey) uses ttyUSB0. 

```
Mar 12 08:03:38 newsjtclap99 kernel: [86024.996000] usb 3-2: new full speed USB device using uhci_hcd and address 6
Mar 12 08:03:38 newsjtclap99 kernel: [86025.148000] usb 3-2: configuration #1 chosen from 1 choice
Mar 12 08:03:38 newsjtclap99 kernel: [86025.152000] option 3-2:1.0: GSM modem (1-port) converter detected
Mar 12 08:03:38 newsjtclap99 kernel: [86025.152000] usb 3-2: GSM modem (1-port) converter now attached to ttyUSB0
Mar 12 08:03:40 newsjtclap99 kernel: [86026.256000] usb 3-2: USB disconnect, address 6
Mar 12 08:03:40 newsjtclap99 kernel: [86026.256000] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
Mar 12 08:03:40 newsjtclap99 kernel: [86026.256000] option 3-2:1.0: device disconnected
Mar 12 08:03:40 newsjtclap99 kernel: [86027.000000] usb 3-2: new full speed USB device using uhci_hcd and address 7
Mar 12 08:03:40 newsjtclap99 kernel: [86027.156000] usb 3-2: configuration #1 chosen from 1 choice
Mar 12 08:03:40 newsjtclap99 kernel: [86027.160000] option 3-2:1.0: GSM modem (1-port) converter detected
Mar 12 08:03:40 newsjtclap99 kernel: [86027.160000] usb 3-2: GSM modem (1-port) converter now attached to ttyUSB0
Mar 12 08:03:40 newsjtclap99 kernel: [86027.164000] option 3-2:1.1: GSM modem (1-port) converter detected
Mar 12 08:03:40 newsjtclap99 kernel: [86027.164000] usb 3-2: GSM modem (1-port) converter now attached to ttyUSB1
Mar 12 08:03:40 newsjtclap99 kernel: [86027.164000] option 3-2:1.2: GSM modem (1-port) converter detected
Mar 12 08:03:40 newsjtclap99 kernel: [86027.164000] usb 3-2: GSM modem (1-port) converter now attached to ttyUSB2
Mar 12 08:04:58 newsjtclap99 pppd[16949]: pppd 2.4.4 started by paul, uid 1000
Mar 12 08:04:58 newsjtclap99 pppd[16949]: Using interface ppp0
Mar 12 08:04:58 newsjtclap99 pppd[16949]: Connect: ppp0 <--> /dev/ttyUSB0
Mar 12 08:04:58 newsjtclap99 pppd[16949]: CHAP authentication succeeded
Mar 12 08:04:58 newsjtclap99 pppd[16949]: CHAP authentication succeeded
Mar 12 08:05:05 newsjtclap99 pppd[16949]: Could not determine remote IP address: defaulting to 10.64.64.64
Mar 12 08:05:05 newsjtclap99 pppd[16949]: local  IP address 10.227.43.201
Mar 12 08:05:05 newsjtclap99 pppd[16949]: remote IP address 10.64.64.64
Mar 12 08:08:25 newsjtclap99 pppd[16949]: LCP terminated by peer
Mar 12 08:08:25 newsjtclap99 pppd[16949]: Connect time 3.4 minutes.
Mar 12 08:08:25 newsjtclap99 pppd[16949]: Sent 67847 bytes, received 180782 bytes.
Mar 12 08:08:25 newsjtclap99 pppd[16949]: Hangup (SIGHUP)
Mar 12 08:08:25 newsjtclap99 pppd[16949]: Modem hangup
Mar 12 08:08:25 newsjtclap99 pppd[16949]: Connection terminated.
Mar 12 08:08:25 newsjtclap99 pppd[16949]: Exit.
Mar 12 08:08:30 newsjtclap99 pppd[17018]: pppd 2.4.4 started by paul, uid 1000
Mar 12 08:08:30 newsjtclap99 pppd[17018]: Using interface ppp0
Mar 12 08:08:30 newsjtclap99 pppd[17018]: Connect: ppp0 <--> /dev/ttyUSB0
Mar 12 08:08:30 newsjtclap99 pppd[17018]: CHAP authentication succeeded
Mar 12 08:08:30 newsjtclap99 pppd[17018]: CHAP authentication succeeded
Mar 12 08:09:00 newsjtclap99 pppd[17018]: Terminating on signal 15
Mar 12 08:09:00 newsjtclap99 pppd[17018]: Connection terminated.
Mar 12 08:09:00 newsjtclap99 pppd[17018]: Exit.

```

---

### Post by xet on 2008-03-13
Hi!
Now I get it to work!
Using udevrule:
ATTRS{idProduct}=="1003", ATTRS{idVendor}=="12d1", RUN+="script", GROUP="dialout"
and script:
modprobe -r uhci_hcd
modprobe uhci_hcd

Thank you
Per

---

