---
title: "trying to connect using ubuntu 14.04.4 , but wireless keeps turning off"
date: 2016-08-18
forum: Networking &amp; Wireless
---

### Post by Gatorade on 2016-08-18
I've been trying to dual boot an hp pavillion x360 m1 with windows 10 and ubuntu.

I am trying to get the bootable USB to connect to the wif, but each time I try to turn the wireless connection on it just flashes for a half second and then goes back to being switched off.

does anyone know why it's doing this, and how to fix it?

---

### Post by Gatorade on 2016-08-18
this computer also has a GRUB boot issue, BTW.
I had successfully installed Ubuntu along side windows 10 , but after re-booting it goes directly to windows without giving me the option to select Ubuntu.
Since it was two problems, I wasn't sure whether to post here or general help.

---

### Post by chili555 on 2016-08-18
> **Gatorade said:**
> I've been trying to dual boot an hp pavillion x360 m1 with windows 10 and ubuntu.

I am trying to get the bootable USB to connect to the wif, but each time I try to turn the wireless connection on it just flashes for a half second and then goes back to being switched off.

does anyone know why it's doing this, and how to fix it?It probably happens because the helper module that translates key presses, in your case, the wireless switch, into action, in your case, turn on the wireless radio, is not working correctly. Let's see if we can tweak it. Please open a terminal and run and post:```
rfkill list all
lsmod
```After we've finished, please ask about GRUB over on General Help. They don't allow me to play with complicated things like GRUB, scissors or drain cleaner.

---

