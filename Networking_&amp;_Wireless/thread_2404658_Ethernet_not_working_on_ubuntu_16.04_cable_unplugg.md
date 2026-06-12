---
title: "Ethernet not working on ubuntu 16.04 cable unplugged"
date: 2018-10-26
forum: Networking &amp; Wireless
---

### Post by castellanos7718 on 2018-10-26
Hello all,

Please help

Ethernet conection appears unplugged in network settings, eventhough it is plugged; 

```
napoleon@Compaq:~$ lspci -nnk
00:00.0 Host bridge [0600]: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub [8086:2a40] (rev 07)
	Subsystem: Hewlett-Packard Company Mobile 4 Series Chipset Memory Controller Hub [103c:1484]
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a42] (rev 07)
	DeviceName: Mobile Intel(R) 4 Series Express Chipset Family
	Subsystem: Hewlett-Packard Company Mobile 4 Series Chipset Integrated Graphics Controller [103c:1484]
	Kernel driver in use: i915
	Kernel modules: i915
00:02.1 Display controller [0380]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a43] (rev 07)
	Subsystem: Hewlett-Packard Company Mobile 4 Series Chipset Integrated Graphics Controller [103c:1484]
00:1a.0 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 [8086:2937] (rev 03)
	Subsystem: Hewlett-Packard Company 82801I (ICH9 Family) USB UHCI Controller [103c:1484]
	Kernel driver in use: uhci_hcd
00:1a.1 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 [8086:2938] (rev 03)
	Subsystem: Hewlett-Packard Company 82801I (ICH9 Family) USB UHCI Controller [103c:1484]
	Kernel driver in use: uhci_hcd
00:1a.7 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 [8086:293c] (rev 03)
	Subsystem: Hewlett-Packard Company 82801I (ICH9 Family) USB2 EHCI Controller [103c:1484]
	Kernel driver in use: ehci-pci
00:1b.0 Audio device [0403]: Intel Corporation 82801I (ICH9 Family) HD Audio Controller [8086:293e] (rev 03)
	Subsystem: Hewlett-Packard Company 82801I (ICH9 Family) HD Audio Controller [103c:1484]
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd_hda_intel
00:1c.0 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 [8086:2940] (rev 03)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:1c.1 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 [8086:2942] (rev 03)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:1d.0 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 [8086:2934] (rev 03)
	Subsystem: Hewlett-Packard Company 82801I (ICH9 Family) USB UHCI Controller [103c:1484]
	Kernel driver in use: uhci_hcd
00:1d.1 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 [8086:2935] (rev 03)
	Subsystem: Hewlett-Packard Company 82801I (ICH9 Family) USB UHCI Controller [103c:1484]
	Kernel driver in use: uhci_hcd
00:1d.2 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 [8086:2936] (rev 03)
	Subsystem: Hewlett-Packard Company 82801I (ICH9 Family) USB UHCI Controller [103c:1484]
	Kernel driver in use: uhci_hcd
00:1d.3 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 [8086:2939] (rev 03)
	Subsystem: Hewlett-Packard Company 82801I (ICH9 Family) USB UHCI Controller [103c:1484]
	Kernel driver in use: uhci_hcd
00:1d.7 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 [8086:293a] (rev 03)
	Subsystem: Hewlett-Packard Company 82801I (ICH9 Family) USB2 EHCI Controller [103c:1484]
	Kernel driver in use: ehci-pci
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 93)
00:1f.0 ISA bridge [0601]: Intel Corporation ICH9M LPC Interface Controller [8086:2919] (rev 03)
	Subsystem: Hewlett-Packard Company ICH9M LPC Interface Controller [103c:1484]
	Kernel driver in use: lpc_ich
	Kernel modules: lpc_ich
00:1f.2 SATA controller [0106]: Intel Corporation 82801IBM/IEM (ICH9M/ICH9M-E) 4 port SATA Controller [AHCI mode] [8086:2929] (rev 03)
	Subsystem: Hewlett-Packard Company 82801IBM/IEM (ICH9M/ICH9M-E) 4 port SATA Controller [AHCI mode] [103c:1484]
	Kernel driver in use: ahci
	Kernel modules: ahci
00:1f.3 SMBus [0c05]: Intel Corporation 82801I (ICH9 Family) SMBus Controller [8086:2930] (rev 03)
	Subsystem: Hewlett-Packard Company 82801I (ICH9 Family) SMBus Controller [103c:1484]
	Kernel modules: i2c_i801
00:1f.6 Signal processing controller [1180]: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem [8086:2932] (rev 03)
	Subsystem: Hewlett-Packard Company 82801I (ICH9 Family) Thermal Subsystem [103c:1484]
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8191SEvA Wireless LAN Controller [10ec:8171] (rev 10)
	DeviceName: Intel(R) Centrino(R) Advanced-N 6300 AGN
	Subsystem: Hewlett-Packard Company RTL8191SEvA Wireless LAN Controller [103c:1467]
	Kernel driver in use: rtl8192se
	Kernel modules: rtl8192se, wl
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [10ec:8136] (rev 02)
	Subsystem: Hewlett-Packard Company RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [103c:1484]
	Kernel driver in use: r8169
	Kernel modules: r8169
```


