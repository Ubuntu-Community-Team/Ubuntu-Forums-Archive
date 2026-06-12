---
title: "Help on getting D-link 530 to work with WPA"
date: 2005-11-29
forum: Networking &amp; Wireless
---

### Post by Anomaly on 2005-11-29
My card is the D-link 530 and the first thing I did was install the driver using ndiswrapper. Next, I went on to install wpa_supplicant wich should make ndiswrapper work with WPA.

Here is the good bit......

I tried to test wpa_supplicant with ndiswrapper

         sudo wpa_supplicant -iath0 -c wpa_supplicant.conf -Dndiswrapper -dd

Most unfortunately I got this error message...

```
Initializing interface 'ath0' conf 'wpa_supplicant.conf' driver 'ndiswrapper'
Configuration file 'wpa_supplicant.conf' -> '/usr/share/doc/wpasupplicant/examples/wpa_supplicant.conf'
Reading configuration file '/usr/share/doc/wpasupplicant/examples/wpa_supplicant.conf'
ctrl_interface='/var/run/wpa_supplicant'
ctrl_interface_group=0
eapol_version=1
ap_scan=1
fast_reauth=1
opensc_engine_path='/usr/lib/opensc/engine_opensc.so'
pkcs11_engine_path='/usr/lib/opensc/engine_pkcs11.so'
pkcs11_module_path='/usr/lib/pkcs11/opensc-pkcs11.so'
Line: 595 - start of a new network block
ssid - hexdump_ascii(len=9):
     6e 65 6c 6c 6f 6e 65 74 32                        nellonet2
PSK (ASCII passphrase) - hexdump_ascii(len=10): [REMOVED]
priority=5 (0x5)
PSK (from passphrase) - hexdump(len=32): [REMOVED]
Line: 601 - start of a new network block
ssid - hexdump_ascii(len=9):
     6e 65 6c 6c 6f 6e 65 74 32                        nellonet2
proto: 0x1
key_mgmt: 0x2
PSK - hexdump(len=32): [REMOVED]
Priority group 5
   id=0 ssid='nellonet2'
Priority group 0
   id=1 ssid='nellonet2'
Initializing interface (2) 'ath0'
ENGINE: Loading dynamic engine
ENGINE: Loading OpenSC Engine from /usr/lib/opensc/engine_opensc.so
ENGINE: 'SO_PATH' '/usr/lib/opensc/engine_opensc.so'
ENGINE: 'ID' 'opensc'
ENGINE: 'LIST_ADD' '1'
ENGINE: 'LOAD' '(null)'
ENGINE: ctrl cmd_string failed: LOAD (null) [error:25066067:DSO support routines:DLFCN_LOAD:could not load the shared library]
SSL: Failed to initialize TLS context.
Failed to initialize EAPOL state machines.
```

I dont know what to make of this, so any reply's will be greatly appreciated!:D

---

### Post by mlavikai on 2005-12-08
Hi.

Have you tried to install opensc and libopensc-openssl packages?

---

