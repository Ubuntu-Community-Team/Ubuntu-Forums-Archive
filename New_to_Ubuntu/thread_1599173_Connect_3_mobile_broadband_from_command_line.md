---
title: "Connect 3 mobile broadband from command line"
date: 2010-10-17
forum: New to Ubuntu
---

### Post by Stephen Morgan on 2010-10-17
Purely because I like using the command line I'd like to be able to  connect from the command line, but can't figure out how to do it.  wvdialconf works well enough, as does poff, but pon just hangs and  wvdial fails with "Connect script failed".

The log for connecting with the GUI, which works perfectly, looks like this iin te syslog:

Oct 17 17:06:40 brueria pppd[5971]: Plugin /usr/lib/pppd/2.4.4/nm-pppd-plugin.so loaded.
Oct 17 17:06:40 brueria pppd[5971]: pppd 2.4.5 started by root, uid 0
Oct 17 17:06:40 brueria pppd[5971]: Using interface ppp0
Oct 17 17:06:40 brueria pppd[5971]: Connect: ppp0 <--> /dev/ttyUSB2
Oct 17 17:06:40 brueria pppd[5971]: CHAP authentication succeeded
Oct 17 17:06:40 brueria pppd[5971]: CHAP authentication succeeded
Oct 17 17:06:46 brueria pppd[5971]: Could not determine remote IP address: defaulting to 10.64.64.64
Oct 17 17:06:46 brueria pppd[5971]: local  IP address 94.196.234.211
Oct 17 17:06:46 brueria pppd[5971]: remote IP address 10.64.64.64
Oct 17 17:26:52 brueria pppd[5971]: Terminating on signal 15
Oct 17 17:26:52 brueria pppd[5971]: Connect time 20.1 minutes.
Oct 17 17:26:52 brueria pppd[5971]: Sent 621325 bytes, received 3702241 bytes.
Oct 17 17:26:52 brueria pppd[5971]: Connection terminated.
Oct 17 17:26:52 brueria pppd[5971]: Exit.

Whereas with wvdial I get this:

Oct 17 17:39:56 brueria modem-manager: (ttyUSB2) closing serial device...
Oct 17 17:39:56 brueria modem-manager: Modem /org/freedesktop/ModemManager/Modems/1: state changed (registered -> disabled)
Oct 17 17:39:56 brueria modem-manager: Removed modem /sys/devices/pci0000:00/0000:00:1d.7/usb2/2-1
Oct 17 17:39:56 brueria NetworkManager: <info>  (ttyUSB2): now unmanaged
Oct 17 17:39:56 brueria NetworkManager: <info>  (ttyUSB2): device state change: 3 -> 1 (reason 36)
Oct 17 17:39:56 brueria NetworkManager: <info>  (ttyUSB2): cleaning up...
Oct 17 17:39:56 brueria NetworkManager: <info>  (ttyUSB2): taking down device.
Oct  17 17:39:56 brueria NetworkManager: <info>  Unmanaged Device  found; state CONNECTED forced. (see  [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889))

Oct 17 17:39:56 brueria modem-manager: (ttyUSB2) closing serial device...
Oct 17 17:39:56 brueria modem-manager: Modem /org/freedesktop/ModemManager/Modems/1: state changed (registered -> disabled)
Oct 17 17:39:56 brueria modem-manager: Removed modem /sys/devices/pci0000:00/0000:00:1d.7/usb2/2-1
Oct 17 17:39:56 brueria NetworkManager: <info>  (ttyUSB2): now unmanaged
Oct 17 17:39:56 brueria NetworkManager: <info>  (ttyUSB2): device state change: 3 -> 1 (reason 36)
Oct 17 17:39:56 brueria NetworkManager: <info>  (ttyUSB2): cleaning up...
Oct 17 17:39:56 brueria NetworkManager: <info>  (ttyUSB2): taking down device.
Oct 17 17:39:56 brueria kernel: [40429.045625] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
Oct 17 17:39:56 brueria kernel: [40429.045656] option 2-1:1.0: device disconnected
Oct 17 17:39:56 brueria kernel: [40429.045824] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
Oct 17 17:39:56 brueria kernel: [40429.045838] option 2-1:1.1: device disconnected
Oct 17 17:39:56 brueria kernel: [40429.045912] option: option_instat_callback: error -108
Oct 17 17:39:56 brueria kernel: [40429.046513] option1 ttyUSB2: GSM modem (1-port) converter now disconnected from ttyUSB2
Oct 17 17:39:56 brueria kernel: [40429.046528] option 2-1:1.3: device disconnected
Oct  17 17:39:56 brueria NetworkManager: <info>  Unmanaged Device  found; state CONNECTED forced. (see  [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889))
Oct 17 17:39:56 brueria  NetworkManager: <info>  Unmanaged Device found; state CONNECTED  forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889))
Oct 17 17:39:56 brueria kernel: [40429.162547] usb 2-1: reset high speed USB device using ehci_hcd and address 7
Oct 17 17:40:12 brueria kernel: [40444.282528] usb 2-1: device descriptor read/64, error -110
Oct 17 17:40:27 brueria kernel: [40459.512530] usb 2-1: device descriptor read/64, error -110
Oct 17 17:40:27 brueria kernel: [40459.742529] usb 2-1: reset high speed USB device using ehci_hcd and address 7
Oct 17 17:40:42 brueria kernel: [40474.862538] usb 2-1: device descriptor read/64, error -110
Oct 17 17:40:57 brueria kernel: [40490.092614] usb 2-1: device descriptor read/64, error -110
Oct 17 17:40:58 brueria kernel: [40490.322538] usb 2-1: reset high speed USB device using ehci_hcd and address 7
Oct 17 17:41:08 brueria kernel: [40500.742108] usb 2-1: device not accepting address 7, error -110
Oct 17 17:41:08 brueria kernel: [40500.860167] usb 2-1: reset high speed USB device using ehci_hcd and address 7
Oct 17 17:41:19 brueria kernel: [40511.282519] usb 2-1: device not accepting address 7, error -110
Oct 17 17:41:19 brueria kernel: [40511.282559] usb 2-1: USB disconnect, address 7
Oct 17 17:41:19 brueria kernel: [40511.282806] sd 11:0:0:0: Device offlined - not ready after error recovery
Oct 17 17:41:19 brueria kernel: [40511.422549] usb 2-1: new high speed USB device using ehci_hcd and address 8
Oct 17 17:41:34 brueria kernel: [40526.540190] usb 2-1: device descriptor read/64, error -110

And  so on, after which the modem needs to be removed and reattached before  it'll work again. In Bash the wvdial command returns the following:

--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT*99#
--> Waiting for carrier.
ATDT*99#
--> Disconnecting at Sun Oct 17 17:39:56 2010

---