```
napoleon@Compaq:~$ lsmod
Module                  Size  Used by
8021q                  32768  0
garp                   16384  1 8021q
mrp                    20480  1 8021q
stp                    16384  1 garp
llc                    16384  2 stp,garp
iptable_filter         16384  0
ip_tables              28672  1 iptable_filter
x_tables               40960  2 iptable_filter,ip_tables
rfcomm                 77824  2
ccm                    20480  3
bnep                   20480  2
snd_hda_codec_hdmi     49152  1
gpio_ich               16384  0
snd_hda_codec_realtek   106496  1
snd_hda_codec_generic    73728  1 snd_hda_codec_realtek
snd_hda_intel          40960  6
snd_hda_codec         126976  4 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec_realtek
coretemp               16384  0
snd_hda_core           81920  5 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hda_codec_realtek
snd_hwdep              20480  1 snd_hda_codec
snd_pcm                98304  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hda_core
hp_wmi                 16384  0
serio_raw              16384  0
sparse_keymap          16384  1 hp_wmi
wmi_bmof               16384  0
snd_seq_midi           16384  0
wl                   6447104  0
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            32768  1 snd_seq_midi
joydev                 24576  0
uvcvideo               86016  0
videobuf2_vmalloc      16384  1 uvcvideo
videobuf2_memops       16384  1 videobuf2_vmalloc
arc4                   16384  2
videobuf2_v4l2         24576  1 uvcvideo
videobuf2_core         40960  2 videobuf2_v4l2,uvcvideo
btusb                  45056  0
btrtl                  16384  1 btusb
input_leds             16384  0
btbcm                  16384  1 btusb
btintel                16384  1 btusb
videodev              180224  3 videobuf2_core,videobuf2_v4l2,uvcvideo
snd_seq                65536  2 snd_seq_midi,snd_seq_midi_event
media                  40960  2 videodev,uvcvideo
bluetooth             557056  31 btrtl,btintel,btbcm,bnep,btusb,rfcomm
lpc_ich                24576  0
rtl8192se              73728  0
rtl_pci                32768  1 rtl8192se
rtlwifi                77824  2 rtl_pci,rtl8192se
mac80211              778240  3 rtl_pci,rtlwifi,rtl8192se
snd_seq_device         16384  3 snd_seq,snd_seq_midi,snd_rawmidi
snd_timer              32768  2 snd_seq,snd_pcm
ecdh_generic           24576  1 bluetooth
cfg80211              622592  3 wl,rtlwifi,mac80211
snd                    81920  23 snd_hda_codec_generic,snd_seq,snd_seq_device,snd_hda_codec_hdmi,snd_hwdep,snd_hda_intel,snd_hda_codec,snd_hda_codec_realtek,snd_timer,snd_pcm,snd_rawmidi
shpchp                 36864  0
soundcore              16384  1 snd
mac_hid                16384  0
parport_pc             36864  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 parport_pc,lp,ppdev
autofs4                40960  2
hid_generic            16384  0
usbhid                 49152  0
hid                   118784  2 usbhid,hid_generic
ums_realtek            20480  0
uas                    24576  0
usb_storage            69632  2 uas,ums_realtek
i915                 1630208  30
i2c_algo_bit           16384  1 i915
drm_kms_helper        172032  1 i915
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
fb_sys_fops            16384  1 drm_kms_helper
drm                   401408  10 drm_kms_helper,i915
psmouse               151552  0
ahci                   36864  3
libahci                32768  1 ahci
r8169                  86016  0
mii                    16384  1 r8169
wmi                    24576  2 hp_wmi,wmi_bmof
video                  45056  1 i915
napoleon@Compaq:~$ ifconfig -a
enp3s0    Link encap:Ethernet  HWaddr 00:00:00:00:00:00  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


enp3s0.3  Link encap:Ethernet  HWaddr 00:00:00:00:00:00  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:6252 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6252 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:541587 (541.5 KB)  TX bytes:541587 (541.5 KB)


wlo1      Link encap:Ethernet  HWaddr 70:f1:a1:ed:f6:88  
          inet addr:192.168.0.19  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::35ed:1d25:5163:2eed/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:97996 errors:0 dropped:0 overruns:0 frame:0
          TX packets:66092 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:120245223 (120.2 MB)  TX bytes:8699866 (8.6 MB)
```

