---
title: "Wifi stops working after a while but works after reboot"
date: 2013-12-03
forum: Networking &amp; Wireless
---

### Post by kashif-razzaqui on 2013-12-03
Wifi stops working after a while but works after reboot, this behavior is consistent across different wifi networks at home and office. And has happened for the first time in a few years of my using ubuntu on this very laptop.

Here is the output from some commands that might help diagnose the problem. Would appreciate any help, please let me know if you need any more diagnostics.

Laptop brand and model: Lenevo x201i



```

$ uname -a

Linux kashif 3.11.0-13-lowlatency #5-Ubuntu SMP PREEMPT Tue Oct 29 16:09:48 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

```

```

$ lspci -nnk | grep -iA2 net

00:19.0 Ethernet controller [0200]: Intel Corporation 82577LM Gigabit Network Connection [8086:10ea] (rev 06)
    Subsystem: Lenovo Device [17aa:2153]
    Kernel driver in use: e1000e
--
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8191SEvB Wireless LAN Controller [10ec:8172] (rev 10)
    Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:e020]
    Kernel driver in use: rtl8192se


```

```

$ lsusb


Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 17ef:4816 Lenovo 
Bus 001 Device 003: ID 0a5c:217f Broadcom Corp. BCM2045B (BDC-2.1)
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub



```

```

$ iwconfig wlan0


wlan0     IEEE 802.11bgn  ESSID:"kash"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: C8:60:00:D2:FB:18   
          Bit Rate:72.2 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=10 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:289   Missed beacon:0

```

```

$ lsmod


Module                  Size  Used by
cuse                   13274  3 
parport_pc             32701  0 
ppdev                  17671  0 
rfcomm                 69070  12 
bnep                   19564  2 
snd_hda_codec_hdmi     41117  1 
snd_hda_codec_conexant    56990  1 
intel_powerclamp       14705  0 
coretemp               13435  0 
kvm                   431365  0 
uvcvideo               80885  0 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
videobuf2_core         40469  1 uvcvideo
videodev              133390  2 uvcvideo,videobuf2_core
btusb                  28267  0 
bluetooth             372007  22 bnep,btusb,rfcomm
thinkpad_acpi          80701  0 
arc4                   12608  2 
nvram                  14362  1 thinkpad_acpi
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
rtl8192se              63196  0 
snd_hda_intel          44075  3 
snd_rawmidi            30095  1 snd_seq_midi
rtl_pci                26641  1 rtl8192se
microcode              23518  0 
rtlwifi                63229  2 rtl_pci,rtl8192se
mac80211              613561  3 rtl_pci,rtlwifi,rtl8192se
snd_hda_codec         188696  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
snd_hwdep              13602  1 snd_hda_codec
psmouse                97626  0 
serio_raw              13413  0 
intel_ips              18470  0 
lpc_ich                21080  0 
snd_pcm               101983  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
cfg80211              496195  2 mac80211,rtlwifi
i915                  655899  3 
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29433  2 snd_pcm,snd_seq
drm_kms_helper         52651  1 i915
wmi                    19070  0 
snd                    69141  18 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,thinkpad_acpi,snd_seq_device,snd_seq_midi
soundcore              12680  1 snd
tpm_tis                19123  0 
drm                   296739  4 i915,drm_kms_helper
video                  19318  1 i915
mei_me                 18421  0 
mei                    77692  1 mei_me
mac_hid                13205  0 
i2c_algo_bit           13413  1 i915
lp                     17759  0 
parport                42299  3 lp,ppdev,parport_pc
e1000e                250025  0 
ahci                   25819  3 
ptp                    18580  1 e1000e
libahci                31898  1 ahci
pps_core               19027  1 ptp



```

