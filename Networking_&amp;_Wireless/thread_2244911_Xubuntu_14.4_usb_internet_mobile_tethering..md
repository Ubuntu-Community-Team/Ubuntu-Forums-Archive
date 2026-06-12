---
title: "Xubuntu 14.4 usb internet mobile tethering."
date: 2014-09-19
forum: Networking &amp; Wireless
---

### Post by brunomatti on 2014-09-19
Hi All.    I recently got a Firefox OS mobile.  Now, my old nokia handset was recognised as a mobile internet dongle, and worked with plug and play to get me online, even though this feature was not supported by the handset.    The Firefox OS supports internet tethering by cable, and network manager detects the device, but the option to connect to the internet via tethered mobile if ghosted.    Running ```
ifconfig -a
``` in the terminal gives   the handset as 'usb0' with a hardware address and an internet address.  So My computer knows the device is there, and knows it can use it as to connect to the net.  Any idea how I can activate the option in network manager?  Thanks all!

---

### Post by varunendra on 2014-09-20
Please show us the outputs of -
```
ifconfig -a
lsusb
route -n
nm-tool
```

---

### Post by brunomatti on 2014-09-20
Hi Varunendra.  Thanks for joining in!  Output of the commands are (assuming this gives out no information I should't want on the internet!):

 ```
ifconfig -a
``````
eth0      Link encap:Ethernet  HWaddr 00:1d:09:60:ca:32  
          inet6 addr: fe80::21d:9ff:fe60:ca32/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:59012 errors:0 dropped:0 overruns:0 frame:0
          TX packets:54782 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:66472801 (66.4 MB)  TX bytes:4614065 (4.6 MB)
          Interrupt:16 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:9481 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9481 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1054309 (1.0 MB)  TX bytes:1054309 (1.0 MB)


usb0      Link encap:Ethernet  HWaddr 2a:f7:d6:91:e5:36  
          inet6 addr: fe80::28f7:d6ff:fe91:e536/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:23 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:368 (368.0 B)  TX bytes:6300 (6.3 KB)


wlan0     Link encap:Ethernet  HWaddr 00:1f:3c:54:3b:45  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```


```
lsusb
```
```
Bus 002 Device 004: ID 19d2:1373 ZTE WCDMA Technologies MSM 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```


```
route -n
```
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
```
```
nm-tool
```


```
NetworkManager Tool


State: disconnected


- Device: usb0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            rndis_host
  State:             disconnected
  Default:           no
  HW Address:        2A:F7:D6:91:E5:36


  Capabilities:
    Carrier Detect:  yes


  Wired Properties
    Carrier:         on




- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwl3945
  State:             unavailable
  Default:           no
  HW Address:        00:1F:3C:54:3B:45


  Capabilities:


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points 




- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            sky2
  State:             disconnected
  Default:           no
  HW Address:        00:1D:09:60:CA:32


  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s


  Wired Properties
    Carrier:         on
```

---

### Post by varunendra on 2014-09-23
It doesn't look like it is supposed to work as a mobile broadband dongle. Perhaps it would rather work as a router, that connects to internet by itself, then shares the connection with the connected computer.

Can we see the output of -
```
dmesg | tail -40
```
..when you connect it to the laptop and it starts showing up as "usb0" in ifconfig? Have you tested the mobile with any other OS yet?

---

### Post by brunomatti on 2014-09-23
I have tested it on two computers, but both run Xububtu 14.4.  It doesn't work on either!  Oddly enough,my old Nokia worked perfectly as an internet dongle, despite this not being a supported feature of the phone!

Output of 

```
dmesg | tail -40
```
```
 [   41.283268] <6>[fglrx] IRQ 80 Enabled[   41.297818] <6>[fglrx] Reserved FB block: Shared offset:0, size:1000000 
[   41.297827] <6>[fglrx] Reserved FB block: Unshared offset:fc51000, size:3000 
[   41.297834] <6>[fglrx] Reserved FB block: Unshared offset:fc54000, size:3ac000 
[   41.297840] <6>[fglrx] Reserved FB block: Unshared offset:1ffc8000, size:38000 
[   41.544936] <6>[fglrx] ATIF platform detected with notification ID: 0x81
[   46.983023] init: plymouth-upstart-bridge main process (177) killed by TERM signal
[   53.909627] audit_printk_skb: 51 callbacks suppressed
[   53.909641] type=1400 audit(1411484874.953:53): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=1331 comm="apparmor_parser"
[   53.909665] type=1400 audit(1411484874.953:54): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=1331 comm="apparmor_parser"
[   53.911122] type=1400 audit(1411484874.953:55): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=1331 comm="apparmor_parser"
[  276.753195] usb 5-1: new high-speed USB device number 2 using xhci_hcd
[  276.772391] usb 5-1: New USB device found, idVendor=19d2, idProduct=1351
[  276.772414] usb 5-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[  276.772427] usb 5-1: Product: Handset
[  276.772438] usb 5-1: Manufacturer: Handset
[  276.772448] usb 5-1: SerialNumber: roamer2
[  276.858030] usb-storage 5-1:1.0: USB Mass Storage device detected
[  276.858247] scsi2 : usb-storage 5-1:1.0
[  276.858473] usbcore: registered new interface driver usb-storage
[  277.858481] scsi 2:0:0:0: Direct-Access     Linux    File-CD Gadget   0000 PQ: 0 ANSI: 2
[  277.859610] sd 2:0:0:0: Attached scsi generic sg1 type 0
[  277.862368] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[  298.608514] sd 2:0:0:0: [sdb] 61521920 512-byte logical blocks: (31.4 GB/29.3 GiB)
[  298.609121] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  298.614572]  sdb: sdb1
[  300.321610] FAT-fs (sdb1): Volume was not properly unmounted. Some data may be corrupt. Please run fsck.
[  316.747816] usb 5-1: USB disconnect, device number 2
[  316.776632] sd 2:0:0:0: [sdb] Synchronizing SCSI cache
[  316.776751] sd 2:0:0:0: [sdb]  
[  316.776759] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[  317.056274] usb 5-1: new high-speed USB device number 3 using xhci_hcd
[  317.075388] usb 5-1: New USB device found, idVendor=19d2, idProduct=1373
[  317.075412] usb 5-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[  317.075425] usb 5-1: Product: Handset
[  317.075436] usb 5-1: Manufacturer: Handset
[  317.075446] usb 5-1: SerialNumber: roamer2
[  317.178180] usbcore: registered new interface driver cdc_ether
[  317.192466] rndis_host 5-1:1.0 usb0: register 'rndis_host' at usb-0000:00:10.0-1, RNDIS device, 9e:46:0b:33:fb:96
[  317.193114] usbcore: registered new interface driver rndis_host
```

---

### Post by varunendra on 2014-09-23
I don't have much experience or understanding of these rndis+cdc_ether devices, but it indeed looks like an internet connection sharing device to me.

Your old nokia was working just as a modem used to connect to internet (even my 3 years old cheap karbonn444 can do that via bluetooth). This new device is like an independent system that connects to the internet on its own, then 'Shares' its connection with the other connected device (your computer in this case).

Have you looked into the settings of you mobile phone? Is there something that says or indicates something about connection sharing? Is it enabled?

---

### Post by brunomatti on 2014-09-24
The phone has settings for enabling internet connection sharing -- as detailed [here](https://support.mozilla.org/en-US/kb/share-your-internet-connection#w_share-your-connection-over-usb), though that seems not to have allowed me to actually select the phones internet connection in Xubuntu.

---

### Post by varunendra on 2014-09-24
After turning the connection sharing "on", does the usb0 interface get an IP address? After a usb cable disconnect --> reconnect cycle?

In this mode, I would expect the phone to act as a DHCP server, supplying an IP, Gateway and DNS addresses to the device it is connected via usb. Although I don't know how Network Manager handles these connections.

If that doesn't happen (no IP assignment to 'usb0' interface), could you check and determine what kind of IP range the phone assigns to the connected device? We can try to manually assign one of those addresses and see if you can ping the phone that way.

Sorry for not being able to provide concrete guidelines. Having no experience with such devices, I can only think along the fundamentals I already know.

---

### Post by brunomatti on 2014-09-24
No worries about not knowing the concrete guidelines -- you know more than I do!  I appreciate any help ^_^

The output posted above is after turning teathering 'on', so unfortunately no, usb0 does not seem to get an IP address assigned.  How would I go about checking and determining what kind of IP range the phone assigns to the connected device?

---

### Post by varunendra on 2014-09-24
> **brunomatti said:**
> The output posted above is after turning teathering 'on', so unfortunately no, usb0 does not seem to get an IP address assigned.
Are there any hints in /var/log/syslog? If you can't find any obvious hints, please check some specific terms -
```
egrep -i 'usb0|dhclient|dhcp|network|rndis|cdc_ether' /var/log/syslog
```
..after connecting the USB cable with tethering 'on'. The output of the above might be too long to fit in the terminal. In which case, you can direct it to a file by appending " > (filename)" after the above command, then upload the contents of this file to pastebin and post its link here. You can do the same with entire syslog, but don't expect much at this point.

> How would I go about checking and determining what kind of IP range the phone assigns to the connected device?
Perhaps the OS of the phone has some place to list its current settings and configurations? Categorized or not. In Android phones, many internal settings are visible only in '**Debug**' mode. What we need to see can be easily hidden away from the user since the user is usually not supposed to alter these settings. So the OS may not have a place to display these settings at all, I can't be sure about that.

The only other way to check would be to use this feature with Windows, which almost all vendors make sure to make their products fully compatible with. :|
If it works with Windows, the settings can be checked at its command prompt with the command "ipconfig /all".

---

### Post by Vladlenin5000 on 2014-09-24
In what concerns USB tethering, FirefoxOS seems to work pretty much like Android, ie, it should appear in Ubuntu like a standard LAN (Ethernet) connection.

---

### Post by brunomatti on 2014-09-24
Vladlenin5000, yes it does seem it should work that way.  While the phone appears in Network Manager, it is ghosted out -- not allowing me to select it.  So it appears as a standard LAN, but does not allow me to use it.  

Varunendra, the output of the command you suggested is:

```
 Sep 24 09:54:48 inspiron NetworkManager[938]: <info> Activation (eth0) starting connection 'Wired connection 1'Sep 24 09:54:48 inspiron NetworkManager[938]: <info> (eth0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Sep 24 09:54:48 inspiron NetworkManager[938]: <info> NetworkManager state is now CONNECTING
Sep 24 09:54:48 inspiron NetworkManager[938]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Sep 24 09:54:48 inspiron NetworkManager[938]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Sep 24 09:54:48 inspiron NetworkManager[938]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Sep 24 09:54:48 inspiron NetworkManager[938]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Sep 24 09:54:48 inspiron NetworkManager[938]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Sep 24 09:54:48 inspiron NetworkManager[938]: <info> (eth0): device state change: prepare -> config (reason 'none') [40 50 0]
Sep 24 09:54:48 inspiron NetworkManager[938]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Sep 24 09:54:48 inspiron NetworkManager[938]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Sep 24 09:54:48 inspiron NetworkManager[938]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Sep 24 09:54:48 inspiron NetworkManager[938]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Sep 24 09:54:48 inspiron NetworkManager[938]: <info> (eth0): device state change: config -> ip-config (reason 'none') [50 70 0]
Sep 24 09:54:48 inspiron NetworkManager[938]: <info> Activation (eth0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Sep 24 09:54:49 inspiron NetworkManager[938]: <info> dhclient started with pid 2359
Sep 24 09:54:49 inspiron NetworkManager[938]: <info> Activation (eth0) Beginning IP6 addrconf.
Sep 24 09:54:49 inspiron NetworkManager[938]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Sep 24 09:54:49 inspiron dhclient: Internet Systems Consortium DHCP Client 4.2.4
Sep 24 09:54:49 inspiron dhclient: Copyright 2004-2012 Internet Systems Consortium.
Sep 24 09:54:49 inspiron dhclient: All rights reserved.
Sep 24 09:54:49 inspiron dhclient: For info, please visit https://www.isc.org/software/dhcp/
Sep 24 09:54:49 inspiron dhclient: 
Sep 24 09:54:49 inspiron NetworkManager[938]: <info> (eth0): DHCPv4 state changed nbi -> preinit
Sep 24 09:54:49 inspiron dhclient: Listening on LPF/eth0/00:1d:09:60:ca:32
Sep 24 09:54:49 inspiron dhclient: Sending on   LPF/eth0/00:1d:09:60:ca:32
Sep 24 09:54:49 inspiron dhclient: Sending on   Socket/fallback
Sep 24 09:54:49 inspiron dhclient: DHCPREQUEST of 192.168.1.34 on eth0 to 255.255.255.255 port 67 (xid=0x257a7116)
Sep 24 09:54:49 inspiron dhclient: DHCPACK of 192.168.1.34 from 192.168.1.1
Sep 24 09:54:49 inspiron dhclient: bound to 192.168.1.34 -- renewal in 100909 seconds.
Sep 24 09:54:49 inspiron NetworkManager[938]: <info> (eth0): DHCPv4 state changed preinit -> reboot
Sep 24 09:54:49 inspiron NetworkManager[938]: <info>   address 192.168.1.34
Sep 24 09:54:49 inspiron NetworkManager[938]: <info>   prefix 24 (255.255.255.0)
Sep 24 09:54:49 inspiron NetworkManager[938]: <info>   gateway 192.168.1.1
Sep 24 09:54:49 inspiron NetworkManager[938]: <info>   hostname 'dhcppc1'
Sep 24 09:54:49 inspiron NetworkManager[938]: <info>   nameserver '192.168.1.1'
Sep 24 09:54:49 inspiron NetworkManager[938]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Sep 24 09:54:49 inspiron NetworkManager[938]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Commit) started...
Sep 24 09:54:50 inspiron NetworkManager[938]: <info> (eth0): device state change: ip-config -> secondaries (reason 'none') [70 90 0]
Sep 24 09:54:50 inspiron NetworkManager[938]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Commit) complete.
Sep 24 09:54:50 inspiron NetworkManager[938]: <info> (eth0): device state change: secondaries -> activated (reason 'none') [90 100 0]
Sep 24 09:54:50 inspiron NetworkManager[938]: <info> NetworkManager state is now CONNECTED_GLOBAL
Sep 24 09:54:50 inspiron NetworkManager[938]: <info> Policy set 'Wired connection 1' (eth0) as default for IPv4 routing and DNS.
Sep 24 09:54:50 inspiron NetworkManager[938]: <info> DNS: starting dnsmasq...
Sep 24 09:54:50 inspiron NetworkManager[938]: <warn> dnsmasq not available on the bus, can't update servers.
Sep 24 09:54:50 inspiron NetworkManager[938]: <error> [1411548890.508198] [nm-dns-dnsmasq.c:396] update(): dnsmasq owner not found on bus: Could not get owner of name 'org.freedesktop.NetworkManager.dnsmasq': no such name
Sep 24 09:54:50 inspiron NetworkManager[938]: <warn> DNS: plugin dnsmasq update failed
Sep 24 09:54:50 inspiron NetworkManager[938]: <info> Writing DNS information to /sbin/resolvconf
Sep 24 09:54:50 inspiron dnsmasq[2364]: compile time options: IPv6 GNU-getopt DBus i18n IDN DHCP DHCPv6 no-Lua TFTP conntrack ipset auth
Sep 24 09:54:51 inspiron NetworkManager[938]: <info> Activation (eth0) successful, device activated.
Sep 24 09:54:51 inspiron NetworkManager[938]: <warn> dnsmasq appeared on DBus: :1.67
Sep 24 09:54:51 inspiron NetworkManager[938]: <info> Writing DNS information to /sbin/resolvconf
Sep 24 09:55:09 inspiron NetworkManager[938]: <info> (eth0): IP6 addrconf timed out or failed.
Sep 24 09:55:09 inspiron NetworkManager[938]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Sep 24 09:55:09 inspiron NetworkManager[938]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) started...
Sep 24 09:55:09 inspiron NetworkManager[938]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) complete.
Sep 24 20:24:54 inspiron NetworkManager[938]: <info> (eth0): carrier now OFF (device state 100, deferring action for 4 seconds)
Sep 24 20:24:58 inspiron NetworkManager[938]: <info> (eth0): device state change: activated -> unavailable (reason 'carrier-changed') [100 20 40]
Sep 24 20:24:58 inspiron NetworkManager[938]: <info> (eth0): deactivating device (reason 'carrier-changed') [40]
Sep 24 20:24:59 inspiron NetworkManager[938]: <info> (eth0): canceled DHCP transaction, DHCP client pid 2359
Sep 24 20:24:59 inspiron NetworkManager[938]: <warn> DNS: plugin dnsmasq update failed
Sep 24 20:24:59 inspiron NetworkManager[938]: <info> Removing DNS information from /sbin/resolvconf
Sep 24 20:25:00 inspiron NetworkManager[938]: <info> NetworkManager state is now DISCONNECTED
Sep 24 21:27:16 inspiron NetworkManager[938]: <info> (eth0): carrier now ON (device state 20)
Sep 24 21:27:16 inspiron NetworkManager[938]: <info> (eth0): device state change: unavailable -> disconnected (reason 'carrier-changed') [20 30 40]
Sep 24 21:27:24 inspiron NetworkManager[938]: <info> Activation (eth0) starting connection 'Wired connection 1'
Sep 24 21:27:24 inspiron NetworkManager[938]: <info> (eth0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Sep 24 21:27:24 inspiron NetworkManager[938]: <info> NetworkManager state is now CONNECTING
Sep 24 21:27:24 inspiron NetworkManager[938]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Sep 24 21:27:24 inspiron NetworkManager[938]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Sep 24 21:27:24 inspiron NetworkManager[938]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Sep 24 21:27:24 inspiron NetworkManager[938]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Sep 24 21:27:24 inspiron NetworkManager[938]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Sep 24 21:27:24 inspiron NetworkManager[938]: <info> (eth0): device state change: prepare -> config (reason 'none') [40 50 0]
Sep 24 21:27:24 inspiron NetworkManager[938]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Sep 24 21:27:24 inspiron NetworkManager[938]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Sep 24 21:27:24 inspiron NetworkManager[938]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Sep 24 21:27:24 inspiron NetworkManager[938]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Sep 24 21:27:24 inspiron NetworkManager[938]: <info> (eth0): device state change: config -> ip-config (reason 'none') [50 70 0]
Sep 24 21:27:25 inspiron NetworkManager[938]: <info> Activation (eth0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Sep 24 21:27:25 inspiron NetworkManager[938]: <info> dhclient started with pid 21045
Sep 24 21:27:25 inspiron NetworkManager[938]: <info> Activation (eth0) Beginning IP6 addrconf.
Sep 24 21:27:25 inspiron NetworkManager[938]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Sep 24 21:27:25 inspiron dhclient: Internet Systems Consortium DHCP Client 4.2.4
Sep 24 21:27:25 inspiron dhclient: Copyright 2004-2012 Internet Systems Consortium.
Sep 24 21:27:25 inspiron dhclient: All rights reserved.
Sep 24 21:27:25 inspiron dhclient: For info, please visit https://www.isc.org/software/dhcp/
Sep 24 21:27:25 inspiron dhclient: 
Sep 24 21:27:25 inspiron dhclient: Listening on LPF/eth0/00:1d:09:60:ca:32
Sep 24 21:27:25 inspiron dhclient: Sending on   LPF/eth0/00:1d:09:60:ca:32
Sep 24 21:27:25 inspiron dhclient: Sending on   Socket/fallback
Sep 24 21:27:25 inspiron dhclient: DHCPREQUEST of 192.168.1.34 on eth0 to 255.255.255.255 port 67 (xid=0x26b00267)
Sep 24 21:27:25 inspiron dhclient: DHCPACK of 192.168.1.34 from 192.168.1.1
Sep 24 21:27:25 inspiron NetworkManager[938]: <info> (eth0): DHCPv4 state changed nbi -> preinit
Sep 24 21:27:25 inspiron dhclient: bound to 192.168.1.34 -- renewal in 110824 seconds.
Sep 24 21:27:25 inspiron NetworkManager[938]: <info> (eth0): DHCPv4 state changed preinit -> reboot
Sep 24 21:27:25 inspiron NetworkManager[938]: <info>   address 192.168.1.34
Sep 24 21:27:25 inspiron NetworkManager[938]: <info>   prefix 24 (255.255.255.0)
Sep 24 21:27:25 inspiron NetworkManager[938]: <info>   gateway 192.168.1.1
Sep 24 21:27:25 inspiron NetworkManager[938]: <info>   hostname 'dhcppc1'
Sep 24 21:27:25 inspiron NetworkManager[938]: <info>   nameserver '192.168.1.1'
Sep 24 21:27:25 inspiron NetworkManager[938]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Sep 24 21:27:25 inspiron NetworkManager[938]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Commit) started...
Sep 24 21:27:26 inspiron NetworkManager[938]: <info> (eth0): device state change: ip-config -> secondaries (reason 'none') [70 90 0]
Sep 24 21:27:26 inspiron NetworkManager[938]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Commit) complete.
Sep 24 21:27:26 inspiron NetworkManager[938]: <info> (eth0): device state change: secondaries -> activated (reason 'none') [90 100 0]
Sep 24 21:27:26 inspiron NetworkManager[938]: <info> NetworkManager state is now CONNECTED_GLOBAL
Sep 24 21:27:26 inspiron NetworkManager[938]: <info> Policy set 'Wired connection 1' (eth0) as default for IPv4 routing and DNS.
Sep 24 21:27:26 inspiron NetworkManager[938]: <info> Writing DNS information to /sbin/resolvconf
Sep 24 21:27:27 inspiron NetworkManager[938]: <info> Activation (eth0) successful, device activated.
Sep 24 21:27:45 inspiron NetworkManager[938]: <info> (eth0): IP6 addrconf timed out or failed.
Sep 24 21:27:45 inspiron NetworkManager[938]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Sep 24 21:27:45 inspiron NetworkManager[938]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) started...
Sep 24 21:27:45 inspiron NetworkManager[938]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) complete.
Sep 24 23:11:48 inspiron kernel: [51205.673444] usbcore: registered new interface driver cdc_ether
Sep 24 23:11:48 inspiron kernel: [51205.682178] rndis_host 2-4:1.0 usb0: register 'rndis_host' at usb-0000:00:1d.7-4, RNDIS device, b6:fb:5c:29:78:90
Sep 24 23:11:48 inspiron kernel: [51205.682223] usbcore: registered new interface driver rndis_host
Sep 24 23:11:48 inspiron NetworkManager[938]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1d.7/usb2/2-4/2-4:1.0/net/usb0, iface: usb0)
Sep 24 23:11:48 inspiron NetworkManager[938]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1d.7/usb2/2-4/2-4:1.0/net/usb0, iface: usb0): no ifupdown configuration found.
Sep 24 23:11:48 inspiron NetworkManager[938]: <warn> failed to allocate link cache: (-12) Object not found
Sep 24 23:11:48 inspiron NetworkManager[938]: <info> (usb0): carrier is OFF
Sep 24 23:11:48 inspiron NetworkManager[938]: <info> (usb0): new Ethernet device (driver: 'rndis_host' ifindex: 4)
Sep 24 23:11:48 inspiron NetworkManager[938]: <info> (usb0): exported as /org/freedesktop/NetworkManager/Devices/2
Sep 24 23:11:49 inspiron NetworkManager[938]: <info> (usb0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Sep 24 23:11:49 inspiron NetworkManager[938]: <info> (usb0): bringing up device.
Sep 24 23:11:49 inspiron NetworkManager[938]: <info> (usb0): carrier now ON (device state 20)
Sep 24 23:11:49 inspiron NetworkManager[938]: <info> (usb0): preparing device.
Sep 24 23:11:49 inspiron NetworkManager[938]: <info> (usb0): deactivating device (reason 'managed') [2]
Sep 24 23:11:49 inspiron NetworkManager[938]: <info> (usb0): device state change: unavailable -> disconnected (reason 'none') [20 30 0]
Sep 24 23:11:50 inspiron avahi-daemon[516]: Joining mDNS multicast group on interface usb0.IPv6 with address fe80::b4fb:5cff:fe29:7890.
Sep 24 23:11:50 inspiron avahi-daemon[516]: New relevant interface usb0.IPv6 for mDNS.
Sep 24 23:11:50 inspiron avahi-daemon[516]: Registering new address record for fe80::b4fb:5cff:fe29:7890 on usb0.*.
Sep 24 23:11:55 inspiron NetworkManager[938]: <info> (eth0): device state change: activated -> disconnected (reason 'user-requested') [100 30 39]
Sep 24 23:11:55 inspiron NetworkManager[938]: <info> (eth0): deactivating device (reason 'user-requested') [39]
Sep 24 23:11:55 inspiron NetworkManager[938]: <info> (eth0): canceled DHCP transaction, DHCP client pid 21045
Sep 24 23:11:55 inspiron NetworkManager[938]: <warn> DNS: plugin dnsmasq update failed
Sep 24 23:11:55 inspiron NetworkManager[938]: <info> Removing DNS information from /sbin/resolvconf
Sep 24 23:11:55 inspiron NetworkManager[938]: <info> NetworkManager state is now DISCONNECTED
Sep 24 23:11:59 inspiron NetworkManager[938]: <info> (eth0): carrier now OFF (device state 30)
Sep 24 23:11:59 inspiron NetworkManager[938]: <info> (eth0): device state change: disconnected -> unavailable (reason 'carrier-changed') [30 20 40]
Sep 24 23:11:59 inspiron NetworkManager[938]: <info> (eth0): deactivating device (reason 'carrier-changed') [40]
```

I disconnected from the regular LAN cable before plugging the phone and seeing if it'll connect there.  If you want me to check some specific terms, I am afraid I'd need some guidance there too -- what terms to put in, and how to drop them into the command you suggested (unless that command was already the specific terms... in which case sorry for being a bit slow!). 

I'll investigate a debug mode and see if I can ge in somehow, and will see if I can track down a Windows machine to check settings there.

---

### Post by varunendra on 2014-09-24
Is the "usb0" interface mentioned in your /etc/network/interfaces file? If yes, please remove any lines you have added for it, or comment them out. Ideally, if you are using Network Manager for everything, the 'interfaces' file should have only two lines in it -
```
auto lo
iface lo inet loopback

```

If this file is already like this, then I must be missing or unaware of something about rndis/cdc_ether devices that prevents NM from taking control of it. But try this for now if the 'interfaces' file is already at defaults -
```
sudo sed -i 's/^managed=false/managed=true/' /etc/NetworkManager/NetworkManager.conf
```
This will change the value of "managed=" from 'false' to 'true' in NetworkManager.conf file. You may need to disable/re-enable NM for the change to take effect (or simply rebot).

Does this activate the 'usb0' interface in NM?

And yes, the command I suggested in my earlier post already contained the 'specific terms' I was hoping to see some clue with. I did get some - the thing seems to be working as expected, only doesn't complete the configuration steps. There seem to be no errors, just doesn't complete a few more steps, unless the relevant messages have been missed out due to the 'specific-term-filters' in the command.

---

### Post by brunomatti on 2014-09-27
Hi again.  Sorry for the slow response -- it's been a mad busy week!  

Indeed my /etc/network/interfaces file was still as the  default you slit above.  I tried the new command you give and restarted network manager, but alas no joy.  Still ghosted in the task bar.  It sounds promising though, that we now know it jsut isn't finishing auto-configuring...?

---

### Post by varunendra on 2014-09-28
Without further hints, I'm afraid I may not be able to suggest much options now. But based on another close observation of the syslog snippets you posted -
```
Sep 24 23:11:49 inspiron NetworkManager[938]: <info> (usb0): preparing device.
Sep 24 23:11:49 inspiron NetworkManager[938]: <info> (usb0): deactivating device (reason 'managed') [2]
Sep 24 **23:11:49** inspiron NetworkManager[938]: <info> **(usb0): device state change: unavailable -> disconnected** (reason 'none') [20 30 0]
....<snip>...
Sep 24 **[COLOR="#FF0000"]23:11:55[/COLOR]** inspiron NetworkManager[938]: <info> **(eth0): device state change: activated -> disconnected** (reason 'user-requested') [100 30 39]
```
Even if you disconnected the ethernet cable before connecting the phone, it seems the system detected the disconnection AFTER connecting and failing to configure the 'usb0' connection. As such, I recommend trying that again, preferably keeping the Ethernet cable unplugged from the start, that is, from booting.

Another thought based on the recurrence of these -
```
Sep 24 23:11:55 inspiron NetworkManager[938]: <warn> DNS: **plugin dnsmasq** update failed
```
.... and the information on the [wiki-page]("https://help.ubuntu.com/community/Dnsmasq") about dnsmasq -
> Note that the package **"dnsmasq" interferes with Network Manager** which can use "dnsmasq-base" to provide DHCP services when sharing an internet connection. Therefore,** if you use network manager (fine in simple set-ups only), then install dnsmasq-base, but not dnsmasq.**
Accordingly, please check whether you have only dnsmasq-base installed or 'dnsmasq' too -
```
dpkg -l | grep dnsmasq
```
On my system here it returns only 'dnsmasq-base' -
```
ii  dnsmasq-base                                  2.59-4                                  Small caching DNS proxy and DHCP/TFTP server
```
The "ii" in the beginning means "installed". If the package "dnsmasq" also seems to be installed, please try purging it -
```
sudo apt-get purge dnsmasq
```
..then try the phone connection again, reboot if immediate attempt fails again, and let us know if there is any difference/success.

Beyond this, I'm afraid I don't know what else to try. Maybe a full syslog could shed some more light on this, or someone with more knowledge about 'cdc_ether' devices could.

---

### Post by brunomatti on 2014-10-04
Hi Again.  Sorry I'm slow replying -- it's been a busy week!  I tried booting with the mobile tethering plugged in and active, but still no dice.  It's still ghosted in network manager.

Do we have anything else we can try, or are we stumped?

---

### Post by Vladlenin5000 on 2014-10-04
It was recommended to boot without the Ethernet cable... Have you tried that?

---

### Post by varunendra on 2014-10-04
> **Vladlenin5000 said:**
> It was recommended to boot without the Ethernet cable... Have you tried that?

This ^^.
Plus, you did not confirm the state of dnsmasq packages. Did you check that? Is only dnsmasq-base installed or 'dnsmasq' too?

Just post the output of -
```
dpkg -l | grep dnsmasq
```
..if not sure.

---

