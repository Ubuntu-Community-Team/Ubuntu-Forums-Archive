---
title: "Ralink RT5390 on Ubuntu 13.10"
date: 2013-10-25
forum: Networking &amp; Wireless
---

### Post by silvrous on 2013-10-25
My wireless works just fine in Windoes 7, but in Ubuntu, the drivers do not work. I've tried the solutions posted around 2011, but they don't seem to work anymore. What could I do?

---

### Post by praseodym on 2013-10-25
Hi,

please show the terminal outputs of
```

lspci -nnk | grep -iA2 net
lsmod
ifconfig -a
iwconfig
rfkill list
cat /etc/resolv.conf
dmesg | grep rt2
```

---

### Post by silvrous on 2013-10-26
```

silviu@Laptobuntu:~$ lspci -nnk | grep -iA2 net
03:00.0 Network controller [0280]: Ralink corp. RT5390 Wireless 802.11n 1T/1R PCIe [1814:5390]
	Subsystem: Foxconn International, Inc. Device [105b:e054]
	Kernel driver in use: rt2860
04:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8161 Gigabit Ethernet [1969:1091] (rev 10)
	Subsystem: ASUSTeK Computer Inc. Device [1043:14c7]
	Kernel driver in use: alx
silviu@Laptobuntu:~$ lsmod
Module                  Size  Used by
binfmt_misc            17468  1 
alx                    32255  0 
mdio                   13807  1 alx
cfg80211              479757  0 
parport_pc             32701  0 
ppdev                  17671  0 
rfcomm                 69070  0 
bnep                   19564  2 
bluetooth             371874  10 bnep,rfcomm
joydev                 17377  0 
snd_hda_codec_hdmi     41276  1 
snd_hda_codec_realtek    51465  1 
x86_pkg_temp_thermal    14162  0 
intel_powerclamp       14705  0 
coretemp               13435  0 
kvm_intel             138538  0 
kvm                   431315  1 kvm_intel
crct10dif_pclmul       14289  0 
crc32_pclmul           13113  0 
ghash_clmulni_intel    13259  0 
aesni_intel            55624  0 
aes_x86_64             17131  1 aesni_intel
lrw                    13257  1 aesni_intel
gf128mul               14951  1 lrw
glue_helper            13990  1 aesni_intel
ablk_helper            13597  1 aesni_intel
cryptd                 20329  3 ghash_clmulni_intel,aesni_intel,ablk_helper
asus_nb_wmi            16990  0 
asus_wmi               24191  1 asus_nb_wmi
sparse_keymap          13948  1 asus_wmi
uvcvideo               80885  0 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
videobuf2_core         40469  1 uvcvideo
videodev              133390  2 uvcvideo,videobuf2_core
rt5390sta            1452086  1 
snd_hda_intel          48171  3 
snd_hda_codec         188738  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm               102033  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
microcode              23518  0 
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30095  1 snd_seq_midi
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
psmouse                97626  0 
serio_raw              13413  0 
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29433  2 snd_pcm,snd_seq
snd                    69141  17 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
nouveau               943295  0 
mei_me                 18421  0 
i915                  655752  3 
mei                    77692  1 mei_me
lpc_ich                21080  0 
mxm_wmi                13021  1 nouveau
ttm                    83995  1 nouveau
soundcore              12680  1 snd
drm_kms_helper         52651  2 i915,nouveau
drm                   296739  6 ttm,i915,drm_kms_helper,nouveau
i2c_algo_bit           13413  2 i915,nouveau
wmi                    19070  3 mxm_wmi,nouveau,asus_wmi
video                  19318  3 i915,nouveau,asus_wmi
mac_hid                13205  0 
lp                     17759  0 
parport                42299  3 lp,ppdev,parport_pc
ahci                   25819  3 
libahci                31898  1 ahci
silviu@Laptobuntu:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr d8:50:e6:38:8a:77  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:19 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:3516 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3516 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:437935 (437.9 KB)  TX bytes:437935 (437.9 KB)

ra0       Link encap:Ethernet  HWaddr 70:18:8b:14:a1:1b  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::7218:8bff:fe14:a11b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:199647 errors:0 dropped:0 overruns:0 frame:0
          TX packets:107936 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:286602984 (286.6 MB)  TX bytes:11762053 (11.7 MB)
          Interrupt:17 

silviu@Laptobuntu:~$ iwconfig
ra0       Ralink STA  ESSID:"0057"  Nickname:"RT2860STA"
          Mode:Managed  Frequency=2.427 GHz  Access Point: F8:D1:11:AC:81:4C   
          Bit Rate=135 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=100/100  Signal level:-40 dBm  Noise level:-68 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

lo        no wireless extensions.

silviu@Laptobuntu:~$ rfkill list
0: asus-wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
silviu@Laptobuntu:~$ cat /etc/resolv.config
cat: /etc/resolv.config: No such file or directory
silviu@Laptobuntu:~$ dmesg | grep rt2
[   12.299613] register rt2860
[   15.395126]  [<ffffffffa0404824>] rt28xx_init+0x274/0x6f0 [rt5390sta]
[   15.395138]  [<ffffffffa0482295>] rt28xx_open+0x95/0x100 [rt5390sta]
[   15.581583] <==== rt28xx_init, Status=0
[   15.598876] <==== rt28xx_init, Status=0
[   15.617056] <==== rt28xx_init, Status=0
[   15.759047] <==== rt28xx_init, Status=0
[   15.775610] <==== rt28xx_init, Status=0
[   57.465410] <==== rt28xx_init, Status=0
[   57.490248] <==== rt28xx_init, Status=0
[   57.513964] <==== rt28xx_init, Status=0
[   57.539153] <==== rt28xx_init, Status=0
[   57.562473] <==== rt28xx_init, Status=0
silviu@Laptobuntu:~$ 

```

