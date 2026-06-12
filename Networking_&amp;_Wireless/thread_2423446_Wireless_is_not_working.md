---
title: "Wireless is not working"
date: 2019-07-23
forum: Networking &amp; Wireless
---

### Post by ragingrhino489 on 2019-07-23
Hello I am using an HP Laptop and I currently have Ubuntu 18.04 installed on it. It is using a realtek driver and it will not let me connect to wireless.

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 005: ID 2a94:5009  
Bus 001 Device 004: ID 0bda:b00a Realtek Semiconductor Corp. 
Bus 001 Device 003: ID 04f2:b65d Chicony Electronics Co., Ltd 
Bus 001 Device 002: ID 046d:c534 Logitech, Inc. Unifying Receiver
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


That is the result when I used lsusb. 

hp_wmi                 16384  0
wmi_bmof               16384  0
intel_wmi_thunderbolt    16384  0
snd_soc_acpi           16384  1 snd_soc_skl
snd_rawmidi            32768  1 snd_seq_midi
wmi                    24576  3 hp_wmi,intel_wmi_thunderbolt,wmi_bmof
snd_seq_device         16384  3 snd_seq,snd_seq_midi,snd_rawmidi
snd                    81920  22 snd_hda_codec_generic,snd_seq,snd_seq_device,snd_hda_codec_hdmi,snd_hwdep,snd_hda_intel,snd_hda_codec,snd_hda_codec_realtek,snd_timer,snd_compress,snd_soc_core,snd_pcm,snd_rawmidi
sparse_keymap          16384  2 hp_wmi,intel_vbtn
acpi_thermal_rel       16384  1 int3400_thermal
acpi_pad              180224  0

That is the result when I used lsmod | grep -e wmi -e acpi. If someone could please give me some insight on what I am not doing correctly it would be greatly appreciated!

---

### Post by jeremy31 on 2019-07-23
Moved to Networking and Wireless, please see the wireless script link in my signature and post results

---

### Post by ragingrhino489 on 2019-07-23
Ubuntu is stating that its unable to resolve host address 'github'

---

