---
title: "Netgear wna1000m usb wifi dongle not connecting"
date: 2017-09-08
forum: Networking &amp; Wireless
---

### Post by chown2 on 2017-09-08
I am able to connect by wired connection but not with wifi dongle , It tries to connect but fails to connect at end ,Please check the details i thought would be necessary to understand what may be the issue 
&#10140;  ~ uname -a
Linux codexian-pc 4.10.0-33-generic #37-Ubuntu SMP Fri Aug 11 10:55:28 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux

&#10140;```
  ~  lsb_release -a 
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 17.04
Release:    17.04
Codename:    zesty
```


&#10140; ```
 ~ lsusb
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 002: ID 0bda:0411 Realtek Semiconductor Corp. 
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 001 Device 005: ID 0846:9041 NetGear, Inc. WNA1000M 802.11bgn [Realtek RTL8188CUS]
Bus 001 Device 004: ID 04d9:1203 Holtek Semiconductor, Inc. Keyboard
Bus 001 Device 002: ID 0bda:5411 Realtek Semiconductor Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```
==================================================================
&#10140; ```
 ~ lsmod
Module                  Size  Used by
msr                    16384  0
des_generic            24576  0
md4                    16384  0
nls_utf8               16384  1
cifs                  708608  2
ccm                    20480  0
fscache                61440  1 cifs
input_leds             16384  0
rtl8xxxu              126976  0
arc4                   16384  2
rtl8192cu              69632  0
rtl_usb                20480  1 rtl8192cu
rtl8192c_common        53248  1 rtl8192cu
rtlwifi                98304  3 rtl_usb,rtl8192c_common,rtl8192cu
mac80211              782336  4 rtl_usb,rtlwifi,rtl8192cu,rtl8xxxu
cfg80211              602112  2 mac80211,rtlwifi
snd_hda_codec_hdmi     49152  1
bnep                   20480  2
snd_hda_codec_ca0132    61440  1
intel_rapl             20480  0
x86_pkg_temp_thermal    16384  0
intel_powerclamp       16384  0
snd_hda_intel          36864  2
kvm_intel             200704  0
snd_hda_codec         126976  3 snd_hda_intel,snd_hda_codec_hdmi,snd_hda_codec_ca0132
kvm                   593920  1 kvm_intel
snd_hda_core           81920  4 snd_hda_intel,snd_hda_codec,snd_hda_codec_hdmi,snd_hda_codec_ca0132
irqbypass              16384  1 kvm
snd_hwdep              16384  1 snd_hda_codec
snd_pcm               102400  4 snd_hda_intel,snd_hda_codec,snd_hda_core,snd_hda_codec_hdmi
crct10dif_pclmul       16384  0
crc32_pclmul           16384  0
snd_seq_midi           16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            32768  1 snd_seq_midi
ghash_clmulni_intel    16384  0
pcbc                   16384  0
snd_seq                65536  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              32768  2 snd_seq,snd_pcm
aesni_intel           167936  0
aes_x86_64             20480  1 aesni_intel
crypto_simd            16384  1 aesni_intel
glue_helper            16384  1 aesni_intel
cryptd                 24576  3 crypto_simd,ghash_clmulni_intel,aesni_intel
snd                    77824  14 snd_hda_intel,snd_hwdep,snd_seq,snd_hda_codec,snd_timer,snd_rawmidi,snd_hda_codec_hdmi,snd_seq_device,snd_hda_codec_ca0132,snd_pcm
soundcore              16384  1 snd
shpchp                 36864  0
mei_me                 40960  0
mei                   102400  1 mei_me
hci_uart               98304  0
btbcm                  16384  1 hci_uart
btqca                  16384  1 hci_uart
btintel                16384  1 hci_uart
bluetooth             557056  11 hci_uart,btintel,btqca,bnep,btbcm
intel_lpss_acpi        16384  0
intel_lpss             16384  1 intel_lpss_acpi
tpm_infineon           20480  0
acpi_pad              180224  0
acpi_als               16384  0
kfifo_buf              16384  1 acpi_als
industrialio           69632  2 acpi_als,kfifo_buf
mac_hid                16384  0
coretemp               16384  0
parport_pc             32768  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,parport_pc,ppdev
ip_tables              24576  0
x_tables               36864  1 ip_tables
autofs4                40960  2
hid_logitech_hidpp     28672  0
hid_logitech_dj        20480  0
hid_generic            16384  0
usbhid                 53248  0
mxm_wmi                16384  0
i915                 1449984  149
i2c_algo_bit           16384  1 i915
e1000e                249856  0
drm_kms_helper        151552  1 i915
syscopyarea            16384  1 drm_kms_helper
ptp                    20480  1 e1000e
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
pps_core               20480  1 ptp
fb_sys_fops            16384  1 drm_kms_helper
alx                    45056  0
nvme                   28672  1
drm                   352256  8 i915,drm_kms_helper
mdio                   16384  1 alx
ahci                   36864  0
nvme_core              57344  3 nvme
libahci                32768  1 ahci
wmi                    16384  1 mxm_wmi
pinctrl_sunrisepoint    28672  0
video                  40960  1 i915
i2c_hid                20480  0
pinctrl_intel          20480  1 pinctrl_sunrisepoint
hid                   114688  6 i2c_hid,hid_generic,usbhid,hid_logitech_dj,hid_logitech_hidpp
```
==============================================================================================
&#10140; ```
 ~ cat /etc/resolv.conf
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
# 127.0.0.53 is the systemd-resolved stub resolver.
# run "systemd-resolve --status" to see details about the actual nameservers.

