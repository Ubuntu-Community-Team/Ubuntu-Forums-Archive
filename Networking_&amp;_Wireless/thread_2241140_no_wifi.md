---
title: "no wifi"
date: 2014-08-24
forum: Networking &amp; Wireless
---

### Post by Laima on 2014-08-24
i cant connect any wireless internet. and i cant tur on/off wireless with fn+f2. it shows that my wireless is off. what can i do?
i am new. and can someone help me?

---

### Post by praseodym on 2014-08-24
Hi,

please open a terminal and show the outputs of these commands:
```

lspci -nnk | grep -iA2 net
lsusb
rfkill list
iwconfig
lsmod
```
Does LAN work? What computer is it?

---

### Post by Laima on 2014-08-24
laima@laima-Inspiron-3521:~$ lspci -nnk |grep -iA2 net
07:00.0 Ethernet controller [0200]: RealtekSemiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller[10ec:8136] (rev 05)
            Subsystem:Dell Device [1028:0598]
            Kerneldriver in use: r8169
--
08:00.0 Network controller [0280]: QualcommAtheros QCA9565 / AR9565 Wireless Network Adapter [168c:0036] (rev 01)
            Subsystem:Dell Device [1028:020c]
 



laima@laima-Inspiron-3521:~$ lsusb
Bus 001 Device 021: ID 0cf3:0036 AtherosCommunications, Inc.
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 LinuxFoundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 LinuxFoundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 LinuxFoundation 3.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp.Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp.Integrated Rate Matching Hub
Bus 001 Device 004: ID 0bda:0129 RealtekSemiconductor Corp.
Bus 001 Device 005: ID 0c45:64ad Microdia
 




laima@laima-Inspiron-3521:~$ rfkill list
0: dell-wifi: Wireless LAN
            Softblocked: no
            Hardblocked: no
1: dell-bluetooth: Bluetooth
            Softblocked: no
            Hardblocked: no
9: hci0: Bluetooth
            Softblocked: no
            Hardblocked: no
 



laima@laima-Inspiron-3521:~$ iwconfig
lo       no wireless extensions.
 
eth0     no wireless extensions.
 




laima@laima-Inspiron-3521:~$ lsmod
Module                  Size  Used by
snd_hda_codec_hdmi     32193 1
snd_hda_codec_realtek    73693 1
joydev                 17693  0
rfcomm                 47604  12
bnep                   18281  2
parport_pc             32866  0
ppdev                  17113  0
btusb                  18332  2
dell_wmi               12681  0
sparse_keymap          13890 1 dell_wmi
snd_hda_intel          33327 3
snd_hda_codec         134156 3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              17764  1 snd_hda_codec
snd_pcm               97275  3snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
uvcvideo               72627  0
videodev               98259  1 uvcvideo
v4l2_compat_ioctl32    17128 1 videodev
rts5139               351188  0
snd_seq_midi           13324  0
dm_multipath           23275  0
dell_laptop            18119  0
fglrx                6725632  125
dcdbas                 14490  1 dell_laptop
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899 1 snd_seq_midi
snd_seq                61929  2 snd_seq_midi,snd_seq_midi_event
ath3k                  12910  0
bluetooth             180113  24 rfcomm,bnep,btusb,ath3k
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540 3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                98051  0
serio_raw              13211  0
snd                    79041  16snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i915                  478689  2
soundcore              15091  1 snd
snd_page_alloc         18529 2 snd_hda_intel,snd_pcm
mei                    41616  0
drm_kms_helper         46978 1 i915
drm                   241971  3 i915,drm_kms_helper
i2c_algo_bit           13423  1 i915
wmi                    19256  1 dell_wmi
video                  19651  1 i915
mac_hid                13253  0
lp                     17799  0
parport                46562  3 parport_pc,ppdev,lp
r8169                  62190  0
dm_raid45              78155  0
xor                    12894  1 dm_raid45
dm_mirror              22203  0
dm_region_hash         20961 1 dm_mirror
dm_log                 18564  3 dm_raid45,dm_mirror,dm_region_hash
btrfs                 653116  0
zlib_deflate           27139  1 btrfs
libcrc32c              12644  1 btrfs



and it show that my internet is disabled. it is dell inspiron 15 (3521). with ubuntu 12.04

---

### Post by praseodym on 2014-08-24
The driver is not loaded:
```

sudo modprobe -v ath9k
```
If it works make it permanent:
```

echo ath9k | sudo tee -a /etc/modules
```

---

### Post by Laima on 2014-08-24
i wrote first but nothing changed. what could change?

---

### Post by praseodym on 2014-08-24
Lets check:
```

sudo service network-manager restart
lsmod
ifconfig -a
iwconfig
cat /etc/resolv.conf
```

---