```

$ nm-tool



NetworkManager Tool


State: connected (global)


- Device: wlan0  [kash] --------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8192se
  State:             connected
  Default:           yes
  HW Address:        1C:65:9D:95:F4:2A


  Capabilities:
    Speed:           72 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    Saxena:          Infra, 78:54:2E:77:38:6F, Freq 2412 MHz, Rate 54 Mb/s, Strength 10 WPA WPA2
    Truth of Touch:  Infra, 94:D7:23:48:1C:E0, Freq 2412 MHz, Rate 54 Mb/s, Strength 10 WPA
    F-1203:          Infra, 00:02:6F:A2:B8:DB, Freq 2417 MHz, Rate 54 Mb/s, Strength 10 WPA WPA2
    Broadcom:        Infra, 00:1E:40:14:EB:4B, Freq 2437 MHz, Rate 54 Mb/s, Strength 10 WPA
    atulgupta:       Infra, 0C:D2:B5:0C:65:B8, Freq 2457 MHz, Rate 54 Mb/s, Strength 10 WPA2
    MANISH:          Infra, 00:1E:40:83:F2:E0, Freq 2462 MHz, Rate 54 Mb/s, Strength 10 WPA
    Sethis:          Infra, 00:24:B2:86:B6:22, Freq 2462 MHz, Rate 54 Mb/s, Strength 10 WPA WPA2
    BSNL:            Infra, 00:25:5E:33:E4:7C, Freq 2462 MHz, Rate 11 Mb/s, Strength 10 WPA
    samir2:          Infra, 94:D7:23:12:1B:2C, Freq 2412 MHz, Rate 54 Mb/s, Strength 100 WPA
    ashish:          Infra, 80:A1:D7:E0:FC:E2, Freq 2462 MHz, Rate 54 Mb/s, Strength 100 WPA
    Hsdutta1:        Infra, 00:25:5E:33:D1:38, Freq 2412 MHz, Rate 54 Mb/s, Strength 10 WEP
    MGMNT:           Infra, 94:D7:23:12:1B:2D, Freq 2412 MHz, Rate 54 Mb/s, Strength 10 WEP
    Partha:          Infra, B8:A3:86:35:46:32, Freq 2412 MHz, Rate 54 Mb/s, Strength 10 WEP
    Our net:         Infra, 00:25:5E:3D:72:84, Freq 2442 MHz, Rate 54 Mb/s, Strength 10 WEP
    MGMNT:           Infra, 80:A1:D7:E0:FC:E3, Freq 2462 MHz, Rate 54 Mb/s, Strength 10 WEP
    Meher :          Infra, 00:1B:2F:5E:57:68, Freq 2462 MHz, Rate 54 Mb/s, Strength 10 WEP
    MGMNT:           Infra, 94:D7:23:7D:89:61, Freq 2472 MHz, Rate 54 Mb/s, Strength 10 WEP
    *kash:           Infra, C8:60:00:D2:FB:18, Freq 2462 MHz, Rate 54 Mb/s, Strength 100 WPA2
    naveen:          Infra, 0C:D2:B5:0C:1B:28, Freq 2462 MHz, Rate 54 Mb/s, Strength 10 WPA2
    Private:         Infra, 00:1E:40:14:E7:BC, Freq 2462 MHz, Rate 54 Mb/s, Strength 10 WPA
    purab404:        Infra, 00:1E:40:19:02:E0, Freq 2462 MHz, Rate 54 Mb/s, Strength 10 WPA
    Trozen13:        Infra, 80:A1:D7:77:C6:94, Freq 2462 MHz, Rate 54 Mb/s, Strength 10 WPA


  IPv4 Settings:
    Address:         192.168.1.12
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1


    DNS:             8.8.8.8
    DNS:             8.8.4.4




- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            e1000e
  State:             unavailable
  Default:           no
  HW Address:        F0:DE:F1:2E:9F:53


  Capabilities:
    Carrier Detect:  yes


  Wired Properties
    Carrier:         off



```


```

$ dmesg | egrep 'wlan|iwl|firm'


[    3.359722] Loading firmware rtlwifi/rtl8192sefw.bin
[    4.122258] psmouse serio1: trackpoint: IBM TrackPoint firmware: 0x0e, buttons: 3/3
[    5.487014] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[    5.487467] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[    7.442824] wlan0: authenticate with c8:60:00:d2:fb:18
[    7.461619] wlan0: send auth to c8:60:00:d2:fb:18 (try 1/3)
[    7.463178] wlan0: authenticated
[    7.464371] wlan0: associate with c8:60:00:d2:fb:18 (try 1/3)
[    7.467552] wlan0: RX AssocResp from c8:60:00:d2:fb:18 (capab=0x411 status=0 aid=4)
[    7.469230] wlan0: associated
[    7.469242] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready



```


