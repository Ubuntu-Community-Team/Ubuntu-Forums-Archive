---
title: "ipw2200 problem"
date: 2005-11-05
forum: Networking &amp; Wireless
---

### Post by sporto on 2005-11-05
Hi all,

I posted the following in the wrong thread (i am using 5.1 not 5.04):

[http://www.ubuntuforums.org/showpost.php?p=469692&postcount=466](http://www.ubuntuforums.org/showpost.php?p=469692&postcount=466)

i am trying with ieee80211-1.1.6 , ipw2200-1.0.8, and ipw2200-fw-2.4.

I successfully get this with dmesg:
[4296316.590000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.0.8
[4296316.590000] ipw2200: Copyright(c) 2003-2005 Intel Corporation

when I run sudo wpa_supplicant -B -i eth1 -c /etc/wpa_supplicant.conf -D ipw -w -dd

i get:

Initializing interface 'eth1' conf '/etc/wpa_supplicant.conf' driver 'ipw'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
ctrl_interface='/var/run/wpa_supplicant'
Line: 4 - start of a new network block
ssid - hexdump_ascii(len=14):
62 69 6c 6c 79 20 61 6e 64 20 62 65 61 72 billy and bear
scan_ssid=1 (0x1)
proto: 0x1
key_mgmt: 0x2
PSK - hexdump(len=32): [REMOVED]
Priority group 0
id=0 ssid='billy and bear'
Daemonize..


if i run without -dd i get:
mathew@ubuntu:~$ sudo wpa_supplicant -B -i eth1 -c /etc/wpa_supplicant.conf -D ipw
ioctl[SIOCSIWPMKSA]: Operation not supported

and dmesg shows:

[4296316.590000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.0.8
[4296316.590000] ipw2200: Copyright(c) 2003-2005 Intel Corporation
[4296316.594000] ipw2200: Detected Intel PRO/Wireless 2915ABG Network Connection[4296316.930000] ipw2200: Can't set TKIP countermeasures: crypt not set!
[4296324.669000] ipw2200: Can't set TKIP countermeasures: crypt not set!
[4296324.670000] ipw2200: Can't set TKIP countermeasures: crypt not set!


can someone help me with the problem?

many thanks.  :KS

---

### Post by sporto on 2005-11-06
now i tried with 1.0.6 as included with breezy-686 kernel.

all i did was install wpa supplicant.

now i get..

mathew@ubuntu:~$ sudo wpa_supplicant -i eth1 -c /etc/wpa_supplicant.conf -D ipw
ioctl[SIOCSIWPMKSA]: Operation not supported
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Trying to associate with 00:14:bf:93:53:2d (SSID='billy and bear' freq=0 MHz)
Associated with 00:14:bf:93:53:2d
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Trying to associate with 00:14:bf:93:53:2d (SSID='billy and bear' freq=0 MHz)
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys

etc..

*please* help!

---

