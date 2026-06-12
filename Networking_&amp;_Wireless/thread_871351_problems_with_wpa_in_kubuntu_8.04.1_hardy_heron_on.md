---
title: "problems with wpa in kubuntu 8.04.1 hardy heron on hp dv2945"
date: 2008-07-26
forum: Networking &amp; Wireless
---

### Post by Atheossapiens on 2008-07-26
I am running kubuntu on an hp pavillion 2945. I have the broadcom 4310 wifi
card working with the wl driver. I am able to connect to my, and others,
access points only if they are unsecured. I turned off my security (WPA)
on my router, a westell versalink 327w15, and was able to connect to it
but when I turn my security back on, either WPA or WEP, I am no longer
able to connect. It reaches the point of "IP configuration started" at
which point it fails with "Could not connect to the network..." I use the
knetworkmanager.

here are the relevant lines in by syslog

------------------------------------------------------------------------------------------------------------------------------------

Jul 11 18:03:49 atheossapiens-laptop NetworkManager: <debug>
[1215813829.160789] nm_device_802_11_wireless_get_activation_ap(): Forcing
AP '07B408687936'
Jul 11 18:03:49 atheossapiens-laptop NetworkManager: <info>  User Switch:
/org/freedesktop/NetworkManager/Devices/eth1 / 07B408687936
Jul 11 18:03:49 atheossapiens-laptop NetworkManager: <info>  Deactivating
device eth1.
Jul 11 18:03:49 atheossapiens-laptop NetworkManager: <WARN>
nm_device_802_11_wireless_set_wep_enc_key(): error setting key for device
eth1: Invalid argument
Jul 11 18:03:49 atheossapiens-laptop NetworkManager: <info>  Device eth1
activation scheduled...
Jul 11 18:03:49 atheossapiens-laptop NetworkManager: <info>  Deactivating
device eth0.
Jul 11 18:03:49 atheossapiens-laptop dhclient: There is already a pid file
/var/run/dhclient.eth0.pid with pid 6337
Jul 11 18:03:49 atheossapiens-laptop dhclient: killed old client process,
removed PID file
Jul 11 18:03:49 atheossapiens-laptop dhclient: DHCPRELEASE on eth0 to
192.168.1.1 port 67
Jul 11 18:03:49 atheossapiens-laptop avahi-daemon[5348]: Withdrawing
address record for 192.168.1.42 on eth0.
Jul 11 18:03:49 atheossapiens-laptop avahi-daemon[5348]: Leaving mDNS
multicast group on interface eth0.IPv4 with address 192.168.1.42.
Jul 11 18:03:49 atheossapiens-laptop avahi-daemon[5348]: Interface
eth0.IPv4 no longer relevant for mDNS.
Jul 11 18:03:50 atheossapiens-laptop avahi-daemon[5348]: Withdrawing
address record for fe80::21d:72ff:fe5d:fd80 on eth0.
Jul 11 18:03:50 atheossapiens-laptop NetworkManager: <info>  Activation
(eth1) started...
Jul 11 18:03:50 atheossapiens-laptop NetworkManager: <info>  Activation
(eth1) Stage 1 of 5 (Device Prepare) scheduled...
Jul 11 18:03:50 atheossapiens-laptop NetworkManager: <info>  Activation
(eth1) Stage 1 of 5 (Device Prepare) started...
Jul 11 18:03:50 atheossapiens-laptop NetworkManager: <info>  Activation
(eth1) Stage 2 of 5 (Device Configure) scheduled...
Jul 11 18:03:50 atheossapiens-laptop NetworkManager: <info>  Activation
(eth1) Stage 1 of 5 (Device Prepare) complete.
Jul 11 18:03:50 atheossapiens-laptop NetworkManager: <info>  Activation
(eth1) Stage 2 of 5 (Device Configure) starting...
Jul 11 18:03:50 atheossapiens-laptop NetworkManager: <info>  Activation
(eth1/wireless): access point '07B408687936' is encrypted, and a key
exists.  No new key needed.
Jul 11 18:03:50 atheossapiens-laptop NetworkManager: <info>  Old device
'eth1' activating, won't change.
Jul 11 18:03:51 atheossapiens-laptop NetworkManager: <info>  retry to
connect to global supplicant socket (try=1)
Jul 11 18:03:51 atheossapiens-laptop NetworkManager: <info>  SUP: sending
command 'INTERFACE_ADD eth1^I^Iwext^I/var/run/wpa_supplicant0^I'
Jul 11 18:03:51 atheossapiens-laptop NetworkManager: <info>  SUP: response
was 'OK'
Jul 11 18:03:52 atheossapiens-laptop NetworkManager: <info>  SUP: sending
command 'AP_SCAN 1'
Jul 11 18:03:52 atheossapiens-laptop NetworkManager: <info>  SUP: response
was 'OK'
Jul 11 18:03:52 atheossapiens-laptop NetworkManager: <info>  SUP: sending
command 'ADD_NETWORK'
Jul 11 18:03:52 atheossapiens-laptop NetworkManager: <info>  SUP: response
was '0'
Jul 11 18:03:52 atheossapiens-laptop NetworkManager: <info>  SUP: sending
command 'SET_NETWORK 0 ssid 303742343038363837393336'
Jul 11 18:03:52 atheossapiens-laptop NetworkManager: <info>  SUP: response
was 'OK'
Jul 11 18:03:52 atheossapiens-laptop NetworkManager: <info>  SUP: sending
command 'SET_NETWORK 0 proto WPA'
Jul 11 18:03:52 atheossapiens-laptop NetworkManager: <info>  SUP: response
was 'OK'
Jul 11 18:03:52 atheossapiens-laptop NetworkManager: <info>  SUP: sending
command 'SET_NETWORK 0 key_mgmt WPA-PSK'
Jul 11 18:03:52 atheossapiens-laptop NetworkManager: <info>  SUP: response
was 'OK'
Jul 11 18:03:52 atheossapiens-laptop NetworkManager: <info>  SUP: sending
command 'SET_NETWORK 0 psk <key>'
Jul 11 18:03:52 atheossapiens-laptop NetworkManager: <info>  SUP: response
was 'OK'
Jul 11 18:03:52 atheossapiens-laptop NetworkManager: <info>  SUP: sending
command 'ENABLE_NETWORK 0'
Jul 11 18:03:52 atheossapiens-laptop NetworkManager: <info>  SUP: response
was 'OK'
Jul 11 18:03:52 atheossapiens-laptop NetworkManager: <info>  Activation
(eth1) Stage 2 of 5 (Device Configure) complete.
Jul 11 18:03:52 atheossapiens-laptop NetworkManager: <info>  Supplicant
state changed: 0
Jul 11 18:04:00 atheossapiens-laptop NetworkManager: <info>  Supplicant
state changed: 1
Jul 11 18:04:00 atheossapiens-laptop NetworkManager: <info>  Activation
(eth1/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to
access point '07B408687936'.
Jul 11 18:04:00 atheossapiens-laptop NetworkManager: <info>  Activation
(eth1) Stage 3 of 5 (IP Configure Start) scheduled.
Jul 11 18:04:00 atheossapiens-laptop NetworkManager: <info>  Activation
(eth1) Stage 3 of 5 (IP Configure Start) started...
Jul 11 18:04:00 atheossapiens-laptop kernel: [  291.368518]
ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
Jul 11 18:04:01 atheossapiens-laptop avahi-daemon[5348]: Registering new
address record for fe80::221:ff:fe26:a6ba on eth1.*.
Jul 11 18:04:02 atheossapiens-laptop NetworkManager: <info>  Activation
(eth1) Beginning DHCP transaction.
Jul 11 18:04:02 atheossapiens-laptop NetworkManager: <info>  Activation
(eth1) Stage 3 of 5 (IP Configure Start) complete.
Jul 11 18:04:02 atheossapiens-laptop NetworkManager: <info>  DHCP daemon
state is now 12 (successfully started) for interface eth1
Jul 11 18:04:02 atheossapiens-laptop avahi-autoipd(eth1)[6297]: Got
SIGTERM, quitting.
Jul 11 18:04:02 atheossapiens-laptop avahi-autoipd(eth1)[6297]: Callout
STOP, address 169.254.6.206 on interface eth1
Jul 11 18:04:02 atheossapiens-laptop avahi-autoipd(eth1)[6298]: client:
RTNETLINK answers: Cannot assign requested address
Jul 11 18:04:02 atheossapiens-laptop avahi-autoipd(eth1)[6298]: Script
execution failed with return value 2
Jul 11 18:04:03 atheossapiens-laptop NetworkManager: <info>  DHCP daemon
state is now 1 (starting) for interface eth1
Jul 11 18:04:04 atheossapiens-laptop dhclient: DHCPDISCOVER on eth1 to
255.255.255.255 port 67 interval 4
Jul 11 18:04:08 atheossapiens-laptop dhclient: DHCPDISCOVER on eth1 to
255.255.255.255 port 67 interval 5
Jul 11 18:04:08 atheossapiens-laptop NetworkManager: <info>  Supplicant
state changed: 0
Jul 11 18:04:10 atheossapiens-laptop kernel: [  295.436989] eth1: no IPv6
routers present
Jul 11 18:04:12 atheossapiens-laptop NetworkManager: <info>  Supplicant
state changed: 1
Jul 11 18:04:13 atheossapiens-laptop dhclient: DHCPDISCOVER on eth1 to
255.255.255.255 port 67 interval 6
Jul 11 18:04:19 atheossapiens-laptop dhclient: DHCPDISCOVER on eth1 to
255.255.255.255 port 67 interval 15
Jul 11 18:04:20 atheossapiens-laptop NetworkManager: <info>  Supplicant
state changed: 0
Jul 11 18:04:24 atheossapiens-laptop NetworkManager: <info>  Supplicant
state changed: 1
Jul 11 18:04:32 atheossapiens-laptop NetworkManager: <info>  Supplicant
state changed: 0
Jul 11 18:04:34 atheossapiens-laptop dhclient: DHCPDISCOVER on eth1 to
255.255.255.255 port 67 interval 1
Jul 11 18:04:35 atheossapiens-laptop dhclient: No DHCPOFFERS received.
Jul 11 18:04:35 atheossapiens-laptop avahi-autoipd(eth1)[6717]: Found user
'avahi-autoipd' (UID 105) and group 'avahi-autoipd' (GID 113).
Jul 11 18:04:35 atheossapiens-laptop avahi-autoipd(eth1)[6717]:
Successfully called chroot().
Jul 11 18:04:35 atheossapiens-laptop avahi-autoipd(eth1)[6717]:
Successfully dropped root privileges.
Jul 11 18:04:35 atheossapiens-laptop avahi-autoipd(eth1)[6717]: Starting
with address 169.254.6.206
Jul 11 18:04:36 atheossapiens-laptop NetworkManager: <info>  Supplicant
state changed: 1
Jul 11 18:04:40 atheossapiens-laptop avahi-autoipd(eth1)[6717]: Callout
BIND, address 169.254.6.206 on interface eth1
Jul 11 18:04:40 atheossapiens-laptop avahi-daemon[5348]: Joining mDNS
multicast group on interface eth1.IPv4 with address 169.254.6.206.
Jul 11 18:04:40 atheossapiens-laptop avahi-daemon[5348]: New relevant
interface eth1.IPv4 for mDNS.
Jul 11 18:04:40 atheossapiens-laptop avahi-daemon[5348]: Registering new
address record for 169.254.6.206 on eth1.IPv4.
Jul 11 18:04:44 atheossapiens-laptop NetworkManager: <info>  Supplicant
state changed: 0
Jul 11 18:04:44 atheossapiens-laptop avahi-autoipd(eth1)[6717]:
Successfully claimed IP address 169.254.6.206
Jul 11 18:04:44 atheossapiens-laptop NetworkManager: <info>  DHCP daemon
state is now 9 (fail) for interface eth1
Jul 11 18:04:44 atheossapiens-laptop NetworkManager: <info>  Activation
(eth1) Stage 4 of 5 (IP Configure Timeout) scheduled...
Jul 11 18:04:44 atheossapiens-laptop NetworkManager: <info>  Activation
(eth1) Stage 4 of 5 (IP Configure Timeout) started...
Jul 11 18:04:44 atheossapiens-laptop NetworkManager: <info>  Activation
(eth1) failure scheduled...
Jul 11 18:04:44 atheossapiens-laptop NetworkManager: <info>  Activation
(eth1) Stage 4 of 5 (IP Configure Timeout) complete.
Jul 11 18:04:44 atheossapiens-laptop dhcdbd: Unrequested down ?:3
Jul 11 18:04:44 atheossapiens-laptop NetworkManager: <info>  DHCP daemon
state is now 14 (normal exit) for interface eth1
Jul 11 18:04:44 atheossapiens-laptop NetworkManager: <info>  Activation
(eth1) failed for access point (07B408687936)
Jul 11 18:04:44 atheossapiens-laptop NetworkManager: <info>  Activation
(eth1) failed.
Jul 11 18:04:44 atheossapiens-laptop NetworkManager: <info>  Deactivating
device eth1.
Jul 11 18:04:44 atheossapiens-laptop avahi-daemon[5348]: Withdrawing
address record for 169.254.6.206 on eth1.
Jul 11 18:04:44 atheossapiens-laptop avahi-daemon[5348]: Leaving mDNS
multicast group on interface eth1.IPv4 with address 169.254.6.206.
Jul 11 18:04:44 atheossapiens-laptop avahi-daemon[5348]: Interface
eth1.IPv4 no longer relevant for mDNS.
Jul 11 18:04:44 atheossapiens-laptop avahi-daemon[5348]: Withdrawing
address record for fe80::221:ff:fe26:a6ba on eth1.
Jul 11 18:04:44 atheossapiens-laptop NetworkManager: <WARN>
nm_device_802_11_wireless_set_wep_enc_key(): error setting key for device
eth1: Invalid argument
Jul 11 18:04:44 atheossapiens-laptop NetworkManager: <info>  SWITCH: no
current connection, found better connection 'eth0'.
Jul 11 18:04:44 atheossapiens-laptop NetworkManager: <info>  Will activate
connection 'eth0'.
Jul 11 18:04:44 atheossapiens-laptop NetworkManager: <info>  Device eth0
activation scheduled...
Jul 11 18:04:44 atheossapiens-laptop NetworkManager: <info>  Activation
(eth0) started...
Jul 11 18:04:44 atheossapiens-laptop NetworkManager: <info>  Activation
(eth0) Stage 1 of 5 (Device Prepare) scheduled...
Jul 11 18:04:44 atheossapiens-laptop NetworkManager: <info>  Activation
(eth0) Stage 1 of 5 (Device Prepare) started...
Jul 11 18:04:44 atheossapiens-laptop NetworkManager: <info>  Activation
(eth0) Stage 2 of 5 (Device Configure) scheduled...
Jul 11 18:04:44 atheossapiens-laptop NetworkManager: <info>  Activation
(eth0) Stage 1 of 5 (Device Prepare) complete.
Jul 11 18:04:44 atheossapiens-laptop NetworkManager: <info>  Activation
(eth0) Stage 2 of 5 (Device Configure) starting...
Jul 11 18:04:44 atheossapiens-laptop NetworkManager: <info>  Activation
(eth0) Stage 2 of 5 (Device Configure) successful.
Jul 11 18:04:44 atheossapiens-laptop NetworkManager: <info>  Activation
(eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Jul 11 18:04:44 atheossapiens-laptop NetworkManager: <info>  Activation
(eth0) Stage 2 of 5 (Device Configure) complete.
Jul 11 18:04:44 atheossapiens-laptop NetworkManager: <info>  Activation
(eth0) Stage 3 of 5 (IP Configure Start) started...
Jul 11 18:04:45 atheossapiens-laptop NetworkManager: <info>  Activation
(eth0) Beginning DHCP transaction.
Jul 11 18:04:45 atheossapiens-laptop dhclient: There is already a pid file
/var/run/dhclient.eth0.pid with pid 0
Jul 11 18:04:45 atheossapiens-laptop NetworkManager: <info>  Activation
(eth0) Stage 3 of 5 (IP Configure Start) complete.
Jul 11 18:04:45 atheossapiens-laptop NetworkManager: <info>  DHCP daemon
state is now 12 (successfully started) for interface eth0
Jul 11 18:04:46 atheossapiens-laptop NetworkManager: <info>  DHCP daemon
state is now 1 (starting) for interface eth0
Jul 11 18:04:48 atheossapiens-laptop dhclient: DHCPDISCOVER on eth0 to
255.255.255.255 port 67 interval 5
Jul 11 18:04:49 atheossapiens-laptop dhclient: DHCPOFFER of 192.168.1.42
from 192.168.1.1
Jul 11 18:04:49 atheossapiens-laptop dhclient: DHCPREQUEST of 192.168.1.42
on eth0 to 255.255.255.255 port 67
Jul 11 18:04:49 atheossapiens-laptop dhclient: DHCPACK of 192.168.1.42
from 192.168.1.1
Jul 11 18:04:49 atheossapiens-laptop avahi-daemon[5348]: Joining mDNS
multicast group on interface eth0.IPv4 with address 192.168.1.42.
Jul 11 18:04:49 atheossapiens-laptop avahi-daemon[5348]: New relevant
interface eth0.IPv4 for mDNS.
Jul 11 18:04:49 atheossapiens-laptop avahi-daemon[5348]: Registering new
address record for 192.168.1.42 on eth0.IPv4.
Jul 11 18:04:49 atheossapiens-laptop avahi-daemon[5348]: Withdrawing
address record for 192.168.1.42 on eth0.
Jul 11 18:04:49 atheossapiens-laptop avahi-daemon[5348]: Leaving mDNS
multicast group on interface eth0.IPv4 with address 192.168.1.42.
Jul 11 18:04:49 atheossapiens-laptop avahi-daemon[5348]: Interface
eth0.IPv4 no longer relevant for mDNS.
Jul 11 18:04:49 atheossapiens-laptop avahi-daemon[5348]: Joining mDNS
multicast group on interface eth0.IPv4 with address 192.168.1.42.
Jul 11 18:04:49 atheossapiens-laptop avahi-daemon[5348]: New relevant
interface eth0.IPv4 for mDNS.
Jul 11 18:04:49 atheossapiens-laptop avahi-daemon[5348]: Registering new
address record for 192.168.1.42 on eth0.IPv4.
Jul 11 18:04:49 atheossapiens-laptop NetworkManager: <info>  DHCP daemon
state is now 2 (bound) for interface eth0
Jul 11 18:04:49 atheossapiens-laptop NetworkManager: <info>  Activation
(eth0) Stage 4 of 5 (IP Configure Get) scheduled...
Jul 11 18:04:49 atheossapiens-laptop NetworkManager: <info>  Activation
(eth0) Stage 4 of 5 (IP Configure Get) started...
Jul 11 18:04:49 atheossapiens-laptop dhcdbd: message_handler: message
handler not found under /com/redhat/dhcp/eth0 for sub-path
eth0.dbus.get.host_name
Jul 11 18:04:49 atheossapiens-laptop dhclient: bound to 192.168.1.42 --
renewal in 41516 seconds.
Jul 11 18:04:49 atheossapiens-laptop dhcdbd: message_handler: message
handler not found under /com/redhat/dhcp/eth0 for sub-path
eth0.dbus.get.nis_domain
Jul 11 18:04:49 atheossapiens-laptop dhcdbd: message_handler: message
handler not found under /com/redhat/dhcp/eth0 for sub-path
eth0.dbus.get.nis_servers
Jul 11 18:04:49 atheossapiens-laptop NetworkManager: <info>  Retrieved the
following IP4 configuration from the DHCP daemon:
Jul 11 18:04:49 atheossapiens-laptop NetworkManager: <info>    address
192.168.1.42
Jul 11 18:04:49 atheossapiens-laptop NetworkManager: <info>    netmask
255.255.255.0
Jul 11 18:04:49 atheossapiens-laptop NetworkManager: <info>    broadcast
255.255.255.255
Jul 11 18:04:49 atheossapiens-laptop NetworkManager: <info>    gateway
192.168.1.1
Jul 11 18:04:49 atheossapiens-laptop NetworkManager: <info>    nameserver
192.168.1.1
Jul 11 18:04:49 atheossapiens-laptop NetworkManager: <info>    nameserver
192.168.1.1
Jul 11 18:04:49 atheossapiens-laptop NetworkManager: <info>    domain name
'myhome.westell.com'
Jul 11 18:04:49 atheossapiens-laptop dhcdbd: message_handler: message
handler not found under /com/redhat/dhcp/eth0 for sub-path
eth0.dbus.get.interface_mtu
Jul 11 18:04:49 atheossapiens-laptop NetworkManager: <info>  Activation
(eth0) Stage 5 of 5 (IP Configure Commit) scheduled...
Jul 11 18:04:49 atheossapiens-laptop NetworkManager: <info>  Activation
(eth0) Stage 4 of 5 (IP Configure Get) complete.
Jul 11 18:04:49 atheossapiens-laptop NetworkManager: <info>  Activation
(eth0) Stage 5 of 5 (IP Configure Commit) started...
Jul 11 18:04:49 atheossapiens-laptop avahi-daemon[5348]: Withdrawing
address record for 192.168.1.42 on eth0.
Jul 11 18:04:49 atheossapiens-laptop avahi-daemon[5348]: Leaving mDNS
multicast group on interface eth0.IPv4 with address 192.168.1.42.
Jul 11 18:04:49 atheossapiens-laptop avahi-daemon[5348]: Interface
eth0.IPv4 no longer relevant for mDNS.
Jul 11 18:04:49 atheossapiens-laptop avahi-daemon[5348]: Joining mDNS
multicast group on interface eth0.IPv4 with address 192.168.1.42.
Jul 11 18:04:49 atheossapiens-laptop avahi-daemon[5348]: New relevant
interface eth0.IPv4 for mDNS.
Jul 11 18:04:49 atheossapiens-laptop avahi-daemon[5348]: Registering new
address record for 192.168.1.42 on eth0.IPv4.
Jul 11 18:04:50 atheossapiens-laptop NetworkManager: <info>  Clearing nscd
hosts cache.
Jul 11 18:04:50 atheossapiens-laptop NetworkManager: <WARN>
nm_spawn_process(): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not
spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such
file or directory))
Jul 11 18:04:50 atheossapiens-laptop NetworkManager: <info>  Activation
(eth0) successful, device activated.
Jul 11 18:04:50 atheossapiens-laptop NetworkManager: <info>  Activation
(eth0) Finish handler scheduled.
Jul 11 18:04:50 atheossapiens-laptop NetworkManager: <info>  Activation
(eth0) Stage 5 of 5 (IP Configure Commit) complete.
Jul 11 18:04:50 atheossapiens-laptop ntpdate[6819]: adjust time server
91.189.94.4 offset -0.029933 sec
Jul 11 18:04:52 atheossapiens-laptop avahi-daemon[5348]: Registering new
address record for fe80::21d:72ff:fe5d:fd80 on eth0.*.
Jul 11 18:04:55 atheossapiens-laptop NetworkManager: <WARN>
request_and_convert_scan_results(): unknown error, or the card returned
too much scan info: Invalid argument
Jul 11 18:05:01 atheossapiens-laptop kernel: [  315.554719] eth0: no IPv6
routers present

-----------------------------------------------------------------------------------------------------------------------------------

Any help that anybody can give me would be greatly appreciated.

I have also tried wicd and a few other managers. i have wpa_supplicant installed but it crashes when i try to connect to a wpa router.

---

### Post by Atheossapiens on 2008-07-26
i solved it using ndiswrapper

---

