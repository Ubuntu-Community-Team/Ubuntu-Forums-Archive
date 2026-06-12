---
title: "TP-Link TL-WN822N is not ready"
date: 2013-12-13
forum: Networking &amp; Wireless
---

### Post by gringo.g on 2013-12-13
Hi,
I've bought external network card TP-Link TL-WN822N. I've installed drivers as is written here: [http://www.ajaykumarsingh.com/linux/tp-link-tl-wn822n-300mbps-high-gain-wireless-n-usb-adapter-not-working-on-ubuntu-12-04.html/comment-page-1#comment-34551](http://www.ajaykumarsingh.com/linux/tp-link-tl-wn822n-300mbps-high-gain-wireless-n-usb-adapter-not-working-on-ubuntu-12-04.html/comment-page-1#comment-34551) and it has been working pretty good, but after updating kernel from 3.8.0-33 to 3.8.0-34 the device "is not ready" and it doesn't work. So the question is how can I resolve this problem? Maybe the best way will be when I'll uninstall all drivers associated with this device, but how to do it? 

Regards.

---

### Post by chili555 on 2013-12-13
The process you linked compiles a driver against the currently running kernel only; in your case, 3.8.0-33. Now that you are running 3.8.0-34, simply re-compile:> cd to the folder where you unzipped the driver and run following commands. If you are not root then use sudo before these commands where required.

chmod 755 ./install.sh
./install.shYou should be all set.

---

### Post by gringo.g on 2013-12-13
Yep, now the device is displayed, but still it's trying to connect to a network and asking about password although I've entered it correctly. Moreover, LED isn't lighting although the device is plugged in.

---

### Post by chili555 on 2013-12-13
Please temporarily try the old driver:```
sudo modprobe -r 8192cu
sudo modprobe rtl8192cu
```Is the behavior improved?

---

### Post by gringo.g on 2013-12-13
```
sudo modprobe -r 8192cu
```
Deleted the device from the list.

```
sudo modprobe rtl8192cu
```
I've received a message: 
> FATAL: Module rtl8192cu not found.

To sum up, nothing changed. So maybe totally uninstalling all drivers and installing them again will help?

---

### Post by chili555 on 2013-12-13
Before we proceed to more drastic methods, let's check the log:```
sudo modprobe 8192cu
dmesg | grep -e 8192 -e rtl
```

---

### Post by gringo.g on 2013-12-14
Here you are:
> [    0.000000] PERCPU: Embedded 28 pages/cpu @ffff88013f400000 s84928 r8192 d21568 u262144
[    0.000000] pcpu-alloc: s84928 r8192 d21568 u262144 alloc=1*2097152
[    8.929844] rtl8192cu driver version=v4.0.2_9000.20130911
[    8.929939] CHIP TYPE: RTL8188C_8192C
[    8.931802] ====> ReadAdapterInfo8192C
[    9.338613] readAdapterInfo_8192CU(): REPLACEMENT = 1
[    9.338617] <==== ReadAdapterInfo8192C in 408 ms
[    9.339247] usbcore: registered new interface driver rtl8192cu
[   24.433740] rtl8192cu_hal_init in 1056ms
[   28.279362] SetHwReg8192CU, 5130, RCR= 700060ca 
[   28.437185] rtl8192c_set_FwJoinBssReport_cmd mstatus(1)
[   28.484055] rtl8192c_set_FwJoinBssReport_cmd mstatus(0)
[   31.581122] ==> rtl8192cu_hal_deinit 
[   34.483003] rtl8192cu_hal_init in 1068ms
[   35.817275] ==> rtl8192cu_hal_deinit 


---

### Post by chili555 on 2013-12-14
Interesting:> [ 8.929844] [COLOR="#FF0000"]rtl8192cu[/COLOR] driver version=v4.0.2_9000.20130911I thought that we were using 8192cu and not rtl8192cu and that, furthermore, the system couldn't find rtl8192cu:> FATAL: Module rtl8192cu not found. Let's double-check:```
lsmod
```We are about to go nuclear...

---

### Post by gringo.g on 2013-12-14
> Module                  Size  Used by
nvram                  14413  0 
ath3k                  12968  0 
btusb                  22431  0 
pci_stub               12622  1 
vboxpci                23236  0 
vboxnetadp             25670  0 
vboxnetflt             27612  0 
vboxdrv               335187  3 vboxpci,vboxnetadp,vboxnetflt
bnep                   18258  2 
rfcomm                 47864  12 
bluetooth             247165  25 ath3k,btusb,bnep,rfcomm
parport_pc             28284  0 
ppdev                  17113  0 
binfmt_misc            17540  1 
ath9k_htc              92962  0 
uvcvideo               82214  0 
videobuf2_core         40785  1 uvcvideo
videodev              130053  2 uvcvideo,videobuf2_core
videobuf2_vmalloc      13056  1 uvcvideo
videobuf2_memops       13202  1 videobuf2_vmalloc
snd_hda_codec_hdmi     37463  1 
snd_hda_codec_idt      71153  1 
snd_hda_intel          44339  3 
snd_hda_codec         141761  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
arc4                   12573  4 
snd_hwdep              13668  1 snd_hda_codec
ath9k                 151796  0 
mac80211              630977  2 ath9k_htc,ath9k
snd_pcm               102477  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30417  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
ath9k_common           14053  2 ath9k_htc,ath9k
snd_seq                61930  2 snd_seq_midi,snd_seq_midi_event
ath9k_hw              422432  3 ath9k_htc,ath9k,ath9k_common
snd_timer              29989  2 snd_pcm,snd_seq
coretemp               13596  0 
snd_seq_device         14497  3 snd_seq_midi,snd_rawmidi,snd_seq
ath                    24123  4 ath9k_htc,ath9k,ath9k_common,ath9k_hw
joydev                 17613  0 
i915                  620571  4 
cfg80211              525326  4 ath9k_htc,ath9k,mac80211,ath
kvm_intel             137899  0 
drm_kms_helper         49597  1 i915
drm                   287564  5 i915,drm_kms_helper
kvm                   455932  1 kvm_intel
psmouse                97873  0 
mei                    41820  0 
snd                    69533  16 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
hp_accel               26012  0 
ghash_clmulni_intel    13259  0 
soundcore              12680  1 snd
snd_page_alloc         18798  2 snd_hda_intel,snd_pcm
cryptd                 20501  1 ghash_clmulni_intel
lis3lv02d              20200  1 hp_accel
lpc_ich                17144  0 
input_polldev          13896  1 lis3lv02d
hp_wmi                 18092  0 
sparse_keymap          13890  1 hp_wmi
i2c_algo_bit           13564  1 i915
serio_raw              13215  0 
wmi                    19256  1 hp_wmi
jmb38x_ms              17646  0 
memstick               16605  1 jmb38x_ms
microcode              23017  0 
video                  19652  1 i915
mac_hid                13253  0 
8192cu                646134  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
hid_generic            12540  0 
hid_logitech_dj        18767  0 
usbhid                 47346  1 hid_logitech_dj
hid                   105826  3 hid_generic,hid_logitech_dj,usbhid
ahci                   25879  2 
libahci                31606  1 ahci
r8169                  68716  0 
sdhci_pci              18721  0 
sdhci                  33141  1 sdhci_pci



I can't see neither rtl8192cu nor 8192cu as used. Now when I'm checking the device is disconnected on the list.

---

### Post by chili555 on 2013-12-14
> I can't see neither rtl8192cu nor 8192cu as used. Now when I'm checking the device is disconnected on the list. Here ya go:> ....
video 19652 1 i915
mac_hid 13253 0
[COLOR="#FF0000"]8192cu[/COLOR] 646134 0
lp 17799 0
parport 46562 3 parport_pc,ppdev,lp
hid_generic 12540 0
hid_logitech_dj 18767 0 
....And what do we see here??> ath9k 151796 0 ...and here?> ath9k_htc 92962 0 How many conflicting drivers can we load at one time?? Do you have an internal device that we ought to either troubleshoot and get going properly or did you make a few additions to /etc/modules or ... what??

May we have a peek?```
cat /etc/modules
```

---

### Post by hiteshhp on 2013-12-15
Hello Guys

Newbi on linux here. 
OS System: Ubuntu 12.04 LTS 64 bit 
Kernel: 3.8.0.29 generic
Wirelss USB adaptor : TP link TL-WN822N Version 3.0
Issue : Not installed any driver myself, just installed Ubuntu 12.04, can see wireless networks listed and when it does ask for password but then does not connect to network after sometime it asks for password again, password is definately correct but still can't connect.

Please help me to go to internet. Wireless router is far from room so can not connect it via Ethernet.

---

### Post by gringo.g on 2013-12-15
/etc/modules
> lp
rtc
8192cu

> [COLOR=#000000]How many conflicting drivers can we load at one time?? Do you have an internal device that we ought to either troubleshoot and get going properly or did you make a few additions to /etc/modules or ... what??[/COLOR]
Besides the WN822N and internal network card I have TP-Link WN722N with which I'm connecting to a network, cause WN822N doesn't work so far.

@[COLOR=#000000]hiteshhp
[/COLOR][http://www.ajaykumarsingh.com/linux/tp-link-tl-wn822n-300mbps-high-gain-wireless-n-usb-adapter-not-working-on-ubuntu-12-04.html](http://www.ajaykumarsingh.com/linux/tp-link-tl-wn822n-300mbps-high-gain-wireless-n-usb-adapter-not-working-on-ubuntu-12-04.html)

---

### Post by hiteshhp on 2013-12-15
Thanks gringo.g

It worked like a charm. Just for future ref, if i update Ubuntu with updated kernels, will i lose drivers again ? What should be done to preserve these drivers during upgrade.

Thanks

Regards,

Hitesh

---

### Post by chili555 on 2013-12-15
> **gringo.g said:**
> /etc/modules



Besides the WN822N and internal network card I have TP-Link WN722N with which I'm connecting to a network, cause WN822N doesn't work so far.

@[COLOR=#000000]hiteshhp
[/COLOR][http://www.ajaykumarsingh.com/linux/tp-link-tl-wn822n-300mbps-high-gain-wireless-n-usb-adapter-not-working-on-ubuntu-12-04.html](http://www.ajaykumarsingh.com/linux/tp-link-tl-wn822n-300mbps-high-gain-wireless-n-usb-adapter-not-working-on-ubuntu-12-04.html)I suggest you blacklist the internal assuming you have exhausted all efforts to get it to work properly:```
sudo -i
echo "blacklist ath9k"  >>  /etc/modprobe.d/blacklist.conf
exit
```Now detach the 722N so its driver can't interfer and reboot. Then run:```
cat /var/log/syslog | grep -e etwork -e 8192 | tail -n25  > wifi.txt
```Find the file wifi.txt in your user directory, hook up the 722N and post it here.

---

### Post by gringo.g on 2013-12-17
ath9k is my internal network card, am I right?

Content of wifi.txt:
> Dec 17 15:51:55 ProBook NetworkManager[1233]: <info> (eth0): exported as /org/freedesktop/NetworkManager/Devices/0
Dec 17 15:51:55 ProBook NetworkManager[1233]: <info> (eth0): now managed
Dec 17 15:51:55 ProBook NetworkManager[1233]: <info> (eth0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Dec 17 15:51:55 ProBook NetworkManager[1233]: <info> (eth0): bringing up device.
Dec 17 15:51:55 ProBook NetworkManager[1233]: <info> (eth0): preparing device.
Dec 17 15:51:55 ProBook NetworkManager[1233]: <info> (eth0): deactivating device (reason 'managed') [2]
Dec 17 15:51:55 ProBook NetworkManager[1233]: <info> Added default wired connection 'Po&#322;&#261;czenie przewodowe 1' for /sys/devices/pci0000:00/0000:00:1c.5/0000:25:00.0/net/eth0
Dec 17 15:53:20 ProBook NetworkManager[1233]: <info> WiFi now disabled by radio killswitch
Dec 17 15:53:24 ProBook NetworkManager[1233]: <info> WiFi now enabled by radio killswitch
Dec 17 15:53:28 ProBook NetworkManager[1233]: <info> WiFi now disabled by radio killswitch
Dec 17 15:53:34 ProBook NetworkManager[1233]: <info> disable requested (sleeping: no  enabled: yes)
Dec 17 15:53:34 ProBook NetworkManager[1233]: <info> sleeping or disabling...
Dec 17 15:53:34 ProBook NetworkManager[1233]: <info> (eth0): now unmanaged
Dec 17 15:53:34 ProBook NetworkManager[1233]: <info> (eth0): device state change: unavailable -> unmanaged (reason 'sleeping') [20 10 37]
Dec 17 15:53:34 ProBook NetworkManager[1233]: <info> (eth0): cleaning up...
Dec 17 15:53:34 ProBook NetworkManager[1233]: <info> (eth0): taking down device.
Dec 17 15:53:36 ProBook NetworkManager[1233]: <info> enable requested (sleeping: no  enabled: no)
Dec 17 15:53:36 ProBook NetworkManager[1233]: <info> waking up and re-enabling...
Dec 17 15:53:36 ProBook NetworkManager[1233]: <info> WWAN now enabled by management service
Dec 17 15:53:36 ProBook NetworkManager[1233]: <info> (eth0): now managed
Dec 17 15:53:36 ProBook NetworkManager[1233]: <info> (eth0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Dec 17 15:53:36 ProBook NetworkManager[1233]: <info> (eth0): bringing up device.
Dec 17 15:53:36 ProBook NetworkManager[1233]: <info> (eth0): preparing device.
Dec 17 15:53:36 ProBook NetworkManager[1233]: <info> (eth0): deactivating device (reason 'managed') [2]
Dec 17 15:53:40 ProBook NetworkManager[1233]: <info> WiFi now enabled by radio killswitch


---

### Post by chili555 on 2013-12-17
We see a lot of data here regarding your ethernet card. Was the ethernet cable detached at the time? Were you attempting to connect with the 822N only at the time? We see nothing useful related to wireless. Would you please try again?> ath9k is my internal network card, am I right?Correct. Do you mind if I ask why you are struggling with an external USB if you have an internal that is or can be made to work correctly?

---

### Post by gringo.g on 2013-12-17
Above commands I've used when WN822N was plugged in and 722N was unplugged, so should I try again with unplugged 822N?

I'm struggling with external USB cause internal has a very weak signal and my router is far a bit.

---

### Post by chili555 on 2013-12-17
> so should I try again with unplugged 822N?Certainly not. Aren't we trying to troubleshoot the 822N and not anything else?

With only the 822N inserted and with the ethernet detached, try to connect and then let us see:```
cat /var/log/syslog | grep wlan | tail -n25
```

---

### Post by gringo.g on 2013-12-17
Now, even WN722N can't connect with my network.

```
cat /var/log/syslog | grep wlan | tail -n25
```
> Dec 17 21:24:39 ProBook NetworkManager[1281]: <info> Activation (wlan2) Stage 1 of 5 (Device Prepare) complete.
Dec 17 21:24:39 ProBook NetworkManager[1281]: <info> Activation (wlan2) Stage 2 of 5 (Device Configure) starting...
Dec 17 21:24:39 ProBook NetworkManager[1281]: <info> (wlan2): device state change: prepare -> config (reason 'none') [40 50 0]
Dec 17 21:24:40 ProBook NetworkManager[1281]: <info> Activation (wlan2/wireless): access point 'Mateusz' has security, but secrets are required.
Dec 17 21:24:40 ProBook NetworkManager[1281]: <info> (wlan2): device state change: config -> need-auth (reason 'none') [50 60 0]
Dec 17 21:24:40 ProBook NetworkManager[1281]: <info> Activation (wlan2) Stage 2 of 5 (Device Configure) complete.
Dec 17 21:24:46 ProBook NetworkManager[1281]: <info> Activation (wlan2) Stage 1 of 5 (Device Prepare) scheduled...
Dec 17 21:24:46 ProBook NetworkManager[1281]: <info> Activation (wlan2) Stage 1 of 5 (Device Prepare) started...
Dec 17 21:24:46 ProBook NetworkManager[1281]: <info> (wlan2): device state change: need-auth -> prepare (reason 'none') [60 40 0]
Dec 17 21:24:46 ProBook NetworkManager[1281]: <info> Activation (wlan2) Stage 2 of 5 (Device Configure) scheduled...
Dec 17 21:24:46 ProBook NetworkManager[1281]: <info> Activation (wlan2) Stage 1 of 5 (Device Prepare) complete.
Dec 17 21:24:46 ProBook NetworkManager[1281]: <info> Activation (wlan2) Stage 2 of 5 (Device Configure) starting...
Dec 17 21:24:46 ProBook NetworkManager[1281]: <info> (wlan2): device state change: prepare -> config (reason 'none') [40 50 0]
Dec 17 21:24:46 ProBook NetworkManager[1281]: <info> Activation (wlan2/wireless): connection 'Mateusz' has security, and secrets exist.  No new secrets needed.
Dec 17 21:24:46 ProBook NetworkManager[1281]: <info> Activation (wlan2) Stage 2 of 5 (Device Configure) complete.
Dec 17 21:25:47 ProBook NetworkManager[1281]: <warn> Activation (wlan2/wireless): association took too long.
Dec 17 21:25:47 ProBook NetworkManager[1281]: <info> (wlan2): device state change: config -> need-auth (reason 'none') [50 60 0]
Dec 17 21:25:47 ProBook NetworkManager[1281]: <warn> Activation (wlan2/wireless): asking for new secrets
Dec 17 21:25:49 ProBook NetworkManager[1281]: <info> (wlan2): supplicant interface state: inactive -> disconnected
Dec 17 21:25:50 ProBook NetworkManager[1281]: <info> (wlan2): supplicant interface state: disconnected -> inactive
Dec 17 21:27:09 ProBook NetworkManager[1281]: <info> (wlan2): device state change: need-auth -> failed (reason 'no-secrets') [60 120 7]
Dec 17 21:27:09 ProBook NetworkManager[1281]: <warn> Activation (wlan2) failed for access point (Mateusz)
Dec 17 21:27:09 ProBook NetworkManager[1281]: <warn> Activation (wlan2) failed.
Dec 17 21:27:09 ProBook NetworkManager[1281]: <info> (wlan2): device state change: failed -> disconnected (reason 'none') [120 30 0]
Dec 17 21:27:09 ProBook NetworkManager[1281]: <info> (wlan2): deactivating device (reason 'none') [0]

Tail of blacklist.conf
> blacklist rtl8192cu
blacklist rtl8192c_common
blacklist rtlwifi
blacklist ath9k


/etc/modules
> lp
rtc
8192cu

Because it doesn't work still, so maybe delete all drivers (722 and 822) as well as wlan1 and wlan2 from ifconfig?

---

### Post by chili555 on 2013-12-17
> Because it doesn't work still, so maybe delete all drivers (722 and 822) as well as wlan1 and wlan2 from ifconfig? I was under the impression that the 722 was working properly:>  I have TP-Link WN722N with which I'm connecting to a network,Why not just use it and be done?

---

### Post by gringo.g on 2013-12-17
> [COLOR=#000000]Why not just use it and be done?[/COLOR]
WN822N gives a much better signal, WN722N is not enough. ;)

---

### Post by chili555 on 2013-12-17
My next suggestion is the backports driver suite. Please use the 722 connection and open a terminal:
```
sudo apt-get install build-essential linux-headers-generic
```

Download this file to your desktop: [http://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.12.2/backports-3.12.2-1.tar.bz2](http://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.12.2/backports-3.12.2-1.tar.bz2) Right-click it and select 'Extract Here.' Now back to the teminal:
```
cd ~/Desktop/backports-3.12-1
make defconfig-rtlwifi
make

```
Make takes a while depending on memory, CPU cores, et al. I generally refresh my beverage and check emails.
```
sudo make install
```

Detach the 722.

Now edit /etc/modules to delete the reference to 8192cu. Edit blacklist.conf to delete the rtl8192cu line. Reboot and let us hear your success!

---

### Post by gringo.g on 2014-02-20
Hi again, after 2 months. I haven't solved my problem yet, but now a situation is different a bit. 

I have internal WiFi adapter and I'd like to use my external TP-Link TL-WN822N. After attaching external adapter I can't connect with Internet, although I'm having a connection with my router. First:
```
uname -r
```
```
3.13.4-031304-generic
```

```
lsusb
```
```
Bus 002 Device 005: ID 0cf3:3005 Atheros Communications, Inc. AR3011 Bluetooth
Bus 002 Device 004: ID 0461:4dc7 Primax Electronics, Ltd 
Bus 002 Device 003: ID 046d:c52f Logitech, Inc. Unifying Receiver
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
**Bus 003 Device 004: ID 0bda:8178 Realtek Semiconductor Corp. RTL8192CU 802.11n WLAN Adapter**
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

```
lsmod
```
```
Module                  Size  Used by
rtl8192cu              68561  0 
rtl_usb                22809  1 rtl8192cu
rtlwifi                64281  2 rtl_usb,rtl8192cu
rtl8192c_common        58122  1 rtl8192cu
ctr                    13193  1 
ccm                    17856  1 
rfcomm                 74748  12 
parport_pc             32866  0 
bnep                   19884  2 
ppdev                  17711  0 
binfmt_misc            17508  1 
intel_rapl             19228  0 
arc4                   12573  4 
x86_pkg_temp_thermal    14269  0 
intel_powerclamp       19031  0 
ath9k                 166504  0 
coretemp               17728  0 
ath9k_common           13551  1 ath9k
ath9k_hw              462940  2 ath9k_common,ath9k
snd_hda_codec_hdmi     46898  1 
kvm_intel             144426  0 
snd_hda_codec_idt      59236  1 
snd_hda_intel          57222  3 
kvm                   468181  1 kvm_intel
ath                    29145  3 ath9k_common,ath9k,ath9k_hw
snd_hda_codec         199156  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
mac80211              654124  4 ath9k,rtl_usb,rtlwifi,rtl8192cu
crct10dif_pclmul       14250  0 
snd_hwdep              13613  1 snd_hda_codec
snd_pcm               107140  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
crc32_pclmul           13160  0 
snd_page_alloc         18798  2 snd_pcm,snd_hda_intel
ghash_clmulni_intel    13259  0 
hp_wmi                 18202  0 
snd_seq_midi           13324  0 
cryptd                 20530  1 ghash_clmulni_intel
sparse_keymap          13890  1 hp_wmi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30465  1 snd_seq_midi
uvcvideo               82247  0 
snd_seq                66061  2 snd_seq_midi_event,snd_seq_midi
btusb                  28326  0 
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
videobuf2_vmalloc      13216  1 uvcvideo
snd_timer              30038  2 snd_pcm,snd_seq
videobuf2_memops       13362  1 videobuf2_vmalloc
mei_me                 18578  0 
lp                     17799  0 
videobuf2_core         40972  1 uvcvideo
bluetooth             411140  22 bnep,btusb,rfcomm
cfg80211              509407  4 ath,ath9k,mac80211,rtlwifi
psmouse               108513  0 
snd                    69754  17 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_idt,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
mei                    82749  1 mei_me
parport                42481  3 lp,ppdev,parport_pc
videodev              139761  2 uvcvideo,videobuf2_core
microcode              23788  0 
dm_multipath           27401  0 
scsi_dh                14873  1 dm_multipath
hp_accel               26012  0 
joydev                 17575  0 
lpc_ich                21163  0 
serio_raw              13462  0 
lis3lv02d              20280  1 hp_accel
jmb38x_ms              18947  0 
input_polldev          13896  1 lis3lv02d
memstick               16968  1 jmb38x_ms
soundcore              12680  1 snd
mac_hid                13253  0 
dm_mirror              22356  0 
dm_region_hash         21010  1 dm_mirror
dm_log                 18527  2 dm_region_hash,dm_mirror
hid_generic            12548  0 
usbhid                 53067  0 
hid                   106254  3 hid_generic,usbhid
i915                  816909  3 
i2c_algo_bit           13564  1 i915
ahci                   30063  2 
drm_kms_helper         53224  1 i915
libahci                32277  1 ahci
r8169                  73299  0 
drm                   308397  4 i915,drm_kms_helper
mii                    13981  1 r8169
sdhci_pci              19241  0 
sdhci                  43409  1 sdhci_pci
wmi                    19363  1 hp_wmi
video                  19859  1 i915

```
ath9k it's my internal adapter.

then:
```
sudo apt-get install build-essential
```

Finally I downloaded drivers from Realtek website and I tried to compile them, but:
```
cc1: some warnings being treated as errors
make[2]: *** [/home/grzegorz/Pobrane/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.o] B&#322;&#261;d 1
make[1]: *** [_module_/home/grzegorz/Pobrane/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911] B&#322;&#261;d 2
make[1]: Opuszczenie katalogu `/usr/src/linux-headers-3.13.4-031304-generic'
make: *** [modules] B&#322;&#261;d 2
##################################################
Compile make driver error: 2
Please check error Mesg
##################################################

```
What to do now?

BTW, what do you think about this solution [https://github.com/pvaret/rtl8192cu-fixes?](https://github.com/pvaret/rtl8192cu-fixes?) I'm wondering about it, however I have 3.13.4 kernel, not 3.11.

---

### Post by chili555 on 2014-02-20
Before you proceed, I'd unload *ath9k*:```
sudo modprobe -r ath9k
```Check to see if any other of the *ath* family are still loaded and remove if necessary:```
lsmod | grep ath
```Now does the USB connect? If so, we'll blacklist *ath9k* and a few others and be all set.

---

### Post by gringo.g on 2014-02-20
To unload with modprobe? Not rmmod? Nevertheless, after that any other ath devices don't exist. It's a little strange, because I've connected with web via WN822N, but just after a while I lost it.

---

### Post by chili555 on 2014-02-20
> To unload with modprobe? Not rmmod?rmmod only unloads the specific module; modprobe -r removes the specific module and its dependencies. ```
depends:        ath9k_hw,mac80211,ath9k_common,cfg80211,ath
```> I've connected with web via WN822N, but just after while I lost it. Are there any interesting clues?```
cat /var/log/syslog | grep -e ethwork -e rtl | tail -n20
```

---

### Post by gringo.g on 2014-02-20
```
cat /var/log/syslog | grep -e ethwork -e rtl | tail -n20
```
```
Feb 21 03:29:30 ProBook kernel: [   16.508447] rtlwifi: Loading alternative firmware rtlwifi/rtl8192cufw.bin
Feb 21 03:29:30 ProBook kernel: [   16.521875] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
Feb 21 03:29:30 ProBook kernel: [   16.523195] rtlwifi: wireless switch is on
Feb  21 03:29:31 ProBook NetworkManager[770]: <info> rfkill2: found  WiFi radio killswitch (at  /sys/devices/pci0000:00/0000:00:1c.7/0000:26:00.0/usb3/3-1/3-1:1.0/ieee80211/phy0/rfkill2)  (driver rtl8192cu)
Feb 21 03:29:32 ProBook NetworkManager[770]: <info> (wlan1): new 802.11 WiFi device (driver: 'rtl8192cu' ifindex: 3)
Feb 21 03:29:32 ProBook kernel: [   19.288786] rtl8192cu: MAC auto ON okay!
Feb 21 03:29:32 ProBook kernel: [   19.488520] rtl8192cu: Tx queue select: 0x05
Feb 21 03:34:05 ProBook kernel: [   16.474621] rtl8192cu: Chip version 0x11
Feb 21 03:34:05 ProBook kernel: [   16.887396] rtl8192cu: MAC address: 64:66:b3:26:28:a0
Feb 21 03:34:05 ProBook kernel: [   16.887408] rtl8192cu: Board Type 0
Feb 21 03:34:05 ProBook kernel: [   16.888142] rtl_usb: rx_max_size 15360, rx_urb_num 8, in_ep 1
Feb 21 03:34:05 ProBook kernel: [   16.888203] rtl8192cu: Loading firmware rtlwifi/rtl8192cufw_TMSC.bin
Feb 21 03:34:05 ProBook kernel: [   16.888344] usbcore: registered new interface driver rtl8192cu
Feb 21 03:34:05 ProBook kernel: [   16.975487] rtlwifi: Loading alternative firmware rtlwifi/rtl8192cufw.bin
Feb 21 03:34:05 ProBook kernel: [   16.975705] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
Feb 21 03:34:05 ProBook kernel: [   16.977057] rtlwifi: wireless switch is on
Feb  21 03:34:06 ProBook NetworkManager[805]: <info> rfkill3: found  WiFi radio killswitch (at  /sys/devices/pci0000:00/0000:00:1c.7/0000:26:00.0/usb3/3-1/3-1:1.0/ieee80211/phy0/rfkill3)  (driver rtl8192cu)
Feb 21 03:34:06 ProBook NetworkManager[805]: <info> (wlan1): new 802.11 WiFi device (driver: 'rtl8192cu' ifindex: 4)
Feb 21 03:34:06 ProBook kernel: [   19.825703] rtl8192cu: MAC auto ON okay!
Feb 21 03:34:06 ProBook kernel: [   20.025546] rtl8192cu: Tx queue select: 0x05
```

---

### Post by chili555 on 2014-02-20
No action from Network Manager; let's dig deeper, and spell correctly!```
cat /var/log/syslog | grep  etwork | tail -n20
```I am a bit worried about this little gem:> rtl8192cu: Loading firmware rtlwifi/rtl8192cufw_TMSC.bin
<snip>
Loading alternative firmware rtlwifi/rtl8192cufw.binWhat does your version of the driver say about firmware?```
modinfo rtl8192cu | grep firm
```Mine, on a 3.11.0-xx kernel, says:```
firmware:       rtlwifi/rtl8192cufw.bin
```I'm not quite sure what the TMSC version is all about. Googling...

---

### Post by gringo.g on 2014-02-20
Here you are:
```
Feb 21 04:10:24 ProBook NetworkManager[808]: <warn> sysctl: failed to open '/proc/sys/net/ipv6/conf/wlan0/use_tempaddr': (2) Nie ma takiego pliku ani katalogu
Feb 21 04:10:24 ProBook NetworkManager[808]: <warn> (3) failed to find interface name for index
Feb 21 04:10:24 ProBook NetworkManager[808]: (nm-system.c:766):nm_system_iface_get_flags: runtime check failed: (iface != NULL)
Feb 21 04:10:24 ProBook NetworkManager[808]: <error> [1392952224.801517] [nm-system.c:768] nm_system_iface_get_flags(): (unknown): failed to get interface link object
Feb 21 04:10:24 ProBook NetworkManager[808]: <warn> (3) failed to find interface name for index
Feb 21 04:10:24 ProBook NetworkManager[808]: (nm-system.c:766):nm_system_iface_get_flags: runtime check failed: (iface != NULL)
Feb 21 04:10:24 ProBook NetworkManager[808]: <error> [1392952224.801653] [nm-system.c:768] nm_system_iface_get_flags(): (unknown): failed to get interface link object
Feb 21 04:10:24 ProBook NetworkManager[808]: <info> (wlan0): bringing up device.
Feb 21 04:10:24 ProBook NetworkManager[808]: <warn> (3) failed to find interface name for index
Feb 21 04:10:24 ProBook NetworkManager[808]: nm_system_iface_flush_routes: assertion 'iface != NULL' failed
Feb 21 04:10:24 ProBook NetworkManager[808]: <warn> (3) failed to find interface name for index
Feb 21 04:10:24 ProBook NetworkManager[808]: <info> Policy set 'Automatyczne Dom' (wlan1) as default for IPv4 routing and DNS.
Feb 21 04:10:24 ProBook NetworkManager[808]: <info> Writing DNS information to /sbin/resolvconf
Feb 21 04:10:24 ProBook NetworkManager[808]: <info> (wlan0): cleaning up...
Feb 21 04:10:24 ProBook NetworkManager[808]: <warn> (3) failed to find interface name for index
Feb 21 04:10:24 ProBook NetworkManager[808]: (nm-system.c:766):nm_system_iface_get_flags: runtime check failed: (iface != NULL)
Feb 21 04:10:24 ProBook NetworkManager[808]: <error> [1392952224.812464] [nm-system.c:768] nm_system_iface_get_flags(): (unknown): failed to get interface link object
Feb 21 04:10:24 ProBook NetworkManager[808]: <info> Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Feb 21 04:10:24 ProBook NetworkManager[808]:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/pci0000:00/0000:00:1c.3/0000:24:00.0/net/wlan0, iface: wlan0)
Feb 21 04:10:24 ProBook NetworkManager[808]: <info> radio killswitch /sys/devices/pci0000:00/0000:00:1c.3/0000:24:00.0/ieee80211/phy1/rfkill2 disappeared


