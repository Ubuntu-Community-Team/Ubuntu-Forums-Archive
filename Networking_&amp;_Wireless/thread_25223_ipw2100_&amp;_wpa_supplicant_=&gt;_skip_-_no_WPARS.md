---
title: "ipw2100 &amp; wpa_supplicant =&gt; skip - no WPA/RSN IE"
date: 2005-04-09
forum: Networking &amp; Wireless
---

### Post by C38a7r1zvl on 2005-04-09
Hi everybody.

I've just switched from Mandriva Linux to (K)Ubuntu and I have to say, it's a lovely.. err.. forget that.. it's an AWESOME distribution! :) Had some difficulties with the standard installer but nevermind.

Unfortunately I can't manage to get my wirelass lan working. My wifi-card is "Intel® PRO/Wireless Lan Kit 2200 (802.11b/g)" and my AP a Netgear WAP54G. On my AP I chose "WPA Pre-Shared Key" as the security mode and "TKIP" as the WPA algorithm. Here's my wpa_supplicant.conf:
```
network={
        ssid="ssid"
        #scan_ssid=1
        key_mgmt=WPA-PSK
        proto=WPA
        psk="passphrase"
        bssid=00:0F:66:E9:C0:80
}

```

And that's the lovely outpout of "wpa_supplicant -ieth1 -c/etc/wpa_supplicant.conf -t -dddd -Dipw":
```
Apr 09 20:20:21.035356: Initializing interface 'eth1' conf '/etc/wpa_supplicant.conf' driver 'ipw'
Apr 09 20:20:21.035935: Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Apr 09 20:20:21.036284: Reading configuration file '/etc/wpa_supplicant.conf'
Apr 09 20:20:21.036641: ctrl_interface='/var/run/wpa_supplicant'
Apr 09 20:20:21.036922: Line: 6 - start of a new network block
Apr 09 20:20:21.037251: ssid - hexdump_ascii(len=8):
     47 61 57 69 2d 4c 41 4e                           GaWi-LAN
Apr 09 20:20:21.037796: key_mgmt: 0x2
Apr 09 20:20:21.038037: proto: 0x1
Apr 09 20:20:21.038263: PSK (ASCII passphrase) - hexdump_ascii(len=26): [REMOVED]
Apr 09 20:20:21.038570: BSSID - hexdump(len=6): 00 0f 66 e9 c0 80
Apr 09 20:20:21.129929: PSK (from passphrase) - hexdump(len=32): [REMOVED]
Apr 09 20:20:21.130444: Priority group 0
Apr 09 20:20:21.130710:    id=0 ssid='GaWi-LAN'
Apr 09 20:20:21.131059: Initializing interface (2) 'eth1'
Apr 09 20:20:21.139067: EAPOL: SUPP_PAE entering state DISCONNECTED
Apr 09 20:20:21.139367: EAPOL: KEY_RX entering state NO_KEY_RECEIVE
Apr 09 20:20:21.139646: EAPOL: SUPP_BE entering state INITIALIZE
Apr 09 20:20:21.140153: EAP: EAP entering state DISABLED
Apr 09 20:20:21.140505: EAPOL: External notification - portEnabled=0
Apr 09 20:20:21.140829: EAPOL: External notification - portValid=0
Apr 09 20:20:21.141162: wpa_driver_ipw_init is called
Apr 09 20:20:21.144986: Own MAC address: 00:0e:35:86:2b:9c
Apr 09 20:20:21.145273: wpa_driver_ipw_set_wpa: enabled=1
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
Apr 09 20:20:21.145855: wpa_driver_ipw_set_key: alg=none key_idx=0 set_tx=0 seq_len=0 key_len=0
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
Apr 09 20:20:21.146480: Failed to set encryption.
Apr 09 20:20:21.146726: wpa_driver_ipw_set_key: alg=none key_idx=1 set_tx=0 seq_len=0 key_len=0
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
Apr 09 20:20:21.147399: Failed to set encryption.
Apr 09 20:20:21.147646: wpa_driver_ipw_set_key: alg=none key_idx=2 set_tx=0 seq_len=0 key_len=0
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
Apr 09 20:20:21.148261: Failed to set encryption.
Apr 09 20:20:21.148505: wpa_driver_ipw_set_key: alg=none key_idx=3 set_tx=0 seq_len=0 key_len=0
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
Apr 09 20:20:21.149120: Failed to set encryption.
Apr 09 20:20:21.149365: wpa_driver_ipw_set_countermeasures: enabled=0
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
Apr 09 20:20:21.149921: wpa_driver_ipw_set_drop_unencrypted: enabled=1
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
Apr 09 20:20:21.150510: Setting scan request: 0 sec 100000 usec
Apr 09 20:20:21.151088: Wireless event: cmd=0x8b06 len=8
Apr 09 20:20:21.151378: RTM_NEWLINK, IFLA_IFNAME: Interface 'eth1' added
Apr 09 20:20:21.151682: RTM_NEWLINK, IFLA_IFNAME: Interface 'eth1' added
Apr 09 20:20:21.250974: Starting AP scan (broadcast SSID)
Apr 09 20:20:22.140837: EAPOL: Port Timers tick - authWhile=0 heldWhile=0 startWhen=0 idleWhile=0
Apr 09 20:20:23.141761: EAPOL: Port Timers tick - authWhile=0 heldWhile=0 startWhen=0 idleWhile=0
Apr 09 20:20:24.142529: EAPOL: Port Timers tick - authWhile=0 heldWhile=0 startWhen=0 idleWhile=0
Apr 09 20:20:24.315506: Scan timeout - try to get results
Apr 09 20:20:24.315639: Received 226 bytes of scan results (1 BSSes)
Apr 09 20:20:24.315682: Scan results: 1
Apr 09 20:20:24.315709: Selecting BSS from priority group 0
Apr 09 20:20:24.315741: 0: 00:0f:66:e9:c0:80 ssid='GaWi-LAN' wpa_ie_len=0 rsn_ie_len=0
Apr 09 20:20:24.315788:    skip - no WPA/RSN IE
Apr 09 20:20:24.315816: No suitable AP found.
Apr 09 20:20:24.315848: Setting scan request: 5 sec 0 usec
Apr 09 20:20:25.143382: EAPOL: Port Timers tick - authWhile=0 heldWhile=0 startWhen=0 idleWhile=0
Apr 09 20:20:26.144268: EAPOL: Port Timers tick - authWhile=0 heldWhile=0 startWhen=0 idleWhile=0
Apr 09 20:20:27.145075: EAPOL: Port Timers tick - authWhile=0 heldWhile=0 startWhen=0 idleWhile=0
Apr 09 20:20:28.147232: EAPOL: Port Timers tick - authWhile=0 heldWhile=0 startWhen=0 idleWhile=0
Apr 09 20:20:29.155769: EAPOL: Port Timers tick - authWhile=0 heldWhile=0 startWhen=0 idleWhile=0
Apr 09 20:20:29.316746: Starting AP scan (broadcast SSID)
Apr 09 20:20:30.156618: EAPOL: Port Timers tick - authWhile=0 heldWhile=0 startWhen=0 idleWhile=0
Apr 09 20:20:31.157462: EAPOL: Port Timers tick - authWhile=0 heldWhile=0 startWhen=0 idleWhile=0
Apr 09 20:20:32.158310: EAPOL: Port Timers tick - authWhile=0 heldWhile=0 startWhen=0 idleWhile=0
Apr 09 20:20:32.317287: Scan timeout - try to get results
Apr 09 20:20:32.317380: Received 226 bytes of scan results (1 BSSes)
Apr 09 20:20:32.317420: Scan results: 1
Apr 09 20:20:32.317447: Selecting BSS from priority group 0
Apr 09 20:20:32.317479: 0: 00:0f:66:e9:c0:80 ssid='GaWi-LAN' wpa_ie_len=0 rsn_ie_len=0
Apr 09 20:20:32.317526:    skip - no WPA/RSN IE
Apr 09 20:20:32.317553: No suitable AP found.
Apr 09 20:20:32.317585: Setting scan request: 5 sec 0 usec
Apr 09 20:20:33.159163: EAPOL: Port Timers tick - authWhile=0 heldWhile=0 startWhen=0 idleWhile=0
Apr 09 20:20:34.160005: EAPOL: Port Timers tick - authWhile=0 heldWhile=0 startWhen=0 idleWhile=0
Apr 09 20:20:35.160853: EAPOL: Port Timers tick - authWhile=0 heldWhile=0 startWhen=0 idleWhile=0
Apr 09 20:20:36.161701: EAPOL: Port Timers tick - authWhile=0 heldWhile=0 startWhen=0 idleWhile=0
Apr 09 20:20:37.162549: EAPOL: Port Timers tick - authWhile=0 heldWhile=0 startWhen=0 idleWhile=0
Apr 09 20:20:37.318525: Starting AP scan (broadcast SSID)
Apr 09 20:20:38.163397: EAPOL: Port Timers tick - authWhile=0 heldWhile=0 startWhen=0 idleWhile=0
Apr 09 20:20:39.164288: EAPOL: Port Timers tick - authWhile=0 heldWhile=0 startWhen=0 idleWhile=0
Apr 09 20:20:39.506674: Signal 2 received - terminating
Apr 09 20:20:39.506729: No keys have been configured - skip key clearing
Apr 09 20:20:39.506767: EAPOL: External notification - portEnabled=0
Apr 09 20:20:39.506900: EAPOL: External notification - portValid=0
Apr 09 20:20:39.506982: wpa_driver_ipw_set_wpa: enabled=0
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
Apr 09 20:20:39.507158: wpa_driver_ipw_set_drop_unencrypted: enabled=0
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
Apr 09 20:20:39.507259: wpa_driver_ipw_set_countermeasures: enabled=0
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported

```

Using Kernel 2.6.10-5-686 and the driver from ipw2100-source.

Any hint is appreciated.

Greetings from Cologne, Germany!

---

### Post by joshmachine on 2005-04-09
You have a 2200 but you are using the ipw2100 source.  I assume that this is causing your problem.  They must be similar since you can load the module.

The source for the 2200 driver doesn't appear to be in the repositories but you can download it from 

[http://ipw2200.sourceforge.net/](http://ipw2200.sourceforge.net/)

Cheers and Greetings from New Delhi, India!

---

### Post by C38a7r1zvl on 2005-04-10
Alright, I'll check that. Thx in advance!

---

### Post by javaguru on 2005-11-09
use wpa_supplicant -i interface -c /etc/wpa_config -D wext -w -dd

ipp2200 uses the wireless extensions nowadays .. I still however have problems with wpa and wpa2

---