### Post by Laima on 2014-08-24
laima@laima-Inspiron-3521:~$ sudo servicenetwork-manager restart
network-manager stop/waiting
network-manager start/running, process 19035
 
but it still showed that wireless is offline
 
 
laima@laima-Inspiron-3521:~$ lsmod
Module                  Size  Used by
usbhid                 47238  0
hid                    99883  1usbhid
ath9k                 132556  0
mac80211              506862  1 ath9k
ath9k_common           14053  1 ath9k
ath9k_hw              411239  2 ath9k,ath9k_common
ath                    24067  3 ath9k,ath9k_common,ath9k_hw
cfg80211             205774  3 ath9k,mac80211,ath
nls_iso8859_1          12713 0
nls_cp437              16991  0
vfat                   17585  0
fat                    61512  1 vfat
usb_storage            49198  0
snd_hda_codec_hdmi     32193 1
snd_hda_codec_realtek    73693 1
joydev                 17693  0
rfcomm                 47604  12
bnep                   18281  2
parport_pc             32866  0
ppdev                  17113  0
btusb                  18332  2
dell_wmi               12681  0
sparse_keymap          13890 1 dell_wmi
snd_hda_intel          33327 3
snd_hda_codec         134156 3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              17764  1 snd_hda_codec
snd_pcm                97275  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
uvcvideo               72627  0
videodev               98259  1 uvcvideo
v4l2_compat_ioctl32    17128 1 videodev
rts5139               351188  0
snd_seq_midi           13324  0
dm_multipath           23275  0
dell_laptop            18119  0
fglrx                6725632  133
dcdbas                 14490  1 dell_laptop
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899 1 snd_seq_midi
snd_seq                61929  2 snd_seq_midi,snd_seq_midi_event
ath3k                  12910  0
bluetooth             180113  24 rfcomm,bnep,btusb,ath3k
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540 3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                98051  0
serio_raw              13211  0
snd                    79041  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i915                  478689  2
soundcore              15091  1 snd
snd_page_alloc         18529 2 snd_hda_intel,snd_pcm
mei                    41616  0
drm_kms_helper         46978 1 i915
drm                   241971  3 i915,drm_kms_helper
i2c_algo_bit           13423  1 i915
wmi                    19256  1 dell_wmi
video                  19651  1 i915
mac_hid               13253  0
lp                     17799  0
parport                46562  3 parport_pc,ppdev,lp
r8169                  62190  0
dm_raid45              78155  0
xor                    12894  1 dm_raid45
dm_mirror              22203  0
dm_region_hash         20961 1 dm_mirror
dm_log                 18564  3 dm_raid45,dm_mirror,dm_region_hash
btrfs                 653116  0
zlib_deflate           27139  1 btrfs
libcrc32c              12644  1 btrfs
 
laima@laima-Inspiron-3521:~$ ifconfig -a
eth0     Link encap:Ethernet  HWaddr34:17:eb:57:a1:60  
         UP BROADCAST MULTICAST MTU:1500  Metric:1
         RX packets:0 errors:0 dropped:0 overruns:0 frame:0
         TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
         collisions:0 txqueuelen:1000
         RX bytes:0 (0.0 B)  TX bytes:0(0.0 B)
         Interrupt:43 Base address:0x8000
 
lo       Link encap:Local Loopback  
         inet addr:127.0.0.1 Mask:255.0.0.0
         inet6 addr: ::1/128 Scope:Host
         UP LOOPBACK RUNNING MTU:16436  Metric:1
         RX packets:5100 errors:0 dropped:0 overruns:0 frame:0
         TX packets:5100 errors:0 dropped:0 overruns:0 carrier:0
         collisions:0 txqueuelen:0
         RX bytes:415672 (415.6 KB)  TXbytes:415672 (415.6 KB)
 
 
laima@laima-Inspiron-3521:~$ iwconfig
lo       no wireless extensions.
 
eth0     no wireless extensions.
 
laima@laima-Inspiron-3521:~$ cat/etc/resolv.conf
# Dynamic resolv.conf(5) file for glibcresolver(3) generated by resolvconf(8)
#    DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN

---

### Post by praseodym on 2014-08-24
Which Ubuntu version is it? For 14.04:
```

sudo apt-get install --reinstall linux-headers-generic build-essential
mkdir ~/driver
cd ~/driver
wget www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.14/backports-3.14-1.tar.xz
tar xvf backports-3.14-1.tar.xz
cd backports-3.14-1
make defconfig-ath9k
make
sudo make install
```
Reboot.

---

### Post by Laima on 2014-08-24
it is 12.04

---

### Post by varunendra on 2014-08-25
Hello Laima,