I've found that the drivers do work if, after booting, I close the lid of the laptop and login again, otherwise it just doesn't find any networks, but the signal seems weaker than it is under Windows.

---

### Post by ganesh3 on 2013-10-26
I too am facing the same problem with the same set of drivers and pasting the output of the commands.

ganesh@ganesh-HP-Pavilion-Sleekbook-14-PC:~$ lspci -nnk | grep -iA2 net
06:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
    Subsystem: Hewlett-Packard Company Device [103c:1902]
    Kernel driver in use: r8169
--
07:00.0 Network controller [0280]: Ralink corp. RT3290 Wireless 802.11n 1T/1R PCIe [1814:3290]
    Subsystem: Hewlett-Packard Company Device [103c:18ec]
    Kernel driver in use: rt2860
ganesh@ganesh-HP-Pavilion-Sleekbook-14-PC:~$ lsmod
Module                  Size  Used by
nvram                  14413  0 
dm_crypt               23120  0 
parport_pc             32866  0 
ppdev                  17113  0 
rfcomm                 47922  0 
bnep                   18315  2 
bluetooth             218412  10 bnep,rfcomm
snd_hda_codec_idt      70773  1 
snd_hda_codec_hdmi     32506  1 
binfmt_misc            17540  1 
nls_iso8859_1          12713  1 
uvcvideo               82212  0 
videobuf2_vmalloc      12860  1 uvcvideo
videobuf2_memops       13368  1 videobuf2_vmalloc
videobuf2_core         36094  1 uvcvideo
videodev              120715  2 uvcvideo,videobuf2_core
joydev                 17693  0 
hp_wmi                 18092  0 
sparse_keymap          13890  1 hp_wmi
kvm_amd                56135  0 
kvm                   437435  1 kvm_amd
snd_hda_intel          34147  5 
microcode              23040  0 
snd_hda_codec         135374  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
rt2800pci              18750  0 
rt2800lib              63557  1 rt2800pci
rt2x00pci              14578  1 rt2800pci
rt2x00lib              55527  3 rt2x00pci,rt2800lib,rt2800pci
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                97661  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
psmouse                92362  0 
mac80211              564631  3 rt2x00lib,rt2x00pci,rt2800lib
radeon                917652  3 
cfg80211              212917  2 mac80211,rt2x00lib
eeprom_93cx6           13302  1 rt2800pci
serio_raw              13215  0 
crc_ccitt              12667  1 rt2800lib
snd_page_alloc         18572  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
k10temp                13173  0 
snd_rawmidi            30749  1 snd_seq_midi
ttm                    88492  1 radeon
snd_seq                61897  2 snd_seq_midi_event,snd_seq_midi
rts5229               319201  0 
drm_kms_helper         46931  1 radeon
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
rt3290sta            1174333  1 
snd_timer              29989  2 snd_pcm,snd_seq
drm                   277074  5 ttm,drm_kms_helper,radeon
snd                    79391  20 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_idt,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device
i2c_piix4              13504  0 
wmi                    19256  1 hp_wmi
hp_accel               26012  0 
soundcore              15091  1 snd
i2c_algo_bit           13564  1 radeon
lis3lv02d              19877  1 hp_accel
input_polldev          13896  1 lis3lv02d
video                  19412  0 
lp                     17799  0 
parport                46562  3 lp,ppdev,parport_pc
mac_hid                13253  0 
hid_generic            12493  0 
usbhid                 47307  0 
hid                   100612  2 hid_generic,usbhid
r8169                  68885  0 
ganesh@ganesh-HP-Pavilion-Sleekbook-14-PC:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 28:92:4a:43:f7:f4  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:339 errors:0 dropped:0 overruns:0 frame:0
          TX packets:339 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:49896 (49.8 KB)  TX bytes:49896 (49.8 KB)

