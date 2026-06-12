---
title: "Slow Wifi + Connected and No internet access"
date: 2017-02-10
forum: Networking &amp; Wireless
---

### Post by iam4war on 2017-02-10
Hi, 

I am new to Ubuntu, I have installed Ubuntu 16.04 LTS on my Acer E5-575 notebook. There are two problems 1. Wifi is very slow 2. Even though it is connected but there is no internet.

I have tried the following tricks:
1. echo "options ath9k nohwcrypt=1" >> /etc/modprobe.d/ath9k.conf
2.sudo gedit /etc/nsswitch.conf and  hosts:          files dns
3. Turned off power management
4. Disabled ipv6

Here is the output of some commands:
```
cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=16.04
DISTRIB_CODENAME=xenial
DISTRIB_DESCRIPTION="Ubuntu 16.04.1 LTS"
Linux machine-learning 4.4.0-62-generic #83-Ubuntu SMP Wed Jan 18 14:10:15 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux

lspci -nnk | grep -iA2 net

02:00.0 Network controller [0280]: Qualcomm Atheros Device [168c:0042] (rev 31)
    Subsystem: Lite-On Communications Inc Device [11ad:08a6]
    Kernel driver in use: ath10k_pci
--
03:00.1 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 12)
    Subsystem: Acer Incorporated [ALI] RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [1025:1094]
    Kernel driver in use: r8169
    Kernel modules: r8169

iwconfig

enp3s0f1  no wireless extensions.

lo        no wireless extensions.

wlp2s0    IEEE 802.11abgn  ESSID:"TheVeryEndOfYou"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: E4:6F:13:B5:32:BA   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=38/70  Signal level=-72 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1116  Invalid misc:847   Missed beacon:0



rfkill list all
0: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: acer-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
lsmod
Module                  Size  Used by
rfcomm                 69632  2
drbg                   32768  1
ansi_cprng             16384  0
ctr                    16384  2
ccm                    20480  2
bnep                   20480  2
arc4                   16384  2
nls_iso8859_1          16384  1
snd_hda_codec_hdmi     53248  1
snd_hda_codec_realtek    86016  1
snd_hda_codec_generic    77824  1 snd_hda_codec_realtek
snd_hda_intel          40960  3
snd_hda_codec         135168  4 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel
snd_hda_core           73728  5 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel
snd_hwdep              16384  1 snd_hda_codec
uvcvideo               90112  0
snd_pcm               106496  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_core
videobuf2_vmalloc      16384  1 uvcvideo
videobuf2_memops       16384  1 videobuf2_vmalloc
snd_seq_midi           16384  0
videobuf2_v4l2         28672  1 uvcvideo
videobuf2_core         36864  2 uvcvideo,videobuf2_v4l2
i2c_designware_platform    16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
i2c_designware_core    20480  1 i2c_designware_platform
snd_rawmidi            32768  1 snd_seq_midi
v4l2_common            16384  1 videobuf2_v4l2
ath10k_pci             45056  0
btusb                  45056  0
videodev              176128  4 uvcvideo,v4l2_common,videobuf2_core,videobuf2_v4l2
ath10k_core           311296  1 ath10k_pci
snd_seq                69632  2 snd_seq_midi_event,snd_seq_midi
x86_pkg_temp_thermal    16384  0
media                  24576  2 uvcvideo,videodev
coretemp               16384  0
acer_wmi               20480  0
sparse_keymap          16384  1 acer_wmi
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
btrtl                  16384  1 btusb
ath                    32768  1 ath10k_core
btbcm                  16384  1 btusb
btintel                16384  1 btusb
mac80211              737280  1 ath10k_core
kvm_intel             172032  0
cfg80211              565248  3 ath,mac80211,ath10k_core
bluetooth             520192  29 bnep,btbcm,btrtl,btusb,rfcomm,btintel
kvm                   540672  1 kvm_intel
irqbypass              16384  1 kvm
snd_timer              32768  2 snd_pcm,snd_seq
crct10dif_pclmul       16384  0
crc32_pclmul           16384  0
ghash_clmulni_intel    16384  0
mei_me                 36864  0
rtsx_pci_ms            20480  0
aesni_intel           167936  4
mei                    98304  1 mei_me
snd                    81920  17 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
memstick               20480  1 rtsx_pci_ms
aes_x86_64             20480  1 aesni_intel
lrw                    16384  1 aesni_intel
gf128mul               16384  1 lrw
idma64                 20480  0
glue_helper            16384  1 aesni_intel
ablk_helper            16384  1 aesni_intel
cryptd                 20480  3 ghash_clmulni_intel,aesni_intel,ablk_helper
virt_dma               16384  1 idma64
intel_lpss_pci         16384  0
input_leds             16384  0
shpchp                 36864  0
joydev                 20480  0
serio_raw              16384  0
soundcore              16384  1 snd
acpi_pad               24576  0
tpm_crb                16384  0
dell_smo8800           16384  0
intel_lpss_acpi        16384  0
intel_lpss             16384  2 intel_lpss_pci,intel_lpss_acpi
mac_hid                16384  0
parport_pc             32768  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,ppdev,parport_pc
autofs4                40960  2
rtsx_pci_sdmmc         24576  0
i915_bpo             1302528  6
intel_ips              20480  1 i915_bpo
i2c_algo_bit           16384  1 i915_bpo
drm_kms_helper        155648  1 i915_bpo
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
psmouse               131072  0
sysimgblt              16384  1 drm_kms_helper
fb_sys_fops            16384  1 drm_kms_helper
drm                   364544  7 i915_bpo,drm_kms_helper
r8169                  81920  0
rtsx_pci               53248  2 rtsx_pci_ms,rtsx_pci_sdmmc
ahci                   36864  3
mii                    16384  1 r8169
libahci                32768  1 ahci
i2c_hid                20480  0
hid                   118784  1 i2c_hid
wmi                    20480  1 acer_wmi
video                  40960  2 i915_bpo,acer_wmi
pinctrl_sunrisepoint    28672  0
pinctrl_intel          20480  1 pinctrl_sunrisepoint
fjes                   28672  0



```
Thank you!

