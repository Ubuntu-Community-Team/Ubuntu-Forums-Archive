---
title: "network manager won't connect to wpa network"
date: 2008-09-19
forum: Networking &amp; Wireless
---

### Post by mathfeel on 2008-09-19
I am connecting using the following hardware:

```
  *-network
       description: Wireless interface
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wifi0
       version: 01
       serial: 00:15:af:b2:8f:f7
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci latency=0 module=ath_pci multicast=yes wireless=IEEE 802.11g
```

to the following network:
```
          Cell 02 - Address: 00:04:E2:DA:86:63
                    ESSID:"NOWIRE"
                    Mode:Master
                    Frequency:2.417 GHz (Channel 2)
                    Quality=26/70  Signal level=-69 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
```,

NetworkManager would ask me for the passphrase, which I provided, but nm would just stall:

```
Sep 18 21:32:41 Regents NetworkManager: <debug> [1221798761.957107] nm_device_802_11_wireless_get_activation_ap(): Forcing AP 'NOWIRE' 
Sep 18 21:32:41 Regents NetworkManager: <info>  User Switch: /org/freedesktop/NetworkManager/Devices/ath0 / NOWIRE 
Sep 18 21:32:41 Regents NetworkManager: <info>  Deactivating device ath0. 
Sep 18 21:32:41 Regents NetworkManager: <info>  Device ath0 activation scheduled... 
Sep 18 21:32:42 Regents NetworkManager: <info>  Activation (ath0) started... 
Sep 18 21:32:42 Regents NetworkManager: <info>  Activation (ath0) Stage 1 of 5 (Device Prepare) scheduled... 
Sep 18 21:32:42 Regents NetworkManager: <info>  Activation (ath0) Stage 1 of 5 (Device Prepare) started... 
Sep 18 21:32:42 Regents NetworkManager: <info>  Activation (ath0) Stage 2 of 5 (Device Configure) scheduled... 
Sep 18 21:32:42 Regents NetworkManager: <info>  Activation (ath0) Stage 1 of 5 (Device Prepare) complete. 
Sep 18 21:32:42 Regents NetworkManager: <info>  Activation (ath0) Stage 2 of 5 (Device Configure) starting... 
Sep 18 21:32:42 Regents NetworkManager: <info>  Activation (ath0/wireless): access point 'NOWIRE' is encrypted, but NO valid key exists.  New key needed. 
Sep 18 21:32:42 Regents NetworkManager: <info>  Activation (ath0) New wireless user key requested for network 'NOWIRE'. 
Sep 18 21:32:42 Regents NetworkManager: <info>  Activation (ath0) Stage 2 of 5 (Device Configure) complete. 
Sep 18 21:32:51 Regents NetworkManager: <info>  Activation (ath0) New wireless user key for network 'NOWIRE' received. 
Sep 18 21:32:51 Regents NetworkManager: <info>  Activation (ath0) Stage 1 of 5 (Device Prepare) scheduled... 
Sep 18 21:32:51 Regents NetworkManager: <info>  Activation (ath0) Stage 1 of 5 (Device Prepare) started... 
Sep 18 21:32:51 Regents NetworkManager: <info>  Activation (ath0) Stage 2 of 5 (Device Configure) scheduled... 
Sep 18 21:32:51 Regents NetworkManager: <info>  Activation (ath0) Stage 1 of 5 (Device Prepare) complete. 
Sep 18 21:32:51 Regents NetworkManager: <info>  Activation (ath0) Stage 2 of 5 (Device Configure) starting... 
Sep 18 21:32:51 Regents NetworkManager: <info>  Activation (ath0/wireless): access point 'NOWIRE' is encrypted, and a key exists.  No new key needed. 
Sep 18 21:32:52 Regents NetworkManager: <info>  SUP: sending command 'INTERFACE_ADD ath0^I^Imadwifi^I/var/run/wpa_supplicant0^I' 
Sep 18 21:32:52 Regents NetworkManager: <info>  SUP: response was 'OK' 
Sep 18 21:32:52 Regents NetworkManager: <info>  SUP: sending command 'AP_SCAN 1' 
Sep 18 21:32:52 Regents NetworkManager: <info>  SUP: response was 'OK' 
Sep 18 21:32:52 Regents NetworkManager: <info>  SUP: sending command 'ADD_NETWORK' 
Sep 18 21:32:52 Regents NetworkManager: <info>  SUP: response was '0' 
Sep 18 21:32:52 Regents NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 ssid 4e4f57495245' 
Sep 18 21:32:52 Regents NetworkManager: <info>  SUP: response was 'OK' 
Sep 18 21:32:52 Regents NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 proto WPA' 
Sep 18 21:32:52 Regents NetworkManager: <info>  SUP: response was 'OK' 
Sep 18 21:32:52 Regents NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 key_mgmt WPA-PSK' 
Sep 18 21:32:52 Regents NetworkManager: <info>  SUP: response was 'OK' 
Sep 18 21:32:52 Regents NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 psk <key>' 
Sep 18 21:32:52 Regents NetworkManager: <info>  SUP: response was 'OK' 
Sep 18 21:32:52 Regents NetworkManager: <info>  SUP: sending command 'ENABLE_NETWORK 0' 
Sep 18 21:32:52 Regents NetworkManager: <info>  SUP: response was 'OK' 
Sep 18 21:32:52 Regents NetworkManager: <info>  Activation (ath0) Stage 2 of 5 (Device Configure) complete. 
Sep 18 21:32:55 Regents NetworkManager: <debug> [1221798775.709928] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_54c_2a5_1A07121895603_if0_scsi_host_scsi_device_lun0_scsi_generic'). 
Sep 18 21:32:56 Regents NetworkManager: <debug> [1221798776.004801] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_68D4_F9FC'). 
Sep 18 21:32:56 Regents NetworkManager: <debug> [1221798776.029089] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/storage_serial_Sony_Storage_Media_1A07121895603_0_0'). 
Sep 18 21:32:56 Regents NetworkManager: <debug> [1221798776.039627] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_54c_2a5_1A07121895603_if0_scsi_host_scsi_device_lun0'). 
Sep 18 21:32:56 Regents NetworkManager: <debug> [1221798776.083986] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_54c_2a5_1A07121895603_if0_scsi_host'). 
Sep 18 21:32:56 Regents NetworkManager: <debug> [1221798776.105852] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_54c_2a5_1A07121895603_if0'). 
Sep 18 21:32:56 Regents NetworkManager: <debug> [1221798776.152422] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_54c_2a5_1A07121895603'). 
Sep 18 21:33:00 Regents NetworkManager: <info>  Old device 'ath0' activating, won't change. 
Sep 18 21:33:13 Regents NetworkManager: <info>  Old device 'ath0' activating, won't change. 
Sep 18 21:33:25 Regents NetworkManager: <info>  Old device 'ath0' activating, won't change. 
Sep 18 21:33:38 Regents NetworkManager: <info>  Old device 'ath0' activating, won't change. 
Sep 18 21:33:50 Regents NetworkManager: <info>  Old device 'ath0' activating, won't change. 
Sep 18 21:33:52 Regents NetworkManager: <info>  Activation (ath0/wireless): association took too long (>60s), failing activation. 
Sep 18 21:33:52 Regents NetworkManager: <info>  Activation (ath0) failure scheduled... 
Sep 18 21:33:53 Regents NetworkManager: <info>  Activation (ath0) failed for access point (NOWIRE) 
Sep 18 21:33:53 Regents NetworkManager: <info>  Activation (ath0) failed. 
Sep 18 21:33:53 Regents NetworkManager: <info>  Deactivating device ath0. 
```

The same router works in Windows and the same computer is able to connect to another router using WPA2. Help!

---