```

```
firmware:       rtlwifi/rtl8192cufw_TMSC.bin
firmware:       rtlwifi/rtl8192cufw_B.bin
firmware:       rtlwifi/rtl8192cufw_A.bin
firmware:       rtlwifi/rtl8192cufw.bin


```

---

### Post by chili555 on 2014-02-20
> BTW, what do you think about this solution [https://github.com/pvaret/rtl8192cu-fixes?](https://github.com/pvaret/rtl8192cu-fixes?) I'm wondering about it, however I have 3.13.4 kernel, not 3.11. It's worth a try. There are pretty complete instructions there but if you need any additional guidance, I'll be happy to help. I think I'd probably compile it through 'make' first before you do the whole dkms route:```
sudo apt-get install linux-headers-generic build-essential git dkms
git clone https://github.com/pvaret/rtl8192cu-fixes.git
cd rtl8192cu-fixes
make
```If it ends in a module .ko and not an error, I'd then:```
make clean
cd ~
```Then start here in his instructions: 'Set it up as a DKMS module:'

The rtl8192cu is a bit buggy.

---

### Post by gringo.g on 2014-02-21
I used this solution:
```
sudo apt-get install linux-headers-generic build-essential dkmsgit clone https://github.com/pvaret/rtl8192cu-fixes.git
sudo dkms add ./rtl8192cu-fixes
sudo dkms install 8192cu/1.8
sudo depmod -a
sudo cp ./rtl8192cu-fixes/blacklist-native-rtl8192.conf /etc/modprobe.d/
```

Let's have a look to logs.
```
cat /var/log/syslog | grep -e ethwork -e rtl | tail -n20Feb 21 12:33:42 ProBook kernel: [  456.092930] rtl8192c_set_FwPwrMode_cmd(): Mode = 1, SmartPS = 2
Feb 21 12:33:42 ProBook kernel: [  456.264552] rtl8192c_set_FwPwrMode_cmd(): Mode = 0, SmartPS = 0
Feb 21 12:33:46 ProBook kernel: [  460.102736] rtl8192c_set_FwPwrMode_cmd(): Mode = 1, SmartPS = 2
Feb 21 12:33:48 ProBook kernel: [  462.108329] rtl8192c_set_FwPwrMode_cmd(): Mode = 0, SmartPS = 0
Feb 21 12:33:56 ProBook kernel: [  470.128437] rtl8192c_set_FwPwrMode_cmd(): Mode = 1, SmartPS = 2
Feb 21 12:33:58 ProBook kernel: [  472.134093] rtl8192c_set_FwPwrMode_cmd(): Mode = 0, SmartPS = 0
Feb 21 12:34:08 ProBook kernel: [  482.159334] rtl8192c_set_FwPwrMode_cmd(): Mode = 1, SmartPS = 2
Feb 21 12:34:10 ProBook kernel: [  484.164997] rtl8192c_set_FwPwrMode_cmd(): Mode = 0, SmartPS = 0
Feb 21 12:34:12 ProBook kernel: [  486.169575] rtl8192c_set_FwPwrMode_cmd(): Mode = 1, SmartPS = 2
Feb 21 12:34:14 ProBook kernel: [  488.174866] rtl8192c_set_FwPwrMode_cmd(): Mode = 0, SmartPS = 0
Feb 21 12:34:22 ProBook kernel: [  496.195132] rtl8192c_set_FwPwrMode_cmd(): Mode = 1, SmartPS = 2
Feb 21 12:34:24 ProBook kernel: [  498.200918] rtl8192c_set_FwPwrMode_cmd(): Mode = 0, SmartPS = 0
Feb 21 12:34:26 ProBook kernel: [  500.205375] rtl8192c_set_FwPwrMode_cmd(): Mode = 1, SmartPS = 2
Feb 21 12:34:32 ProBook kernel: [  506.220979] rtl8192c_set_FwPwrMode_cmd(): Mode = 0, SmartPS = 0
Feb 21 12:34:36 ProBook kernel: [  510.230923] rtl8192c_set_FwPwrMode_cmd(): Mode = 1, SmartPS = 2
Feb 21 12:34:38 ProBook kernel: [  512.236465] rtl8192c_set_FwPwrMode_cmd(): Mode = 0, SmartPS = 0
Feb 21 12:34:54 ProBook kernel: [  528.276894] rtl8192c_set_FwPwrMode_cmd(): Mode = 1, SmartPS = 2
Feb 21 12:34:55 ProBook kernel: [  528.553587] rtl8192c_set_FwPwrMode_cmd(): Mode = 0, SmartPS = 0
Feb 21 12:34:58 ProBook kernel: [  532.287205] rtl8192c_set_FwPwrMode_cmd(): Mode = 1, SmartPS = 2
Feb 21 12:35:00 ProBook kernel: [  534.292703] rtl8192c_set_FwPwrMode_cmd(): Mode = 0, SmartPS = 0

