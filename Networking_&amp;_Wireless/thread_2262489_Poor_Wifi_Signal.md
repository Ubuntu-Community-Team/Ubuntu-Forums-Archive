---
title: "Poor Wifi Signal"
date: 2015-01-25
forum: Networking &amp; Wireless
---

### Post by Baurzhan on 2015-01-25
So here is my issue: I recently installed ubuntu 14.04 on my Asus notebook  X553M in dual boot with Windows 7. All is working well, however, Wifi  never goes more thant 2 bars near the router and got disconnected as  about 4 or 5 meters only. While on Windows 7 the signal strength is  perfect, I don't have any issue to connect wirelessly on my Asus. When  wired, connection is perfect too. Hope you'll be able to help me. Thank  you

azzed@azzed-Ubu:~$ lspci -nn -d 14e4:
02:00.0 Network controller [0280]: Broadcom Corporation BCM43142 802.11b/g/n [14e4:4365] (rev 01)

azzed@azzed-Ubu:~$ iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"ZTE"  
          Mode:Managed  Frequency:2.447 GHz  Access Point: 00 :15:EB:F6:2F: DC   
          Retry  long limit:7   RTS thr: off   Fragment thr: off
          Power Management off

---

### Post by chili555 on 2015-01-25
May we see:```
sudo iwlist wlan0 scan
dmesg | grep wl
```For the scan, please omit all other access points except yours and disguise the MAC address thus: xx:xx:xx:xx

Thanks.

---

### Post by Baurzhan on 2015-01-25
azzed@azzed-Ubu:~$ sudo iwlist wlan0 scan
[sudo] password for azzed: 
wlan0     Scan completed :
          Cell 01 - Address: 00:15:EB:F6:2F: DC
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key: On
                    ESSID:"ZTE"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 4ms ago
                    IE: Unknown: 00035A5445
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030108
                    IE: Unknown: 2A0104
                    IE: Unknown: 32080C1218243048606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK

