---
title: "Very slow and unstable WiFi on BCM4313 (xubuntu 14.04)"
date: 2015-12-25
forum: Networking &amp; Wireless
---

### Post by eshkel on 2015-12-25
Last few weeks I noticed slow internet and last few days it becomes very unstable on my dell lattitude.

previously I uses script to enable brcmsmac driver, and it works quite stable (and faster than wl)

---
sudo rmmod wl
sudo modprobe brcmsmac
---

few days ago this script doesn't help, either wl and brcmsmac becomes unstable, the changing to brcmsmac even not allow to authenticate on WiFi.
in dmesg I see multiple
[37828.352012] wlan0: send auth to 14:cc:20:c1:bc:66 (try 1/3)
[37828.372097] wlan0: authenticated
[37833.350698] wlan0: deauthenticating from 14:cc:20:c1:bc:66 by local choice (reason=3)


lspci -nn | grep 0280

02:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)

I reinstalled the wl drivers according to [http://askubuntu.com/questions/55868/installing-broadcom-wireless-drivers](http://askubuntu.com/questions/55868/installing-broadcom-wireless-drivers)

the ping to WiFi router is abnormally unstable (few ms to few seconds, same as internet resources, the router is 5 meters far from me)
64 bytes from 192.168.0.1: icmp_seq=72 ttl=64 time=29.1 ms
64 bytes from 192.168.0.1: icmp_seq=73 ttl=64 time=1.54 ms
64 bytes from 192.168.0.1: icmp_seq=74 ttl=64 time=1.59 ms
64 bytes from 192.168.0.1: icmp_seq=75 ttl=64 time=199 ms
64 bytes from 192.168.0.1: icmp_seq=76 ttl=64 time=10914 ms
64 bytes from 192.168.0.1: icmp_seq=77 ttl=64 time=9933 ms
64 bytes from 192.168.0.1: icmp_seq=78 ttl=64 time=8986 ms
64 bytes from 192.168.0.1: icmp_seq=79 ttl=64 time=8019 ms
64 bytes from 192.168.0.1: icmp_seq=80 ttl=64 time=7033 ms
64 bytes from 192.168.0.1: icmp_seq=81 ttl=64 time=6056 ms
64 bytes from 192.168.0.1: icmp_seq=82 ttl=64 time=9005 ms
64 bytes from 192.168.0.1: icmp_seq=83 ttl=64 time=8075 ms
64 bytes from 192.168.0.1: icmp_seq=84 ttl=64 time=7077 ms
64 bytes from 192.168.0.1: icmp_seq=85 ttl=64 time=6156 ms
64 bytes from 192.168.0.1: icmp_seq=86 ttl=64 time=5164 ms
64 bytes from 192.168.0.1: icmp_seq=87 ttl=64 time=4183 ms
64 bytes from 192.168.0.1: icmp_seq=88 ttl=64 time=3713 ms
64 bytes from 192.168.0.1: icmp_seq=89 ttl=64 time=2738 ms
64 bytes from 192.168.0.1: icmp_seq=90 ttl=64 time=1741 ms
64 bytes from 192.168.0.1: icmp_seq=91 ttl=64 time=762 ms
64 bytes from 192.168.0.1: icmp_seq=92 ttl=64 time=7.96 ms
64 bytes from 192.168.0.1: icmp_seq=93 ttl=64 time=286 ms
64 bytes from 192.168.0.1: icmp_seq=94 ttl=64 time=745 ms


WiFi on smartphone works fine (no huge delays on sites browsing) connected to same router. 
CRDA region set to UA.

Any help would be much appreciated,
Eugene.

---

### Post by Hadaka on 2015-12-25
Hi, your card : BCM4313 802.11bgn Wireless Network Adapter [[COLOR=#ff0000]14e4:4727[/COLOR]][COLOR=#000000]
Uses "brcmsmac/bcma" combination . shown as *Special case #1. for 14.04 here
[http://ubuntuforums.org/showthread.php?t=2214110](http://ubuntuforums.org/showthread.php?t=2214110)
Please open a terminal and do.. *ignore any not found*[/COLOR]
```
sudo apt-get install --reinstall linux-firmware
sudo apt-get remove --purge bcmwl-kernel-source
echo "blacklist b43\nblacklist ssb" | sudo tee -a /etc/modprobe.d/blacklist.conf
sudo modprobe -rf [COLOR=#000000]brcmsmac
sudo modprobe -v [/COLOR][COLOR=#000000]brcmsmac[/COLOR]
```

---

### Post by Bucky Ball on 2015-12-25
Welcome ... and post any terminal output between code tags, please (see last link in my signture). :)

---

### Post by eshkel on 2015-12-27
> **Hadaka said:**
> Hi, your card : BCM4313 802.11bgn Wireless Network Adapter [[COLOR=#ff0000]14e4:4727[/COLOR]][COLOR=#000000]
Uses "brcmsmac/bcma" combination . shown as *Special case #1. for 14.04 here
[http://ubuntuforums.org/showthread.php?t=2214110](http://ubuntuforums.org/showthread.php?t=2214110)
Please open a terminal and do.. *ignore any not found*[/COLOR]
```
sudo apt-get install --reinstall linux-firmware
sudo apt-get remove --purge bcmwl-kernel-source
echo "blacklist b43\nblacklist ssb" | sudo tee -a /etc/modprobe.d/blacklist.conf
sudo modprobe -rf [COLOR=#000000]brcmsmac
sudo modprobe -v [/COLOR][COLOR=#000000]brcmsmac[/COLOR]
```

Thank you for your help.
Applied commands from post above.
I have two routers at home. TP-LINK WR743ND and LINKSYS e1200, when changed to second router I noticed high ping
```

ping: sendmsg: Network is unreachable
ping: sendmsg: Network is unreachable
ping: sendmsg: Network is unreachable
64 bytes from 176.31.92.112: icmp_seq=56348 ttl=55 time=725 ms
64 bytes from 176.31.92.112: icmp_seq=56355 ttl=55 time=9808 ms
64 bytes from 176.31.92.112: icmp_seq=56356 ttl=55 time=11360 ms
64 bytes from 176.31.92.112: icmp_seq=56357 ttl=55 time=12364 ms
64 bytes from 176.31.92.112: icmp_seq=56358 ttl=55 time=11449 ms
64 bytes from 176.31.92.112: icmp_seq=56359 ttl=55 time=10639 ms
64 bytes from 176.31.92.112: icmp_seq=56360 ttl=55 time=10228 ms
64 bytes from 176.31.92.112: icmp_seq=56362 ttl=55 time=12712 ms
64 bytes from 176.31.92.112: icmp_seq=56363 ttl=55 time=15595 ms
64 bytes from 176.31.92.112: icmp_seq=56364 ttl=55 time=18114 ms
64 bytes from 176.31.92.112: icmp_seq=56366 ttl=55 time=21084 ms
64 bytes from 176.31.92.112: icmp_seq=56367 ttl=55 time=27164 ms
64 bytes from 176.31.92.112: icmp_seq=56368 ttl=55 time=28522 ms
64 bytes from 176.31.92.112: icmp_seq=56369 ttl=55 time=34799 ms

```
Switched to first one and back - either works ok.
When I try to switch back to the first router - WiFi connection on it was enabled at 5-7 try. I saw some errors when executed dmesg
```

[124354.725882] cfg80211: Calling CRDA for country: UA
[124354.731336] cfg80211: Regulatory domain changed to country: UA
[124354.731341] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[124354.731344] cfg80211:   (2400000 KHz - 2483500 KHz @ 40000 KHz), (N/A, 2000 mBm)
[124354.731346] cfg80211:   (5150000 KHz - 5350000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[124354.731348] cfg80211:   (57240000 KHz - 65880000 KHz @ 2160000 KHz), (N/A, 4000 mBm)
[124354.850333] cfg80211: Calling CRDA to update world regulatory domain
[124354.853909] cfg80211: World regulatory domain updated:
[124354.853914] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[124354.853917] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[124354.853919] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[124354.853921] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[124354.853924] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[124354.853926] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[124354.854277] cfg80211: Calling CRDA for country: UA
[124354.859998] cfg80211: Regulatory domain changed to country: UA
[124354.860004] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[124354.860007] cfg80211:   (2400000 KHz - 2483500 KHz @ 40000 KHz), (N/A, 2000 mBm)
[124354.860010] cfg80211:   (5150000 KHz - 5350000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[124354.860012] cfg80211:   (57240000 KHz - 65880000 KHz @ 2160000 KHz), (N/A, 4000 mBm)
[124354.945880] ------------[ cut here ]------------
[124354.945919] WARNING: CPU: 3 PID: 9939 at /build/linux-_xRakU/linux-3.13.0/net/wireless/sme.c:662 __cfg80211_connect_result+0x3db/0x420 [cfg80211]()
[124354.945922] Modules linked in: brcmsmac cordic brcmutil bcma mac80211 nls_iso8859_1 hid_logitech_dj snd_hda_codec_hdmi snd_hda_codec_idt rfcomm bnep hid_generic usbhid hid dell_wmi sparse_keymap binfmt_misc intel_rapl x86_pkg_temp_thermal intel_powerclamp dell_laptop coretemp kvm_intel dcdbas kvm snd_hda_intel crct10dif_pclmul crc32_pclmul snd_hda_codec snd_hwdep snd_pcm snd_page_alloc snd_seq_midi snd_seq_midi_event snd_rawmidi aesni_intel aes_x86_64 lrw gf128mul wl(POX) glue_helper ablk_helper cryptd cfg80211 snd_seq snd_seq_device btusb snd_timer bluetooth snd joydev serio_raw lpc_ich soundcore shpchp i915 mei_me mei drm_kms_helper drm i2c_algo_bit wmi parport_pc ppdev video mac_hid lp parport mmc_block psmouse ahci e1000e sdhci_pci libahci sdhci ptp pps_core
[124354.945996] CPU: 3 PID: 9939 Comm: kworker/u8:2 Tainted: P        W  OX 3.13.0-74-generic #118-Ubuntu
[124354.945999] Hardware name: Dell Inc. Latitude E6330/0F7WM9, BIOS A10 05/20/2013
[124354.946017] Workqueue: cfg80211 cfg80211_event_work [cfg80211]
[124354.946020]  0000000000000009 ffff8801505a5ca8 ffffffff81724b70 0000000000000000
[124354.946026]  ffff8801505a5ce0 ffffffff810678bd 0000000000000000 0000000000000000
[124354.946031]  ffff8800a72a5818 ffff880036ae7400 ffff8803089b4000 ffff8801505a5cf0
[124354.946036] Call Trace:
[124354.946045]  [<ffffffff81724b70>] dump_stack+0x45/0x56
[124354.946052]  [<ffffffff810678bd>] warn_slowpath_common+0x7d/0xa0
[124354.946057]  [<ffffffff8106799a>] warn_slowpath_null+0x1a/0x20
[124354.946080]  [<ffffffffa0343b9b>] __cfg80211_connect_result+0x3db/0x420 [cfg80211]
[124354.946100]  [<ffffffffa03225a4>] cfg80211_process_wdev_events+0x194/0x1c0 [cfg80211]
[124354.946119]  [<ffffffffa0322610>] cfg80211_process_rdev_events+0x40/0x90 [cfg80211]
[124354.946136]  [<ffffffffa031e01e>] cfg80211_event_work+0x1e/0x30 [cfg80211]
[124354.946143]  [<ffffffff81083cd2>] process_one_work+0x182/0x450
[124354.946148]  [<ffffffff81084ac1>] worker_thread+0x121/0x410
[124354.946154]  [<ffffffff810849a0>] ? rescuer_thread+0x430/0x430
[124354.946159]  [<ffffffff8108b8a2>] kthread+0xd2/0xf0
[124354.946164]  [<ffffffff8108b7d0>] ? kthread_create_on_node+0x1c0/0x1c0
[124354.946170]  [<ffffffff817356a8>] ret_from_fork+0x58/0x90
[124354.946175]  [<ffffffff8108b7d0>] ? kthread_create_on_node+0x1c0/0x1c0
[124354.946178] ---[ end trace 1a282412de56ef15 ]---
[124355.425670] systemd-hostnamed[18326]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!
[124696.570539] cfg80211: Calling CRDA to update world regulatory domain
[124696.576887] cfg80211: World regulatory domain updated:
[124696.576891] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[124696.576893] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[124696.576895] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[124696.576896] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[124696.576898] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[124696.576899] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[124696.577069] cfg80211: Calling CRDA for country: UA
[124696.580475] cfg80211: Regulatory domain changed to country: UA
[124696.580478] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[124696.580480] cfg80211:   (2400000 KHz - 2483500 KHz @ 40000 KHz), (N/A, 2000 mBm)
[124696.580481] cfg80211:   (5150000 KHz - 5350000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[124696.580482] cfg80211:   (57240000 KHz - 65880000 KHz @ 2160000 KHz), (N/A, 4000 mBm)
[124697.106896] cfg80211: Calling CRDA for country: UA
[124697.112557] cfg80211: Regulatory domain changed to country: UA
[124697.112564] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[124697.112569] cfg80211:   (2400000 KHz - 2483500 KHz @ 40000 KHz), (N/A, 2000 mBm)
[124697.112573] cfg80211:   (5150000 KHz - 5350000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[124697.112576] cfg80211:   (57240000 KHz - 65880000 KHz @ 2160000 KHz), (N/A, 4000 mBm)

```

At office I'm using TP-LINK router as well (but different model). Wired connection works fine for both of them. Other devices don't have such troubles.

---

### Post by eshkel on 2015-12-27
Thank you, sorry for pure formatting.

---

### Post by Hadaka on 2015-12-27
Hi, Ubuntu/linux is not windows,android,mac or any other os.
so what works with alot of other devices, may or may not work
with Ubuntu.
The typical settings for the router is WPA2 AES and no TKIP
Country codes will also create issues, yours is currently set at UA
if this is not correct, see this link to find your correct 2 letter.UPPER CASE code.
[http://www.osb.org/geog/countrycodes.html](http://www.osb.org/geog/countrycodes.html)
and replace the "XX's" with the correct code.
```
sudo iw reg set [COLOR=#ff0000]XX[/COLOR]
sudo sed -i 's/^REG.*=$/&[COLOR=#ff0000]XX[/COLOR]/' /etc/default/crda
```
If you are still having issues please go here.
[http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)
Read the instructions then post your [B]wireless-info.txt 

[/B]

---

### Post by eshkel on 2015-12-28
Thank you a lot, seems the connection is stable now (added brcmsmac to /etc/modules). But the speed is quite low. On laptop I see download speed 5-7 Mbps and  upload speed 3-5 Mbps. On smartphone I see download speed 26-28 Mbps  and upload speed 22-36 Mbps. This is very close to ISP limits (30Mbps). Is it possible to increase download/upload speed for this module?

The UA is correct country code. 
wireless-info.txt attached as archive [ATTACH]266418[/ATTACH]

---

### Post by eshkel on 2015-12-29
Today the problem with WiFi connection appeared again. Laptop can't connect to router through wifi. 
dmesg output
```

[29139.750324] atkbd serio0: Unknown key pressed (translated set 2, code 0x88 on isa0060/serio0).
[29139.750330] atkbd serio0: Use 'setkeycodes e008 <keycode>' to make it known.
[29141.291885] atkbd serio0: Unknown key pressed (translated set 2, code 0x88 on isa0060/serio0).
[29141.291892] atkbd serio0: Use 'setkeycodes e008 <keycode>' to make it known.
[29141.556397] atkbd serio0: Unknown key pressed (translated set 2, code 0x88 on isa0060/serio0).
[29141.556405] atkbd serio0: Use 'setkeycodes e008 <keycode>' to make it known.
[29141.992787] usb 1-1.4: USB disconnect, device number 3
[29152.610222] atkbd serio0: Unknown key pressed (translated set 2, code 0x88 on isa0060/serio0).
[29152.610232] atkbd serio0: Use 'setkeycodes e008 <keycode>' to make it known.
[29152.879272] usb 1-1.4: new full-speed USB device number 4 using ehci-pci
[29152.975119] usb 1-1.4: New USB device found, idVendor=413c, idProduct=8197
[29152.975127] usb 1-1.4: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[29152.975131] usb 1-1.4: Product: BCM20702A0
[29152.975134] usb 1-1.4: Manufacturer: Broadcom Corp
[29152.975137] usb 1-1.4: SerialNumber: B00594EF8F31
[29152.975945] usb 1-1.4: Direct firmware load failed with error -2
[29152.975953] usb 1-1.4: Falling back to user helper
[29152.977306] Bluetooth: can't load firmware, may not work correctly
[29156.956941] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[29156.956957] brcmsmac bcma0:0: brcms_ops_config: change power-save mode: false (implement)
[29156.957675] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[29179.555768] wlan0: authenticate with 14:cc:20:c1:bc:66
[29179.555840] wlan0: send auth to 14:cc:20:c1:bc:66 (try 1/3)
[29179.822612] wlan0: authenticated
[29184.566425] wlan0: deauthenticating from 14:cc:20:c1:bc:66 by local choice (reason=3)
[29196.187196] wlan0: authenticate with 14:cc:20:c1:bc:66
[29196.187268] wlan0: send auth to 14:cc:20:c1:bc:66 (try 1/3)
[29196.805941] wlan0: send auth to 14:cc:20:c1:bc:66 (try 2/3)
[29197.771242] wlan0: send auth to 14:cc:20:c1:bc:66 (try 3/3)
[29198.796575] wlan0: authentication with 14:cc:20:c1:bc:66 timed out
[29201.198144] wlan0: deauthenticating from 14:cc:20:c1:bc:66 by local choice (reason=3)

```

dmesg output after laptop reboot (can't connect as well)
```

[    5.016269] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    5.016313] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[    5.052192] ACPI Warning: 0x0000000000000428-0x000000000000042f SystemIO conflicts with Region \PMIO 1 (20131115/utaddress-251)
[    5.052202] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    5.052207] ACPI Warning: 0x0000000000000530-0x000000000000053f SystemIO conflicts with Region \GPIO 1 (20131115/utaddress-251)
[    5.052209] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    5.052211] ACPI Warning: 0x0000000000000500-0x000000000000052f SystemIO conflicts with Region \GPIO 1 (20131115/utaddress-251)
[    5.052213] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    5.052214] lpc_ich: Resource conflict(s) found affecting gpio_ich
[    5.052387] snd_hda_intel 0000:00:1b.0: irq 47 for MSI/MSI-X
[    5.071777] autoconfig: line_outs=1 (0xe/0x0/0x0/0x0/0x0) type:line
[    5.071781]    speaker_outs=1 (0xd/0x0/0x0/0x0/0x0)
[    5.071782]    hp_outs=1 (0xb/0x0/0x0/0x0/0x0)
[    5.071783]    mono: mono_out=0x0
[    5.071784]    inputs:
[    5.071785]      Dock Mic=0xf
[    5.071786]      Internal Mic=0x11
[    5.071788]      Headset Mic=0xa
[    5.087194] input: HDA Intel PCH HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input19
[    5.087268] input: HDA Intel PCH HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input18
[    5.087327] input: HDA Intel PCH HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input17
[    5.087384] input: HDA Intel PCH Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input16
[    5.087434] input: HDA Intel PCH Dock Line Out as /devices/pci0000:00/0000:00:1b.0/sound/card0/input15
[    5.087482] input: HDA Intel PCH Headset Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input14
[    5.087531] input: HDA Intel PCH Dock Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input13
[    5.136171] e1000e 0000:00:19.0: irq 44 for MSI/MSI-X
[    5.240233] e1000e 0000:00:19.0: irq 44 for MSI/MSI-X
[    5.240332] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    5.240345] cfg80211: Calling CRDA for country: UA
[    5.240601] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    5.409266] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[    5.409318] brcmsmac bcma0:0: brcms_ops_config: change power-save mode: false (implement)
[    5.409955] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[    5.409978] cfg80211: Regulatory domain changed to country: UA
[    5.409980] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[    5.409982] cfg80211:   (2400000 KHz - 2483500 KHz @ 40000 KHz), (N/A, 2000 mBm)
[    5.409984] cfg80211:   (5150000 KHz - 5350000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[    5.409985] cfg80211:   (57240000 KHz - 65880000 KHz @ 2160000 KHz), (N/A, 4000 mBm)
[    5.410267] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[    6.141786] init: plymouth-upstart-bridge main process ended, respawning
[    6.146485] init: plymouth-upstart-bridge main process (1399) terminated with status 1
[    6.146495] init: plymouth-upstart-bridge main process ended, respawning
[    6.286446] wlan0: authenticate with 14:cc:20:c1:bc:66
[    6.289919] wlan0: send auth to 14:cc:20:c1:bc:66 (try 1/3)
[    6.294860] wlan0: authenticated
[    6.295004] brcmsmac bcma0:0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[    6.295007] brcmsmac bcma0:0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[    6.297598] wlan0: associate with 14:cc:20:c1:bc:66 (try 1/3)
[    6.366588] wlan0: RX AssocResp from 14:cc:20:c1:bc:66 (capab=0x431 status=0 aid=2)
[    6.367216] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[    6.367223] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[    6.367237] wlan0: associated
[    6.367271] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[    7.081376] init: plymouth-stop pre-start process (1731) terminated with status 1
[   10.435590] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: 1 addresses (implement)
[   34.660204] audit_printk_skb: 114 callbacks suppressed
[   34.660206] type=1400 audit(1451384627.181:49): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=3007 comm="apparmor_parser"
[   34.660212] type=1400 audit(1451384627.181:50): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=3007 comm="apparmor_parser"
[   34.660504] type=1400 audit(1451384627.181:51): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=3007 comm="apparmor_parser"



```
I compared wireless-info.txt when WiFi works and when it doesn't - the only valuable(as for me) different part was WiFi channel (8 - doesn't work, 11 - works). Changed router configuration to using channel 11 - I was able to browse internet but time to time the connection is stucking, the ping to router at that time increases to few seconds.

---

### Post by Bucky Ball on 2015-12-29
Switch to channel 6 and see if that makes a difference. You only need to configure this on the router. 

IPv6 tab should be set to ignore, 'General' tab first two ticked; 'Automatically Connect ...' and 'All Users may Connect'.

---

### Post by eshkel on 2015-12-29
IPv6 was set to ingore (previous value - auto)
 the 'Automatically Connect ...' and 'All Users may Connect' were checked, so I didn't change it. 
Channel 6 works similar to 8 (Dwnld 3-6 Mbps, upld 2-3Mbps).
 Channel 2 has worst speed (Dwnld 0.5-1 Mbps, upld ~1 Mbps),
Channel 4 was in middle (Dwnld 2-3 Mbps, upld 1-2Mbps).

Does it mean something?

---

### Post by eshkel on 2015-12-30
Today 8 channel works unstable, channel 13 works (dwnld 3, upload 0.7)

---

