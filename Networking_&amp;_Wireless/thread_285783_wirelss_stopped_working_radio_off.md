---
title: "wirelss stopped working: radio off"
date: 2006-10-27
forum: Networking &amp; Wireless
---

### Post by attilia on 2006-10-27
Dear all, :) 

I am a kubuntu 6.06 user on an Acer travelmate 660.
I used to surf the web quite nicely with my wireless card, until one day wlanassistant told me that the "radio" of my card was off, and if I wanted it to be turned on. Choosing "yes" the same old list of networks appears, but it cannot connect to any, let alone mine.

I will be grateful for any help, from small hints to - of course - ready-packed solutions!

I hacked a bit on iwconfig, and it appears it cannot SET the txpower to on. Here is the log of my iwscan and of me running iwconfig txpower on and wlassistant:

root@celestina:~# iwconfig eth1
eth1      IEEE 802.11b  ESSID:"Wifi_Erasmus"  Nickname:"ipw2100"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:19:07:94:85:40
          Bit Rate=2 Mb/s   Tx-Power:off
          Retry limit:16   RTS thr:off   Fragment thr:off
          Encryption key:3030-3030-3030-3030-3030-6161-61   Security mode:open
          Power Management:off
          Link Quality=68/100  Signal level=-81 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:16   Missed beacon:4


IF I try to set txpower (and the radio) to on:

root@celestina:~# iwconfig eth1 txpower on
Error for wireless request "Set Tx Power" (8B26) :
    SET failed on device eth1 ; Invalid argument.
root@celestina:~# iwconfig eth1 txpower auto
Error for wireless request "Set Tx Power" (8B26) :
    SET failed on device eth1 ; Invalid argument.


SO I try to run wlanassistant:

root@celestina:~# wlassistant
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
ScimInputContextPlugin()
kdecore (KConfigSkeleton): Creating KConfigSkeleton (0x8169d18)
kdecore (KConfigSkeleton): KConfigSkeleton::readConfig()
kdecore (KConfigSkeleton): KConfigSkeleton::readConfig()
Loaded application options.
DHCP Client: dhclient
All executables found.
iwconfig_status: /sbin/iwconfig
==>stderr: lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

Wireless interface(s): eth1
Permissions checked.
radio_on: /sbin/iwconfig eth1 txpower auto
==>stderr: Error for wireless request "Set Tx Power" (8B26) :
    SET failed on device eth1 ; Invalid argument.
ifconfig_status: /sbin/ifconfig eth1
scan: /sbin/iwlist eth1 scan
Networks found: 7
Checking for active connection.
Trying to get gateway address...
...from /var/lib/dhcp3/dhclient.leases
Gateway address: 192.168.1.254
Checking for active connection.
Checking for active connection.
Checking for active connection.
Checking for active connection.


...and it goes on like this without any specific reason.

ANOTHER try:

radio_on: /sbin/iwconfig eth1 txpower auto
==>stderr: Error for wireless request "Set Tx Power" (8B26) :
    SET failed on device eth1 ; Invalid argument.
ifconfig_status: /sbin/ifconfig eth1
scan: /sbin/iwlist eth1 scan
Networks found: 5
Checking for active connection.
ACTION: CONNECT.
kdecore (KConfigSkeleton): KConfigSkeleton::writeConfig()
kdecore (KConfigSkeleton): KConfigSkeleton::readConfig()
Network settings updated.
kill_dhcp: /sbin/dhclient -r eth1
==>stderr: Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth1/00:04:23:84:30:15
Sending on   LPF/eth1/00:04:23:84:30:15
Sending on   Socket/fallback
DHCPRELEASE on eth1 to 192.168.1.254 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.
ifup: /sbin/ifconfig eth1 up
iwconfig_set: /sbin/iwconfig eth1 mode managed channel 6 key open 0000000000aaaaaaaaa111bbb2 essid touwslagerflat
==>stderr: Error for wireless request "Set Frequency" (8B04) :
    SET failed on device eth1 ; Operation not supported.
iwconfig_ap: /sbin/iwconfig eth1 ap 00:17:DF:97:1A:B0
ifconfig_dhcp: /sbin/dhclient -q eth1
kill_dhcp: /sbin/dhclient -r eth1
==>stderr: Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth1/00:04:23:84:30:15
Sending on   LPF/eth1/00:04:23:84:30:15
Sending on   Socket/fallback
DHCPRELEASE on eth1 to 192.168.1.254 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.
CONNECTION FAILED.
Checking for active connection.
Checking for active connection.

---

