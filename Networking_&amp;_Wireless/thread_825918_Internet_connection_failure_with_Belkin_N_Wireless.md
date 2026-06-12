---
title: "Internet connection failure with Belkin N Wireless Modem Router and Ubuntu 8.04"
date: 2008-06-11
forum: Networking &amp; Wireless
---

### Post by spnoe on 2008-06-11
Internet connection failure with Belkin N Wireless Modem Router and Ubuntu 8.04.
After some some messing with the network panels I have managed to get the Router working and get the Bars up on the panel but I can not connect to the internet, using any software. I am sure it is a simple solution but I am a novice and have no idea how to tweak this to work. One window said IP not available if that is of help.

Could someone advise? Many thanks.
Steve

---

### Post by superprash2003 on 2008-06-11
please post output of ping google.com

---

### Post by spnoe on 2008-06-12
> **superprash2003 said:**
> please post output of ping google.com

Superprash, sorry, you are responding to a complete novice. How do I ping? 

Thanks for your help.

Steve

---

### Post by superprash2003 on 2008-06-12
sorry mate.. go to the terminal (Applications->Accessories->Terminal) and type ping google.com  .. you would get an output.. highlight the output.. right click .. click on copy and paste it here

---

### Post by spnoe on 2008-06-12
> **superprash2003 said:**
> sorry mate.. go to the terminal (Applications->Accessories->Terminal) and type ping google.com  .. you would get an output.. highlight the output.. right click .. click on copy and paste it here

Ok here is the output; ping: unknown host Google.com
I tried the Router URL 192.168.2.2 and it said unable to reach network.

When I log on or start the computer the connection tries to start the network and the lower green dot illuminates but the top does not and I have to recreate a new network to get it to work but I am not sure what I am doing, so may be it is not set up correctly.

I appreciate your time and effort to help.

Steve

---

### Post by superprash2003 on 2008-06-12
please post output of ifconfig and iwconfig from the terminal
  Same procedure , go to terminal type the command paste the output here

---

### Post by spnoe on 2008-06-12
> **superprash2003 said:**
> please post output of ifconfig and iwconfig from the terminal
  Same procedure , go to terminal type the command paste the output here
I did not attempt to start connection and it did not start automatically.

stephen @ stephen-desktop: -$ ifconfig
ethO Link encap:Ethernet HWaddr 00:16:17:25:lc:d8
UP BROADCAST MULTICAST MTU:1500 Metric:l RX packets:0 errors:0 dropped:0 overruns:0 frame:0 TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 collisions:0 txqueuelen: 1000
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
Interrupt: 19 Base address:OxecOO
to	Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: :: 1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric: I
RX packets:2022 errors:0 dropped:0 overruns:0 frame:0 TX packets:2022 errors:0 dropped:0 overruns:0 carrier:0 collisions:0 txqueuelen:0
RX bytes: 101100 (98.7 KB) TX bytes:101100 (98.7 KB)
wianO Link encap:Ethernet HWaddr 00:12:bf:64:2b:21
UP BROADCAST MULTICAST MTU:1500 Metric:1 RX packets:0 errors:0 dropped:0 overruns:0 frame:0 TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 collisions:0 txqueuelen: 1000
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
wmaster0 Link encap:UNSPEC HWaddr 00-12-BF-64-2B-21-00-00-00-00-00-00-00-00-00-00 UP BROADCAST RUNNING MULTICAST MTU: 1500 Metric: I
RX packets:0 errors:0 dropped:0 overruns:0 frame:0 TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 collisions:0 txqueuelen: 1000
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
stephen@stephen-desktop:-$ iwconfig to	no wireless extensions.
ethO no wireless extensions.
wmaster0 no wireless extensions.
wlan0 IEEE 802.11g ESSID:""
Mode:Managed Frequency:2.412 GHz Access Point: Not-Associated Tx-Power=27 dBm
Retry min limit:7 RTS thr:off Fragment thr=2346 B
Link Quality:0 Signal level:0 Noise level:0
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

---

### Post by superprash2003 on 2008-06-12
your iwconfig output isnt showing any wifi networks.. are you sure you are able to connect to your wifi modem wirelessly?

---

### Post by spnoe on 2008-06-13
Yes I have done previously, but I have to go through setting up a new network each time. The settings do not seem to be saved. However,as I said before I am not sure what I am doing or if I am setting the network up correctly.

Steve

---

