---
title: "Wireless not working after suspend iwl3945 driver"
date: 2014-03-28
forum: Networking &amp; Wireless
---

### Post by chris198 on 2014-03-28
Okay everyone, I'm new to Ubuntu-- 

I have been searching and tried a number of things.  Nothing has resolved this.

My problem is pretty straight forward, when I suspend my laptop with Ubuntu 12.4.04 (just installed) my wireless becomes disabled, entirely... like it's not even there.

The nearest thread I've found to my problem is [http://ubuntuforums.org/showthread.php?t=2011612&highlight=wireless+suspend+iwl3945](http://ubuntuforums.org/showthread.php?t=2011612&highlight=wireless+suspend+iwl3945)

The poster there didn't resolve his problem and neither have I.  To speed things along below is the return for the commands suggested on that thread...  NOTE: this is while wireless is working.  I don't have wired internet available so any requests for command returns while the wireless is unavailable after suspension will take awhile to post given that a restart is required to regain wireless connection.

cat /etc/lsb-release; uname -a```
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.4 LTS"
Linux chris-GX620 3.11.0-15-generic #25~precise1-Ubuntu SMP Thu Jan 30 17:42:40 UTC 2014 i686 i686 i386 GNU/Linux

```

lspci -nnk | grep -iA2 net
```
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 01)
    Subsystem: Micro-Star International Co., Ltd. Device [1462:6510]
    Kernel driver in use: r8169
--
06:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4222] (rev 02)
    Subsystem: Intel Corporation PRO/Wireless 3945ABG Network Connection [8086:1000]
    Kernel driver in use: iwl3945
    Kernel modules: iwl3945

```






lsusb
```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


```

iwconfig
```
wlan0     IEEE 802.11abg  ESSID:"Lucky Dog"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:25:9C:3B:D6:BE   
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=63/70  Signal level=-47 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:283   Missed beacon:0

lo        no wireless extensions.

eth0      no wireless extensions.


```


rfkill list all
```
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


```

lsmod
```
Module                  Size  Used by
bnep                   19210  2 
rfcomm                 59026  0 
bluetooth             341971  10 bnep,rfcomm
parport_pc             32114  0 
ppdev                  17423  0 
vesafb                 13540  0 
snd_hda_codec_hdmi     40852  1 
nouveau               870273  3 
snd_hda_codec_realtek    50304  1 
snd_hda_intel          43326  3 
snd_hda_codec         169534  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
ttm                    76692  1 nouveau
snd_pcm                94597  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
drm_kms_helper         47306  1 nouveau
snd_rawmidi            25157  1 snd_seq_midi
drm                   247722  5 nouveau,ttm,drm_kms_helper
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                55716  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28930  2 snd_pcm,snd_seq
ir_lirc_codec          12869  0 
lirc_dev               19354  1 ir_lirc_codec
ir_rc6_decoder         12754  0 
ir_sanyo_decoder       12727  0 
ir_sony_decoder        12625  0 
ir_rc5_decoder         12622  0 
ir_nec_decoder         12787  0 
ir_mce_kbd_decoder     13151  0 
ir_jvc_decoder         12655  0 
snd_seq_device         14137  3 snd_seq_midi,snd_rawmidi,snd_seq
rc_rc6_mce             12454  0 
i2c_algo_bit           13316  1 nouveau
gpio_ich               13278  0 
psmouse                92648  0 
msi_wmi                13130  0 
snd                    61270  17 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_seq_midi,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
jmb38x_ms              18451  0 
sparse_keymap          13658  1 msi_wmi
soundcore              12600  1 snd
memstick               16051  1 jmb38x_ms
ene_ir                 28284  0 
serio_raw              13189  0 
snd_page_alloc         18398  2 snd_hda_intel,snd_pcm
mxm_wmi                12893  1 nouveau
arc4                   12509  2 
rc_core                26461  11 ir_lirc_codec,ir_rc6_decoder,ir_sanyo_decoder,ir_sony_decoder,ir_rc5_decoder,ir_nec_decoder,ir_mce_kbd_decoder,ir_jvc_decoder,rc_rc6_mce,ene_ir
wmi                    18744  3 nouveau,msi_wmi,mxm_wmi
lpc_ich                16987  0 
video                  19046  1 nouveau
mac_hid                13077  0 
iwl3945                64640  0 
iwlegacy               88342  1 iwl3945
mac80211              534884  2 iwl3945,iwlegacy
cfg80211              416271  3 iwl3945,iwlegacy,mac80211
lp                     13359  0 
parport                40930  3 parport_pc,ppdev,lp
firewire_ohci          36064  0 
firewire_core          62303  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
sdhci_pci              18588  0 
r8169                  62856  0 
sdhci                  37958  1 sdhci_pci
mii                    13693  1 r8169


```

All suggestions appreciated.

---

### Post by GigabyteProduction on 2014-03-28
The only solution i can think of is to restart the driver.
```
modprobe -r drivername
modprobe drivername
```
i am not sure if this is how it's intended to restart i driver but it's worth trying, and if it doesn't work maybe lookup restarting a driver and try it before it lockes up and then if it works, make it lock up and try it.

---

### Post by chris198 on 2014-03-29
thanks for the reply Gibabyte.  Unfortunately, that didn't work.  Below is the reply from terminal when I entered the comman with my driver name...

```
   chris@chris-GX620:~$ modprobe -r iwl3945 
FATAL: Error removing iwl3945 (/lib/modules/3.11.0-18-generic/kernel/drivers/net/wireless/iwlegacy/iwl3945.ko): Operation not permitted
```

