---
title: "dell 6000 centrino wireless wpa setup problem"
date: 2005-11-16
forum: Networking &amp; Wireless
---

### Post by dipstick456 on 2005-11-16
I have installed ubuntu 5.10 (breezy), and I have been struggling over the last several days to get wireless running.  I followed everything that was in 

[B][http://www.ubuntuforums.org/showthread.php?t=26623](http://www.ubuntuforums.org/showthread.php?t=26623) and also
[http://www.ubuntuforums.org/archive/index.php/t-31418.html](http://www.ubuntuforums.org/archive/index.php/t-31418.html) (partially)
[/B]

but I still cannot seem to get the WPA working.  Wireless works seemlessly under windows XP.  Ubuntu has detected the card (as shown in the system->adminstrator->network correctly, system->administrator->devices->wireless, and also from dmesg).  I have included some specifics below:

Dell 6000
w29n51.inf wireless card (according to the wireless information under c:\drivers)
linksys 54G wireless router

I have recompiled everything as indicated in the first link
==============
**dmesg | grep ipw**
[4294697.737000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.0.6
[4294697.737000] ipw2200: Copyright(c) 2003-2004 Intel Corporation
[4294697.740000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection

==============
i**wconfig output (Note I have changed the SSID**
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"#########"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:12:17:CA:39:44
          Bit Rate=54 Mb/s   Tx-Power=20 dBm
          Retry limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=96/100  Signal level=-30 dBm  Noise level=-87 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:176   Missed beacon:0

sit0      no wireless extensions.

==========
**/etc/wpa_supplicant.conf (NOTE: I have changed the SSID and the psk.   wpas_passphrase was used to generate the psk)**

ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=0

eapol_version=1
ap_scan=2
fast_reauth=1

### Associate with any open access point
###  Scans/ESSID changes can be done with wpa_cli
network={
        ssid="#########"
        scan_ssid=1
        proto=WPA
        key_mgmt=WPA-PSK
        pairwise=TKIP
        ##psk="#############################"
       psk=##################
}

======================
**output of wpa_supplicant -B -i eth1 -c /etc/wpa_supplicant.conf -D ipw -dd**

Initializing interface 'eth1' conf '/etc/wpa_supplicant.conf' driver 'ipw'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
ctrl_interface='/var/run/wpa_supplicant'
ctrl_interface_group=0
eapol_version=1
ap_scan=2
fast_reauth=1
Line: 15 - start of a new network block
ssid - hexdump_ascii(len=11):
     70 61 6c 6d 65 72 5f 68 6f 6d 65                  ########
scan_ssid=1 (0x1)
proto: 0x1
key_mgmt: 0x2
pairwise: 0x8
PSK - hexdump(len=32): [REMOVED]
Line 25: removed CCMP from group cipher list since it was not allowed for pairwise cipher
Priority group 0
   id=0 ssid='palmer_home'
Initializing interface (2) 'eth1'
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
wpa_driver_ipw_init is called
ioctl[SIOCSIWPMKSA]: Operation not supported
SIOCGIWRANGE: too old (short) data - assuming WPA is not supported
Own MAC address: 00:0e:35:fc:be:fb
wpa_driver_ipw_set_wpa: enabled=1
wpa_driver_ipw_set_key: alg=none key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_ipw_set_key: alg=none key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_ipw_set_key: alg=none key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_ipw_set_key: alg=none key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_ipw_set_countermeasures: enabled=0
wpa_driver_ipw_set_drop_unencrypted: enabled=1
Setting scan request: 0 sec 100000 usec
Daemonize..

===================
**Output of ifconfig eth1**

eth1      Link encap:Ethernet  HWaddr 00:0E:35:FC:BE:FB
          inet6 addr: fe80::20e:35ff:fefc:befb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3 errors:0 dropped:176 overruns:0 frame:0
          TX packets:3 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000
          RX bytes:187248 (182.8 KiB)  TX bytes:164160 (160.3 KiB)
          Interrupt:17 Base address:0xc000 Memory:dfdfd000-dfdfdfff

====================
Attempts at pinging the network or obtaining a dhcp address (dhclient eth1) does not work.  I am missing something extremely simple.  I currently am at a loss as to why I can not get the wireless working.  Thanks in advance.

---

### Post by dipstick456 on 2005-11-17
I have it resolved.  I had a captialization error in the wpa passphrase.

---

