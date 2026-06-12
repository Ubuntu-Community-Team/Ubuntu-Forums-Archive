---
title: "Realtek RTL8192SE , can't connect to wifi."
date: 2014-01-19
forum: Networking &amp; Wireless
---

### Post by al-lara2799 on 2014-01-19
I dont know what the problem is. I've connected to the wifi before but no its not connecting at all. Any help please.

---

### Post by praseodym on 2014-01-19
Please show the outputs of:
```

lsb_release -a
uname -a
lspci -nnk | grep -iA2 net
lsusb
lsmod
ifconfig -a
iwconfig
cat /etc/resolv.conf
rfkill list
```
Does LAN work? What computer is it?

---

### Post by al-lara2799 on 2014-01-19
Yeah, the LAN is Working an I have a Gateway NV55c, It has a Pentium(R) CPU P6100 @ 2.00GHz × 2, 8 GB of Ram an a  Ironlake Mobile Graphics Card

---

### Post by al-lara2799 on 2014-01-19
```
LSB Version:    core-2.0-amd64:core-2.0-noarch:core-3.0-amd64:core-3.0-noarch:core-3.1-amd64:core-3.1-noarch:core-3.2-amd64:core-3.2-noarch:core-4.0-amd64:core-4.0-noarch:core-4.1-amd64:core-4.1-noarch:security-4.0-amd64:security-4.0-noarch:security-4.1-amd64:security-4.1-noarch
Distributor ID:    Ubuntu
Description:    Ubuntu 13.10
Release:    13.10
Codename:    saucy
alberto@Geogre:~$ uname -a
Linux Geogre 3.11.0-15-generic #23-Ubuntu SMP Mon Dec 9 18:17:04 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
alberto@Geogre:~$ lspci -nnk | grep -iA2 net
01:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM57780 Gigabit Ethernet PCIe [14e4:1692] (rev 01)
    Subsystem: Acer Incorporated [ALI] Device [1025:036d]
    Kernel driver in use: tg3
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8192SE Wireless LAN Controller [10ec:8174] (rev 10)
    Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:8186]
    Kernel driver in use: rtl8192se
alberto@Geogre:~$ lsusb
Bus 002 Device 003: ID 1bcf:0005 Sunplus Innovation Technology Inc. 
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 0bda:0138 Realtek Semiconductor Corp. RTS5138 Card Reader Controller
Bus 001 Device 003: ID 064e:a219 Suyin Corp. 1.3M WebCam (notebook emachines E730, Acer sub-brand)
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
alberto@Geogre:~$ lsmod
Module                  Size  Used by
cdc_acm                28754  0 
nls_iso8859_1          12713  1 
parport_pc             32701  0 
ppdev                  17671  0 
bnep                   19704  2 
rfcomm                 69130  0 
bluetooth             372041  10 bnep,rfcomm
binfmt_misc            17468  1 
intel_powerclamp       14705  0 
coretemp               13435  0 
hid_sony               13234  0 
hid_generic            12548  0 
arc4                   12608  2 
uvcvideo               80885  0 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
videobuf2_core         40499  1 uvcvideo
videodev              133509  2 uvcvideo,videobuf2_core
microcode              23576  0 
snd_hda_codec_hdmi     41117  1 
snd_hda_codec_realtek    55704  1 
psmouse                97655  0 
serio_raw              13413  0 
rtl8192se              63196  0 
rtl_pci                26641  1 rtl8192se
rtlwifi                63229  2 rtl_pci,rtl8192se
intel_ips              18470  0 
mac80211              597268  3 rtl_pci,rtlwifi,rtl8192se
i915                  661261  6 
snd_hda_intel          48171  4 
snd_hda_codec         188738  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
drm_kms_helper         52710  1 i915
snd_hwdep              13602  1 snd_hda_codec
drm                   297056  7 i915,drm_kms_helper
lpc_ich                21080  0 
snd_pcm               102033  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
cfg80211              480503  2 mac80211,rtlwifi
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30095  1 snd_seq_midi
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29433  2 snd_pcm,snd_seq
i2c_algo_bit           13413  1 i915
mei_me                 18421  0 
snd                    69141  19 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
mei                    77782  1 mei_me
soundcore              12680  1 snd
joydev                 17377  0 
acer_wmi               32522  0 
sparse_keymap          13948  1 acer_wmi
mac_hid                13205  0 
mxm_wmi                13021  0 
video                  19318  2 i915,acer_wmi
wmi                    19070  2 acer_wmi,mxm_wmi
tifm_sd                18344  0 
tifm_core              15654  1 tifm_sd
lp                     17759  0 
parport                42299  3 lp,ppdev,parport_pc
usbhid                 53014  0 
hid                   105858  3 hid_sony,hid_generic,usbhid
ums_realtek            18029  0 
usb_storage            62062  2 ums_realtek
tg3                   162318  0 
ahci                   25819  2 
ptp                    18580  1 tg3
libahci                31928  1 ahci
pps_core               19057  1 ptp
alberto@Geogre:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 88:ae:1d:90:c0:94  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:18861 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17184 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9631402 (9.6 MB)  TX bytes:2476964 (2.4 MB)
          Interrupt:16 


ham0      Link encap:Ethernet  HWaddr 7a:79:19:14:85:7f  
          inet addr:25.20.133.127  Bcast:25.255.255.255  Mask:255.0.0.0
          inet6 addr: 2620:9b::1914:857f/96 Scope:Global
          inet6 addr: fe80::7879:19ff:fe14:857f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1404  Metric:1
          RX packets:15506 errors:0 dropped:0 overruns:0 frame:0
          TX packets:579 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:1797295 (1.7 MB)  TX bytes:84111 (84.1 KB)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:931095 errors:0 dropped:0 overruns:0 frame:0
          TX packets:931095 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:178962929 (178.9 MB)  TX bytes:178962929 (178.9 MB)


wlan0     Link encap:Ethernet  HWaddr 1c:65:9d:35:c4:7e  
          inet addr:192.168.2.103  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::1e65:9dff:fe35:c47e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:703048 errors:0 dropped:0 overruns:0 frame:0
          TX packets:534921 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:441047722 (441.0 MB)  TX bytes:68809895 (68.8 MB)


alberto@Geogre:~$ iwconfig
ham0      no wireless extensions.


eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:"AndroidTether"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 38:AA:3C:3F:BA:DC   
          Bit Rate=144.4 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=10 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:114   Missed beacon:0


alberto@Geogre:~$ cat /etc/resolv.conf
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.1.1
```