---

### Post by wildmanne39 on 2017-02-10
Click on the wireless script in my signature and follow the directions for running it and posting the file it creates here using code tags.

You have tried some things that do not apply to your wifi card. 

Also confusing you say the wifi is slow, then you say you have no internet it.

---

### Post by iam4war on 2017-02-10
Sorry for the confusion, I can connect to the internet, when i boot my computer, the internet connection works but it is slow. After a while, the wifi is still connected but there is no internet. If I disconnect and the reconnect to the wifi network, it works again.

I have attached the results of the wireless script.

---

### Post by wildmanne39 on 2017-02-10
First to connect and actually use the wifi you have to unplug your ethernet connection because it overrides the wifi by default and it is using the wrong driver so that makes your connection very slow.

Let's turn power management of permanently:
```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf

```
We need to change your country code if you are in India please do:
```
sudo iw reg set IN
sudo sed -i 's/^REG.*=$/&IN/' /etc/default/crda
```
Let's do some house keeping:
```
sudo rm /etc/modprobe.d/ath9k.conf
```
Set your settings in network manager to match the screenshots:
Reboot

Make sure your ethernet is unplugged.

It looks like you may have a network manager bug but please do all the above and see how wifi is working if you are still having issues let us know if it is better or not and post a new file from the wireless script.

---

### Post by iam4war on 2017-02-10
Just one quick point, I don't have a wired connection at all. I only have wifi, maybe a bug. I will apply the settings, reboot and let you know.

The results are disappointing, it got worse. In fact, internet is unbearably slow. 
Please see the log. This time I was connected to wifi but not internet. I checked my mobile phone and I could access internet, but not from my laptop.

Also, I had deleted the Wired Connection before rebooting. But again I can see the ethernet connection. I don't have any wires attached to my laptop.

---

### Post by wildmanne39 on 2017-02-10
It is very late here I will research this issue tomorrow please leave all the settings the same maybe someone with more experience with this driver will step in.

---

