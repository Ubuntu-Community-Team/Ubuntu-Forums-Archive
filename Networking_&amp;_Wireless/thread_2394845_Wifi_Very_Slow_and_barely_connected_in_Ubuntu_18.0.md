---
title: "Wifi Very Slow and barely connected in Ubuntu 18.04 LTS. works perfectly windows 10"
date: 2018-06-22
forum: Networking &amp; Wireless
---

### Post by mjt07 on 2018-06-22
Hello, I have a dual boot windows 10 and ubunto 18.04 LTS. I can barely move my laptop from the router when on ubunto. Can anyone help please?

Thanks in advance.

Output of commands:

**mjt07@mjt07:~$ lspci -nnk |grep -iA2 net**
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [10ec:8136] (rev 07)
    Subsystem: Hewlett-Packard Company RTL810xE PCI Express Fast Ethernet controller [103c:8136]
    Kernel driver in use: r8169
    Kernel modules: r8169
03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter [10ec:b723]
    Subsystem: Hewlett-Packard Company RTL8723BE PCIe Wireless Network Adapter [103c:804c]
    Kernel driver in use: rtl8723be
    Kernel modules: rtl8723be

**mjt07@mjt07:~$ lsusb**
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 0c45:651b Microdia 
Bus 001 Device 002: ID 0bda:b006 Realtek Semiconductor Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

**mjt07@mjt07:~$ lsmod**
Module                  Size  Used by
rfcomm                 77824  4
ccm                    20480  3
bnep                   20480  2
nls_iso8859_1          16384  1
uvcvideo               86016  0
videobuf2_vmalloc      16384  1 uvcvideo
videobuf2_memops       16384  1 videobuf2_vmalloc
videobuf2_v4l2         24576  1 uvcvideo
videobuf2_core         40960  2 uvcvideo,videobuf2_v4l2
videodev              184320  3 uvcvideo,videobuf2_core,videobuf2_v4l2
media                  40960  2 uvcvideo,videodev
snd_hda_codec_hdmi     49152  1
snd_hda_codec_realtek   102400  1
snd_hda_codec_generic    73728  1 snd_hda_codec_realtek
snd_soc_skl            90112  0
snd_soc_skl_ipc        65536  1 snd_soc_skl
snd_hda_ext_core       24576  1 snd_soc_skl
snd_soc_sst_dsp        32768  1 snd_soc_skl_ipc
snd_soc_sst_ipc        16384  1 snd_soc_skl_ipc
snd_soc_acpi           16384  1 snd_soc_skl
intel_rapl             20480  0
snd_soc_core          241664  1 snd_soc_skl
x86_pkg_temp_thermal    16384  0
intel_powerclamp       16384  0
coretemp               16384  0
snd_compress           20480  1 snd_soc_core
ac97_bus               16384  1 snd_soc_core
kvm_intel             204800  0
snd_pcm_dmaengine      16384  1 snd_soc_core
snd_hda_intel          40960  6
kvm                   593920  1 kvm_intel
irqbypass              16384  1 kvm
snd_hda_codec         126976  4 snd_hda_intel,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec_realtek
crct10dif_pclmul       16384  0
snd_hda_core           81920  7 snd_hda_intel,snd_hda_codec,snd_hda_ext_core,snd_soc_skl,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec_realtek
snd_hwdep              20480  1 snd_hda_codec
crc32_pclmul           16384  0
ghash_clmulni_intel    16384  0
snd_pcm                98304  8 snd_hda_intel,snd_hda_codec,snd_pcm_dmaengine,snd_hda_ext_core,snd_hda_core,snd_soc_skl,snd_hda_codec_hdmi,snd_soc_core
snd_seq_midi           16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
pcbc                   16384  0
snd_rawmidi            32768  1 snd_seq_midi
processor_thermal_device    16384  0
int340x_thermal_zone    16384  1 processor_thermal_device
intel_soc_dts_iosf     16384  1 processor_thermal_device
aesni_intel           188416  2
snd_seq                65536  2 snd_seq_midi_event,snd_seq_midi
arc4                   16384  2
aes_x86_64             20480  1 aesni_intel
crypto_simd            16384  1 aesni_intel
glue_helper            16384  1 aesni_intel
cryptd                 24576  3 crypto_simd,ghash_clmulni_intel,aesni_intel
intel_cstate           20480  0
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              32768  2 snd_seq,snd_pcm
intel_rapl_perf        16384  0
rtl8723be              98304  0
btcoexist             131072  1 rtl8723be
rtl8723_common         24576  1 rtl8723be
rtl_pci                32768  1 rtl8723be
rtlwifi                77824  4 rtl_pci,btcoexist,rtl8723_common,rtl8723be
mac80211              778240  3 rtl_pci,rtlwifi,rtl8723be
input_leds             16384  0
joydev                 24576  0
wmi_bmof               16384  0
serio_raw              16384  0
snd                    81920  25 snd_compress,snd_hda_intel,snd_hwdep,snd_seq,snd_hda_codec,snd_timer,snd_rawmidi,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_seq_device,snd_hda_codec_realtek,snd_soc_core,snd_pcm
hp_wmi                 16384  0
sparse_keymap          16384  1 hp_wmi
btusb                  45056  0
btrtl                  16384  1 btusb
intel_wmi_thunderbolt    16384  0
btbcm                  16384  1 btusb
cfg80211              622592  2 mac80211,rtlwifi
btintel                16384  1 btusb
soundcore              16384  1 snd
bluetooth             548864  33 btrtl,btintel,bnep,btbcm,rfcomm,btusb
ecdh_generic           24576  1 bluetooth
mei_me                 40960  0
intel_pch_thermal      16384  0
mei                    90112  1 mei_me
shpchp                 36864  0
int3400_thermal        16384  0
acpi_pad              180224  0
acpi_thermal_rel       16384  1 int3400_thermal
mac_hid                16384  0
hp_wireless            16384  0
sch_fq_codel           20480  6
parport_pc             36864  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,parport_pc,ppdev
ip_tables              28672  0
x_tables               40960  1 ip_tables
autofs4                40960  2
amdgpu               2703360  0
chash                  16384  1 amdgpu
i915                 1617920  25
radeon               1470464  1
ttm                   106496  2 amdgpu,radeon
i2c_algo_bit           16384  3 amdgpu,radeon,i915
drm_kms_helper        167936  3 amdgpu,radeon,i915
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
fb_sys_fops            16384  1 drm_kms_helper
r8169                  86016  0
psmouse               147456  0
mii                    16384  1 r8169
drm                   401408  20 amdgpu,radeon,i915,ttm,drm_kms_helper
ahci                   36864  2
libahci                32768  1 ahci
wmi                    24576  3 wmi_bmof,intel_wmi_thunderbolt,hp_wmi
video                  40960  1 i915

