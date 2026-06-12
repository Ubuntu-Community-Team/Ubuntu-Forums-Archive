---
title: "can`t get WPA to run...."
date: 2006-08-08
forum: Networking &amp; Wireless
---

### Post by yankee on 2006-08-08
Hello,

i am using the AVM! Wlan USB-Stick with my Ubuntu-Server. The Ndiswrapper discovers the stick and install the driver correctly. The Device WLAN0 is active, i can scan for WLAN-Devices.

Output from Syslog by loding the ndiswrapper:
```
Aug  9 00:44:34 jupiter kernel: [4446553.739000] ndiswrapper: device eth%%d removed
Aug  9 00:44:34 jupiter kernel: [4446553.739000] ndiswrapper: probe of 4-5:1.0 failed with error -22
Aug  9 00:44:34 jupiter kernel: [4446553.739000] usbcore: registered new driver ndiswrapper
Aug  9 00:44:34 jupiter kernel: [4446553.739000] usb 4-5: USB disconnect, address 2
Aug  9 00:44:34 jupiter kernel: [4446553.842000] usb 4-5: new high speed USB device using ehci_hcd and address 3
Aug  9 00:44:34 jupiter kernel: [4446554.257000] usb 4-5: reset high speed USB device using ehci_hcd and address 3
Aug  9 00:44:35 jupiter kernel: [4446555.156000] wlan0: vendor: 'AVM FRITZ!WLAN USB Stick'
Aug  9 00:44:35 jupiter kernel: [4446555.156000] wlan0: ethernet device 00:04:0e:c6:b5:f2 using NDIS driver fwlan, 057C:5601.F.conf
Aug  9 00:44:35 jupiter kernel: [4446555.157000] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK

```

The WPA-Supplicant shows the follwing messages:

```
sudo wpa_supplicant -i wlan0 -c /etc/wpa_supplicant.conf -D ndiswrapper -dd
Initializing interface 'wlan0' conf '/etc/wpa_supplicant.conf' driver 'ndiswrapper' ctrl_interface 'N/A'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
ctrl_interface='/var/run/wpa_supplicant'
Line: 3 - start of a new network block
ssid - hexdump_ascii(len=11):
     55 74 74 69 60 73 20 48 6f 6d 65                  Utti`s Home
scan_ssid=1 (0x1)
key_mgmt: 0x2
PSK - hexdump(len=32): [REMOVED]
Priority group 0
   id=0 ssid='Utti`s Home'
Initializing interface (2) 'wlan0'
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
SIOCGIWRANGE: WE(compiled)=19 WE(source)=18 enc_capa=0xf
  capabilities: key_mgmt 0xf enc 0xf
Own MAC address: 00:04:0e:c6:b5:f2
Driver does not support WPA.
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
Setting scan request: 0 sec 100000 usec
Added interface wlan0
Wireless event: cmd=0x8b06 len=8
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
State: DISCONNECTED -> SCANNING
Starting AP scan (specific SSID)
Scan SSID - hexdump_ascii(len=11):
     55 74 74 69 60 73 20 48 6f 6d 65                  Utti`s Home
Scan timeout - try to get results
Received 748 bytes of scan results (3 BSSes)
Scan results: 3
Selecting BSS from priority group 0
0: 00:15:0c:50:62:de ssid='Utti`s Home' wpa_ie_len=26 rsn_ie_len=0 caps=0x11
   selected based on WPA IE