It seems you are using a very old kernel. You can compile a backported driver that supports your card following this post : [http://ubuntuforums.org/showpost.php?p=12866455](http://ubuntuforums.org/showpost.php?p=12866455) (replace the package name "backports-3.13-rc2-1" with "backports-3.12.8-1").

Alternatively, you may choose to do a clean install of either 12.04.5 or 14.04.1. Although there are other options in-between, like upgrading your [Hardware Enablement Stack]("https://wiki.ubuntu.com/Kernel/LTSEnablementStack"), but I personally don't recommend them due to possible breakage of functionality (none, or a few, or entire OS in some cases).

---

### Post by Laima on 2014-08-25
[COLOR=#000000]If i dont have cable internet what should i do?

Before compiling the driver, make sure you have necessary support packages installed. To do so, open a terminal (Ctrl-Alt-T) and install/reinstall the following (while being connected to internet using your cable connection) -[/COLOR]
[COLOR=#000000]Code:
sudo apt-get install --reinstall linux-headers-generic build-essential[/COLOR]

---

### Post by praseodym on 2014-08-25
In this case its easier to install the respective mainline kernel directly which contains the driver:

For 32bit:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.14.1-trusty/linux-headers-3.14.1-031401-generic_3.14.1-031401.201404141220_i386.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.14.1-trusty/linux-headers-3.14.1-031401-generic_3.14.1-031401.201404141220_i386.deb)
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.14.1-trusty/linux-image-3.14.1-031401-generic_3.14.1-031401.201404141220_i386.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.14.1-trusty/linux-image-3.14.1-031401-generic_3.14.1-031401.201404141220_i386.deb)

For 64bit:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.14.1-trusty/linux-headers-3.14.1-031401-generic_3.14.1-031401.201404141220_amd64.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.14.1-trusty/linux-headers-3.14.1-031401-generic_3.14.1-031401.201404141220_amd64.deb)
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.14.1-trusty/linux-image-3.14.1-031401-generic_3.14.1-031401.201404141220_amd64.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.14.1-trusty/linux-image-3.14.1-031401-generic_3.14.1-031401.201404141220_amd64.deb)

For both necessary:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.14.1-trusty/linux-headers-3.14.1-031401_3.14.1-031401.201404141220_all.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.14.1-trusty/linux-headers-3.14.1-031401_3.14.1-031401.201404141220_all.deb)

Save the three packages in "Downloads" and install via
```

sudo dpkg -i ~/Downloads/*.deb
```
Reboot.

---

### Post by varunendra on 2014-08-25
> **Laima said:**
> If i dont have cable internet what should i do?

> **praseodym said:**
> In this case its easier to install the respective mainline kernel directly which contains the driver..
This ^.

Although keep in mind that jumping to a much newer kernel manually has the potential to break some functionality. It replaces entire engine that the OS is running upon, while installing the backported driver only replaces the particular driver we need. So it is much easier, but not the safest.

However, the good part is that in case something breaks, it is quite easy to just revert back to the older kernel by booting into it, and removing the newer one, then start over using a different solution.

---

### Post by Laima on 2014-08-26
i need to download backports- 3.12.8-1?

---

### Post by varunendra on 2014-08-26
You can, you don't have to. Usually the latest one is recommended, but even 3.12 should solve the purpose.

Are you willing to try the backports way? If yes, how are you planning to get the headers and build-essential?

Does this give you any download URIs at the bottom of the output? -
```
apt-get install --print-uris linux-headers-generic build-essential
```

---

