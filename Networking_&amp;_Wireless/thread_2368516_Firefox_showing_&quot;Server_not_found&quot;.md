---
title: "Firefox showing &quot;Server not found&quot;"
date: 2017-08-11
forum: Networking &amp; Wireless
---

### Post by Mryl on 2017-08-11
Ethernet shows connected but Firefox showing "Server not found", I don't know what to do, tried google.com . Old Dell latitude XT, I installed Lubuntu which seems fine but no internet. (Not finding wifi either). Can anyone help?

Thanks

---

### Post by QIII on 2017-08-11
Hello!

Are you connecting through a router/gateway?  Do you have other devices connecting via it?  Can you reach the internet from those devices?

---

### Post by Mryl on 2017-08-11
Connecting thru router, other devices fine

---

### Post by wildmanne39 on 2017-08-12
Hi, welcome to the forum! Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # then paste the information between the brackets.
Thank you

---

### Post by Mryl on 2017-08-12
```


mls@mls-Latitude-XT:~$ sudo cat/etc/lsb-release;unam/e-a
[sudo] password for mls: 
sudo: cat/etc/lsb-release: command not found
bash: unam/e-a: No such file or directory
mls@mls-Latitude-XT:~$ 
mls@mls-Latitude-XT:~$ lspci-nnk|grep-iA2net
lspci-nnk: command not found
grep-iA2net: command not found
mls@mls-Latitude-XT:~$ lsusb
Bus 001 Device 004: ID 154b:00c4 PNY 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 0483:2016 STMicroelectronics Fingerprint Reader
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 1b96:0001 N-Trig Duosense Transparent Electromagnetic Digitizer
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
mls@mls-Latitude-XT:~$ iwconfig
lo        no wireless extensions.


enp9s0    no wireless extensions.


mls@mls-Latitude-XT:~$ rfkill list all
0: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: dell-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
mls@mls-Latitude-XT:~$ lsmod
Module                  Size  Used by
nls_iso8859_1          16384  1
uas                    24576  0
usb_storage            69632  2 uas
dell_wmi               16384  0
sparse_keymap          16384  1 dell_wmi
dell_rbtn              16384  0
dell_laptop            20480  0
dell_smbios            16384  2 dell_wmi,dell_laptop
dcdbas                 16384  1 dell_smbios
dell_smm_hwmon         16384  0
coretemp               16384  0
b43                   413696  0
kvm                   593920  0
bcma                   57344  1 b43
mac80211              782336  1 b43
hid_ntrig              20480  0
irqbypass              16384  1 kvm
snd_hda_codec_idt      57344  1
snd_hda_codec_generic    73728  1 snd_hda_codec_idt
snd_hda_intel          36864  3
snd_hda_codec         126976  3 snd_hda_intel,snd_hda_codec_idt,snd_hda_codec_generic
pcmcia                 61440  0
cfg80211              602112  2 b43,mac80211
joydev                 20480  0
input_leds             16384  0
serio_raw              16384  0
snd_hda_core           81920  4 snd_hda_intel,snd_hda_codec,snd_hda_codec_idt,snd_hda_codec_generic
snd_hwdep              16384  1 snd_hda_codec
snd_pcm               102400  3 snd_hda_intel,snd_hda_codec,snd_hda_core
yenta_socket           49152  0
pcmcia_rsrc            20480  1 yenta_socket
pcmcia_core            24576  3 yenta_socket,pcmcia,pcmcia_rsrc
snd_timer              32768  1 snd_pcm
snd                    77824  13 snd_hda_intel,snd_hwdep,snd_hda_codec,snd_hda_codec_idt,snd_timer,snd_hda_codec_generic,snd_pcm
soundcore              16384  1 snd
i2c_piix4              24576  0
mac_hid                16384  0
shpchp                 36864  0
parport_pc             32768  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,parport_pc,ppdev
ip_tables              24576  0
x_tables               36864  1 ip_tables
autofs4                40960  2
pata_acpi              16384  0
usbhid                 53248  0
amdkfd                139264  1
hid                   114688  2 hid_ntrig,usbhid
amd_iommu_v2           20480  1 amdkfd
radeon               1507328  2
ssb_hcd                16384  0
i2c_algo_bit           16384  1 radeon
ttm                    98304  1 radeon
drm_kms_helper        151552  1 radeon
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
firewire_ohci          40960  0
fb_sys_fops            16384  1 drm_kms_helper
tg3                   163840  0
drm                   352256  5 radeon,ttm,drm_kms_helper
psmouse               139264  0
sdhci_pci              28672  0
firewire_core          65536  1 firewire_ohci
sdhci                  45056  1 sdhci_pci
crc_itu_t              16384  1 firewire_core
ptp                    20480  1 tg3
pata_atiixp            16384  1
pps_core               20480  1 ptp
ssb                    57344  2 b43,ssb_hcd
wmi                    16384  1 dell_wmi
video                  40960  2 dell_wmi,dell_laptop
```

Thanks

---

### Post by praseodym on 2017-08-12
Looks like Broadcom devices. Download this firmware file (somehow) and save it in "Downloads":

[https://media-cdn.ubuntu-de.org/forum/attachments/04/32/2480236-Broadcom_Firmware.tar.gz](https://media-cdn.ubuntu-de.org/forum/attachments/04/32/2480236-Broadcom_Firmware.tar.gz)

Installation:
```

sudo tar xvf ~/Downloads/2480236-Broadcom_Firmware.tar.gz -C /lib/firmware/ 
```
Reboot

---

### Post by Mryl on 2017-08-12
Wireless and ethernet working great
Thanks everyone!

---

### Post by wildmanne39 on 2017-08-12
Glad it is working, please use thread tools at the top of the page to mark the thread solved.

Thanks

---

