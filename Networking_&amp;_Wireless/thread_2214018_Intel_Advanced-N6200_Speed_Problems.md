---
title: "Intel Advanced-N6200 Speed Problems"
date: 2014-03-30
forum: Networking &amp; Wireless
---

### Post by bthoward on 2014-03-30
Laptop is a Sony Vaio Z VPCZ12CGX.

i had the problem a few versions ago where 802.11n was disabled but I thought that was all over with.  I'm connected to my access point at 216Mb/s.  However when I run iperf to a server on the other side of the network wired via gigabit I only get about 25Mbit.  When I do a test from that same box back to my laptop I get about 50Mbit.  When doing a test from another laptop on the same wireless network to the same box things run around 85-90Mbit this box has an Intel 5100 card.  Ranges to the access point is about the same on both machines.  I've tried changing channels and its the only 5Ghz AP in the area.  AP is a WNDR3700.  Using latest 14.04 but I had these exact same issues on 13.10 and was hoping that a format and fresh install would help.  No such luck.  I've verified that I've got the latest driver from ([http://wireless.kernel.org/en/users/Drivers/iwlwifi](http://wireless.kernel.org/en/users/Drivers/iwlwifi)) and have tried loading the version from there into my firmware folder.  No change there either.

```
brett@lappy:~$ iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"howard5g"  
          Mode:Managed  Frequency:5.785 GHz  Access Point: 00:24:B2:5A:8B:56   
          Bit Rate=216 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=55/70  Signal level=-55 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:337   Missed beacon:0

```

```
brett@lappy:~$ lspci | grep Network
00:19.0 Ethernet controller: Intel Corporation 82577LC Gigabit Network Connection (rev 05)
02:00.0 Network controller: Intel Corporation Centrino Advanced-N 6200 (rev 35)

```

```
brett@lappy:~$ dmesg | grep iwl
[    4.202205] iwlwifi 0000:02:00.0: can't disable ASPM; OS doesn't have ASPM control
[    4.202271] iwlwifi 0000:02:00.0: irq 43 for MSI/MSI-X
[    4.204575] iwlwifi 0000:02:00.0: Direct firmware load failed with error -2
[    4.204580] iwlwifi 0000:02:00.0: Falling back to user helper
[    4.586250] iwlwifi 0000:02:00.0: Direct firmware load failed with error -2
[    4.586252] iwlwifi 0000:02:00.0: Falling back to user helper
[    4.604828] iwlwifi 0000:02:00.0: loaded firmware version 9.221.4.1 build 25532 op_mode iwldvm
[    4.636542] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_DEBUG disabled
[    4.636544] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[    4.636545] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[    4.636547] iwlwifi 0000:02:00.0: Detected Intel(R) Centrino(R) Advanced-N 6200 AGN, REV=0x74
[    4.636602] iwlwifi 0000:02:00.0: L1 Enabled; Disabling L0S
[    4.657639] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[    5.668494] Modules linked in: joydev arc4 iwldvm mac80211 mxm_wmi intel_powerclamp coretemp kvm_intel kvm crct10dif_pclmul crc32_pclmul ghash_clmulni_intel aesni_intel snd_hda_intel(+) aes_x86_64 lrw gf128mul glue_helper ablk_helper cryptd snd_hda_codec snd_hwdep snd_pcm rfcomm dm_multipath bnep scsi_dh psmouse snd_page_alloc serio_raw snd_seq_midi snd_seq_midi_event snd_rawmidi uvcvideo iwlwifi btusb videobuf2_vmalloc videobuf2_memops videobuf2_core bluetooth intel_ips(+) videodev snd_seq mac_hid snd_seq_device i915(+) snd_timer snd sony_laptop cfg80211 drm_kms_helper drm wmi video i2c_algo_bit soundcore mei_me mei lpc_ich binfmt_misc lp parport ahci libahci sdhci_pci sdhci dm_mirror dm_region_hash dm_log e1000e ptp pps_core
[    6.878377] iwlwifi 0000:02:00.0: L1 Enabled; Disabling L0S
[    6.885047] iwlwifi 0000:02:00.0: Radio type=0x1-0x3-0x1
[    7.096813] iwlwifi 0000:02:00.0: L1 Enabled; Disabling L0S
[    7.103702] iwlwifi 0000:02:00.0: Radio type=0x1-0x3-0x1

```

---

### Post by bthoward on 2014-03-31
On a whim I just bought a 802.11ac router and found there to be no change.  I've also placed an order for an Intel 7260 mini pcie half card.  Perhaps that will help me out.

---

### Post by chili555 on 2014-03-31
First, check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, I have better luck with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz. I also have better luck with a fixed channel, either 1 or 11, rather than automatic channel selection. After making these changes, reboot the router.

Next, I recommend that your regulatory domain be set explicitly. Check yours:```
sudo iw reg get
```If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it permanently:```
gksudo gedit /etc/rc.local
```Right above the line exit 0, add the line:```
iw reg set IS
```Of course, substitute your country code if not Iceland. Proofread carefully, save and close gedit. 

If these changes are ineffective, I will propose the backported driver from kernel 3.13.

---

### Post by bthoward on 2014-04-05
I didn't see any reason to go into the WAP settings because another computer gets the speeds that I want to get.  When I run the iw reg get command I get:

> country US:
	(2402 - 2472 @ 40), (3, 27)
	(5170 - 5250 @ 40), (3, 17)
	(5250 - 5330 @ 40), (3, 20), DFS
	(5490 - 5600 @ 40), (3, 20), DFS
	(5650 - 5710 @ 40), (3, 20), DFS
	(5735 - 5835 @ 40), (3, 30)
	(57240 - 63720 @ 2160), (N/A, 40)


I've since installed my 7260 card and speeds went from 25 mbit to about 85-95mbit and when testing in the other direction back to me I get as high at 160mbit.  I'm happy enough with that.  But I think that there is a bug or something with regard to the 6200 card.

~Brett

---

### Post by chili555 on 2014-04-05
My suggestions in regard to the router are generally accepted and not just in Linux: [http://www.smallnetbuilder.com/wireless/wireless-basics/30664-5-ways-to-fix-slow-80211n-speed](http://www.smallnetbuilder.com/wireless/wireless-basics/30664-5-ways-to-fix-slow-80211n-speed)

[https://communities.intel.com/thread/40405](https://communities.intel.com/thread/40405)

It is certainly your choice to implement or not any of my suggestions.

---

### Post by bthoward on 2014-04-05
I'd already done those things to maximize speed.  And it was faster with this laptop on a previous version of Ubuntu with the 6200 card but 14.04 had an issue with the 6200 and I couldn't seem to get it over about 25 mbit or so...

---

