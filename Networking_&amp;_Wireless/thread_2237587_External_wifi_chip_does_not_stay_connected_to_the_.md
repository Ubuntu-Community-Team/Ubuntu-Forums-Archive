---
title: "External wifi chip does not stay connected to the internet"
date: 2014-08-02
forum: Networking &amp; Wireless
---

### Post by gretha2 on 2014-08-02
I have a Lenovo t440s laptop and I have dual booted Ubuntu 14.04.1 and Windows 8.1. The internal wifi chip is not recognized by ubuntu so I bought an Edimax EW-7811Un. It connects to my wifi for about 3 minutes and disconnects. If I unplug the edimax and plug it back in, it works for another 3 minutes. What can I do to make the connection more stable?

---

### Post by praseodym on 2014-08-02
Please open a terminal with CTRL+ALT+T and show the outputs of these commands:
```

lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
rfkill list
```
Does LAN work?

---

### Post by mikewhatever on 2014-08-02
Here is the bug report: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/852190](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/852190)
It's been three years, and the in kernel driver still doesn't work well.

---

### Post by praseodym on 2014-08-02
That Edimax stick should work with this driver change:

[http://forum.ubuntuusers.de/topic/wlan-stick-524440/3/#Realtek-rtl8192cu-s-Treiber-fuer-12-04-4-und-13-10-fuer-Kernel-3-11](http://forum.ubuntuusers.de/topic/wlan-stick-524440/3/#Realtek-rtl8192cu-s-Treiber-fuer-12-04-4-und-13-10-fuer-Kernel-3-11)

But there should also be an internal card...

---

### Post by gretha2 on 2014-08-02
Please open a terminal with CTRL+ALT+T and show the outputs of these commands:
 	Code:
 	lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
rfkill list 
Does LAN work?


gretha@gds:~$ lspci -nnk | grep -iA2 net
00:19.0 Ethernet controller [0200]: Intel Corporation Ethernet Connection I218-LM [8086:155a] (rev 04)
    Subsystem: Lenovo Device [17aa:2214]
    Kernel driver in use: e1000e
--
03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8192EE PCIe Wireless Network Adapter [10ec:818b]
    Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:001b]
gretha@gds:~$ lsusb
Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 004: ID 04f2:b39a Chicony Electronics Co., Ltd 
Bus 002 Device 002: ID 138a:0017 Validity Sensors, Inc. 
Bus 002 Device 010: ID 7392:7811 Edimax Technology Co., Ltd EW-7811Un 802.11n Wireless Adapter [Realtek RTL8188CUS]
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
gretha@gds:~$ lsmod
Module                  Size  Used by
arc4                   12608  2 
rtl8192cu              67723  0 
rtl_usb                18448  1 rtl8192cu
rtlwifi                63475  2 rtl_usb,rtl8192cu
rtl8192c_common        53172  1 rtl8192cu
mac80211              630653  3 rtl_usb,rtlwifi,rtl8192cu
cfg80211              484040  2 mac80211,rtlwifi
rfcomm                 69160  0 
bnep                   19624  2 
nls_iso8859_1          12713  1 
snd_hda_codec_hdmi     46254  1 
snd_hda_codec_realtek    61438  1 
uvcvideo               80885  0 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
videobuf2_core         40664  1 uvcvideo
videodev              134688  2 uvcvideo,videobuf2_core
intel_rapl             18773  0 
x86_pkg_temp_thermal    14205  0 
intel_powerclamp       14705  0 
coretemp               13435  0 
kvm                   451511  0 
crct10dif_pclmul       14289  0 
crc32_pclmul           13113  0 
ghash_clmulni_intel    13216  0 
aesni_intel            55624  0 
aes_x86_64             17131  1 aesni_intel
lrw                    13286  1 aesni_intel
gf128mul               14951  1 lrw
glue_helper            13990  1 aesni_intel
ablk_helper            13597  1 aesni_intel
cryptd                 20359  3 ghash_clmulni_intel,aesni_intel,ablk_helper
thinkpad_acpi          81013  1 
joydev                 17381  0 
nvram                  14411  1 thinkpad_acpi
serio_raw              13462  0 
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
lpc_ich                21080  0 
mei_me                 18627  0 
mei                    82276  1 mei_me
btusb                  32412  0 
snd_hda_intel          52355  12 
bluetooth             391196  11 bnep,btusb,rfcomm
snd_hda_codec         192906  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_rawmidi            30144  1 snd_seq_midi
snd_hwdep              13602  1 snd_hda_codec
snd_pcm               102099  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
wmi                    19177  0 
snd_timer              29482  2 snd_pcm,snd_seq
snd                    69238  35 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,thinkpad_acpi,snd_seq_device,snd_seq_midi
i915                  783805  8 
soundcore              12680  1 snd
video                  19476  1 i915
drm_kms_helper         53081  1 i915
intel_smartconnect     12619  0 
drm                   303102  7 i915,drm_kms_helper
mac_hid                13205  0 
i2c_algo_bit           13413  1 i915
parport_pc             32701  0 
ppdev                  17671  0 
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
e1000e                254433  0 
psmouse               106678  0 
ahci                   25819  4 
ptp                    18933  1 e1000e
libahci                32560  1 ahci
rtsx_pci               45956  0 
pps_core               19382  1 ptp
gretha@gds:~$ iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"LFWN1"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:1F:90:E9:2A:B0   
          Bit Rate=18 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=30/70  Signal level=-80 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:149   Missed beacon:0