### Post by Gatorade on 2016-08-18
```
ubuntu@ubuntu:~$ rfkill list all 
0: hci0: Bluetooth 
	Soft blocked: no 
	Hard blocked: no 
1: phy0: Wireless LAN 
	Soft blocked: no 
	Hard blocked: no 
2: acer-wireless: Wireless LAN 
	Soft blocked: yes 
	Hard blocked: no 
ubuntu@ubuntu:~$ lsmod 
Module                  Size  Used by 
hid_sensor_gyro_3d     16384  0 
hid_sensor_accel_3d    16384  0 
hid_sensor_incl_3d     16384  0 
hid_sensor_rotation    16384  0 
hid_sensor_magn_3d     16384  0 
hid_sensor_trigger     16384  10 hid_sensor_gyro_3d,hid_sensor_incl_3d,hid_sensor_accel_3d,hid_sensor_rotation,hid_sensor_magn_3d 
industrialio_triggered_buffer    16384  5 hid_sensor_gyro_3d,hid_sensor_incl_3d,hid_sensor_accel_3d,hid_sensor_rotation,hid_sensor_magn_3d 
kfifo_buf              16384  1 industrialio_triggered_buffer 
industrialio           61440  8 hid_sensor_trigger,hid_sensor_gyro_3d,industrialio_triggered_buffer,hid_sensor_incl_3d,hid_sensor_accel_3d,hid_sensor_rotation,kfifo_buf,hid_sensor_magn_3d 
hid_sensor_iio_common    16384  6 hid_sensor_trigger,hid_sensor_gyro_3d,hid_sensor_incl_3d,hid_sensor_accel_3d,hid_sensor_rotation,hid_sensor_magn_3d 
hid_sensor_custom      20480  0 
snd_hda_codec_hdmi     49152  1 
hid_multitouch         20480  0 
snd_hda_codec_realtek    86016  0 
snd_hda_codec_generic    73728  2 snd_hda_codec_realtek 
intel_rapl             20480  0 
dm_crypt               28672  0 
intel_powerclamp       16384  0 
hp_wmi                 16384  0 
snd_hda_intel          36864  3 
coretemp               16384  0 
acer_wmi               20480  0 
sparse_keymap          16384  2 acer_wmi,hp_wmi 
snd_hda_codec         135168  4 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel 
snd_hda_core           65536  5 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel 
kvm                   507904  0 
uvcvideo               90112  0 
snd_hwdep              16384  1 snd_hda_codec 
videobuf2_vmalloc      16384  1 uvcvideo 
punit_atom_debug       16384  0 
videobuf2_memops       16384  1 videobuf2_vmalloc 
crct10dif_pclmul       16384  0 
crc32_pclmul           16384  0 
snd_pcm               102400  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_core 
videobuf2_core         49152  1 uvcvideo 
cmac                   16384  2 
v4l2_common            16384  1 videobuf2_core 
aesni_intel           167936  2 
arc4                   16384  2 
videodev              172032  3 uvcvideo,v4l2_common,videobuf2_core 
snd_seq_midi           16384  0 
iwlmvm                290816  0 
aes_x86_64             20480  1 aesni_intel 
hid_sensor_hub         20480  8 hid_sensor_trigger,hid_sensor_gyro_3d,hid_sensor_incl_3d,hid_sensor_accel_3d,hid_sensor_rotation,hid_sensor_custom,hid_sensor_magn_3d,hid_sensor_iio_common 
snd_seq_midi_event     16384  1 snd_seq_midi 
media                  24576  2 uvcvideo,videodev 
mac80211              729088  1 iwlmvm 
lrw                    16384  1 aesni_intel 
gf128mul               16384  1 lrw 
glue_helper            16384  1 aesni_intel 
dm_multipath           24576  0 
scsi_dh                16384  1 dm_multipath 
btusb                  45056  0 
ablk_helper            16384  1 aesni_intel 
btrtl                  16384  1 btusb 
snd_rawmidi            32768  1 snd_seq_midi 
input_leds             16384  0 
btbcm                  16384  1 btusb 
bnep                   20480  2 
snd_seq                69632  2 snd_seq_midi_event,snd_seq_midi 
iwlwifi               204800  1 iwlmvm 
joydev                 20480  0 
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi 
btintel                16384  1 btusb 
serio_raw              16384  0 
rtsx_pci_ms            20480  0 
cryptd                 20480  2 aesni_intel,ablk_helper 
cfg80211              540672  3 iwlwifi,mac80211,iwlmvm 
rfcomm                 69632  8 
memstick               20480  1 rtsx_pci_ms 
snd_timer              32768  2 snd_pcm,snd_seq 
hp_accel               28672  0 
bluetooth             512000  25 bnep,btbcm,btrtl,btusb,rfcomm,btintel 
mei_txe                20480  0 
snd                    81920  17 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device 
lis3lv02d              20480  1 hp_accel 
i2c_hid                20480  0 
soc_button_array       16384  0 
processor_thermal_device    16384  0 
int3403_thermal        16384  0 
8250_fintek            16384  0 
mei                    98304  1 mei_txe 
int3400_thermal        16384  0 
soundcore              16384  1 snd 
int340x_thermal_zone    16384  2 processor_thermal_device,int3403_thermal 
acpi_thermal_rel       16384  1 int3400_thermal 
intel_soc_dts_iosf     16384  1 processor_thermal_device 
lpc_ich                24576  0 
pinctrl_cherryview     32768  0 
tpm_crb                16384  0 
hp_wireless            16384  0 
input_polldev          16384  1 lis3lv02d 
shpchp                 36864  0 
i2c_designware_platform    16384  0 
mac_hid                16384  0 
i2c_designware_core    16384  1 i2c_designware_platform 
parport_pc             32768  0 
ppdev                  20480  0 
lp                     20480  0 
parport                49152  3 lp,ppdev,parport_pc 
squashfs               49152  1 
overlay                45056  1 
nls_iso8859_1          16384  1 
dm_mirror              24576  0 
dm_region_hash         20480  1 dm_mirror 
dm_log                 20480  2 dm_region_hash,dm_mirror 
uas                    24576  0 
usb_storage            69632  2 uas 
usbhid                 49152  0 
hid                   118784  4 i2c_hid,hid_multitouch,hid_sensor_hub,usbhid 
rtsx_pci_sdmmc         24576  0 
i915                 1126400  4 
i2c_algo_bit           16384  1 i915 
psmouse               126976  0 
drm_kms_helper        126976  1 i915 
drm                   360448  5 i915,drm_kms_helper 
rtsx_pci               53248  2 rtsx_pci_ms,rtsx_pci_sdmmc 
ahci                   36864  1 
libahci                32768  1 ahci 
wmi                    20480  2 acer_wmi,hp_wmi 
video                  36864  2 i915,acer_wmi 
sdhci_acpi             16384  0 
sdhci                  45056  1 sdhci_acpi 
ubuntu@ubuntu:~$ lsmod
```

---

### Post by chili555 on 2016-08-18
> ubuntu@ubuntu:~$ rfkill list all 
0: hci0: Bluetooth 
Soft blocked: no 
Hard blocked: no 
1: phy0: Wireless LAN 
Soft blocked: no 
Hard blocked: no 
2: [COLOR="#FF0000"]acer-wireless: Wireless LAN 
Soft blocked: yes [/COLOR]
Hard blocked: no Hmmm. Your HP laptop is not also an Acer, I suspect. Let's blacklist and unload the module and see if it helps:```
sudo -i
echo "blacklist acer-wmi"  >>  /etc/modprobe.d/blacklist.conf
modprobe -r acer-wmi
exit
```Any improvement? It may take a reboot.

---

### Post by Gatorade on 2016-08-18
awesome, it worked !

thank-you.

did a re-boot and it kept the changes. 
At least I got it to work , now to try to fix the GRUB issue.

---

### Post by wildmanne39 on 2016-08-18
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by Gatorade on 2016-08-19
ok,thx for telling me that, will do.

---