```
napoleon@Compaq:~$ cat /etc/network/interfaces
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback
**napoleon@Compaq:~$** cat /etc/resolv.conf
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.1.1
search hitronhub.home
napoleon@Compaq:~$ 
napoleon@Compaq:~$ 
napoleon@Compaq:~$ 
napoleon@Compaq:~$ 
napoleon@Compaq:~$ 
napoleon@Compaq:~$ 
napoleon@Compaq:~$ sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  gir1.2-appindicator3-0.1 liba11y-profile-manager-0.1-0
  liba11y-profile-manager-data
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  linux-headers-4.4.0-138 linux-headers-4.4.0-138-generic
The following NEW packages will be installed:
  linux-headers-4.4.0-138 linux-headers-4.4.0-138-generic
  linux-headers-generic
0 upgraded, 3 newly installed, 3 reinstalled, 0 to remove and 2 not upgraded.
Need to get 10.9 MB/12.0 MB of archives.
After this operation, 78.5 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Abort.
napoleon@Compaq:~$ sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  gir1.2-appindicator3-0.1 liba11y-profile-manager-0.1-0
  liba11y-profile-manager-data
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  linux-headers-4.4.0-138 linux-headers-4.4.0-138-generic
The following NEW packages will be installed:
  linux-headers-4.4.0-138 linux-headers-4.4.0-138-generic
  linux-headers-generic
0 upgraded, 3 newly installed, 3 reinstalled, 0 to remove and 2 not upgraded.
Need to get 10.9 MB/12.0 MB of archives.
After this operation, 78.5 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Abort.

```

```
napoleon@Compaq:~$ sudo tar xvf 3005217-r8168-dkms-8.031.00.tar.gz -C /usr/src
tar: 3005217-r8168-dkms-8.031.00.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
napoleon@Compaq:~$ sudo dkms add -m r8168-dkms -v 8.031.00
Error! Could not find module source directory.
Directory: /usr/src/r8168-dkms-8.031.00 does not exist.
napoleon@Compaq:~$ sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  gir1.2-appindicator3-0.1 liba11y-profile-manager-0.1-0
  liba11y-profile-manager-data
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  linux-headers-4.4.0-138 linux-headers-4.4.0-138-generic
The following NEW packages will be installed:
  linux-headers-4.4.0-138 linux-headers-4.4.0-138-generic
  linux-headers-generic
0 upgraded, 3 newly installed, 3 reinstalled, 0 to remove and 2 not upgraded.
Need to get 10.9 MB/12.0 MB of archives.
After this operation, 78.5 MB of additional disk space will be used.
Do you want to continue? [Y/n] Y
Abort.

```

```
napoleon@Compaq:~$  sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic-pae build-essential dkms 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package linux-headers-generic-pae
**napoleon@Compaq:~$** cat /etc/udev/rules.d/70-persistent-net.rules
cat: /etc/udev/rules.d/70-persistent-net.rules: No such file or directory

napoleon@Compaq:~$ sudo service udev reload
napoleon@Compaq:~$ sudo service udev restart
napoleon@Compaq:~$ sudo /etc/init.d/networking restart
[ ok ] Restarting networking (via systemctl): networking.service.
```

```

napoleon@Compaq:~$ ifconfig -a
enp3s0    Link encap:Ethernet  HWaddr 00:00:00:00:00:00  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


enp3s0.3  Link encap:Ethernet  HWaddr 00:00:00:00:00:00  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:6330 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6330 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:548997 (548.9 KB)  TX bytes:548997 (548.9 KB)


wlo1      Link encap:Ethernet  HWaddr 70:f1:a1:ed:f6:88  
          inet addr:192.168.0.19  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::35ed:1d25:5163:2eed/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:98757 errors:0 dropped:0 overruns:0 frame:0
          TX packets:66824 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:120425951 (120.4 MB)  TX bytes:8811412 (8.8 MB)


napoleon@Compaq:~$ sudo ifconfig wlo1 down
napoleon@Compaq:~$ sudo ifconfig wlo1 up
napoleon@Compaq:~$ sudo service networking restart
```

No success, please help

---

### Post by TheFu on 2018-10-26
Try a different cat5e cable and different port on the switch/router, as a start.

Output from** sudo lshw -C network** would be helpful too.

BTW, it would really help people read all that data if you used "code tags". Things would line up. It is really hard to read as posted.

---

### Post by wildmanne39 on 2018-10-26
Moved to networking.

---

### Post by DuckHook on 2018-10-26
Welcome to the forums, castellanos7718.

Please post your output between [noparse]```
 and 
```[/noparse] tags for clarity. Or highlight the output and use the [img]http://ubuntuforums.org/images/editor/code.gif[/img] button in the *Adv Reply* toolbar.

---

### Post by QIII on 2018-10-26
@castellanos7718:

Please use code tags to enclose terminal commands and their results.  That keeps your posts concise, makes them easier to read and preserves formatting.

To use code tags:

1.  Click on the # button above the text entry box, place your cursor between the code tags that appear and type or paste your text.  Alternatively, type or paste your text, highlight it and then click the # button.

2.  Type [noparse]```
[/noparse] before your text and [noparse]
```[/noparse] after your text.  The square brackets are required.

Thanks.

---