azzed@azzed-Ubu:~$ dmesg | grep wl
[   14.117394] wl: module license 'MIXED/Proprietary' taints kernel.
[   14.121216] wl: module verification failed: signature and/or  required key missing - tainting kernel
[   14.156428] INFO @wl_cfg80211_attach : Registered CFG80211 phy
[   14.277100] wlan0: Broadcom BCM4365 802.11 Hybrid Wireless Controller 6.30.223.141 (r415941)
[ 3583.481490] Modules linked in: michael_mic arc4 bnep rfcomm bluetooth snd_hda_codec_hdmi snd_hda_codec_realtek lib80211_crypt_tkip wl(POX) uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_core videodev lib80211 cfg80211 asus_nb_wmi asus_wmi sparse_keymap snd_hda_intel snd_hda_codec snd_hwdep snd_pcm snd_page_alloc intel_rapl coretemp snd_seq_midi snd_seq_midi_event kvm snd_rawmidi crct10dif_pclmul crc32_pclmul ghash_clmulni_intel cryptd snd_seq snd_seq_device snd_timer rtsx_pci_ms memstick joydev serio_raw i915 snd soundcore drm_kms_helper drm i2c_algo_bit wmi video mac_hid parport_pc ppdev lp parport rtsx_pci_sdmmc psmouse r8169 mii ahci rtsx_pci libahci
[ 3583.481702] CPU: 3 PID: 395 Comm: wl_event_handle Tainted: P           OX 3.13.0-44-generic #73-Ubuntu
[ 3583.482189]  [<ffffffffa05a9528>] wl_bss_connect_done.isra.21+0x98/0x1a0 [wl]
[ 3583.482336]  [<ffffffffa05a982c>] wl_notify_connect_status+0x1fc/0x410 [wl]
[ 3583.482481]  [<ffffffffa05a8135>] wl_event_handler+0x55/0x220 [wl]
[ 3583.482627]  [<ffffffffa05a80e0>] ? wl_get_assoc_ies+0x240/0x240 [wl]
[ 4479.558406] ERROR @wl_dev_intvar_get : error (-1)
[ 4479.558413] ERROR @wl_cfg80211_get_tx_power : error (-1)
[ 4502.210901] ERROR @wl_dev_intvar_get : error (-1)
[ 4502.210912] ERROR @wl_cfg80211_get_tx_power : error (-1)
[ 6309.191134] ERROR @wl_dev_intvar_get : error (-1)
[ 6309.191141] ERROR @wl_cfg80211_get_tx_power : error (-1)
[13919.901987] Modules linked in: michael_mic arc4 bnep rfcomm bluetooth snd_hda_codec_hdmi snd_hda_codec_realtek lib80211_crypt_tkip wl(POX) uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_core videodev lib80211 cfg80211 asus_nb_wmi asus_wmi sparse_keymap snd_hda_intel snd_hda_codec snd_hwdep snd_pcm snd_page_alloc intel_rapl coretemp snd_seq_midi snd_seq_midi_event kvm snd_rawmidi crct10dif_pclmul crc32_pclmul ghash_clmulni_intel cryptd snd_seq snd_seq_device snd_timer rtsx_pci_ms memstick joydev serio_raw i915 snd soundcore drm_kms_helper drm i2c_algo_bit wmi video mac_hid parport_pc ppdev lp parport rtsx_pci_sdmmc psmouse r8169 mii ahci rtsx_pci libahci
[13919.902198] CPU: 0 PID: 395 Comm: wl_event_handle Tainted: P        W  OX 3.13.0-44-generic #73-Ubuntu
[13919.902466]  [<ffffffffa05a9528>] wl_bss_connect_done.isra.21+0x98/0x1a0 [wl]
[13919.902500]  [<ffffffffa05a982c>] wl_notify_connect_status+0x1fc/0x410 [wl]
[13919.902588]  [<ffffffffa05a8135>] wl_event_handler+0x55/0x220 [wl]
[13919.902733]  [<ffffffffa05a80e0>] ? wl_get_assoc_ies+0x240/0x240 [wl]
[13929.149443] Modules linked in: michael_mic arc4 bnep rfcomm bluetooth snd_hda_codec_hdmi snd_hda_codec_realtek lib80211_crypt_tkip wl(POX) uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_core videodev lib80211 cfg80211 asus_nb_wmi asus_wmi sparse_keymap snd_hda_intel snd_hda_codec snd_hwdep snd_pcm snd_page_alloc intel_rapl coretemp snd_seq_midi snd_seq_midi_event kvm snd_rawmidi crct10dif_pclmul crc32_pclmul ghash_clmulni_intel cryptd snd_seq snd_seq_device snd_timer rtsx_pci_ms memstick joydev serio_raw i915 snd soundcore drm_kms_helper drm i2c_algo_bit wmi video mac_hid parport_pc ppdev lp parport rtsx_pci_sdmmc psmouse r8169 mii ahci rtsx_pci libahci
[13929.149555] CPU: 1 PID: 395 Comm: wl_event_handle Tainted: P        W  OX 3.13.0-44-generic #73-Ubuntu
[13929.149737]  [<ffffffffa05a9528>] wl_bss_connect_done.isra.21+0x98/0x1a0 [wl]
[13929.149774]  [<ffffffffa05a982c>] wl_notify_connect_status+0x1fc/0x410 [wl]
[13929.149811]  [<ffffffffa05a8135>] wl_event_handler+0x55/0x220 [wl]
[13929.149851]  [<ffffffffa05a80e0>] ? wl_get_assoc_ies+0x240/0x240 [wl]
[13929.221236] Modules linked in: michael_mic arc4 bnep rfcomm bluetooth snd_hda_codec_hdmi snd_hda_codec_realtek lib80211_crypt_tkip wl(POX) uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_core videodev lib80211 cfg80211 asus_nb_wmi asus_wmi sparse_keymap snd_hda_intel snd_hda_codec snd_hwdep snd_pcm snd_page_alloc intel_rapl coretemp snd_seq_midi snd_seq_midi_event kvm snd_rawmidi crct10dif_pclmul crc32_pclmul ghash_clmulni_intel cryptd snd_seq snd_seq_device snd_timer rtsx_pci_ms memstick joydev serio_raw i915 snd soundcore drm_kms_helper drm i2c_algo_bit wmi video mac_hid parport_pc ppdev lp parport rtsx_pci_sdmmc psmouse r8169 mii ahci rtsx_pci libahci
[13929.221309] CPU: 1 PID: 395 Comm: wl_event_handle Tainted: P        W  OX 3.13.0-44-generic #73-Ubuntu
[13929.221445]  [<ffffffffa05a940c>] wl_notify_roaming_status+0xac/0x130 [wl]
[13929.221489]  [<ffffffffa05a8135>] wl_event_handler+0x55/0x220 [wl]
[13929.221533]  [<ffffffffa05a80e0>] ? wl_get_assoc_ies+0x240/0x240 [wl]
[13938.393340] Modules linked in: michael_mic arc4 bnep rfcomm bluetooth snd_hda_codec_hdmi snd_hda_codec_realtek lib80211_crypt_tkip wl(POX) uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_core videodev lib80211 cfg80211 asus_nb_wmi asus_wmi sparse_keymap snd_hda_intel snd_hda_codec snd_hwdep snd_pcm snd_page_alloc intel_rapl coretemp snd_seq_midi snd_seq_midi_event kvm snd_rawmidi crct10dif_pclmul crc32_pclmul ghash_clmulni_intel cryptd snd_seq snd_seq_device snd_timer rtsx_pci_ms memstick joydev serio_raw i915 snd soundcore drm_kms_helper drm i2c_algo_bit wmi video mac_hid parport_pc ppdev lp parport rtsx_pci_sdmmc psmouse r8169 mii ahci rtsx_pci libahci
[13938.393541] CPU: 1 PID: 395 Comm: wl_event_handle Tainted: P        W  OX 3.13.0-44-generic #73-Ubuntu
[13938.393918]  [<ffffffffa05a9528>] wl_bss_connect_done.isra.21+0x98/0x1a0 [wl]
[13938.394065]  [<ffffffffa05a982c>] wl_notify_connect_status+0x1fc/0x410 [wl]
[13938.394210]  [<ffffffffa05a8135>] wl_event_handler+0x55/0x220 [wl]
[13938.394356]  [<ffffffffa05a80e0>] ? wl_get_assoc_ies+0x240/0x240 [wl]
[13938.446290] Modules linked in: michael_mic arc4 bnep rfcomm bluetooth snd_hda_codec_hdmi snd_hda_codec_realtek lib80211_crypt_tkip wl(POX) uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_core videodev lib80211 cfg80211 asus_nb_wmi asus_wmi sparse_keymap snd_hda_intel snd_hda_codec snd_hwdep snd_pcm snd_page_alloc intel_rapl coretemp snd_seq_midi snd_seq_midi_event kvm snd_rawmidi crct10dif_pclmul crc32_pclmul ghash_clmulni_intel cryptd snd_seq snd_seq_device snd_timer rtsx_pci_ms memstick joydev serio_raw i915 snd soundcore drm_kms_helper drm i2c_algo_bit wmi video mac_hid parport_pc ppdev lp parport rtsx_pci_sdmmc psmouse r8169 mii ahci rtsx_pci libahci
[13938.446500] CPU: 1 PID: 395 Comm: wl_event_handle Tainted: P        W  OX 3.13.0-44-generic #73-Ubuntu
[13938.446880]  [<ffffffffa05a940c>] wl_notify_roaming_status+0xac/0x130 [wl]
[13938.447026]  [<ffffffffa05a8135>] wl_event_handler+0x55/0x220 [wl]
[13938.447172]  [<ffffffffa05a80e0>] ? wl_get_assoc_ies+0x240/0x240 [wl]

