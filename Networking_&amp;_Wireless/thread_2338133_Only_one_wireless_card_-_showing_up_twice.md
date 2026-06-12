---
title: "Only one wireless card - showing up twice"
date: 2016-09-25
forum: Networking &amp; Wireless
---

### Post by h0l on 2016-09-25
Hi, my device is an i7 stylus, the build in wifi is a RTL8723B.

Yesterdas I did a fresh install of xubuntu, got the driver from here [https://github.com/lwfinger/rtl8723bu](https://github.com/lwfinger/rtl8723bu), seems all to be working fine, but: in the network manager, the card is listed twice. How can I remove one of entries?

[URL="http://i.imgur.com/4jTq1yx.png"]
  [IMG]http://imgur.com/4jTq1yxl.png[/IMG]
[/URL]

---

### Post by ajgreeny on 2016-09-25
Could that be that both the 2.4 GHz and also the 5 GHz networks are showing?

---

### Post by h0l on 2016-09-25
> **ajgreeny said:**
> Could that be that both the 2.4 GHz and also the 5 GHz networks are showing?

Nope, happens at my place as well, and my Netrworks are named ****2.4 and ****5. The 5 GHz Network does not show up at all, as far as I know the chip does not even support 5GHz.

---

### Post by jeremy31 on 2016-09-25
Post the result for ```
cat /etc/network/interfaces
```

---

### Post by h0l on 2016-09-25
```
# interfaces(5) file used by ifup(8) and ifdown(8)auto lo
iface lo inet loopback
```

Here you go

---

### Post by jeremy31 on 2016-09-25
See the wireless script link in my signature and post the contents of the wireless-info.txt file or attach the wireless-info.tar.gz file

---

### Post by h0l on 2016-09-25
> **jeremy31 said:**
> See the wireless script link in my signature and post the contents of the wireless-info.txt file or attach the wireless-info.tar.gz file

File was too large, so here you go: [http://paste.ubuntu.com/23228885/](http://paste.ubuntu.com/23228885/)

---

### Post by jeremy31 on 2016-09-25
What is the report for ```
grep [[:alnum:]] /sys/module/8723bu/parameters/*
```

---

### Post by h0l on 2016-09-25
> **jeremy31 said:**
> What is the report for ```
grep [[:alnum:]] /sys/module/8723bu/parameters/*
```
 ```
/sys/module/8723bu/parameters/if2name:wlan%d/sys/module/8723bu/parameters/ifname:wlan%d
/sys/module/8723bu/parameters/rtw_80211d:0
/sys/module/8723bu/parameters/rtw_adaptivity_en:2
/sys/module/8723bu/parameters/rtw_adaptivity_mode:0
/sys/module/8723bu/parameters/rtw_ampdu_amsdu:0
/sys/module/8723bu/parameters/rtw_ampdu_enable:1
/sys/module/8723bu/parameters/rtw_antdiv_cfg:2
/sys/module/8723bu/parameters/rtw_antdiv_type:0
/sys/module/8723bu/parameters/rtw_ant_num:-1
/sys/module/8723bu/parameters/rtw_btcoex_enable:1
/sys/module/8723bu/parameters/rtw_busy_thresh:40
/sys/module/8723bu/parameters/rtw_bw_mode:33
/sys/module/8723bu/parameters/rtw_channel:1
/sys/module/8723bu/parameters/rtw_channel_plan:88
/sys/module/8723bu/parameters/rtw_chip_version:0
/sys/module/8723bu/parameters/rtw_decrypt_phy_file:0
/sys/module/8723bu/parameters/rtw_enusbss:0
/sys/module/8723bu/parameters/rtw_hiq_filter:1
/sys/module/8723bu/parameters/rtw_ht_enable:1
/sys/module/8723bu/parameters/rtw_hwpdn_mode:2
/sys/module/8723bu/parameters/rtw_hwpwrp_detect:0
/sys/module/8723bu/parameters/rtw_hw_wps_pbc:1
/sys/module/8723bu/parameters/rtw_initmac:(null)
/sys/module/8723bu/parameters/rtw_ips_mode:1
/sys/module/8723bu/parameters/rtw_lbkmode:0
/sys/module/8723bu/parameters/rtw_load_phy_file:68
/sys/module/8723bu/parameters/rtw_low_power:0
/sys/module/8723bu/parameters/rtw_lowrate_two_xmit:1
/sys/module/8723bu/parameters/rtw_max_roaming_times:2
/sys/module/8723bu/parameters/rtw_mc2u_disable:0
/sys/module/8723bu/parameters/rtw_mp_mode:0
/sys/module/8723bu/parameters/rtw_network_mode:0
/sys/module/8723bu/parameters/rtw_notch_filter:0
/sys/module/8723bu/parameters/rtw_power_mgnt:1
/sys/module/8723bu/parameters/rtw_qos_opt_enable:0
/sys/module/8723bu/parameters/rtw_rf_config:5
/sys/module/8723bu/parameters/rtw_rfintfs:2
/sys/module/8723bu/parameters/rtw_rx_stbc:1
/sys/module/8723bu/parameters/rtw_smart_ps:2
/sys/module/8723bu/parameters/rtw_special_rf_path:0
/sys/module/8723bu/parameters/rtw_tx_pwr_by_rate:0
/sys/module/8723bu/parameters/rtw_tx_pwr_lmt_enable:0
/sys/module/8723bu/parameters/rtw_usb_rxagg_mode:2
/sys/module/8723bu/parameters/rtw_vcs_type:1
/sys/module/8723bu/parameters/rtw_vrtl_carrier_sense:2
/sys/module/8723bu/parameters/rtw_wifi_spec:0
/sys/module/8723bu/parameters/rtw_wmm_enable:1



```

---

### Post by jeremy31 on 2016-09-25
Let's see if the new naming scheme is at fault
```
sudo ln -s /dev/null /etc/udev/rules.d/80-net-setup-link.rules
```

Reboot and check ```
iwconfig
```

---

### Post by h0l on 2016-09-25
It's still in there... twice

```
usb0      no wireless extensions.

lo        no wireless extensions.


wlan1     unassociated  Nickname:"<WIFI@REALTEK>"
          Mode:Managed  Frequency=2.412 GHz  Access Point: Not-Associated   
          Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


wlan0     unassociated  Nickname:"<WIFI@REALTEK>"
          Mode:Managed  Frequency=2.412 GHz  Access Point: Not-Associated   
          Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0



```

---

### Post by jeremy31 on 2016-09-25
How about ```
dmesg | grep 8723bu
```

---

### Post by h0l on 2016-09-25
output is
```
[    3.936135] 8723bu: module verification failed: signature and/or required key missing - tainting kernel[    3.941213] RTL871X: rtl8723bu v4.3.6.11_12942.20141204_BTCOEX20140507-4E40
[    3.941216] RTL871X: rtl8723bu BT-Coex version = BTCOEX20140507-4E40
[    4.014538] usbcore: registered new interface driver rtl8723bu



```

---

### Post by jeremy31 on 2016-09-25
What other modules are loaded ```
lsmod
```

---

### Post by h0l on 2016-09-25
modules loaded:
```
Module                  Size  Used byrndis_host             16384  0
cdc_ether              16384  1 rndis_host
usbnet                 45056  2 rndis_host,cdc_ether
mii                    16384  1 usbnet
rfcomm                 69632  12
rtsx_usb_sdmmc         28672  0
rtsx_usb_ms            20480  0
memstick               20480  1 rtsx_usb_ms
bnep                   20480  2
8723bu                880640  0
btusb                  45056  0
btrtl                  16384  1 btusb
btbcm                  16384  1 btusb
uvcvideo               90112  0
videobuf2_vmalloc      16384  1 uvcvideo
hid_generic            16384  0
btintel                16384  1 btusb
videobuf2_memops       16384  1 videobuf2_vmalloc
cfg80211              565248  1 8723bu
bluetooth             520192  37 bnep,btbcm,btrtl,btusb,rfcomm,btintel
videobuf2_v4l2         28672  1 uvcvideo
usbhid                 49152  0
videobuf2_core         36864  2 uvcvideo,videobuf2_v4l2
v4l2_common            16384  1 videobuf2_v4l2
videodev              176128  4 uvcvideo,v4l2_common,videobuf2_core,videobuf2_v4l2
cdc_acm                36864  0
media                  24576  2 uvcvideo,videodev
rtsx_usb               24576  2 rtsx_usb_sdmmc,rtsx_usb_ms
snd_hda_codec_hdmi     53248  1
joydev                 20480  0
hid_multitouch         20480  0
wacom                  94208  0
intel_rapl             20480  0
x86_pkg_temp_thermal    16384  0
intel_powerclamp       16384  0
coretemp               16384  0
nls_iso8859_1          16384  1
kvm_intel             172032  0
snd_hda_codec_realtek    86016  1
snd_soc_rt5640        114688  0
snd_hda_codec_generic    77824  1 snd_hda_codec_realtek
kvm                   540672  1 kvm_intel
snd_soc_rl6231         16384  1 snd_soc_rt5640
snd_soc_ssm4567        16384  0
irqbypass              16384  1 kvm
crct10dif_pclmul       16384  0
snd_soc_core          212992  2 snd_soc_rt5640,snd_soc_ssm4567
crc32_pclmul           16384  0
snd_hda_intel          36864  7
aesni_intel           167936  0
snd_hda_codec         135168  4 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel
elan_i2c               36864  0
aes_x86_64             20480  1 aesni_intel
snd_compress           20480  1 snd_soc_core
lrw                    16384  1 aesni_intel
ac97_bus               16384  1 snd_soc_core
gf128mul               16384  1 lrw
snd_pcm_dmaengine      16384  1 snd_soc_core
glue_helper            16384  1 aesni_intel
ablk_helper            16384  1 aesni_intel
snd_hda_core           73728  5 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel
cryptd                 20480  2 aesni_intel,ablk_helper
snd_hwdep              16384  1 snd_hda_codec
snd_pcm               106496  8 snd_soc_rt5640,snd_soc_core,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_pcm_dmaengine,snd_hda_core
snd_seq_midi           16384  0
input_leds             16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
serio_raw              16384  0
snd_rawmidi            32768  1 snd_seq_midi
snd_seq                69632  2 snd_seq_midi_event,snd_seq_midi
intel_pch_thermal      16384  0
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              32768  2 snd_pcm,snd_seq
mei_me                 36864  0
snd                    81920  26 snd_hda_codec_realtek,snd_soc_core,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_compress
mei                    98304  1 mei_me
lpc_ich                24576  0
processor_thermal_device    16384  0
int340x_thermal_zone    16384  1 processor_thermal_device
soundcore              16384  1 snd
intel_soc_dts_iosf     16384  1 processor_thermal_device
dw_dmac                16384  0
dw_dmac_core           24576  1 dw_dmac
snd_soc_sst_acpi       16384  0
mac_hid                16384  0
tpm_crb                16384  0
acpi_pad               20480  0
i2c_designware_platform    16384  0
spi_pxa2xx_platform    24576  0
8250_dw                16384  0
i2c_designware_core    20480  1 i2c_designware_platform
parport_pc             32768  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,ppdev,parport_pc
autofs4                40960  2
i915                 1208320  10
i2c_algo_bit           16384  1 i915
drm_kms_helper        147456  1 i915
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
fb_sys_fops            16384  1 drm_kms_helper
drm                   364544  11 i915,drm_kms_helper
ahci                   36864  3
libahci                32768  1 ahci
sdhci_acpi             16384  0
video                  40960  1 i915
sdhci                  45056  1 sdhci_acpi
fjes                   28672  0
i2c_hid                20480  0
hid                   118784  5 i2c_hid,hid_multitouch,wacom,hid_generic,usbhid



```

---

### Post by jeremy31 on 2016-09-25
Actually stumped now, I wonder if something in ```
lshw -c net
```
Will show why that USB shows up as 2 devices

---

### Post by h0l on 2016-09-25
Here you go...
```
jan@jan-i7-Stylus:~$ sudo !!
sudo lshw -c net
[sudo] password for jan: 
  *-network:0             
       description: Wireless interface
       physical id: 2
       bus info: usb@1:6
       logical name: wlan1
       serial: 7e:c7:09:72:a1:f8
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rtl8723bu multicast=yes wireless=unassociated
  *-network:1
       description: Wireless interface
       physical id: 3
       bus info: usb@1:6
       logical name: wlan0
       serial: 7c:c7:09:72:a1:f8
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rtl8723bu ip=192.168.188.21 multicast=yes wireless=IEEE 802.11bgn



```

This time I'm at home connected to my wifi and not using tethering.

---

### Post by jeremy31 on 2016-09-25
Not really sure as it actually appears to be 2 devices, try a different USB port

Is there a MAC address somewhere on the USB device?  If it is a very small device, the MAC is likely not printed on it

---

### Post by h0l on 2016-09-25
> **jeremy31 said:**
> Not really sure as it actually appears to be 2 devices, try a different USB port

Is there a MAC address somewhere on the USB device?  If it is a very small device, the MAC is likely not printed on it

The device is built in. Unless I force open the tablet, no chance I can do that.

---

### Post by jeremy31 on 2016-09-25
See if ```
sudo ifconfig wlan1 down
```
Removes one of the interfaces

---

### Post by h0l on 2016-09-28
> **jeremy31 said:**
> See if ```
sudo ifconfig wlan1 down
```
Removes one of the interfaces

Unfortunately, it does not. I decided to switch back to windows, because I had some other driver problems with this tablet running Ubuntu as well. There are a few tools that I needed, and for those I am using the newly available Ubuntu Bash on Windows. 

Thanks for your effort and support!

---

