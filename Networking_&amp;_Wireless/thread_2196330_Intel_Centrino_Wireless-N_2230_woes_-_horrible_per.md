---
title: "Intel Centrino Wireless-N 2230 woes - horrible performance"
date: 2013-12-28
forum: Networking &amp; Wireless
---

### Post by CaptSaltyJack on 2013-12-28
I'm about to give up on Linux. Wifi has ALWAYS been such a weak point in the kernel, and I intentionally got a laptop (Lenovo) with an Intel wifi chipset to avoid Realtek which is almost always a disaster. Well, looks like this was a mistake too.

I get wifi slowdowns and total dropouts where I still am connected, but the network appears to be dead (can't ping anything, or pings are 1000ms!). I edited the /etc/modprobe.d/iwlwifi.conf file to add the "options 11n_disable=1" option which fixes it for some people, but not for me. My measly iPhone gets a whopping 20Mbps via speedtest.net, but my laptop struggles to even get a fraction of a megabit/sec. Actually, it won't even load speedtest.net at all. If I disable the wifi radio on the laptop and turn it back on, it's fine (for a while).

Now there's a slight chance the wifi radio itself is hosed, and I can only test that by installing Windows on this thing to test it out, which I might do for a while.

If anyone has any advice on how to solve this, I'd love to hear any ideas. Thanks in advance.

---

### Post by mörgæs on 2013-12-29
If you want help please begin posting the outputs mentioned here:
[http://ubuntuforums.org/showthread.php?p=6183681](http://ubuntuforums.org/showthread.php?p=6183681)

---

### Post by chili555 on 2013-12-29
>  I edited the /etc/modprobe.d/iwlwifi.conf file to add the "options 11n_disable=1" option which fixes it for some people, but not for me.Did you mean:```
options [COLOR="#FF0000"]iwlwifi[/COLOR] 11n_disable=1
```??

The parameter will be ineffective unless you declare to which module it is to be applied.

My Lenovo laptop uses iwlwifi without drama. I suspect part of the well-known 11n_disable issue is related to specific wireless card and router combinations.

---

### Post by CaptSaltyJack on 2013-12-29
Laptop: Lenovo S431, running Ubuntu 13.10, kernel 3.11.0-14-generic x86_64

Wireless Brand/model: Intel Centrino Wireless-N 2230

Relevant ifconfig output:

```
wlan0     Link encap:Ethernet  HWaddr 68:17:29:5e:4b:1f  
          inet addr:192.168.11.100  Bcast:192.168.11.255  Mask:255.255.255.0
          inet6 addr: fe80::6a17:29ff:fe5e:4b1f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:539 errors:0 dropped:0 overruns:0 frame:0
          TX packets:549 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:234395 (234.3 KB)  TX bytes:143304 (143.3 KB)

```

Relevant iwconfig output:

```
wlan0     IEEE 802.11bgn  ESSID:"WildCity"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 90:72:40:24:50:78   
          Bit Rate=104 Mb/s   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=47/70  Signal level=-63 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:88  Invalid misc:60   Missed beacon:0

```

lsmod output:

```

Module                  Size  Used by
btusb                  28267  0 
uvcvideo               80885  0 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
videobuf2_core         40469  1 uvcvideo
videodev              133390  2 uvcvideo,videobuf2_core
joydev                 17377  0 
parport_pc             32701  0 
ppdev                  17671  0 
bnep                   19564  2 
rfcomm                 69070  12 
bluetooth             371880  22 bnep,btusb,rfcomm
arc4                   12608  2 
iwldvm                237440  0 
mac80211              596969  1 iwldvm
x86_pkg_temp_thermal    14162  0 
intel_powerclamp       14705  0 
coretemp               13435  0 
kvm_intel             138538  0 
kvm                   431315  1 kvm_intel
microcode              23518  0 
iwlwifi               165398  1 iwldvm
snd_hda_codec_hdmi     41117  1 
snd_hda_codec_realtek    55704  1 
psmouse                97626  0 
serio_raw              13413  0 
lpc_ich                21080  0 
cfg80211              479757  3 iwlwifi,mac80211,iwldvm
snd_hda_intel          48171  3 
snd_hda_codec         188738  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
rtsx_pci_ms            18151  0 
snd_hwdep              13602  1 snd_hda_codec
memstick               16760  1 rtsx_pci_ms
snd_pcm               102033  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
mei_me                 18421  0 
mei                    77692  1 mei_me
tpm_tis                19123  0 
nls_iso8859_1          12713  1 
ext2                   72832  1 
thinkpad_acpi          80701  0 
nvram                  14362  1 thinkpad_acpi
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30095  1 snd_seq_midi
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29433  2 snd_pcm,snd_seq
snd                    69141  18 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,thinkpad_acpi,snd_seq_device,snd_seq_midi
soundcore              12680  1 snd
mac_hid                13205  0 
lp                     17759  0 
parport                42299  3 lp,ppdev,parport_pc
dm_crypt               22728  1 
rtsx_pci_sdmmc         23527  0 
crct10dif_pclmul       14289  0 
crc32_pclmul           13113  0 
ghash_clmulni_intel    13259  0 
i915                  655752  3 
aesni_intel            55624  5 
aes_x86_64             17131  1 aesni_intel
lrw                    13257  1 aesni_intel
gf128mul               14951  1 lrw
glue_helper            13990  1 aesni_intel
ablk_helper            13597  1 aesni_intel
cryptd                 20329  4 ghash_clmulni_intel,aesni_intel,ablk_helper
ahci                   25819  3 
libahci                31898  1 ahci
i2c_algo_bit           13413  1 i915
r8169                  67341  0 
drm_kms_helper         52651  1 i915
rtsx_pci               45546  2 rtsx_pci_ms,rtsx_pci_sdmmc
mii                    13934  1 r8169
drm                   296739  4 i915,drm_kms_helper
wmi                    19070  0 
video                  19318  1 i915

```

dmesg output (limited to wifi related stuff):

```

[   10.906240] Intel(R) Wireless WiFi driver for Linux, in-tree:
[   10.914831] iwlwifi 0000:03:00.0: can't disable ASPM; OS doesn't have ASPM control
[   10.914972] iwlwifi 0000:03:00.0: irq 47 for MSI/MSI-X
[   11.019577] iwlwifi 0000:03:00.0: loaded firmware version 18.168.6.1 op_mode iwldvm
[   11.050591] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEBUG disabled
[   11.050597] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[   11.050600] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[   11.050602] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_P2P disabled
[   11.050605] iwlwifi 0000:03:00.0: Detected Intel(R) Centrino(R) Wireless-N 2230 BGN, REV=0xC8
[   11.050706] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[   11.631343] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[   11.638977] iwlwifi 0000:03:00.0: Radio type=0x2-0x0-0x0
[   11.883694] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[   11.891746] iwlwifi 0000:03:00.0: Radio type=0x2-0x0-0x0

```

lshw -C network output:

```

  *-network
       description: Wireless interface
       product: Centrino Wireless-N 2230
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: c4
       serial: 68:17:29:5e:4b:1f
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.11.0-14-generic firmware=18.168.6.1 ip=192.168.11.100 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:47 memory:f1d00000-f1d01fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 07
       serial: b8:88:e3:fa:69:8e
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168e-3_0.0.4 03/27/12 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:42 ioport:2000(size=256) memory:f0c04000-f0c04fff memory:f0c00000-f0c03fff

```

iwlist scan output:

```

wlan0     Scan completed :
          Cell 01 - Address: 90:72:40:24:50:78
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=53/70  Signal level=-57 dBm  
                    Encryption key:on
                    ESSID:"WildCity"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000cce59f7ec
                    Extra: Last beacon: 16256ms ago
                    IE: Unknown: 000F5320697320666F722053747564696F
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 0706555320010B1E
                    IE: Unknown: 200100
                    IE: Unknown: 23021400
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AAD1917FFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: 3D1601081500000000000000000000000000000000000000
                    IE: Unknown: 7F080000000000000040
                    IE: Unknown: DD0B0017F20100010100000007
                    IE: Unknown: DD0700039301780320
                    IE: Unknown: DD0E0017F20700010106907240245079
                    IE: Unknown: DD090010180203001C0000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 46050200010000

```

Result of "sudo service networking restart": screen goes white with a few grey blocks on it. Mouse and system still works, but had to jump into a text-only shell and reboot.

---

### Post by CaptSaltyJack on 2013-12-29
Ahh damn, I got duped!! Here I was thinking I was going to get Intel chipset for wifi, but it looks like it's just Realtek. Argh! If this is the case, then this could be the issue that working Realtek wifi drivers don't exist for kernel 3.10+.

---

### Post by chili555 on 2013-12-29
Yes, you do have an Intel wireless chipset:> *-network
       description: Wireless interface
      [COLOR="#FF0000"] product: Centrino Wireless-N 2230
       vendor: Intel Corporation[/COLOR]
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: c4
       serial: 68:17:29:5e:4b:1f
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=[COLOR="#FF0000"]iwlwifi [/COLOR]driverversion=3.11.0-14-generic firmware=18.168.6.1 ip=192.168.11.100 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:47 memory:f1d00000-f1d01fffAnd, no, you do not have N speeds disabled as I suspected:> wlan0     IEEE 802.11bgn  ESSID:"WildCity"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 90:72:40:24:50:78   
          [COLOR="#FF0000"]Bit Rate=104 Mb/s[/COLOR]   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:onI suggest you retrace your steps and correct your /etc/modprobe.d/iwlwifi.conf file and then reboot.

---

### Post by CaptSaltyJack on 2014-01-15
Oh, forgot that part about putting "options iwlwifi 11n_disable=1". Let me try that.

---

### Post by CaptSaltyJack on 2014-01-15
Well, it seems more stable now I think. Speeds are terrible though. My Ubuntu laptop gets about 5Mbps down/up via speedtest while my iPhone clocks in at 18Mbps down/12Mbps up.

---

### Post by annevanrossum on 2014-05-13
[h=2]Intel Centrino Wireless-N 2230[/h]
I have been patiently waiting for a long time to have a proper iwlwifi driver. It is still not working correctly. My Android phone clocks much higher speeds than my Laptop, it's terrible! 

I can repeat all of the output from the topic starter, but it's the same for me. And I've been playing around for a while:

```
# /etc/modprobe.d/iwlwifi.conf# iwlwifi will dyamically load either iwldvm or iwlmvm depending on the
# microcode file installed on the system.  When removing iwlwifi, first
# remove the iwl?vm module and then iwlwifi.
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211


# Intel Corporation Centrino Wireless-N 2230 should have been made for n-networks!
# so, I don't want to disable this!!
options iwlwifi 11n_disable=0


# from: http://forums.gentoo.org/viewtopic-t-933360-start-0.html
# according to dmesg this is actually not an option for the driver (anymore)
# options iwlwifi auto_agg=0 


# watchdog timer, doesn't need to be disabled necessarily
options iwlwifi wd_disable=0


# enable bluetooth/wifi coexistence, because it didn't make a difference
options iwlwifi bt_coex_active=1


# http://ubuntuforums.org/showthread.php?t=2105974, but doesn't up my speed, around 10Mbps
# options cfg80211 cfg80211_disable_40mhz_24ghz=0

```

Can anyone point to bug report for these low speeds?

---

### Post by CaptSaltyJack on 2014-05-13
Are you still having issues on Ubuntu 14.04?

---