I tried it prior to standby use, then after standby use-- just to see if it was different.  Got the same response in both senarios.

---

### Post by Toz on 2014-03-29
@chris198, you need root privileges to unload a kernel module. Try this procedure:

1. Unload the wireless kernel module:
```
sudo modprobe -r iwl3954
```
2. Suspend/resume the system.
3. Reload the kernel module:
```
sudo modprobe iwl3954
```


According to the thread you linked to, the poster was getting error messages. Are you getting the same:
```
dmesg | egrep 'iwl|firm|etork|wlan0'
```
...and also try:
```
cat /var/log/syslog | grep PM:
```


And finally, you might find some useful information in /var/log/pm-suspend.log. Run the following command:
```
pastebinit /var/log/pm-suspend.log
```
...and post back the link that is generated so that we can have a look at that log file. (If pastebinit isn't installed, you can install it via "sudo apt-get install pastebinit").

---

### Post by chili555 on 2014-03-29
My esteemed colleague means:```
*sudo* modprobe -r iwl3945
*sudo* modprobe iwl3945
```I'd also like to see:```
lsmod > after.txt
```Please run it after suspend when the wireless isn't working. Find the file after.txt in your user directory and paste it here.

---

### Post by chris198 on 2014-03-29
the sudo modprobe -r codes didn't alter a thing, even using the correct driver name :P

Here are the returns on the codes, this first batch I ran after waking did not recover wireless-- so that is while the problem is present.  Chili, I didn't see your request until after I rebooted and regained wireless, so I didn't run it while it was disabled.  I'll generate the problem again and edit my post to include it in the returns.

```
   chris@chris-GX620:~$ dmesg | egrep 'iwl|firm|etork|wlan0'  
 [    7.077596] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s  
 [    7.077600] iwl3945: Copyright(c) 2003-2011 Intel Corporation  
 [    7.131163] iwl3945 0000:06:00.0: Tunable channels: 11 802.11bg, 13 802.11a channels  
 [    7.131166] iwl3945 0000:06:00.0: Detected Intel Wireless WiFi Link 3945ABG  
 [    7.131227] iwl3945 0000:06:00.0: irq 47 for MSI/MSI-X  
 [    7.415836] ieee80211 phy0: Selected rate control algorithm 'iwl-3945-rs'  
 [   13.207693] iwl3945 0000:06:00.0: loaded firmware version 15.32.2.9  
 [   13.277490] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready  
 [   13.277752] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready  
 [   18.112541] wlan0: authenticate with 00:25:9c:3b:d6:be  
 [   18.116341] wlan0: send auth to 00:25:9c:3b:d6:be (try 1/3)  
 [   18.118117] wlan0: authenticated  
 [   18.118241] iwl3945 0000:06:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP  
 [   18.118246] iwl3945 0000:06:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP  
 [   18.120059] wlan0: associate with 00:25:9c:3b:d6:be (try 1/3)  
 [   18.122373] wlan0: RX AssocResp from 00:25:9c:3b:d6:be (capab=0x411 status=0 aid=4)  
 [   18.123688] wlan0: associated  
 [   18.123714] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready  
 [ 1310.948092] wlan0: deauthenticating from 00:25:9c:3b:d6:be by local choice (reason=3)  
 

 chris@chris-GX620:~$ cat /var/log/syslog | grep PM:  
 Mar 28 20:46:08 chris-GX620 kernel: [    0.000000] PM: Registered nosave memory: [mem 0x0009a000-0x0009ffff]  
 Mar 28 20:46:08 chris-GX620 kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000dffff]  
 Mar 28 20:46:08 chris-GX620 kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000e0000-0x000fffff]  
 Mar 28 20:46:08 chris-GX620 kernel: [    0.080216] PM: Registering ACPI NVS region [mem 0xbff9e000-0xbffdffff] (270336 bytes)  
 Mar 28 20:46:08 chris-GX620 kernel: [    0.642210] PM: Hibernation image not present or could not be loaded.  
 Mar 28 21:03:52 chris-GX620 kernel: [    0.000000] PM: Registered nosave memory: [mem 0x0009a000-0x0009ffff]  
 Mar 28 21:03:52 chris-GX620 kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000dffff]  
 Mar 28 21:03:52 chris-GX620 kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000e0000-0x000fffff]  
 Mar 28 21:03:52 chris-GX620 kernel: [    0.084217] PM: Registering ACPI NVS region [mem 0xbff9e000-0xbffdffff] (270336 bytes)  
 Mar 28 21:03:52 chris-GX620 kernel: [    0.639080] PM: Hibernation image not present or could not be loaded.  
 Mar 28 21:04:42 chris-GX620 kernel: [   56.794255] PM: Syncing filesystems ... done.  
 Mar 28 21:04:42 chris-GX620 kernel: [   57.006334] PM: Preparing system for mem sleep  
 Mar 28 21:04:54 chris-GX620 kernel: [   57.128698] PM: Entering mem sleep  
 Mar 28 21:04:54 chris-GX620 kernel: [   62.012154] PM: suspend of devices complete after 4883.226 msecs  
 Mar 28 21:04:54 chris-GX620 kernel: [   62.012453] PM: late suspend of devices complete after 0.295 msecs  
 Mar 28 21:04:54 chris-GX620 kernel: [   62.076158] PM: noirq suspend of devices complete after 63.702 msecs  
 Mar 28 21:04:54 chris-GX620 kernel: [   62.077563] PM: Saving platform NVS memory  
 Mar 28 21:04:54 chris-GX620 kernel: [   62.180209] PM: Restoring platform NVS memory  
 Mar 28 21:04:54 chris-GX620 kernel: [   62.424292] PM: noirq resume of devices complete after 229.477 msecs  
 Mar 28 21:04:54 chris-GX620 kernel: [   62.424431] PM: early resume of devices complete after 0.108 msecs  
 Mar 28 21:04:54 chris-GX620 kernel: [   63.436170] PM: Device 0000:07:00.0 failed to resume async: error -16  
 Mar 28 21:04:54 chris-GX620 kernel: [   65.538258] PM: resume of devices complete after 3113.824 msecs  
 Mar 28 21:04:54 chris-GX620 kernel: [   65.538813] PM: Finishing wakeup.  
 Mar 29 07:07:43 chris-GX620 kernel: [    0.000000] PM: Registered nosave memory: [mem 0x0009a000-0x0009ffff]  
 Mar 29 07:07:43 chris-GX620 kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000dffff]  
 Mar 29 07:07:43 chris-GX620 kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000e0000-0x000fffff]  
 Mar 29 07:07:43 chris-GX620 kernel: [    0.080217] PM: Registering ACPI NVS region [mem 0xbff9e000-0xbffdffff] (270336 bytes)  
 Mar 29 07:07:43 chris-GX620 kernel: [    0.644612] PM: Hibernation image not present or could not be loaded.  
 Mar 29 07:24:49 chris-GX620 kernel: [    0.000000] PM: Registered nosave memory: [mem 0x0009a000-0x0009ffff]  
 Mar 29 07:24:49 chris-GX620 kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000dffff]  
 Mar 29 07:24:49 chris-GX620 kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000e0000-0x000fffff]  
 Mar 29 07:24:49 chris-GX620 kernel: [    0.084206] PM: Registering ACPI NVS region [mem 0xbff9e000-0xbffdffff] (270336 bytes)  
 Mar 29 07:24:49 chris-GX620 kernel: [    0.621841] PM: Hibernation image not present or could not be loaded.  
 Mar 29 07:26:59 chris-GX620 kernel: [  131.919702] PM: Syncing filesystems ... done.  
 Mar 29 07:26:59 chris-GX620 kernel: [  132.055419] PM: Preparing system for mem sleep  
 Mar 29 07:26:59 chris-GX620 kernel: [  132.058443] PM: Entering mem sleep  
 Mar 29 07:26:59 chris-GX620 kernel: [  132.996190] PM: suspend of devices complete after 937.513 msecs  
 Mar 29 07:26:59 chris-GX620 kernel: [  132.996431] PM: late suspend of devices complete after 0.237 msecs  
 Mar 29 07:26:59 chris-GX620 kernel: [  133.060204] PM: noirq suspend of devices complete after 63.771 msecs  
 Mar 29 07:26:59 chris-GX620 kernel: [  133.061021] PM: Saving platform NVS memory  
 Mar 29 07:26:59 chris-GX620 kernel: [  133.164390] PM: Restoring platform NVS memory  
 Mar 29 07:26:59 chris-GX620 kernel: [  133.392331] PM: noirq resume of devices complete after 213.299 msecs  
 Mar 29 07:26:59 chris-GX620 kernel: [  133.392466] PM: early resume of devices complete after 0.103 msecs  
 Mar 29 07:26:59 chris-GX620 kernel: [  134.376179] PM: Device 0000:07:00.0 failed to resume async: error -16 
 Mar 29 07:26:59 chris-GX620 kernel: [  136.023560] PM: resume of devices complete after 2631.091 msecs  
 Mar 29 07:26:59 chris-GX620 kernel: [  136.024243] PM: Finishing wakeup.  
 Mar 29 07:31:43 chris-GX620 kernel: [    0.000000] PM: Registered nosave memory: [mem 0x0009a000-0x0009ffff]  
 Mar 29 07:31:43 chris-GX620 kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000dffff]  
 Mar 29 07:31:43 chris-GX620 kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000e0000-0x000fffff]  
 Mar 29 07:31:43 chris-GX620 kernel: [    0.088206] PM: Registering ACPI NVS region [mem 0xbff9e000-0xbffdffff] (270336 bytes)  
 Mar 29 07:31:43 chris-GX620 kernel: [    0.630203] PM: Hibernation image not present or could not be loaded.  
 Mar 29 07:33:55 chris-GX620 kernel: [  128.686565] PM: Syncing filesystems ... done.  
 Mar 29 07:33:55 chris-GX620 kernel: [  128.887326] PM: Preparing system for mem sleep  
 Mar 29 07:33:55 chris-GX620 kernel: [  128.890254] PM: Entering mem sleep  
 Mar 29 07:33:55 chris-GX620 kernel: [  129.808169] PM: suspend of devices complete after 917.682 msecs  
 Mar 29 07:33:55 chris-GX620 kernel: [  129.808419] PM: late suspend of devices complete after 0.245 msecs  
 Mar 29 07:33:55 chris-GX620 kernel: [  129.872159] PM: noirq suspend of devices complete after 63.738 msecs  
 Mar 29 07:33:55 chris-GX620 kernel: [  129.872977] PM: Saving platform NVS memory  
 Mar 29 07:33:55 chris-GX620 kernel: [  129.976180] PM: Restoring platform NVS memory  
 Mar 29 07:33:55 chris-GX620 kernel: [  130.204283] PM: noirq resume of devices complete after 213.488 msecs  
 Mar 29 07:33:55 chris-GX620 kernel: [  130.204438] PM: early resume of devices complete after 0.103 msecs  
 Mar 29 07:33:55 chris-GX620 kernel: [  131.204116] PM: Device 0000:07:00.0 failed to resume async: error -16 
 Mar 29 07:33:55 chris-GX620 kernel: [  133.290940] PM: resume of devices complete after 3086.499 msecs  
 Mar 29 07:33:55 chris-GX620 kernel: [  133.291575] PM: Finishing wakeup.  
 Mar 29 07:35:41 chris-GX620 kernel: [    0.000000] PM: Registered nosave memory: [mem 0x0009a000-0x0009ffff]  
 Mar 29 07:35:41 chris-GX620 kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000dffff]  
 Mar 29 07:35:41 chris-GX620 kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000e0000-0x000fffff]  
 Mar 29 07:35:41 chris-GX620 kernel: [    0.088206] PM: Registering ACPI NVS region [mem 0xbff9e000-0xbffdffff] (270336 bytes)  
 Mar 29 07:35:41 chris-GX620 kernel: [    0.654973] PM: Hibernation image not present or could not be loaded.  
 Mar 29 12:34:53 chris-GX620 kernel: [    0.000000] PM: Registered nosave memory: [mem 0x0009a000-0x0009ffff]  
 Mar 29 12:34:53 chris-GX620 kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000dffff]  
 Mar 29 12:34:53 chris-GX620 kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000e0000-0x000fffff]  
 Mar 29 12:34:53 chris-GX620 kernel: [    0.084206] PM: Registering ACPI NVS region [mem 0xbff9e000-0xbffdffff] (270336 bytes)  
 Mar 29 12:34:53 chris-GX620 kernel: [    0.650204] PM: Hibernation image not present or could not be loaded.  
 Mar 29 20:28:40 chris-GX620 kernel: [    0.000000] PM: Registered nosave memory: [mem 0x0009a000-0x0009ffff]  
 Mar 29 20:28:40 chris-GX620 kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000dffff]  
 Mar 29 20:28:40 chris-GX620 kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000e0000-0x000fffff]  
 Mar 29 20:28:40 chris-GX620 kernel: [    0.084205] PM: Registering ACPI NVS region [mem 0xbff9e000-0xbffdffff] (270336 bytes)  
 Mar 29 20:28:40 chris-GX620 kernel: [    0.646306] PM: Hibernation image not present or could not be loaded.  
 Mar 29 20:50:45 chris-GX620 kernel: [ 1325.126689] PM: Syncing filesystems ... done.  
 Mar 29 20:50:45 chris-GX620 kernel: [ 1325.442317] PM: Preparing system for mem sleep  
 Mar 29 20:50:45 chris-GX620 kernel: [ 1325.445312] PM: Entering mem sleep  
 Mar 29 20:50:45 chris-GX620 kernel: [ 1326.380150] PM: suspend of devices complete after 934.612 msecs  
 Mar 29 20:50:45 chris-GX620 kernel: [ 1326.380415] PM: late suspend of devices complete after 0.261 msecs  
 Mar 29 20:50:45 chris-GX620 kernel: [ 1326.428159] PM: noirq suspend of devices complete after 47.743 msecs 
 Mar 29 20:50:45 chris-GX620 kernel: [ 1326.428975] PM: Saving platform NVS memory  
 Mar 29 20:50:45 chris-GX620 kernel: [ 1326.532199] PM: Restoring platform NVS memory  
 Mar 29 20:50:45 chris-GX620 kernel: [ 1326.744282] PM: noirq resume of devices complete after 197.452 msecs 
 Mar 29 20:50:45 chris-GX620 kernel: [ 1326.744416] PM: early resume of devices complete after 0.102 msecs  
 Mar 29 20:50:45 chris-GX620 kernel: [ 1327.732174] PM: Device 0000:07:00.0 failed to resume async: error -16  
 Mar 29 20:50:45 chris-GX620 kernel: [ 1329.889811] PM: resume of devices complete after 3145.391 msecs  
 Mar 29 20:50:45 chris-GX620 kernel: [ 1329.890403] PM: Finishing wakeup.
 

 chris@chris-GX620:~$ pastebinit /var/log/pm-suspend.log  
 Traceback (most recent call last):  
   File "/usr/bin/pastebinit", line 339, in <module>  
     page = url_opener.open(website, params) #Send the informations and be redirected to the final page  
   File "/usr/lib/python2.7/urllib.py", line 209, in open  
     return getattr(self, name)(url, data)  
   File "/usr/lib/python2.7/urllib.py", line 344, in open_http  
     h.endheaders(data)  
   File "/usr/lib/python2.7/httplib.py", line 954, in endheaders  
     self._send_output(message_body)  
   File "/usr/lib/python2.7/httplib.py", line 814, in _send_output  
     self.send(msg)  
   File "/usr/lib/python2.7/httplib.py", line 776, in send  
     self.connect()  
   File "/usr/lib/python2.7/httplib.py", line 757, in connect  
     self.timeout, self.source_address)  
   File "/usr/lib/python2.7/socket.py", line 553, in create_connection  
     for res in getaddrinfo(host, port, 0, SOCK_STREAM):  
 IOError: [Errno socket error] [Errno -2] Name or service not known  