gretha@gds:~$ rfkill list
1: tpacpi_bluetooth_sw: Bluetooth
    Soft blocked: yes
    Hard blocked: no
7: phy5: Wireless LAN
    Soft blocked: no
    Hard blocked: no

 LAN does work

---

### Post by praseodym on 2014-08-03
Change the driver for the stick:

```
sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms git 
git clone https://github.com/pvaret/rtl8192cu-fixes.git
sudo dkms add ./rtl8192cu-fixes
sudo dkms install 8192cu/1.9
echo "blacklist rtl8192cu" | sudo tee -a /etc/modprobe.d/blacklist.conf   
```
Reload the driver:
```

sudo modprobe -rv rtl8192cu
sudo modprobe -v 8192cu
```
Replug the stick. Then load the driver for the internal card:
```

sudo modprobe -v rtl8188ee
```
and check the outputs of:
```

ifconfig -a
iwconfig
iwlist chan
lsmod
sudo iwlist scan
dmesg | egrep 'rtl8|8192'
grep rtl8 /etc/modprobe.d/*
cat /etc/modules
```

---

### Post by gretha2 on 2014-08-03
> **praseodym said:**
> Change the driver for the stick:

```
sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms git 
git clone https://github.com/pvaret/rtl8192cu-fixes.git
sudo dkms add ./rtl8192cu-fixes
sudo dkms install 8192cu/1.9
echo "blacklist rtl8192cu" | sudo tee -a /etc/modprobe.d/blacklist.conf   
```
Reload the driver:
```

sudo modprobe -rv rtl8192cu
sudo modprobe -v 8192cu
```
Replug the stick. Then load the driver for the internal card:
```

sudo modprobe -v rtl8188ee
```
and check the outputs of:
```

ifconfig -a
iwconfig
iwlist chan
lsmod
sudo iwlist scan
dmesg | egrep 'rtl8|8192'
grep rtl8 /etc/modprobe.d/*
cat /etc/modules
```

gretha@gds:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 28:d2:44:89:7f:d4  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:5312 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4113 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6996971 (6.9 MB)  TX bytes:374546 (374.5 KB)
          Interrupt:20 Memory:f0600000-f0620000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:455 errors:0 dropped:0 overruns:0 frame:0
          TX packets:455 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:40614 (40.6 KB)  TX bytes:40614 (40.6 KB)

wlan0     Link encap:Ethernet  HWaddr 80:1f:02:f5:27:a6  
          inet addr:192.168.1.10  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::821f:2ff:fef5:27a6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:70 errors:0 dropped:5 overruns:0 frame:0
          TX packets:111 errors:0 dropped:2 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:15067 (15.0 KB)  TX bytes:20298 (20.2 KB)

gretha@gds:~$ iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"LFWN1"  Nickname:"<WIFI@REALTEK>"
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:1F:90:E9:2A:B0   
          Bit Rate:54 Mb/s   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=100/100  Signal level=96/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

gretha@gds:~$ iwlist chan
eth0      no frequency information.

lo        no frequency information.

wlan0     11 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Current Frequency:2.412 GHz (Channel 1)

