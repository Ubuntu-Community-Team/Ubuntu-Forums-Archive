---
title: "WiFi shows connected but stops after every few minutes"
date: 2014-03-30
forum: Networking &amp; Wireless
---

### Post by Gaurav_Joshi on 2014-03-30
Hi 

I have RTL8191SeVa card installed in my laptop
With Ubuntu 13.10. Everything was working fine until last night , my WiFi stops working it shows connected but I can't browse or use internet. Once I reconnect the same WiFi it starts working but only for few minutes then it stops again.
Please help me with this. I have tried many different options from the forum but it didn't work.
I have attached outputs of some commands but if you need more details let me know.

> $ lspci -nnk | grep -iA2 net

02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8191SEvA Wireless LAN Controller [10ec:8171] (rev 10)
    Subsystem: Hewlett-Packard Company Device [103c:1467]
    Kernel driver in use: rtl8192se
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
    Subsystem: Hewlett-Packard Company Device [103c:1425]
    Kernel driver in use: r8169


> $ lsusb

Bus 002 Device 003: ID 064e:f203 Suyin Corp. 
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


> $ lsmod

Module                  Size  Used by
ums_realtek            17733  0 
usb_storage            48294  1 ums_realtek
pci_stub               12550  1 
vboxpci                22896  0 
vboxnetadp             25636  0 
vboxnetflt             27291  0 
vboxdrv               285205  3 vboxnetadp,vboxnetflt,vboxpci
parport_pc             31981  0 
ppdev                  17391  0 
bnep                   18959  2 
rfcomm                 53664  0 
bluetooth             323656  10 bnep,rfcomm
binfmt_misc            13140  1 
ext2                   67224  1 
intel_powerclamp       14239  0 
coretemp               13195  0 
kvm                   368949  0 
joydev                 17097  0 
uvcvideo               71309  0 
videobuf2_vmalloc      13048  1 uvcvideo
videobuf2_memops       13170  1 videobuf2_vmalloc
videobuf2_core         39125  1 uvcvideo
videodev              107508  2 uvcvideo,videobuf2_core
arc4                   12536  2 
hp_wmi                 13702  0 
sparse_keymap          13708  1 hp_wmi
snd_hda_codec_hdmi     40373  1 
snd_hda_codec_realtek    50261  1 
snd_hda_intel          42658  3 
snd_hda_codec         164003  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13272  1 snd_hda_codec
snd_pcm                89488  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
rtl8192se              58091  0 
rtl_pci                22177  1 rtl8192se
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
rtlwifi                52621  2 rtl_pci,rtl8192se
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
mac80211              517444  3 rtl_pci,rtlwifi,rtl8192se
microcode              18894  0 
snd_rawmidi            25094  1 snd_seq_midi
snd_seq                55383  2 snd_seq_midi_event,snd_seq_midi
cfg80211              401762  2 mac80211,rtlwifi
psmouse                90642  0 
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              24447  2 snd_pcm,snd_seq
serio_raw              13189  0 
snd                    60790  17 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
intel_ips              18055  0 
lpc_ich                16864  0 
mei_me                 13933  0 
soundcore              12600  1 snd
mei                    66411  1 mei_me
mac_hid                13037  0 
lp                     13299  0 
parport                40795  3 lp,ppdev,parport_pc
xts                    12749  1 
gf128mul               14503  1 xts
dm_crypt               22316  2 
i915                  594442  9 
i2c_algo_bit           13197  1 i915
drm_kms_helper         46867  1 i915
drm                   242400  5 i915,drm_kms_helper
r8169                  61562  0 
ahci                   25579  2 
libahci                26619  1 ahci
mii                    13654  1 r8169
wmi                    18590  1 hp_wmi
video                  18777  1 i915




> $ iwconfig

lo        no wireless extensions.


eth2      no wireless extensions.


wlan1     IEEE 802.11bgn  ESSID:"757240"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 38:60:77:49:D9:46   
          Bit Rate=72.2 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=52/70  Signal level=-58 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:51   Missed beacon:0

>  ifconfig

eth2      Link encap:Ethernet  HWaddr 60:eb:69:5b:0f:72  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:1858 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1858 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:212956 (212.9 KB)  TX bytes:212956 (212.9 KB)


wlan1     Link encap:Ethernet  HWaddr 1c:65:9d:4a:90:ac  
          inet addr:192.168.0.26  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::1e65:9dff:fe4a:90ac/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:572697 errors:0 dropped:0 overruns:0 frame:0
          TX packets:235687 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:472255636 (472.2 MB)  TX bytes:28811226 (28.8 MB)




---

### Post by Hadaka on 2014-03-30
please post the output of..
```
cat /etc/udev/rules.d/70-persistent-net.rules
lspci -nnk | grep -iA2 net
```
then do..
```
sudo rm  /etc/udev/rules.d/70-persistent-net.rules
```
boot
better?

---

### Post by Gaurav_Joshi on 2014-03-30
$ cat /etc/udev/rules.d/70-persistent-net.rules
```


# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:1c.3/0000:04:00.0 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:1e:ec:f3:a8:b3", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="1c:c1:de:ab:57:99", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"


# PCI device 0x8086:/sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0 (iwlwifi)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:26:c7:a8:6e:fc", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="60:eb:69:5b:0f:72", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth2"


# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:1c.0/0000:02:00.0 (rtl8192se)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="1c:65:9d:4a:90:ac", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"

```
$ lspci -nnk | grep -iA2 net
```

02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8191SEvA Wireless LAN Controller [10ec:8171] (rev 10)
	Subsystem: Hewlett-Packard Company Device [103c:1467]
	Kernel driver in use: rtl8192se
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
	Subsystem: Hewlett-Packard Company Device [103c:1425]



```

OUTPUT BEFORE BOOTING.
Thanks for the quick reply.

---

### Post by Gaurav_Joshi on 2014-03-30
Hey Thanks!
 now its working Better.

---

### Post by Gaurav_Joshi on 2014-03-30
Just for curiosity can you please tell what was wrong.

---

### Post by Hadaka on 2014-03-30
hi, it was obvious you had tried different drivers and possibly a
differnt wifi or dongle. There were some pieces of those attemps
left over in the udev file...so we reset it to current... Glad its better,
if you are satisfied with the results, please mark your thread solved
How to-.[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)
thanks

---

### Post by Gaurav_Joshi on 2014-03-30
Thank again.

---

