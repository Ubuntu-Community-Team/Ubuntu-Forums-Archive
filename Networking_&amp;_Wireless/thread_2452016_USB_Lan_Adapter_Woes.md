---
title: "USB Lan Adapter Woes"
date: 2020-10-14
forum: Networking &amp; Wireless
---

### Post by ranchhand2 on 2020-10-14
I picked up an 802.11ac USB adapter and have been having quite a few issues.  The connections are very intermittent.  It can sometimes take a while to connect and will experience frequent disconnects.  The system was stable using an older 2.4ghz adapter.

I ran the wireless info script and the results are located here:  [https://pastebin.com/sqsbP7TA](https://pastebin.com/sqsbP7TA)

---

### Post by chili555 on 2020-10-14
I am very suspicious of this:

```
##### modprobe options ##################
 
[/etc/modprobe.d/88XXau.conf]
options 88XXau rtw_switch_usb_mode=2

```
I wonder where you found this as a suggestion to improve connectivity. I am not at all confident that it does anything useful.

I am even more disturbed by:

```
SSID                  BSSID              MODE   CHAN  FREQ      RATE        SIGNAL  BARS  SECURITY  ACTIVE  IN-USE 
Sock                  <MAC 'Sock' [AN1]>  Infra  11    2462 MHz  130 Mbit/s  100     &#9602;&#9604;&#9606;&#9608;  WPA2      no             
Sock                  <MAC 'Sock' [AN2]>  Infra  52    5260 MHz  405 Mbit/s  85      &#9602;&#9604;&#9606;&#9608;  WPA2      yes     *      
Sock                  <MAC 'Sock' [AN3]>  Infra  52    5260 MHz  540 Mbit/s  59      &#9602;&#9604;&#9606;_  WPA2      no             
--                    <MAC '--' [AN4]>  Infra  4     2427 MHz  130 Mbit/s  44      &#9602;&#9604;__  WPA2      no             
Sock                  <MAC 'Sock' [AN5]>  Infra  4     2427 MHz  130 Mbit/s  44      &#9602;&#9604;__  WPA2      no             
MotoVAP               <MAC 'MotoVAP' [AN6]>  Infra  108   5540 MHz  540 Mbit/s  40      &#9602;&#9604;__  WPA2      no       

```
There are four access points with the same name, Sock, and you are not even connected to the strongest instance. I am confident that a significant issue is that your wireless is disconnecting and reconnecting, always looking for a better connection, much like my ex-girlfriend.

I suggest that you ask Network Manager to bind to the strongest instance like this:  [https://askubuntu.com/questions/425583/ubuntu-connect-drops-worked-for-a-while-then-started-dropping-again/425617#425617](https://askubuntu.com/questions/425583/ubuntu-connect-drops-worked-for-a-while-then-started-dropping-again/425617#425617)

---

### Post by ranchhand2 on 2020-10-14
Thank you for the quick reply!

> **chili555 said:**
> I am very suspicious of this:

```
##### modprobe options ##################
 
[/etc/modprobe.d/88XXau.conf]
options 88XXau rtw_switch_usb_mode=2

```
I wonder where you found this as a suggestion to improve connectivity. I am not at all confident that it does anything useful.

I added that when I first got the adapter to force it to use USB 3 .... I eventually took it back to the default USB 2 mode, thinking this was the stability issue.

> **chili555 said:**
> 
I am even more disturbed by:

```
SSID                  BSSID              MODE   CHAN  FREQ      RATE        SIGNAL  BARS  SECURITY  ACTIVE  IN-USE 
Sock                  <MAC 'Sock' [AN1]>  Infra  11    2462 MHz  130 Mbit/s  100     &#9602;&#9604;&#9606;&#9608;  WPA2      no             
Sock                  <MAC 'Sock' [AN2]>  Infra  52    5260 MHz  405 Mbit/s  85      &#9602;&#9604;&#9606;&#9608;  WPA2      yes     *      
Sock                  <MAC 'Sock' [AN3]>  Infra  52    5260 MHz  540 Mbit/s  59      &#9602;&#9604;&#9606;_  WPA2      no             
--                    <MAC '--' [AN4]>  Infra  4     2427 MHz  130 Mbit/s  44      &#9602;&#9604;__  WPA2      no             
Sock                  <MAC 'Sock' [AN5]>  Infra  4     2427 MHz  130 Mbit/s  44      &#9602;&#9604;__  WPA2      no             
MotoVAP               <MAC 'MotoVAP' [AN6]>  Infra  108   5540 MHz  540 Mbit/s  40      &#9602;&#9604;__  WPA2      no       

```
There are four access points with the same name, Sock, and you are not even connected to the strongest instance. I am confident that a significant issue is that your wireless is disconnecting and reconnecting, always looking for a better connection, much like my ex-girlfriend.

I suggest that you ask Network Manager to bind to the strongest instance like this:  [https://askubuntu.com/questions/425583/ubuntu-connect-drops-worked-for-a-while-then-started-dropping-again/425617#425617](https://askubuntu.com/questions/425583/ubuntu-connect-drops-worked-for-a-while-then-started-dropping-again/425617#425617)

I have a mesh router.  You are seeing the both gateway and the satellite broadcasting on both the 2.4ghz and the 5ghz bands. My adapter connected to the 5ghz band of the closest access point.

I followed your suggestion of putting the BSSID of the 5ghz access point into the wifi settings.  However, the connection is still not stable.  It frequently disconnects and reconnects.  Honestly, it seems to be disconnecting more often now, but that my just be observation bias on my part.

---

### Post by ranchhand2 on 2020-10-15
Maybe I am asking the wrong question?  I noticed the sticky thread at the top for "recommended USB wireless devices" and it shows an N150 as the recommended adapter.

Does Ubuntu support 5ghz wifi?  My old 2.4 no-name adapter was stable, albeit slower than I would have liked.  Hopefully I am not barking up the wrong tree trying to get something to work if the underlying OS doesn't even support it.

---

### Post by chili555 on 2020-10-16
> I followed your suggestion of putting the BSSID of the 5ghz access point into the wifi settings. However, the connection is still not stable. IAre there any clues in the log?

```
dmesg | grep -e wlx -e 88XX
```

> Does Ubuntu support 5ghz wifi?Perfectly well. I use it every day.

```
wlp3s0    IEEE 802.11  ESSID:"GBR5"  
          Mode:Managed [COLOR="#FF0000"] Frequency:5.745 GHz  [/COLOR]Access Point: xx:2B:B0:DC:45:xx
          [COLOR="#FF0000"]Bit Rate=866.7 Mb/s [/COLOR]  Tx-Power=22 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=56/70  Signal level=-54 dBm  

```

---

### Post by ranchhand2 on 2020-10-16
> **chili555 said:**
> Are there any clues in the log?```
dmesg | grep -e wlx -e 88XX
```

```
[    3.131357] 88XXau: loading out-of-tree module taints kernel.
[    3.132081] 88XXau: module verification failed: signature and/or required key missing - tainting kernel
[   10.094226] usb 1-4: 88XXau <MAC Addr> hw_info[d7]
[   10.149051] usbcore: registered new interface driver rtl88XXau
[   10.162969] rtl88XXau 1-4:1.0 wlx<MAC Addr>: renamed from wlan0
[   20.772672] IPv6: ADDRCONF(NETDEV_CHANGE): wlx<MAC Addr>: link becomes ready


```

Apparently my kernel is tainted?  I'm guessing that is not a good thing .... hopefully it is readily fixable?

---

### Post by chili555 on 2020-10-16
> Apparently my kernel is tainted? I'm guessing that is not a good thing .... hopefully it is readily fixable?I doubt that it is readily fixable by ordinary users; I also doubt that it need be fixed. It simply means that there is no verification key so that the module is verified as really, truly, swear to Linus free and open source software.

There are those in the Linux community that only believe in genuine verified open source software; they can be spotted because they all wear hair shirts. Others, like me, really don't adhere to rigid and strict standards; I just want my computer to work!

In fact, the driver is completely open source. We can all read every line of the source code in clear text; here is a snippet:

```
/******************************************************************************
 *
 * Copyright(c) 2007 - 2017 Realtek Corporation.
 *
 * This program is free software; you can redistribute it and/or modify it
 * under the terms of version 2 of the GNU General Public License as
 * published by the Free Software Foundation.
 *
 * This program is distributed in the hope that it will be useful, but WITHOUT
 * ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or
 * FITNESS FOR A PARTICULAR PURPOSE. See the GNU General Public License for
 * more details.
 *
 *****************************************************************************/
#define _HCI_INTF_C_

#include <drv_types.h>
#include <hal_data.h>

#include <platform_ops.h>

#ifndef CONFIG_USB_HCI
#error "CONFIG_USB_HCI shall be on!\n"
<snip>
```The kernel message simply gives you a warning; it doesn't prevent any feature or impair the driver in any way. 

I see no sign of instability in your dmesg. Were you using ethernet at the time? Were you actually connected and experiencing trouble?

Please try again.

---

### Post by ranchhand2 on 2020-10-21
It is possible that I was using the older 2.4 ghz adapter.  For good measure, i ran dmesg -C to zap the logs and rebooted the machine.

After it connected to the network, I ran the dmesg:
```
$ dmesg | grep -e wlx -e 88XX
[    3.146234] 88XXau: loading out-of-tree module taints kernel.
[    3.189980] 88XXau: module verification failed: signature and/or required key missing - tainting kernel
[   10.183444] usb 1-4: 88XXau <mac id> hw_info[d7]
[   10.238212] usbcore: registered new interface driver rtl88XXau
[   10.254149] rtl88XXau 1-4:1.0 wlx<mac id>: renamed from wlan0
[   20.852909] IPv6: ADDRCONF(NETDEV_CHANGE): wlx<mac id>: link becomes ready
[  120.626021] Modules linked in: nls_iso8859_1 snd_hda_codec_realtek snd_hda_codec_generic ledtrig_audio snd_hda_codec_hdmi snd_hda_intel snd_intel_dspcfg snd_hda_codec snd_usb_audio snd_hda_core snd_usbmidi_lib snd_hwdep snd_pcm snd_seq_midi snd_seq_midi_event edac_mce_amd snd_rawmidi kvm_amd ccp amdgpu kvm snd_seq snd_seq_device 88XXau(OE) crct10dif_pclmul snd_timer ghash_clmulni_intel aesni_intel uvcvideo crypto_simd amd_iommu_v2 gpu_sched videobuf2_vmalloc cryptd videobuf2_memops videobuf2_v4l2 glue_helper ttm videobuf2_common snd videodev drm_kms_helper joydev i2c_algo_bit wmi_bmof cfg80211 mc fb_sys_fops k10temp syscopyarea input_leds sysfillrect sysimgblt soundcore mac_hid sch_fq_codel parport_pc ppdev lp parport drm ip_tables x_tables autofs4 hid_logitech_hidpp hid_microsoft hid_logitech_dj ff_memless hid_generic usbhid hid uas usb_storage crc32_pclmul nvme i2c_piix4 nvme_core r8169 ahci realtek libahci wmi video gpio_amdpt gpio_generic
[  120.626224]  rtw_cfg80211_ch_switch_notify+0x132/0x141 [88XXau]
[  120.626264]  rtw_chk_start_clnt_join+0x76/0x80 [88XXau]
[  120.626302]  join_cmd_hdl+0x26e/0x36f [88XXau]
[  120.626350]  ? rtw_chk_start_clnt_join+0x80/0x80 [88XXau]
[  120.626388]  rtw_cmd_thread+0x2b2/0x407 [88XXau]
[  120.626435]  ? rtw_stop_cmd_thread+0x3e/0x3e [88XXau]
[  122.952588] IPv6: ADDRCONF(NETDEV_CHANGE): wlx<mac id>: link becomes ready

```

I then waited a few minutes for the connection to fail and did it again:
```
$ dmesg | grep -e wlx -e 88XX
[    3.146234] 88XXau: loading out-of-tree module taints kernel.
[    3.189980] 88XXau: module verification failed: signature and/or required key missing - tainting kernel
[   10.183444] usb 1-4: 88XXau <mac id> hw_info[d7]
[   10.238212] usbcore: registered new interface driver rtl88XXau
[   10.254149] rtl88XXau 1-4:1.0 wlx<mac id>: renamed from wlan0
[   20.852909] IPv6: ADDRCONF(NETDEV_CHANGE): wlx<mac id>: link becomes ready
[  120.626021] Modules linked in: nls_iso8859_1 snd_hda_codec_realtek snd_hda_codec_generic ledtrig_audio snd_hda_codec_hdmi snd_hda_intel snd_intel_dspcfg snd_hda_codec snd_usb_audio snd_hda_core snd_usbmidi_lib snd_hwdep snd_pcm snd_seq_midi snd_seq_midi_event edac_mce_amd snd_rawmidi kvm_amd ccp amdgpu kvm snd_seq snd_seq_device 88XXau(OE) crct10dif_pclmul snd_timer ghash_clmulni_intel aesni_intel uvcvideo crypto_simd amd_iommu_v2 gpu_sched videobuf2_vmalloc cryptd videobuf2_memops videobuf2_v4l2 glue_helper ttm videobuf2_common snd videodev drm_kms_helper joydev i2c_algo_bit wmi_bmof cfg80211 mc fb_sys_fops k10temp syscopyarea input_leds sysfillrect sysimgblt soundcore mac_hid sch_fq_codel parport_pc ppdev lp parport drm ip_tables x_tables autofs4 hid_logitech_hidpp hid_microsoft hid_logitech_dj ff_memless hid_generic usbhid hid uas usb_storage crc32_pclmul nvme i2c_piix4 nvme_core r8169 ahci realtek libahci wmi video gpio_amdpt gpio_generic
[  120.626224]  rtw_cfg80211_ch_switch_notify+0x132/0x141 [88XXau]
[  120.626264]  rtw_chk_start_clnt_join+0x76/0x80 [88XXau]
[  120.626302]  join_cmd_hdl+0x26e/0x36f [88XXau]
[  120.626350]  ? rtw_chk_start_clnt_join+0x80/0x80 [88XXau]
[  120.626388]  rtw_cmd_thread+0x2b2/0x407 [88XXau]
[  120.626435]  ? rtw_stop_cmd_thread+0x3e/0x3e [88XXau]
[  122.952588] IPv6: ADDRCONF(NETDEV_CHANGE): wlx<mac id>: link becomes ready
[  165.241060] Modules linked in: nls_iso8859_1 snd_hda_codec_realtek snd_hda_codec_generic ledtrig_audio snd_hda_codec_hdmi snd_hda_intel snd_intel_dspcfg snd_hda_codec snd_usb_audio snd_hda_core snd_usbmidi_lib snd_hwdep snd_pcm snd_seq_midi snd_seq_midi_event edac_mce_amd snd_rawmidi kvm_amd ccp amdgpu kvm snd_seq snd_seq_device 88XXau(OE) crct10dif_pclmul snd_timer ghash_clmulni_intel aesni_intel uvcvideo crypto_simd amd_iommu_v2 gpu_sched videobuf2_vmalloc cryptd videobuf2_memops videobuf2_v4l2 glue_helper ttm videobuf2_common snd videodev drm_kms_helper joydev i2c_algo_bit wmi_bmof cfg80211 mc fb_sys_fops k10temp syscopyarea input_leds sysfillrect sysimgblt soundcore mac_hid sch_fq_codel parport_pc ppdev lp parport drm ip_tables x_tables autofs4 hid_logitech_hidpp hid_microsoft hid_logitech_dj ff_memless hid_generic usbhid hid uas usb_storage crc32_pclmul nvme i2c_piix4 nvme_core r8169 ahci realtek libahci wmi video gpio_amdpt gpio_generic
[  165.241263]  rtw_cfg80211_ch_switch_notify+0x132/0x141 [88XXau]
[  165.241302]  rtw_chk_start_clnt_join+0x76/0x80 [88XXau]
[  165.241340]  join_cmd_hdl+0x26e/0x36f [88XXau]
[  165.241379]  ? rtw_chk_start_clnt_join+0x80/0x80 [88XXau]
[  165.241406]  rtw_cmd_thread+0x2b2/0x407 [88XXau]
[  165.241437]  ? rtw_stop_cmd_thread+0x3e/0x3e [88XXau]
[  397.053315] Modules linked in: nls_iso8859_1 snd_hda_codec_realtek snd_hda_codec_generic ledtrig_audio snd_hda_codec_hdmi snd_hda_intel snd_intel_dspcfg snd_hda_codec snd_usb_audio snd_hda_core snd_usbmidi_lib snd_hwdep snd_pcm snd_seq_midi snd_seq_midi_event edac_mce_amd snd_rawmidi kvm_amd ccp amdgpu kvm snd_seq snd_seq_device 88XXau(OE) crct10dif_pclmul snd_timer ghash_clmulni_intel aesni_intel uvcvideo crypto_simd amd_iommu_v2 gpu_sched videobuf2_vmalloc cryptd videobuf2_memops videobuf2_v4l2 glue_helper ttm videobuf2_common snd videodev drm_kms_helper joydev i2c_algo_bit wmi_bmof cfg80211 mc fb_sys_fops k10temp syscopyarea input_leds sysfillrect sysimgblt soundcore mac_hid sch_fq_codel parport_pc ppdev lp parport drm ip_tables x_tables autofs4 hid_logitech_hidpp hid_microsoft hid_logitech_dj ff_memless hid_generic usbhid hid uas usb_storage crc32_pclmul nvme i2c_piix4 nvme_core r8169 ahci realtek libahci wmi video gpio_amdpt gpio_generic
[  397.053445]  rtw_cfg80211_ch_switch_notify+0x132/0x141 [88XXau]
[  397.053469]  rtw_chk_start_clnt_join+0x76/0x80 [88XXau]
[  397.053492]  join_cmd_hdl+0x26e/0x36f [88XXau]
[  397.053516]  ? rtw_chk_start_clnt_join+0x80/0x80 [88XXau]
[  397.053532]  rtw_cmd_thread+0x2b2/0x407 [88XXau]
[  397.053551]  ? rtw_stop_cmd_thread+0x3e/0x3e [88XXau]
[  402.972035] Modules linked in: nls_iso8859_1 snd_hda_codec_realtek snd_hda_codec_generic ledtrig_audio snd_hda_codec_hdmi snd_hda_intel snd_intel_dspcfg snd_hda_codec snd_usb_audio snd_hda_core snd_usbmidi_lib snd_hwdep snd_pcm snd_seq_midi snd_seq_midi_event edac_mce_amd snd_rawmidi kvm_amd ccp amdgpu kvm snd_seq snd_seq_device 88XXau(OE) crct10dif_pclmul snd_timer ghash_clmulni_intel aesni_intel uvcvideo crypto_simd amd_iommu_v2 gpu_sched videobuf2_vmalloc cryptd videobuf2_memops videobuf2_v4l2 glue_helper ttm videobuf2_common snd videodev drm_kms_helper joydev i2c_algo_bit wmi_bmof cfg80211 mc fb_sys_fops k10temp syscopyarea input_leds sysfillrect sysimgblt soundcore mac_hid sch_fq_codel parport_pc ppdev lp parport drm ip_tables x_tables autofs4 hid_logitech_hidpp hid_microsoft hid_logitech_dj ff_memless hid_generic usbhid hid uas usb_storage crc32_pclmul nvme i2c_piix4 nvme_core r8169 ahci realtek libahci wmi video gpio_amdpt gpio_generic
[  402.972198]  rtw_cfg80211_ch_switch_notify+0x132/0x141 [88XXau]
[  402.972228]  rtw_chk_start_clnt_join+0x76/0x80 [88XXau]
[  402.972257]  join_cmd_hdl+0x26e/0x36f [88XXau]
[  402.972284]  ? rtw_chk_start_clnt_join+0x80/0x80 [88XXau]
[  402.972300]  rtw_cmd_thread+0x2b2/0x407 [88XXau]
[  402.972322]  ? rtw_stop_cmd_thread+0x3e/0x3e [88XXau]
[  423.454324] Modules linked in: nls_iso8859_1 snd_hda_codec_realtek snd_hda_codec_generic ledtrig_audio snd_hda_codec_hdmi snd_hda_intel snd_intel_dspcfg snd_hda_codec snd_usb_audio snd_hda_core snd_usbmidi_lib snd_hwdep snd_pcm snd_seq_midi snd_seq_midi_event edac_mce_amd snd_rawmidi kvm_amd ccp amdgpu kvm snd_seq snd_seq_device 88XXau(OE) crct10dif_pclmul snd_timer ghash_clmulni_intel aesni_intel uvcvideo crypto_simd amd_iommu_v2 gpu_sched videobuf2_vmalloc cryptd videobuf2_memops videobuf2_v4l2 glue_helper ttm videobuf2_common snd videodev drm_kms_helper joydev i2c_algo_bit wmi_bmof cfg80211 mc fb_sys_fops k10temp syscopyarea input_leds sysfillrect sysimgblt soundcore mac_hid sch_fq_codel parport_pc ppdev lp parport drm ip_tables x_tables autofs4 hid_logitech_hidpp hid_microsoft hid_logitech_dj ff_memless hid_generic usbhid hid uas usb_storage crc32_pclmul nvme i2c_piix4 nvme_core r8169 ahci realtek libahci wmi video gpio_amdpt gpio_generic
[  423.454462]  rtw_cfg80211_ch_switch_notify+0x132/0x141 [88XXau]
[  423.454489]  rtw_chk_start_clnt_join+0x76/0x80 [88XXau]
[  423.454514]  join_cmd_hdl+0x26e/0x36f [88XXau]
[  423.454540]  ? rtw_chk_start_clnt_join+0x80/0x80 [88XXau]
[  423.454557]  rtw_cmd_thread+0x2b2/0x407 [88XXau]
[  423.454579]  ? rtw_stop_cmd_thread+0x3e/0x3e [88XXau]

```

Any thoughts or insights?

---

### Post by chili555 on 2020-10-21
> Any thoughts or insights?You have a very unhappy driver and hardware combination. Which version is it? From where did you download or clone it? Any clues here?

```
modinfo 88XXau | grep filename
sudo dkms status

```
We may try updating to a better, more current version.

---

### Post by ranchhand2 on 2020-10-21
I download the driver from this website:
[https://github.com/aircrack-ng/rtl8812au](https://github.com/aircrack-ng/rtl8812au)

It seemed to be the preferred choice of this and other forums.

```
$ modinfo 88XXau | grep filename
filename:       /lib/modules/5.4.0-52-generic/updates/dkms/88XXau.ko
$ sudo dkms status
rtl8812au, 5.6.4.2, 5.4.0-48-generic, x86_64: installed
rtl8812au, 5.6.4.2, 5.4.0-51-generic, x86_64: installed
rtl8812au, 5.6.4.2, 5.4.0-52-generic, x86_64: installed

```

---

### Post by morrownr on 2020-10-21
I'm going to go with what Chili555 said. Older versions of drivers may not handle mesh and other interesting new things very well. What I have been seeing from recent releases of Realtek drivers is big changes in the firmware file and other parts of the driver that do things like support mesh and power saving. I uploaded a new version of the rtl88x2bu driver a couple of days ago after testing...

 github.com/morrownr

During testing of the new driver I could not believe the speed increases. I beat it up pretty good and could not find a single bug but then I can't test mesh or other things that I don't have so you can test for us. Fair enough?

If you can give me a day or two to test, I will upload the new version of the 8812au driver. Don't download the version (5.6.4.2) that is there now.

Cheers

---

### Post by morrownr on 2020-10-22
Okay, I had time this evening. The new driver is up:

[https://github.com/morrownr/8812au](https://github.com/morrownr/8812au)

Some things to note:

- The new driver name will be 8812au (8812au.ko). 

- Your old driver name was 88XXau.

- You need to carefully follow the uninstallation instruction for the driver you were using and then reboot.

- Install the new driver using the instructions in the README file.

Let us know how it goes.

---

### Post by ranchhand2 on 2020-10-22
Thank you, morrownr, for taking the time to put together a new driver.  You clearly have a passion and a skillset for this sort of thing, especially to do it so quickly.  I wish I had your talent.

I am a bit concerned, though, about a comment you posted on github in relation to the 88x2bu driver.  You mentioned that you did not recall where you located the source code for that 5.8.7.2 realtek driver.  The source you linked to earlier for this 8812 driver looks to be based upon 5.9.3.2 from realtek, if I am understanding the readme correctly.  Honestly, compiling software from a random dropbox into my system isn't something I am comfortable doing.  So I was wondering if you could post a link to where you located the 5.9.3.2 source code?

Thank You!

---

### Post by morrownr on 2020-10-22
I understand your concern but I think you are reading something into my comment about me not remembering exactly where I picked up the source for a specific driver. I do not look in random  dropboxes for driver source code. Many sellers who support Linux to one degree or another post the source packages on their support sites. Examples of companies that do this include DLink, Cudy, Edup and many more. Those support sites are where I download source packages. Do I use them, even though they are from reputable sellers, without checking? No. 

I'm not so sure that I have special talents. 40+ years ago I took enough computer science in college to be pretty good at FORTRAN and COBAL. I tried to stay current and at times it came in handy. My 2 careers were not in IT. A few months ago, I needed to come up to speed on using Github and this project is what I decided to do. I had to dust off my old C books and let me tell you, wifi programming is a truly complicated effort and we don't have access to all of the source code as one large file in the source of Realtek drivers is coded so we can't really see what it does. What I do while learning is look for problems and see if I can fix them. I also use fixes that others have found and I look to see if there is any capability I can add without messing things up.

Regards.

---

