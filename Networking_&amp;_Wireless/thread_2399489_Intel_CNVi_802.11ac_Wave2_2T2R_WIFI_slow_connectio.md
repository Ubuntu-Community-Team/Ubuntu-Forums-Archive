---
title: "Intel CNVi 802.11ac Wave2 2T2R WIFI slow connection Ubuntu 18.04.1 LTS"
date: 2018-08-25
forum: Networking &amp; Wireless
---

### Post by jsrco on 2018-08-25
Using: Gigabyte H370 AORUS Gaming 3 WiFi motherboard.

Works fine when I had Windows, but in Ubuntu it does not go above the low 20s mbps. 

I have attached the pastebin files. Would love any assistance possible.

---

### Post by chili555 on 2018-08-26
> Cell 01 - Address: <MAC 'Orlando' [AC1]>
                    Channel:149
                    Frequency:5.745 GHz
                    Quality=68/70  Signal level=-42 dBm  
                    Encryption key:on
                    ESSID:"Orlando"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000537bed9f4c
                    Extra: Last beacon: 188ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSKYou have a wonderful wireless device in a modern fast computer that is struggling with default settings in the router.

First, check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, you may have better connectivity with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz, although it is likely to affect N speeds. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. In the 5 GHz band, I'd select, if possible, an unused channel; in your case it appears that channel 44 is ideal as it is currently not occupied.

Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. After making these changes, reboot the router. 

Next, I recommend that your regulatory domain be set explicitly. Check yours:

   ```
 sudo iw reg get
```

If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:

    ```
sudo iw reg set IS
```

Of course, substitute your country code if not Iceland. Set it permanently:

    ```
sudo nano /etc/default/crda
```

Change the last line to read:

   ```
 REGDOMAIN=IS
```

Proofread carefully, save and close the text editor.

After these changes, reboot the computer and tell us if there is any improvement.

---

### Post by praseodym on 2018-08-26
No dmesg-output?! Lets see
```

dmesg | grep iwl
```

---

### Post by jsrco on 2018-08-26
praseodym:
> [54578.486545] Modules linked in: btrfs zstd_compress xor raid6_pq ufs qnx4 hfsplus hfs minix ntfs msdos jfs xfs libcrc32c rfcomm ccm bnep nls_iso8859_1 snd_hda_codec_hdmi intel_rapl x86_pkg_temp_thermal intel_powerclamp coretemp kvm_intel kvm irqbypass crct10dif_pclmul crc32_pclmul ghash_clmulni_intel pcbc aesni_intel aes_x86_64 crypto_simd glue_helper cryptd arc4 snd_hda_codec_realtek wmi_bmof intel_wmi_thunderbolt snd_hda_codec_generic snd_hda_intel snd_usb_audio iwlmvm snd_hda_codec snd_usbmidi_lib snd_hda_core snd_seq_midi btusb snd_seq_midi_event snd_hwdep intel_cstate mac80211 joydev snd_rawmidi input_leds snd_seq btrtl snd_pcm btbcm btintel snd_seq_device iwlwifi bluetooth snd_timer intel_rapl_perf snd mei_me shpchp ecdh_generic cfg80211 mei soundcore intel_pch_thermal wmi nvidia_uvm(POE) acpi_pad
[54578.486624]  ? iwl_write32+0x38/0x90 [iwlwifi]


---

### Post by jsrco on 2018-08-26
I have made those changes and no improvement.

---

### Post by chili555 on 2018-08-26
> **jsrco said:**
> I have made those changes and no improvement.May we see a new wireless-info?

---

### Post by jsrco on 2018-08-26
New info attached. sudo [ATTACH]280866[/ATTACH]

> 
[    7.046117] iwlwifi 0000:00:14.3: enabling device (0000 -> 0002)[    7.058706] iwlwifi 0000:00:14.3: loaded firmware version 34.0.0 op_mode iwlmvm
[    7.083684] iwlwifi 0000:00:14.3: Detected Intel(R) Dual Band Wireless AC 9560, REV=0x318
[    7.138192] iwlwifi 0000:00:14.3: base HW address: 00:24:d6:f2:57:5b
[    7.207324] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[    7.207990] iwlwifi 0000:00:14.3 wlo1: renamed from wlan0


---

### Post by chili555 on 2018-08-27
In your paste, we see this:> [/etc/modprobe.d/rtl88821ae_options.conf]
options rtl8821ae swenc=1 swlps=1 fwlps=0 ips=0
Do you actually have an rtl8821ae device? If not, let's remove the unneeded file:```
sudo rm /etc/modprobe.d/rtl88821ae_options.conf
```We also see this:> [/etc/modprobe.d/iwlwifi.conf]
options iwlwifi 11n_disable=1First, I doubt that 11n_disable is needed here. Second, in adding the parameter to the conf file, you overwrote the prior file instead of appending it. Let's correct it:```
sudo nano /etc/modprobe.d/iwlwifi.conf
```Remove the existing line and add instead:```
# /etc/modprobe.d/iwlwifi.conf
# iwlwifi will dyamically load either iwldvm or iwlmvm depending on the
# microcode file installed on the system.  When removing iwlwifi, first
# remove the iwl?vm module and then iwlwifi.
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

```Proofread carefully twice, save and close the text editor.

Now unload and reload the module:```
sudo modprobe -r iwlwifi && sudo modprobe iwlwifi
```Now is there any improvement?

---

### Post by jsrco on 2018-08-27
This improved it on the 2.4 ghz range, it was operating at the same speed as everything the house. The 5ghz won't even go above 1mbps now.

---

### Post by chili555 on 2018-08-28
Please try:

```
sudo modprobe -r iwlwifi
sudo modprobe iwlwifi 11n_disable=8
```

If it helps, we'll make it persistent.

---

### Post by jsrco on 2018-08-28
That didn't seem to change anything, but the 2.6 is working correctly and that is good enough for me.

Thank you very much for the assistance.

---