---

### Post by al-lara2799 on 2014-01-19
yeah im also new to this forums sorry

---

### Post by QIII on 2014-01-19
Hello!

Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header.

If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by al-lara2799 on 2014-01-19
ok and sorry im new

---

### Post by praseodym on 2014-01-19
Update the driver via LAN:
```

sudo apt-get install git
git clone https://github.com/FreedomBen/rtl8188ce-linux-driver
cd rtl8188ce-linux-driver
make
sudo make install
sudo cp -r firmware/* /lib/firmware  
```
Reboot.

---

### Post by al-lara2799 on 2014-01-19
it still doesnt connect to my router

---

### Post by al-lara2799 on 2014-01-19
```
if [ -e verify_branch.sh ] ; \	then \
	    ./verify_branch.sh ; \
	fi;
Verifying a sane branch for your kernel version...
Yes
make -C /lib/modules/3.11.0-15-generic/build M=/home/alberto/rtl8188ce-linux-driver modules
make: *** /lib/modules/3.11.0-15-generic/build: No such file or directory.  Stop.
make: *** [all] Error 2

```
this is what pops up

---

### Post by Zhivargo on 2014-01-20
```
sudo iwlist wlan0 scan
```

---

### Post by praseodym on 2014-01-20
Modify the file verify_branch.sh according to this

[https://github.com/FreedomBen/rtl8188ce-linux-driver/blob/master/verify_branch.sh](https://github.com/FreedomBen/rtl8188ce-linux-driver/blob/master/verify_branch.sh)

---

### Post by al-lara2799 on 2014-01-20
I ran the command an i see my wifi, i just dont know how that helps can you be more elaborate - Zhivargo
I modified it but nothing has change. I still can't connect - praseodym

---

### Post by praseodym on 2014-01-20
Try booting in an earlier kernel. Reboot and press SHIFT during boot-up. In the grub-manager choose "previous ubuntu versions" and try the 2nd latest kernel

---

### Post by al-lara2799 on 2014-01-20
Thank you that solved the problem. :p I appreciate the help.

---

### Post by al-lara2799 on 2014-01-20
now do i have to load the earlier kernel just to use my wifi? or will there be an update to fix it?

---

### Post by praseodym on 2014-01-20
Install the grub-customizer:
```

sudo add-apt-repository ppa:danielrichter2007/grub-customizer
sudo apt-get update
sudo apt-get install grub-customizer
```
Choose the working kernel as "default" (and wait for a fix with upcoming ones)

---

