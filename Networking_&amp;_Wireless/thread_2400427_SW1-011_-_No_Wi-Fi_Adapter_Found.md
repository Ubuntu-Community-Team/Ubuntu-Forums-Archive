---
title: "SW1-011 - No Wi-Fi Adapter Found"
date: 2018-09-06
forum: Networking &amp; Wireless
---

### Post by csharpconner on 2018-09-06
After weeks of trying I'm turning to these forums.

Ubuntu 18.04.1 LTS
64 bit

On Windows 10 OS it says network adapter is:
RealTek RTL8723BS Wireless Lan

I have tried downloading files using windows and booting into Ubuntu to use them.... I have tried so many things I have been utterly defeated.

I have Secure Boot turned off and UEFI is terrible... it seems no supervisor password and says Mode = User.... it was a miracle I even got this far  .... though I haven't figured out dual boot screen to pick from yet and need to F2 and swap the boot loader around from windows an ubuntu....

This has been a terrible experience.....

I've tried installing a bunch of dpkg from the usb drive I made with Rufus and got stuff seemingly installed but still no wifi..  there is no ethernet port on this tablet....

I have to use terminal with xrandr -o right everytime I boot up to make the screen the right way on the docked keyboard.....

This is a total nightmare and I need help with this godforsaken Acer Switch One 10 Netbook/Tablet.. horrid thing

---

### Post by chili555 on 2018-09-06
I believe the correct driver is already included in Ubuntu 18.04; perhaps there is some other issue.

Please open a terminal and do:```
sudo modprobe r8723bs
```And now lets's see what the logs have to report:```
dmesg | grep 8723
iwconfig
```

---

### Post by csharpconner on 2018-09-06
```
weixin@SW1-011:~$ sudo modprobe r8723bs

weixin@SW1-011:~$ dmesg | grep 8723


[    5.600621] r8723bs: module is from the staging directory, the quality is unknown, you have been warned.


[    5.601668] r8723bs: module verification failed: signature and/or required key missing - tainting kernel


[    5.605817] RTL8723BS: module init start


[    5.605822] RTL8723BS: rtl8723bs v4.3.5.5_12290.20140916_BTCOEX20140507-4E40


[    5.605823] RTL8723BS: rtl8723bs BT-Coex version = BTCOEX20140507-4E40


[    5.605876] RTL8723BS: module init ret =0


[   25.268723]  Audio Port: ASoC: no backend DAIs enabled for Audio Port


[  251.588723]  Audio Port: ASoC: no backend DAIs enabled for Audio Port


[  252.418723]  Audio Port: ASoC: no backend DAIs enabled for Audio Port


weixin@SW1-011:~$ iwconfig


lo        no wireless extensions.





```

Image here: [https://imgur.com/a/mcKrDX2](https://imgur.com/a/mcKrDX2)

[img]https://imgur.com/a/mcKrDX2[/img]
[IMG]https://imgur.com/a/mcKrDX2[/IMG]

---

### Post by chili555 on 2018-09-06
> RTL8723BS: module init ret =0I am very suspicious about that; Googling...

May I also see:```
dmesg | grep -i rtl
```

---

### Post by csharpconner on 2018-09-07
Image Here: [https://imgur.com/a/hNdWeJA](https://imgur.com/a/hNdWeJA)
[https://imgur.com/a/hNdWeJA](https://imgur.com/a/hNdWeJA)
[https://i.imgur.com/UVmxt2P.png](https://i.imgur.com/UVmxt2P.png)

---

### Post by chili555 on 2018-09-07
We still see nothing useful; that is, fixable. How about:```
dmesg | grep -i sdio
```

---

### Post by csharpconner on 2018-09-07
```
[     3.096773]mmc1: new high speed SDIO card at address 0001
```

---

### Post by chili555 on 2018-09-08
Aside from this mysterious message, I am unclear at all as to why the driver and hardware don't create a wireless interface and start up as expected.> RTL8723BS: module init ret =0Let's try something to see if it is helpful. We will load a driver parameter and check the log for useful clues:```
sudo modprobe -r r8723bs
sudo modprobe r8723bs rtw_btcoex_enable=0
dmesg | grep 8723
```

-----------------------

Note to Chili: default=1??,  possible?? =2 or =3 os_dep/linux/os_intfs.c

---

### Post by csharpconner on 2018-09-11
```
weixin@SW1-011:~$ sudo modprobe -r r8723bsweixin@SW1-011:~$ sudo modprobe r8723bs rtw_btcoex_enable=0
weixin@SW1-011:~$ dmesg | grep 8723
[    5.760707] r8723bs: module is from the staging directory, the quality is unknown, you have been warned.
[    5.785503] r8723bs: module verification failed: signature and/or required key missing - tainting kernel
[    5.789044] RTL8723BS: module init start
[    5.789049] RTL8723BS: rtl8723bs v4.3.5.5_12290.20140916_BTCOEX20140507-4E40
[    5.789051] RTL8723BS: rtl8723bs BT-Coex version = BTCOEX20140507-4E40
[    5.789085] RTL8723BS: module init ret =0
[100953.608399] Modules linked in: snd_soc_sst_bytcr_rt5651 nls_iso8859_1 axp288_fuel_gauge axp288_charger axp20x_pek axp288_adc extcon_axp288 intel_rapl intel_powerclamp coretemp kvm_intel gpio_keys kvm irqbypass punit_atom_debug crct10dif_pclmul crc32_pclmul ghash_clmulni_intel pcbc aesni_intel aes_x86_64 crypto_simd glue_helper cryptd snd_intel_sst_acpi snd_intel_sst_core intel_cstate snd_soc_sst_atom_hifi2_platform snd_soc_rt5651 snd_soc_acpi snd_soc_rl6231 snd_soc_acpi_intel_match wmi_bmof sparse_keymap joydev snd_soc_core input_leds snd_compress ac97_bus hid_multitouch snd_hdmi_lpe_audio snd_pcm_dmaengine snd_seq_midi snd_seq_midi_event snd_pcm mei_txe lpc_ich snd_rawmidi mei processor_thermal_device intel_soc_dts_iosf snd_seq r8723bs(CE) snd_seq_device intel_cht_int33fe dw_dmac dw_dmac_core axp20x_i2c
[345162.248597] RTL8723BS: module exit start
[345162.250015] RTL8723BS: module exit success
[345205.894255] r8723bs: module is from the staging directory, the quality is unknown, you have been warned.
[345205.898731] RTL8723BS: module init start
[345205.898735] RTL8723BS: rtl8723bs v4.3.5.5_12290.20140916_BTCOEX20140507-4E40
[345205.898736] RTL8723BS: rtl8723bs BT-Coex version = BTCOEX20140507-4E40
[345205.898787] RTL8723BS: module init ret =0

```

Image Here:  [https://i.imgur.com/I73zQ4D.png](https://i.imgur.com/I73zQ4D.png)

---

### Post by chili555 on 2018-09-12
Frankly, I can see no reason and I haven't any suggestions as to why your device doesn't start. I think, but I'm not certain, that this is the clue:> RTL8723BS: module init ret =0I regret that I have no other suggestions.

I recommend that you file a bug report: [https://bugs.launchpad.net/](https://bugs.launchpad.net/)

---

### Post by csharpconner on 2018-09-12
Thank you for your efforts.... I suppose I will have to try another Linux OS instead now.  Again, thank you for trying.

---

### Post by chili555 on 2018-09-12
If it works, we will be very surprised and we hope you will return to this thread so we may ask you for some log outputs.

---