### Post by spnoe on 2008-06-25
I understand that the driver for my wlan card a rt2500usb is already installed and should work out of the box. So what am I doing wrong.
I have the following printout if someone understands it and can help me solve my problem. Thanks.
stephen@Stephen_Noe:~$ sudo tail -f /var/log/syslog
[sudo] password for stephen:
Jun 18 10:18:33 Stephen_Noe NetworkManager: <info> Device wlan0 activation scheduled...
Jun 18 10:18:33 Stephen_Noe NetworkManager: <info> Activation (wlan0) started...
Jun 18 10:18:33 Stephen_Noe NetworkManager: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jun 18 10:18:33 Stephen_Noe NetworkManager: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jun 18 10:18:33 Stephen_Noe NetworkManager: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jun 18 10:18:33 Stephen_Noe NetworkManager: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jun 18 10:18:33 Stephen_Noe NetworkManager: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jun 18 10:18:33 Stephen_Noe NetworkManager: <info> Activation (wlan0/wireless): access point 'Belkin_N_ADSL_771473' is encrypted, but NO valid key exists. New key needed.
Jun 18 10:18:33 Stephen_Noe NetworkManager: <info> Activation (wlan0) New wireless user key requested for network 'Belkin_N_ADSL_771473'.
Jun 18 10:18:33 Stephen_Noe NetworkManager: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.

I then tried to start the connection by setting up a new network and this is the printout,