```

$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 82577LM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 06
       serial: f0:de:f1:2e:9f:53
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi cap_list ethernet physical
       configuration: broadcast=yes driver=e1000e latency=0 multicast=yes
       resources: irq:20 memory:f2500000-f251ffff memory:f2525000-f2525fff ioport:1820(size=32)
  *-network
       description: Wireless interface
       product: RTL8191SEvB Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 10
       serial: 1c:65:9d:95:f4:2a
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192se driverversion=3.11.0-13-lowlatency firmware=N/A ip=192.168.1.12 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:16 ioport:3000(size=256) memory:f2400000-f2403fff



```

```

$ sudo service networking restart

This causes the system to hang

```

---

### Post by praseodym on 2013-12-03
Try to update the driver
```

sudo apt-get install --reinstall build-essential linux-headers-$(uname -r)
wget media.cdn.ubuntu-de.org/forum/attachments/39/19/5443987-rtl_92ce_92se_92de_8723ae_88ee_0012.0207.2013.tar.gz
tar xvf 5443987-rtl_92ce_92se_92de_8723ae_88ee_0012.0207.2013.tar.gz
cd rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/
make
sudo make install
sudo depmod -a
sudo update-initramfs -u
sudo cp -r firmware/* /lib/firmware  
```
Reboot.

---

### Post by kashif-razzaqui on 2013-12-03
Will try and let you know the results.

---

### Post by kashif-razzaqui on 2013-12-03
This does not work because it throws some compilation errors while make-ing

```
wget media.cdn.ubuntu-de.org/forum/attachments/39/19/5443987-rtl_92ce_92se_92de_8723ae_88ee_0012.0207.2013.tar.gz
```

---

### Post by praseodym on 2013-12-03
Driver attached.

---

### Post by kashif-razzaqui on 2013-12-03
```

$ make


make -C /lib/modules/3.11.0-13-lowlatency/build M=/home/kashif/Downloads/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013 modules
make[1]: Entering directory `/usr/src/linux-headers-3.11.0-13-lowlatency'
  CC [M]  /home/kashif/Downloads/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/base.o
In file included from /home/kashif/Downloads/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/base.c:39:0:
/home/kashif/Downloads/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/pci.h:247:15: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘rtl_pci_probe’
 int __devinit rtl_pci_probe(struct pci_dev *pdev,
               ^
/home/kashif/Downloads/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/base.c: In function ‘rtl_action_proc’:
/home/kashif/Downloads/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/base.c:885:32: error: ‘struct ieee80211_conf’ has no member named ‘channel’
       rx_status.freq = hw->conf.channel->center_freq;
                                ^
/home/kashif/Downloads/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/base.c:886:32: error: ‘struct ieee80211_conf’ has no member named ‘channel’
       rx_status.band = hw->conf.channel->band;
                                ^
/home/kashif/Downloads/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/base.c: In function ‘rtl_send_smps_action’:
/home/kashif/Downloads/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/base.c:1451:24: error: ‘struct ieee80211_conf’ has no member named ‘channel’
   info->band = hw->conf.channel->band;
                        ^
make[2]: *** [/home/kashif/Downloads/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/base.o] Error 1
make[1]: *** [_module_/home/kashif/Downloads/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.11.0-13-lowlatency'
make: *** [all] Error 2




```

---

### Post by kashif-razzaqui on 2013-12-05
Would appreciate some assistance.

---

### Post by praseodym on 2013-12-05
Please show
```

iwlist chan
sudo iwlist scan
cat /etc/resolv.conf
```

---

### Post by Jim_Granite on 2013-12-05
I just noticed this thread.
Like the OP, my Lenovo W510 Intel Centrino Ultimate-N 6300 wireless NIC had been working just fine, for months, on Ubuntu 13.10 up until yesterday.

Now it loses the connection every minute or two (which can easily be seen with a ping to 192.168.1.1).
There's nothing wrong with the router because other laptops and devices have no problem.
It doesn't happen when I dual boot to Windows, so it's not the signal level either.

** I suspect *something* recently changed in Ubuntu that crapped on the wireless card.**
My independent thread on the topic is here, if the OP wants information:
- [Intel Centrino Ultimate-N 6300 drops out & reconnects almost every minute]("http://ubuntuforums.org/showthread.php?t=2191982")

EDIT: The team helped me solve my connection problem. I posted all my debugging commands in that thread above (so others can follow in our footsteps).

---