nameserver 127.0.0.53
```
===================================================================================================

&#10140;```
  ~ ifconfig -a
enp0s31f6: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.0.4  netmask 255.255.255.0  broadcast 192.168.0.255
        inet6 fe80::789f:7e9c:6d01:5c7  prefixlen 64  scopeid 0x20<link>
        ether 1c:1b:0d:93:b4:c0  txqueuelen 1000  (Ethernet)
        RX packets 69151  bytes 52259556 (52.2 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 62146  bytes 11088562 (11.0 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
        device interrupt 16  memory 0xed200000-ed220000  

enp5s0: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        ether 1c:1b:0d:93:b4:be  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
        device interrupt 18  

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 731  bytes 88498 (88.4 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 731  bytes 88498 (88.4 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

wlx28c68ef84a5b: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        ether f6:1c:28:65:6e:52  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
```
===================================================================================
```
&#10140;  ~ iwconfig
wlx28c68ef84a5b  IEEE 802.11  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          
enp0s31f6  no wireless extensions.

enp5s0    no wireless extensions.

lo        no wireless extensions.
```
============================================
&#10140;  ~ sudo iwlist scan

```
wlx28c68ef84a5b  No scan results

enp0s31f6  Interface doesn't support scanning.

enp5s0    Interface doesn't support scanning.

lo        Interface doesn't support scanning.
```


=============================================
out put of tail -f /var/log/syslog when trying to connect to wireless AP


```
Sep  8 18:55:42 codexian-pc NetworkManager[929]: <info>  [1504877142.5307] device (wlx28c68ef84a5b): supplicant interface state: disconnected -> inactive
Sep  8 18:56:26 codexian-pc NetworkManager[929]: <info>  [1504877186.0404] device (wlx28c68ef84a5b): Activation: starting connection 'ZTE944D3E' (5ab03cde-1736-4dcd-b845-1e028193c04b)
Sep  8 18:56:26 codexian-pc NetworkManager[929]: <info>  [1504877186.0406] audit: op="connection-activate" uuid="5ab03cde-1736-4dcd-b845-1e028193c04b" name="ZTE944D3E" pid=2926 uid=1000 result="success"
Sep  8 18:56:26 codexian-pc NetworkManager[929]: <info>  [1504877186.0409] device (wlx28c68ef84a5b): state change: disconnected -> prepare (reason 'none') [30 40 0]
Sep  8 18:56:26 codexian-pc NetworkManager[929]: <info>  [1504877186.0464] device (wlx28c68ef84a5b): set-hw-addr: set-cloned MAC address to 28:C6:8E:F8:4A:5B (permanent)
Sep  8 18:56:26 codexian-pc kernel: [ 1966.869950] rtl8192cu: MAC auto ON okay!
Sep  8 18:56:26 codexian-pc kernel: [ 1966.880952] rtl8192cu: Tx queue select: 0x05
Sep  8 18:56:26 codexian-pc NetworkManager[929]: <info>  [1504877186.4365] device (wlx28c68ef84a5b): state change: prepare -> config (reason 'none') [40 50 0]
Sep  8 18:56:26 codexian-pc kernel: [ 1967.258005] IPv6: ADDRCONF(NETDEV_UP): wlx28c68ef84a5b: link is not ready
Sep  8 18:56:26 codexian-pc NetworkManager[929]: <info>  [1504877186.4366] device (wlx28c68ef84a5b): Activation: (wifi) access point 'ZTE944D3E' has security, but secrets are required.
Sep  8 18:56:26 codexian-pc NetworkManager[929]: <info>  [1504877186.4366] device (wlx28c68ef84a5b): state change: config -> need-auth (reason 'none') [50 60 0]
Sep  8 18:56:26 codexian-pc NetworkManager[929]: <info>  [1504877186.4392] device (wlx28c68ef84a5b): state change: need-auth -> prepare (reason 'none') [60 40 0]
Sep  8 18:56:26 codexian-pc NetworkManager[929]: <info>  [1504877186.4394] device (wlx28c68ef84a5b): state change: prepare -> config (reason 'none') [40 50 0]
Sep  8 18:56:26 codexian-pc NetworkManager[929]: <info>  [1504877186.4395] device (wlx28c68ef84a5b): Activation: (wifi) connection 'ZTE944D3E' has security, and secrets exist.  No new secrets needed.
Sep  8 18:56:26 codexian-pc NetworkManager[929]: <info>  [1504877186.4395] Config: added 'ssid' value 'ZTE944D3E'
Sep  8 18:56:26 codexian-pc NetworkManager[929]: <info>  [1504877186.4395] Config: added 'scan_ssid' value '1'
Sep  8 18:56:26 codexian-pc NetworkManager[929]: <info>  [1504877186.4395] Config: added 'key_mgmt' value 'WPA-PSK'
Sep  8 18:56:26 codexian-pc NetworkManager[929]: <info>  [1504877186.4395] Config: added 'auth_alg' value 'OPEN'
Sep  8 18:56:26 codexian-pc NetworkManager[929]: <info>  [1504877186.4395] Config: added 'psk' value '<omitted>'
Sep  8 18:56:26 codexian-pc NetworkManager[929]: <info>  [1504877186.4403] sup-iface[0x55d023718090,wlx28c68ef84a5b]: config: set interface ap_scan to 1
Sep  8 18:56:26 codexian-pc NetworkManager[929]: <info>  [1504877186.4494] device (wlx28c68ef84a5b): supplicant interface state: inactive -> scanning
Sep  8 18:56:27 codexian-pc wpa_supplicant[1311]: wlx28c68ef84a5b: SME: Trying to authenticate with c8:64:c7:94:4d:3e (SSID='ZTE944D3E' freq=2412 MHz)
Sep  8 18:56:27 codexian-pc kernel: [ 1968.211350] wlx28c68ef84a5b: authenticate with c8:64:c7:94:4d:3e
Sep  8 18:56:27 codexian-pc NetworkManager[929]: <info>  [1504877187.4118] device (wlx28c68ef84a5b): supplicant interface state: scanning -> authenticating
Sep  8 18:56:27 codexian-pc kernel: [ 1968.232912] wlx28c68ef84a5b: send auth to c8:64:c7:94:4d:3e (try 1/3)
Sep  8 18:56:27 codexian-pc kernel: [ 1968.249511] wlx28c68ef84a5b: authenticated
Sep  8 18:56:32 codexian-pc kernel: [ 1973.238020] wlx28c68ef84a5b: aborting authentication with c8:64:c7:94:4d:3e by local choice (Reason: 3=DEAUTH_LEAVING)
Sep  8 18:56:32 codexian-pc wpa_supplicant[1311]: wlx28c68ef84a5b: CTRL-EVENT-SSID-TEMP-DISABLED id=0 ssid="ZTE944D3E" auth_failures=1 duration=10 reason=CONN_FAILED
Sep  8 18:56:32 codexian-pc NetworkManager[929]: <info>  [1504877192.4330] device (wlx28c68ef84a5b): supplicant interface state: authenticating -> disconnected
Sep  8 18:56:42 codexian-pc NetworkManager[929]: <info>  [1504877202.4411] device (wlx28c68ef84a5b): supplicant interface state: disconnected -> scanning
Sep  8 18:56:43 codexian-pc wpa_supplicant[1311]: wlx28c68ef84a5b: CTRL-EVENT-SSID-REENABLED id=0 ssid="ZTE944D3E"
Sep  8 18:56:43 codexian-pc wpa_supplicant[1311]: wlx28c68ef84a5b: SME: Trying to authenticate with c8:64:c7:94:4d:3e (SSID='ZTE944D3E' freq=2412 MHz)
Sep  8 18:56:43 codexian-pc kernel: [ 1984.195520] wlx28c68ef84a5b: authenticate with c8:64:c7:94:4d:3e
Sep  8 18:56:43 codexian-pc NetworkManager[929]: <info>  [1504877203.3958] device (wlx28c68ef84a5b): supplicant interface state: scanning -> authenticating
Sep  8 18:56:43 codexian-pc kernel: [ 1984.216813] wlx28c68ef84a5b: send auth to c8:64:c7:94:4d:3e (try 1/3)
Sep  8 18:56:43 codexian-pc kernel: [ 1984.240362] wlx28c68ef84a5b: authenticated
Sep  8 18:56:48 codexian-pc kernel: [ 1989.220724] wlx28c68ef84a5b: aborting authentication with c8:64:c7:94:4d:3e by local choice (Reason: 3=DEAUTH_LEAVING)
Sep  8 18:56:48 codexian-pc wpa_supplicant[1311]: wlx28c68ef84a5b: CTRL-EVENT-SSID-TEMP-DISABLED id=0 ssid="ZTE944D3E" auth_failures=2 duration=20 reason=CONN_FAILED
Sep  8 18:56:48 codexian-pc NetworkManager[929]: <info>  [1504877208.4156] device (wlx28c68ef84a5b): supplicant interface state: authenticating -> disconnected
Sep  8 18:56:52 codexian-pc NetworkManager[929]: <warn>  [1504877212.1868] device (wlx28c68ef84a5b): Activation: (wifi) association took too long, failing activation
Sep  8 18:56:52 codexian-pc NetworkManager[929]: <info>  [1504877212.1869] device (wlx28c68ef84a5b): state change: config -> failed (reason 'ssid-not-found') [50 120 53]
Sep  8 18:56:52 codexian-pc NetworkManager[929]: <warn>  [1504877212.1883] device (wlx28c68ef84a5b): Activation: failed for connection 'ZTE944D3E'
Sep  8 18:56:52 codexian-pc NetworkManager[929]: <info>  [1504877212.1892] device (wlx28c68ef84a5b): state change: failed -> disconnected (reason 'none') [120 30 0]
Sep  8 18:56:52 codexian-pc kernel: [ 1993.011482] IPv6: ADDRCONF(NETDEV_UP): wlx28c68ef84a5b: link is not ready
Sep  8 18:56:52 codexian-pc NetworkManager[929]: <info>  [1504877212.1950] device (wlx28c68ef84a5b): set-hw-addr: set MAC address to 6E:C2:F0:40:18:60 (scanning)
Sep  8 18:56:52 codexian-pc kernel: [ 1993.018342] rtl8192cu: MAC auto ON okay!
Sep  8 18:56:52 codexian-pc kernel: [ 1993.029452] rtl8192cu: Tx queue select: 0x05
Sep  8 18:56:52 codexian-pc kernel: [ 1993.406474] IPv6: ADDRCONF(NETDEV_UP): wlx28c68ef84a5b: link is not ready
Sep  8 18:56:53 codexian-pc NetworkManager[929]: <info>  [1504877213.5268] device (wlx28c68ef84a5b): supplicant interface state: disconnected -> inactive
```

---

### Post by chili555 on 2017-09-08
This is exactly the issue and the exact solution that I suggest: [https://askubuntu.com/questions/947648/edimax-usb-wifi-ew-7811un-not-connecting-on-17-04/947652#947652](https://askubuntu.com/questions/947648/edimax-usb-wifi-ew-7811un-not-connecting-on-17-04/947652#947652)

---

### Post by chown2 on 2017-09-12
Followed these steps :

Try1: 

[COLOR=#111111][FONT=Consolas]lsmod | grep rtl
[/FONT][/COLOR][COLOR=#111111][FONT=Consolas]sudo -i
[/FONT][/COLOR][COLOR=#111111][FONT=Consolas]echo "blacklist rtl8192cu"  >>  /etc/modprobe.d/blacklist.conf
[/FONT][/COLOR][COLOR=#111111][FONT=Consolas]exit
[/FONT][/COLOR]sudo nano /etc/NetworkManager/NetworkManager.conf
Added new section
[device]
wifi.scan-rand-mac-address=no
Rebooted , Result All access points are gone 

Try 2:

[COLOR=#111111][FONT=Consolas]lsmod | grep rtl
[/FONT][/COLOR][COLOR=#111111][FONT=Consolas]sudo -i
[/FONT][/COLOR][COLOR=#111111][FONT=Consolas]echo "blacklist [/FONT][/COLOR][COLOR=#000000]rtl8xxxu[/COLOR][COLOR=#111111][FONT=Consolas]" >> /etc/modprobe.d/blacklist.conf
[/FONT][/COLOR][COLOR=#111111][FONT=Consolas]exit
[/FONT][/COLOR]sudo nano /etc/NetworkManager/NetworkManager.conf
Added new section
[device]
wifi.scan-rand-mac-address=no
Rebooted , Result All access points are gone 

Try 3:

[COLOR=#111111][FONT=Consolas]sudo nano /etc/modprobe.d/blacklist.conf
[/FONT][/COLOR]removed all previously blocked rtl driver

Added new section
[device]
wifi.scan-rand-mac-address=no[FONT=Verdana]Rebooted and voilla!!!! APs are showing and i was able to connect   , There were no rtl drivers disabled  but one thing i noticed  that output of [/FONT][COLOR=#111111]lsmod | grep rtl   [/COLOR][FONT=Verdana]did not had entry of [/FONT][COLOR=#000000]rtl8xxxu 126976 0  [/COLOR][FONT=Verdana]any more             [/FONT]

---

### Post by chown2 on 2017-09-12
Please mark this thread as fixed so it will be helpful for others too

---

