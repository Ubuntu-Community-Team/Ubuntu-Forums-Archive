---
title: "TP-Link TL-WN823N refusing to connect to wireless networks after update to 17.14"
date: 2017-07-22
forum: Networking &amp; Wireless
---

### Post by thecrazydude778 on 2017-07-22
Hello,

My wireless adapter that I managed to get working a couple of months ago is now refusing to connect to my wireless network. This problem occurred after the update to Ubuntu 17.04 where the driver seemed to work as it showed the wireless networks in my area but when it tried to connect to my router the computer refused to connect giving no information other than a disconnected pop up in the top right-hand corner. I tried using my guest network and it still wouldn't connect. I also tried to install the driver that worked last time on Ubuntu 16.04 (The version before the update) and install it via the make commands but that wouldn't work as well.

My computer is a DELL Optiplex 745 and the wireless adapter is the TP-Link TL-WN823N version 2.

A link to the problems installing the adapter (in case that might help): [https://ubuntuforums.org/showthread.php?t=2348667](https://ubuntuforums.org/showthread.php?t=2348667)

Some information:

sudo lshw -C network:
```
*-network DISABLED       
       description: Ethernet interface
       product: NetXtreme BCM5754 Gigabit Ethernet PCI Express
       vendor: Broadcom Limited
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: enp3s0
       version: 02
       serial: 00:19:b9:44:37:01
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.137 firmware=5754-v3.15 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:16 memory:fe6f0000-fe6fffff
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@1:3
       logical name: wlx98ded0153e8e
       serial: c2:b3:30:23:76:de
       capabilities: ethernet physical wireless

       configuration: broadcast=yes driver=rtl8xxxu driverversion=4.10.0-28-generic firmware=N/A link=no multicast=yes wireless=IEEE 802.11
```

lsusb:
```
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 1307:0310 Transcend Information, Inc. SD/MicroSD CardReader [hama]
Bus 001 Device 005: ID 2357:0109  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 004: ID 046d:c045 Logitech, Inc. Optical Mouse
Bus 003 Device 003: ID 04b3:301b IBM Corp. SK-8815 Keyboard
Bus 003 Device 002: ID 04b3:301a IBM Corp. 2-port low-power hub

Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

dmesg | grep rtl:
```
[   24.568573] usb 1-4: rtl8192eu_parse_efuse: dumping efuse (0x200 bytes):

[   24.568682] usb 1-4: rtl8xxxu: Loading firmware rtlwifi/rtl8192eu_nic.bin
[   25.898067] usb 1-4: rtl8192eu_rx_iqk_path_a: Path A RX IQK failed!
[   25.930189] usb 1-4: rtl8192eu_rx_iqk_path_a: Path A RX IQK failed!
[   26.157295] usbcore: registered new interface driver rtl8xxxu
[   26.452693] RTL871X: rtl8192eu v4.3.1.1_11320.20140505
[   26.452742] usbcore: registered new interface driver rtl8192eu
[   27.232369] rtl8xxxu 1-4:1.0 wlx98ded0153e8e: renamed from wlan0
[   89.331154] usb 1-4: rtl8192eu_active_to_emu: Disabling MAC timed out
[   91.200851] usb 1-3: rtl8192eu_parse_efuse: dumping efuse (0x200 bytes):
[   91.200962] usb 1-3: rtl8xxxu: Loading firmware rtlwifi/rtl8192eu_nic.bin

[   92.399833] rtl8xxxu 1-3:1.0 wlx98ded0153e8e: renamed from wlan0
```


iwconfig:
```
enp3s0    no wireless extensions.

 
wlx98ded0153e8e  IEEE 802.11  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          

lo        no wireless extensions.
```

rfkill list all:
```
1: phy1: Wireless LAN

            Soft blocked: no

            Hard blocked: no
```

lsmod:

```
Module                  Size  Used by

nls_iso8859_1          16384  1
uas                    24576  0
usb_storage            69632  2 uas
binfmt_misc            20480  1
dcdbas                 16384  0
8192eu                937984  0
arc4                   16384  2
snd_hda_codec_analog    16384  1
snd_hda_codec_generic    73728  1 snd_hda_codec_analog
snd_hda_intel          36864  3
snd_hda_codec         126976  3 snd_hda_intel,snd_hda_codec_analog,snd_hda_codec_generic
snd_hda_core           81920  4 snd_hda_intel,snd_hda_codec,snd_hda_codec_analog,snd_hda_codec_generic
coretemp               16384  0
snd_hwdep              16384  1 snd_hda_codec
rtl8xxxu              126976  0
kvm_intel             200704  0
snd_pcm               102400  3 snd_hda_intel,snd_hda_codec,snd_hda_core
mac80211              782336  1 rtl8xxxu
kvm                   593920  1 kvm_intel
input_leds             16384  0
cfg80211              602112  1 mac80211
snd_seq_midi           16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
irqbypass              16384  1 kvm
snd_rawmidi            32768  1 snd_seq_midi
serio_raw              16384  0
snd_seq                65536  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              32768  2 snd_seq,snd_pcm
snd                    77824  16 snd_hda_intel,snd_hwdep,snd_seq,snd_hda_codec,snd_hda_codec_analog,snd_timer,snd_rawmidi,snd_hda_codec_generic,snd_seq_device,snd_pcm
lpc_ich                24576  0
soundcore              16384  1 snd
shpchp                 36864  0
mac_hid                16384  0
parport_pc             32768  1
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,parport_pc,ppdev
ip_tables              24576  0
x_tables               36864  1 ip_tables
autofs4                40960  2
hid_generic            16384  0
usbhid                 53248  0
hid                   114688  2 hid_generic,usbhid
i915                 1449984  99
psmouse               139264  0
tg3                   163840  0
pata_acpi              16384  0
video                  40960  1 i915
i2c_algo_bit           16384  1 i915
ptp                    20480  1 tg3
drm_kms_helper        151552  1 i915
pps_core               20480  1 ptp
syscopyarea            16384  1 drm_kms_helper
floppy                 77824  0
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
fjes                   73728  0
fb_sys_fops            16384  1 drm_kms_helper
drm                   352256  6 i915,drm_kms_helper
 
```


Sorry about not using the wireless-info script as it would not execute on my computer. I used the commands that people asked me to do in another thread about installing the adapter.

---

### Post by jeremy31 on 2017-07-22
For 17.04 try disabling the MAC randomization using [https://askubuntu.com/a/905019/300665](https://askubuntu.com/a/905019/300665)
Or you can use Hadaka idea
```
printf "[device]\nwifi.scan-rand-mac-address=0\n"| sudo tee -a /etc/NetworkManager/*.conf
```
Then restart Network Manager
```
systemctl restart network-manager.service
```

---

### Post by thecrazydude778 on 2017-07-22
I tryed disabling the MAC randomisation but that didn't fix the problem. I also disabled DNSSEC as well ([https://superuser.com/questions/1153203/ubuntu-17-04-systemd-resolved-dns-lookups-randomly-fail/1200745#1200745](https://superuser.com/questions/1153203/ubuntu-17-04-systemd-resolved-dns-lookups-randomly-fail/1200745#1200745)) but the problem still remains. Another thing is that my iPhone with it's personal hotspot attached to the computer (via USB) still will not allow me an internet connection.

---

### Post by BenginM on 2017-07-22
from lsmod we see:

8192eu                937984  0 , 
rtl8xxxu              126976  0

both are not used... which one is the driver! because the result of dmesg is confusing! and lshw shows the driver in usd but look a the firmware line..

 configuration: broadcast=yes driver=rtl8xxxu driverversion=4.10.0-28-generic firmware=N/A

so maybe try and unload 
rtl8xxxu

and load 

8192eu

with modprobe , also what would dmesg | grep 8192eu .. show us!

---

