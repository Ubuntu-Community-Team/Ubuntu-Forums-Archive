---
title: "E220  connects but E270 won't  on 8.10 x64 bit"
date: 2008-11-25
forum: Networking &amp; Wireless
---

### Post by jimmyjim11 on 2008-11-25
Just after upgrading to Ubuntu 8.10 from 8.04
where i had a O2 Huawei E270 modem working no problems

the new network manager found the modem straight away e220/e270.
entered settings but would not connect and when it did no data could be  transferred :confused:

print out of log.
> Nov 4 21:15:11 sham-desktop pppd[6349]: pppd 2.4.4 started by root, uid 0

Nov 4 21:15:11 sham-desktop pppd[6349]: Using interface ppp0

Nov 4 21:15:11 sham-desktop pppd[6349]: Connect: ppp0 <--> /dev/ttyUSB0

Nov 4 21:15:11 sham-desktop pppd[6349]: CHAP authentication succeeded

Nov 4 21:15:11 sham-desktop pppd[6349]: CHAP authentication succeeded

Nov 4 21:15:19 sham-desktop pppd[6349]: Could not determine remote IP address: defaulting to 10.64.64.64

Nov 4 21:15:19 sham-desktop pppd[6349]: local IP address 89.204.253.194

Nov 4 21:15:19 sham-desktop pppd[6349]: remote IP address 10.64.64.64

Nov 4 21:15:19 sham-desktop pppd[6349]: primary DNS address 10.11.12.13

Nov 4 21:15:19 sham-desktop pppd[6349]: secondary DNS address 10.11.12.14 

got the loan of a E220 modem put my sim card into it and it worked no problems just disconnected every 15 20 mins or so 

any settings i could change :confused:
TIA


> /etc/init.d/NetworkManager stop
 * Stopping NetworkManager...                                            [ OK ] 
root@sham-desktop:/home/sham# NM_SERIAL_DEBUG=1 NetworkManager --no-daemon 2>&1 | tee /tmp/nm-serial.txt
NetworkManager: <info>  starting...
NetworkManager: <info>  ttyUSB0: driver is 'option'.
NetworkManager: <debug> [1227652269.469830] setup_monitor_device(): No monitoring udi provided
NetworkManager: <info>  Found new Modem device 'ttyUSB0'.
NetworkManager: <info>  (ttyUSB0): exported as /org/freedesktop/Hal/devices/usb_device_12d1_1003_noserial_if0_serial_usb_0
NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889))
NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889))
NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889))
NetworkManager: <info>  (ttyUSB0): device state change: 1 -> 2
NetworkManager: <info>  (ttyUSB0): deactivating device (reason: 2).
NetworkManager: nm_system_device_flush_ip4_routes_with_iface: assertion `iface_idx >= 0' failed
NetworkManager: nm_system_device_flush_ip4_addresses_with_iface: assertion `iface_idx >= 0' failed
NetworkManager: <info>  (ttyUSB0): device state change: 2 -> 3



---

### Post by jimmyjim11 on 2008-11-29
managed to get the e270 working it seems you have to have the PIN verification ON to get it to connect ](*,)

now my only problem is to keep in connected it disconnects every 5 to 20 mins :frown: :confused:

---

