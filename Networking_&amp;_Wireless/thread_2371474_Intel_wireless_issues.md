---
title: "Intel wireless issues"
date: 2017-09-14
forum: Networking &amp; Wireless
---

### Post by hamakei on 2017-09-14
Sorry for butting in to an old thread, but I've been having a similar problem for a few weeks now and am tearing my hair out trying to find a solution. I'm running an Intel 7260, and am experiencing the same inexplicable drops with my connection. It can happen after a few minutes, or a few hours, but like the OP it does seem to happen quicker if there is a lot of network traffic.

So...I'm running firmware [COLOR=#000000]iwlwifi-7260-17.ucode[/COLOR], I've disabled power saving, I've disabled 802.11n support, I'm pretty sure it's nothing to do with temperature or electrical interference, I'm using software crypto, both the software and hardware locks for wifi are off,

And nothing short of a complete reboot seems to fix it. Killing everything network related and restarting it just reports that the device isn't ready (both WPA Supplicant and network-manager, and no, I'm not running them both at the same time).

I'm pretty sure this started happening after an update, possibly of the kernel...as I haven't changed any hardware for months...and all updates have come through my package manager so I haven't been installing anything weird...

This is my dmesg, though I notice I'm getting something to do with a "stuck timer" although the end result seems to be the same "failed to wake NIC for hcmd" error...which I'm guessing filters through to a "device not ready" error higher up..

> [ 3257.255016] ------------[ cut here ]------------[ 3257.255040] WARNING: CPU: 0 PID: 2916 at /build/linux-YyUNAI/linux-4.4.0/drivers/net/wireless/iwlwifi/iwl-trans.h:1058 iwl_pcie_txq_stuck_timer+0x2bd/0x390 [iwlwifi]()
[ 3257.255043] Modules linked in: drbg ansi_cprng ctr ccm rfcomm snd_hrtimer bnep binfmt_misc arc4 nvidia_uvm(POE) iwlmvm mac80211 kvm_amd kvm irqbypass crct10dif_pclmul crc32_pclmul ghash_clmulni_intel aesni_intel snd_hda_codec_hdmi snd_hda_codec_realtek snd_hda_codec_generic aes_x86_64 lrw snd_hda_intel snd_hda_codec gf128mul glue_helper ablk_helper snd_hda_core cryptd fam15h_power i2c_piix4 edac_mce_amd snd_hwdep snd_seq_midi k10temp edac_core snd_pcm snd_seq_midi_event serio_raw joydev snd_rawmidi btusb snd_seq usblp input_leds btrtl snd_seq_device btbcm btintel snd_timer bluetooth snd iwlwifi soundcore cfg80211 tpm_infineon shpchp wmi 8250_fintek mac_hid f71882fg parport_pc ppdev lp parport autofs4 hid_generic usbhid hid uas usb_storage nvidia_drm(POE) nvidia_modeset(POE) nvidia(POE) drm_kms_helper
[ 3257.255118]  syscopyarea sysfillrect sysimgblt fb_sys_fops ahci drm libahci r8169 mii fjes video
[ 3257.255133] CPU: 0 PID: 2916 Comm: chromium-browse Tainted: P        W  OE   4.4.0-93-generic #116-Ubuntu
[ 3257.255137] Hardware name: MSI MS-7913/A88XI AC V2 (MS-7913), BIOS V2.1 04/15/2015
[ 3257.255140]  0000000000000286 bc91cb17894a6fa4 ffff88043ec03da8 ffffffff813f9f83
[ 3257.255146]  0000000000000000 ffffffffc0d7e0b8 ffff88043ec03de0 ffffffff810812f2
[ 3257.255150]  000000000000000b ffff8804229c8200 ffff8804229c8000 0000000000a02e60
[ 3257.255155] Call Trace:
[ 3257.255158]  <IRQ>  [<ffffffff813f9f83>] dump_stack+0x63/0x90
[ 3257.255172]  [<ffffffff810812f2>] warn_slowpath_common+0x82/0xc0
[ 3257.255177]  [<ffffffff8108143a>] warn_slowpath_null+0x1a/0x20
[ 3257.255190]  [<ffffffffc0d665ad>] iwl_pcie_txq_stuck_timer+0x2bd/0x390 [iwlwifi]
[ 3257.255204]  [<ffffffffc0d662f0>] ? iwl_pcie_txq_unmap+0xf0/0xf0 [iwlwifi]
[ 3257.255212]  [<ffffffff810ecfe5>] call_timer_fn+0x35/0x120
[ 3257.255224]  [<ffffffffc0d662f0>] ? iwl_pcie_txq_unmap+0xf0/0xf0 [iwlwifi]
[ 3257.255230]  [<ffffffff810ed99a>] run_timer_softirq+0x23a/0x2f0
[ 3257.255236]  [<ffffffff81085dd1>] __do_softirq+0x101/0x290
[ 3257.255240]  [<ffffffff810860d3>] irq_exit+0xa3/0xb0
[ 3257.255247]  [<ffffffff81845ca2>] smp_apic_timer_interrupt+0x42/0x50
[ 3257.255252]  [<ffffffff81843f62>] apic_timer_interrupt+0x82/0x90
[ 3257.255254]  <EOI> 
[ 3257.255258] ---[ end trace 3c17d4c03d58a29b ]---


