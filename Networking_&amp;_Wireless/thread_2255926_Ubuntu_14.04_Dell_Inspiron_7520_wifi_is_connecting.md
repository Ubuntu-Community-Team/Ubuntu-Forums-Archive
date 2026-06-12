---
title: "Ubuntu 14.04 Dell Inspiron 7520 wifi is connecting but falis"
date: 2014-12-08
forum: Networking &amp; Wireless
---

### Post by vasiliy3 on 2014-12-08
Wifi on my laptop is trying to connect all the time, but unsuccessfully. Result of running wireless script is attached.
Log is here:
> Dec 20 15:30:05 vasylok-Inspiron-7520 NetworkManager[1069]: <info> Activation (wlan0) starting connection 'ASUS-F7B8 1'Dec 20 15:30:05 vasylok-Inspiron-7520 NetworkManager[1069]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Dec 20 15:30:05 vasylok-Inspiron-7520 NetworkManager[1069]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Dec 20 15:30:05 vasylok-Inspiron-7520 NetworkManager[1069]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Dec 20 15:30:05 vasylok-Inspiron-7520 NetworkManager[1069]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Dec 20 15:30:05 vasylok-Inspiron-7520 NetworkManager[1069]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Dec 20 15:30:05 vasylok-Inspiron-7520 NetworkManager[1069]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Dec 20 15:30:05 vasylok-Inspiron-7520 NetworkManager[1069]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Dec 20 15:30:05 vasylok-Inspiron-7520 NetworkManager[1069]: <info> Activation (wlan0/wireless): access point 'ASUS-F7B8 1' has security, but secrets are required.
Dec 20 15:30:05 vasylok-Inspiron-7520 NetworkManager[1069]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
Dec 20 15:30:05 vasylok-Inspiron-7520 NetworkManager[1069]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Dec 20 15:30:05 vasylok-Inspiron-7520 NetworkManager[1069]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Dec 20 15:30:05 vasylok-Inspiron-7520 NetworkManager[1069]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Dec 20 15:30:05 vasylok-Inspiron-7520 NetworkManager[1069]: <info> (wlan0): device state change: need-auth -> prepare (reason 'none') [60 40 0]
Dec 20 15:30:05 vasylok-Inspiron-7520 NetworkManager[1069]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Dec 20 15:30:05 vasylok-Inspiron-7520 NetworkManager[1069]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Dec 20 15:30:05 vasylok-Inspiron-7520 NetworkManager[1069]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Dec 20 15:30:05 vasylok-Inspiron-7520 NetworkManager[1069]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Dec 20 15:30:05 vasylok-Inspiron-7520 NetworkManager[1069]: <info> Activation (wlan0/wireless): connection 'ASUS-F7B8 1' has security, and secrets exist.  No new secrets needed.
Dec 20 15:30:05 vasylok-Inspiron-7520 NetworkManager[1069]: <info> Config: added 'ssid' value 'ASUS-F7B8'
Dec 20 15:30:05 vasylok-Inspiron-7520 NetworkManager[1069]: <info> Config: added 'scan_ssid' value '1'
Dec 20 15:30:05 vasylok-Inspiron-7520 NetworkManager[1069]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Dec 20 15:30:05 vasylok-Inspiron-7520 NetworkManager[1069]: <info> Config: added 'psk' value '<omitted>'
Dec 20 15:30:05 vasylok-Inspiron-7520 NetworkManager[1069]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Dec 20 15:30:05 vasylok-Inspiron-7520 NetworkManager[1069]: <info> Config: set interface ap_scan to 1
Dec 20 15:30:05 vasylok-Inspiron-7520 NetworkManager[1069]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Dec 20 15:30:06 vasylok-Inspiron-7520 NetworkManager[1069]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Dec 20 15:30:06 vasylok-Inspiron-7520 NetworkManager[1069]: <info> (wlan0): supplicant interface state: authenticating -> associating
Dec 20 15:30:06 vasylok-Inspiron-7520 NetworkManager[1069]: <info> (wlan0): supplicant interface state: associating -> 4-way handshake
Dec 20 15:30:06 vasylok-Inspiron-7520 NetworkManager[1069]: <info> (wlan0): supplicant interface state: 4-way handshake -> completed
Dec 20 15:30:06 vasylok-Inspiron-7520 NetworkManager[1069]: <info> Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'ASUS-F7B8'.
Dec 20 15:30:06 vasylok-Inspiron-7520 NetworkManager[1069]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Dec 20 15:30:06 vasylok-Inspiron-7520 NetworkManager[1069]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Dec 20 15:30:06 vasylok-Inspiron-7520 NetworkManager[1069]: <info> (wlan0): device state change: config -> ip-config (reason 'none') [50 70 0]
Dec 20 15:30:06 vasylok-Inspiron-7520 NetworkManager[1069]: <info> Activation (wlan0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Dec 20 15:30:06 vasylok-Inspiron-7520 NetworkManager[1069]: <info> dhclient started with pid 14861
Dec 20 15:30:06 vasylok-Inspiron-7520 NetworkManager[1069]: <info> Activation (wlan0) Beginning IP6 addrconf.
Dec 20 15:30:06 vasylok-Inspiron-7520 NetworkManager[1069]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Dec 20 15:30:06 vasylok-Inspiron-7520 NetworkManager[1069]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
Dec 20 15:30:26 vasylok-Inspiron-7520 NetworkManager[1069]: <info> (wlan0): IP6 addrconf timed out or failed.
Dec 20 15:30:26 vasylok-Inspiron-7520 NetworkManager[1069]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Dec 20 15:30:26 vasylok-Inspiron-7520 NetworkManager[1069]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) started...
Dec 20 15:30:26 vasylok-Inspiron-7520 NetworkManager[1069]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) complete.
Dec 20 15:30:51 vasylok-Inspiron-7520 NetworkManager[1069]: <warn> (wlan0): DHCPv4 request timed out.
Dec 20 15:30:51 vasylok-Inspiron-7520 NetworkManager[1069]: <info> (wlan0): canceled DHCP transaction, DHCP client pid 14861
Dec 20 15:30:51 vasylok-Inspiron-7520 NetworkManager[1069]: <info> Activation (wlan0) Stage 4 of 5 (IPv4 Configure Timeout) scheduled...
Dec 20 15:30:51 vasylok-Inspiron-7520 NetworkManager[1069]: <info> Activation (wlan0) Stage 4 of 5 (IPv4 Configure Timeout) started...
Dec 20 15:30:51 vasylok-Inspiron-7520 NetworkManager[1069]: <info> (wlan0): device state change: ip-config -> failed (reason 'ip-config-unavailable') [70 120 5]
Dec 20 15:30:51 vasylok-Inspiron-7520 NetworkManager[1069]: <info> Marking connection 'ASUS-F7B8 1' invalid.
Dec 20 15:30:51 vasylok-Inspiron-7520 NetworkManager[1069]: <warn> Activation (wlan0) failed for connection 'ASUS-F7B8 1'
Dec 20 15:30:51 vasylok-Inspiron-7520 NetworkManager[1069]: <info> Activation (wlan0) Stage 4 of 5 (IPv4 Configure Timeout) complete.
Dec 20 15:30:51 vasylok-Inspiron-7520 NetworkManager[1069]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0]
Dec 20 15:30:51 vasylok-Inspiron-7520 NetworkManager[1069]: <info> (wlan0): deactivating device (reason 'none') [0]
Dec 20 15:30:51 vasylok-Inspiron-7520 NetworkManager[1069]: <warn> Connection disconnected (reason -3)
Dec 20 15:30:51 vasylok-Inspiron-7520 NetworkManager[1069]: <info> (wlan0): supplicant interface state: completed -> disconnected
Dec 20 15:30:51 vasylok-Inspiron-7520 NetworkManager[1069]: <warn> Connection disconnected (reason -3

---

