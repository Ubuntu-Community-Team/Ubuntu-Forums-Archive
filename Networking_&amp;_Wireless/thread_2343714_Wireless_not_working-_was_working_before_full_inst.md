---
title: "Wireless not working- was working before full install"
date: 2016-11-18
forum: Networking &amp; Wireless
---

### Post by AttentionDesperate on 2016-11-18
I've installed ubuntu on my PC. I need help getting the internet to work. I have a wifi card built into my PC. During the installation the wifi was working fine, but I restarted the computer like it asked and the the wifi broke. 

If you could tell me the basic procedure for troubleshooting this problem, so that I can work through it and post my findings.

---

### Post by wildmanne39 on 2016-11-18
Hi, please click on the wireless script in my signature and follow the directions for running the script and posting the results here. 
Thanks

---

### Post by AttentionDesperate on 2016-11-18
> **Wild Man said:**
> Hi, please click on the wireless script in my signature and follow the directions for running the script and posting the results here. 
Thanks

I don't have access to a wired connection.

---

### Post by wildmanne39 on 2016-11-18
Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

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

### Post by AttentionDesperate on 2016-11-18
note that I also have a usb adapter plugged in, and I don't know if it's functional. The main hardware is the wireless card built-into the PC.

```
cat /etc/lsb-release; uname -aDISTRIB_ID=Ubuntu
DISTRIB_RELEASE=16.04
DISTRIB_CODENAME=xenial
DISTRIB_DESCRIPTION="Ubuntu 16.04.1 LTS"
Linux isaac-500-056 4.4.0-47-generic #68-Ubuntu SMP Wed Oct 26 19:39:52 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux


lspci -nnk | grep -iA2 net
01:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8161 Gigabit Ethernet [1969:1091] (rev 10)
	Subsystem: Hewlett-Packard Company AR8161 Gigabit Ethernet [103c:2ae0]
	Kernel driver in use: alx
	Kernel modules: alx
04:00.0 Network controller [0280]: Ralink corp. RT3290 Wireless 802.11n 1T/1R PCIe [1814:3290]
	Subsystem: Hewlett-Packard Company Ralink RT3290LE 802.11bgn 1x1 Wi-Fi and Bluetooth 4.0 Combo Adapter [103c:18ec]
	Kernel driver in use: rt2800pci


lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 1a2c:0021 China Resource Semico Co., Ltd Keyboard
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 093a:2521 Pixart Imaging, Inc. Optical Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 008 Device 002: ID 0781:5530 SanDisk Corp. Cruzer
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 006 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


iwconfig
lo        no wireless extensions.


enp1s0    no wireless extensions.


wlp4s0f0  IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off


rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no


lsbmod
No command 'lsbmod' found, did you mean:
 Command 'lsmod' from package 'kmod' (main)
lsbmod: command not found
isaac@isaac-500-056:~$ lsmod
Module                  Size  Used by
uas                    24576  0
usb_storage            69632  2 uas
nls_utf8               16384  0
isofs                  40960  0
drbg                   32768  1
ansi_cprng             16384  0
dm_crypt               28672  1
nls_iso8859_1          16384  2
snd_hda_codec_idt      57344  1
kvm_amd                65536  0
input_leds             16384  0
arc4                   16384  2
rt2800pci              16384  0
rt2800mmio             20480  1 rt2800pci
snd_hda_codec_generic    77824  1 snd_hda_codec_idt
kvm                   540672  1 kvm_amd
rt2800lib              94208  2 rt2800pci,rt2800mmio
joydev                 20480  0
irqbypass              16384  1 kvm
hp_wmi                 16384  0
snd_hda_intel          40960  3
rt2x00pci              16384  1 rt2800pci
sparse_keymap          16384  1 hp_wmi
rt2x00mmio             16384  2 rt2800pci,rt2800mmio
crct10dif_pclmul       16384  0
snd_hda_codec         135168  3 snd_hda_codec_idt,snd_hda_codec_generic,snd_hda_intel
rt2x00lib              57344  5 rt2x00pci,rt2800lib,rt2800pci,rt2800mmio,rt2x00mmio
snd_hda_core           73728  4 snd_hda_codec_idt,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel
crc32_pclmul           16384  0
snd_hwdep              16384  1 snd_hda_codec
mac80211              737280  3 rt2x00lib,rt2x00pci,rt2800lib
aesni_intel           167936  375
cfg80211              565248  2 mac80211,rt2x00lib
aes_x86_64             20480  1 aesni_intel
lrw                    16384  1 aesni_intel
snd_pcm               106496  3 snd_hda_codec,snd_hda_intel,snd_hda_core
snd_seq_midi           16384  0
eeprom_93cx6           16384  1 rt2800pci
gf128mul               16384  1 lrw
glue_helper            16384  1 aesni_intel
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            32768  1 snd_seq_midi
snd_seq                69632  2 snd_seq_midi_event,snd_seq_midi
ablk_helper            16384  1 aesni_intel
crc_ccitt              16384  1 rt2800lib
cryptd                 20480  189 aesni_intel,ablk_helper
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              32768  2 snd_pcm,snd_seq
snd                    81920  16 snd_hwdep,snd_timer,snd_hda_codec_idt,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
soundcore              16384  1 snd
serio_raw              16384  0
shpchp                 36864  0
k10temp                16384  0
i2c_piix4              24576  0
mac_hid                16384  0
parport_pc             32768  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,ppdev,parport_pc
autofs4                40960  2
hid_generic            16384  0
usbhid                 49152  0
hid                   118784  2 hid_generic,usbhid
amdkfd                131072  1
amd_iommu_v2           20480  1 amdkfd
radeon               1515520  3
i2c_algo_bit           16384  1 radeon
psmouse               126976  0
ttm                    94208  1 radeon
drm_kms_helper        155648  1 radeon
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
fb_sys_fops            16384  1 drm_kms_helper
drm                   364544  6 ttm,drm_kms_helper,radeon
alx                    36864  0
mdio                   16384  1 alx
ahci                   36864  3
libahci                32768  1 ahci
wmi                    20480  1 hp_wmi
fjes                   28672  0







```