Trying to associate with 00:15:0c:50:62:de (SSID='Utti`s Home' freq=2437 MHz)
Cancelling scan request
WPA: clearing own WPA/RSN IE
Automatic auth_alg selection: 0x1
WPA: using IEEE 802.11i/D3.0
WPA: Selected cipher suites: group 8 pairwise 8 key_mgmt 2
WPA: set AP WPA IE - hexdump(len=26): dd 18 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02 00 00
WPA: clearing AP RSN IE
WPA: using GTK TKIP
WPA: using PTK TKIP
WPA: using KEY_MGMT WPA-PSK
WPA: Set own WPA IE default - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
No keys have been configured - skip key clearing
State: SCANNING -> ASSOCIATING
Association request to the driver failed
Setting authentication timeout: 5 sec 0 usec
EAPOL: External notification - EAP success=0
EAPOL: External notification - EAP fail=0
EAPOL: External notification - portControl=Auto
Authentication with 00:00:00:00:00:00 timed out.
Added BSSID 00:00:00:00:00:00 into blacklist
State: ASSOCIATING -> DISCONNECTED
No keys have been configured - skip key clearing
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
Setting scan request: 0 sec 0 usec
State: DISCONNECTED -> SCANNING
Starting AP scan (broadcast SSID)
Scan timeout - try to get results
Received 527 bytes of scan results (2 BSSes)
Scan results: 2
Selecting BSS from priority group 0
0: 00:15:0c:50:62:de ssid='Utti`s Home' wpa_ie_len=26 rsn_ie_len=0 caps=0x11
   selected based on WPA IE
Trying to associate with 00:15:0c:50:62:de (SSID='Utti`s Home' freq=2437 MHz)
Cancelling scan request
WPA: clearing own WPA/RSN IE
Automatic auth_alg selection: 0x1
WPA: using IEEE 802.11i/D3.0
WPA: Selected cipher suites: group 8 pairwise 8 key_mgmt 2
WPA: set AP WPA IE - hexdump(len=26): dd 18 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02 00 00
WPA: clearing AP RSN IE
WPA: using GTK TKIP
WPA: using PTK TKIP
WPA: using KEY_MGMT WPA-PSK
WPA: Set own WPA IE default - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
No keys have been configured - skip key clearing
State: SCANNING -> ASSOCIATING
Association request to the driver failed
Setting authentication timeout: 5 sec 0 usec
EAPOL: External notification - EAP success=0
EAPOL: External notification - EAP fail=0
EAPOL: External notification - portControl=Auto
CTRL-EVENT-TERMINATING - signal 2 received
Removing interface wlan0
State: ASSOCIATING -> DISCONNECTED
No keys have been configured - skip key clearing
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
Failed to disable WPA in the driver.
No keys have been configured - skip key clearing
Removed BSSID 00:00:00:00:00:00 from blacklist (clear)
Cancelling scan request

```

This is my wpa_supplicant.conf:

```
ctrl_interface=/var/run/wpa_supplicant

network={
    ssid="Utti`s Home"
    scan_ssid=1
    key_mgmt=WPA-PSK
    psk= secret ;)
}

```

Anny Ideas?

Thanx Patrick

---

### Post by wieman01 on 2006-08-08
There is one line missing"
> ctrl_interface=/var/run/wpa_supplicant

network={
    ssid="Utti`s Home"
    scan_ssid=1
    **proto=WPA**
    key_mgmt=WPA-PSK
    psk= secret ;)
}

Does that work? What does your "interfaces" file look like? Is your ESSID hidden by chance?

You could also try to configure WPA/WPA2 this way (may be easier):