[ 3262.148755] iwlwifi 0000:03:00.0: Scan failed! ret -5
[ 3263.167762] iwlwifi 0000:03:00.0: Failed to wake NIC for hcmd
[ 3263.167803] iwlwifi 0000:03:00.0: Error sending SCAN_OFFLOAD_REQUEST_CMD: enqueue_hcmd failed: -5

One thing I did notice that was strange...was that my Ubuntu repository only seems to have version 1.157 of linux-firmware, not 1.161. No idea why.

---

### Post by chili555 on 2017-09-14
> This is my dmesg, though I notice I'm getting something to do with a "stuck timer" although the end result seems to be the same "failed to wake NIC for hcmd" error...which I'm guessing filters through to a "device not ready" error higher up..May we see:```
modinfo iwlwifi | grep parm
```We may see something we can use: wd_disable

The -17 firmware is the latest workable for your device. We might just see if it is corrupted.```
md5sum  /lib/firmware/iwlwifi-7260-17.ucode
```We hope we see:```
chili@T440p:~$ md5sum  /lib/firmware/iwlwifi-7260-17.ucode
[COLOR="#FF0000"]73a217f55c47d3a70bb5dbbe1d676423 [/COLOR] /lib/firmware/iwlwifi-7260-17.ucode

```

---