### Post by iam4war on 2017-02-10
Meanwhile here is something that might be of some help:
```
lspci -nnk | grep -iA2 net; dmesg | grep ath10k

02:00.0 Network controller [0280]: Qualcomm Atheros Device [168c:0042] (rev 31)
    Subsystem: Lite-On Communications Inc Device [11ad:08a6]
    Kernel driver in use: ath10k_pci
--
03:00.1 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 12)
    Subsystem: Acer Incorporated [ALI] RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [1025:1094]
    Kernel driver in use: r8169
    Kernel modules: r8169
[   10.253148] ath10k_pci 0000:02:00.0: pci irq msi-x interrupts 8 irq_mode 0 reset_mode 0
[   10.684429] ath10k_pci 0000:02:00.0: Direct firmware load for ath10k/cal-pci-0000:02:00.0.bin failed with error -2
[   12.728674] ath10k_pci 0000:02:00.0: qca9377 hw1.1 (0x05020001, 0x003821ff sub 11ad:08a6) fw WLAN.TF.1.0-00267-1 fwapi 5 bdapi 2 htt-ver 3.1 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1 features ignore-otp
[   12.728679] ath10k_pci 0000:02:00.0: debug 0 debugfs 1 tracing 1 dfs 0 testmode 0
[   12.871265] ath10k_pci 0000:02:00.0 wlp2s0: renamed from wlan0
[  932.748019] ath10k_pci 0000:02:00.0: firmware crashed! 
[  932.748026] ath10k_pci 0000:02:00.0: qca9377 hw1.1 (0x05020001, 0x003821ff sub 11ad:08a6) fw WLAN.TF.1.0-00267-1 fwapi 5 bdapi 2 htt-ver 3.1 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1 features ignore-otp
[  932.748028] ath10k_pci 0000:02:00.0: debug 0 debugfs 1 tracing 1 dfs 0 testmode 0
[  932.750029] ath10k_pci 0000:02:00.0: firmware register dump:
[  932.750032] ath10k_pci 0000:02:00.0: [00]: 0x05020001 0x000015B3 0x00985B3A 0x00955B31
[  932.750033] ath10k_pci 0000:02:00.0: [04]: 0x00985B3A 0x00060730 0x00000004 0x00000001
[  932.750035] ath10k_pci 0000:02:00.0: [08]: 0x00955A00 0x00438A0C 0x004510FC 0x00420970
[  932.750036] ath10k_pci 0000:02:00.0: [12]: 0x00000009 0x00000000 0x00952CD0 0x00952CE6
[  932.750038] ath10k_pci 0000:02:00.0: [16]: 0x00952CC4 0x0091080D 0x00000000 0x0091080D
[  932.750039] ath10k_pci 0000:02:00.0: [20]: 0x40985B3A 0x0040E788 0x00400000 0x00421888
[  932.750040] ath10k_pci 0000:02:00.0: [24]: 0x809BF546 0x0040E7E8 0x00426470 0xC0985B3A
[  932.750042] ath10k_pci 0000:02:00.0: [28]: 0x809B90D8 0x0040E958 0x00000018 0x0042E9E8
[  932.750043] ath10k_pci 0000:02:00.0: [32]: 0x809B859A 0x0040E9A8 0x0040E9D0 0x00428D74
[  932.750044] ath10k_pci 0000:02:00.0: [36]: 0x8091D252 0x0040E9C8 0x00000000 0x00000002
[  932.750046] ath10k_pci 0000:02:00.0: [40]: 0x809EDD7B 0x0040EA78 0x00437544 0x00429428
[  932.750047] ath10k_pci 0000:02:00.0: [44]: 0x809EB6A6 0x0040EA98 0x00437544 0x00000001
[  932.750048] ath10k_pci 0000:02:00.0: [48]: 0x80911210 0x0040EAE8 0x00000010 0x004041D0
[  932.750049] ath10k_pci 0000:02:00.0: [52]: 0x80911154 0x0040EB28 0x00400000 0x00000000
[  932.750051] ath10k_pci 0000:02:00.0: [56]: 0x8091122D 0x0040EB48 0x00000000 0x00400600
[  934.715299] ath10k_pci 0000:02:00.0: device successfully recovered
```

---

### Post by wildmanne39 on 2017-02-10
Let's try a different driver:
```
sudo apt-get install git
git clone https://github.com/jeremyb31/ath10k-firmware.git
sudo cp ath10k-firmware/ /lib/firmware/ath10k/
```
code from here:
[https://ubuntuforums.org/showthread.php?t=2323812](https://ubuntuforums.org/showthread.php?t=2323812)

---

### Post by iam4war on 2017-02-11
The repository doesn't exist. Can you please check?

---

### Post by wildmanne39 on 2017-02-11
Let's try this driver:

```
sudo apt-get install --reinstall linux-headers-$(uname -r) build-essential
wget https://www.kernel.org/pub/linux/kernel/projects/backports/stable/v4.4.2/backports-4.4.2-1.tar.gz
tar -zxvf backports-4.4.2-1.tar.gz
cd backports-4.4.2-1
make defconfig-ath10k
make
sudo make install
```
After a kernel upgrade you will need to do this:
```
cd backports-4.4.2-1
make clean
make defconfig-ath10k
make
```
Reboot

---

### Post by iam4war on 2017-02-11
Not working.. 

```
dmesg | grep ath10k
[   10.362764] ath10k_pci 0000:02:00.0: pci irq msi-x interrupts 8 irq_mode 0 reset_mode 0
[   10.841270] ath10k_pci 0000:02:00.0: Direct firmware load for ath10k/cal-pci-0000:02:00.0.bin failed with error -2
[   13.417025] ath10k_pci 0000:02:00.0: qca9377 hw1.1 (0x05020001, 0x003821ff sub 11ad:08a6) fw WLAN.TF.1.0-00267-1 fwapi 5 bdapi 2 htt-ver 3.1 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1 features ignore-otp
[   13.417028] ath10k_pci 0000:02:00.0: debug 1 debugfs 1 tracing 0 dfs 0 testmode 0
[   13.558973] ath10k_pci 0000:02:00.0 wlp2s0: renamed from wlan0
[   29.486377] ath10k_pci 0000:02:00.0: no channel configured; ignoring frame(s)!
[  501.476256] ath10k_pci 0000:02:00.0: no channel configured; ignoring frame(s)!
[  501.478110] ath10k_pci 0000:02:00.0: no channel configured; ignoring frame(s)
```

---

### Post by jeremy31 on 2017-02-11
About the only thing I can think of is ```
sudo apt-get install --reinstall linux-firmware
```
It might help to move your wifi router to channel 1.  Check ```
iwconfig
``` results to confirm power management being off

---

