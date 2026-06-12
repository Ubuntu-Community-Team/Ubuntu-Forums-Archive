---
title: "Wifi drivers for TPLINK T4UH V2 AC1300 not working"
date: 2018-04-17
forum: Networking &amp; Wireless
---

### Post by adelpozoman-f on 2018-04-17
Hi, yesterday I bought the TPLINK T4UH V2 AC1300 wich is supposed to have the rtl8812au chip inside it. I tried the drivers of these 2 repositories without luck (make, then sudo make install).
[https://github.com/abperiasamy/rtl8812AU_8821AU_linux](https://github.com/abperiasamy/rtl8812AU_8821AU_linux)
[https://github.com/ptpt52/rtl8812au](https://github.com/ptpt52/rtl8812au)
I restarted and got no wifi options anywhere. I tried this single debian package, but it didnt work:
[https://www.ubuntuupdates.org/package/core/xenial/universe/base/rtl8812au-dkms](https://www.ubuntuupdates.org/package/core/xenial/universe/base/rtl8812au-dkms)

My system is kubuntu 17.10, kernel 4.13.0-38-generic, ryzen cpu, radeon 7950 gpu with opensource mesa and 8 gb ram. Actually using an ethernet cable from my netbook.



Here are some output for troubleshooting:

lsusb
```

Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 002: ID 1908:2070 GEMBIRD
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 002: ID 2357:010e 
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 046d:c31c Logitech, Inc. Keyboard K120
Bus 001 Device 004: ID 1d57:ad17 Xenta
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

lsmod
```

Module                  Size  Used by
joydev                 20480  0
input_leds             16384  0
snd_hda_codec_realtek    98304  1
snd_hda_codec_generic    73728  1 snd_hda_codec_realtek
edac_mce_amd           28672  0
kvm                   589824  0
irqbypass              16384  1 kvm
crct10dif_pclmul       16384  0
crc32_pclmul           16384  0
ghash_clmulni_intel    16384  0
snd_hda_codec_hdmi     49152  1
snd_usb_audio         196608  2
pcbc                   16384  0
snd_hda_intel          40960  5
snd_usbmidi_lib        32768  1 snd_usb_audio
snd_hda_codec         126976  4 snd_hda_intel,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec_realtek
aesni_intel           188416  0
snd_hda_core           81920  5 snd_hda_intel,snd_hda_codec,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec_realtek
snd_hwdep              20480  2 snd_hda_codec,snd_usb_audio
aes_x86_64             20480  1 aesni_intel
crypto_simd            16384  1 aesni_intel
glue_helper            16384  1 aesni_intel
snd_pcm                98304  5 snd_hda_intel,snd_hda_codec,snd_usb_audio,snd_hda_core,snd_hda_codec_hdmi
cryptd                 24576  3 crypto_simd,ghash_clmulni_intel,aesni_intel
snd_seq_midi           16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            32768  2 snd_seq_midi,snd_usbmidi_lib
snd_seq                65536  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
wmi_bmof               16384  0
snd_timer              32768  2 snd_seq,snd_pcm
i2c_piix4              24576  0
ccp                    73728  0
snd                    81920  27 snd_hda_intel,snd_hwdep,snd_seq,snd_hda_codec,snd_usb_audio,snd_timer,snd_rawmidi,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_usbmidi_lib,snd_seq_device,snd_hda_codec_realtek,snd_pcm
soundcore              16384  1 snd
shpchp                 36864  0
8250_dw                16384  0
mac_hid                16384  0
parport_pc             32768  1
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,parport_pc,ppdev
ip_tables              24576  0
x_tables               40960  1 ip_tables
autofs4                40960  2
amdgpu               2019328  0
hid_generic            16384  0
usbhid                 49152  0
hid                   118784  2 hid_generic,usbhid
amdkfd                188416  1
amd_iommu_v2           20480  1 amdkfd
radeon               1478656  35
i2c_algo_bit           16384  2 amdgpu,radeon
ttm                    94208  2 amdgpu,radeon
drm_kms_helper        167936  2 amdgpu,radeon
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
fb_sys_fops            16384  1 drm_kms_helper
drm                   360448  15 amdgpu,radeon,ttm,drm_kms_helper
r8169                  86016  0
ahci                   36864  3
mii                    16384  1 r8169
libahci                32768  1 ahci
wmi                    24576  1 wmi_bmof
gpio_amdpt             16384  0
gpio_generic           16384  1 gpio_amdpt

```


iwconfig
```

enp3s0    no wireless extensions.

lo        no wireless extensions.


```


Any help is appreciated, please.
I would like to come back to Linux but this is very frustrating.

---

### Post by jeremy31 on 2018-04-17
*Thread moved to **Networking & Wireless**.*

What happens if you try ```
sudo modprobe 8812au
```

---

### Post by chili555 on 2018-04-17
As well, please show Jeremy:```
modinfo 8812au | grep 010E
```Jeremy will probably want to tweak the usb_intf.c file a bit!

---

### Post by jeremy31 on 2018-04-17
abperiasamy's github has the ID ```
	{USB_DEVICE(0x2357, 0x010E),.driver_info = RTL8812}, /* TP-Link - Archer T4UH AC1300 */
```
So either Secure Boot is enabled, or something else is going on

---

### Post by adelpozoman-f on 2018-04-21
sorry for late reply. At last sudo make install for the mod at [https://github.com/abperiasamy/rtl8812AU_8821AU_linux](https://github.com/abperiasamy/rtl8812AU_8821AU_linux) worked and now I can see the wifi networks, but cant connect to them.


sudo modprobe rtl8812au doesnt output anything (I suppose that is good?), and sudo modprobe rtl8812au.ko gives
```
modprobe: FATAL: Module rtl8812au.ko not found in directory /lib/modules/4.13.0-38-generic

```
I dont know if that is good.


modinfo rtl8812au | grep 010E
```
alias:          usb:v2357p010Ed*dc*dsc*dp*ic*isc*ip*in*
```


When trying to connect it keeps at "Configuring interface" and then asks for the password in a loop.


Mokutil says EFI variables not supported in this system.


Here is what I got while trying to connect at ksyslog:
```

21/4/18 11:00    NetworkManager    <info>  [1524301229.1610] keyfile: add connection in-memory (2c592f50-4bab-4406-891a-58dcf4bae78b,"Orange-919A")
21/4/18 11:00    NetworkManager    <info>  [1524301229.1640] device (wlx7c8bca0f3035): Activation: starting connection 'Orange-919A' (2c592f50-4bab-4406-891a-58dcf4bae78b)
21/4/18 11:00    NetworkManager    <info>  [1524301229.1795] keyfile: update /etc/NetworkManager/system-connections/Orange-919A (2c592f50-4bab-4406-891a-58dcf4bae78b,"Orange-919A") and persist connection
21/4/18 11:00    NetworkManager    <info>  [1524301229.1806] keyfile: update /etc/NetworkManager/system-connections/Orange-919A (2c592f50-4bab-4406-891a-58dcf4bae78b,"Orange-919A") after persisting connection
21/4/18 11:00    NetworkManager    <info>  [1524301229.1808] audit: op="connection-add-activate" uuid="2c592f50-4bab-4406-891a-58dcf4bae78b" name="Orange-919A" pid=1119 uid=1000 result="success"
21/4/18 11:00    NetworkManager    <info>  [1524301229.1857] device (wlx7c8bca0f3035): state change: disconnected -> prepare (reason 'none', internal state 'managed')
21/4/18 11:00    NetworkManager    <info>  [1524301229.1858] manager: NetworkManager state is now CONNECTING
21/4/18 11:00    NetworkManager    <info>  [1524301229.1865] device (wlx7c8bca0f3035): state change: prepare -> config (reason 'none', internal state 'managed')
21/4/18 11:00    NetworkManager    <info>  [1524301229.1870] device (wlx7c8bca0f3035): Activation: (wifi) access point 'Orange-919A' has security, but secrets are required.
21/4/18 11:00    NetworkManager    <info>  [1524301229.1871] device (wlx7c8bca0f3035): state change: config -> need-auth (reason 'none', internal state 'managed')
21/4/18 11:00    NetworkManager    <info>  [1524301233.2782] device (wlx7c8bca0f3035): state change: need-auth -> prepare (reason 'none', internal state 'managed')
21/4/18 11:00    NetworkManager    <info>  [1524301233.2795] device (wlx7c8bca0f3035): state change: prepare -> config (reason 'none', internal state 'managed')
21/4/18 11:00    NetworkManager    <info>  [1524301233.2799] device (wlx7c8bca0f3035): Activation: (wifi) connection 'Orange-919A' has security, and secrets exist.  No new secrets needed.
21/4/18 11:00    NetworkManager    <info>  [1524301233.2799] Config: added 'ssid' value 'Orange-919A'
21/4/18 11:00    NetworkManager    <info>  [1524301233.2800] Config: added 'scan_ssid' value '1'
21/4/18 11:00    NetworkManager    <info>  [1524301233.2800] Config: added 'key_mgmt' value 'WPA-PSK'
21/4/18 11:00    NetworkManager    <info>  [1524301233.2800] Config: added 'auth_alg' value 'OPEN'
21/4/18 11:00    NetworkManager    <info>  [1524301233.2800] Config: added 'psk' value '<hidden>'
21/4/18 11:00    wpa_supplicant    wlx7c8bca0f3035: Trying to associate with d4:63:fe:9c:91:9c (SSID='Orange-919A' freq=2462 MHz)
21/4/18 11:00    NetworkManager    <info>  [1524301234.3905] device (wlx7c8bca0f3035): supplicant interface state: inactive -> associating
21/4/18 11:00    kernel    RTL871X: rtw_set_802_11_connect(wlx7c8bca0f3035)  fw_state=0x00000008
21/4/18 11:00    wpa_supplicant    wlx7c8bca0f3035: CTRL-EVENT-ASSOC-REJECT status_code=1
21/4/18 11:00    wpa_supplicant    wlx7c8bca0f3035: CTRL-EVENT-ASSOC-REJECT status_code=1
21/4/18 11:00    NetworkManager    <info>  [1524301240.5253] device (wlx7c8bca0f3035): supplicant interface state: associating -> disconnected
21/4/18 11:00    NetworkManager    <info>  [1524301240.6255] device (wlx7c8bca0f3035): supplicant interface state: disconnected -> scanning
21/4/18 11:00    wpa_supplicant    wlx7c8bca0f3035: Trying to associate with d4:63:fe:9c:91:9c (SSID='Orange-919A' freq=2462 MHz)
21/4/18 11:00    kernel    RTL871X: rtw_set_802_11_connect(wlx7c8bca0f3035)  fw_state=0x00000008
21/4/18 11:00    NetworkManager    <info>  [1524301248.7325] device (wlx7c8bca0f3035): supplicant interface state: scanning -> associating
21/4/18 11:00    systemd    Starting Stop ureadahead data collection...
21/4/18 11:00    systemd    Started Stop ureadahead data collection.
21/4/18 11:00    wpa_supplicant    wlx7c8bca0f3035: CTRL-EVENT-ASSOC-REJECT status_code=1
21/4/18 11:00    NetworkManager    <info>  [1524301253.4633] device (wlx7c8bca0f3035): supplicant interface state: associating -> disconnected
21/4/18 11:00    NetworkManager    <warn>  [1524301258.6410] device (wlx7c8bca0f3035): Activation: (wifi) association took too long
21/4/18 11:00    NetworkManager    <info>  [1524301258.6411] device (wlx7c8bca0f3035): state change: config -> need-auth (reason 'none', internal state 'managed')
21/4/18 11:00    NetworkManager    <warn>  [1524301258.6440] device (wlx7c8bca0f3035): Activation: (wifi) asking for new secrets
21/4/18 11:01    NetworkManager    <info>  [1524301263.4825] device (wlx7c8bca0f3035): supplicant interface state: disconnected -> scanning
21/4/18 11:01    sudo    adelpozoman : TTY=pts/2 ; PWD=/home/adelpozoman ; USER=root ; COMMAND=/usr/lib/x86_64-linux-gnu/libexec/kf5/kdesu_stub -
21/4/18 11:01    sudo    pam_unix(sudo:session): session opened for user root by (uid=0)
21/4/18 11:01    sudo    pam_unix(sudo:session): session closed for user root
21/4/18 11:01    sudo    adelpozoman : TTY=pts/2 ; PWD=/home/adelpozoman ; USER=root ; COMMAND=/usr/lib/x86_64-linux-gnu/libexec/kf5/kdesu_stub -
21/4/18 11:01    sudo    pam_unix(sudo:session): session opened for user root by (uid=0)
21/4/18 11:01    NetworkManager    <info>  [1524301268.6290] device (wlx7c8bca0f3035): state change: need-auth -> prepare (reason 'none', internal state 'managed')
21/4/18 11:01    NetworkManager    <info>  [1524301268.6295] device (wlx7c8bca0f3035): state change: prepare -> config (reason 'none', internal state 'managed')
21/4/18 11:01    NetworkManager    <info>  [1524301268.6299] device (wlx7c8bca0f3035): Activation: (wifi) connection 'Orange-919A' has security, and secrets exist.  No new secrets needed.
21/4/18 11:01    NetworkManager    <info>  [1524301268.6300] Config: added 'ssid' value 'Orange-919A'
21/4/18 11:01    NetworkManager    <info>  [1524301268.6300] Config: added 'scan_ssid' value '1'
21/4/18 11:01    NetworkManager    <info>  [1524301268.6300] Config: added 'key_mgmt' value 'WPA-PSK'
21/4/18 11:01    NetworkManager    <info>  [1524301268.6300] Config: added 'auth_alg' value 'OPEN'
21/4/18 11:01    NetworkManager    <info>  [1524301268.6301] Config: added 'psk' value '<hidden>'
21/4/18 11:01    wpa_supplicant    wlx7c8bca0f3035: Trying to associate with d4:63:fe:9c:91:9c (SSID='Orange-919A' freq=2462 MHz)
21/4/18 11:01    NetworkManager    <info>  [1524301271.5136] device (wlx7c8bca0f3035): supplicant interface state: scanning -> associating
21/4/18 11:01    kernel    RTL871X: rtw_set_802_11_connect(wlx7c8bca0f3035)  fw_state=0x00000008
21/4/18 11:01    wpa_supplicant    wlx7c8bca0f3035: CTRL-EVENT-ASSOC-REJECT status_code=1
21/4/18 11:01    wpa_supplicant    wlx7c8bca0f3035: CTRL-EVENT-ASSOC-REJECT status_code=1
21/4/18 11:01    NetworkManager    <info>  [1524301279.9495] device (wlx7c8bca0f3035): supplicant interface state: associating -> disconnected
21/4/18 11:01    NetworkManager    <info>  [1524301280.9500] device (wlx7c8bca0f3035): supplicant interface state: disconnected -> scanning
21/4/18 11:01    wpa_supplicant    wlx7c8bca0f3035: Trying to associate with d4:63:fe:9c:91:9c (SSID='Orange-919A' freq=2462 MHz)
21/4/18 11:01    kernel    RTL871X: rtw_set_802_11_connect(wlx7c8bca0f3035)  fw_state=0x00000008
21/4/18 11:01    NetworkManager    <info>  [1524301289.1794] device (wlx7c8bca0f3035): supplicant interface state: scanning -> associating
21/4/18 11:01    wpa_supplicant    wlx7c8bca0f3035: CTRL-EVENT-ASSOC-REJECT status_code=1
21/4/18 11:01    wpa_supplicant    wlx7c8bca0f3035: CTRL-EVENT-SSID-TEMP-DISABLED id=0 ssid="Orange-919A" auth_failures=1 duration=10 reason=CONN_FAILED
21/4/18 11:01    NetworkManager    <info>  [1524301291.2960] device (wlx7c8bca0f3035): supplicant interface state: associating -> disconnected
21/4/18 11:01    NetworkManager    <warn>  [1524301293.6413] device (wlx7c8bca0f3035): Activation: (wifi) association took too long
21/4/18 11:01    NetworkManager    <info>  [1524301293.6414] device (wlx7c8bca0f3035): state change: config -> need-auth (reason 'none', internal state 'managed')
21/4/18 11:01    NetworkManager    <warn>  [1524301293.6441] device (wlx7c8bca0f3035): Activation: (wifi) asking for new secrets
21/4/18 11:01    NetworkManager    <warn>  [1524301294.9732] device (wlx7c8bca0f3035): User canceled the secrets request.
21/4/18 11:01    NetworkManager    <info>  [1524301294.9732] device (wlx7c8bca0f3035): state change: need-auth -> failed (reason 'no-secrets', internal state 'managed')
21/4/18 11:01    NetworkManager    <info>  [1524301294.9736] manager: NetworkManager state is now DISCONNECTED
21/4/18 11:01    NetworkManager    <warn>  [1524301294.9742] device (wlx7c8bca0f3035): Activation: failed for connection 'Orange-919A'
21/4/18 11:01    NetworkManager    <info>  [1524301294.9769] device (wlx7c8bca0f3035): state change: failed -> disconnected (reason 'none', internal state 'managed')
21/4/18 11:01    kernel    IPv6: ADDRCONF(NETDEV_UP): wlx7c8bca0f3035: link is not ready
21/4/18 11:01    NetworkManager    <info>  [1524301299.0842] keyfile: update /etc/NetworkManager/system-connections/Orange-919A (2c592f50-4bab-4406-891a-58dcf4bae78b,"Orange-919A")
21/4/18 11:01    NetworkManager    <info>  [1524301299.0853] keyfile: update /etc/NetworkManager/system-connections/Orange-919A (2c592f50-4bab-4406-891a-58dcf4bae78b,"Orange-919A") after persisting connection
21/4/18 11:01    NetworkManager    <info>  [1524301299.0859] audit: op="connection-update" uuid="2c592f50-4bab-4406-891a-58dcf4bae78b" name="Orange-919A" args="802-11-wireless.mac-address,802-11-wireless-security.auth-alg,802-11-wireless-security.psk" pid=1429 uid=1000 result="success"
21/4/18 11:01    NetworkManager    <info>  [1524301312.7161] device (wlx7c8bca0f3035): supplicant interface state: disconnected -> inactive
21/4/18 11:01    NetworkManager    <info>  [1524301315.7464] device (wlx7c8bca0f3035): Activation: starting connection 'Orange-919A' (2c592f50-4bab-4406-891a-58dcf4bae78b)
21/4/18 11:01    NetworkManager    <info>  [1524301315.7466] audit: op="connection-activate" uuid="2c592f50-4bab-4406-891a-58dcf4bae78b" name="Orange-919A" pid=1119 uid=1000 result="success"
21/4/18 11:01    NetworkManager    <info>  [1524301315.7470] device (wlx7c8bca0f3035): state change: disconnected -> prepare (reason 'none', internal state 'managed')
21/4/18 11:01    NetworkManager    <info>  [1524301315.7473] manager: NetworkManager state is now CONNECTING
21/4/18 11:01    NetworkManager    <info>  [1524301315.7484] device (wlx7c8bca0f3035): state change: prepare -> config (reason 'none', internal state 'managed')
21/4/18 11:01    NetworkManager    <info>  [1524301315.7489] device (wlx7c8bca0f3035): Activation: (wifi) access point 'Orange-919A' has security, but secrets are required.
21/4/18 11:01    NetworkManager    <info>  [1524301315.7489] device (wlx7c8bca0f3035): state change: config -> need-auth (reason 'none', internal state 'managed')
21/4/18 11:01    NetworkManager    <info>  [1524301315.7663] device (wlx7c8bca0f3035): state change: need-auth -> prepare (reason 'none', internal state 'managed')
21/4/18 11:01    NetworkManager    <info>  [1524301315.7667] device (wlx7c8bca0f3035): state change: prepare -> config (reason 'none', internal state 'managed')
21/4/18 11:01    NetworkManager    <info>  [1524301315.7669] device (wlx7c8bca0f3035): Activation: (wifi) connection 'Orange-919A' has security, and secrets exist.  No new secrets needed.
21/4/18 11:01    NetworkManager    <info>  [1524301315.7670] Config: added 'ssid' value 'Orange-919A'
21/4/18 11:01    NetworkManager    <info>  [1524301315.7670] Config: added 'scan_ssid' value '1'
21/4/18 11:01    NetworkManager    <info>  [1524301315.7670] Config: added 'key_mgmt' value 'WPA-PSK'
21/4/18 11:01    NetworkManager    <info>  [1524301315.7670] Config: added 'psk' value '<hidden>'
21/4/18 11:02    wpa_supplicant    wlx7c8bca0f3035: Trying to associate with d4:63:fe:9c:91:9c (SSID='Orange-919A' freq=2462 MHz)
21/4/18 11:02    NetworkManager    <info>  [1524301320.9248] device (wlx7c8bca0f3035): supplicant interface state: inactive -> associating
21/4/18 11:02    kernel    RTL871X: rtw_set_802_11_connect(wlx7c8bca0f3035)  fw_state=0x00000008
21/4/18 11:02    wpa_supplicant    wlx7c8bca0f3035: CTRL-EVENT-ASSOC-REJECT status_code=1
21/4/18 11:02    wpa_supplicant    wlx7c8bca0f3035: CTRL-EVENT-SSID-TEMP-DISABLED id=0 ssid="Orange-919A" auth_failures=1 duration=10 reason=CONN_FAILED
21/4/18 11:02    wpa_supplicant    wlx7c8bca0f3035: CTRL-EVENT-ASSOC-REJECT status_code=1
21/4/18 11:02    NetworkManager    <info>  [1524301329.8730] device (wlx7c8bca0f3035): supplicant interface state: associating -> disconnected
21/4/18 11:02    NetworkManager    <warn>  [1524301340.6409] device (wlx7c8bca0f3035): Activation: (wifi) association took too long
21/4/18 11:02    NetworkManager    <info>  [1524301340.6410] device (wlx7c8bca0f3035): state change: config -> need-auth (reason 'none', internal state 'managed')
21/4/18 11:02    NetworkManager    <warn>  [1524301340.6437] device (wlx7c8bca0f3035): Activation: (wifi) asking for new secrets
21/4/18 11:02    NetworkManager    <info>  [1524301345.7116] device (wlx7c8bca0f3035): state change: need-auth -> prepare (reason 'none', internal state 'managed')
21/4/18 11:02    NetworkManager    <info>  [1524301345.7132] device (wlx7c8bca0f3035): state change: prepare -> config (reason 'none', internal state 'managed')
21/4/18 11:02    NetworkManager    <info>  [1524301349.4855] device (wlx7c8bca0f3035): Activation: (wifi) connection 'Orange-919A' has security, and secrets exist.  No new secrets needed.
21/4/18 11:02    NetworkManager    <info>  [1524301349.4856] Config: added 'ssid' value 'Orange-919A'
21/4/18 11:02    NetworkManager    <info>  [1524301349.4856] Config: added 'scan_ssid' value '1'
21/4/18 11:02    NetworkManager    <info>  [1524301349.4856] Config: added 'key_mgmt' value 'WPA-PSK'
21/4/18 11:02    NetworkManager    <info>  [1524301349.4857] Config: added 'psk' value '<hidden>'
21/4/18 11:02    NetworkManager    <info>  [1524301349.4907] device (wlx7c8bca0f3035): supplicant interface state: disconnected -> scanning
21/4/18 11:02    wpa_supplicant    wlx7c8bca0f3035: Trying to associate with d4:63:fe:9c:91:9c (SSID='Orange-919A' freq=2462 MHz)
21/4/18 11:02    NetworkManager    <info>  [1524301357.5325] device (wlx7c8bca0f3035): supplicant interface state: scanning -> associating
21/4/18 11:02    kernel    RTL871X: rtw_set_802_11_connect(wlx7c8bca0f3035)  fw_state=0x00000008
21/4/18 11:02    wpa_supplicant    wlx7c8bca0f3035: CTRL-EVENT-ASSOC-REJECT status_code=1
21/4/18 11:02    wpa_supplicant    wlx7c8bca0f3035: CTRL-EVENT-SSID-TEMP-DISABLED id=0 ssid="Orange-919A" auth_failures=1 duration=10 reason=CONN_FAILED
21/4/18 11:02    wpa_supplicant    wlx7c8bca0f3035: CTRL-EVENT-ASSOC-REJECT status_code=1
21/4/18 11:02    NetworkManager    <info>  [1524301365.9657] device (wlx7c8bca0f3035): supplicant interface state: associating -> disconnected
21/4/18 11:02    dbus    [system] Activating service name='org.debian.AptXapianIndex' (using servicehelper)
21/4/18 11:02    dbus    [system] Successfully activated service 'org.debian.AptXapianIndex'
21/4/18 11:02    dbus    [system] Rejected send message, 3 matched rules; type="method_return", sender=":1.59" (uid=0 pid=1455 comm="/usr/bin/python3 /usr/share/apt-xapian-index/updat") interface="(unset)" member="(unset)" error name="(unset)" requested_reply="0" destination=":1.24" (uid=1000 pid=1073 comm="kded5 [kdeinit5]                                  ")
21/4/18 11:02    NetworkManager    <warn>  [1524301374.6396] device (wlx7c8bca0f3035): Activation: (wifi) association took too long
21/4/18 11:02    NetworkManager    <info>  [1524301374.6396] device (wlx7c8bca0f3035): state change: config -> need-auth (reason 'none', internal state 'managed')
21/4/18 11:02    NetworkManager    <warn>  [1524301374.6409] device (wlx7c8bca0f3035): Activation: (wifi) asking for new secrets
21/4/18 11:02    NetworkManager    <info>  [1524301375.9665] device (wlx7c8bca0f3035): supplicant interface state: disconnected -> inactive
21/4/18 11:03    kernel    r8169 0000:03:00.0 enp3s0: link up
21/4/18 11:03    kernel    IPv6: ADDRCONF(NETDEV_CHANGE): enp3s0: link becomes ready
21/4/18 11:03    NetworkManager    <info>  [1524301417.4188] device (enp3s0): link connected
21/4/18 11:03    NetworkManager    <info>  [1524301417.4193] device (enp3s0): state change: unavailable -> disconnected (reason 'carrier-changed', internal state 'managed')
21/4/18 11:03    NetworkManager    <warn>  [1524301421.8005] device (wlx7c8bca0f3035): User canceled the secrets request.
21/4/18 11:03    NetworkManager    <info>  [1524301421.8005] device (wlx7c8bca0f3035): state change: need-auth -> failed (reason 'no-secrets', internal state 'managed')
21/4/18 11:03    NetworkManager    <info>  [1524301421.8009] manager: NetworkManager state is now DISCONNECTED
21/4/18 11:03    NetworkManager    <warn>  [1524301421.8015] device (wlx7c8bca0f3035): Activation: failed for connection 'Orange-919A'



```

---

### Post by chili555 on 2018-04-21
Have you tried all the suggested tweaks? [https://askubuntu.com/questions/1026395/ubuntu-16-04-internet-drops-within-few-seconds/1026426#1026426](https://askubuntu.com/questions/1026395/ubuntu-16-04-internet-drops-within-few-seconds/1026426#1026426)

---

### Post by adelpozoman-f on 2018-04-22
My region is good (spain) 
(sudo iw reg get)
```

global
country ES: DFS-ETSI
        (2400 - 2483 @ 40), (N/A, 20), (N/A)
        (5150 - 5250 @ 80), (N/A, 23), (N/A), NO-OUTDOOR, AUTO-BW
        (5250 - 5350 @ 80), (N/A, 20), (0 ms), NO-OUTDOOR, DFS, AUTO-BW
        (5470 - 5725 @ 160), (N/A, 26), (0 ms), DFS
        (57000 - 66000 @ 2160), (N/A, 40), (N/A)

```

I configured the 2.4 ghz beacon at channel 6 and 5 ghz one at 36, both only with 20 MHz.
2.4 GHz band has mixed 11g + 11n, while 5GHz hast mixed 11a+11n+11ac.
I dont know what to choose between them.
Both using only WPA2, and WPS feature is enabled

---

### Post by chili555 on 2018-04-22
> 2.4 GHz band has mixed 11g + 11nI hope it has mixed 11b, 11g and 11n, which is what I suggest that you select.

---

### Post by adelpozoman-f on 2018-04-23
Done, and still nothing

---

### Post by adelpozoman-f on 2018-04-26
UPDATE:
I did make clean, then make, then sudo make install and now I see this on the networks screen:


[IMG]https://i.imgur.com/W2RVsXA.png[/IMG]

Still unable to join any network, even the one from my phone. It keeps "configuring interface".

EDIT: Here is some (strange?) output of iwconfig:

```
enp3s0    no wireless extensions.

wlp1s0f0u2  unassociated  Nickname:"<WIFI@REALTEK>"
          Mode:Managed  Frequency=2.412 GHz  Access Point: Not-Associated   
          Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

wlx7c8bca0f3035  unassociated  Nickname:"<WIFI@REALTEK>"
          Mode:Managed  Frequency=2.412 GHz  Access Point: Not-Associated   
          Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

lo        no wireless extensions.
```


Any help is appreciated

---

### Post by adelpozoman-f on 2018-04-28
OK so can someone tell me some Wireless USB adapter that works (or has working drivers) for linux?

---

### Post by chili555 on 2018-04-30
We are confused. Do you have two wireless devices?> [COLOR="#FF0000"]wlp1s0f0u2[/COLOR]  unassociated  Nickname:"<WIFI@REALTEK>"
          Mode:Managed  Frequency=2.412 GHz  Access Point: Not-Associated   
          Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

[COLOR="#FF0000"]wlx7c8bca0f3035[/COLOR]  unassociated  Nickname:"<WIFI@REALTEK>"
          Mode:Managed  Frequency=2.412 GHz  Access Point: Not-Associated   
          Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0Why not just concentrate on the internal device and get it working?

May we see:```
lspci -nnk | grep 0280 -A3
lsmod | grep -e rtl -e 8812
```If you have two Realtek devices running at once, I am quite confident that the drivers conflict.

---

### Post by adelpozoman-f on 2018-05-01
UPDATED: ITs now solved!!.
I tried these drivers: [https://www.erol.name/compile-realtek-rtl8812au8821au-usb-wifi-driver-debian-jessie/](https://www.erol.name/compile-realtek-rtl8812au8821au-usb-wifi-driver-debian-jessie/)
, then [https://github.com/mk-fg/rtl8812au](https://github.com/mk-fg/rtl8812au)
and then [https://github.com/gnab/rtl8812au](https://github.com/gnab/rtl8812au).
None of them worked so I tried again: [https://github.com/abperiasamy/rtl8812AU_8821AU_linux](https://github.com/abperiasamy/rtl8812AU_8821AU_linux)
It worked for 1 minute!. Then it disconnected and started the "Configuring interface" loop. So I restarted and now it works!!! Sometimes it wants the loop again, so I disconnect the USB Dongle and reconnect it again until it works! Fantastic!. Here are some output if it can help someone:

Album:
[https://imgur.com/a/5IL3BKx](https://imgur.com/a/5IL3BKx)

---

### Post by adelpozoman-f on 2018-05-01
oh @chili555 sorry; I didnt notice about the 2nd page of the thread. I think there are 2 options because the T4UH V2 is dualband. I can confirm now that when using abperiasamy drivers and reconnecting it multiple times it works, and even at windows-like speed. Thanks for the help.
By the way, lspci -nnk | grep 0280 -A3 gives no output. 
Curiously        lsmod | grep -e rtl -e 8812   gives:
```

rtl8812au            1359872  0
cfg80211              622592  1 rtl8812au

```

---

### Post by adelpozoman-f on 2018-05-12
New update, because I'm going crazy about this. Usually it doesnt work, but after reconnecting 10-20 times then it works. This is not bearable and I am looking for a solution wherever I can. I+m using this driver:
[https://github.com/abperiasamy/rtl8812AU_8821AU_linux](https://github.com/abperiasamy/rtl8812AU_8821AU_linux)

On the journal, when failing to connect I get this:
```
12/5/18 20:05    NetworkManager    <info>  [1526148338.9611] device (wlx7c8bca0f3035): supplicant interface state: ready -> scanning
12/5/18 20:05    wpa_supplicant    wlx7c8bca0f3035: Trying to associate with d4:63:fe:9c:91:9c (SSID='Orange-919A' freq=2437 MHz)
12/5/18 20:05    NetworkManager    <info>  [1526148347.0714] device (wlx7c8bca0f3035): supplicant interface state: scanning -> associating
12/5/18 20:05    wpa_supplicant    wlx7c8bca0f3035: CTRL-EVENT-ASSOC-REJECT status_code=1
12/5/18 20:05    NetworkManager    <info>  [1526148353.7130] device (wlx7c8bca0f3035): supplicant interface state: associating -> disconnected
12/5/18 20:05    wpa_supplicant    wlx7c8bca0f3035: CTRL-EVENT-REGDOM-CHANGE init=CORE type=WORLD
12/5/18 20:05    wpa_supplicant    wlx7c8bca0f3035: CTRL-EVENT-REGDOM-CHANGE init=USER type=COUNTRY alpha2=ES
12/5/18 20:05    NetworkManager    <info>  [1526148353.8180] device (wlx7c8bca0f3035): supplicant interface state: disconnected -> scanning
12/5/18 20:06    wpa_supplicant    wlx7c8bca0f3035: Trying to associate with d4:63:fe:9c:91:9c (SSID='Orange-919A' freq=2437 MHz)
12/5/18 20:06    NetworkManager    <info>  [1526148361.9150] device (wlx7c8bca0f3035): supplicant interface state: scanning -> associating
12/5/18 20:06    NetworkManager    <warn>  [1526148364.6284] device (wlx7c8bca0f3035): Activation: (wifi) association took too long
12/5/18 20:06    NetworkManager    <info>  [1526148364.6284] device (wlx7c8bca0f3035): state change: config -> need-auth (reason 'none', sys-iface-state: 'managed')
12/5/18 20:06    NetworkManager    <info>  [1526148364.6287] sup-iface[0x556ab3739820,wlx7c8bca0f3035]: wps: type pbc start...
12/5/18 20:06    NetworkManager    <warn>  [1526148364.6308] device (wlx7c8bca0f3035): Activation: (wifi) asking for new secrets
12/5/18 20:06    NetworkManager    <info>  [1526148364.6354] device (wlx7c8bca0f3035): state change: need-auth -> prepare (reason 'none', sys-iface-state: 'managed')
12/5/18 20:06    NetworkManager    <info>  [1526148364.6362] device (wlx7c8bca0f3035): state change: prepare -> config (reason 'none', sys-iface-state: 'managed')
12/5/18 20:06    wpa_supplicant    wlx7c8bca0f3035: CTRL-EVENT-DISCONNECTED bssid=d4:63:fe:9c:91:9c reason=3 locally_generated=1
12/5/18 20:06    NetworkManager    <info>  [1526148366.6398] device (wlx7c8bca0f3035): Activation: (wifi) connection 'Orange-919A' has security, and secrets exist.  No new secrets needed.
12/5/18 20:06    NetworkManager    <info>  [1526148366.6399] Config: added 'ssid' value 'Orange-919A'
12/5/18 20:06    NetworkManager    <info>  [1526148366.6399] Config: added 'scan_ssid' value '1'
12/5/18 20:06    NetworkManager    <info>  [1526148366.6400] Config: added 'bgscan' value 'simple:30:-80:86400'
12/5/18 20:06    NetworkManager    <info>  [1526148366.6400] Config: added 'key_mgmt' value 'WPA-PSK'
12/5/18 20:06    NetworkManager    <info>  [1526148366.6400] Config: added 'psk' value '<hidden>'

```

sudo modprobe rtl8812au: nothing
lspci -nnk | grep 0280 -A3: nothing
lsmod | grep -e rtl -e 8812: 
```
rtl8812au            1359872  0
cfg80211              622592  1 rtl8812au

```

Ifconfig:
```
enp3s0: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        ether 1c:1b:0d:9b:63:15  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 4749  bytes 333667 (333.6 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 4749  bytes 333667 (333.6 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

wlx7c8bca0f3035: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.1.101  netmask 255.255.255.0  broadcast 192.168.1.255
        inet6 fe80::7e8b:caff:fe0f:3035  prefixlen 64  scopeid 0x20<link>
        ether 7c:8b:ca:0f:30:35  txqueuelen 1000  (Ethernet)
        RX packets 2894  bytes 2477836 (2.4 MB)
        RX errors 0  dropped 898  overruns 0  frame 0
        TX packets 2026  bytes 614242 (614.2 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

```

iwconfig:
```
lo        no wireless extensions.

enp3s0    no wireless extensions.

wlx7c8bca0f3035  IEEE 802.11bgn  ESSID:"Orange-919A"  Nickname:"<WIFI@REALTEK>"
          Mode:Managed  Frequency:2.437 GHz  Access Point: D4:63:FE:9C:91:9C   
          Bit Rate:144.4 Mb/s   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=100/100  Signal level=74/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```

As always, any helps is appreciated, please. I will try whatever you suggest.

---

### Post by adelpozoman-f on 2018-05-17
SOLVED: Returned the TP link T4UH (realtek) and got the T6E (wich has a Broadcom chip and has propietary drivers available on Ubuntu).

---

