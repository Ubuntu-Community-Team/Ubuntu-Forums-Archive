---
title: "&quot;Wi-fi disabled by hardware switch&quot; Lenovo Thinkpad E330 with Ubuntu 14.04LTS"
date: 2014-09-18
forum: Networking &amp; Wireless
---

### Post by maximovna on 2014-09-18
Dear all,
this week suddenly I was dropped offline and my Network Manager said: "Wi-Fi disabled by hardware switch", which of course is not the case. I tried restarting, suspending and so on without effect.
rfkill list all says yes to hard block, and sudo rfkill unblock all doesn't change it. 
I reseted the BIOS to defaults, no change.
In the System Settings/Network it's not possible to slide the Wireless switch to on.
I have a Lenovo Thinkpad E330 with Ubuntu 14.04LTS.
Thank you in advance!
Irina

---

### Post by praseodym on 2014-09-18
Checked this?

[http://ubuntuforums.org/showthread.php?t=2111690&p=12490285#post12490285](http://ubuntuforums.org/showthread.php?t=2111690&p=12490285#post12490285)

---

### Post by maximovna on 2014-09-22
unfortunately none of these worked. I still don't have a solution for the problem.

---

### Post by praseodym on 2014-09-22
Please show the terminal outputs of these commands:
```

lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
rfkill list
dmesg | egrep 'radio|kill|switch'
```

---

### Post by maximovna on 2014-09-25
```
irina@irina-ThinkPad:~$ lspci -nnk | grep -iA2 net  
 02:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N 2230 [8086:0888] (rev c4)  
 	Subsystem: Intel Corporation Centrino Wireless-N 2230 BGN [8086:4262]  
 	Kernel driver in use: iwlwifi  
 --  
 08:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 07)  
 	Subsystem: Lenovo Device [17aa:5006]  
 	Kernel driver in use: r8169  
 irina@irina-ThinkPad:~$ lsusb  
 Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub  
 Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub  
 Bus 001 Device 003: ID 5986:0299 Acer, Inc  
 Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub  
 Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub  
 Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub  
 Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub  
 irina@irina-ThinkPad:~$ lsmod  
 Module                  Size  Used by  
 bnep                   19624  2  
 rfcomm                 69160  0  
 bluetooth             391196  10 bnep,rfcomm  
 snd_hda_codec_hdmi     46254  1  
 snd_hda_codec_realtek    61438  1  
 acer_wmi               32522  0  
 sparse_keymap          13948  1 acer_wmi  
 uvcvideo               80885  0  
 videobuf2_vmalloc      13216  1 uvcvideo  
 videobuf2_memops       13362  1 videobuf2_vmalloc  
 videobuf2_core         40664  1 uvcvideo  
 videodev              134688  2 uvcvideo,videobuf2_core  
 arc4                   12608  2  
 iwldvm                232285  0  
 mac80211              630653  1 iwldvm  
 intel_rapl             18773  0  
 x86_pkg_temp_thermal    14205  0  
 intel_powerclamp       14705  0  
 coretemp               13435  0  
 crct10dif_pclmul       14289  0  
 crc32_pclmul           13113  0  
 ghash_clmulni_intel    13216  0  
 cryptd                 20359  1 ghash_clmulni_intel  
 snd_hda_intel          52355  3  
 snd_hda_codec         192906  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel  
 snd_hwdep              13602  1 snd_hda_codec  
 thinkpad_acpi          81013  1  
 nvram                  14411  1 thinkpad_acpi  
 snd_pcm               102099  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel  
 snd_seq_midi           13324  0  
 snd_seq_midi_event     14899  1 snd_seq_midi  
 iwlwifi               169932  1 iwldvm  
 snd_rawmidi            30144  1 snd_seq_midi  
 joydev                 17381  0  
 snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi  
 serio_raw              13462  0  
 rtsx_pci_ms            18151  0  
 lpc_ich                21080  0  
 memstick               16966  1 rtsx_pci_ms  
 mei_me                 18627  0  
 cfg80211              484040  3 iwlwifi,mac80211,iwldvm  
 snd_page_alloc         18710  2 snd_pcm,snd_hda_intel  
 i915                  783805  3  
 mei                    82276  1 mei_me  
 snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi  
 snd_timer              29482  2 snd_pcm,snd_seq  
 snd                    69238  18 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,thinkpad_acpi,snd_seq_device,snd_seq_midi 
 drm_kms_helper         53081  1 i915  
 drm                   303102  4 i915,drm_kms_helper  
 i2c_algo_bit           13413  1 i915  
 wmi                    19177  1 acer_wmi  
 video                  19476  2 i915,acer_wmi  
 soundcore              12680  1 snd  
 mac_hid                13205  0  
 parport_pc             32701  0  
 ppdev                  17671  0  
 lp                     17759  0  
 parport                42348  3 lp,ppdev,parport_pc  
 rtsx_pci_sdmmc         23274  0  
 psmouse               106678  0  
 ahci                   25819  2  
 r8169                  67581  0  
 mii                    13934  1 r8169  
 libahci                32560  1 ahci  
 rtsx_pci               45956  2 rtsx_pci_ms,rtsx_pci_sdmmc  
 irina@irina-ThinkPad:~$ iwconfig  
 eth0      no wireless extensions.  
 

 lo        no wireless extensions.  
 

 wlan0     IEEE 802.11bgn  ESSID:off/any   
           Mode:Managed  Access Point: Not-Associated   Tx-Power=off    
           Retry  long limit:7   RTS thr:off   Fragment thr:off  
           Power Management:on  
            
 irina@irina-ThinkPad:~$ rfkill list  
 0: tpacpi_bluetooth_sw: Bluetooth  
 	Soft blocked: no  
 	Hard blocked: no  
 1: phy0: Wireless LAN  
 	Soft blocked: yes  
 	Hard blocked: yes  
 irina@irina-ThinkPad:~$ dmesg | egrep 'radio|kill|switch'  
 [    0.802189] Console: switching to colour frame buffer device 170x48  
 [   10.546193] Console: switching to colour dummy device 80x25  
 [   10.655731] thinkpad_acpi: rfkill switch tpacpi_bluetooth_sw: radio is blocked  
 [   10.869777] iwlwifi 0000:02:00.0: RF_KILL bit toggled to disable radio.  
 [   11.393288] Console: switching to colour frame buffer device 170x48  
 [   12.857591] init: failsafe main process (581) killed by TERM signal  
 [   13.390595] init: cups main process (651) killed by HUP signal  
 [   20.582032] init: anacron main process (925) killed by TERM signal  
 irina@irina-ThinkPad:~$ 


```

---

### Post by praseodym on 2014-09-25
Blacklist this module and reboot:
```

echo "blacklist acer_wmi" | sudo tee -a /etc/modprobe.d/blacklist.conf
```

---

### Post by maximovna on 2014-09-25
thank you very much for your reply
the wifi is still "disabled by hardware switch

---

### Post by praseodym on 2014-09-25
Please try:

```
sudo rmmod thinkpad_acpi
sudo rfkill unblock all
```

---

### Post by maximovna on 2014-09-25
```
sudo rmmod thinkpad_acpi
``` 
gives me
```
rmmod: ERROR: Module thinkpad_acpi is in use
```
the ```
sudo rfkill unblock all
``` doesn't help

---

### Post by mil2 on 2015-08-29
> **maximovna said:**
> ```
sudo rmmod thinkpad_acpi
``` 
gives me
```
rmmod: ERROR: Module thinkpad_acpi is in use
```
the ```
sudo rfkill unblock all
``` doesn't help

 On Lenovo z61 
I found that when installing from dvd allows wifi usage, but after updates wifi is disabled. I rebooted and went into bios setup, and then disabled Bluetooth, which will be marked as hidden, and then rebooted again and now am able to use wifi.

---