---

### Post by wildmanne39 on 2016-11-18
Please do:
```
echo "options rt2800pci nohwcrypt=1" | sudo tee /etc/modprobe.d/rt2800pci.conf
sudo modprobe -rfv rt2800pci
sudo modprobe -v rt2800pci
```
if it does not come on shutdown your computer and remove the usb adapter then boot back up.
Thanks

---

### Post by AttentionDesperate on 2016-11-18
ran it

the first two output the same "command not found", not sure why it didn't copy over

```
isaac@isaac-500-056:~$ echo "options rt2800pci nohwcrypt=1" | sudo tee/etc/modprobe.d/rt2800pci.conf
sudo: tee/etc/modprobe.d/rt2800pci.conf: command not found
isaac@isaac-500-056:~$ sudo modprobe -rfv rt2800pci
rmmod rt2800pci
rmmod eeprom_93cx6
rmmod rt2x00pci
rmmod rt2800mmio
rmmod rt2x00mmio
rmmod rt2800lib
rmmod crc_ccitt
rmmod rt2x00lib
rmmod mac80211
rmmod cfg80211



```

---

### Post by AttentionDesperate on 2016-11-18
had to fix that code

**hold on im not sure what happened **

---

### Post by AttentionDesperate on 2016-11-18
> **Wild Man said:**
> Please do:
```
echo "options rt2800pci nohwcrypt=1" | sudo tee /etc/modprobe.d/rt2800pci.conf
sudo modprobe -rfv rt2800pci
sudo modprobe -v rt2800pci
```
if it does not come on shutdown your computer and remove the usb adapter then boot back up.
Thanks

Ok
```
echo "options rt2800pci nohwcrypt=1" | sudo tee /etc/modprobe.d/rt2800pci.confoptions rt2800pci nohwcrypt=1


sudo modprobe -v rt2800pci
insmod /lib/modules/4.4.0-47-generic/kernel/lib/crc-ccitt.ko 
insmod /lib/modules/4.4.0-47-generic/kernel/drivers/misc/eeprom/eeprom_93cx6.ko 
insmod /lib/modules/4.4.0-47-generic/kernel/net/wireless/cfg80211.ko 
insmod /lib/modules/4.4.0-47-generic/kernel/net/mac80211/mac80211.ko 
insmod /lib/modules/4.4.0-47-generic/kernel/drivers/net/wireless/rt2x00/rt2x00lib.ko 
insmod /lib/modules/4.4.0-47-generic/kernel/drivers/net/wireless/rt2x00/rt2x00mmio.ko 
insmod /lib/modules/4.4.0-47-generic/kernel/drivers/net/wireless/rt2x00/rt2x00pci.ko 
insmod /lib/modules/4.4.0-47-generic/kernel/drivers/net/wireless/rt2x00/rt2800lib.ko 
insmod /lib/modules/4.4.0-47-generic/kernel/drivers/net/wireless/rt2x00/rt2800mmio.ko 
insmod /lib/modules/4.4.0-47-generic/kernel/drivers/net/wireless/rt2x00/rt2800pci.ko 




isaac@isaac-500-056:~$ sudo modprobe -rfv rt2800pci
rmmod rt2800pci
rmmod eeprom_93cx6
rmmod rt2x00pci
rmmod rt2800mmio
rmmod rt2x00mmio
rmmod rt2800lib
rmmod crc_ccitt
rmmod rt2x00lib
rmmod mac80211
rmmod cfg80211



```

---

### Post by wildmanne39 on 2016-11-18
Please do:
```
sudo modprobe -v rt2800pci
```
Thanks

---

### Post by AttentionDesperate on 2016-11-18
> **Wild Man said:**
> Please do:
```
sudo modprobe -v rt2800pci
```
Thanks

Its above

---

### Post by wildmanne39 on 2016-11-18
Does it work now? did you restart?
I have to leave for awhile hopefully someone will help you while I am out.

---

### Post by AttentionDesperate on 2016-11-18
Still not working. It says "device not ready" under Wi-Fi networks (also greyed out).

---

### Post by AttentionDesperate on 2016-11-18
It started working unexpectedly

i was planning on reinstalling because it was working during install but during trying to get the install to come up (had install disc but wasn't being read) about the third restart the wifi started working

---

### Post by wildmanne39 on 2016-11-18
Glad it is working!
Enjoy!

---