[http://www.ubuntuforums.org/showthread.php?t=202834]("http://www.ubuntuforums.org/showthread.php?t=202834")

This guide is meant for WPA2, please let me know if you want to have WPA1 rather than WPA2.

---

### Post by yankee on 2006-08-09
Thany for your Reply.
After adding the proto=WPA to my config, i get the following output from the WPA_supplicant. I wondering about "Driver does not support WPA". By loading ndiswrapper the wpa mode is listet as supported.

```
sudo wpa_supplicant -i wlan0 -c /etc/wpa_supplicant.conf -D ndiswrapper -dd
Initializing interface 'wlan0' conf '/etc/wpa_supplicant.conf' driver 'ndiswrapper' ctrl_interface 'N/A'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
ctrl_interface='/var/run/wpa_supplicant'
Line: 3 - start of a new network block
ssid - hexdump_ascii(len=11):
     55 74 74 69 60 73 20 48 6f 6d 65                  Utti`s Home
scan_ssid=1 (0x1)
proto: 0x1
key_mgmt: 0x2
PSK - hexdump(len=32): [REMOVED]
Priority group 0
   id=0 ssid='Utti`s Home'
Initializing interface (2) 'wlan0'
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
SIOCGIWRANGE: WE(compiled)=19 WE(source)=18 enc_capa=0xf
  capabilities: key_mgmt 0xf enc 0xf
Own MAC address: 00:04:0e:c6:b5:f2
Driver does not support WPA.
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
Setting scan request: 0 sec 100000 usec
Using existing control interface directory.
bind(PF_UNIX): Address already in use
ctrl_iface exists and seems to be in use - cannot override it
Delete '/var/run/wpa_supplicant/wlan0' manually if it is not used anymore
Failed to initialize control interface '/var/run/wpa_supplicant'.
You may have another wpa_supplicant process already running or the file was
left by an unclean termination of wpa_supplicant in which case you will need
to manually remove this file before starting wpa_supplicant again.
Failed to add interface wlan0
State: DISCONNECTED -> DISCONNECTED
No keys have been configured - skip key clearing
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
Failed to disable WPA in the driver.
No keys have been configured - skip key clearing
Cancelling scan request

```

My Interfaces:```

auto eth0
iface eth0 inet static
address 192.168.111.100
netmask 255.255.255.0
gateway 192.168.111.1
network 192.168.111.0

auto wlan0
iface wlan0 inet static
address 192.168.111.99
netmask 255.255.255.0
network 192.168.111.0
broadcast 192.168.111.255
gateway 192.168.111.1
dns-nameservers 192.168.111.1

```

I will try the other way later this day.

---

### Post by stricevics on 2006-08-09
> **yankee said:**
> 
```
sudo wpa_supplicant -i wlan0 -c /etc/wpa_supplicant.conf -D ndiswrapper -dd

```


Try to specify [FONT="Courier New"]wext[/FONT] as your driver instead of [FONT="Courier New"]ndiswrapper[/FONT]. Also, try typing it as:

```
sudo wpa_supplicant -iwlan0 -c/etc/wpa_supplicant.conf -Dwext -dd

```

Hope this helps,

St.

---

### Post by wieman01 on 2006-08-09
Would you mind dropping the "wpa_supplicant.conf" file and configuring WPA this way?

> auto wlan0
iface wlan0 inet static
address 192.168.111.99
netmask 255.255.255.0
network 192.168.111.0
broadcast 192.168.111.255
gateway 192.168.111.1
dns-nameservers 192.168.111.1
[B]wpa-driver wext
wpa-conf managed
wpa-ssid Utti_Home
wpa-ap-scan 1
wpa-proto WPA
wpa-pairwise TKIP
wpa-group TKIP
wpa-key-mgmt WPA-PSK
wpa-psk your_hex_key[/B]
This the easiest way to configure your network. You may have to restart your network twice (known bug) but we got it working. Restarting your computer may be necessary as well. Reference:

[http://www.ubuntuforums.org/showthread.php?t=225290&page=11]("http://www.ubuntuforums.org/showthread.php?t=225290&page=11")

Advantage is that you control your network using one single file. Also be careful with the ESSID because I am not sure how the system copes with special characters ("Utti`s Home"). 

The PSK must be generated using **"wpa_passphrase"** (see howto mentioned above).  "wext" is the right driver for "ndiswrapper".

---

### Post by yankee on 2006-08-13
Thanks to all, it will work now. I must use the wext-driver like explained...

Thanx...

Patrick

---

### Post by Korsaire71100 on 2008-03-05
Thanks stricevics, with wext, it runs.

GNU/Linux Debian Etch, ndiswrapper 1.28-1, driver acer inprocomm 64 bits 3.07.05.2005

I love GNU/LINUX ;-)

---

