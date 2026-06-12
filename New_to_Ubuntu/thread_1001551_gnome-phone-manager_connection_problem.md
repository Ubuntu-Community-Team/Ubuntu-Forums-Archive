---
title: "gnome-phone-manager connection problem"
date: 2008-12-04
forum: New to Ubuntu
---

### Post by nashrafeeg on 2008-12-04
hi i am trying to connect my nokia 3230 to phone manager via the data cable 
when i attach it, it is recognized as a mobile broad band modem my lsusb is follows 
[PHP]Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 011: ID 0421:0421 Nokia Mobile Phones 3230 Phone Parent
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 064e:a101 Suyin Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
[/PHP]

and my dmesg is as follows
[PHP][109138.598832] usb 3-2: USB disconnect, address 11
[109144.185068] usb 3-2: new full speed USB device using ohci_hcd and address 12
[109144.416760] usb 3-2: configuration #1 chosen from 1 choice
[109144.430685] cdc_acm 3-2:1.5: ttyACM0: USB ACM device
[/PHP]

seeing this i changed the port on connection preferences to /dev/ttyACM0
even after this i am not able to connect the error i am getting is 

nash@MDUB:~$ gnome-phone-manager 
** Message: bdaddr 
** Message: New connection device is /dev/ttyACM0 (changed)
** Message: New connection device is /dev/ttyACM0 (not changed)
** Message: Connecting...
** Message: Status 1
** Message: Making serial port connection
** Message: Couldn't connect to the device, gnapplet needed but not running
** Message: Failed connection to device on /dev/ttyACM0
** Message: Exiting connect thread

so can any one point me in the right direction to fix this i am trying this method cause my pc does not have a blue tooth capability 


cheers 
nash

---

### Post by nashrafeeg on 2008-12-06
bump

---