```

This batch is with the system functioning normally...

```
chris@chris-GX620:~$ dmesg | egrep 'iwl|firm|etork|wlan0'
[    6.705689] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
[    6.705693] iwl3945: Copyright(c) 2003-2011 Intel Corporation
[    6.759358] iwl3945 0000:06:00.0: Tunable channels: 11 802.11bg, 13 802.11a channels
[    6.759362] iwl3945 0000:06:00.0: Detected Intel Wireless WiFi Link 3945ABG
[    6.759425] iwl3945 0000:06:00.0: irq 47 for MSI/MSI-X
[    6.982924] ieee80211 phy0: Selected rate control algorithm 'iwl-3945-rs'
[   13.009767] iwl3945 0000:06:00.0: loaded firmware version 15.32.2.9
[   13.077126] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   13.077430] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   18.040538] wlan0: authenticate with 00:25:9c:3b:d6:be
[   18.044132] wlan0: send auth to 00:25:9c:3b:d6:be (try 1/3)
[   18.046038] wlan0: authenticated
[   18.046115] iwl3945 0000:06:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   18.046118] iwl3945 0000:06:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   18.048034] wlan0: associate with 00:25:9c:3b:d6:be (try 1/3)
[   18.050339] wlan0: RX AssocResp from 00:25:9c:3b:d6:be (capab=0x411 status=0 aid=4)
[   18.051658] wlan0: associated
[   18.051677] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
chris@chris-GX620:~$ 
chris@chris-GX620:~$ 
chris@chris-GX620:~$ cat /var/log/syslog | grep PM:
Mar 28 20:46:08 chris-GX620 kernel: [    0.000000] PM: Registered nosave memory: [mem 0x0009a000-0x0009ffff]
Mar 28 20:46:08 chris-GX620 kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000dffff]
Mar 28 20:46:08 chris-GX620 kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000e0000-0x000fffff]
Mar 28 20:46:08 chris-GX620 kernel: [    0.080216] PM: Registering ACPI NVS region [mem 0xbff9e000-0xbffdffff] (270336 bytes)
Mar 28 20:46:08 chris-GX620 kernel: [    0.642210] PM: Hibernation image not present or could not be loaded.
Mar 28 21:03:52 chris-GX620 kernel: [    0.000000] PM: Registered nosave memory: [mem 0x0009a000-0x0009ffff]
Mar 28 21:03:52 chris-GX620 kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000dffff]
Mar 28 21:03:52 chris-GX620 kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000e0000-0x000fffff]
Mar 28 21:03:52 chris-GX620 kernel: [    0.084217] PM: Registering ACPI NVS region [mem 0xbff9e000-0xbffdffff] (270336 bytes)
Mar 28 21:03:52 chris-GX620 kernel: [    0.639080] PM: Hibernation image not present or could not be loaded.
Mar 28 21:04:42 chris-GX620 kernel: [   56.794255] PM: Syncing filesystems ... done.
Mar 28 21:04:42 chris-GX620 kernel: [   57.006334] PM: Preparing system for mem sleep
Mar 28 21:04:54 chris-GX620 kernel: [   57.128698] PM: Entering mem sleep
Mar 28 21:04:54 chris-GX620 kernel: [   62.012154] PM: suspend of devices complete after 4883.226 msecs
Mar 28 21:04:54 chris-GX620 kernel: [   62.012453] PM: late suspend of devices complete after 0.295 msecs
Mar 28 21:04:54 chris-GX620 kernel: [   62.076158] PM: noirq suspend of devices complete after 63.702 msecs
Mar 28 21:04:54 chris-GX620 kernel: [   62.077563] PM: Saving platform NVS memory
Mar 28 21:04:54 chris-GX620 kernel: [   62.180209] PM: Restoring platform NVS memory
Mar 28 21:04:54 chris-GX620 kernel: [   62.424292] PM: noirq resume of devices complete after 229.477 msecs
Mar 28 21:04:54 chris-GX620 kernel: [   62.424431] PM: early resume of devices complete after 0.108 msecs
Mar 28 21:04:54 chris-GX620 kernel: [   63.436170] PM: Device 0000:07:00.0 failed to resume async: error -16
Mar 28 21:04:54 chris-GX620 kernel: [   65.538258] PM: resume of devices complete after 3113.824 msecs
Mar 28 21:04:54 chris-GX620 kernel: [   65.538813] PM: Finishing wakeup.
Mar 29 07:07:43 chris-GX620 kernel: [    0.000000] PM: Registered nosave memory: [mem 0x0009a000-0x0009ffff]
Mar 29 07:07:43 chris-GX620 kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000dffff]
Mar 29 07:07:43 chris-GX620 kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000e0000-0x000fffff]
Mar 29 07:07:43 chris-GX620 kernel: [    0.080217] PM: Registering ACPI NVS region [mem 0xbff9e000-0xbffdffff] (270336 bytes)
Mar 29 07:07:43 chris-GX620 kernel: [    0.644612] PM: Hibernation image not present or could not be loaded.
Mar 29 07:24:49 chris-GX620 kernel: [    0.000000] PM: Registered nosave memory: [mem 0x0009a000-0x0009ffff]
Mar 29 07:24:49 chris-GX620 kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000dffff]
Mar 29 07:24:49 chris-GX620 kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000e0000-0x000fffff]
Mar 29 07:24:49 chris-GX620 kernel: [    0.084206] PM: Registering ACPI NVS region [mem 0xbff9e000-0xbffdffff] (270336 bytes)
Mar 29 07:24:49 chris-GX620 kernel: [    0.621841] PM: Hibernation image not present or could not be loaded.
Mar 29 07:26:59 chris-GX620 kernel: [  131.919702] PM: Syncing filesystems ... done.
Mar 29 07:26:59 chris-GX620 kernel: [  132.055419] PM: Preparing system for mem sleep
Mar 29 07:26:59 chris-GX620 kernel: [  132.058443] PM: Entering mem sleep
Mar 29 07:26:59 chris-GX620 kernel: [  132.996190] PM: suspend of devices complete after 937.513 msecs
Mar 29 07:26:59 chris-GX620 kernel: [  132.996431] PM: late suspend of devices complete after 0.237 msecs
Mar 29 07:26:59 chris-GX620 kernel: [  133.060204] PM: noirq suspend of devices complete after 63.771 msecs
Mar 29 07:26:59 chris-GX620 kernel: [  133.061021] PM: Saving platform NVS memory
Mar 29 07:26:59 chris-GX620 kernel: [  133.164390] PM: Restoring platform NVS memory
Mar 29 07:26:59 chris-GX620 kernel: [  133.392331] PM: noirq resume of devices complete after 213.299 msecs
Mar 29 07:26:59 chris-GX620 kernel: [  133.392466] PM: early resume of devices complete after 0.103 msecs
Mar 29 07:26:59 chris-GX620 kernel: [  134.376179] PM: Device 0000:07:00.0 failed to resume async: error -16
Mar 29 07:26:59 chris-GX620 kernel: [  136.023560] PM: resume of devices complete after 2631.091 msecs
Mar 29 07:26:59 chris-GX620 kernel: [  136.024243] PM: Finishing wakeup.
Mar 29 07:31:43 chris-GX620 kernel: [    0.000000] PM: Registered nosave memory: [mem 0x0009a000-0x0009ffff]
Mar 29 07:31:43 chris-GX620 kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000dffff]
Mar 29 07:31:43 chris-GX620 kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000e0000-0x000fffff]
Mar 29 07:31:43 chris-GX620 kernel: [    0.088206] PM: Registering ACPI NVS region [mem 0xbff9e000-0xbffdffff] (270336 bytes)
Mar 29 07:31:43 chris-GX620 kernel: [    0.630203] PM: Hibernation image not present or could not be loaded.
Mar 29 07:33:55 chris-GX620 kernel: [  128.686565] PM: Syncing filesystems ... done.
Mar 29 07:33:55 chris-GX620 kernel: [  128.887326] PM: Preparing system for mem sleep
Mar 29 07:33:55 chris-GX620 kernel: [  128.890254] PM: Entering mem sleep
Mar 29 07:33:55 chris-GX620 kernel: [  129.808169] PM: suspend of devices complete after 917.682 msecs
Mar 29 07:33:55 chris-GX620 kernel: [  129.808419] PM: late suspend of devices complete after 0.245 msecs
Mar 29 07:33:55 chris-GX620 kernel: [  129.872159] PM: noirq suspend of devices complete after 63.738 msecs
Mar 29 07:33:55 chris-GX620 kernel: [  129.872977] PM: Saving platform NVS memory
Mar 29 07:33:55 chris-GX620 kernel: [  129.976180] PM: Restoring platform NVS memory
Mar 29 07:33:55 chris-GX620 kernel: [  130.204283] PM: noirq resume of devices complete after 213.488 msecs
Mar 29 07:33:55 chris-GX620 kernel: [  130.204438] PM: early resume of devices complete after 0.103 msecs
Mar 29 07:33:55 chris-GX620 kernel: [  131.204116] PM: Device 0000:07:00.0 failed to resume async: error -16
Mar 29 07:33:55 chris-GX620 kernel: [  133.290940] PM: resume of devices complete after 3086.499 msecs
Mar 29 07:33:55 chris-GX620 kernel: [  133.291575] PM: Finishing wakeup.
Mar 29 07:35:41 chris-GX620 kernel: [    0.000000] PM: Registered nosave memory: [mem 0x0009a000-0x0009ffff]
Mar 29 07:35:41 chris-GX620 kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000dffff]
Mar 29 07:35:41 chris-GX620 kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000e0000-0x000fffff]
Mar 29 07:35:41 chris-GX620 kernel: [    0.088206] PM: Registering ACPI NVS region [mem 0xbff9e000-0xbffdffff] (270336 bytes)
Mar 29 07:35:41 chris-GX620 kernel: [    0.654973] PM: Hibernation image not present or could not be loaded.
Mar 29 12:34:53 chris-GX620 kernel: [    0.000000] PM: Registered nosave memory: [mem 0x0009a000-0x0009ffff]
Mar 29 12:34:53 chris-GX620 kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000dffff]
Mar 29 12:34:53 chris-GX620 kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000e0000-0x000fffff]
Mar 29 12:34:53 chris-GX620 kernel: [    0.084206] PM: Registering ACPI NVS region [mem 0xbff9e000-0xbffdffff] (270336 bytes)
Mar 29 12:34:53 chris-GX620 kernel: [    0.650204] PM: Hibernation image not present or could not be loaded.
Mar 29 20:28:40 chris-GX620 kernel: [    0.000000] PM: Registered nosave memory: [mem 0x0009a000-0x0009ffff]
Mar 29 20:28:40 chris-GX620 kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000dffff]
Mar 29 20:28:40 chris-GX620 kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000e0000-0x000fffff]
Mar 29 20:28:40 chris-GX620 kernel: [    0.084205] PM: Registering ACPI NVS region [mem 0xbff9e000-0xbffdffff] (270336 bytes)
Mar 29 20:28:40 chris-GX620 kernel: [    0.646306] PM: Hibernation image not present or could not be loaded.
Mar 29 20:50:45 chris-GX620 kernel: [ 1325.126689] PM: Syncing filesystems ... done.
Mar 29 20:50:45 chris-GX620 kernel: [ 1325.442317] PM: Preparing system for mem sleep
Mar 29 20:50:45 chris-GX620 kernel: [ 1325.445312] PM: Entering mem sleep
Mar 29 20:50:45 chris-GX620 kernel: [ 1326.380150] PM: suspend of devices complete after 934.612 msecs
Mar 29 20:50:45 chris-GX620 kernel: [ 1326.380415] PM: late suspend of devices complete after 0.261 msecs
Mar 29 20:50:45 chris-GX620 kernel: [ 1326.428159] PM: noirq suspend of devices complete after 47.743 msecs
Mar 29 20:50:45 chris-GX620 kernel: [ 1326.428975] PM: Saving platform NVS memory
Mar 29 20:50:45 chris-GX620 kernel: [ 1326.532199] PM: Restoring platform NVS memory
Mar 29 20:50:45 chris-GX620 kernel: [ 1326.744282] PM: noirq resume of devices complete after 197.452 msecs
Mar 29 20:50:45 chris-GX620 kernel: [ 1326.744416] PM: early resume of devices complete after 0.102 msecs
Mar 29 20:50:45 chris-GX620 kernel: [ 1327.732174] PM: Device 0000:07:00.0 failed to resume async: error -16
Mar 29 20:50:45 chris-GX620 kernel: [ 1329.889811] PM: resume of devices complete after 3145.391 msecs
Mar 29 20:50:45 chris-GX620 kernel: [ 1329.890403] PM: Finishing wakeup.
Mar 29 20:55:30 chris-GX620 kernel: [    0.000000] PM: Registered nosave memory: [mem 0x0009a000-0x0009ffff]
Mar 29 20:55:30 chris-GX620 kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000dffff]
Mar 29 20:55:30 chris-GX620 kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000e0000-0x000fffff]
Mar 29 20:55:30 chris-GX620 kernel: [    0.080206] PM: Registering ACPI NVS region [mem 0xbff9e000-0xbffdffff] (270336 bytes)
Mar 29 20:55:30 chris-GX620 kernel: [    0.622209] PM: Hibernation image not present or could not be loaded.
Mar 29 20:59:06 chris-GX620 kernel: [  213.912826] PM: Syncing filesystems ... done.
Mar 29 20:59:06 chris-GX620 kernel: [  214.054775] PM: Preparing system for mem sleep
Mar 29 20:59:06 chris-GX620 kernel: [  214.059276] PM: Entering mem sleep
Mar 29 20:59:06 chris-GX620 kernel: [  214.980191] PM: suspend of devices complete after 920.691 msecs
Mar 29 20:59:06 chris-GX620 kernel: [  214.980434] PM: late suspend of devices complete after 0.239 msecs
Mar 29 20:59:06 chris-GX620 kernel: [  215.028166] PM: noirq suspend of devices complete after 47.730 msecs
Mar 29 20:59:06 chris-GX620 kernel: [  215.028985] PM: Saving platform NVS memory
Mar 29 20:59:06 chris-GX620 kernel: [  215.132213] PM: Restoring platform NVS memory
Mar 29 20:59:06 chris-GX620 kernel: [  215.344288] PM: noirq resume of devices complete after 197.460 msecs
Mar 29 20:59:06 chris-GX620 kernel: [  215.344441] PM: early resume of devices complete after 0.102 msecs
Mar 29 20:59:06 chris-GX620 kernel: [  216.340231] PM: Device 0000:07:00.0 failed to resume async: error -16
Mar 29 20:59:06 chris-GX620 kernel: [  218.494844] PM: resume of devices complete after 3150.399 msecs
Mar 29 20:59:06 chris-GX620 kernel: [  218.495424] PM: Finishing wakeup.
Mar 29 21:00:06 chris-GX620 kernel: [    0.000000] PM: Registered nosave memory: [mem 0x0009a000-0x0009ffff]
Mar 29 21:00:06 chris-GX620 kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000dffff]
Mar 29 21:00:06 chris-GX620 kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000e0000-0x000fffff]
Mar 29 21:00:06 chris-GX620 kernel: [    0.084206] PM: Registering ACPI NVS region [mem 0xbff9e000-0xbffdffff] (270336 bytes)
Mar 29 21:00:06 chris-GX620 kernel: [    0.623842] PM: Hibernation image not present or could not be loaded.
chris@chris-GX620:~$ 
chris@chris-GX620:~$ 
chris@chris-GX620:~$ pastebinit /var/log/pm-suspend.log
http://paste.ubuntu.com/7177290/


