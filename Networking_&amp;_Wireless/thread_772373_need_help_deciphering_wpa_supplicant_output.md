---
title: "need help deciphering wpa_supplicant output"
date: 2008-04-28
forum: Networking &amp; Wireless
---

### Post by chochem on 2008-04-28
Hi, I'm trying to connect to my library's wireless network but the 'linux setup guide' is a joke (it's just a wpa_supplicant.conf). 

Using [the wiki guide]("https://help.ubuntu.com/community/WifiDocs/WPAHowTo") and the library's instructions I added a wpa_supplicant.conf file like this
```

network={
        ssid="eduroam"
        key_mgmt=WPA-EAP
        eap=TTLS
        identity="[username]"
        password="[password]"
        phase2="auth=PAP"
}
```
 
and having made sure that I was in fact using the madwifi driver and that the device was called ath0, entered
```
wpa_supplicant -iath0 -c/etc/wpa_supplicant.conf -Dmadwifi -w
```

However I just got some 'ioctl' error and using the -dd option got me this (I believe it goes into a loop after this):

```
ioctl[IEEE80211_IOCTL_SETMLME]: Invalid argument
Initializing interface 'ath0' conf '/etc/wpa_supplicant.conf' driver 'madwifi' ctrl_interface 'N/A' bridge 'N/A'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
Line: 1 - start of a new network block
ssid - hexdump_ascii(len=7):
     65 64 75 72 6f 61 6d                              eduroam         
key_mgmt: 0x1
scan_ssid=1 (0x1)
eap methods - hexdump(len=16): 00 00 00 00 15 00 00 00 00 00 00 00 00 00 00 00
identity - hexdump_ascii(len=10):
     31 32 30 34 37 37 32 32 30 33                     1204772203      
password - hexdump_ascii(len=4): [REMOVED]
phase2 - hexdump_ascii(len=8):
     61 75 74 68 3d 50 41 50                           auth=PAP        
Priority group 0
   id=0 ssid='eduroam'
Initializing interface (2) 'ath0'
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
SIOCGIWRANGE: WE(compiled)=22 WE(source)=13 enc_capa=0xf
  capabilities: key_mgmt 0xf enc 0xf
WEXT: Operstate: linkmode=1, operstate=5
Own MAC address: 00:02:e3:47:4f:7a
wpa_driver_madwifi_del_key: keyidx=0
wpa_driver_madwifi_del_key: keyidx=1
wpa_driver_madwifi_del_key: keyidx=2
wpa_driver_madwifi_del_key: keyidx=3
wpa_driver_madwifi_set_countermeasures: enabled=0
wpa_driver_madwifi_set_drop_unencrypted: enabled=1
Setting scan request: 0 sec 100000 usec
Added interface ath0
RTM_NEWLINK: operstate=0 ifi_flags=0x1002 ()
Wireless event: cmd=0x8b06 len=8
Ignore event for foreign ifindex 5
RTM_NEWLINK: operstate=0 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'ath0' added
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'ath0' added
State: DISCONNECTED -> SCANNING
Starting AP scan (specific SSID)
Scan SSID - hexdump_ascii(len=7):
     65 64 75 72 6f 61 6d                              eduroam         
Trying to get current scan results first without requesting a new scan to speed up initial association
Received 256 bytes of scan results (1 BSSes)
Scan results: 1
Selecting BSS from priority group 0
Try to find WPA-enabled AP
0: 00:13:5f:55:91:c0 ssid='AUWLAN' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - no WPA/RSN IE
Try to find non-WPA AP
0: 00:13:5f:55:91:c0 ssid='AUWLAN' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - SSID mismatch
No suitable AP found.
Setting scan request: 0 sec 0 usec
Starting AP scan (broadcast SSID)
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8b1a len=8
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8b19 len=8
Received 3562 bytes of scan results (13 BSSes)
Scan results: 13
Selecting BSS from priority group 0
Try to find WPA-enabled AP
0: 00:1a:e3:74:35:10 ssid='eduroam' wpa_ie_len=26 rsn_ie_len=0 caps=0x11
   selected based on WPA IE
   selected WPA AP 00:1a:e3:74:35:10 ssid='eduroam'
Try to find non-WPA AP
Trying to associate with 00:1a:e3:74:35:10 (SSID='eduroam' freq=2472 MHz)
Cancelling scan request
WPA: clearing own WPA/RSN IE
Automatic auth_alg selection: 0x1
WPA: using IEEE 802.11i/D3.0
WPA: Selected cipher suites: group 8 pairwise 8 key_mgmt 1 proto 1
WPA: set AP WPA IE - hexdump(len=26): dd 18 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 01 28 00
WPA: clearing AP RSN IE
WPA: using GTK TKIP
WPA: using PTK TKIP
WPA: using KEY_MGMT 802.1X
WPA: Set own WPA IE default - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 01
No keys have been configured - skip key clearing
wpa_driver_madwifi_set_drop_unencrypted: enabled=1
State: SCANNING -> ASSOCIATING
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
wpa_driver_madwifi_associate
wpa_driver_madwifi_associate: SETMLME[ASSOC] failed
Association request to the driver failed
Setting authentication timeout: 5 sec 0 usec

```

Amongst the things I tried getting it work was restarting the driver. Taking a peek at dmesg output:
```
[ 5411.916194] ath_pci: driver unloaded
[ 5411.936597] ath_pci: 0.9.4
[ 5411.936695] ACPI: PCI Interrupt 0000:02:01.0[A] -> GSI 23 (level, low) -> IRQ 19
[ 5412.642151] ath_pci: switching rfkill capability off
[ 5412.645769] wifi0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
[ 5412.645776] wifi0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
**[ 5412.645785] wifi0: H/W encryption support: WEP AES AES_CCM TKIP**

```
I noticed that WPA was not listed among the H/W encryption support. I don't know if this is important - I'm able to connect in Windows, so it can't be physically impossible...

Can somebody help me tell what's going on/wrong here?

---