It looks too much, I hope it's what you did ask for. Thanks

---

### Post by chili555 on 2015-01-25
Man, oh man! You have one unhappy driver there! I notice this:> IE: WPA Version 1
Group Cipher : TKIP
Pairwise Ciphers (2) : TKIP CCMP
Authentication Suites (1) : PSK
IE: IEEE 802.11i/WPA2 Version 1
Group Cipher : TKIP
Pairwise Ciphers (2) : TKIP CCMP
Authentication Suites (1) : PSKFirst, check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly _not_ TKIP. Second, if your router is capable of N speeds, I have better luck with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. After making these changes, reboot the router. 

Next, I recommend that your regulatory domain be set explicitly. Check yours:```
sudo iw reg get
```If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:```
sudo iw reg set IS
```Of course, substitute your country code if not Iceland. Set it permanently:```
gksudo gedit /etc/default/crda
```Use nano or kate or leafpad if you don't have the text editor gedit.

Change the last line to read:```
REGDOMAIN=IS
```Proofread carefully, save and close the text editor.

Next, I'd set IPv6 to Ignore in Network Manager: [http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png](http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png)  This example is for ethernet, but you want wireless.

Reboot the computer and tell us if there is any improvement. If not, let's see again:```
dmesg | grep wl
```

---

### Post by Baurzhan on 2015-01-25
I followed all the instructions but unfortunately, it didn't work

azzed@azzed-Ubu:~$ dmesg | grep wl
[   13.472522] wl: module license 'MIXED/Proprietary' taints kernel.
[   13.476406] wl: module verification failed: signature and/or  required key missing - tainting kernel
[   13.510921] INFO @wl_cfg80211_attach : Registered CFG80211 phy
[   13.679706] wlan0: Broadcom BCM4365 802.11 Hybrid Wireless Controller 6.30.223.141 (r415941)

---

### Post by chili555 on 2015-01-25
Except you got rid of* ALL* the errors! How is the performance otherwise?

---

### Post by Baurzhan on 2015-01-25
I dit these two commands ' sudo apt-get remove bcmwl-kernel-source' && 'sudo apt-get install bcmwl-kernel-source'

After, here the output for the last instruction :

azzed@azzed-Ubu:~$ dmesg | grep wl
[   13.668636] wl: module license 'MIXED/Proprietary' taints kernel.
[   13.672478] wl: module verification failed: signature and/or  required key missing - tainting kernel
[   13.707374] INFO @wl_cfg80211_attach : Registered CFG80211 phy
[   13.876108] wlan0: Broadcom BCM4365 802.11 Hybrid Wireless Controller 6.30.223.141 (r415941)
[ 2426.712212] Modules linked in: bnep rfcomm bluetooth snd_hda_codec_hdmi snd_hda_codec_realtek lib80211_crypt_tkip wl(POX) uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_core videodev lib80211 cfg80211 asus_nb_wmi asus_wmi sparse_keymap snd_hda_intel snd_hda_codec snd_hwdep intel_rapl snd_pcm coretemp kvm crct10dif_pclmul snd_page_alloc crc32_pclmul ghash_clmulni_intel cryptd snd_seq_midi snd_seq_midi_event snd_rawmidi rtsx_pci_ms memstick snd_seq joydev snd_seq_device snd_timer serio_raw i915 snd drm_kms_helper soundcore drm wmi i2c_algo_bit parport_pc ppdev video mac_hid lp parport rtsx_pci_sdmmc psmouse r8169 mii ahci rtsx_pci libahci
[ 2426.712499] CPU: 1 PID: 389 Comm: wl_event_handle Tainted: P           OX 3.13.0-44-generic #73-Ubuntu
[ 2426.712855]  [<ffffffffa05b2528>] wl_bss_connect_done.isra.21+0x98/0x1a0 [wl]
[ 2426.713001]  [<ffffffffa05b282c>] wl_notify_connect_status+0x1fc/0x410 [wl]
[ 2426.713147]  [<ffffffffa05b1135>] wl_event_handler+0x55/0x220 [wl]
[ 2426.713291]  [<ffffffffa05b10e0>] ? wl_get_assoc_ies+0x240/0x240 [wl]

---

### Post by Baurzhan on 2015-01-25
The performanche is similar, I mean never more than 2 bars near the router and 0 bar at 3 m or more off the router! 
While with the second OS Wifi works well.

---

### Post by chili555 on 2015-01-25
> I dit these two commands ' sudo apt-get remove bcmwl-kernel-source' && 'sudo apt-get install bcmwl-kernel-source'Why? What suggests that the driver suite was improperly installed? Did you read some other post? May I have a link?

---

### Post by Baurzhan on 2015-01-25
Yes, since one week yet. I tried to overcome this issue from other posts, but it appeared not that easy for me. 
Here are mainstream links in my opinion :
[http://askubuntu.com/questions/576618/ubuntu-wireless-got-disconnected-when-far-from-router?noredirect=1#comment797594_576618](http://askubuntu.com/questions/576618/ubuntu-wireless-got-disconnected-when-far-from-router?noredirect=1#comment797594_576618)
[http://askubuntu.com/questions/55868/installing-broadcom-wireless-drivers](http://askubuntu.com/questions/55868/installing-broadcom-wireless-drivers)
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

I used to spend time on those places in order to learn more about my problem, but coudn't clear anything. 
Thanks again for helping me.

---

### Post by chili555 on 2015-01-25
Will you please try with N speeds turned off in the router? Reboot the router and let us see again:```
dmesg | grep wl
``` We will be interested in entries timestamped after the last you posted above:```
[ 2426.713291] [<ffffffffa05b10e0>] ? wl_get_assoc_ies+0x240/0x240 [wl]
```

---

### Post by Baurzhan on 2015-01-26
Would you please tell  me which one does correspond to the N speed cause I can't find it.
Maybe is has an other meaning in my zte router. Thanks
[http://www.toptechnology4u.com/2012/11/zte-w300-wireless-settings.html](http://www.toptechnology4u.com/2012/11/zte-w300-wireless-settings.html)

---

### Post by chili555 on 2015-01-26
Please see Access Point Settings > Wireless Mode. Currently, your router is set to 802.11b+g+[COLOR="#FF0000"]n[/COLOR]. See if you can drop down the menu and select 802.11b+g only. Click Save.

Then in the Network Manager icon on your computer, click disconnect and then reconnect.

Is the performance improved?

---

### Post by Baurzhan on 2015-01-27
I went to my router setting; however, the default setting is '802.11 b+g' and the other two options are either b or g. The 802.11 b+g+n doesn't exist.
So I tried out both, b and g. And nothing happened. The performance is still the same. (not more than 2 bars )
Any suggestions please.

azzed@azzed-Ubu:~$ dmesg | grep wl
[   13.802332] wl: module license 'MIXED/Proprietary' taints kernel.
[   13.806143] wl: module verification failed: signature and/or  required key missing - tainting kernel
[   13.840111] INFO @wl_cfg80211_attach : Registered CFG80211 phy
[   14.034634] wlan0: Broadcom BCM4365 802.11 Hybrid Wireless Controller 6.30.223.141 (r415941)

---

### Post by chili555 on 2015-01-27
>  The 802.11 b+g+n doesn't exist.It certainly exists in the link you gave us; perhaps you have a different model.

The only possible suggestion I still have is that in the scan results, your access point shows as Quality 34/70:> Cell 01 - Address: 00:15:EB:F6:2F: DC
Channel:8
Frequency:2.447 GHz (Channel 8)
[COLOR="#FF0000"]Quality=34/70[/COLOR] Signal level=-76 dBm 
Encryption key: On
ESSID:"ZTE"
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
36 Mb/s; 48 Mb/s; 54 Mb/s
Mode:MasterPlease experiment with the direction of the antenna. Be sure there are as few obstructions as possible between your computer and the router. Experiment with the orientation of the router; perhaps the signal is better with the router facing in different directions. Check again:```
iwconfig
```See if any change you make improves the signal quality:```
wlan0     IEEE 802.11abgn  ESSID:"GBR1"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: xx:D7:19:41:54:xx  
          Bit Rate=115.6 Mb/s   Tx-Power=15 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          [COLOR="#FF0000"]Link Quality=53/70[/COLOR]  Signal level=-57 dBm  

```Aside from that, I have no other suggestions.

---

