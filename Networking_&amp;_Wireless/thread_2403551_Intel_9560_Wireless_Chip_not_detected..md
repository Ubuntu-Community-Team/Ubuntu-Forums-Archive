---
title: "Intel 9560 Wireless Chip not detected."
date: 2018-10-12
forum: Networking &amp; Wireless
---

### Post by tsuzuku on 2018-10-12
Hello I have seen many post about this, but none of the solutions have worked for me. My laptop cannot seem to find my Intel 9560. I do have Ethernet access if needed. 

EDIT 2: Figure I should mention my laptop as well. Its the newer Lenovo Y530, that comes with a GTX 1050.

EDIT: I Have run the recommended wireless script. Paste can be found here. 
[http://paste.ubuntu.com/p/FCnySDKR44/](http://paste.ubuntu.com/p/FCnySDKR44/)


Here is the output of dmesg | grep iwl 
```


[   13.851406] iwlwifi: unknown parameter 'disable_msix' ignored
[   13.852791] iwlwifi 0000:00:14.3: Direct firmware load for iwlwifi-9000-pu-b0-jf-b0-38.ucode failed with error -2
[   13.852797] iwlwifi 0000:00:14.3: Direct firmware load for iwlwifi-9000-pu-b0-jf-b0-37.ucode failed with error -2
[   13.852802] iwlwifi 0000:00:14.3: Direct firmware load for iwlwifi-9000-pu-b0-jf-b0-36.ucode failed with error -2
[   13.852807] iwlwifi 0000:00:14.3: Direct firmware load for iwlwifi-9000-pu-b0-jf-b0-35.ucode failed with error -2
[   14.478142] iwlwifi 0000:00:14.3: loaded firmware version 34.0.0 op_mode iwlmvm
[   14.879329] iwlwifi 0000:00:14.3: Detected Intel(R) Dual Band Wireless AC 9560, REV=0x318
[   14.935800] iwlwifi 0000:00:14.3: base HW address: c0:b6:f9:13:f9:61
[   15.080134] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[   15.105837] iwlwifi 0000:00:14.3 wlp0s20f3: renamed from wlan0
[   40.834564] Modules linked in: bnep nls_iso8859_1 uvcvideo nvidia_uvm(POE) videobuf2_vmalloc videobuf2_memops videobuf2_v4l2 videobuf2_common nvidia_drm(POE) snd_hda_codec_realtek snd_hda_codec_generic nvidia_modeset(POE) videodev nvidia(POE) media snd_hda_intel snd_hda_codec snd_hda_core snd_hwdep intel_rapl snd_pcm i915 x86_pkg_temp_thermal intel_powerclamp drm_kms_helper snd_seq_midi snd_seq_midi_event coretemp kvm_intel kvm drm arc4 iwlmvm irqbypass crct10dif_pclmul crc32_pclmul ghash_clmulni_intel mac80211 pcbc aesni_intel aes_x86_64 intel_wmi_thunderbolt wmi_bmof crypto_simd cryptd i2c_algo_bit snd_rawmidi ipmi_devintf ipmi_msghandler glue_helper fb_sys_fops iwlwifi snd_seq snd_seq_device cfg80211 snd_timer ideapad_laptop snd btusb intel_cstate mei_me idma64 input_leds joydev serio_raw syscopyarea

```

The output of  sudo modprobe iwlwifi is empty. 

The following are solutions I have attempted. 

```

/**
 *@Attempted Solution 1: Attempting to download the driver from intels site and placing it in /lib/firmware
 */

cd /lib/firmware
sudo wget https://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git/plain/iwlwifi-9000-pu-b0-jf-b0-33.ucode


/**
 *Attempted Solution 2: Simply sudo apt update and upgrade
 */


/**
 *@Attempted Solution 3: Download Driver and move to lib/firmware, iset wlwifi 11n_disable=8 in /etc/modprobe.d/iwlwifi.comf
 *and add the Regdomain to /etc/default/crda
 *
 *@Forum Link: https://askubuntu.com/questions/1045407/wifi-on-asus-rog-gx501-works-with-ubuntu-18-04-fails-on-ubuntu-16-04-intel-wir
 */



/**
 *@Attempted Solution 4: Git fetch the latest iwlwifi Linux Kernel driver and install it. And add 
 * disable_msix=1 to /etc/modprobe.d/iwlwifi.conf
 *
 *@Forum Link : https://askubuntu.com/questions/1038242/no-wifi-option-on-ubuntu-18-04-and-16-04
 */

/**
 *@Attempted Solution 5: purge firmware-b43-installer and install bcmwl-kernel-source 
 *
 *@Forum Link: https://ubuntuforums.org/showthread.php?t=2403385
 */

```

---

### Post by wildmanne39 on 2018-10-12
*Thread moved to **Networking & Wireless for a more appropriate fit**.*

---

### Post by chili555 on 2018-10-13
> 0: ideapad_wlan: Wireless LAN
	Soft blocked: no
	[COLOR="#FF0000"]Hard blocked: yes[/COLOR]Until this is resolved, downloading firmware and adding parameters, etc. will be useless.

Please try:```
sudo modprobe -r ideapad_laptop
sudo rfkill unblock all
```Any improvement? If so, we'll write a quick amendment to a file and make it persistent.

---

### Post by tsuzuku on 2018-10-14
For Some reason blacklisting the ideapad_laptop module was not working if the blacklist was done in a separate file like some solutions suggest. Only when I black listed it in blacklist.conf did it take effect.

---

### Post by jonovisionman on 2019-03-03
> **chili555 said:**
> Until this is resolved, downloading firmware and adding parameters, etc. will be useless.

Please try:```
sudo modprobe -r ideapad_laptop
sudo rfkill unblock all
```Any improvement? If so, we'll write a quick amendment to a file and make it persistent.

Beauty, this worked for me on my Lenovo Ideapad 330.
Thank-you!

jono

---