### Post by Laima on 2014-08-26
[COLOR=#000000]I did this. what do i need to do next?

In this case its easier to install the respective mainline kernel directly which contains the driver:[/COLOR]

[COLOR=#000000]For 32bit:[/COLOR]

[http://kernel.ubuntu.com/~kernel-ppa...41220_i386.deb]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.14.1-trusty/linux-headers-3.14.1-031401-generic_3.14.1-031401.201404141220_i386.deb")
[http://kernel.ubuntu.com/~kernel-ppa...41220_i386.deb]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.14.1-trusty/linux-image-3.14.1-031401-generic_3.14.1-031401.201404141220_i386.deb")

[COLOR=#000000]For 64bit:[/COLOR]
[http://kernel.ubuntu.com/~kernel-ppa...1220_amd64.deb]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.14.1-trusty/linux-headers-3.14.1-031401-generic_3.14.1-031401.201404141220_amd64.deb")
[http://kernel.ubuntu.com/~kernel-ppa...1220_amd64.deb]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.14.1-trusty/linux-image-3.14.1-031401-generic_3.14.1-031401.201404141220_amd64.deb")

[COLOR=#000000]For both necessary:[/COLOR]
[http://kernel.ubuntu.com/~kernel-ppa...141220_all.deb]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.14.1-trusty/linux-headers-3.14.1-031401_3.14.1-031401.201404141220_all.deb")

[COLOR=#000000]Save the three packages in "Downloads" and install via[/COLOR]
[COLOR=#000000]Code:
sudo dpkg -i ~/Downloads/*.deb[/COLOR]
[COLOR=#000000]Reboot.[/COLOR]

---

### Post by praseodym on 2014-08-26
Check now:
```

uname -a
lspci -nnk | grep -iA2 net
lsmod
iwconfig
cat /etc/resolv.conf
rfkill list
```

---

### Post by Laima on 2014-08-26
i have this

```
laima@laima-Inspiron-3521:~$ uname -a
Linux laima-Inspiron-3521 3.2.0-67-generic#101-Ubuntu SMP Tue Jul 15 17:46:11 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
 

laima@laima-Inspiron-3521:~$ lspci -nnk |grep -iA2 net
07:00.0 Ethernet controller [0200]: RealtekSemiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller[10ec:8136] (rev 05)
            Subsystem:Dell Device [1028:0598]
            Kerneldriver in use: r8169
--
08:00.0 Network controller [0280]: QualcommAtheros QCA9565 / AR9565 Wireless Network Adapter [168c:0036] (rev 01)
            Subsystem:Dell Device [1028:020c]
 

laima@laima-Inspiron-3521:~$ lsmod
Module                  Size  Used by
nls_iso8859_1          12713 1
nls_cp437              16991  1
vfat                   17585  1
fat                    61512  1 vfat
snd_hda_codec_hdmi     32193 1
snd_hda_codec_realtek    73693 1
joydev                 17693  0
parport_pc             32866  0
ppdev                  17113  0
rfcomm                 47604  12
bnep                   18281  2
btusb                  18332  2
snd_hda_intel          33327 3
snd_hda_codec         134156 3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              17764  1 snd_hda_codec
snd_pcm                97275  3snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899 1 snd_seq_midi
dell_wmi               12681  0
sparse_keymap          13890 1 dell_wmi
snd_seq                61929  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540 3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    79041  16snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
dell_laptop            18119  0
dm_multipath           23275  0
fglrx                6725632  111
dcdbas                 14490  1 dell_laptop
rts5139               351188  0
uvcvideo               72627  0
videodev               98259  1 uvcvideo
psmouse                98051  0
v4l2_compat_ioctl32    17128 1 videodev
serio_raw              13211 0
mei                    41616  0
i915                  478689  2
ath3k                  12910  0
bluetooth             180113  24 rfcomm,bnep,btusb,ath3k
drm_kms_helper         46978 1 i915
drm                   241971  3 i915,drm_kms_helper
soundcore              15091  1 snd
snd_page_alloc         18529 2 snd_hda_intel,snd_pcm
i2c_algo_bit           13423  1 i915
wmi                    19256  1 dell_wmi
mac_hid                13253  0
video                  19651  1 i915
lp                     17799  0
parport                46562 3 parport_pc,ppdev,lp
usb_storage            49198  1
dm_raid45              78155  0
xor                    12894  1 dm_raid45
dm_mirror              22203  0
dm_region_hash         20961 1 dm_mirror
dm_log                 18564  3 dm_raid45,dm_mirror,dm_region_hash
r8169                  62190  0
btrfs                 653116  0
zlib_deflate           27139  1 btrfs
libcrc32c              12644  1 btrfs
 
laima@laima-Inspiron-3521:~$ iwconfig
lo       no wireless extensions.
 
eth0     no wireless extensions.
 

laima@laima-Inspiron-3521:~$ cat/etc/resolv.conf
 
# Dynamic resolv.conf(5) file for glibcresolver(3) generated by resolvconf(8)
#    DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN


laima@laima-Inspiron-3521:~$ rfkill list
 
0: dell-wifi: Wireless LAN
            Softblocked: no
            Hardblocked: no
1: dell-bluetooth: Bluetooth
            Softblocked: no
            Hardblocked: no
3: hci0: Bluetooth
            Softblocked: no
            Hardblocked: no
```

---

### Post by praseodym on 2014-08-26
Didn't you install the 3 packages (64 bit)?

---

### Post by Laima on 2014-08-27
but there is only one for 64bit

---

### Post by praseodym on 2014-08-27
Post #16, both for 64bit and the one for all

---

### Post by praseodym on 2014-08-27
I had this message:

> i reboot my computer and now it says 
''The system is running in low-graphics mode. Tour screen, graphics card and input device settings could not be detected correctly. You will need to configure these yourself''

i cant move my mouse or press Enter to press button OK. what can i do?
Is it valid? If yes, reboot, press the SHIFT button during boot-up and chode "previous ubuntu versions" in the bootloader. There you can chose kernel 3.13 again.

---

### Post by Laima on 2014-08-27
Thank you very much! I installed and rebooted and now it is ok. My internet is working.

---