```

The after.txt
```
Module                  Size  Used by
bnep                   19210  2 
rfcomm                 59026  0 
bluetooth             341971  10 bnep,rfcomm
parport_pc             32114  0 
ppdev                  17423  0 
nvidia               9589026  42 
snd_hda_codec_hdmi     40881  1 
snd_hda_codec_realtek    50931  1 
snd_hda_intel          43326  3 
arc4                   12509  2 
snd_hda_codec         169608  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
iwl3945                64640  0 
snd_pcm                94597  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
iwlegacy               88342  1 iwl3945
snd_seq_midi           13132  0 
snd_rawmidi            25157  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                55716  2 snd_seq_midi,snd_seq_midi_event
mac80211              534922  2 iwl3945,iwlegacy
snd_timer              28930  2 snd_pcm,snd_seq
snd_seq_device         14137  3 snd_seq_midi,snd_rawmidi,snd_seq
ir_lirc_codec          12869  0 
lirc_dev               19354  1 ir_lirc_codec
ir_mce_kbd_decoder     13151  0 
ir_sanyo_decoder       12727  0 
ir_nec_decoder         12787  0 
ir_jvc_decoder         12655  0 
ir_rc6_decoder         12754  0 
ir_sony_decoder        12625  0 
ir_rc5_decoder         12622  0 
snd                    61270  17 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_seq_midi,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
rc_rc6_mce             12454  0 
soundcore              12600  1 snd
gpio_ich               13278  0 
cfg80211              416271  3 iwl3945,iwlegacy,mac80211
snd_page_alloc         18398  2 snd_hda_intel,snd_pcm
drm                   247722  3 nvidia
jmb38x_ms              18451  0 
ene_ir                 28284  0 
psmouse                92648  0 
msi_wmi                13130  0 
rc_core                26461  11 ir_lirc_codec,ir_mce_kbd_decoder,ir_sanyo_decoder,ir_nec_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_sony_decoder,ir_rc5_decoder,rc_rc6_mce,ene_ir
memstick               16051  1 jmb38x_ms
serio_raw              13189  0 
sparse_keymap          13658  1 msi_wmi
lpc_ich                16987  0 
video                  19046  0 
mxm_wmi                12893  0 
mac_hid                13077  0 
wmi                    18744  2 msi_wmi,mxm_wmi
lp                     13359  0 
parport                40930  3 parport_pc,ppdev,lp
sdhci_pci              18530  0 
sdhci                  37958  1 sdhci_pci
firewire_ohci          36064  0 
firewire_core          62303  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
r8169                  62856  0 
mii                    13693  1 r8169
```

thanks for all the help guys!

---

### Post by Toz on 2014-03-30
> Mar 28 21:04:54 chris-GX620 kernel: [   63.436170] PM: Device 0000:07:00.0 failed to resume async: error -16  
What device is at address 07:00.0? "lspci" should help to identify it.

---

### Post by chris198 on 2014-03-31
"07:00.0 FireWire (IEEE 1394): JMicron Technology Corp. IEEE 1394 Host Controller"

Wireless controller is 06:00.0

```
chris@chris-GX620:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:1a.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801IBM/IEM (ICH9M/ICH9M-E) 2 port SATA Controller [IDE mode] (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
00:1f.5 IDE interface: Intel Corporation 82801IBM/IEM (ICH9M/ICH9M-E) 2 port SATA Controller [IDE mode] (rev 03)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 01)
06:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
07:00.0 FireWire (IEEE 1394): JMicron Technology Corp. IEEE 1394 Host Controller
07:00.1 System peripheral: JMicron Technology Corp. SD/MMC Host Controller
07:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller
07:00.3 System peripheral: JMicron Technology Corp. MS Host Controller
07:00.4 System peripheral: JMicron Technology Corp. xD Host Controller
08:00.0 VGA compatible controller: NVIDIA Corporation G94M [GeForce GTS 160M] (rev a1)


