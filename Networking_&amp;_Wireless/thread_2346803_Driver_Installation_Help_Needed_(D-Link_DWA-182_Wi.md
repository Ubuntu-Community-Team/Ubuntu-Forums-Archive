---
title: "Driver Installation Help Needed (D-Link DWA-182 Wireless USB Adapter)"
date: 2016-12-18
forum: Networking &amp; Wireless
---

### Post by awittyname on 2016-12-18
Good afternoon,

I recently installed Ubuntu for my desktop to Dual-Boot with Windows 7, but for some odd reason I can't install the drivers for my wireless USB adapter. I downloaded the 4.3.2 Linux driver to a flash drive and I also have the CD on standby, but neither attempting to run the install.sh file on the drive or manually activating the autorun file on the CD seems to do anything. Any help?

---

### Post by wildmanne39 on 2016-12-18
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

### Post by awittyname on 2016-12-18
Here is the output; for some odd reason the word "net" always appeared in red, if that's pertinent to the scenario.

```
 johnpeter@johnpeter-Lenovo-Product:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=16.04
DISTRIB_CODENAME=xenial
DISTRIB_DESCRIPTION="Ubuntu 16.04.1 LTS"
Linux johnpeter-Lenovo-Product 4.4.0-31-generic #50-Ubuntu SMP Wed Jul 13 00:07:12 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux
johnpeter@johnpeter-Lenovo-Product:~$ lspci -nnk | grep -iA2 net
00:19.0 Ethernet controller [0200]: Intel Corporation 82579V Gigabit Network Connection [8086:1503] (rev 05)
    DeviceName:  Onboard LAN
    Subsystem: Lenovo 82579V Gigabit Network Connection [17aa:3611]
    Kernel driver in use: e1000e
    Kernel modules: e1000e
johnpeter@johnpeter-Lenovo-Product:~$ lsusb
Bus 002 Device 006: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
Bus 002 Device 005: ID 04a9:10d3 Canon, Inc. 
Bus 002 Device 004: ID 0951:1643 Kingston Technology DataTraveler G3
Bus 002 Device 003: ID 2001:3315 D-Link Corp. 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 05e3:0716 Genesys Logic, Inc. USB 2.0 Multislot Card Reader/Writer
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
johnpeter@johnpeter-Lenovo-Product:~$ iwconfig
lo        no wireless extensions.

eno1      no wireless extensions.

johnpeter@johnpeter-Lenovo-Product:~$ rfkill list all
johnpeter@johnpeter-Lenovo-Product:~$ lsmod
Module                  Size  Used by
nls_utf8               16384  1
nls_iso8859_1          16384  1
udf                    94208  1
crc_itu_t              16384  1 udf
snd_hda_codec_hdmi     53248  4
snd_hda_codec_realtek    86016  1
snd_hda_codec_generic    77824  1 snd_hda_codec_realtek
snd_hda_intel          36864  5
snd_hda_codec         135168  4 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel
snd_hda_core           73728  5 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel
intel_rapl             20480  0
usblp                  20480  0
snd_hwdep              16384  1 snd_hda_codec
x86_pkg_temp_thermal    16384  0
snd_pcm               106496  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_core
intel_powerclamp       16384  0
coretemp               16384  0
snd_seq_midi           16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            32768  1 snd_seq_midi
kvm_intel             172032  0
snd_seq                69632  2 snd_seq_midi_event,snd_seq_midi
gpio_ich               16384  0
kvm                   536576  1 kvm_intel
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
irqbypass              16384  1 kvm
snd_timer              32768  2 snd_pcm,snd_seq
snd                    81920  21 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
crct10dif_pclmul       16384  0
crc32_pclmul           16384  0
soundcore              16384  1 snd
aesni_intel           167936  0
aes_x86_64             20480  1 aesni_intel
lrw                    16384  1 aesni_intel
gf128mul               16384  1 lrw
mei_me                 36864  0
mei                    98304  1 mei_me
shpchp                 36864  0
glue_helper            16384  1 aesni_intel
lpc_ich                24576  0
ablk_helper            16384  1 aesni_intel
input_leds             16384  0
8250_fintek            16384  0
mac_hid                16384  0
cryptd                 20480  2 aesni_intel,ablk_helper
serio_raw              16384  0
parport_pc             32768  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,ppdev,parport_pc
autofs4                40960  2
hid_generic            16384  0
usbhid                 49152  0
hid                   118784  2 hid_generic,usbhid
uas                    24576  0
usb_storage            69632  2 uas
nouveau              1495040  6
mxm_wmi                16384  1 nouveau
video                  40960  1 nouveau
i2c_algo_bit           16384  1 nouveau
ttm                    94208  1 nouveau
drm_kms_helper        147456  1 nouveau
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
fb_sys_fops            16384  1 drm_kms_helper
e1000e                237568  0
ahci                   36864  3
drm                   360448  9 ttm,drm_kms_helper,nouveau
libahci                32768  1 ahci
ptp                    20480  1 e1000e
pps_core               20480  1 ptp
fjes                   28672  0
wmi                    20480  2 mxm_wmi,nouveau 
```

---

### Post by wildmanne39 on 2016-12-18
The reason I did not tell you how to install the driver from your disk is because they never work. Please do:
```
sudo apt-get update
sudo apt-get install rtl8812au-dkms
```
Reboot and let us know if it is working, if you have secure boot turned on you will need to turn it off before you install the driver, and you will need to leave it off.
Thanks

---

### Post by wildmanne39 on 2016-12-18
*Thread moved to **Networking & Wireless**.*

---

### Post by awittyname on 2016-12-19
Attempted the commands, here is what the terminal spat out;

```
 johnpeter@johnpeter-Lenovo-Product:~$ sudo apt-get update
[sudo] password for johnpeter: 
Err:1 http://us.archive.ubuntu.com/ubuntu xenial InRelease
  Temporary failure resolving 'us.archive.ubuntu.com'
Err:2 http://security.ubuntu.com/ubuntu xenial-security InRelease
  Temporary failure resolving 'security.ubuntu.com'
Err:3 http://us.archive.ubuntu.com/ubuntu xenial-updates InRelease
  Temporary failure resolving 'us.archive.ubuntu.com'
Err:4 http://us.archive.ubuntu.com/ubuntu xenial-backports InRelease
  Temporary failure resolving 'us.archive.ubuntu.com'
Reading package lists... Done
W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/xenial/InRelease  Temporary failure resolving 'us.archive.ubuntu.com'
W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/xenial-updates/InRelease  Temporary failure resolving 'us.archive.ubuntu.com'
W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/xenial-backports/InRelease  Temporary failure resolving 'us.archive.ubuntu.com'
W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/xenial-security/InRelease  Temporary failure resolving 'security.ubuntu.com'
W: Some index files failed to download. They have been ignored, or old ones used instead.
johnpeter@johnpeter-Lenovo-Product:~$ sudo apt-get install rtl8812au-dkms
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package rtl8812au-dkms


```

I'm guessing this is due to the fact that I don't have a wired connection to download the drivers for the wireless card. Anything else I can try?

---

### Post by wildmanne39 on 2016-12-19
Indeed that is the reason, you need an internet connect but you can connect your cell phone through the usb port and use it as a tetherings device that works great.

---

### Post by awittyname on 2016-12-19
Ah! Thank you so much, I hadn't thought of tethering my phone's hotspot. I was able to install the drivers correctly, thank you for your help and patience!

---

### Post by wildmanne39 on 2016-12-19
Your welcome!
Enjoy!

---