**mjt07@mjt07:~$ iwconfig**
lo        no wireless extensions.

enp2s0    no wireless extensions.

wlp3s0    IEEE 802.11  ESSID:"03/880 879 Unlimited 4MB"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:25:86:B9:36:72   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:on
          Link Quality=48/70  Signal level=-62 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:12545   Missed beacon:0
[B]
mjt07@mjt07:~$ ifconfig -a[/B]
enp2s0: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        ether 70:5a:0f:5f:ed:52  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 11863  bytes 1121692 (1.1 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 11863  bytes 1121692 (1.1 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

wlp3s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.1.100  netmask 255.255.255.0  broadcast 192.168.1.255
        inet6 fe80::70b3:2dd2:23fa:b219  prefixlen 64  scopeid 0x20<link>
        ether 44:1c:a8:04:33:c1  txqueuelen 1000  (Ethernet)
        RX packets 283204  bytes 341566015 (341.5 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 197543  bytes 22780294 (22.7 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
[B]
mjt07@mjt07:~$ cat /etc/resolv.conf[/B]
# This file is managed by man:systemd-resolved(8). Do not edit.
#
# This is a dynamic resolv.conf file for connecting local clients to the
# internal DNS stub resolver of systemd-resolved. This file lists all
# configured search domains.
#
# Run "systemd-resolve --status" to see details about the uplink DNS servers
# currently in use.
#
# Third party programs must not access this file directly, but only through the
# symlink at /etc/resolv.conf. To manage man:resolv.conf(5) in a different way,
# replace this symlink by a static file or a different symlink.
#
# See man:systemd-resolved.service(8) for details about the supported modes of
# operation for /etc/resolv.conf.

nameserver 127.0.0.53


**mjt07@mjt07:~$ sudo iwlist scan**
[sudo] password for mjt07: 
lo        Interface doesn't support scanning.

enp2s0    Interface doesn't support scanning.

wlp3s0    Scan completed :
          Cell 01 - Address: 00:25:86:B9:36:72
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=48/70  Signal level=-62 dBm  
                    Encryption key:on
                    ESSID:"03/880 879 Unlimited 4MB"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000000c238093
                    Extra: Last beacon: 48ms ago
                    IE: Unknown: 001830332F3838302038373920556E6C696D6974656420344D42
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0102
                    IE: Unknown: 32041224606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD0900037F01010008FF7F
                    IE: Unknown: DD1A00037F0301000000002586B93672022586B9367264002C010808

---

### Post by chili555 on 2018-06-22
Is this a router over which you have administrative privileges? If so, I suggest a few changes.

 WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, you may have better connectivity with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz, although it is likely to affect N speeds. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. After making these changes, reboot the router. 

Here is an excellent piece that tells us why auto channel select is a very bad idea: [https://superuser.com/questions/1311149/why-do-wifi-routers-do-such-a-bad-job-of-channel-selection](https://superuser.com/questions/1311149/why-do-wifi-routers-do-such-a-bad-job-of-channel-selection)

Quite often, the weak signal is a symptom of the antenna wire being connected to connection #1 on the card when the default driver is expecting to see the signal at connection #2. Of course, you could open the laptop and switch the wire or you could implement antenna selection at the driver level.

From the terminal:```
sudo -i
echo "options rtl8723be ant_sel=2"  >  /etc/modprobe.d/rtl8723be.conf
exit
```Reboot. Is there any improvement? If not, run the sequence again with ant_sel=1 and reboot again.

---

