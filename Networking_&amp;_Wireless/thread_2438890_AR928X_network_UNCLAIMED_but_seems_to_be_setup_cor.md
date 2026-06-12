---
title: "AR928X network UNCLAIMED but seems to be setup correctly [Ubuntu 18.04.4]"
date: 2020-03-19
forum: Networking &amp; Wireless
---

### Post by daygovicks on 2020-03-19
I picked up a TPE-N300PCIED wifi network card from thinkpenguin (AR928X chipset). After installing the card I did a fresh install of ubuntu 18.04 with a new image but the wireless card isn't recognized. I can find the card through the terminal, modprobe says the modules are installed, and yet lshw says the network is UNCLAIMED. If I look for WiFi in the settings of Ubuntu it says no card found. I spent the better part of a day searching for the card as well as related issues and trying the things found here and elsewhere to no success. I even tried installing the alpha release of 20.04 which also couldn't recognize the card (same error). I am hoping someone can help me out! Below is the pastebin output from the stickied comment.

[http://paste.ubuntu.com/p/2fNPyw8vYP/](http://paste.ubuntu.com/p/2fNPyw8vYP/)

---

### Post by chili555 on 2020-03-19
Please run and post: ```
sudo modprobe ath9k && dmesg | grep ath
```Thanks.

---

### Post by daygovicks on 2020-03-20
Thanks for the help! Here is the output requested.

[   52.584112] ath9k 0000:41:00.0: enabling device (0000 -> 0002)
[   53.016142] ath: EEPROM regdomain: 0x6a
[   53.016144] ath: EEPROM indicates we should expect a direct regpair map
[   53.016145] ath: Country alpha2 being used: 00
[   53.016146] ath: Regpair used: 0x6a
[   53.016193] ath9k 0000:41:00.0: swiotlb buffer is full (sz: 1926 bytes), total 0 (slots), used 0 (slots)
[   53.016195] ath9k 0000:41:00.0: overflow 0x0000001034853040+1926 of DMA mask ffffffff bus mask 0
[   53.016203] Modules linked in: snd_hda_intel snd_intel_nhlt snd_hda_codec amd64_edac_mod(-) edac_mce_amd ath9k(+) snd_hda_core snd_hwdep ath9k_common kvm_amd snd_pcm kvm irqbypass ath9k_hw ath snd_seq_midi snd_seq_midi_event mac80211 snd_rawmidi snd_seq cfg80211 snd_seq_device wmi_bmof snd_timer libarc4 snd k10temp soundcore ccp mac_hid sch_fq_codel parport_pc ppdev sunrpc lp parport ip_tables x_tables autofs4 algif_skcipher af_alg dm_crypt hid_plantronics hid_generic usbhid hid amdgpu crct10dif_pclmul crc32_pclmul ghash_clmulni_intel amd_iommu_v2 aesni_intel mxm_wmi gpu_sched ttm aes_x86_64 crypto_simd drm_kms_helper cryptd glue_helper syscopyarea sysfillrect sysimgblt fb_sys_fops drm igb nvme dca i2c_piix4 i2c_algo_bit ahci nvme_core libahci gpio_amdpt gpio_generic wmi
[   53.016245]  ath_rx_init+0x474/0x530 [ath9k]
[   53.016249]  ath9k_init_device+0xd64/0xea0 [ath9k]
[   53.016255]  ath_pci_probe+0x1a8/0x380 [ath9k]
[   53.016272]  ? set_use_msi+0x1a/0x1a [ath9k]
[   53.016276]  ? set_use_msi+0x1a/0x1a [ath9k]
[   53.016280]  ath_pci_init+0x23/0x30 [ath9k]
[   53.016282]  ath9k_init+0xe/0xfe6 [ath9k]
[   53.016304] ath: phy0: dma_mapping_error() on RX init
[   53.016340] ath9k 0000:41:00.0: Failed to initialize device
[   53.016430] ath9k: probe of 0000:41:00.0 failed with error -12

---

### Post by chili555 on 2020-03-20
> 
[ 53.016304] ath: phy0: dma_mapping_error() on RX init
[ 53.016340] ath9k 0000:41:00.0: Failed to initialize device
[ 53.016430] ath9k: probe of 0000:41:00.0 failed with error -12Is this a dual-boot with Windows? If so, please check here: [https://wireless.wiki.kernel.org/en/users/drivers/iwlwifi#about_dual-boot_with_windows_and_fast-boot_enabled](https://wireless.wiki.kernel.org/en/users/drivers/iwlwifi#about_dual-boot_with_windows_and_fast-boot_enabled) Please make the change in Windows and try again:```
sudo modprobe ath9k && dmesg | grep ath
```Does the probe still fail with error -12?

If this suggestion is ineffective, then there are several suggestions on various fora that recommend a boot parameter. In the terminal, do:```
sudo nano /etc/default/grub
```Find this line: ```
GRUB_CMDLINE_LINUX=""
```Change it to read: ```
GRUB_CMDLINE_LINUX="iommu=soft"
```Proofread carefully twice. Save (Ctrl+o followed by Enter) and exit nano (Ctrl+x). Now do:```
sudo update-grub
```Reboot. Any improvement?

---

### Post by daygovicks on 2020-03-20
I have never had windows on the PC but the iommu=soft worked like a charm!

I am a fan of learning. Do you have any good resources about what that command does and why it worked?

Thank you so much for the help!

---

### Post by chili555 on 2020-03-20
Awesome! Glad it's working!

You might get more insight here: [https://unix.stackexchange.com/questions/469153/what-are-the-implication-of-iommu-soft](https://unix.stackexchange.com/questions/469153/what-are-the-implication-of-iommu-soft)

Please use thread tools at the top to mark Solved. The searchers will appreciate it.

---