ra0       Link encap:Ethernet  HWaddr 68:94:23:76:97:1f  
          inet addr:192.168.1.8  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::6a94:23ff:fe76:971f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5789 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2398 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2654497 (2.6 MB)  TX bytes:478097 (478.0 KB)
          Interrupt:18 

ganesh@ganesh-HP-Pavilion-Sleekbook-14-PC:~$ iwconfig
ra0       Ralink STA  ESSID:"Home"  Nickname:"RT3290STA"
          Mode:Managed  Frequency=2.412 GHz  Access Point: 80:A1:D7:27:65:D0   
          Bit Rate=13.5 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=46/100  Signal level:-89 dBm  Noise level:-99 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

lo        no wireless extensions.

ganesh@ganesh-HP-Pavilion-Sleekbook-14-PC:~$ iwconfig
ra0       Ralink STA  ESSID:"Home"  Nickname:"RT3290STA"
          Mode:Managed  Frequency=2.412 GHz  Access Point: 80:A1:D7:27:65:D0   
          Bit Rate=13.5 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=48/100  Signal level:-90 dBm  Noise level:-100 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

lo        no wireless extensions.

ganesh@ganesh-HP-Pavilion-Sleekbook-14-PC:~$ rfkill list
0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hp-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
ganesh@ganesh-HP-Pavilion-Sleekbook-14-PC:~$ cat /etc/resolv.conf
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.1.1
ganesh@ganesh-HP-Pavilion-Sleekbook-14-PC:~$ dmesg | grep rt2
[   21.324514] register rt2860
[   29.477504] <==== rt28xx_init, Status=0
[   29.608058] <==== rt28xx_init, Status=0
[   29.737373] <==== rt28xx_init, Status=0
[   29.924528] <==== rt28xx_init, Status=0
[   30.043629] <==== rt28xx_init, Status=0

---

### Post by praseodym on 2013-10-27
@ ganes3:

Blacklist the regular driver rt2800pci and reboot.

@  silvrous

Its
```

cat /etc/resolv.conf
```

---

### Post by zemko on 2013-10-27
I have similar problem, my mom has Asus-X55 (or similar), with Ralink RT3290 WiFi/BT card. When there was Windows, the WiFi connected in room where is no router in, but on Ubuntu it disconnect when she leaves room with router (between laptop and router is wall, or two walls), its connecting but then nothing happened, the SSID disappears and I need to switch networking off and on to show the SSID in networking menu

