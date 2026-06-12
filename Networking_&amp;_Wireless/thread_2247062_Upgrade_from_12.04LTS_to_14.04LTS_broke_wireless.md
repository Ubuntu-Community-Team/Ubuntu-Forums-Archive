---
title: "Upgrade from 12.04LTS to 14.04LTS broke wireless"
date: 2014-10-05
forum: Networking &amp; Wireless
---

### Post by daniel199 on 2014-10-05
I just upgraded from 12.04LTS 64-bit to 14.04LTS 64-bit and now my wireless no longer works. Wired connection still works and so does the wireless connection in my Windows 7 install on the same disc. I have read several similar posts but can not find enough similarity to my circumstances to find a path to resolution.

Ubuntu can see wireless networks including mine. It tries to connect and eventually fails. Also, sometimes the signal strength from my wireless router is *very* weak even though I am sitting right next to the router, but this is not always the case.

I have a Sager [FONT=arial]NP8130. Here is the wireless portion of the output from "[/FONT]sudo lshw -C network[FONT=arial]":

[/FONT]```

*-network
       description: Wireless interface
       product: RTL8188CE 802.11b/g/n WiFi Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wlan0
       version: 01
       serial: 00:1c:7b:75:04:3a
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192ce driverversion=3.13.0-36-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:18 ioport:c000(size=256) memory:f6200000-f6203fff

```[FONT=arial]

Notice that there is no ip listed under "configuration" and "link=no". I am sorry if this have been answered elsewhere but I have searched for hours and have not found the exact symptoms I am experiencing solved anywhere else. I have several other devices that rely on wireless so any router changes will have to play nice with them.

Many thanks[/FONT]

---

### Post by slooksterpsv on 2014-10-05
1) How many devices connect to your wireless router? Why I ask is because we have: 4 laptops, 3 tablets, 4 phones, 1 tv, 2 consoles, and.... I think that's it. Now I notice sometimes when I'm using a *buntu variant it has difficulty connect - strength can be good or bad, it varies, so what I do is I set my IP address to be static for the devices that have difficulty connecting. My IP is as follows (yours may differ)
IP: 192.168.2.107
Subnet: 255.255.255.0
Gateway: 192.168.2.1
DNS: 8.8.4.4, 4.4.4.4  --- I love Google's DNS

2) It's showing the device is found so it may be an interference issue overall. You could try purging the linux-firmware and reinstalling it to see if that helps (most likely won't, but that's another resort to try).

3) This isn't very useful as I don't think it affects Ubuntu, but for me it has had some good results. Open terminal and run:
sudo iw dev wlan0 set power_save off

That should disable the power saving features. This helps me, but others claim it doesn't do anything as Ubuntu handles all that itself, for me it works.

4) LAST RESORT (with breakage possible) You can try to compile and install the drivers yourself. I was able to do it with 12.04 and 13.10. 14.04 it broke my wireless to where I couldn't fix it - you may have better luck. Search for the forums for compile 8192 driver it should come up like that. The 8192 driver compilation package includes mine 8188EE, as well as 8188CE, 8192 (various) 80xx, etc.

---

### Post by varunendra on 2014-10-06
Welcome to the forums Daniel!

Please follow the instructions in this post to download and run 'wireless_script' (alternative version) and post back the report it generates : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Use Code Tags" link in my signature.

---

### Post by Ni Soros on 2014-10-27
I am also having trouble with the same wireless card on Ubuntu 14.10. I can see my wifi network, but cannot connect. 

Some info: 

```
uname -a
Linux ni-soros-ThinkPad-X220 3.16.0-23-generic #31-Ubuntu SMP Tue Oct 21 17:56:17 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

lspci -nnk | grep -iA2 net
00:19.0 Ethernet controller [0200]: Intel Corporation 82579LM Gigabit Network Connection [8086:1502] (rev 04)
    Subsystem: Lenovo Device [17aa:21ce]
    Kernel driver in use: e1000e
--
03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8176] (rev 01)
    Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:8195]
    Kernel driver in use: rtl8192ce

lsusb
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

lsmod
Module                  Size  Used by
ctr                    13049  0 
ccm                    17731  0 
bnep                   19543  2 
rfcomm                 69509  0 
bluetooth             446190  10 bnep,rfcomm
6lowpan_iphc           18702  1 bluetooth
arc4                   12608  2 
snd_seq_midi           13564  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30876  1 snd_seq_midi
intel_rapl             18783  0 
x86_pkg_temp_thermal    14205  0 
intel_powerclamp       18786  0 
coretemp               13441  0 
rtl8192ce              53509  0 
rtl_pci                26674  1 rtl8192ce
snd_seq                67224  2 snd_seq_midi_event,snd_seq_midi
rtlwifi                64237  2 rtl_pci,rtl8192ce
rtl8192c_common        53170  1 rtl8192ce
mac80211              660592  3 rtl_pci,rtlwifi,rtl8192ce
snd_hda_codec_hdmi     47547  1 
kvm                   455570  0 
snd_hda_codec_conexant    22962  1 
snd_hda_codec_generic    68914  1 snd_hda_codec_conexant
snd_hda_intel          30379  3 
joydev                 17344  0 
snd_hda_controller     35152  1 snd_hda_intel
thinkpad_acpi          81069  1 
cfg80211              510218  2 mac80211,rtlwifi
snd_hda_codec         139675  5 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_codec_generic,snd_hda_intel,snd_hda_controller
nvram                  14423  1 thinkpad_acpi
snd_hwdep              17698  1 snd_hda_codec
serio_raw              13434  0 
snd_pcm               104102  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller
lpc_ich                21093  0 
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
shpchp                 37040  0 
snd_timer              29513  2 snd_pcm,snd_seq
mei_me                 19742  0 
mei                    87931  1 mei_me
snd                    87611  18 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,thinkpad_acpi,snd_seq_device
soundcore              15052  2 snd,snd_hda_codec
mac_hid                13227  0 
parport_pc             32741  0 
ppdev                  17671  0 
lp                     17759  0 
parport                42299  3 lp,ppdev,parport_pc
dm_crypt               23172  1 
crct10dif_pclmul       14307  0 
crc32_pclmul           13133  0 
ghash_clmulni_intel    13230  0 
aesni_intel           152552  1685 
i915                  917618  3 
aes_x86_64             17131  1 aesni_intel
lrw                    13287  1 aesni_intel
gf128mul               14951  1 lrw
glue_helper            13944  1 aesni_intel
ablk_helper            13597  1 aesni_intel
cryptd                 20360  845 ghash_clmulni_intel,aesni_intel,ablk_helper
psmouse               106548  0 
ahci                   34062  2 
libahci                32424  1 ahci
i2c_algo_bit           13406  1 i915
drm_kms_helper         61627  1 i915
e1000e                230184  0 
sdhci_pci              23261  0 
sdhci                  43448  1 sdhci_pci
drm                   310919  5 i915,drm_kms_helper
ptp                    19445  1 e1000e
pps_core               19333  1 ptp
wmi                    19193  0 
video                  20128  1 i915

iwconfig
eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          
lo        no wireless extensions.

rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


```

---

### Post by Ni Soros on 2014-11-02
After installing the most recent update, via the update manager software, the wifi seems to work perfectly.

---

### Post by daniel199 on 2014-11-11
> **Ni Soros said:**
> After installing the most recent update, via the update manager software, the wifi seems to work perfectly.

I just updated Ubuntu using the updater and it did not fix my problem. Sorry but I can not run that script and post the output until I have time to read what it does and verify the info is not sensitive.

---