### Post by jeremy31 on 2017-09-14
Split from [https://ubuntuforums.org/showthread.php?t=2339439](https://ubuntuforums.org/showthread.php?t=2339439)

---

### Post by chili555 on 2017-09-15
I understand that your md5sum does not match. Let's reinstall the firmware:

```
wget http://security.ubuntu.com/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.164.1_all.deb
sudo dpkg -i linux-firmware*.deb
```Reboot.

---

### Post by hamakei on 2017-09-16
I updated the firmware as you suggested and now the md5 checksum matches yours...

But it still hangs and stops responding after a variable amount of time.

My dmesg:
```
[ 8733.836251] ------------[ cut here ]------------[ 8733.836263] WARNING: CPU: 1 PID: 12169 at /build/linux-YyUNAI/linux-4.4.0/drivers/net/wireless/iwlwifi/iwl-trans.h:1058 iwl_pcie_txq_stuck_timer+0x2bd/0x390 [iwlwifi]()
[ 8733.836264] Modules linked in: dm_crypt algif_skcipher af_alg drbg ansi_cprng ctr ccm nls_utf8 udf crc_itu_t rfcomm snd_hrtimer bnep binfmt_misc arc4 nvidia_uvm(POE) iwlmvm kvm_amd kvm mac80211 irqbypass crct10dif_pclmul crc32_pclmul ghash_clmulni_intel aesni_intel aes_x86_64 lrw gf128mul glue_helper ablk_helper cryptd snd_hda_codec_hdmi joydev snd_hda_codec_realtek serio_raw usblp input_leds snd_hda_codec_generic fam15h_power k10temp edac_mce_amd snd_hda_intel edac_core snd_hda_codec i2c_piix4 snd_hda_core snd_hwdep btusb snd_pcm snd_seq_midi btrtl snd_seq_midi_event btbcm snd_rawmidi btintel snd_seq bluetooth snd_seq_device snd_timer iwlwifi snd soundcore cfg80211 tpm_infineon wmi shpchp 8250_fintek mac_hid f71882fg parport_pc ppdev lp parport autofs4 hid_generic usbhid hid uas usb_storage nvidia_drm(POE)
[ 8733.836301]  nvidia_modeset(POE) nvidia(POE) drm_kms_helper syscopyarea sysfillrect sysimgblt fb_sys_fops ahci drm libahci r8169 mii fjes video
[ 8733.836309] CPU: 1 PID: 12169 Comm: FU Tainted: P        W  OE   4.4.0-93-generic #116-Ubuntu
[ 8733.836310] Hardware name: MSI MS-7913/A88XI AC V2 (MS-7913), BIOS V2.1 04/15/2015
[ 8733.836312]  0000000000200286 b77c971c7af74b01 ffff88043ec83da8 ffffffff813f9f83
[ 8733.836314]  0000000000000000 ffffffffc0d890b8 ffff88043ec83de0 ffffffff810812f2
[ 8733.836316]  000000000000001e ffff880428e60200 ffff880428e60000 0000000000a02eac
[ 8733.836318] Call Trace:
[ 8733.836319]  <IRQ>  [<ffffffff813f9f83>] dump_stack+0x63/0x90
[ 8733.836335]  [<ffffffff810812f2>] warn_slowpath_common+0x82/0xc0
[ 8733.836337]  [<ffffffff8108143a>] warn_slowpath_null+0x1a/0x20
[ 8733.836342]  [<ffffffffc0d715ad>] iwl_pcie_txq_stuck_timer+0x2bd/0x390 [iwlwifi]
[ 8733.836346]  [<ffffffff8171e1d8>] ? sk_reset_timer+0x18/0x30
[ 8733.836350]  [<ffffffffc0d712f0>] ? iwl_pcie_txq_unmap+0xf0/0xf0 [iwlwifi]
[ 8733.836353]  [<ffffffff810ecfe5>] call_timer_fn+0x35/0x120
[ 8733.836358]  [<ffffffffc0d712f0>] ? iwl_pcie_txq_unmap+0xf0/0xf0 [iwlwifi]
[ 8733.836360]  [<ffffffff810ed99a>] run_timer_softirq+0x23a/0x2f0
[ 8733.836362]  [<ffffffff81085dd1>] __do_softirq+0x101/0x290
[ 8733.836364]  [<ffffffff810860d3>] irq_exit+0xa3/0xb0
[ 8733.836367]  [<ffffffff81845ca2>] smp_apic_timer_interrupt+0x42/0x50
[ 8733.836369]  [<ffffffff81843f62>] apic_timer_interrupt+0x82/0x90
[ 8733.836370]  <EOI> 
[ 8733.836380] ---[ end trace 2b1d1f6b8d63ef8c ]---

```

I also noticed upon restarting that the console had been filled with dozens of messages reading:
> Failed to wake NIC for hcmd

---

### Post by hamakei on 2017-09-16
More dmesg:
```
[ 1299.114295] iwlwifi 0000:03:00.0: Failed to wake NIC for hcmd[ 1299.114380] iwlwifi 0000:03:00.0: Error sending SCAN_OFFLOAD_REQUEST_CMD: enqueue_hcmd failed: -5
[ 1299.114383] iwlwifi 0000:03:00.0: Scan failed! ret -5
[ 1300.133284] iwlwifi 0000:03:00.0: Failed to wake NIC for hcmd
[ 1300.133353] iwlwifi 0000:03:00.0: Error sending SCAN_OFFLOAD_REQUEST_CMD: enqueue_hcmd failed: -5
[ 1300.133358] iwlwifi 0000:03:00.0: Scan failed! ret -5
[ 1301.152410] iwlwifi 0000:03:00.0: Failed to wake NIC for hcmd
[ 1301.152457] iwlwifi 0000:03:00.0: Error sending SCAN_OFFLOAD_REQUEST_CMD: enqueue_hcmd failed: -5
[ 1301.152463] iwlwifi 0000:03:00.0: Scan failed! ret -5
[ 1302.171501] iwlwifi 0000:03:00.0: Failed to wake NIC for hcmd
[ 1302.171553] iwlwifi 0000:03:00.0: Error sending SCAN_OFFLOAD_REQUEST_CMD: enqueue_hcmd failed: -5
[ 1302.171557] iwlwifi 0000:03:00.0: Scan failed! ret -5
[ 1303.190536] iwlwifi 0000:03:00.0: Failed to wake NIC for hcmd
[ 1303.190584] iwlwifi 0000:03:00.0: Error sending SCAN_OFFLOAD_REQUEST_CMD: enqueue_hcmd failed: -5
[ 1303.190593] iwlwifi 0000:03:00.0: Scan failed! ret -5
[ 1304.209577] iwlwifi 0000:03:00.0: Failed to wake NIC for hcmd
[ 1304.209629] iwlwifi 0000:03:00.0: Error sending SCAN_OFFLOAD_REQUEST_CMD: enqueue_hcmd failed: -5
[ 1304.209633] iwlwifi 0000:03:00.0: Scan failed! ret -5
[ 1305.228539] iwlwifi 0000:03:00.0: Failed to wake NIC for hcmd
[ 1305.228594] iwlwifi 0000:03:00.0: Error sending SCAN_OFFLOAD_REQUEST_CMD: enqueue_hcmd failed: -5
[ 1305.228600] iwlwifi 0000:03:00.0: Scan failed! ret -5
[ 1306.247862] iwlwifi 0000:03:00.0: Failed to wake NIC for hcmd
[ 1306.247937] iwlwifi 0000:03:00.0: Error sending SCAN_OFFLOAD_REQUEST_CMD: enqueue_hcmd failed: -5
[ 1306.247942] iwlwifi 0000:03:00.0: Scan failed! ret -5
[ 1307.267067] iwlwifi 0000:03:00.0: Failed to wake NIC for hcmd
[ 1307.267113] iwlwifi 0000:03:00.0: Error sending SCAN_OFFLOAD_REQUEST_CMD: enqueue_hcmd failed: -5
[ 1307.267123] iwlwifi 0000:03:00.0: Scan failed! ret -5
[ 1308.285940] iwlwifi 0000:03:00.0: Failed to wake NIC for hcmd
[ 1308.285989] iwlwifi 0000:03:00.0: Error sending SCAN_OFFLOAD_REQUEST_CMD: enqueue_hcmd failed: -5
[ 1308.285993] iwlwifi 0000:03:00.0: Scan failed! ret -5
[ 1309.304266] iwlwifi 0000:03:00.0: Failed to wake NIC for hcmd
[ 1309.304364] iwlwifi 0000:03:00.0: Error sending SCAN_OFFLOAD_REQUEST_CMD: enqueue_hcmd failed: -5
[ 1309.304368] iwlwifi 0000:03:00.0: Scan failed! ret -5
[ 1310.323468] iwlwifi 0000:03:00.0: Failed to wake NIC for hcmd
[ 1310.323577] iwlwifi 0000:03:00.0: Error sending SCAN_OFFLOAD_REQUEST_CMD: enqueue_hcmd failed: -5
[ 1310.323582] iwlwifi 0000:03:00.0: Scan failed! ret -5
[ 1311.342526] iwlwifi 0000:03:00.0: Failed to wake NIC for hcmd
[ 1311.342577] iwlwifi 0000:03:00.0: Error sending SCAN_OFFLOAD_REQUEST_CMD: enqueue_hcmd failed: -5
[ 1311.342581] iwlwifi 0000:03:00.0: Scan failed! ret -5
[ 1312.361439] iwlwifi 0000:03:00.0: Failed to wake NIC for hcmd
[ 1312.361486] iwlwifi 0000:03:00.0: Error sending SCAN_OFFLOAD_REQUEST_CMD: enqueue_hcmd failed: -5
[ 1312.361489] iwlwifi 0000:03:00.0: Scan failed! ret -5
[ 1313.380153] iwlwifi 0000:03:00.0: Failed to wake NIC for hcmd
[ 1313.380215] iwlwifi 0000:03:00.0: Error sending SCAN_OFFLOAD_REQUEST_CMD: enqueue_hcmd failed: -5
[ 1313.380220] iwlwifi 0000:03:00.0: Scan failed! ret -5
[ 1314.399123] iwlwifi 0000:03:00.0: Failed to wake NIC for hcmd
[ 1314.399175] iwlwifi 0000:03:00.0: Error sending SCAN_OFFLOAD_REQUEST_CMD: enqueue_hcmd failed: -5
[ 1314.399179] iwlwifi 0000:03:00.0: Scan failed! ret -5
[ 1315.417966] iwlwifi 0000:03:00.0: Failed to wake NIC for hcmd
[ 1315.418016] iwlwifi 0000:03:00.0: Error sending SCAN_OFFLOAD_REQUEST_CMD: enqueue_hcmd failed: -5
[ 1315.418020] iwlwifi 0000:03:00.0: Scan failed! ret -5
[ 1316.436952] iwlwifi 0000:03:00.0: Failed to wake NIC for hcmd
[ 1316.437006] iwlwifi 0000:03:00.0: Error sending SCAN_OFFLOAD_REQUEST_CMD: enqueue_hcmd failed: -5
[ 1316.437011] iwlwifi 0000:03:00.0: Scan failed! ret -5
[ 1317.455981] iwlwifi 0000:03:00.0: Failed to wake NIC for hcmd
[ 1317.456027] iwlwifi 0000:03:00.0: Error sending SCAN_OFFLOAD_REQUEST_CMD: enqueue_hcmd failed: -5
[ 1317.456031] iwlwifi 0000:03:00.0: Scan failed! ret -5
[ 1318.475045] iwlwifi 0000:03:00.0: Failed to wake NIC for hcmd
[ 1318.475093] iwlwifi 0000:03:00.0: Error sending SCAN_OFFLOAD_REQUEST_CMD: enqueue_hcmd failed: -5
[ 1318.475098] iwlwifi 0000:03:00.0: Scan failed! ret -5
[ 1319.493562] iwlwifi 0000:03:00.0: Failed to wake NIC for hcmd
[ 1319.493610] iwlwifi 0000:03:00.0: Error sending SCAN_OFFLOAD_REQUEST_CMD: enqueue_hcmd failed: -5
[ 1319.493615] iwlwifi 0000:03:00.0: Scan failed! ret -5
[ 1320.512618] iwlwifi 0000:03:00.0: Failed to wake NIC for hcmd
[ 1320.512674] iwlwifi 0000:03:00.0: Error sending SCAN_OFFLOAD_REQUEST_CMD: enqueue_hcmd failed: -5
[ 1320.512680] iwlwifi 0000:03:00.0: Scan failed! ret -5
```

---

### Post by wildmanne39 on 2017-09-16
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by hamakei on 2017-09-16
Sorry...I wasn't aware that there was a CODE markup on this BB.

I don't know if your reference to "Wireless Script" was aimed at me or just part of your footer, but I installed and ran it anyway:

[http://paste.ubuntu.com/25551616/](http://paste.ubuntu.com/25551616/)

---

### Post by jeremy31 on 2017-09-17
See [https://ubuntuforums.org/showthread.php?t=2354328&p=13614520&#post13614520](https://ubuntuforums.org/showthread.php?t=2354328&p=13614520&#post13614520)
It seems that you have also edited /etc/NetworkManager/NetworkManager.conf and there is now a line that reads
```
;dns=dnsmasq
```
The file normally is
```
[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false
```

---

### Post by hamakei on 2017-09-17
I disabled dnsmasq some months ago...I don't remember the exact circumstances but I think it was something to do with Network Manager refusing to manage my network....but I'll re-enable it to see what happens...

The link you've posted seems to refer to not being able to connect to a particular wi-fi network. My problem is a little more general than that...after a random amount of time, the network stops responding entirely. I can't even bring up a list of SSIDs because everything says the device isn't ready, never mind try and connect to one...

---

### Post by jeremy31 on 2017-09-17
If you want to disable use a # to make the line a comment

---

### Post by wildmanne39 on 2017-09-17
There are many bug reports about this error:
```
Error sending SCAN_OFFLOAD_REQUEST_CMD: enqueue_hcmd failed: -5
```
This is just one of them:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1684213](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1684213)

I researched all of them last night but I did not find a resolution, it may help to change your encryption in your router to just wpa2 if you have that option and a fixed channel of 1,6 and 11 generally work better.

Go into network manager under the ipv6 tab and set it to ignore, then do:
```
sudo systemctl restart NetworkManager.service
```
In the bug reports people upgraded the kernel and firmware and still had the same issue, so you may want to add your name to the bug if it continues.

---

### Post by hamakei on 2017-09-17
Thank you for your reply, but my issue isn't "can't connect to a wireless access point". It's "wireless device stops responding". Neither NetworkManager nor wpasupplicant can communicate with the device, and just report a "device not ready" error. Changing the encryption on the router and/or disabling IPv6 won't make any difference as I can't even get the wireless device to respond and bring up a list of visible SSIDs.

The bug you linked to also seems different as the OP there reports that "even restarting doesn't fix it" whereas restarting DOES fix it for me...temporarily.

---

### Post by wildmanne39 on 2017-09-17
Research that error message and see if you can find a solution I missed and the things I recommended will make your connection work better when you are connected.

---

### Post by jeremy31 on 2017-09-17
Have you tried removing the wireless card and then reinstalling issue to see if the errors are caused by a dirty/bad connection between the card and slot?  I use an Intel 7260 in one laptop and have yet to see those errors

---

### Post by hamakei on 2017-09-17
> [COLOR=#000000]Research that error message and see if you can find a solution I missed and the things I recommended will make your connection work better when you are connected.[/COLOR][COLOR=#000000]

[/COLOR]I did research that error message...it's what originally brought me to this forum...unfortunately 99.9% of search results have nothing to do with this. And...I'm sorry but I don't see the point in fiddling with my access point when you even admit it's not related to this problem. When my wi-fi device is working, everything works perfectly. When the wi-fi device stops working, I can't connect to ANYTHING at all. So..what would changing the channel of my AP achieve? Surely if there was a problem with the settings on my AP then I would be thrown off the connection, but the wi-fi device would continue working? That's not what's happening here.

> [COLOR=#000000]Have you tried removing the wireless card and then reinstalling issue to see if the errors are caused by a dirty/bad connection between the card and slot? I use an Intel 7260 in one laptop and have yet to see those errors[/COLOR][COLOR=#000000]

[/COLOR]I don't have a wireless card - it's a device built in to the motherboard with an external aerial. And it's been working for about 2 years now without any errors until a few weeks ago.

---

### Post by hamakei on 2017-09-18
Hmm. It lasted almost 24 hours that time, which is a record.

If it makes a difference, I'm still running 16.04 LTS so am still on the 4.4 kernel releases. I kind of figured that sticking with LTS releases would avoid system-breaking updates... (if an update is what has caused this)

---