Jun 18 10:24:19 Stephen_Noe kernel: [ 431.538848] wlan0: authenticate with AP 00:00:00:00:00:00
Jun 18 10:24:19 Stephen_Noe kernel: [ 431.738740] wlan0: authentication with AP 00:00:00:00:00:00 timed out
Jun 18 10:24:23 Stephen_Noe NetworkManager: <info> Activation (wlan0/wireless): association took too long (>60s), failing activation.
Jun 18 10:24:23 Stephen_Noe NetworkManager: <info> Activation (wlan0) failure scheduled...
Jun 18 10:24:23 Stephen_Noe NetworkManager: <info> Activation (wlan0) failed for access point (Stephen_Noe)
Jun 18 10:24:23 Stephen_Noe NetworkManager: <info> Activation (wlan0) failed.
Jun 18 10:24:23 Stephen_Noe NetworkManager: <info> Deactivating device wlan0.
Jun 18 10:24:23 Stephen_Noe kernel: [ 436.046641] wlan0: Initial auth_alg=0
Jun 18 10:24:23 Stephen_Noe kernel: [ 436.046649] wlan0: authenticate with AP 00:00:00:00:00:00
Jun 18 10:24:24 Stephen_Noe kernel: [ 436.244249] wlan0: authenticate with AP 00:00:00:00:00:00
Jun 18 10:24:24 Stephen_Noe kernel: [ 436.444146] wlan0: authenticate with AP 00:00:00:00:00:00
Jun 18 10:24:24 Stephen_Noe kernel: [ 436.644038] wlan0: authentication with AP 00:00:00:00:00:00 timed out
Jun 18 10:24:37 Stephen_Noe dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.reason
Jun 18 10:24:37 Stephen_Noe NetworkManager: <debug> [1213777477.576688] nm_device_802_11_wireless_get_activation_ap(): Forcing AP 'Belkin_N_ADSL_771473'
Jun 18 10:24:37 Stephen_Noe NetworkManager: <info> User Switch: /org/freedesktop/NetworkManager/Devices/wlan0 / Belkin_N_ADSL_771473
Jun 18 10:24:37 Stephen_Noe NetworkManager: <info> Deactivating device wlan0.
Jun 18 10:24:37 Stephen_Noe NetworkManager: <info> Device wlan0 activation scheduled...
Jun 18 10:24:37 Stephen_Noe NetworkManager: <info> Activation (wlan0) started...
Jun 18 10:24:37 Stephen_Noe NetworkManager: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jun 18 10:24:37 Stephen_Noe NetworkManager: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jun 18 10:24:37 Stephen_Noe NetworkManager: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jun 18 10:24:37 Stephen_Noe NetworkManager: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jun 18 10:24:37 Stephen_Noe NetworkManager: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jun 18 10:24:37 Stephen_Noe NetworkManager: <info> Activation (wlan0/wireless): access point 'Belkin_N_ADSL_771473' is encrypted, and a key exists. No new key needed.
Jun 18 10:24:38 Stephen_Noe NetworkManager: <info> SUP: sending command 'INTERFACE_ADD wlan0^I^Iwext^I/var/run/wpa_supplicant0^I'
Jun 18 10:24:38 Stephen_Noe modprobe: WARNING: /etc/modprobe.d/blacklist line 40: ignoring bad line starting with 'balcklist'
Jun 18 10:24:38 Stephen_Noe NetworkManager: <info> SUP: response was 'OK'
Jun 18 10:24:39 Stephen_Noe NetworkManager: <info> SUP: sending command 'AP_SCAN 1'
Jun 18 10:24:39 Stephen_Noe NetworkManager: <info> SUP: response was 'OK'
Jun 18 10:24:39 Stephen_Noe NetworkManager: <info> SUP: sending command 'ADD_NETWORK'
Jun 18 10:24:39 Stephen_Noe NetworkManager: <info> SUP: response was '0'
Jun 18 10:24:39 Stephen_Noe NetworkManager: <info> SUP: sending command 'SET_NETWORK 0 ssid 42656c6b696e5f4e5f4144534c5f373731343733'
Jun 18 10:24:39 Stephen_Noe NetworkManager: <info> SUP: response was 'OK'
Jun 18 10:24:39 Stephen_Noe NetworkManager: <info> SUP: sending command 'SET_NETWORK 0 proto WPA2'
Jun 18 10:24:39 Stephen_Noe NetworkManager: <info> SUP: response was 'OK'
Jun 18 10:24:39 Stephen_Noe NetworkManager: <info> SUP: sending command 'SET_NETWORK 0 key_mgmt WPA-PSK'
Jun 18 10:24:39 Stephen_Noe NetworkManager: <info> SUP: response was 'OK'
Jun 18 10:24:39 Stephen_Noe NetworkManager: <info> SUP: sending command 'SET_NETWORK 0 psk <key>'
Jun 18 10:24:39 Stephen_Noe NetworkManager: <info> SUP: response was 'OK'
Jun 18 10:24:39 Stephen_Noe NetworkManager: <info> SUP: sending command 'ENABLE_NETWORK 0'
Jun 18 10:24:39 Stephen_Noe NetworkManager: <info> SUP: response was 'OK'
Jun 18 10:24:39 Stephen_Noe NetworkManager: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jun 18 10:24:39 Stephen_Noe kernel: [ 452.088340] wlan0: Initial auth_alg=0
Jun 18 10:24:39 Stephen_Noe kernel: [ 452.088348] wlan0: authenticate with AP 00:1c:df:77:14:73
Jun 18 10:24:39 Stephen_Noe kernel: [ 452.089938] wlan0: RX authentication from 00:1c:df:77:14:73 (alg=0 transaction=2 status=0)
Jun 18 10:24:39 Stephen_Noe kernel: [ 452.089943] wlan0: authenticated
Jun 18 10:24:39 Stephen_Noe kernel: [ 452.089946] wlan0: associate with AP 00:1c:df:77:14:73
Jun 18 10:24:39 Stephen_Noe kernel: [ 452.092807] wlan0: RX AssocResp from 00:1c:df:77:14:73 (capab=0x431 status=0 aid=1)
Jun 18 10:24:39 Stephen_Noe kernel: [ 452.092812] wlan0: associated
Jun 18 10:24:39 Stephen_Noe kernel: [ 452.092856] wlan0: WMM queue=2 aci=0 acm=0 aifs=3 cWmin=15 cWmax=1023 burst=0
Jun 18 10:24:39 Stephen_Noe kernel: [ 452.092859] wlan0: failed to set TX queue parameters for queue 2
Jun 18 10:24:39 Stephen_Noe kernel: [ 452.092861] wlan0: WMM queue=3 aci=1 acm=0 aifs=7 cWmin=15 cWmax=1023 burst=0
Jun 18 10:24:39 Stephen_Noe kernel: [ 452.092864] wlan0: failed to set TX queue parameters for queue 3
Jun 18 10:24:39 Stephen_Noe kernel: [ 452.092866] wlan0: WMM queue=1 aci=2 acm=0 aifs=2 cWmin=7 cWmax=15 burst=30
Jun 18 10:24:39 Stephen_Noe kernel: [ 452.092869] wlan0: WMM queue=0 aci=3 acm=0 aifs=2 cWmin=3 cWmax=7 burst=15
Jun 18 10:24:39 Stephen_Noe kernel: [ 452.095434] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Jun 18 10:24:40 Stephen_Noe NetworkManager: <info> Supplicant state changed: 1
Jun 18 10:24:40 Stephen_Noe NetworkManager: <info> Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful. Connected to access point 'Belkin_N_ADSL_771473'.
Jun 18 10:24:40 Stephen_Noe NetworkManager: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Jun 18 10:24:40 Stephen_Noe NetworkManager: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Jun 18 10:24:41 Stephen_Noe NetworkManager: <info> Activation (wlan0) Beginning DHCP transaction.
Jun 18 10:24:41 Stephen_Noe NetworkManager: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Jun 18 10:24:41 Stephen_Noe NetworkManager: <info> DHCP daemon state is now 12 (successfully started) for interface wlan0
Jun 18 10:24:41 Stephen_Noe dhclient: wmaster0: unknown hardware address type 801
Jun 18 10:24:41 Stephen_Noe avahi-daemon[5573]: Registering new address record for fe80::212:bfff:fe64:2b21 on wlan0.*.
Jun 18 10:24:42 Stephen_Noe NetworkManager: <info> DHCP daemon state is now 1 (starting) for interface wlan0
Jun 18 10:24:42 Stephen_Noe dhclient: wmaster0: unknown hardware address type 801
Jun 18 10:24:44 Stephen_Noe NetworkManager: <info> Old device 'wlan0' activating, won't change.
Jun 18 10:24:46 Stephen_Noe dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
Jun 18 10:24:50 Stephen_Noe kernel: [ 462.897556] wlan0: no IPv6 routers present
Jun 18 10:24:54 Stephen_Noe dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
Jun 18 10:25:05 Stephen_Noe dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
Jun 18 10:25:13 Stephen_Noe dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
Jun 18 10:25:17 Stephen_Noe dhclient: No DHCPOFFERS received.
Jun 18 10:25:17 Stephen_Noe avahi-autoipd(wlan0)[6650]: Found user 'avahi-autoipd' (UID 105) and group 'avahi-autoipd' (GID 113).
Jun 18 10:25:17 Stephen_Noe avahi-autoipd(wlan0)[6650]: Successfully called chroot().
Jun 18 10:25:17 Stephen_Noe avahi-autoipd(wlan0)[6650]: Successfully dropped root privileges.
Jun 18 10:25:17 Stephen_Noe avahi-autoipd(wlan0)[6650]: Starting with address 169.254.4.14
Jun 18 10:25:22 Stephen_Noe avahi-autoipd(wlan0)[6650]: Callout BIND, address 169.254.4.14 on interface wlan0
Jun 18 10:25:22 Stephen_Noe avahi-daemon[5573]: Joining mDNS multicast group on interface wlan0.IPv4 with address 169.254.4.14.
Jun 18 10:25:22 Stephen_Noe avahi-daemon[5573]: New relevant interface wlan0.IPv4 for mDNS.
Jun 18 10:25:22 Stephen_Noe avahi-daemon[5573]: Registering new address record for 169.254.4.14 on wlan0.IPv4.
Jun 18 10:25:26 Stephen_Noe avahi-autoipd(wlan0)[6650]: Successfully claimed IP address 169.254.4.14
Jun 18 10:25:26 Stephen_Noe NetworkManager: <info> DHCP daemon state is now 9 (fail) for interface wlan0
Jun 18 10:25:26 Stephen_Noe NetworkManager: <info> Activation (wlan0) Stage 4 of 5 (IP Configure Timeout) scheduled...
Jun 18 10:25:26 Stephen_Noe NetworkManager: <info> Activation (wlan0) Stage 4 of 5 (IP Configure Timeout) started...
Jun 18 10:25:26 Stephen_Noe NetworkManager: <info> Activation (wlan0) failure scheduled...
Jun 18 10:25:26 Stephen_Noe NetworkManager: <info> Activation (wlan0) Stage 4 of 5 (IP Configure Timeout) complete.
Jun 18 10:25:26 Stephen_Noe dhcdbd: Unrequested down ?:3
Jun 18 10:25:26 Stephen_Noe NetworkManager: <info> DHCP daemon state is now 14 (normal exit) for interface wlan0
Jun 18 10:25:27 Stephen_Noe NetworkManager: <info> Activation (wlan0) failed for access point (Belkin_N_ADSL_771473)
Jun 18 10:25:27 Stephen_Noe NetworkManager: <info> Activation (wlan0) failed.
Jun 18 10:25:27 Stephen_Noe NetworkManager: <info> Deactivating device wlan0.
Jun 18 10:25:27 Stephen_Noe kernel: [ 499.180461] wlan0: deauthenticate(reason=3)
Jun 18 10:25:27 Stephen_Noe avahi-daemon[5573]: Withdrawing address record for 169.254.4.14 on wlan0.
Jun 18 10:25:27 Stephen_Noe avahi-daemon[5573]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 169.254.4.14.
Jun 18 10:25:27 Stephen_Noe avahi-daemon[5573]: Interface wlan0.IPv4 no longer relevant for mDNS.
Jun 18 10:25:27 Stephen_Noe avahi-daemon[5573]: Withdrawing address record for fe80::212:bfff:fe64:2b21 on wlan0.

I hope this is of help and thank you for taking the time to offer your assistance

Steve

---

