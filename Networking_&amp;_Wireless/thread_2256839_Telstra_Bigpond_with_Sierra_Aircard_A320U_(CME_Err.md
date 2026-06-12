---
title: "Telstra Bigpond with Sierra Aircard A320U (CME Error - No network Service)"
date: 2014-12-15
forum: Networking &amp; Wireless
---

### Post by E._R._Jacobson on 2014-12-15
I am attempting to use a Sierra wireless broadband USB-modem with (Telecom Australia) Bigpond 4G. I am using Ubuntu 14.04 on a Lenovo Thinkpad, approximately two years old. I got similar behaviour with version 12.04. Kernel version is currently 3.13.

I consistently get an error of "No Network Service" when attempting to connect, after the Network Manager reports having registered successfully. My APN is *telstra.bigpond*. All authentication methods are allowed.

When I plug the USB device in, it's detected fine (on ttyUSB2). You can skip down to the third or fourth quotation-block before you see anything that looks like a problem.
```
<date>:44:57 <..> kernel: [ 9085.938621] usb 3-4: new high-speed USB device number 2 using xhci_hcd
<date>:44:57 <..> kernel: [ 9085.956456] usb 3-4: config 1 has an invalid interface number: 7 but max is 4
<date>:44:57 <..> kernel: [ 9085.956465] usb 3-4: config 1 has no interface number 2
<date>:44:57 <..> kernel: [ 9085.957973] usb 3-4: New USB device found, idVendor=0f3d, idProduct=68aa
<date>:44:57 <..> kernel: [ 9085.957979] usb 3-4: New USB device strings: Mfr=3, Product=2, SerialNumber=4
<date>:44:57 <..> kernel: [ 9085.957983] usb 3-4: Product: AirCard 320U
<date>:44:57 <..> kernel: [ 9085.957986] usb 3-4: Manufacturer: Sierra Wireless, Incorporated
<date>:44:57 <..> kernel: [ 9085.957989] usb 3-4: SerialNumber: 357272043209927
<date>:44:57 <..> mtp-probe: checking bus 3, device 2: "/sys/devices/pci0000:00/0000:00:14.0/usb3/3-4"
<date>:44:57 <..> mtp-probe: bus: 3, device: 2 was not an MTP device
<date>:44:57 <..> kernel: [ 9086.001875] usbcore: registered new interface driver usbserial
<date>:44:57 <..> kernel: [ 9086.001891] usbcore: registered new interface driver usbserial_generic
<date>:44:57 <..> kernel: [ 9086.001902] usbserial: USB Serial support registered for generic
<date>:44:57 <..> kernel: [ 9086.022464] usbcore: registered new interface driver sierra
<date>:44:57 <..> kernel: [ 9086.022476] usbserial: USB Serial support registered for Sierra USB modem
<date>:44:57 <..> kernel: [ 9086.022497] sierra 3-4:1.0: Sierra USB modem converter detected
<date>:44:57 <..> kernel: [ 9086.024076] usb 3-4: Sierra USB modem converter now attached to ttyUSB0
<date>:44:57 <..> kernel: [ 9086.024099] sierra 3-4:1.1: Sierra USB modem converter detected
<date>:44:57 <..> kernel: [ 9086.024470] usb 3-4: Sierra USB modem converter now attached to ttyUSB1
<date>:44:57 <..> kernel: [ 9086.024482] sierra 3-4:1.3: Sierra USB modem converter detected
<date>:44:57 <..> kernel: [ 9086.024869] usb 3-4: Sierra USB modem converter now attached to ttyUSB2
<date>:44:57 <..> kernel: [ 9086.024881] sierra 3-4:1.4: Sierra USB modem converter detected
<date>:44:57 <..> kernel: [ 9086.025218] usb 3-4: Sierra USB modem converter now attached to ttyUSB3
<date>:44:57 <..> kernel: [ 9086.049516] sierra_net 3-4:1.7 wwan0: register 'sierra_net' at usb-0000:00:14.0-4, Sierra Wireless USB-to-WWAN Modem, 2e:83:7f:98:01:07
<date>:44:57 <..> kernel: [ 9086.050538] usbcore: registered new interface driver sierra_net
<date>:44:57 <..> NetworkManager[824]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:14.0/usb3/3-4/3-4:1.7/net/wwan0, iface: wwan0)
<date>:44:57 <..> NetworkManager[824]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:14.0/usb3/3-4/3-4:1.7/net/wwan0, iface: wwan0): no ifupdown configuration found.
<date>:44:57 <..> ModemManager[717]: <warn>  (ttyUSB3): port attributes not fully set
<date>:44:57 <..> ModemManager[717]: <warn>  (ttyUSB2): port attributes not fully set
<date>:44:57 <..> ModemManager[717]: <warn>  (ttyUSB0): port attributes not fully set
<date>:44:57 <..> ModemManager[717]: <warn>  (ttyUSB1): port attributes not fully set
[COLOR=blue]<date>:45:14 <..> ModemManager[717]: <info>  Creating modem with plugin 'Sierra' and '5' ports
<date>:45:14 <..> ModemManager[717]: <warn>  Could not grab port (tty/ttyUSB0): 'Cannot add port 'tty/ttyUSB0', unhandled serial type'
<date>:45:14 <..> ModemManager[717]: <warn>  (ttyUSB2): port attributes not fully set
<date>:45:14 <..> ModemManager[717]: <info>  Modem for device at '/sys/devices/pci0000:00/0000:00:14.0/usb3/3-4' successfully created
<date>:45:21 <..> ModemManager[717]: <info>  Modem: state changed (unknown -> disabled)
<date>:45:21 <..> NetworkManager[824]: <warn> (ttyUSB2): failed to look up interface index[/COLOR]
<date>:45:21 <..> NetworkManager[824]: <info> (ttyUSB2): new Broadband device (driver: 'sierra, sierra_net' ifindex: 0)
<date>:45:21 <..> NetworkManager[824]: <info> (ttyUSB2): exported as /org/freedesktop/NetworkManager/Devices/2
```
[FONT=Liberation Serif][COLOR=#000000]Yes, I have redacted the log entries have the date, hour and computer name.

There are a couple of errors reported, that don't look alarming yet. The port attributes aren't fully set and NetworkManager failed to look-up the
interface index. [/COLOR][/FONT]

When I connect, I mostly get noise about the other two network devices, a cable that isn't plugged in and Broadcom Wifi adapter.
```
<date>:07:41 <..> NetworkManager[824]: <info> enable requested (sleeping: no  enabled: no)
<date>:07:41 <..> NetworkManager[824]: <info> waking up and re-enabling...
<date>:07:41 <..> NetworkManager[824]: <info> (wlan0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
<date>:07:41 <..> NetworkManager[824]: <info> (wlan0): bringing up device.
<date>:07:41 <..> NetworkManager[824]: <info> (wlan0): preparing device.
<date>:07:41 <..> NetworkManager[824]: <info> (wlan0): deactivating device (reason 'managed') [2]
<date>:07:41 <..> NetworkManager[824]: <info> Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
<date>:07:41 <..> NetworkManager[824]: message repeated 3 times: [ <info> Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)]
<date>:07:41 <..> NetworkManager[824]: <info> NetworkManager state is now CONNECTED_GLOBAL
<date>:07:41 <..> NetworkManager[824]: <info> Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
<date>:07:41 <..> NetworkManager[824]: <info> Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
<date>:07:41 <..> NetworkManager[824]: <info> (eth0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
<date>:07:41 <..> NetworkManager[824]: <info> (eth0): bringing up device.
<date>:07:41 <..> dbus[693]: [system] Activating service name='fi.w1.wpa_supplicant1' (using servicehelper)
<date>:07:41 <..> NetworkManager[824]: <info> (eth0): preparing device.
<date>:07:41 <..> NetworkManager[824]: <info> (eth0): deactivating device (reason 'managed') [2]
<date>:07:41 <..> NetworkManager[824]: <info> Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
[COLOR=blue]<date>:07:41 <..> NetworkManager[824]: <info> (ttyUSB2): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2][/COLOR]
<date>:07:41 <..> kernel: [10451.995972] r8169 0000:0c:00.0 eth0: link down
<date>:07:41 <..> kernel: [10451.996022] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
<date>:07:41 <..> kernel: [10451.996494] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
<date>:07:41 <..> NetworkManager[824]: <info> (ttyUSB2): deactivating device (reason 'managed') [2]
<date>:07:41 <..> NetworkManager[824]: <info> NetworkManager state is now DISCONNECTED
<date>:07:41 <..> NetworkManager[824]: <info> (ttyUSB2): device state change: unavailable -> disconnected (reason 'none') [20 30 0]
<date>:07:41 <..> dbus[693]: [system] Successfully activated service 'fi.w1.wpa_supplicant1'
<date>:07:41 <..> NetworkManager[824]: <info> wpa_supplicant started
<date>:07:41 <..> wpa_supplicant[4400]: Successfully initialized wpa_supplicant
<date>:07:41 <..> NetworkManager[824]: <info> (wlan0) supports 1 scan SSIDs
<date>:07:41 <..> NetworkManager[824]: <warn> Trying to remove a non-existant call id.
<date>:07:41 <..> NetworkManager[824]: <info> (wlan0): supplicant interface state: starting -> ready
<date>:07:41 <..> NetworkManager[824]: <info> (wlan0): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
<date>:07:41 <..> NetworkManager[824]: <info> (wlan0): supplicant interface state: ready -> disconnected
<date>:07:41 <..> NetworkManager[824]: <info> (wlan0) supports 1 scan SSIDs
<date>:07:41 <..> wpa_supplicant[4405]: wlan0: CTRL-EVENT-SCAN-STARTED
<date>:07:43 <..> avahi-daemon[740]: Joining mDNS multicast group on interface wlan0.IPv6 with address fe80::6a94:23ff:fef6:527f.
<date>:07:43 <..> avahi-daemon[740]: New relevant interface wlan0.IPv6 for mDNS.
<date>:07:43 <..> avahi-daemon[740]: Registering new address record for fe80::6a94:23ff:fef6:527f on wlan0.*.
<date>:07:45 <..> NetworkManager[824]: <info> (wlan0): supplicant interface state: disconnected -> inactive
```

That's only one line about the USB-modem.

When I enable Wireless Broadband, no problems are reported.
```
<date>:09:35 <..> ModemManager[717]: <info>  Modem /org/freedesktop/ModemManager1/Modem/0: state changed (disabled -> enabling)
<date>:09:35 <..> NetworkManager[824]: <info> (ttyUSB2) modem state changed, 'disabled' --> 'enabling' (reason: user-requested)
<date>:09:35 <..> ModemManager[717]: <warn>  (ttyUSB2): port attributes not fully set
<date>:09:35 <..> ModemManager[717]: <warn>  (ttyUSB3): port attributes not fully set
<date>:09:39 <..> ModemManager[717]: <info>  Modem /org/freedesktop/ModemManager1/Modem/0: 3GPP Registration state changed (unknown -> searching)
<date>:09:39 <..> ModemManager[717]: <info>  Modem /org/freedesktop/ModemManager1/Modem/0: state changed (enabling -> searching)
<date>:09:39 <..> NetworkManager[824]: <info> (ttyUSB2) modem state changed, 'enabling' --> 'searching' (reason: user-requested)
<date>:09:39 <..> NetworkManager[824]: <info> WWAN now enabled by management service
<date>:09:44 <..> ModemManager[717]: <info>  Modem /org/freedesktop/ModemManager1/Modem/0: 3GPP Registration state changed (searching -> registering)
<date>:09:44 <..> ModemManager[717]: <info>  Modem /org/freedesktop/ModemManager1/Modem/0: 3GPP location updated (MCC: '505', MNC: '1', Location area code: '0', Cell ID: '0')
<date>:09:44 <..> ModemManager[717]: <info>  Modem /org/freedesktop/ModemManager1/Modem/0: 3GPP Registration state changed (registering -> home)
<date>:09:44 <..> ModemManager[717]: <info>  Modem /org/freedesktop/ModemManager1/Modem/0: state changed (searching -> registered)
<date>:09:44 <..> NetworkManager[824]: <info> (ttyUSB2) modem state changed, 'searching' --> 'registered' (reason: unknown)
<date>:09:44 <..> ModemManager[717]: <info>  Modem /org/freedesktop/ModemManager1/Modem/0: signal quality updated (20)
<date>:09:44 <..> ModemManager[717]: <info>  Modem /org/freedesktop/ModemManager1/Modem/0: access technology changed (unknown -> umts)
<date>:09:50 <..> ModemManager[717]: <info>  Modem /org/freedesktop/ModemManager1/Modem/0: 3GPP Registration state changed (home -> searching)
<date>:09:50 <..> ModemManager[717]: <info>  Modem /org/freedesktop/ModemManager1/Modem/0: 3GPP location updated (MCC: '0', MNC: '0', Location area code: '0', Cell ID: '0')
<date>:10:14 <..> ModemManager[717]: <info>  Modem /org/freedesktop/ModemManager1/Modem/0: access technology changed (umts -> lte)
<date>:10:14 <..> ModemManager[717]: <info>  Modem /org/freedesktop/ModemManager1/Modem/0: signal quality updated (20)
<date>:10:27 <..> ModemManager[717]: <info>  Modem /org/freedesktop/ModemManager1/Modem/0: 3GPP Registration state changed (searching -> registering)
<date>:10:27 <..> ModemManager[717]: <info>  Modem /org/freedesktop/ModemManager1/Modem/0: 3GPP location updated (MCC: '505', MNC: '1', Location area code: '0', Cell ID: '0')
<date>:10:27 <..> ModemManager[717]: <info>  Modem /org/freedesktop/ModemManager1/Modem/0: 3GPP Registration state changed (registering -> home)
```

[FONT=Liberation Serif][COLOR=#000000]The main issue here is that I would prefer to connect using 4G, rather than 3G (and the Network Manager is configured accordingly). Where the modem should flash its 4G green LED first, it is mostly flashing the 3G blue one. (The Aircard actually has two indicators with different coloured-LEDs. I'm only describing the one on the right.)

When, I go to connect, the problem occurs
```
<date>:11:07 <..> NetworkManager[824]: <info> Activation (ttyUSB2) starting connection 'Telstra Telstra BigPond 1'
<date>:11:07 <..> NetworkManager[824]: <info> (ttyUSB2): device state change: disconnected -> prepare (reason 'none') [30 40 0]
<date>:11:07 <..> NetworkManager[824]: <info> NetworkManager state is now CONNECTING
<date>:11:07 <..> NetworkManager[824]: <info> Activation (ttyUSB2) Stage 1 of 5 (Device Prepare) scheduled...
<date>:11:07 <..> NetworkManager[824]: <info> Activation (ttyUSB2) Stage 1 of 5 (Device Prepare) started...
<date>:11:07 <..> NetworkManager[824]: <info> Activation (ttyUSB2) Stage 1 of 5 (Device Prepare) complete.
<date>:11:07 <..> ModemManager[717]: <info>  Simple connect started...
<date>:11:07 <..> ModemManager[717]: <info>  Simple connect state (4/8): Wait to get fully enabled
<date>:11:07 <..> ModemManager[717]: <info>  Simple connect state (5/8): Register
<date>:11:09 <..> ModemManager[717]: <info>  Modem /org/freedesktop/ModemManager1/Modem/0: 3GPP Registration state changed (searching -> registering)
<date>:11:09 <..> ModemManager[717]: <info>  Modem /org/freedesktop/ModemManager1/Modem/0: 3GPP location updated (MCC: '505', MNC: '1', Location area code: '0', Cell ID: '0')
<date>:11:09 <..> ModemManager[717]: <info>  Modem /org/freedesktop/ModemManager1/Modem/0: 3GPP Registration state changed (registering -> home)
<date>:11:10 <..> ModemManager[717]: <info>  Modem /org/freedesktop/ModemManager1/Modem/0: 3GPP location updated (MCC: '505', MNC: '1', Location area code: '2252', Cell ID: '14C2EF7')
<date>:11:10 <..> ModemManager[717]: <info>  Simple connect state (6/8): Bearer
<date>:11:10 <..> ModemManager[717]: <info>  Simple connect state (7/8): Connect
<date>:11:10 <..> ModemManager[717]: <info>  Modem /org/freedesktop/ModemManager1/Modem/0: state changed (registered -> connecting)
<date>:11:10 <..> NetworkManager[824]: <info> (ttyUSB2) modem state changed, 'registered' --> 'connecting' (reason: user-requested)
<date>:11:12 <..> kernel: [10662.690705] sierra_net 3-4:1.7 wwan0: Link type unsupported: 0xff
<date>:11:12 <..> kernel: [10662.690714] sierra_net 3-4:1.7 wwan0: Invalid LSI
<date>:11:12 <..> ModemManager[717]: <info>  Modem /org/freedesktop/ModemManager1/Modem/0: state changed (connecting -> registered)
[COLOR=red]<date>:11:12 <..> NetworkManager[824]: <info> (ttyUSB2) modem state changed, 'connecting' --> 'registered' (reason: user-requested)
<date>:11:12 <..> NetworkManager[824]: <warn> (ttyUSB2) failed to connect modem: No network service[/COLOR]
<date>:11:12 <..> NetworkManager[824]: <info> (ttyUSB2): device state change: prepare -> failed (reason 'gsm-registration-idle') [40 120 30]
```[/COLOR]```

<date>:11:12 <..> NetworkManager[824]: <info> NetworkManager state is now DISCONNECTED
<date>:11:12 <..> NetworkManager[824]: <warn> Activation (ttyUSB2) failed for connection 'Telstra Telstra BigPond 1'
<date>:11:12 <..> NetworkManager[824]: <info> (ttyUSB2): device state change: failed -> disconnected (reason 'none') [120 30 0]
<date>:11:12 <..> NetworkManager[824]: <info> (ttyUSB2): deactivating device (reason 'none') [0]
<date>:11:14 <..> ModemManager[717]: <info>  Modem /org/freedesktop/ModemManager1/Modem/0: access technology changed (lte -> umts)
<date>:11:14 <..> ModemManager[717]: <info>  Modem /org/freedesktop/ModemManager1/Modem/0: signal quality updated (20)
<date>:11:19 <..> ModemManager[717]: <info>  Modem /org/freedesktop/ModemManager1/Modem/0: 3GPP Registration state changed (home -> searching)
<date>:11:19 <..> ModemManager[717]: <info>  Modem /org/freedesktop/ModemManager1/Modem/0: 3GPP location updated (MCC: '0', MNC: '0', Location area code: '2252', Cell ID: '14C2EF7')
<date>:11:19 <..> ModemManager[717]: <info>  Modem /org/freedesktop/ModemManager1/Modem/0: 3GPP location updated (MCC: '0', MNC: '0', Location area code: '0', Cell ID: '0')
```

I also noticed the word GSM there.

This looks like it can be reproduced with minicom.
```
Initializing Modem
+-----------------------+
                                                    
                                                    
                                                    
                                                    
                                                    
 
Welcome to minicom 2.5
 
OPTIONS: I18n
Compiled on May  2 2011, 10:05:24.
Port /dev/ttyUSB2
 
Press CTRL-A Z for help on special keys
 
AT S7=45 S0=0 L1 V1 X4 &c1 E1 Q0
OK
AT!CDG##GDCONT?
ERROR
AT+S#CD#GDCONT?
+CGDCONT: 1,"IP","telstra.bigpond","0.0.0.0",0,0
+CGDCONT: 15,"IP","telstra.bigpond","0.0.0.0",0,0
+CGDCONT: 16,"IP","telstra.internet","0.0.0.0",0,0
 
OK
AT$QCPDPP?
$QCPDPP: 1,1,"<login name>@bigpond.com"
$QCPDPP: 2,0
$QCPDPP: 3,0
$QCPDPP: 4,0
$QCPDPP: 5,0
$QCPDPP: 6,0
$QCPDPP: 7,0
$QCPDPP: 8,0
$QCPDPP: 9,0
$QCPDPP: 10,0
$QCPDPP: 11,0
$QCPDPP: 12,0
$QCPDPP: 13,0
$QCPDPP: 14,0
$QCPDPP: 15,2,"<login name>@bigpond.com"
$QCPDPP: 16,1,"<login name>"
 
OK
AT!SCACT=1,1
+CME ERROR: no network service
AT!PCINFO?
State: 1 (ONLINE)
LPM force flags - W_DISABLE:0, User:0, Temp:0, Volt:0
W_DISABLE: 0
Poweroff mode: 2
LPM Persistent: 0
 
 
OK
AT!GSTATUS?
!GSTATUS:
Current Time:  4252                Temperature: 26
Bootup Time:   1                     Mode:        ONLINE         
System mode:   WCDMA      PS state:    Attached     
WCDMA band:    WCDMA 800  
WCDMA channel: 4436
GMM (PS) state:REGISTERED        NORMAL SERVICE
MM (CS) state: IDLE             NORMAL SERVICE
 
WCDMA L1 State:L1M_PCH_SLEEP         RRC State:   DISCONNECTED   
RX level Carrier 0 (dBm):-74 LAC:         <..> (<..>)
RX level Carrier 1 (dBm):-106           Cell ID:     <..> (<..>)
 
 
OK

```
Again, I have redacted the login-name and some identifiers in the status.

Whether the password provided is correct has no bearing on the behaviour.

nmlist shows minimal information implying that it recognises the device.
```
- Device: ttyUSB2 --------------------------------------------------------------
  Type:              Mobile Broadband (GSM)
  Driver:            sierra_net, sierra
  State:             disconnected
  Default:           no
 
  Capabilities:
 
 
- Device: eth0 -----------------------------------------------------------------
```

The Bigpond helpdesk suggested reinstalling the driver, but I don't think that they were offering Ubuntu expertise. There is enough information to suggest that Sierra Aircard is recognised to at least some extent. With 12.04 and 14.04 both providing wizards for configuring Telstra 4G wireless broadband, Bigpond appears to be a recognised provider.

The USB-modem was registered with Telstra.

Most of the discussions on the web about using Sierra Aircards with Linux are somewhat out-of-date. [FONT=Times New Roman][SIZE=3][COLOR=#000000]They may describe usb_modeswitch. [/COLOR][/SIZE][/FONT]They often point to C source-code to download for a Sierra driver, but the source is too old for my header-files. This reinforces the idea that the 14.04 distribution is ready for the Sierra Aircard USB-modem.

Are there any more up-to-date fixes for the Aircard? Could I get advice as to further diagnostics or corrections to make?[/FONT]

---

### Post by E._R._Jacobson on 2014-12-17
What I didn't mention in my second-last paragraph is that I found some more recent threads with people asking about connecting to Bigpond 4G with later versions of Ubuntu but never discussion as to how problems connecting might be resolved. This thread has dropped to page 3 without a reply.

If I can't use Bigpond 4G/ Sierra Aircard with Ubuntu, something has to be ditched. I'll also take suggestions as to suitable wireless broadband services in Australia.

---

### Post by E._R._Jacobson on 2015-03-07
I'm still interested in getting this connection working. Not having internet access from this computer makes it hard to research what might be wrong. Australian Government policy means that wireless internet access is the only way that I can hope to get internet access at home.

I am currently interested in this output from the COPS command
```
AT+COPS=?
 
+COPS: (1,"Telstra Mobile","Telstra","50501",2),(1,"Telstra Mobile","Telstra",")
 
OK
AT!BAND=03
 
OK
AT+COPS=?
 
+COPS: (1,"Telstra Mobile","Telstra","50501",2),(3,"vodafone AU","voda AU","505)
 
OK
AT!SELRATE=00
 
OK
AT+COPS=?
 
+COPS: (2,"Telstra","Telstra","50501",2),(1,"Telstra Mobile","Telstra","50501",)
 
OK
AT+CFUN=0
 
OK
AT+CFUN=1
 
OK
AT+COPS=?
 
+COPS: (2,"Telstra","Telstra","50501",2),(1,"Telstra Mobile","Telstra","50501",)
OK
```
It is obviously truncated. I've tried altering Minicom settings but they have no effect. How can I get a non-truncated view of this output?

My first post included these messages.
[code]<date>:11:12 <..> kernel: [10662.690705] sierra_net 3-4:1.7 wwan0: Link type unsupported: 0xff
<date>:11:12 <..> kernel: [10662.690714] sierra_net 3-4:1.7 wwan0: Invalid LSI/code]
Initially I didn't mention them because I read a post elsewhere that these messages do not pose a problem for people who were posting about other problems. However, these messages appear every time that I tried to connect and they make clear that a variable somewhere was not initialised correctly (0xFF being a default link-type when no correct one can be found). What might I need to do to initialise the correct link-type?

---