gretha@gds:~$ lsmod
Module                  Size  Used by
rtl8188ee              89677  0 
rtl_pci                26690  1 rtl8188ee
rtlwifi                63475  2 rtl_pci,rtl8188ee
mac80211              630653  3 rtl_pci,rtlwifi,rtl8188ee
cfg80211              484040  2 mac80211,rtlwifi
8192cu                527283  0 
rfcomm                 69160  0 
bnep                   19624  2 
nls_iso8859_1          12713  1 
snd_hda_codec_hdmi     46254  1 
snd_hda_codec_realtek    61438  1 
uvcvideo               80885  0 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
videobuf2_core         40664  1 uvcvideo
videodev              134688  2 uvcvideo,videobuf2_core
snd_hda_intel          52355  5 
snd_hda_codec         192906  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm               102099  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
thinkpad_acpi          81013  1 
nvram                  14411  1 thinkpad_acpi
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30144  1 snd_seq_midi
intel_rapl             18773  0 
x86_pkg_temp_thermal    14205  0 
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
intel_powerclamp       14705  0 
coretemp               13435  0 
kvm                   451511  0 
crct10dif_pclmul       14289  0 
crc32_pclmul           13113  0 
ghash_clmulni_intel    13216  0 
aesni_intel            55624  0 
aes_x86_64             17131  1 aesni_intel
lrw                    13286  1 aesni_intel
gf128mul               14951  1 lrw
glue_helper            13990  1 aesni_intel
ablk_helper            13597  1 aesni_intel
cryptd                 20359  3 ghash_clmulni_intel,aesni_intel,ablk_helper
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
joydev                 17381  0 
serio_raw              13462  0 
snd_timer              29482  2 snd_pcm,snd_seq
snd                    69238  22 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,thinkpad_acpi,snd_seq_device,snd_seq_midi
rtsx_pci_ms            18151  0 
btusb                  32412  0 
bluetooth             391196  11 bnep,btusb,rfcomm
lpc_ich                21080  0 
memstick               16966  1 rtsx_pci_ms
mei_me                 18627  0 
mei                    82276  1 mei_me
wmi                    19177  0 
soundcore              12680  1 snd
i915                  783805  5 
video                  19476  1 i915
drm_kms_helper         53081  1 i915
mac_hid                13205  0 
intel_smartconnect     12619  0 
drm                   303102  4 i915,drm_kms_helper
i2c_algo_bit           13413  1 i915
parport_pc             32701  0 
ppdev                  17671  0 
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
rtsx_pci_sdmmc         23274  0 
e1000e                254433  0 
psmouse               106678  0 
ahci                   25819  4 
ptp                    18933  1 e1000e
libahci                32560  1 ahci
rtsx_pci               45956  2 rtsx_pci_ms,rtsx_pci_sdmmc
pps_core               19382  1 ptp
gretha@gds:~$ sudo iwlist scan
eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:1F:90:E9:2A:B0
                    ESSID:"LFWN1"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Quality=100/100  Signal level=95/100  

gretha@gds:~$ dmesg | egrep 'rtl8|8192'
[    0.000000] PERCPU: Embedded 29 pages/cpu @ffff88031e200000 s86336 r8192 d24256 u262144
[    0.000000] pcpu-alloc: s86336 r8192 d24256 u262144 alloc=1*2097152
[    0.458648] UDP hash table entries: 8192 (order: 6, 262144 bytes)
[    0.458779] UDP-Lite hash table entries: 8192 (order: 6, 262144 bytes)
[  411.665023] 8192cu: module verification failed: signature and/or  required key missing - tainting kernel
[  411.667499] usbcore: registered new interface driver rtl8192cu
gretha@gds:~$ grep rtl8 /etc/modprobe.d/*
/etc/modprobe.d/blacklist.conf:blacklist rtl8192cu
/etc/modprobe.d/blacklist.conf:blacklist rtl8192cu
gretha@gds:~$ cat /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.
# Parameters can be specified after the module name.

lp
rtc

edit: connection seems to be stable now.

---

### Post by praseodym on 2014-08-04
Are you connected via internal card?

```
cat /etc/udev/rules.d/70-persistent-net.rules
arp -v
```

---

### Post by varunendra on 2014-08-04
While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Use Code Tags" link in my signature.

---