```

```
cat /var/log/syslog | grep  etwork | tail -n20
Feb 21 12:26:33 ProBook NetworkManager[785]: <info> (wlan0): device state change: secondaries -> activated (reason 'none') [90 100 0]
Feb 21 12:26:33 ProBook NetworkManager[785]: <info> Policy set 'Automatyczne Dom' (wlan0) as default for IPv4 routing and DNS.
Feb 21 12:26:33 ProBook NetworkManager[785]: <info> Writing DNS information to /sbin/resolvconf
Feb 21 12:26:33 ProBook NetworkManager[785]: <info> Activation (wlan0) successful, device activated.
Feb 21 12:26:34 ProBook NetworkManager[785]: <warn> error monitoring device for netlink events: b&#322;&#261;d podczas przetwarzania komunikatu netlink: Object busy
Feb 21 12:26:45 ProBook NetworkManager[785]: <warn> error monitoring device for netlink events: b&#322;&#261;d podczas przetwarzania komunikatu netlink: Object busy
Feb 21 12:26:50 ProBook NetworkManager[785]: <info> (wlan1): IP6 addrconf timed out or failed.
Feb 21 12:26:50 ProBook NetworkManager[785]: <info> Activation (wlan1) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Feb 21 12:26:50 ProBook NetworkManager[785]: <info> Activation (wlan1) Stage 4 of 5 (IPv6 Configure Timeout) started...
Feb 21 12:26:50 ProBook NetworkManager[785]: <info> Activation (wlan1) Stage 4 of 5 (IPv6 Configure Timeout) complete.
Feb 21 12:26:52 ProBook NetworkManager[785]: <info> (wlan0): IP6 addrconf timed out or failed.
Feb 21 12:26:52 ProBook NetworkManager[785]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Feb 21 12:26:52 ProBook NetworkManager[785]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) started...
Feb 21 12:26:52 ProBook NetworkManager[785]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) complete.
Feb 21 12:26:53 ProBook NetworkManager[785]: <info> (wlan0): device state change: activated -> disconnected (reason 'user-requested') [100 30 39]
Feb 21 12:26:53 ProBook NetworkManager[785]: <info> (wlan0): deactivating device (reason 'user-requested') [39]
Feb 21 12:26:53 ProBook NetworkManager[785]: <info> (wlan0): canceled DHCP transaction, DHCP client pid 1332
Feb 21 12:26:53 ProBook NetworkManager[785]: <info> Policy set 'Automatyczne Dom' (wlan1) as default for IPv4 routing and DNS.
Feb 21 12:26:53 ProBook NetworkManager[785]: <info> Writing DNS information to /sbin/resolvconf
Feb 21 12:26:54 ProBook NetworkManager[785]: <info> (wlan0): supplicant interface state: completed -> disconnected