there are commands
```
helenka@helencin:~$ lspci -nnk | grep -iA2 net01:00.0 Network controller [0280]: Ralink corp. RT3290 Wireless 802.11n 1T/1R PCIe [1814:3290]
    Subsystem: Foxconn International, Inc. Device [105b:e055]
    Kernel driver in use: rt2800pci
--
02:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8161 Gigabit Ethernet [1969:1091] (rev 10)
    Subsystem: ASUSTeK Computer Inc. Device [1043:14e7]
    Kernel driver in use: alx
helenka@helencin:~$ lsmod
Module                  Size  Used by
parport_pc             32701  0 
ppdev                  17671  0 
bnep                   19564  2 
rfcomm                 69070  0 
bluetooth             371874  10 bnep,rfcomm
joydev                 17377  0 
asus_nb_wmi            16990  0 
asus_wmi               24191  1 asus_nb_wmi
sparse_keymap          13948  1 asus_wmi
uvcvideo               80885  0 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
videobuf2_core         40469  1 uvcvideo
videodev              133390  2 uvcvideo,videobuf2_core
kvm_amd                59958  0 
kvm                   431315  1 kvm_amd
snd_seq_midi           13324  0 
snd_hda_codec_via      27860  1 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30095  1 snd_seq_midi
snd_hda_codec_hdmi     41276  1 
microcode              23518  0 
snd_hda_intel          48171  5 
snd_hda_codec         188738  3 snd_hda_codec_hdmi,snd_hda_codec_via,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
psmouse                97626  0 
radeon               1402449  3 
serio_raw              13413  0 
k10temp                13126  0 
snd_pcm               102033  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
ttm                    83995  1 radeon
drm_kms_helper         52651  1 radeon
arc4                   12608  2 
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
i2c_piix4              22106  0 
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_timer              29433  2 snd_pcm,snd_seq
ohci_pci               13561  0 
rt2800pci              18690  0 
rt2800lib              79963  1 rt2800pci
rt2x00pci              13287  1 rt2800pci
rt2x00mmio             13603  1 rt2800pci
drm                   296739  5 ttm,drm_kms_helper,radeon
rt2x00lib              55238  4 rt2x00pci,rt2800lib,rt2800pci,rt2x00mmio
mac80211              596969  3 rt2x00lib,rt2x00pci,rt2800lib
snd                    69141  21 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_via,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
cfg80211              479757  2 mac80211,rt2x00lib
eeprom_93cx6           13344  1 rt2800pci
crc_ccitt              12707  1 rt2800lib
soundcore              12680  1 snd
i2c_algo_bit           13413  1 radeon
wmi                    19070  1 asus_wmi
video                  19318  1 asus_wmi
mac_hid                13205  0 
lp                     17759  0 
parport                42299  3 lp,ppdev,parport_pc
hid_generic            12548  0 
usbhid                 53014  0 
hid                   101512  2 hid_generic,usbhid
sdhci_pci              18985  0 
sdhci                  42630  1 sdhci_pci
alx                    32255  0 
ahci                   25819  2 
libahci                31898  1 ahci
mdio                   13807  1 alx
helenka@helencin:~$ ifconfig -a
eth0      Link encap:Ethernet  HWadr 30:85:a9:d6:0d:0a  
          AKTIVOVÁNO VŠESM&#282;ROVÉ_VYSÍLÁNÍ MULTICAST  MTU:1500  Metrika:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          kolizí:0 délka odchozí fronty:1000 
          P&#345;ijato bajt&#367;: 0 (0.0 B) Odesláno bajt&#367;: 0 (0.0 B)
          P&#345;erušení:17 


lo        Link encap:Místní smy&#269;ka  
          inet adr:127.0.0.1  Maska:255.0.0.0
          inet6-adr: ::1/128 Rozsah:Po&#269;íta&#269;
          AKTIVOVÁNO SMY&#268;KA B&#282;ŽÍ  MTU:65536  Metrika:1
          RX packets:34 errors:0 dropped:0 overruns:0 frame:0
          TX packets:34 errors:0 dropped:0 overruns:0 carrier:0
          kolizí:0 délka odchozí fronty:0 
          P&#345;ijato bajt&#367;: 2262 (2.2 KB) Odesláno bajt&#367;: 2262 (2.2 KB)


wlan0     Link encap:Ethernet  HWadr 84:4b:f5:2c:33:4d  
          AKTIVOVÁNO VŠESM&#282;ROVÉ_VYSÍLÁNÍ MULTICAST  MTU:1500  Metrika:1
          RX packets:21 errors:0 dropped:0 overruns:0 frame:0
          TX packets:53 errors:0 dropped:0 overruns:0 carrier:0
          kolizí:0 délka odchozí fronty:1000 
          P&#345;ijato bajt&#367;: 5497 (5.4 KB) Odesláno bajt&#367;: 11362 (11.3 KB)


helenka@helencin:~$ iwconfig
eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          
helenka@helencin:~$ rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: asus-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: asus-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no
helenka@helencin:~$ cat /etc/resolv.conf
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
helenka@helencin:~$ dmesg | grep rt2
[   11.188197] rt2800pci 0000:01:00.0: irq 46 for MSI/MSI-X
[   11.188302] ieee80211 phy0: rt2x00_set_rt: Info - RT chipset 3290, rev 0013 detected
[   11.204467] ieee80211 phy0: rt2x00_set_rf: Info - RF chipset 3290 detected
[   16.652994] ieee80211 phy0: rt2x00lib_request_firmware: Info - Loading firmware file 'rt3290.bin'
[   16.715554] ieee80211 phy0: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.37
[   25.137805] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[   25.297977] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[   25.737861] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[   25.894126] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[   26.154245] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[   26.314321] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[   26.474383] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[   26.634450] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[   27.854996] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[   28.015101] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[   31.164403] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[   31.324646] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[   31.584630] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[   31.744812] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[   31.904886] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[   32.064969] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[   33.289269] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[   33.450129] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[   38.283613] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[   38.443663] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[   38.603753] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[   38.763805] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[   39.984350] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[   40.144326] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[   44.338075] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[   44.498246] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[   44.658336] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[   44.818383] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[   46.042704] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[   46.202965] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[   46.367040] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[   46.527111] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[   46.687181] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[   46.851044] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[   48.071653] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[   48.231859] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[   53.069894] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[   53.229990] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[   53.394037] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[   53.554107] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[   54.778628] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[   54.942549] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[   59.772600] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[   59.932823] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[   60.092923] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[   60.252984] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[   61.473477] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[   61.633543] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[   66.475610] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[   66.635468] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[   66.795742] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[   66.959824] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[   68.180331] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[   68.340294] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[   70.349096] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[   70.509329] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[   70.669417] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[   70.829461] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[   72.049779] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[   72.210051] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[   73.410598] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[   73.570521] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[   73.730701] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[   73.890657] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[   73.926892] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0
[   75.119279] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[   75.280321] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[   80.117267] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[   80.277397] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[   80.437558] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[   80.597712] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[   80.633624] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0
[   81.826324] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[   81.986098] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[   86.824211] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[   86.984263] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[   87.144493] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[   87.304514] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[   87.340616] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0
[   88.529003] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[   88.691995] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[   93.526981] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[   93.691289] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[   93.851183] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[   94.011412] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[   94.047316] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0
[   95.243701] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[   95.407870] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[   98.365192] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[   98.525096] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[   98.685270] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[   98.845363] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[   98.881388] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0
[  100.065910] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  100.226015] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  101.442366] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  101.602506] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  101.766450] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  101.926799] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  101.962707] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0
[  103.151309] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  103.311305] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  108.145384] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  108.305427] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  108.465585] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  108.629603] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  108.665696] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0
[  109.862021] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  110.026041] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  114.852090] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  115.016372] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  115.176441] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  115.336512] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  115.372461] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0
[  116.564786] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  116.725100] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  121.563169] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  121.723002] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  121.883157] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  122.043285] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  122.079417] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0
[  123.267881] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  123.431820] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  126.381212] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  126.545205] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  126.705347] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  126.865423] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  126.905286] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0
[  128.089923] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  128.250002] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  129.430519] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  129.593433] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  129.750655] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  129.910673] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  129.946723] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0
[  131.135187] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  131.295090] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  136.137116] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  136.301444] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  136.461514] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  136.621582] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  136.657493] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0
[  137.846572] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  138.006037] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  142.844236] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  143.004254] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  143.164369] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  143.324368] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  143.360485] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0
[  144.544892] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  144.704794] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  149.538829] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  149.699155] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  149.859222] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  150.019290] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  150.055091] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0
[  151.247723] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  151.411880] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  154.389026] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  154.549213] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  154.709288] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  154.869355] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  154.905326] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0
[  156.089872] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  156.249934] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  157.382216] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  157.542496] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  157.702568] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  157.862632] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  157.898499] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0
[  159.082941] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  159.243135] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  180.400005] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  180.560124] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  180.720225] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  180.880280] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  180.916374] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0
[  182.100835] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  182.260946] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  213.406241] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  213.566366] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  213.726432] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  213.886500] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  213.926498] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0
[  215.111019] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  215.271090] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  256.424627] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  256.584692] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  256.744651] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  256.904828] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  256.940720] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0
[  258.125347] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  258.285415] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  309.447220] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  309.607277] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  309.767352] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  309.927419] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  309.963318] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0
[  311.147939] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  311.308006] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  372.478072] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  372.638140] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  372.798208] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  372.958274] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  372.994295] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0
[  374.178794] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  374.338860] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  435.500923] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  435.660992] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  435.821059] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  435.981125] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  436.016994] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0
[  437.201645] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  437.361706] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  498.531778] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  498.691822] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  498.851917] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  499.011982] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  499.048048] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0
[  500.232500] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  500.392568] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  561.554629] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  561.714698] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  561.874767] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  562.034830] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  562.070730] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0
[  563.255352] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  563.415415] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  624.585486] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  624.745546] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  624.905623] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  625.065690] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  625.101705] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0
[  626.286208] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  626.446278] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  687.608333] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  687.768405] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  687.928475] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  688.088544] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  688.124434] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0
[  689.309057] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  689.469127] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  750.639194] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  750.799262] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  750.959331] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  751.119397] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  751.155301] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0
[  752.339916] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  752.499979] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  813.662045] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  813.822116] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  813.982177] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  814.142251] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  814.178145] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0
[  815.362764] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  815.522834] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  876.692901] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  876.852971] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  877.013037] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  877.173104] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  877.209093] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0
[  878.393623] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  878.553691] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  939.715751] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  939.875821] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  940.035886] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  940.195955] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  940.231926] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0
[  941.416475] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  941.576540] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 1002.746606] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 1002.906676] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 1003.066746] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 1003.226811] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 1003.262781] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0
[ 1004.447332] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 1004.607399] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 1065.769440] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 1065.929511] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 1066.089578] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 1066.249646] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 1066.285659] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0
[ 1067.470183] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 1067.630052] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 1128.800298] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 1128.960363] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 1129.120434] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 1129.280500] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 1129.316512] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0
[ 1130.501039] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 1130.661105] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 1191.823169] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 1191.983236] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 1192.143301] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 1192.303371] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 1192.339334] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0
[ 1193.523889] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 1193.683956] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 1254.853997] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 1255.014088] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 1255.174159] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 1255.334230] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 1255.370257] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0
[ 1256.554744] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 1256.714811] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 1317.876874] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 1318.036941] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 1318.197010] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 1318.357077] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 1318.392973] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0
[ 1319.577597] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 1319.737664] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 1380.907731] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 1381.067801] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 1381.227862] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 1381.387935] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 1381.423962] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0
[ 1382.608391] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 1382.768519] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 1443.930580] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 1444.090646] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 1444.250718] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 1444.410786] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 1444.446677] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0
[ 1445.631306] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 1445.791373] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 1506.961439] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 1507.121506] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 1507.281575] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 1507.441644] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 1507.477668] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0
[ 1508.662158] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 1508.822224] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 1569.984292] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 1570.144358] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 1570.304427] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 1570.464495] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 1570.500390] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0
[ 1571.685014] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 1571.845080] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 1633.015150] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 1633.175211] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 1633.335281] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 1633.495350] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 1633.531352] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0
[ 1634.715850] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 1634.875919] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 1696.037985] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 1696.198048] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 1696.358115] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 1696.518181] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 1696.554064] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0
[ 1697.738722] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 1697.898681] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 1759.068855] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 1759.228923] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 1759.388988] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 1759.549057] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 1759.584954] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0
[ 1760.769561] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 1760.929624] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 1822.091572] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 1822.251761] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 1822.411828] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 1822.571901] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 1822.607785] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0
[ 1823.792428] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 1823.952344] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 1885.122560] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 1885.282630] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 1885.442698] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 1885.602763] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 1885.638726] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0
[ 1886.823283] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 1886.983348] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 1948.145409] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 1948.305481] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 1948.465549] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 1948.625617] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 1948.661581] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0
[ 1949.846135] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 1950.006203] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 2011.176267] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 2011.336335] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 2011.496404] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 2011.656470] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 2011.692461] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0
[ 2012.876987] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 2013.037001] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 2074.199119] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 2074.359187] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 2074.519256] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 2074.679324] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 2074.715278] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0
[ 2075.899840] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 2076.059905] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 2137.229975] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 2137.390043] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 2137.550112] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 2137.710181] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 2137.746169] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0
[ 2138.930697] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 2139.090764] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 2200.252828] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 2200.412895] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 2200.572956] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 2200.733030] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 2200.769002] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0
[ 2201.953550] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 2202.113617] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 2263.283684] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 2263.443754] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 2263.603818] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 2263.763887] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 2263.799880] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0
[ 2264.984405] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 2265.144473] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 2326.306535] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 2326.466603] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 2326.626673] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 2326.786741] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 2326.822720] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0
[ 2328.011259] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 2328.171325] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 2389.337390] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 2389.497458] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 2389.657527] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 2389.817596] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 2389.853587] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0
[ 2391.038114] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 2391.198179] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 2452.360243] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 2452.520308] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 2452.680378] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 2452.840446] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 2452.876420] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0
[ 2454.060965] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 2454.221030] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 2515.391097] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 2515.551167] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 2515.711234] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 2515.871305] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 2515.907266] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0
[ 2517.091820] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 2517.251887] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 2578.413950] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 2578.573962] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 2578.734086] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 2578.894153] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 2578.930111] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0
[ 2580.114672] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 2580.274740] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 2641.444806] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 2641.604872] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 2641.764942] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 2641.925010] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 2641.960973] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0
[ 2643.145528] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 2643.305595] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 2704.467641] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 2704.627709] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 2704.787780] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 2704.951806] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 2704.987849] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0
[ 2706.172363] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 2706.332449] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 2767.498515] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 2767.658581] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 2767.818634] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 2767.978701] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 2768.014681] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0
[ 2769.199237] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 2769.363289] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 2830.521365] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 2830.681434] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 2830.841503] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 2831.001568] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 2831.037541] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0
[ 2832.222088] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 2832.382155] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 2893.552221] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 2893.712290] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 2893.872358] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 2894.032426] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 2894.068418] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0
[ 2895.252943] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 2895.413012] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 2956.575074] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 2956.735139] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 2956.895210] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 2957.055279] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 2957.091227] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0
[ 2958.275775] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 2958.435843] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 3019.601924] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 3019.761990] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 3019.921970] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 3020.082129] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 3020.118104] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0
[ 3021.302649] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 3021.462716] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 3082.628781] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 3082.788849] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 3082.948916] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 3083.108983] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 3083.144944] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0
[ 3084.329503] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 3084.489569] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 3145.659636] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 3145.819704] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 3145.979772] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 3146.139841] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 3146.175803] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0
[ 3147.360360] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 3147.520427] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 3208.682487] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 3208.842552] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 3209.002621] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 3209.162689] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 3209.198662] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0
[ 3210.383210] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 3210.543278] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 3271.713342] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 3271.873409] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 3272.033477] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 3272.193546] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 3272.229514] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0
[ 3273.414066] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 3273.574133] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 3334.736196] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 3334.896265] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 3335.056332] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 3335.216401] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 3335.252359] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0
[ 3336.440919] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 3336.600986] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 3397.767051] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 3397.927121] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 3398.087189] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 3398.247256] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 3398.283229] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0
[ 3399.467622] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 3399.627841] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 3415.954749] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 3416.114648] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 3416.274814] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 3416.434865] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 3416.471055] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0
[ 3417.659284] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 3417.819854] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 3422.657605] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 3422.817721] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 3422.977747] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 3423.137861] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 3423.173669] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0
[ 3424.362384] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 3424.522448] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 3429.352454] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 3429.512358] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 3429.672639] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 3429.832675] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 3429.868712] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0
[ 3431.053032] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 3431.213247] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 3436.047358] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 3436.207351] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 3436.367497] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 3436.527403] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 3436.563613] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0
[ 3437.760086] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 3437.924089] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 3440.797307] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 3440.957456] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 3441.117522] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 3441.277585] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 3441.313560] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0
[ 3442.498107] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 3442.658175] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 3443.782654] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 3443.942726] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 3444.102794] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 3444.262857] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 3444.298754] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0
[ 3445.483378] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 3445.643447] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 3466.792462] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 3466.952530] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 3467.112597] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 3467.272666] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 3467.308555] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0
[ 3468.493180] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 3468.653252] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 3499.810527] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 3499.970594] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 3500.130666] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 3500.290735] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 3500.326790] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0
[ 3501.511253] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 3501.671317] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 3542.828860] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 3542.988927] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 3543.148992] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 3543.309063] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 3543.345118] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0
[ 3544.529582] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 3544.689649] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 3595.851450] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 3596.011386] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 3596.171586] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 3596.331598] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 3596.367600] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0
[ 3597.552173] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 3597.712237] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 3658.874295] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 3659.034370] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 3659.194438] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 3659.354507] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 3659.390396] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0
[ 3660.575023] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 3660.735090] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 3721.905159] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 3722.065226] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 3722.225295] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 3722.385357] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 3722.421426] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0
[ 3723.605878] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 3723.765942] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush



```