```

---

### Post by Toz on 2014-04-01
Interesting. Unfortunately, I don't see how the SD card would have an affect on wireless not re-starting, so I think its a false alarm. Do either of the following commands help restore wireless:

```
sudo nmcli nm sleep false
```
```
sudo killall NetworkManager
```

[Source]("https://bugs.launchpad.net/ubuntu/+source/systemd-shim/+bug/1184262")

---

### Post by chris198 on 2014-04-01
Here's the response.

```
   chris@chris-GX620:~$ sudo nmcli nm sleep false
 [sudo] password for chris:  
 Error in sleep: Already awake
 chris@chris-GX620:~$  
 chris@chris-GX620:~$  
 chris@chris-GX620:~$  
 chris@chris-GX620:~$ sudo killall NetworkManager
 chris@chris-GX620:~$  
 
```

The first did nothing noticeable, the the second made the wireless seen by the system, but it won't connect to any networks... I'd call it progress.

---

### Post by Toz on 2014-04-01
How about:
```
sudo restart network-manager
```

If that doesn't work, try combining them like:
```
sudo stop network-manager
sudo service networking stop
sudo modprobe -r iwl3945
sudo modprobe iwl3945
sudo service networking start
sudo start network-manager
```

---

### Post by chris198 on 2014-04-02
Same result as before, OS recognizes the wirless card is present but I'm unable to connect or see any networks.  Below is the entry and reply on the commands.

```
   chris@chris-GX620:~$ sudo restart network-manager  
 [sudo] password for chris:  
 network-manager start/running, process 3089  
 chris@chris-GX620:~$ sudo stop network-manager  
 network-manager stop/waiting  
 chris@chris-GX620:~$ sudo service networking stop  
 stop: Unknown instance:  
 chris@chris-GX620:~$ sudo modprobe -r iwl3945  
 chris@chris-GX620:~$ sudo modprobe iwl3945  
 chris@chris-GX620:~$ sudo service networking start  
 networking stop/waiting  
 chris@chris-GX620:~$ sudo start network-manager  
 network-manager start/running, process 3122  
 chris@chris-GX620:~$  


```

---

### Post by chris198 on 2014-04-14
bump

---

### Post by Toz on 2014-04-14
Are you using any modprobe options to load the wireless card on boot? It would be in a config file in /etc/modprobe.d. Try:
```
sudo fgrep -ri iwl /etc/modprobe.d/*
```

---

### Post by chris198 on 2014-04-16
The code returned nothing:

[HTML]chris@chris-GX620:~$ sudo fgrep -ri iwl /etc/modprobe.d/*
[sudo] password for chris: 
chris@chris-GX620:~$ 
[/HTML]

Is the conlfig file located somewhere that I can find it via GUI?

---

### Post by Toz on 2014-04-17
Sorry but I'm not sure why its not working. I'll step aside and let someone else have a go at it.

---

