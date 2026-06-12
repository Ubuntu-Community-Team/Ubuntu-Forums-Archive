---
title: "Unable to connect with WPA"
date: 2008-08-09
forum: Networking &amp; Wireless
---

### Post by kramer2718 on 2008-08-09
Hi guys.  I got ndiswrapper to work on this obscure usb wireless device.  Then I used knetworkmanager to connect to an unencrypted network, but really want to use wpa, because it's the only one that's secure and knetworkmanager just hangs.  So I thought that I would connect manually and maybe get the GUI to work later.

Anyway, I'm following these instructions:

[http://ubuntuforums.org/showthread.php?t=684495](http://ubuntuforums.org/showthread.php?t=684495)

In particular, I'm following the standard WPA 1 instructions.

I've already got wpasupplicant, etc .. installed.


I've set up the /etc/wpa_supplicant as instructed but get stuck here:

[FONT="Courier New"]$ sudo dhclient -r eth1
There is already a pid file /var/run/dhclient.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:17:3f:1f:29:8f
Sending on LPF/eth1/00:17:3f:1f:29:8f
Sending on Socket/fallback
DHCPRELEASE on eth1 to 192.168.2.1 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.
[/FONT]

And then here:

[FONT="Courier New"]$ sudo wpa_supplicant -dd -w -D wext -i eth1 -c /etc/wpa_supplicant
Initializing interface 'eth1' conf '/etc/wpa_supplicant' driver 'wext' ctrl_interface 'N/A' bridge 'N/A'
Configuration file '/etc/wpa_supplicant' -> '/etc/wpa_supplicant'
Reading configuration file '/etc/wpa_supplicant'
Initializing interface (2) 'eth1'
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
SIOCGIWRANGE: WE(compiled)=22 WE(source)=20 enc_capa=0xf
capabilities: key_mgmt 0xf enc 0xf
WEXT: Operstate: linkmode=1, operstate=5
Own MAC address: 00:17:3f:1f:29:8f
wpa_driver_wext_set_wpa
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_countermeasures
wpa_driver_wext_set_drop_unencrypted
Setting scan request: 0 sec 100000 usec
Added interface eth1
RTM_NEWLINK: operstate=0 ifi_flags=0x1002 ()
Wireless event: cmd=0x8b06 len=8
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'eth1' added
State: DISCONNECTED -> SCANNING
Starting AP scan (broadcast SSID)
Trying to get current scan results first without requesting a new scan to speed up initial association
Received 297 bytes of scan results (1 BSSes)
Scan results: 1
No suitable AP found.
Setting scan request: 0 sec 0 usec
No enabled networks - do not scan
State: SCANNING -> INACTIVE[/FONT]


And then it hangs...

Any help would be very much appreciated, guys.

---

### Post by jualin on 2008-08-16
Hi and welcome to Ubuntu! Can you please tell us how exactly did you install your wireless driver using Ndiswrapper?

---

### Post by kramer2718 on 2008-08-16
Sure.  I downloaded the driver from the manufacturer's website (Ativa).  I copied it to the Ubuntu box and did 

ndiswrapper -i odwgu.inf

(that was the only .inf file that came with the driver).

The wireless then seemed to work.  I got it connected by turning off encryption (knetworkmanager seemed to work fine).  I confirmed that the wireless adaptor was compatible with wpa by installing it on my windows machine.

Is it possible that the driver is trying to handle the WPA and clashing with WPA supplicant?  When I installed the driver on my Windows box, it seemed to have its own fancy WPA GUI...

---

### Post by jualin on 2008-08-16
Can you go to the terminal and type > lsusb Also, can you tell us the brand and Model of your wireless adapter?

---

### Post by tl3000 on 2008-08-16
> **kramer2718 said:**
> Hi guys.  I got ndiswrapper to work on this obscure usb wireless device.  Then I used knetworkmanager to connect to an unencrypted network, but really want to use wpa, because it's the only one that's secure and knetworkmanager just hangs.

[ ... snipped for brevity ... ]

Any help would be very much appreciated, guys.

Checkout the following bug report, and if your situation is similar then try the workaround recently posted near the end of the thread:

[https://bugs.launchpad.net/ubuntu/+source/wpasupplicant/+bug/207446](https://bugs.launchpad.net/ubuntu/+source/wpasupplicant/+bug/207446)

---

### Post by kramer2718 on 2008-08-16
Sure.  It is an ativa wireless-g usb network adaptor.

lsusb shows:
Bus 002 Device 002: ID 05d:705c Belkin Components
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 003: ID 03f0:020c Hewlett-Packard Multimedia Keyboard
Bus 001 Device 002: ID 03f0:010c Hewlett-Packard Multimedia Keyboard Hub
Bus 001 Device 001: ID 0000:0000

---

### Post by kramer2718 on 2008-08-20
> **tl3000 said:**
> Checkout the following bug report, and if your situation is similar then try the workaround recently posted near the end of the thread:

[https://bugs.launchpad.net/ubuntu/+source/wpasupplicant/+bug/207446](https://bugs.launchpad.net/ubuntu/+source/wpasupplicant/+bug/207446)


I had a look at that bug report.  I looked at the work around running wpasupplicant with a low nice value.

Tried that.  Didn't work.... Got the same error.  Haven't had time to try switching kernels ... seems like a drastic painful solution.  Unless there is an easy way to do that?

Very very frustrating ... may have to buy a supported card.

This is why Linux will struggle against Windblowz for the time being.  Still can't blame Linux.  Can blame stupid hardware manufacturers that don't open their specs.

Can someone please confirm that WPA

---