---

### Post by praseodym on 2013-10-27
@ zemko

You need nameservers:
```

echo -e "nameserver 8.8.8.8\nnameserver 8.8.4.4" | sudo tee -a /etc/resolv.conf
sudo service network-manager restart
```

---

### Post by silvrous on 2013-10-27
Right, oops.

```

silviu@Laptobuntu:~$ cat /etc/resolv.conf
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.1.1
silviu@Laptobuntu:~$ 

```

---

### Post by zemko on 2013-10-27
@praseodym 

I put these lines into terminal and it wrote me back:

[COLOR=#000000][FONT=Ubuntu Mono]helenka@helencin:[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]~[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]$[/FONT][/COLOR] [COLOR=#000000][FONT=Ubuntu Mono]echo -e "nameserver 8.8.8.8\nnameserver 8.8.4.4" | sudo tee -a /etc/resolv.conf
nameserver 8.8.8.8
nameserver 8.8.4.4

[/FONT][/COLOR]Then I used service n-m restart, it goes ok, the wifi connect for cca 30 seconds and then disconnect, and SSID disappears

---

### Post by praseodym on 2013-10-27
@ zemko

Do you use 13.10?

If yes, try:

```
echo "options asus_nb_wmi wapf=1" | sudo tee /etc/modprobe.d/asus.conf 
```
and reboot.

If no, install this driver:

[http://forum.ubuntuusers.de/topic/nach-update-kein-wlan-mehr-433/2/#post-5641297](http://forum.ubuntuusers.de/topic/nach-update-kein-wlan-mehr-433/2/#post-5641297)

---

### Post by zemko on 2013-10-27
@praseodym yes, new instalation, before that it stabilised and it was connected, but no web pages loaded, so it stays connected, but not working, after your command and reboot it connects and disconnects and disappear again...hate this cheap hardware

---

### Post by praseodym on 2013-10-27
Open the file with
```

gksudo gedit /etc/modprobe.d/asus.conf
```
Try "2", "3" and "4" instead of "1", and reboot each time after saving the file, respectively.

---

### Post by zemko on 2013-10-27
@praseodym nothing new happenned,

---

### Post by zemko on 2013-10-27
@praseodym so after some time of rest for the laptop it stabled and get connected, but web pages don't load, when I tried to ping google it works (it jumps between 146 and 29 ms), my laptop has 10ms to google.com, and intervals between lines is much longer

---

### Post by praseodym on 2013-10-27
Change the encryption mode in your router to pure WPA2-AES, a fixed channel and 20MHz bandwidth

---

### Post by zemko on 2013-10-27
@praseodym channel was fixed on 3, WPA was changed to WPA2, and 20/40 was changed to 20 and I cant get stable connection, it connects for few seconds (2-5)

router is Asus RT-N12

---

### Post by praseodym on 2013-10-27
Router firmware is up-to-date? MAC-addressfilter is "off"? Network is not hidden?

---

### Post by zemko on 2013-10-27
@praseodym triple yes, brother has Asus laptop too, not sure what type of wificard, I have Lenovo, in family are some Android smarphones, except mother's laptop is it without any problems

---

### Post by praseodym on 2013-10-27
Are thee enough IPs available in the router? Check the netmask being **255.255.255.0  **

---

### Post by silvrous on 2013-10-27
And is there anything I could try to solve my issue?

---

### Post by praseodym on 2013-10-27
Did you install the driver?
```
locate rt3290.bin | grep lib
lsmod
iwconfig
dmesg | grep rt3
sudo iwlist scan
```

---

### Post by zemko on 2013-10-27
@praseodym the router is fine, it's new one, when I trie older, the situation is the same. Users from Czech Ubuntu Forum tell me to compile proprietary driver as proposed on launchpad [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1133971/comments/3](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1133971/comments/3), I will try tomorrow

---

### Post by ganesh3 on 2013-10-28
You mean cat /etc/modprobe/blacklist.conf?

---

### Post by zemko on 2013-10-28
so, proprietary driver didn't solved the problem... :(

---

### Post by zemko on 2013-10-28
another update, I blacklisted rt2800pci and rt2x00pci and the connection is stable, minimum packet loss when ping, but when I leave router room with laptop, the connection is still stable, but packet loss is high and web pages don't load

---

### Post by giamgreeg on 2013-11-06
Man, this worked for me: [http://askubuntu.com/a/303422](http://askubuntu.com/a/303422)

---

