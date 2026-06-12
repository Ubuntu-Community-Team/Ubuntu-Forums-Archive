---
title: "&quot;Atheros QCA6174, Ubuntu 14.04, Wireless network disabled&quot;"
date: 2019-01-28
forum: Networking &amp; Wireless
---

### Post by pys11 on 2019-01-28
I updated some packages and afterwards I have been unable to connect to my Wireless network, it looks like it is disabled. My laptop is dual boot Windows, if that matters. I ran the recommended script and posted the result. I am hoping somebody can help me out. Thanks!

```



########## wireless info START ##########


Report from: 28 Jan 2019 18:52 PST -0800


Booted last: 28 Jan 2019 18:06 PST -0800


Script from: 22 Oct 2018 03:34 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 14.04.5 LTS
Release:	14.04
Codename:	trusty


##### kernel ############################


Linux 4.4.0-141-generic #167~14.04.1-Ubuntu SMP Mon Dec 10 13:20:24 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################




3b:00.0 Ethernet controller [0200]: Qualcomm Atheros Device [1969:e0a1] (rev 10)
	Subsystem: Device [0707:2400]
	Kernel driver in use: alx


3c:00.0 Network controller [0280]: Qualcomm Atheros QCA6174 802.11ac Wireless Network Adapter [168c:003e] (rev 32)
	Subsystem: Bigfoot Networks, Inc. Device [1a56:1535]
	Kernel driver in use: ath10k_pci


##### lsusb #############################


Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 1bcf:2b8c Sunplus Innovation Technology Inc. 
Bus 001 Device 003: ID 0cf3:e301 Atheros Communications, Inc. 
Bus 001 Device 002: ID 187c:0528 Alienware Corporation 
Bus 001 Device 005: ID cd12:ef18 SMART TECHNOLOGY INDUSTRIAL LTD. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################




##### rfkill ############################


0: dell-rbtn: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
2: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no


##### secure boot #######################


SecureBoot disabled


##### lsmod #############################


dell_wmi               16384  0 
sparse_keymap          16384  1 dell_wmi
mxm_wmi                16384  0 
ath10k_pci             40960  0 
ath10k_core           315392  1 ath10k_pci
ath                    32768  1 ath10k_core
mac80211              733184  1 ath10k_core
cfg80211              561152  3 ath,mac80211,ath10k_core
wmi                    20480  2 dell_wmi,mxm_wmi
video                  40960  2 i915_bpo,dell_wmi


##### interfaces ########################


[/etc/network/interfaces]
auto lo
iface lo inet loopback




##### ifconfig ##########################


1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: eth0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc pfifo_fast state DOWN group default qlen 1000
    link/ether 28:f1:0e:0e:fc:49 brd ff:ff:ff:ff:ff:ff
3: wlan0: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN group default qlen 1000
    link/ether 9c:b6:d0:0f:4f:99 brd ff:ff:ff:ff:ff:ff


##### iwconfig ##########################


lo        no wireless extensions.


eth0      no wireless extensions.


wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          


##### route #############################




##### resolv.conf #######################


[777 root ‘/etc/resolv.conf’ -> ‘../run/resolvconf/resolv.conf’]


##### network managers ##################


Installed:


	NetworkManager


Running:


root      2458     1  0 18:16 ?        00:00:02 NetworkManager


##### NetworkManager info ###############




NetworkManager Tool


State: disconnected


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath10k_pci
  State:             unavailable
  Default:           no
  HW Address:        9C:B6:D0:0F:4F:99


  Capabilities:


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points 




- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            alx
  State:             unavailable
  Default:           no
  HW Address:        28:F1:0E:0E:FC:49


  Capabilities:
    Carrier Detect:  yes


  Wired Properties
    Carrier:         off






##### NetworkManager.state ##############


[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


##### NetworkManager config #############


[[/etc/NetworkManager/NetworkManager.conf]]
[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq
no-auto-default=28:F1:0E:0E:FC:49,
[ifupdown]
managed=false




##### NetworkManager profiles ###########



```

---

### Post by praseodym on 2019-01-29
```

wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=[COLOR="#FF0000"]0 dBm[/COLOR]   
```
Card seems to be turned off. Any button, switch, key or key combo?

---

### Post by pys11 on 2019-01-29
Thanks, this is odd.

I don't see any switch, but according to my keyboard it looks like with Fn+F2 I should be able to toggle it, but it does nothing. I just tried booting in Windows, and the card IS turned on there (can connect to the wireless network), and I can toggle it with Fn+F2 there. Any ideas?

---