```Here are 2 warns - what is it?

Generally it seems that it works pretty well, although a ping is slightly greater (a few milliseconds) than using internal WiFi. I guess it's normal.

Two questions yet:
1. Now should I add ath9k to blacklist?
2. Before using the solution compiling rtl8192cu drivers is necessary, isn't it?

---

### Post by chili555 on 2014-02-21
> **gringo.g said:**
> Here are 2 warns - what is it?

Generally it seems that it works pretty well, although a ping is slightly greater (a few milliseconds) than using internal WiFi. I guess it's normal.

Two questions yet:
1. Now should I add ath9k to blacklist?
2. Before using the solution compiling rtl8192cu drivers is necessary, isn't it?I don't know what the warnings are; if your device seems to work as expected, I wouldn't bother with it. 

Yes, I'd add ath9k to the blacklist. If you need some additional guidance, post back and I'll be happy to help. 

I am not sure what you mean here: 'Before using the solution compiling rtl8192cu drivers is necessary, isn't it?' Please clarify.

Ping times will differ slightly between any two devices.

---

### Post by gringo.g on 2014-02-21
> **chili555 said:**
> I am not sure what you mean here: 'Before using the solution compiling rtl8192cu drivers is necessary, isn't it?' Please clarify.
I mean first I need to compile drivers and then use [this solution]("https://github.com/pvaret/rtl8192cu-fixes?") to proper work my external adapter. Am I right?

---

### Post by chili555 on 2014-02-21
> **gringo.g said:**
> I mean first I need to compile drivers and then use [this solution]("https://github.com/pvaret/rtl8192cu-fixes?") to proper work my external adapter. Am I right?I thought you did exactly that already. Your earlier post says:> I used this solution:
.....
Generally it seems that it works pretty well,
Did you do it? Did it work? If you did, I think you are all set.

---

### Post by gringo.g on 2014-02-21
Haha, I've done it but I'm asking in general in order to know in the future :P

---

### Post by chili555 on 2014-02-21
> **gringo.g said:**
> Haha, I've done it but I'm asking in general in order to know in the future :PThe dkms process should make the driver carry over throughout regular updates without the need to recompile. If you decide to reinstall, then that is the correct process.

---

### Post by gringo.g on 2014-02-21
Okay, thanks for all!

---

### Post by duartevr on 2014-10-17
I don't even have this issue but I thoroughly enjoyed reading this exchange. Congratulations to both for being awesome humans.

---

### Post by ramious on 2014-10-27
Chili, I have read through this thread and am wondering if i should try the solution listed here. I am on 14.04 with rtl8192cu , using a TP Link TL-WN822N dual antana. Ubuntu is working with this but my signal strength is low and stability of the connection is spotty at best. Would you recommend I thy the before mentioned solution?

---

### Post by chili555 on 2014-10-27
> **ramious said:**
> Chili, I have read through this thread and am wondering if i should try the solution listed here. I am on 14.04 with rtl8192cu , using a TP Link TL-WN822N dual antana. Ubuntu is working with this but my signal strength is low and stability of the connection is spotty at best. Would you recommend I thy the before mentioned solution?Absolutely. Let me know if you get stuck or need additional guidance.

---

### Post by ramious on 2014-10-27
> **chili555 said:**
> Absolutely. Let me know if you get stuck or need additional guidance.


Thank you Chillii. I'll get started on this later this evening and post back with the results. You really do so much and have helped me with other wireless cards with out even knowing it, I just want to say a great Thank You for all you do for our community!!!

---

### Post by ramious on 2014-10-27
> **chili555 said:**
> Absolutely. Let me know if you get stuck or need additional guidance.

Ok I am ready to get started on this just one pre question. In an earlier post . he talked about compiling the rtl8192cu driver "Before using the solution compiling rtl8192cu drivers is necessary, isn't it?"
this is what i currently have , can i just proceed the the solution or are there other pre steps i should take ?

ramious@ramious-ET1330:~$ lsusb
Bus 001 Device 003: ID 0bda:0181 Realtek Semiconductor Corp. 
Bus 001 Device 004: ID 0bda:8178 Realtek Semiconductor Corp. RTL8192CU 802.11n WLAN Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 002: ID 046d:c05a Logitech, Inc. M90/M100 Optical Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by ramious on 2014-10-27
Never Mind Chilii and thank you both gents. this worked like a charm. I have tried another solution similar  to this and on reboot the OS would not see the device. but this worked. Now instead of 1MB and 18MB a sec. I am locked in at a full 54MB a sec and running great. I am about to re-install Ubuntu one more time and completely remove my Win OS . Yey!!!!!!!

---

### Post by chili555 on 2014-10-27
> **ramious said:**
> Never Mind Chilii and thank you both gents. this worked like a charm. I have tried another solution similar  to this and on reboot the OS would not see the device. but this worked. Now instead of 1MB and 18MB a sec. I am locked in at a full 54MB a sec and running great. I am about to re-install Ubuntu one more time and completely remove my Win OS . Yey!!!!!!!Awesome! Glad it's working.

---

