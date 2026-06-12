---
title: "trouble connecting to any WLAN AP"
date: 2008-04-10
forum: Networking &amp; Wireless
---

### Post by equity on 2008-04-10
Since today I did not have any problems connecting to any WLAN AP, no matter if it was unencrypted, WPA1/2 or whatever using the method kevdog introduced:
[http://ubuntuforums.org/showthread.php?t=684495](http://ubuntuforums.org/showthread.php?t=684495)

Now the wpa_supplicant causes trouble, does anyone know what is the problem?
Here is the wpa_supplicant output:

marcello@G1-AP021C:~$ sudo wpa_supplicant -w -Dwext -ieth1 -c /etc/wpa_supplican
t.conf -dd
Initializing interface 'eth1' conf '/etc/wpa_supplicant.conf' driver 'wext' ctrl
_interface 'N/A' bridge 'N/A'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
ap_scan=1
ctrl_interface='/var/run/wpa_supplicant'
Line: 4 - start of a new network block
ssid - hexdump_ascii(len=10):
     47 65 72 6d 61 6e 57 4c 41 4e                     GermanWLAN      
scan_ssid=0 (0x0)
proto: 0x1
key_mgmt: 0x2
PSK (ASCII passphrase) - hexdump_ascii(len=15): [REMOVED]
pairwise: 0x8
group: 0x8
PSK (from passphrase) - hexdump(len=32): [REMOVED]
Line: 14 - start of a new network block
ssid - hexdump_ascii(len=11):
     77 77 77 2e 68 65 74 74 2e 49 54                  [www.hett.IT](www.hett.IT)     
PSK (ASCII passphrase) - hexdump_ascii(len=11): [REMOVED]
key_mgmt: 0x2
proto: 0x2
pairwise: 0x10
PSK (from passphrase) - hexdump(len=32): [REMOVED]
Priority group 0
   id=0 ssid='GermanWLAN'
   id=1 ssid='www.hett.IT'
Initializing interface (2) 'eth1'
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
SIOCGIWRANGE: WE(compiled)=22 WE(source)=16 enc_capa=0xf
  capabilities: key_mgmt 0xf enc 0xf
WEXT: Operstate: linkmode=1, operstate=5
Own MAC address: 00:19:d2:d2:69:00
wpa_driver_wext_set_wpa
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_countermeasures
wpa_driver_wext_set_drop_unencrypted
Setting scan request: 0 sec 100000 usec
Using existing control interface directory.
ctrl_iface bind(PF_UNIX) failed: Address already in use
ctrl_iface exists and seems to be in use - cannot override it
Delete '/var/run/wpa_supplicant/eth1' manually if it is not used anymore
Failed to initialize control interface '/var/run/wpa_supplicant'.
You may have another wpa_supplicant process already running or the file was
left by an unclean termination of wpa_supplicant in which case you will need
to manually remove this file before starting wpa_supplicant again.

Failed to add interface eth1
State: DISCONNECTED -> DISCONNECTED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
No keys have been configured - skip key clearing
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
wpa_driver_wext_set_wpa
wpa_driver_wext_set_drop_unencrypted
wpa_driver_wext_set_countermeasures
No keys have been configured - skip key clearing
Cancelling scan request
Cancelling authentication timeout
WEXT: Operstate: linkmode=0, operstate=6
marcello@G1-AP021C:~$ 
marcello@G1-AP021C:~$

---

### Post by dstew on 2008-04-11
> Using existing control interface directory.
ctrl_iface bind(PF_UNIX) failed: Address already in use
ctrl_iface exists and seems to be in use - cannot override it
Delete '/var/run/wpa_supplicant/eth1' manually if it is not used anymore
Failed to initialize control interface '/var/run/wpa_supplicant'.
You may have another wpa_supplicant process already running or the file was
left by an unclean termination of wpa_supplicant in which case you will need
to manually remove this file before starting wpa_supplicant again.
I don't know much about wpa_supplicant, but from this message it seems that the program shut off previously without being able to delete this file. I would do what it says and delete the file manually. The other possibility is that wpa_supplicant was started twice by mistake, but if you get this error every time, and from fresh boots, it is most likely that the /var/run/wpa_supplicant/eth1 file needs to be removed.

---

### Post by equity on 2008-04-13
Okay, I did delete the file manually by typing "sudo rm -rf /var/run/wpa_supplicant/eth1" but it still does not work. I do not get why wpa_supplicant says, it does not find any suitable AP:

[B]marcello@G1-AP021C:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1A:92:EF:D8:F3  
          inet addr:192.168.1.67  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:92ff:feef:d8f3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1073 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1090 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:654797 (639.4 KB)  TX bytes:212947 (207.9 KB)
          Interrupt:16 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:99 errors:0 dropped:0 overruns:0 frame:0
          TX packets:99 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9714 (9.4 KB)  TX bytes:9714 (9.4 KB)

marcello@G1-AP021C:~$ 
marcello@G1-AP021C:~$ sudo ifconfig eth0 down
marcello@G1-AP021C:~$ 
marcello@G1-AP021C:~$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:99 errors:0 dropped:0 overruns:0 frame:0
          TX packets:99 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9714 (9.4 KB)  TX bytes:9714 (9.4 KB)

marcello@G1-AP021C:~$ sudo wpa_supplicant -w -Dwext -ieth1 -c /etc/wpa_supplican
t.conf -dd
Initializing interface 'eth1' conf '/etc/wpa_supplicant.conf' driver 'wext' ctrl
_interface 'N/A' bridge 'N/A'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
ap_scan=1
ctrl_interface='/var/run/wpa_supplicant'
Line: 4 - start of a new network block
ssid - hexdump_ascii(len=10):
     47 65 72 6d 61 6e 57 4c 41 4e                     GermanWLAN      
scan_ssid=0 (0x0)
proto: 0x1
key_mgmt: 0x2
PSK (ASCII passphrase) - hexdump_ascii(len=15): [REMOVED]
pairwise: 0x8
group: 0x8
PSK (from passphrase) - hexdump(len=32): [REMOVED]
Line: 14 - start of a new network block
ssid - hexdump_ascii(len=11):
     77 77 77 2e 68 65 74 74 2e 49 54                  [www.hett.IT](www.hett.IT)     
PSK (ASCII passphrase) - hexdump_ascii(len=11): [REMOVED]
key_mgmt: 0x2
proto: 0x2
pairwise: 0x10
PSK (from passphrase) - hexdump(len=32): [REMOVED]
Line: 22 - start of a new network block
ssid - hexdump_ascii(len=11):
     49 74 61 6c 69 61 6e 57 4c 41 4e                  ItalianWLAN     
scan_ssid=0 (0x0)
proto: 0x1
key_mgmt: 0x2
PSK (ASCII passphrase) - hexdump_ascii(len=15): [REMOVED]
pairwise: 0x8
group: 0x8
PSK (from passphrase) - hexdump(len=32): [REMOVED]
Priority group 0
   id=0 ssid='GermanWLAN'
   id=1 ssid='www.hett.IT'
   id=2 ssid='ItalianWLAN'
Initializing interface (2) 'eth1'
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
SIOCGIWRANGE: WE(compiled)=22 WE(source)=16 enc_capa=0xf
  capabilities: key_mgmt 0xf enc 0xf
WEXT: Operstate: linkmode=1, operstate=5
Own MAC address: 00:19:d2:d2:69:00
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
Trying to get current scan results first without requesting a new scan to speed 
up initial association
Received 0 bytes of scan results (0 BSSes)
Scan results: 0
Selecting BSS from priority group 0
Try to find WPA-enabled AP
Try to find non-WPA AP
No suitable AP found.
Setting scan request: 0 sec 0 usec
Starting AP scan (broadcast SSID)
Scan timeout - try to get results
Received 0 bytes of scan results (0 BSSes)
Scan results: 0
Selecting BSS from priority group 0
Try to find WPA-enabled AP
Try to find non-WPA AP
No suitable AP found.
Setting scan request: 5 sec 0 usec
Starting AP scan (broadcast SSID)
Scan timeout - try to get results
Received 0 bytes of scan results (0 BSSes)
Scan results: 0
Selecting BSS from priority group 0
Try to find WPA-enabled AP
Try to find non-WPA AP
No suitable AP found.
Setting scan request: 5 sec 0 usec
Starting AP scan (broadcast SSID)
Scan timeout - try to get results
Received 0 bytes of scan results (0 BSSes)
Scan results: 0
Selecting BSS from priority group 0
Try to find WPA-enabled AP
Try to find non-WPA AP
No suitable AP found.
Setting scan request: 5 sec 0 usec
Starting AP scan (broadcast SSID)
Scan timeout - try to get results
Received 0 bytes of scan results (0 BSSes)
Scan results: 0
Selecting BSS from priority group 0
Try to find WPA-enabled AP
Try to find non-WPA AP
No suitable AP found.
Setting scan request: 5 sec 0 usec
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
Wireless event: cmd=0x8b06 len=8
Starting AP scan (broadcast SSID)
Scan timeout - try to get results
Received 0 bytes of scan results (0 BSSes)
Scan results: 0
Selecting BSS from priority group 0
Try to find WPA-enabled AP
Try to find non-WPA AP
No suitable AP found.
Setting scan request: 5 sec 0 usec
Starting AP scan (broadcast SSID)
Scan timeout - try to get results
Received 0 bytes of scan results (0 BSSes)
Scan results: 0
Selecting BSS from priority group 0
Try to find WPA-enabled AP
Try to find non-WPA AP
No suitable AP found.
Setting scan request: 5 sec 0 usec
Starting AP scan (broadcast SSID)
Scan timeout - try to get results
Received 0 bytes of scan results (0 BSSes)
Scan results: 0
Selecting BSS from priority group 0
Try to find WPA-enabled AP
Try to find non-WPA AP
No suitable AP found.
Setting scan request: 5 sec 0 usec
Starting AP scan (broadcast SSID)
Scan timeout - try to get results
Received 0 bytes of scan results (0 BSSes)
Scan results: 0
Selecting BSS from priority group 0
Try to find WPA-enabled AP
Try to find non-WPA AP
No suitable AP found.
Setting scan request: 5 sec 0 usec
Starting AP scan (broadcast SSID)
Scan timeout - try to get results
Received 0 bytes of scan results (0 BSSes)
Scan results: 0
Selecting BSS from priority group 0
Try to find WPA-enabled AP
Try to find non-WPA AP
No suitable AP found.
Setting scan request: 5 sec 0 usec
CTRL-EVENT-TERMINATING - signal 2 received
Removing interface eth1
State: SCANNING -> DISCONNECTED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
No keys have been configured - skip key clearing
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
wpa_driver_wext_set_wpa
wpa_driver_wext_set_drop_unencrypted
wpa_driver_wext_set_countermeasures
No keys have been configured - skip key clearing
Cancelling scan request
Cancelling authentication timeout
WEXT: Operstate: linkmode=0, operstate=6
marcello@G1-AP021C:~$[/B]


after running the dhclient, I opened another xterm:

[B]marcello@G1-AP021C:~$ sudo dhclient eth1
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:19:d2:d2:69:00
Sending on   LPF/eth1/00:19:d2:d2:69:00
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
marcello@G1-AP021C:~$ [/B]


And here is the content of '/etc/wpa_supplicant.conf':

ap_scan=1
ctrl_interface=/var/run/wpa_supplicant 

network={
        ssid="GermanWLAN"
        scan_ssid=0
        proto=WPA
        key_mgmt=WPA-PSK
        psk="004901742003816"
        pairwise=TKIP
        group=TKIP
}

network={
        ssid="www.hett.IT"
        psk="06172985555"
        key_mgmt=WPA-PSK
        proto=RSN
        pairwise=CCMP
}

network={
        ssid="ItalianWLAN"
        scan_ssid=0
        proto=WPA
        key_mgmt=WPA-PSK
        psk="004901787475776"
        pairwise=TKIP
        group=TKIP
}

Why doesn't it work??? Everything seems to be correctly configured...

---

