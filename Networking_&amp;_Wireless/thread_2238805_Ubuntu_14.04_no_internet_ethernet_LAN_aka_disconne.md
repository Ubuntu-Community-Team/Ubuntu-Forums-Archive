---
title: "Ubuntu 14.04 no internet ethernet LAN aka disconnected - you are now offline"
date: 2014-08-10
forum: Networking &amp; Wireless
---

### Post by firstname on 2014-08-10
Well Well, 
after an intense search engine use and numerous misleading "solved" entry's i give up finding the answer and ask for your help.
[B]
The Problem:[/B]
Ubuntu 14.04 pops up the message "disconnected - you are now offline" when connecting the LAN-cable to the pc. 
It does that 3 or 4 times automatically. After that it finally toggles the internet connection to offline....

*On the very first moment I started Ubuntu the connection seemed to work for a few seconds.. but i never came close to see a loaded website.*
[B]
The Background:[/B]
I installed Ubuntu 14 from an USB stick alongside windows 7.
On the win 7 system the internet works just fine. So no hardware failure.

The Ethernet controller is made by realtek 

**The Question:**
How can I connect with Ubuntu 14 to the Internet?


Thanks in advance for your solution ;)

---

### Post by lasleym on 2014-08-10
We have had the same problem. Recently purchased a new computer for my husband. Had several install issues due to new BIOS implements, so install was difficult. Once we finally installed 12.04, we got the same issue you described. If we restarted the computer, the WIRED network connection was treated as a WiFi connection, and it wouldn't load. Often, as you said, disconnecting. Until the most recent update, simply restarting the machine corrected the problem.

We secured a working copy of 14.04 (on CD, as we have had no luck with USB install). During install, the computer recognized the wired connection. Upon restart, it forget it, and repeated the same problem you had. We restarted the computer and the recognizable wired connection returned.

We need a fix more permanent than constant restarts. What is missing in the software of 12.04 and 14.04 that 10.10 and lower had?

(PS - notes on my system below are incorrect!)

---

### Post by praseodym on 2014-08-10
Please show the terminal outputs of these commands:
```

uname -a
lspci -nnk | grep -iA2 net
lsmod
cat /etc/network/interfaces
cat /etc/resolv.conf
route -n
ifconfig -a
```
Does wireless work? If yes, please check also
```

sudo apt-get install ethtool
sudo ethtool eth0
```

---

### Post by firstname on 2014-08-11
So thats it:  ```
 Dimi-PC@PDimi:~$ uname -a
Linux Dimi 3.13.0-32-generic #57-Ubuntu SMP Tue March 18 06:21:02 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
Dimi-PC@Dimi:~$ lspci -nnk | grep -iA2 net
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)
    Subsystem: Gigabyte Technology Co., Ltd Motherboard [1458:e000]
    Kernel driver in use: r8169
Dimi-PC@Dimi:~$ lsmod
Module                  Size  Used by
dm_crypt               23177  0 
joydev                 17381  0 
rfcomm                 69160  0 
bnep                   19624  2 
bluetooth             391196  10 bnep,rfcomm
kvm_amd                59987  0 
kvm                   451511  1 kvm_amd
crct10dif_pclmul       14289  0 
crc32_pclmul           13113  0 
ghash_clmulni_intel    13216  0 
aesni_intel            55624  333 
aes_x86_64             17131  1 aesni_intel
lrw                    13286  1 aesni_intel
gf128mul               14951  1 lrw
glue_helper            13990  1 aesni_intel
ablk_helper            13597  1 aesni_intel
cryptd                 20359  169 ghash_clmulni_intel,aesni_intel,ablk_helper
snd_hda_codec_hdmi     46254  1 
synaptics_usb          13079  0 
serio_raw              13462  0 
snd_hda_codec_realtek    61438  1 
fam15h_power           13119  0 
k10temp                13126  0 
snd_seq_midi           13324  0 
snd_hda_intel          52355  5 
edac_core              62291  0 
snd_seq_midi_event     14899  1 snd_seq_midi
edac_mce_amd           22617  0 
snd_hda_codec         192906  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm               102099  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_rawmidi            30144  1 snd_seq_midi
sp5100_tco             13979  0 
i2c_piix4              22155  0 
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29482  2 snd_pcm,snd_seq
snd                    69238  21 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
soundcore              12680  1 snd
mac_hid                13205  0 
parport_pc             32701  0 
ppdev                  17671  0 
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
ses                    17363  0 
enclosure              15368  1 ses
hid_generic            12548  0 
usbhid                 52570  0 
hid                   106148  2 hid_generic,usbhid
pata_acpi              13038  0 
usb_storage            62209  1 
mxm_wmi                13021  0 
radeon               1522422  3 
firewire_ohci          40409  0 
psmouse               106678  0 
firewire_core          68769  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
pata_atiixp            13271  0 
r8169                  67581  0 
ahci                   25819  3 
i2c_algo_bit           13413  1 radeon
libahci                32560  1 ahci
mii                    13934  1 r8169
ttm                    85115  1 radeon
drm_kms_helper         53081  1 radeon
drm                   303102  5 ttm,drm_kms_helper,radeon
wmi                    19177  1 mxm_wmi
Dimi-PC@Dimi:~$ cat /etc/network/interfaces
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback
Dimi-PC@Dimi:~$ cat /etc/resolv.conf
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
Dimi-PC@Dimi:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
Dimi-PC@Dimi:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 77:e5:53:7c:1f:5f  
          inet6 addr: fe80::77e5:53ee:cb7c:1f5f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:86 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3 errors:0 dropped:141 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5160 (5.1 KB)  TX bytes:495 (495.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1184 (1.1 KB)  TX bytes:1184 (1.1 KB)

 
```
  I dont have Wifi   
@lasleym: Well I often read that some users experiance a temporary internet connection. In my case there is no such luxery ;)

---

### Post by praseodym on 2014-08-11
No problem.

First: Add nameservers to the /etc/resolv.conf file:
```

echo -e "nameserver 8.8.8.8\nnameserver 8.8.4.4" | sudo tee /etc/resolv.conf
sudo service network-manager restart
```
If it works: Ok.
If not: Download these files and save them in "Downloads":

[http://media.cdn.ubuntu-de.org/forum/attachments/45/14/3005217-r8168-dkms-8.038.00.tar.gz](http://media.cdn.ubuntu-de.org/forum/attachments/45/14/3005217-r8168-dkms-8.038.00.tar.gz)

[http://de.archive.ubuntu.com/ubuntu/pool/main/d/dkms/dkms_2.2.0.3-1.1ubuntu5_all.deb](http://de.archive.ubuntu.com/ubuntu/pool/main/d/dkms/dkms_2.2.0.3-1.1ubuntu5_all.deb)

Do not extract the *tar.gz!

Installation:

```
cd ~/Downloads/
sudo dpkg -i *.deb
sudo tar xvf 3005217-r8168-dkms-8.038.00.tar.gz -C /usr/src
sudo dkms add -m r8168-dkms -v 8.038.00
sudo dkms build -m r8168-dkms -v 8.038.00
sudo dkms install -m r8168-dkms -v 8.038.00
sudo depmod -a
sudo update-initramfs -u 
echo "blacklist r8169" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
Reboot.

---

### Post by firstname on 2014-08-13
It works! Many thanks to  you praseodym!

---

### Post by praseodym on 2014-08-13
Did you install the driver? If yes, install all necessary files, if not yet:
```

sudo apt-get install --reinstall linux-headers-generic linux-headers-$(uname -r) build-essential dkms
```
"dkms" builds the driver automatically after a kernel update, for this you need the headers files.

---

### Post by Late_Night_Legend on 2014-08-27
Hi, 

I'm having similar problem but the only difference is that I Nvidia Gigabit Ethernet card.

Could you help me figure this out?

Thanks in advance!

---

### Post by praseodym on 2014-08-27
Which card/driver?

```
lspci -nnk | grep -iA2 net
lsmod
cat /etc/resolv.conf

```

---

### Post by Late_Night_Legend on 2014-08-27
:) thanks for the quick reply!

It's a built in Ethernet port on an Asus M2N-E motherboard. All the info posted in the next post.

---

### Post by Late_Night_Legend on 2014-08-27
```
saurin@Saurin-Ubuntu:~$ uname -a
Linux Saurin-Ubuntu 3.13.0-32-generic #57-Ubuntu SMP Tue Jul 15 03:51:08 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
saurin@Saurin-Ubuntu:~$ lspci -nnk | grep -iA2 net
00:08.0 Bridge [0680]: NVIDIA Corporation MCP55 Ethernet [10de:0373] (rev a2)
    Subsystem: ASUSTeK Computer Inc. Device [1043:8239]
    Kernel driver in use: forcedeth
saurin@Saurin-Ubuntu:~$ lsmod
Module                  Size  Used by
nls_iso8859_1          12713  1 
snd_hda_codec_hdmi     46254  4 
bnep                   19624  2 
rfcomm                 69160  0 
bluetooth             391196  10 bnep,rfcomm
snd_hda_codec_analog    15049  1 
joydev                 17381  0 
hid_logitech           26709  0 
ff_memless             13573  1 hid_logitech
hid_generic            12548  0 
kvm_amd                59987  0 
kvm                   451511  1 kvm_amd
serio_raw              13462  0 
usbhid                 52570  0 
hid                   106148  3 hid_generic,hid_logitech,usbhid
k8temp                 12978  0 
edac_core              62291  0 
edac_mce_amd           22617  0 
nouveau              1097199  3 
mxm_wmi                13021  1 nouveau
wmi                    19177  2 mxm_wmi,nouveau
video                  19476  1 nouveau
ttm                    85115  1 nouveau
drm_kms_helper         53081  1 nouveau
drm                   303102  5 ttm,drm_kms_helper,nouveau
snd_ens1371            25427  2 
snd_hda_intel          52355  5 
snd_ac97_codec        130285  1 snd_ens1371
snd_hda_codec         192906  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec_analog
ac97_bus               12730  1 snd_ac97_codec
gameport               15758  1 snd_ens1371
snd_hwdep              13602  1 snd_hda_codec
snd_pcm               102099  5 snd_ac97_codec,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_ens1371
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30144  2 snd_ens1371,snd_seq_midi
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29482  2 snd_pcm,snd_seq
bttv                  139212  0 
btcx_risc              13640  1 bttv
tveeprom               21216  1 bttv
videobuf_dma_sg        19262  1 bttv
rc_core                28124  1 bttv
v4l2_common            15681  1 bttv
videobuf_core          26023  2 bttv,videobuf_dma_sg
snd                    69238  27 snd_ac97_codec,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_ens1371,snd_seq_device,snd_hda_codec_analog,snd_seq_midi
videodev              134688  2 bttv,v4l2_common
i2c_algo_bit           13413  2 bttv,nouveau
shpchp                 37032  0 
soundcore              12680  1 snd
asus_atk0110           18657  0 
parport_pc             32701  1 
mac_hid                13205  0 
nv_tco                 13564  0 
i2c_nforce2            13221  0 
ppdev                  17671  0 
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
usb_storage            62209  1 
pata_acpi              13038  0 
psmouse               106678  0 
floppy                 69418  0 
forcedeth              67509  0 
pata_amd               18225  0 
sata_nv                27745  2 
saurin@Saurin-Ubuntu:~$ cat /etc/network/interfaces
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback
saurin@Saurin-Ubuntu:~$ cat /etc/resolv.conf
nameserver 8.8.8.8
nameserver 8.8.4.4
saurin@Saurin-Ubuntu:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
saurin@Saurin-Ubuntu:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:1a:92:be:f7:ad  
          inet6 addr: fe80::21a:92ff:febe:f7ad/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:251 errors:0 dropped:1 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:38970 (38.9 KB)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:165 errors:0 dropped:0 overruns:0 frame:0
          TX packets:165 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:11841 (11.8 KB)  TX bytes:11841 (11.8 KB)

```

---

### Post by praseodym on 2014-08-28
Try these module parameters:
```

echo "options forcedeth msi=0 msix=0" | sudo tee /etc/modprobe.d/forcedeth.conf
```
Reboot

---

### Post by Late_Night_Legend on 2014-08-28
Still the same problem.

---

### Post by praseodym on 2014-08-29
Have you checked the cable or tried another slot in your router?

---

### Post by Late_Night_Legend on 2014-08-29
Switched the cable, tried new slot.  Only thing I haven't done is get a new NIC.  I'm thinking that's the next logical step

---

### Post by praseodym on 2014-08-29
Install this package

[http://de.archive.ubuntu.com/ubuntu/pool/main/e/ethtool/ethtool_3.13-1_amd64.deb](http://de.archive.ubuntu.com/ubuntu/pool/main/e/ethtool/ethtool_3.13-1_amd64.deb)


and show
```

sudo ethtool eth0
```

---

### Post by lasleym on 2014-09-30
Hello. Back on the husband's computer. Here are the commands when we get the error. (It's getting worse, for what it's worth. It used to fix itself after 1 or 2 reboots, then 5, now we're up to 11.)

**Commands when no network connection**

[FONT=courier new]home@Home:~$ uname -a
Linux Home 3.13.0-35-generic #62-Ubuntu SMP Fri Aug 15 01:58:42 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
home@Home:~$ lspci -nnk | grep -iA2 net
05:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)
    Subsystem: Gigabyte Technology Co., Ltd Motherboard [1458:e000]
    Kernel driver in use: r8169
home@Home:~$ lsmod
Module                  Size  Used by
snd_hda_codec_hdmi     46368  1 
rfcomm                 69160  0 
bnep                   19624  2 
bluetooth             391136  10 bnep,rfcomm
binfmt_misc            17468  1 
mxm_wmi                13021  0 
kvm_amd                59987  0 
joydev                 17381  0 
kvm                   451511  1 kvm_amd
crct10dif_pclmul       14289  0 
crc32_pclmul           13113  0 
ghash_clmulni_intel    13216  0 
aesni_intel            55624  0 
aes_x86_64             17131  1 aesni_intel
lrw                    13286  1 aesni_intel
gf128mul               14951  1 lrw
glue_helper            13990  1 aesni_intel
ablk_helper            13597  1 aesni_intel
cryptd                 20359  3 ghash_clmulni_intel,aesni_intel,ablk_helper
snd_hda_codec_realtek    65580  1 
snd_hda_intel          56451  5 
serio_raw              13462  0 
fam15h_power           13119  0 
snd_hda_codec         192906  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
edac_core              62291  0 
edac_mce_amd           22617  0 
k10temp                13126  0 
snd_pcm               102099  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30144  1 snd_seq_midi
sp5100_tco             13979  0 
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
i2c_piix4              22155  0 
radeon               1522474  3 
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29482  2 snd_pcm,snd_seq
ttm                    85115  1 radeon
drm_kms_helper         53081  1 radeon
snd                    69322  21 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
drm                   303102  5 ttm,drm_kms_helper,radeon
wmi                    19177  1 mxm_wmi
soundcore              12680  1 snd
i2c_algo_bit           13413  1 radeon
mac_hid                13205  0 
parport_pc             32701  0 
ppdev                  17671  0 
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
pata_acpi              13038  0 
hid_generic            12548  0 
psmouse               106678  0 
r8169                  67581  0 
firewire_ohci          40409  0 
usbhid                 52570  0 
mii                    13934  1 r8169
firewire_core          68769  1 firewire_ohci
hid                   106148  2 hid_generic,usbhid
crc_itu_t              12707  1 firewire_core
ahci                   25819  2 
pata_atiixp            13271  0 
libahci                32716  1 ahci
home@Home:~$ cat /etc/network/interfaces
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback
home@Home:~$ cat /etc/resolv.conf
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
home@Home:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
home@Home:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 74:d4:35:92:f7:30  
          inet6 addr: fe80::76d4:35ff:fe92:f730/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:141 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:391 errors:0 dropped:0 overruns:0 frame:0
          TX packets:391 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:62688 (62.6 KB)  TX bytes:62688 (62.6 KB)[/FONT]

**Commands when network connection works**

[FONT=courier new]home@Home:~$ uname -a
Linux Home 3.13.0-35-generic #62-Ubuntu SMP Fri Aug 15 01:58:42 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
home@Home:~$ lspci -nnk | grep -iA2 net
05:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)
    Subsystem: Gigabyte Technology Co., Ltd Motherboard [1458:e000]
    Kernel driver in use: r8169
home@Home:~$ lsmod
Module                  Size  Used by
btrfs                 835954  0 
raid6_pq               97812  1 btrfs
xor                    21411  1 btrfs
ufs                    74890  0 
qnx4                   13317  0 
hfsplus               107516  0 
hfs                    54677  0 
minix                  36140  0 
ntfs                   97369  0 
msdos                  17332  0 
jfs                   181348  0 
xfs                   912173  0 
libcrc32c              12644  2 xfs,btrfs
snd_hda_codec_hdmi     46368  1 
bnep                   19624  2 
rfcomm                 69160  0 
bluetooth             391136  10 bnep,rfcomm
binfmt_misc            17468  1 
joydev                 17381  0 
mxm_wmi                13021  0 
kvm_amd                59987  0 
kvm                   451511  1 kvm_amd
crct10dif_pclmul       14289  0 
crc32_pclmul           13113  0 
ghash_clmulni_intel    13216  0 
aesni_intel            55624  0 
aes_x86_64             17131  1 aesni_intel
lrw                    13286  1 aesni_intel
snd_hda_codec_realtek    65580  1 
gf128mul               14951  1 lrw
glue_helper            13990  1 aesni_intel
ablk_helper            13597  1 aesni_intel
cryptd                 20359  3 ghash_clmulni_intel,aesni_intel,ablk_helper
snd_hda_intel          56451  5 
snd_seq_midi           13324  0 
snd_hda_codec         192906  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
serio_raw              13462  0 
snd_seq_midi_event     14899  1 snd_seq_midi
edac_core              62291  0 
snd_rawmidi            30144  1 snd_seq_midi
snd_hwdep              13602  1 snd_hda_codec
edac_mce_amd           22617  0 
fam15h_power           13119  0 
k10temp                13126  0 
snd_pcm               102099  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
radeon               1522474  3 
snd_timer              29482  2 snd_pcm,snd_seq
sp5100_tco             13979  0 
i2c_piix4              22155  0 
snd                    69322  21 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
ttm                    85115  1 radeon
soundcore              12680  1 snd
drm_kms_helper         53081  1 radeon
drm                   303102  5 ttm,drm_kms_helper,radeon
i2c_algo_bit           13413  1 radeon
parport_pc             32701  0 
ppdev                  17671  0 
mac_hid                13205  0 
lp                     17759  0 
wmi                    19177  1 mxm_wmi
parport                42348  3 lp,ppdev,parport_pc
pata_acpi              13038  0 
hid_generic            12548  0 
firewire_ohci          40409  0 
r8169                  67581  0 
mii                    13934  1 r8169
psmouse               106678  0 
firewire_core          68769  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
usbhid                 52570  0 
hid                   106148  2 hid_generic,usbhid
ahci                   25819  2 
pata_atiixp            13271  0 
libahci                32716  1 ahci
home@Home:~$ cat /etc/network/interfaces
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback
home@Home:~$ cat /etc/resolv.conf
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.1.1
search home.network
home@Home:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.0.0.1        0.0.0.0         UG    0      0        0 eth0
10.0.0.0        0.0.0.0         255.255.255.0   U     1      0        0 eth0
home@Home:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 74:d4:35:92:f7:30  
          inet addr:10.0.0.7  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::76d4:35ff:fe92:f730/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:217293 errors:0 dropped:0 overruns:0 frame:0
          TX packets:83075 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:325912638 (325.9 MB)  TX bytes:5676578 (5.6 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:1759 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1759 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:978130 (978.1 KB)  TX bytes:978130 (978.1 KB)[/FONT]

I can notice a few obvious differences, but I'm not sure what a logical next step is. Naming the namessevers? If so, can I get more detail around that instruction please? Thanks in advance!

---

### Post by praseodym on 2014-10-02
You need nameservers when its not working:
```

echo -e "nameserver 8.8.8.8\nnameserver 8.8.4.4" | sudo tee -a /etc/resolv.conf
sudo service networking restart
```

---

### Post by Michael_McKenney on 2014-10-02
I had issues on a new 14.04 installation with performance on Nvidia based NICs.  I went to Micro Center and bought an Intel PCIe X1 Gigabit NIC for $39.99.  Problems went away immediately.  I read nothing but issues with the Nvidia NIC.   Everyone said the Intel NIC was the way to go.

---

### Post by tom137 on 2014-10-03
Hi all. Same problems here, and after using others' solutions without getting the desired result - a working ethernet LAN connection - I hope you can help me. I'm pretty much a layman at this.
I don't have a wireless connection possibility at this computer.

```
tom@Tom:~$ uname -aLinux Tom 3.13.0-35-generic #62-Ubuntu SMP Fri Aug 15 01:58:01 UTC 2014 i686 i686 i686 GNU/Linux
tom@Tom:~$ lspci -nnk | grep -iA2 net
02:00.0 Ethernet controller [0200]: Qualcomm Atheros Attansic L2 Fast Ethernet [1969:2048] (rev a0)
    Subsystem: ASUSTeK Computer Inc. Device [1043:8233]
    Kernel driver in use: atl2
tom@Tom:~$ lsmod
Module                  Size  Used by
nls_iso8859_1          12617  1 
bnep                   18895  2 
rfcomm                 53664  0 
bluetooth             342208  10 bnep,rfcomm
gpio_ich               13229  0 
binfmt_misc            13140  1 
snd_hda_codec_hdmi     45440  1 
snd_hda_codec_realtek    55163  1 
snd_hda_intel          42730  5 
snd_hda_codec         164067  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13272  1 snd_hda_codec
snd_pcm                85501  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_rawmidi            25135  1 snd_seq_midi
coretemp               13195  0 
snd_seq                55383  2 snd_seq_midi_event,snd_seq_midi
kvm_intel             132549  0 
radeon               1420570  3 
kvm                   388084  1 kvm_intel
ttm                    72698  1 radeon
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              28584  2 snd_pcm,snd_seq
drm_kms_helper         47182  1 radeon
serio_raw              13230  0 
lpc_ich                16864  0 
drm                   244037  5 ttm,drm_kms_helper,radeon
asus_atk0110           18201  0 
snd                    60939  21 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
i2c_algo_bit           13197  1 radeon
mac_hid                13037  0 
soundcore              12600  1 snd
parport_pc             31981  1 
ppdev                  17391  0 
lp                     13299  0 
parport                40836  3 lp,ppdev,parport_pc
usb_storage            48417  1 
psmouse                91329  0 
floppy                 55416  0 
atl2                   27628  0 
tom@Tom:~$ cat /etc/network/interfaces
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback
tom@Tom:~$ cat /etc/resolv.conf
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
tom@Tom:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
tom@Tom:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:1d:60:2b:96:e6  
          inet6 addr: fe80::21d:60ff:fe2b:96e6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:792 errors:0 dropped:0 overruns:0 frame:0
          TX packets:374 errors:0 dropped:0 overruns:0 carrier:2
          collisions:0 txqueuelen:1000 
          RX bytes:46705 (46.7 KB)  TX bytes:74639 (74.6 KB)
          Memory:dfec0000-dff00000 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:474 errors:0 dropped:0 overruns:0 frame:0
          TX packets:474 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:39251 (39.2 KB)  TX bytes:39251 (39.2 KB)
```

---

### Post by praseodym on 2014-10-03
@tom137: You need nameservers:
```

echo -e "nameserver 8.8.8.8\nnameserver 8.8.4.4" | sudo tee /etc/resolv.conf
sudo service network-manager restart
```

---

### Post by tom137 on 2014-10-07
@praseodym: thanks for your quick reply. I tried your code but it didnt work. It still tells me 'no internet ethernet LAN aka disconnected - you are now offline'.
Any other ideas? Or do you need more information?

---

### Post by praseodym on 2014-10-07
How do you connect? Router? Modem? Both? Did you get Login/PW of your ISP?

---

### Post by gpsvn2 on 2014-10-08
> **praseodym said:**
> No problem.

First: Add nameservers to the /etc/resolv.conf file:
```

echo -e "nameserver 8.8.8.8\nnameserver 8.8.4.4" | sudo tee /etc/resolv.conf
sudo service network-manager restart
```
If it works: Ok.
If not: Download these files and save them in "Downloads":

[http://media.cdn.ubuntu-de.org/forum/attachments/45/14/3005217-r8168-dkms-8.038.00.tar.gz](http://media.cdn.ubuntu-de.org/forum/attachments/45/14/3005217-r8168-dkms-8.038.00.tar.gz)

[http://de.archive.ubuntu.com/ubuntu/pool/main/d/dkms/dkms_2.2.0.3-1.1ubuntu5_all.deb](http://de.archive.ubuntu.com/ubuntu/pool/main/d/dkms/dkms_2.2.0.3-1.1ubuntu5_all.deb)

Do not extract the *tar.gz!

Installation:

```
cd ~/Downloads/
sudo dpkg -i *.deb
sudo tar xvf 3005217-r8168-dkms-8.038.00.tar.gz -C /usr/src
sudo dkms add -m r8168-dkms -v 8.038.00
sudo dkms build -m r8168-dkms -v 8.038.00
sudo dkms install -m r8168-dkms -v 8.038.00
sudo depmod -a
sudo update-initramfs -u 
echo "blacklist r8169" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
Reboot.

I have the same problem. Wifi is still working but "*Ethernet Network disconnected*". Followed the steps, outputs are shown below. Downloaded two files and installed, so far nothing works. Appreciate your help.

```
bao@bao-Ubuntu:~$ uname -aLinux bao-Ubuntu 3.13.0-36-generic #63-Ubuntu SMP Wed Sep 3 21:30:07 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
bao@bao-Ubuntu:~$ lspci -nnk | grep -iA2 net
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
    Subsystem: Hewlett-Packard Company Device [103c:360b]
    Kernel driver in use: r8169
03:00.0 Ethernet controller [0200]: Qualcomm Atheros AR242x / AR542x Wireless Network Adapter (PCI-Express) [168c:001c] (rev 01)
    Subsystem: Hewlett-Packard Company Device [103c:137b]
    Kernel driver in use: ath5k
bao@bao-Ubuntu:~$ lsmod
Module                  Size  Used by
ctr                    13049  2 
ccm                    17773  2 
nls_utf8               12557  1 
udf                    89723  1 
crc_itu_t              12707  1 udf
hp_wmi                 14062  0 
sparse_keymap          13948  1 hp_wmi
gpio_ich               13476  0 
uvcvideo               80885  0 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
videobuf2_core         40664  1 uvcvideo
videodev              134688  2 uvcvideo,videobuf2_core
bnep                   19624  2 
rfcomm                 69160  0 
bluetooth             391136  10 bnep,rfcomm
arc4                   12608  2 
snd_hda_codec_hdmi     46368  1 
snd_hda_codec_conexant    57441  1 
snd_hda_intel          56451  1 
snd_hda_codec         192906  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm               102099  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
coretemp               13435  0 
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
binfmt_misc            17468  1 
snd_rawmidi            30144  1 snd_seq_midi
joydev                 17381  0 
serio_raw              13462  0 
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
nvidia              11334886  55 
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29482  2 snd_pcm,snd_seq
ath5k                 149924  0 
ath                    28698  1 ath5k
snd                    69322  13 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
mac80211              630653  1 ath5k
lpc_ich                21080  0 
cfg80211              484040  3 ath,ath5k,mac80211
soundcore              12680  1 snd
wmi                    19177  1 hp_wmi
parport_pc             32701  0 
ppdev                  17671  0 
mac_hid                13205  0 
video                  19476  0 
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
hid_generic            12548  0 
ums_realtek            18029  0 
usbhid                 52659  0 
r8169                  67581  0 
hid                   106148  2 hid_generic,usbhid
usb_storage            62209  2 ums_realtek
psmouse               106678  0 
mii                    13934  1 r8169
ahci                   25819  3 
libahci                32716  1 ahci
bao@bao-Ubuntu:~$ cat /etc/network/interfaces
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback
cat /etc/resolv.conf
bao@bao-Ubuntu:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.100.1   0.0.0.0         UG    0      0        0 wlan0
192.168.100.0   0.0.0.0         255.255.255.0   U     9      0        0 wlan0
bao@bao-Ubuntu:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:1f:16:59:4a:dd  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:1938 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1938 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:278433 (278.4 KB)  TX bytes:278433 (278.4 KB)


wlan0     Link encap:Ethernet  HWaddr 00:24:2b:24:8a:b8  
          inet addr:192.168.100.15  Bcast:192.168.100.255  Mask:255.255.255.0
          inet6 addr: fe80::224:2bff:fe24:8ab8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:21902 errors:0 dropped:0 overruns:0 frame:0
          TX packets:19255 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:11380483 (11.3 MB)  TX bytes:16861621 (16.8 MB)


bao@bao-Ubuntu:~$ sudo ethtool eth0
Settings for eth0:
    Supported ports: [ TP MII ]
    Supported link modes:   10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
    Supported pause frame use: No
    Supports auto-negotiation: Yes
    Advertised link modes:  10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
    Advertised pause frame use: Symmetric Receive-only
    Advertised auto-negotiation: Yes
    Speed: 10Mb/s
    Duplex: Half
    Port: MII
    PHYAD: 0
    Transceiver: internal
    Auto-negotiation: on
    Supports Wake-on: pumbg
    Wake-on: g
    Current message level: 0x00000033 (51)
                   drv probe ifdown ifup
    Link detected: no



```

---

### Post by praseodym on 2014-10-08
Hi, this driver is not suitable for your card, but there will be no harm of it. This

```
    Link detected: no
```
looks like a broken cable?!

---

### Post by gpsvn2 on 2014-10-09
> **praseodym said:**
> Hi, this driver is not suitable for your card, but there will be no harm of it. This

```
    Link detected: no
```
looks like a broken cable?!

Thank you, cable replaced and it works.

---

### Post by tom137 on 2014-10-12
suddently it worked. Now, I quickly updated to the latest kernel and hopefully everything keeps working now.
Many thanks!

---

### Post by agha2 on 2014-10-14
Hi Praseodym,
I have installed ubuntu in vmWare workstation on windows 8.1, i have been facing same problem like @firstname.
kindly help me out.
 here is the output

agha@agha:~$ uname -a
Linux agha 3.13.0-32-generic #57-Ubuntu SMP Tue Jul 15 03:51:08 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
agha@agha:~$ lspci -nnk | grep -iA2 net
02:01.0 Ethernet controller [0200]: Intel Corporation 82545EM Gigabit Ethernet Controller (Copper) [8086:100f] (rev 01)
	Subsystem: VMware PRO/1000 MT Single Port Adapter [15ad:0750]
	Kernel driver in use: e1000
agha@agha:~$ lsmod
Module                  Size  Used by
bnep                   19624  2 
rfcomm                 69160  8 
snd_ens1371            25427  2 
snd_ac97_codec        130285  1 snd_ens1371
ac97_bus               12730  1 snd_ac97_codec
gameport               15758  1 snd_ens1371
vmw_balloon            13415  0 
snd_pcm               102099  2 snd_ac97_codec,snd_ens1371
coretemp               13435  0 
crct10dif_pclmul       14289  0 
crc32_pclmul           13113  0 
ghash_clmulni_intel    13216  0 
snd_page_alloc         18710  1 snd_pcm
aesni_intel            55624  0 
aes_x86_64             17131  1 aesni_intel
lrw                    13286  1 aesni_intel
gf128mul               14951  1 lrw
glue_helper            13990  1 aesni_intel
snd_seq_midi           13324  0 
ablk_helper            13597  1 aesni_intel
snd_seq_midi_event     14899  1 snd_seq_midi
cryptd                 20359  3 ghash_clmulni_intel,aesni_intel,ablk_helper
snd_rawmidi            30144  2 snd_ens1371,snd_seq_midi
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
joydev                 17381  0 
serio_raw              13462  0 
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29482  2 snd_pcm,snd_seq
btusb                  32412  0 
bluetooth             391196  22 bnep,btusb,rfcomm
snd                    69238  12 snd_ac97_codec,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_ens1371,snd_seq_device,snd_seq_midi
vmwgfx                175358  2 
ttm                    85115  1 vmwgfx
soundcore              12680  1 snd
shpchp                 37032  0 
drm                   303102  3 ttm,vmwgfx
i2c_piix4              22155  0 
vmw_vmci               62966  0 
parport_pc             32701  1 
mac_hid                13205  0 
ppdev                  17671  0 
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
hid_generic            12548  0 
usbhid                 52570  0 
hid                   106148  2 hid_generic,usbhid
psmouse               106678  0 
e1000                 145174  0 
vmw_pvscsi             22858  0 
floppy                 69418  0 
vmxnet3                49693  0 
mptspi                 22542  2 
mptscsih               40150  1 mptspi
mptbase               101822  2 mptspi,mptscsih
agha@agha:~$ cat /etc/network/interfaces
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback
agha@agha:~$ cat /etc/resolv.conf
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
agha@agha:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
agha@agha:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:0c:29:d3:08:a1  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:80 errors:0 dropped:0 overruns:0 frame:0
          TX packets:80 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15870 (15.8 KB)  TX bytes:15870 (15.8 KB)


agha@agha:~$ sudo apt-get install ethtool
[sudo] password for agha: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ethtool is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
agha@agha:~$ sudo ethtool eth0
Settings for eth0:
	Supported ports: [ TP ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Supported pause frame use: No
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Advertised pause frame use: No
	Advertised auto-negotiation: Yes
	Speed: Unknown!
	Duplex: Unknown! (255)
	Port: Twisted Pair
	PHYAD: 0
	Transceiver: internal
	Auto-negotiation: on
	MDI-X: Unknown (auto)
	Supports Wake-on: d
	Wake-on: d
	Current message level: 0x00000007 (7)
			       drv probe link
	Link detected: no
agha@agha:~$

---

### Post by robert131 on 2014-10-14
I am having this same problem, but I have "Link detected: yes". The output of the cable has the orange light on, so it must have connection. If I try to do `ping google.com` I get `unknown host: google.com` though. It keeps randomly alerting me that I'm disconnected through the red popup, but even when I am "connected", I can't connect to the internet through ethernet. I'm running a m4a88t-m le mobo, and it works fine on my other machines, but when I erased the hdd with windows on it and installed ubuntu 14.04, the internet no longer works. Any ideas?

---

### Post by praseodym on 2014-10-14
@agha2: You need nameservers, too. Check this thread.

@robert131: Show the same outputs as agha2 did.

---

### Post by agha2 on 2014-10-15
problem remains the same :(

here is output

agha@agha:~$ echo -e "nameserver 8.8.8.8\nnameserver 8.8.4.4" | sudo tee /etc/resolv.conf
nameserver 8.8.8.8
nameserver 8.8.4.4
agha@agha:~$ sudo service network-manager restart
network-manager stop/waiting
network-manager start/running, process 2375
agha@agha:~$ cd ~/Downloads/
agha@agha:~/Downloads$ sudo dpkg -i *.deb
Selecting previously unselected package dkms.
(Reading database ... 163651 files and directories currently installed.)
Preparing to unpack dkms_2.2.0.3-1.1ubuntu5_all.deb ...
Unpacking dkms (2.2.0.3-1.1ubuntu5) ...
Setting up dkms (2.2.0.3-1.1ubuntu5) ...
Processing triggers for man-db (2.6.7.1-1) ...
agha@agha:~/Downloads$ sudo tar xvf 3005217-r8168-dkms-8.038.00.tar.gz -C /usr/src
r8168-dkms-8.038.00/src/Makefile
r8168-dkms-8.038.00/src/Makefile_linux24x
r8168-dkms-8.038.00/src/r8168.h
r8168-dkms-8.038.00/src/r8168_asf.c
r8168-dkms-8.038.00/src/r8168_asf.h
r8168-dkms-8.038.00/src/r8168_dash.h
r8168-dkms-8.038.00/src/r8168_n.c
r8168-dkms-8.038.00/src/rtltool.c
r8168-dkms-8.038.00/src/rtltool.h
r8168-dkms-8.038.00/src/rtl_eeprom.c
r8168-dkms-8.038.00/src/rtl_eeprom.h
r8168-dkms-8.038.00/dkms.conf
r8168-dkms-8.038.00/autorun.sh
r8168-dkms-8.038.00/Makefile
r8168-dkms-8.038.00/README
r8168-dkms-8.038.00/src/
r8168-dkms-8.038.00/
agha@agha:~/Downloads$ sudo dkms add -m r8168-dkms -v 8.038.00


Creating symlink /var/lib/dkms/r8168-dkms/8.038.00/source ->
                 /usr/src/r8168-dkms-8.038.00


DKMS: add completed.
agha@agha:~/Downloads$ sudo dkms build -m r8168-dkms -v 8.038.00


Kernel preparation unnecessary for this kernel.  Skipping...


Building module:
cleaning build area....
'make' -C src/ all..............
cleaning build area....


DKMS: build completed.
agha@agha:~/Downloads$ sudo dkms install -m r8168-dkms -v 8.038.00


r8168:
Running module version sanity check.


Good news! Module version 8.038.00-NAPI for r8168.ko
exactly matches what is already found in kernel 3.13.0-32-generic.
DKMS will not replace this module.
You may override by specifying --force.


depmod.......


DKMS: install completed.
agha@agha:~/Downloads$ sudo depmod -a
agha@agha:~/Downloads$ sudo update-initramfs -u 
update-initramfs: Generating /boot/initrd.img-3.13.0-32-generic
agha@agha:~/Downloads$ echo "blacklist r8169" | sudo tee -a /etc/modprobe.d/blacklist.conf
blacklist r8169
agha@agha:~/Downloads$

---

### Post by praseodym on 2014-10-15
Please try the latest driver version. Uninstall version 38 first:
```

sudo dkms remove -m r8168-dkms -v 8.038.00 --all
sudo rm -r /usr/src/r8168-dkms-8.038.00 
```
Download this file

[http://media.cdn.ubuntu-de.org/forum/attachments/24/39/3005217-r8168-dkms-8.039.00.tar.gz](http://media.cdn.ubuntu-de.org/forum/attachments/24/39/3005217-r8168-dkms-8.039.00.tar.gz)

and install it via

```
sudo tar xvf 3005217-r8168-dkms-8.039.00.tar.gz -C /usr/src
sudo dkms add -m r8168-dkms -v 8.039.00
sudo dkms build -m r8168-dkms -v 8.039.00
sudo dkms install -m r8168-dkms -v 8.039.00
sudo depmod -a
sudo update-initramfs -u 
```
Reboot.

---

### Post by agha2 on 2014-10-15
i have downloaded file in Download directory, facing an other error


agha@agha:~$ sudo tar xvf 3005217-r8168-dkms-8.039.00.tar.gz -C /usr/src
sudo: error in /etc/sudo.conf, line 0 while loading plugin `sudoers_policy'
sudo: /usr/lib/sudo/sudoers.so must be only be writable by owner
sudo: fatal error, unable to load plugins

---

### Post by tom137 on 2014-10-17
Hi there, unfortunately I'm back again. Internet connection keeps failing.

@praseodym, i connect by cable to modem. ISP provided no login or password.
I installed latest driver version (39) - uninstalled 38 first. However, still no working internet connection.

Possibly i messed around in the configurations of the network connections.. besides that, i noticed that, opposed to others here, no information is returned when using "route -n". I don't have a clue on what it means or if it's important.


```
tom@Tom:~$ route -nKernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
```

---

### Post by gpsvn2 on 2014-10-17
Unfortunately I am back again, the Ethernet stops working. 
 
```
bao@bao-Ubuntu:~$ uname -aLinux bao-Ubuntu 3.13.0-37-generic #64-Ubuntu SMP Mon Sep 22 21:28:38 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
bao@bao-Ubuntu:~$ lspci -nnk | grep -iA2 net
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
	Subsystem: Hewlett-Packard Company Device [103c:360b]
03:00.0 Ethernet controller [0200]: Qualcomm Atheros AR242x / AR542x Wireless Network Adapter (PCI-Express) [168c:001c] (rev 01)
	Subsystem: Hewlett-Packard Company Device [103c:137b]
	Kernel driver in use: ath5k
bao@bao-Ubuntu:~$ lsmod
Module                  Size  Used by
nls_utf8               12557  1 
udf                    89684  1 
crc_itu_t              12707  1 udf
ctr                    13049  0 
ccm                    17773  0 
rfcomm                 69160  0 
bnep                   19624  2 
bluetooth             391136  10 bnep,rfcomm
arc4                   12608  2 
binfmt_misc            17468  1 
gpio_ich               13476  0 
hp_wmi                 14062  0 
sparse_keymap          13948  1 hp_wmi
uvcvideo               80885  0 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
videobuf2_core         40664  1 uvcvideo
videodev              134688  2 uvcvideo,videobuf2_core
coretemp               13435  0 
snd_hda_codec_hdmi     46368  1 
snd_hda_codec_conexant    57441  1 
snd_hda_intel          56451  1 
snd_hda_codec         192906  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm               102099  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
joydev                 17381  0 
ath5k                 149924  0 
snd_rawmidi            30144  1 snd_seq_midi
ath                    28698  1 ath5k
serio_raw              13462  0 
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29482  2 snd_pcm,snd_seq
mac80211              630653  1 ath5k
snd                    69322  13 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
lpc_ich                21080  0 
cfg80211              484040  3 ath,ath5k,mac80211
soundcore              12680  1 snd
nvidia              11334886  55 
parport_pc             32701  0 
ppdev                  17671  0 
wmi                    19177  1 hp_wmi
video                  19476  0 
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
mac_hid                13205  0 
hid_generic            12548  0 
usbhid                 52659  0 
psmouse               106678  0 
hid                   106148  2 hid_generic,usbhid
ums_realtek            18029  0 
usb_storage            62209  2 ums_realtek
ahci                   25819  3 
libahci                32716  1 ahci
bao@bao-Ubuntu:~$ cat /etc/network/interfaces
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback
bao@bao-Ubuntu:~$ cat /etc/resolv.conf
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.1.1
bao@bao-Ubuntu:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.100.1   0.0.0.0         UG    0      0        0 wlan0
192.168.100.0   0.0.0.0         255.255.255.0   U     9      0        0 wlan0
bao@bao-Ubuntu:~$ ifconfig -a
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:1120 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1120 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:188238 (188.2 KB)  TX bytes:188238 (188.2 KB)


wlan0     Link encap:Ethernet  HWaddr 00:24:2b:24:8a:b8  
          inet addr:192.168.100.15  Bcast:192.168.100.255  Mask:255.255.255.0
          inet6 addr: fe80::224:2bff:fe24:8ab8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:143432 errors:0 dropped:0 overruns:0 frame:0
          TX packets:275778 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:15643520 (15.6 MB)  TX bytes:409532834 (409.5 MB)


bao@bao-Ubuntu:~$ sudo apt-get install ethtool
[sudo] password for bao: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ethtool is already the newest version.
The following packages were automatically installed and are no longer required:
  libgstreamer-plugins-base0.10-0:i386 libgstreamer0.10-0:i386
  liborc-0.4-0:i386 linux-headers-3.13.0-24 linux-headers-3.13.0-24-generic
  linux-headers-3.13.0-27 linux-headers-3.13.0-27-generic
  linux-headers-3.13.0-29 linux-headers-3.13.0-29-generic
  linux-headers-3.13.0-30 linux-headers-3.13.0-30-generic
  linux-headers-3.13.0-32 linux-headers-3.13.0-32-generic
  linux-headers-3.13.0-33 linux-headers-3.13.0-33-generic
  linux-headers-3.13.0-34 linux-headers-3.13.0-34-generic
  linux-headers-3.13.0-35 linux-headers-3.13.0-35-generic
  linux-image-3.13.0-24-generic linux-image-3.13.0-27-generic
  linux-image-3.13.0-29-generic linux-image-3.13.0-30-generic
  linux-image-3.13.0-32-generic linux-image-3.13.0-33-generic
  linux-image-3.13.0-34-generic linux-image-3.13.0-35-generic
  linux-image-extra-3.13.0-24-generic linux-image-extra-3.13.0-27-generic
  linux-image-extra-3.13.0-29-generic linux-image-extra-3.13.0-30-generic
  linux-image-extra-3.13.0-32-generic linux-image-extra-3.13.0-33-generic
  linux-image-extra-3.13.0-34-generic linux-image-extra-3.13.0-35-generic
  odbcinst odbcinst1debian2 unixodbc
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 10 not upgraded.
bao@bao-Ubuntu:~$ sudo ethtool eth0
Settings for eth0:
Cannot get device settings: No such device
Cannot get wake-on-lan settings: No such device
Cannot get message level: No such device
Cannot get link status: No such device
No data available



```

---

### Post by praseodym on 2014-10-18
For this device the r8168 is not suitable, and r8169 is not loaded:
```

sudo modprobe -v r8169
grep r8 /etc/modprobe.d/*
cat /etc/modules
```

---

### Post by gpsvn2 on 2014-10-20
> **praseodym said:**
> For this device the r8168 is not suitable, and r8169 is not loaded:
```

sudo modprobe -v r8169
grep r8 /etc/modprobe.d/*
cat /etc/modules
```

Thank you praseodym. After typing sudo modprobe -v r8169, it works right away.

---

### Post by tom137 on 2014-10-20
Thank you praseodym - I do appreciate your efforts.

For me no success so far. This is what the last codes give me:
```
tom@Tom:~$ sudo modprobe -v r8169insmod /lib/modules/3.13.0-37-generic/kernel/drivers/net/mii.ko 
insmod /lib/modules/3.13.0-37-generic/kernel/drivers/net/ethernet/realtek/r8169.ko 
tom@Tom:~$ grep r8 /etc/modprobe.d/*
/etc/modprobe.d/blacklist.conf:blacklist r8169
tom@Tom:~$ cat /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.
# Parameters can be specified after the module name.


lp



```

---

### Post by Aniruthan_M_E on 2014-10-24
[SIZE=2]Hello,
I've tried all the methods listed above. No luck. Now I am directly requesting your help. Thank you very much.
As far as including nameservers go, it's there when I add it for the current session, but once I restart, like it says, the changes are overwritten.

```

aniruth@Jarvis:~$ uname -a
Linux Jarvis 3.13.0-37-generic #64-Ubuntu SMP Mon Sep 22 21:28:38 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

aniruth@Jarvis:~$ lspci -nnk | grep -iA2 net
07:00.0 Network controller [0280]: Broadcom Corporation BCM43142 802.11b/g/n [14e4:4365] (rev 01)
    Subsystem: Foxconn International, Inc. Device [105b:e071]
    Kernel driver in use: wl
--
0e:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0c)
    Subsystem: Sony Corporation Device [104d:90b8]
    Kernel driver in use: r8168

aniruth@Jarvis:~$ lsmod
Module                  Size  Used by
bnep                   19624  2 
rfcomm                 69160  0 
bluetooth             391136  10 bnep,rfcomm
nls_iso8859_1          12713  1 
snd_hda_codec_hdmi     46368  1 
snd_hda_codec_realtek    65580  1 
microread_mei          12811  0 
microread              13420  1 microread_mei
mei_phy                13881  1 microread_mei
crc_ccitt              12707  1 microread
hci                    44425  2 mei_phy,microread
nfc                    95012  2 hci,microread
uvcvideo               80885  0 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
videobuf2_core         40664  1 uvcvideo
videodev              134688  2 uvcvideo,videobuf2_core
snd_hda_intel          56451  3 
snd_hda_codec         192906  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm               102099  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30144  1 snd_seq_midi
intel_rapl             18773  0 
x86_pkg_temp_thermal    14205  0 
intel_powerclamp       14705  0 
coretemp               13435  0 
kvm_intel             143109  0 
kvm                   451552  1 kvm_intel
crct10dif_pclmul       14289  0 
crc32_pclmul           13113  0 
ghash_clmulni_intel    13216  0 
aesni_intel            55624  0 
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
aes_x86_64             17131  1 aesni_intel
lrw                    13286  1 aesni_intel
gf128mul               14951  1 lrw
glue_helper            13990  1 aesni_intel
ablk_helper            13597  1 aesni_intel
cryptd                 20359  3 ghash_clmulni_intel,aesni_intel,ablk_helper
lib80211_crypt_tkip    17619  0 
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29482  2 snd_pcm,snd_seq
joydev                 17381  0 
serio_raw              13462  0 
rtsx_pci_ms            18151  0 
memstick               16966  1 rtsx_pci_ms
wl                   4207846  0 
lib80211               14381  2 wl,lib80211_crypt_tkip
cfg80211              484040  1 wl
lpc_ich                21080  0 
snd                    69322  17 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
soundcore              12680  1 snd
mei_me                 18627  0 
mei                    82276  3 mei_phy,mei_me,microread_mei
i915                  783805  3 
nouveau              1097199  1 
sony_laptop            54219  0 
mxm_wmi                13021  1 nouveau
wmi                    19177  2 mxm_wmi,nouveau
video                  19476  2 i915,nouveau
ttm                    85150  1 nouveau
drm_kms_helper         55071  2 i915,nouveau
mac_hid                13205  0 
drm                   303102  7 ttm,i915,drm_kms_helper,nouveau
i2c_algo_bit           13413  2 i915,nouveau
parport_pc             32701  0 
ppdev                  17671  0 
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
usb_storage            62209  1 
hid_generic            12548  0 
usbhid                 52659  0 
hid                   106148  2 hid_generic,usbhid
rtsx_pci_sdmmc         23274  0 
psmouse               106678  0 
ahci                   25819  3 
libahci                32716  1 ahci
rtsx_pci               46202  2 rtsx_pci_ms,rtsx_pci_sdmmc
r8168                 434402  0 

aniruth@Jarvis:~$ cat /etc/network/interfaces
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

aniruth@Jarvis:~$ cat /etc/resolv.conf
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN

aniruth@Jarvis:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

aniruth@Jarvis:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 78:84:3c:38:24:88  
          inet6 addr: fe80::7a84:3cff:fe38:2488/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6213 errors:0 dropped:0 overruns:0 frame:0
          TX packets:436 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:540348 (540.3 KB)  TX bytes:79684 (79.6 KB)
          Interrupt:44 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:233 errors:0 dropped:0 overruns:0 frame:0
          TX packets:233 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:16909 (16.9 KB)  TX bytes:16909 (16.9 KB)

wlan0     Link encap:Ethernet  HWaddr 0c:84:dc:f4:4e:47  
          inet6 addr: fe80::e84:dcff:fef4:4e47/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16

```
[/SIZE]

---

### Post by praseodym on 2014-10-25
@Aniruthan_M_E: Uninstall this package then
```

sudo apt-get remove --purge resolvconf
```
and try it again.

@tom137: Have you tried it via:
```

sudo pppoeconf
```
Answer all questions with "Yes" or "OK" and check

---

### Post by Aniruthan_M_E on 2014-10-25
Ok. Going to try it. Thanks.

---

### Post by Aniruthan_M_E on 2014-10-25
> **praseodym said:**
> @Aniruthan_M_E: Uninstall this package then
```

sudo apt-get remove --purge resolvconf
```
and try it again.

@tom137: Have you tried it via:
```

sudo pppoeconf
```
Answer all questions with "Yes" or "OK" and check

Thanks @praseodym. When I rebooted this time, nameservers for my LAN have been automatically added. Don't know how. But it works just fine now. Thanks for all the help rendered.

---

### Post by prelude2 on 2014-10-25
> **praseodym said:**
> @Aniruthan_M_E: Uninstall this package then
```

sudo apt-get remove --purge resolvconf
```
and try it again.

@tom137: Have you tried it via:
```

sudo pppoeconf
```
Answer all questions with "Yes" or "OK" and check


Hi praseodym,

Any chance you could take a look at my problem? 

[http://ubuntuforums.org/showthread.php?t=2249933](http://ubuntuforums.org/showthread.php?t=2249933)

Thanks!

---

### Post by tom137 on 2014-10-27
Hi all.

many many thanks, ethernet is working now. Thanks a lot!

---

### Post by gpsvn2 on 2014-10-28
> **gpsvn2 said:**
> Thank you praseodym. After typing sudo modprobe -v r8169, it works right away.

It seems I have to run this command every time my PC restarted.

---

### Post by praseodym on 2014-10-28
Check the blacklists:
```

grep r8 /etc/modprobe.d/*
```
If there is no output force the module  being loaded at boot-up:
```

echo r8169 | sudo tee -a /etc/modules
```

---

### Post by lasleym on 2014-10-28
OK - three weeks later, had to restart computer. after first command, results indicate name server has been renamed. 

Check route -n same status.

Restarting networking says Job failed while stopping. 
Stopping says Job failed while stopping. 
Force-reload days Job is already running: networking.

Network-manager can stop and start, but name server still does not stick, and we still have a supposed Wi-FI connection even though we're using a hard wired modem. 

> **praseodym said:**
> You need nameservers when its not working:
```

echo -e "nameserver 8.8.8.8\nnameserver 8.8.4.4" | sudo tee -a /etc/resolv.conf
sudo service networking restart
```

---

### Post by felix18 on 2014-10-29
> **praseodym said:**
> No problem.

First: Add nameservers to the /etc/resolv.conf file:
```

echo -e "nameserver 8.8.8.8\nnameserver 8.8.4.4" | sudo tee /etc/resolv.conf
sudo service network-manager restart
```
If it works: Ok.
If not: Download these files and save them in "Downloads":

[http://media.cdn.ubuntu-de.org/forum/attachments/45/14/3005217-r8168-dkms-8.038.00.tar.gz](http://media.cdn.ubuntu-de.org/forum/attachments/45/14/3005217-r8168-dkms-8.038.00.tar.gz)

[http://de.archive.ubuntu.com/ubuntu/pool/main/d/dkms/dkms_2.2.0.3-1.1ubuntu5_all.deb](http://de.archive.ubuntu.com/ubuntu/pool/main/d/dkms/dkms_2.2.0.3-1.1ubuntu5_all.deb)

Do not extract the *tar.gz!

Installation:

```
cd ~/Downloads/
sudo dpkg -i *.deb
sudo tar xvf 3005217-r8168-dkms-8.038.00.tar.gz -C /usr/src
sudo dkms add -m r8168-dkms -v 8.038.00
sudo dkms build -m r8168-dkms -v 8.038.00
sudo dkms install -m r8168-dkms -v 8.038.00
sudo depmod -a
sudo update-initramfs -u 
echo "blacklist r8169" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
Reboot.

I got the same problem with Ubuntu 14.04 LTS on DELL Optiplex 9020.
The ethernet controller is I217-LM.
I tried these steps but still can not access the internet.

The outputs:

uname -a
Linux felix 3.13.0-32-generic #57-Ubuntu SMP Tue Jul 15 03:51:08 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux


lspci -nnk | grep -iA2 net
00:19.0 Ethernet controller [0200]: Intel Corporation Ethernet Connection I217-LM [8086:153a] (rev 04)
    Subsystem: Dell Device [1028:05a4]
    Kernel driver in use: e1000e


lsmod
Module                  Size  Used by
bnep                   19624  2 
rfcomm                 69160  0 
bluetooth             391196  10 bnep,rfcomm
snd_hda_codec_realtek    61438  1 
snd_hda_codec_hdmi     46254  2 
dcdbas                 14928  0 
x86_pkg_temp_thermal    14205  0 
intel_powerclamp       14705  0 
coretemp               13435  0 
kvm_intel             143060  0 
kvm                   451511  1 kvm_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
crct10dif_pclmul       14289  0 
crc32_pclmul           13113  0 
ghash_clmulni_intel    13216  0 
aesni_intel            55624  0 
aes_x86_64             17131  1 aesni_intel
lrw                    13286  1 aesni_intel
gf128mul               14951  1 lrw
glue_helper            13990  1 aesni_intel
ablk_helper            13597  1 aesni_intel
cryptd                 20359  3 ghash_clmulni_intel,aesni_intel,ablk_helper
snd_hda_intel          52355  7 
snd_rawmidi            30144  1 snd_seq_midi
serio_raw              13462  0 
radeon               1522422  1 
snd_hda_codec         192906  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
snd_pcm               102099  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
lpc_ich                21080  0 
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
i915                  783805  5 
snd_timer              29482  2 snd_pcm,snd_seq
mei_me                 18627  0 
mei                    82276  1 mei_me
snd                    69238  25 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
ttm                    85115  1 radeon
drm_kms_helper         53081  2 i915,radeon
soundcore              12680  1 snd
drm                   303102  7 ttm,i915,drm_kms_helper,radeon
i2c_algo_bit           13413  2 i915,radeon
video                  19476  1 i915
mac_hid                13205  0 
parport_pc             32701  0 
ppdev                  17671  0 
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
hid_generic            12548  0 
usbhid                 52570  0 
hid                   106148  2 hid_generic,usbhid
e1000e                264078  0 
ptp                    18933  1 e1000e
ahci                   25819  2 
psmouse               106678  0 
libahci                32560  1 ahci
pps_core               19382  1 ptp


cat /etc/network/interfaces
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback


route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface


ifconfig -a
eth0      Link encap:Ethernet  HWaddr 98:90:96:9a:ed:f5  
          inet6 addr: fe80::9a90:96ff:fe9a:edf5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:23507 errors:0 dropped:159 overruns:0 frame:0
          TX packets:773 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3419588 (3.4 MB)  TX bytes:210132 (210.1 KB)
          Interrupt:20 Memory:f7d00000-f7d20000 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:472 errors:0 dropped:0 overruns:0 frame:0
          TX packets:472 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:35984 (35.9 KB)  TX bytes:35984 (35.9 KB)


sudo ethtool eth0
Settings for eth0:
    Supported ports: [ TP ]
    Supported link modes:   10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Full 
    Supported pause frame use: No
    Supports auto-negotiation: Yes
    Advertised link modes:  10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Full 
    Advertised pause frame use: No
    Advertised auto-negotiation: Yes
    Speed: 100Mb/s
    Duplex: Full
    Port: Twisted Pair
    PHYAD: 1
    Transceiver: internal
    Auto-negotiation: on
    MDI-X: on (auto)
    Supports Wake-on: pumbg
    Wake-on: g
    Current message level: 0x00000007 (7)
                   drv probe link
    Link detected: yes

---

### Post by MrKappa on 2014-11-08
> **praseodym said:**
> @Aniruthan_M_E: Uninstall this package then
```

sudo apt-get remove --purge resolvconf
```
and try it again.

@tom137: Have you tried it via:
```

sudo pppoeconf
```
Answer all questions with "Yes" or "OK" and check

Hello' I have LAN connection problem too on Asus K50C where I had to install Ubuntu 14.04 LTS from scratch.
Previously on this pc there was Ubuntu 12.04 and ethernet was working fine.
Originally, just after the installation, there was not ethernet connection available (on Ubuntu panel the lan connection was in grey and not selectable). Wifi connection was working fine.

Now I followed some recommandation from this thread and I have installed r8168 drivers and removed r8169 version.

cd ~/Downloads/
sudo dpkg -i *.deb
sudo tar xvf 3005217-r8168-dkms-8.038.00.tar.gz -C /usr/src
sudo dkms add -m r8168-dkms -v 8.038.00
sudo dkms build -m r8168-dkms -v 8.038.00
sudo dkms install -m r8168-dkms -v 8.038.00
sudo depmod -a
sudo update-initramfs -u 
echo "blacklist r8169" | sudo tee -a /etc/modprobe.d/blacklist.

After reboot now the network functionality (lan) is available but I don't have the ethernet in ready status. It always try to get the router IP and get disconnected. If I switch from DHCP to manual IP and gateway the network apparently is ready but the connection in reality does not work and I don't have access even to the local router page. Lan cable itself or hardware is fine as the pc is working fine booting from Windows with a live cd (like Bart PE).

From terminal I get the following:

username@username-K50C:~$ uname -a
Linux username-K50C 3.13.0-40-generic #68-Ubuntu SMP Tue Nov 4 01:48:53 UTC 2014 i686 i686 i686 GNU/Linux

usernamee@username-K50C:~$ lspci -nnk | grep -iA2 net
02:00.0 Network controller [0280]: Qualcomm Atheros AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
	Subsystem: AzureWave AW-NE785 / AW-NE785H 802.11bgn Wireless Full or Half-size Mini PCIe Card [1a3b:1089]
	Kernel driver in use: ath9k
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 01)
	Subsystem: Realtek Semiconductor Co., Ltd. RTL8111/8168 PCI Express Gigabit Ethernet controller [10ec:8168]
	Kernel driver in use: r8168

username@username-K50C:~$ lsmod
Module                  Size  Used by
ctr                    12905  1 
ccm                    17496  1 
snd_hda_codec_realtek    59259  1 
snd_hda_intel          42730  6 
snd_hda_codec         164067  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13272  1 snd_hda_codec
snd_pcm                85501  2 snd_hda_codec,snd_hda_intel
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_rawmidi            25135  1 snd_seq_midi
arc4                   12536  2 
snd_seq                55383  2 snd_seq_midi_event,snd_seq_midi
ath9k                 144602  0 
ath9k_common           13359  1 ath9k
rfcomm                 53664  4 
coretemp               13195  0 
uvcvideo               71309  0 
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
bnep                   18895  2 
ath9k_hw              438205  2 ath9k_common,ath9k
snd_timer              28584  2 snd_pcm,snd_seq
bluetooth             342208  10 bnep,rfcomm
videobuf2_vmalloc      13048  1 uvcvideo
ath                    23922  3 ath9k_common,ath9k,ath9k_hw
snd                    60939  22 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
videobuf2_memops       13170  1 videobuf2_vmalloc
videobuf2_core         39258  1 uvcvideo
joydev                 17101  0 
mac80211              546051  1 ath9k
videodev              108503  2 uvcvideo,videobuf2_core
soundcore              12600  1 snd
serio_raw              13230  0 
cfg80211              409394  3 ath,ath9k,mac80211
shpchp                 32128  0 
sis_agp                13091  1 
video                  18903  0 
parport_pc             31981  0 
ppdev                  17391  0 
asus_laptop            23897  0 
r8169                  61562  0 
mii                    13654  1 r8169
sparse_keymap          13708  1 asus_laptop
lp                     13299  0 

username@username-K50C:~$ cat /etc/network/interfaces
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

username@username-K50C:~$ cat /etc/resolv.conf
# Generated by NetworkManager
domain fritz.box
search fritz.box
nameserver 127.0.1.1

username@username-K50C:~$ route -n
Tabella di routing IP del kernel
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.178.1   0.0.0.0         UG    0      0        0 wlan0
192.168.178.0   0.0.0.0         255.255.255.0   U     9      0        0 wlan0

username@username-K50C:~$ ifconfig -a
eth0      Link encap:Ethernet  IndirizzoHW 48:5b:39:08:7f:09  
          indirizzo inet6: fe80::4a5b:39ff:fe08:7f09/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2048 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:2192 overruns:0 carrier:0
          collisioni:0 txqueuelen:1000 
          Byte RX:242807 (242.8 KB)  Byte TX:0 (0.0 B)
          Interrupt:40 Indirizzo base:0x2000 

lo        Link encap:Loopback locale  
          indirizzo inet:127.0.0.1  Maschera:255.0.0.0
          indirizzo inet6: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:14452 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14452 errors:0 dropped:0 overruns:0 carrier:0
          collisioni:0 txqueuelen:0 
          Byte RX:1181015 (1.1 MB)  Byte TX:1181015 (1.1 MB)

wlan0     Link encap:Ethernet  IndirizzoHW 1c:4b:d6:7a:c6:ac  
          indirizzo inet:192.168.178.34  Bcast:192.168.178.255  Maschera:255.255.255.0
          indirizzo inet6: fe80::1e4b:d6ff:fe7a:c6ac/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:16009 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5401 errors:0 dropped:0 overruns:0 carrier:0
          collisioni:0 txqueuelen:1000 
          Byte RX:3026377 (3.0 MB)  Byte TX:927503 (927.5 KB)
 

parport                40836  3 lp,ppdev,parport_pc
input_polldev          13648  1 asus_laptop
mac_hid                13037  0 
pata_acpi              12886  0 
psmouse                91357  0 
sata_sis               12711  2 
r8168                 387138  0 

username@username-K50C:~$ sudo ethtool eth0
Settings for eth0:
	Supported ports: [ TP ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Supported pause frame use: No
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Advertised pause frame use: Symmetric Receive-only
	Advertised auto-negotiation: Yes
	Speed: 100Mb/s
	Duplex: Full
	Port: Twisted Pair
	PHYAD: 0
	Transceiver: internal
	Auto-negotiation: on
	MDI-X: Unknown
	Supports Wake-on: pumbg
	Wake-on: g
	Current message level: 0x00000033 (51)
			       drv probe ifdown ifup
	Link detected: yes

Please, do you understand what is wrong currently? Thank you in advance

---

### Post by praseodym on 2014-11-09
Obviously, the wrong driver is still loaded:
```

sudo modprobe -rfv r8169
sudo modprobe -v r8168
sudo depmod -a
sudo update-initramfs -u
```

---

### Post by MrKappa on 2014-11-09
> **praseodym said:**
> Obviously, the wrong driver is still loaded:
```

sudo modprobe -rfv r8169
sudo modprobe -v r8168
sudo depmod -a
sudo update-initramfs -u
```

Thanks praseodym. Unfortunately the result is the same.

username@username-K50C:~$ sudo modprobe -rfv r8169
[sudo] password for username: 
rmmod r8169
rmmod mii
username@username-K50C:~$ sudo modprobe -v r8168
username@username-K50C:~$ sudo depmod -a
username@username-K50C:~$ sudo update-initramfs -u
update-initramfs: Generating /boot/initrd.img-3.13.0-40-generic
username@username-K50C:~$ 

After the rebooot I see that LAN does not have internet but seems to be apparently connected with manual ip, mask, gateway but get no connections and restart in DHCP.

I notice from "ifconfig -a" that subnet mask is not 255.255.255.0 except on wlan0. It should not be the same for both? 

lo Link encap:Loopback locale
indirizzo inet:127.0.0.1 Maschera:255.0.0.0
indirizzo inet6: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:65536 Metric:1
RX packets:14452 errors:0 dropped:0 overruns:0 frame:0
TX packets:14452 errors:0 dropped:0 overruns:0 carrier:0
collisioni:0 txqueuelen:0
Byte RX:1181015 (1.1 MB) Byte TX:1181015 (1.1 MB)

wlan0 Link encap:Ethernet IndirizzoHW 1c:4b:d6:7a:c6:ac
indirizzo inet:192.168.178.34 Bcast:192.168.178.255 Maschera:255.255.255.0
indirizzo inet6: fe80::1e4b:d6ff:fe7a:c6ac/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:16009 errors:0 dropped:0 overruns:0 frame:0
TX packets:5401 errors:0 dropped:0 overruns:0 carrier:0
collisioni:0 txqueuelen:1000
Byte RX:3026377 (3.0 MB) Byte TX:927503 (927.5 KB)

If I type "sudo pppoeconf" I get this error:

Not connected
Controllate 2 interfacce, ma il concentratore d'accesso  &#9474;          
          &#9474; del provider non ha risposto. Controllare la rete e i    &#9474;          
          &#9474; cavi del modem. Un'altra ragione per il fallimento del   &#9474;          
          &#9474; controllo potrebbe anche essere un'altra istanza di      &#9474;          
          &#9474; pppoe in esecuzione, che controlla il modem.  

Which means: 2 interfaces have been checked but access concentrator of the provider did respond.
Check the network and the modem cables. Another reason for failing could be another running PPPOE istance that is controlling the modem.

Thanks again for any suggestion.

---

### Post by praseodym on 2014-11-09
Tried:
```

sudo pppoeconf eth0
```

---

### Post by MrKappa on 2014-11-09
> **praseodym said:**
> Tried:
```

sudo pppoeconf eth0
```

I tried this command typing yes to all questions and adding my adsl account information (I understood I should add username and password of my provider).
But after reboot the LAN is again in grey and I read "Device not available" 

Regards

---

### Post by praseodym on 2014-11-09
Open this file:

```
gksudo gedit cat /etc/NetworkManager/NetworkManager.conf
```
Change "false" to "true", save, close the editor and reboot.

---

### Post by Jim_Menegay on 2014-11-09
I have a wired home network consisting of an Apple &#8220;Airport&#8221; router and wifi base, an iMac, and a Windows system.  Put together a homebuilt based on Gigabyte GA-970A-UD3P and an AMD CPU.  Installed Ubuntu 14.04.  Can&#8217;t get wired connection to internet working.  Is supposed to plug-and-play with DHCP???

After reading in this thread, I guessed the problem might be the Realtek r8169 driver, so I tried following instructions for changing to r8168.  But it doesn&#8217;t seem to have changed anything after the reboot.  The iMac and Windows PC are still connected to internet OK.

I followed these instructions:
echo -e "nameserver 8.8.8.8\nnameserver 8.8.4.4" | sudo tee /etc/resolv.conf
sudo service network-manager restart

sudo dpkg -i *.deb
sudo tar xvf 3005217-r8168-dkms-8.038.00.tar.gz -C /usr/src
sudo dkms add -m r8168-dkms -v 8.038.00
sudo dkms build -m r8168-dkms -v 8.038.00
sudo dkms install -m r8168-dkms -v 8.038.00
sudo depmod -a
sudo update-initramfs -u 
echo "blacklist r8169" | sudo tee -a /etc/modprobe.d/blacklist.conf

<reboot>

But I still have the problem.  Here is some of what I see:

Settings for eth0:
    Supported ports: [ TP MII ]
    Supported link modes:   10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Half 1000baseT/Full 
    Supported pause frame use: No
    Supports auto-negotiation: Yes
    Advertised link modes:  10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Half 1000baseT/Full 
    Advertised pause frame use: Symmetric Receive-only
    Advertised auto-negotiation: Yes
    Link partner advertised link modes:  10baseT/Half 10baseT/Full 
                                         100baseT/Half 100baseT/Full 
                                         1000baseT/Full 
    Link partner advertised pause frame use: Symmetric
    Link partner advertised auto-negotiation: Yes
    Speed: 1000Mb/s
    Duplex: Full
    Port: MII
    PHYAD: 0
    Transceiver: internal
    Auto-negotiation: on
    Supports Wake-on: pumbg
    Wake-on: g
    Current message level: 0x00000033 (51)
                   drv probe ifdown ifup
    Link detected: yes


##ifconfig
eth0      Link encap:Ethernet  HWaddr fc:aa:14:0e:86:93  
          inet6 addr: fe80::feaa:14ff:fe0e:8693/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1870 errors:0 dropped:0 overruns:0 frame:0
          TX packets:27 errors:0 dropped:1577 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:234345 (234.3 KB)  TX bytes:4577 (4.5 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:149 errors:0 dropped:0 overruns:0 frame:0
          TX packets:149 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:10465 (10.4 KB)  TX bytes:10465 (10.4 KB)

#lshw
  *-network
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 06
       serial: fc:aa:14:0e:86:93
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168e-3_0.0.4 03/27/12 latency=0 link=yes multicast=yes port=MII speed=1Gbit/s
       resources: irq:73 ioport:d000(size=256) memory:fe100000-fe100fff memory:d2100000-d2103fff

#/etc/modprobe.d/blacklist.conf
&#8230;
# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac
blacklist r8169
<eof>

#/etc/resolv.conf  <after running echo &#8230;>
nameserver 8.8.8.8
nameserver 8.8.4.4

#/etc/resolve.conf <after reboot>
# Dynamic resolv.conf(5) file for glib resolver(3) generated by resolvconf(8)
##  DO NOT EDIT THIS FILE BY HAND - - YOUR CHANGES WILL BE OVERWRITTEN

ADDED 30 MIN LATER...
After posting, I noticed the following instructions:
sudo modprobe -rfv r8169
sudo modprobe -v r8168
sudo depmod -a
sudo update-initramfs -u

I typed that in, and after a reboot, it is working.  Thx to Praseodyme.

---

### Post by Michael Steinberg on 2014-11-11
I had intermittent connection problems which have turned into a full blown failure. For a while I could get the connection back by restarting netword-manager but now nothing works. I use Ubuntu 1404, with Intel 82566 card. I was able to upgrade to the current driver, 3.1.0.2, and then linked it with dkms. The new driver shows up when i hit lshw -C network but I still have no connection. I tried redoing the nameservers and that has no effect; the actual resolv.conf file never changes. PLEASE help me. This computer is how I make my living.

---

### Post by praseodym on 2014-11-12
Try
```

sudo apt-get remove --purge resolvconf
```
and reboot.

---

### Post by Michael Steinberg on 2014-11-12
Thanks for the reply but it makes no difference. i am no expert in reading log files but i see that both IvP4 and 6 connections timed out.

---

### Post by praseodym on 2014-11-12
Now try
```

echo -e "nameserver 8.8.8.8\nnameserver 8.8.4.4" | sudo tee /etc/resolv.conf
sudo /etc/init.d/networking restart
```

---

### Post by Michael Steinberg on 2014-11-12
Alas, same nothing even after reboot. BTW, i tried the live CD of 14.10 and it couldn't connect either. (I think, because it wouldn't give me anything but visual garbage after the initial try-or-install screen. Could the network failure be a hardware problem? Should i buy a new network card and use that instead?

---

### Post by Michael Steinberg on 2014-11-12
I really don't want to but I'm getting pretty desperate.

---

### Post by praseodym on 2014-11-12
Install this file via double-click and show the output of
```

sudo ethtool eth0
```

[http://de.archive.ubuntu.com/ubuntu/pool/main/e/ethtool/ethtool_3.13-1_i386.deb](http://de.archive.ubuntu.com/ubuntu/pool/main/e/ethtool/ethtool_3.13-1_i386.deb)

---

### Post by Michael Steinberg on 2014-11-12
Strangely, after leaving it for a while I came back and the networking returned. i wish I could be confident that it won't go away again. Thanks VERY MUCH and I hope I won't have to call upon your good offices again! I had ethtool installed already and the output was:

	Supported ports: [ TP ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Supported pause frame use: No
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Advertised pause frame use: No
	Advertised auto-negotiation: Yes
	Speed: 100Mb/s
	Duplex: Half
	Port: Twisted Pair
	PHYAD: 1
	Transceiver: internal
	Auto-negotiation: on
	MDI-X: off (auto)
	Supports Wake-on: pumbg
	Wake-on: g
	Current message level: 0x00000007 (7)
			       drv probe link
	Link detected: yes

Is there anything else I should know?

---

### Post by Michael Steinberg on 2014-11-12
well....the network was dead the next time the computer woke from suspend. Restarting it fixed the problem for now but I'm clearly still having problems. What next?

---

### Post by MrKappa on 2014-11-14
> **praseodym said:**
> Open this file:

```
gksudo gedit cat /etc/NetworkManager/NetworkManager.conf
```
Change "false" to "true", save, close the editor and reboot.

Hello' praseodym, sorry for no feedback but I could not run any test in these days. 

After last advice I got a secondary LAN connections called "ifupdown" but the result does not change unfortunately. :(
I understand I can remove it again following this page:
[http://askubuntu.com/questions/455736/remove-ifupdowneth0-connection](http://askubuntu.com/questions/455736/remove-ifupdowneth0-connection)

Then after reboot I see that LAN try to connect but nothing happen. 

NetworkManager.conf is now:
[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

no-auto-default=48:5B:39:08:7F:09,

[ifupdown]
managed=false

I tested: cat /etc/udev/rules.d/70-persistent-net.rules
# This file was automatically generated by the /lib/udev/write_net_rules
# program, run by the persistent-net-generator.rules rules file.
#
# You can modify it, as long as you keep each rule on a single
# line, and change only the value of the NAME= key.

# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="48:5b:39:08:7f:09", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x168c:0x002b (ath9k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="1c:4b:d6:7a:c6:ac", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

echo -e "nameserver 8.8.8.8\nnameserver 8.8.4.4" | sudo tee /etc/resolv.conf
[sudo] password for username: 
nameserver 8.8.8.8
nameserver 8.8.4.4

I have repeated again the sequence on this thread and your advices from the first post:

```
uname -a
Linux username-K50C 3.13.0-39-generic #66-Ubuntu SMP Tue Oct 28 13:31:23 UTC 2014 i686 i686 i686 GNU/Linux

 lspci -nnk | grep -iA2 net
02:00.0 Network controller [0280]: Qualcomm Atheros AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
	Subsystem: AzureWave AW-NE785 / AW-NE785H 802.11bgn Wireless Full or Half-size Mini PCIe Card [1a3b:1089]
	Kernel driver in use: ath9k
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 01)
	Subsystem: Realtek Semiconductor Co., Ltd. RTL8111/8168 PCI Express Gigabit Ethernet controller [10ec:8168]
	Kernel driver in use: r8168

lsmod
Module                  Size  Used by
ctr                    12905  1 
ccm                    17496  1 
snd_hda_codec_realtek    59259  1 
snd_hda_intel          42730  3 
hid_generic            12492  0 
snd_hda_codec         164067  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13272  1 snd_hda_codec
arc4                   12536  2 
snd_pcm                85501  2 snd_hda_codec,snd_hda_intel
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
ath9k                 144602  0 
snd_rawmidi            25135  1 snd_seq_midi
ath9k_common           13359  1 ath9k
ath9k_hw              438205  2 ath9k_common,ath9k
snd_seq                55383  2 snd_seq_midi_event,snd_seq_midi
coretemp               13195  0 
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
ath                    23922  3 ath9k_common,ath9k,ath9k_hw
uvcvideo               71309  0 
snd_timer              28584  2 snd_pcm,snd_seq
videobuf2_vmalloc      13048  1 uvcvideo
snd                    60939  16 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
mac80211              546051  1 ath9k
joydev                 17101  0 
videobuf2_memops       13170  1 videobuf2_vmalloc
usbhid                 47070  0 
videobuf2_core         39258  1 uvcvideo
serio_raw              13230  0 
videodev              108503  2 uvcvideo,videobuf2_core
soundcore              12600  1 snd
rfcomm                 53664  0 
hid                    87604  2 hid_generic,usbhid
bnep                   18895  2 
bluetooth             342208  10 bnep,rfcomm
cfg80211              409394  3 ath,ath9k,mac80211
video                  18903  0 
asus_laptop            23897  0 
sparse_keymap          13708  1 asus_laptop
input_polldev          13648  1 asus_laptop
sis_agp                13091  1 
mac_hid                13037  0 
shpchp                 32128  0 
parport_pc             31981  0 
ppdev                  17391  0 
lp                     13299  0 
parport                40836  3 lp,ppdev,parport_pc
pata_acpi              12886  0 
psmouse                91357  0 
r8168                 461472  0 
sata_sis               12711  2 

cat /etc/network/interfaces
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

=> nothing to add on interfaces config for eth0?

cat /etc/resolv.conf
# Generated by NetworkManager
domain fritz.box
search fritz.box
nameserver 127.0.1.1

route -n
Tabella di routing IP del kernel
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.178.1   0.0.0.0         UG    0      0        0 wlan0
192.168.178.0   0.0.0.0         255.255.255.0   U     9      0        0 wlan0

=> here I don't see routing for eth0!!!

ifconfig -a
eth0      Link encap:Ethernet  IndirizzoHW 48:5b:39:08:7f:09  
          indirizzo inet6: fe80::4a5b:39ff:fe08:7f09/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:169 overruns:0 carrier:0
          collisioni:0 txqueuelen:1000 
          Byte RX:0 (0.0 B)  Byte TX:0 (0.0 B)
          Interrupt:40 Indirizzo base:0xe000 

lo        Link encap:Loopback locale  
          indirizzo inet:127.0.0.1  Maschera:255.0.0.0
          indirizzo inet6: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:1818 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1818 errors:0 dropped:0 overruns:0 carrier:0
          collisioni:0 txqueuelen:0 
          Byte RX:190315 (190.3 KB)  Byte TX:190315 (190.3 KB)

wlan0     Link encap:Ethernet  IndirizzoHW 1c:4b:d6:7a:c6:ac  
          indirizzo inet:192.168.178.34  Bcast:192.168.178.255  Maschera:255.255.255.0
          indirizzo inet6: fe80::1e4b:d6ff:fe7a:c6ac/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8144 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7249 errors:0 dropped:0 overruns:0 carrier:0
          collisioni:0 txqueuelen:1000 
          Byte RX:6135539 (6.1 MB)  Byte TX:983095 (983.0 KB)

sudo ethtool eth0
Settings for eth0:
	Supported ports: [ TP ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Supported pause frame use: No
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Advertised pause frame use: No
	Advertised auto-negotiation: Yes
	Speed: 100Mb/s
	Duplex: Full
	Port: Twisted Pair
	PHYAD: 0
	Transceiver: internal
	Auto-negotiation: off
	MDI-X: Unknown
	Supports Wake-on: pumbg
	Wake-on: g
	Current message level: 0x00000033 (51)
			       drv probe ifdown ifup
	Link detected: yes


```

Apparently hardware and driver seems to be ok but maybe still some routing or gateway problem?

Thank you if you have some other idea!

---

### Post by MrKappa on 2014-11-15
PS: also I don't understand why I should add pppoe data (adsl account information) using "sudo pppoeconf eth0" on a pc connected to router which does provide internet connection to other devices through lan and wlan. 
This pc in particular should be used by my brothers in another location then it should be able to be used through lan in DHCP as before (I hope!). Thanks again

---

### Post by gsaggior on 2014-11-15
I have a similar problem. Launching wireshark i see that either packets are sent and received. Do you think it could be a problem related to the dns server presence into the resolv.conf ?
DHCP client does not work anymore, it was a couple of days ago, I tried to restart the Vodafone Station 2, but with no success.

Thanks

P.S. I know i did not tried any hints suggested in the 3d, but the Ubuntu Pc is currently not connected..... I am lazy.... ;-)

---

### Post by MrKappa on 2014-11-15
> **gsaggior said:**
> I have a similar problem. Launching wireshark i see that either packets are sent and received. Do you think it could be a problem related to the dns server presence into the resolv.conf ?
DHCP client does not work anymore, it was a couple of days ago, I tried to restart the Vodafone Station 2, but with no success.

Thanks

P.S. I know i did not tried any hints suggested in the 3d, but the Ubuntu Pc is currently not connected..... I am lazy.... ;-)

Generally this issue reported on this thread is related to some pc where latest drivers for LAN are not compatible. Then if your pc was working before and you didn't change anything I may understand it could be a local issue with your Vodafone station. The router should be able to assign the IP to each device in the network using DHCP or otherwise you can try fixed IP and use for i.e. "open dns" address to get access to internet (220.67.222.222). Do you have the possibility to use a live cd (ubuntu or other distro), boot from it and check if you go to internet to exclude no other problems on hardware of your pc, cable or router? 
Furtheway I recommend to post the result of these commands here:
[http://ubuntuforums.org/showthread.php?t=2238805&p=13094940#post13094940](http://ubuntuforums.org/showthread.php?t=2238805&p=13094940#post13094940)

---

### Post by gsaggior on 2014-11-15
Those commands fixed immediately my problem !!!!  

echo -e "nameserver 192.168.1.1\nnameserver 8.8.4.4" | sudo tee /etc/resolv.conf
sudo /etc/init.d/networking restart

But restarting the PC my problem appeared again, even reconfiguring the resolv.conf manually . I need to investigate with more precision.

---

### Post by gsaggior on 2014-11-15
Mr. Kappa,

Probably it makes sense what you are telling. 
In my case could be a problem related to the BOOTP/DHCP protocol server running on the vodafone station. 
However as soon as I modified the resolv.conf everything started working, in fact i saw the Ip address given by the DHCP server; but after restarting the PC and modifying again resolv.conf it did not fix again my problem.
I need to investigate more, also with wireshark and create the outputs for a better analysis 
I would like also to recreate, step-by-step, the situation that allowed me to get the ethernet interface up & running.

Thanks !

---

### Post by MrKappa on 2014-11-15
> **gsaggior said:**
> Mr. Kappa,

Probably it makes sense what you are telling. 
In my case could be a problem related to the BOOTP/DHCP protocol server running on the vodafone station. 
However as soon as I modified the resolv.conf everything started working, in fact i saw the Ip address given by the DHCP server; but after restarting the PC and modifying again resolv.conf it did not fix again my problem.
I need to investigate more, also with wireshark and create the outputs for a better analysis 
I would like also to recreate, step-by-step, the situation that allowed me to get the ethernet interface up & running.

Thanks !

You are welcome. I was hoping for you that you had fixed the problem. I'm still fighting with my issue on LAN as well after several tests.... :(

---

### Post by MrKappa on 2014-11-18
After several tests and attemps finally I could solve my problem on Asus K50C laptop using Realtek Ethernet controller. I got no success with Ubuntu 14.04 then I decide to use the older version 12.04 LTS (which I understood is supported until 2017) and I have repeated the recommandation in this thread. 
I got the "light" with lan connection after the driver update as suggested on this post:
[http://ubuntuforums.org/showthread.php?t=2238805&page=4&p=13144232#post13144232](http://ubuntuforums.org/showthread.php?t=2238805&page=4&p=13144232#post13144232)
I hope it might help others. Thank you

---

### Post by Michael Steinberg on 2014-11-21
I am once again having problems, only worse. None of the fixes work for long; every now and then I connect but once the computer suspends it's offline again. Restarting occasionally helps but again not for long. The kern.log says "link becomes ready" but that's it, and it reads the same whether there's a connection or not. I replaced my router because the old one was getting flaky but that didn't help either. HELP!

---

### Post by Michael Steinberg on 2015-03-26
It turned out someone or something had switched my ethernet hub from "Dual speed" to "Extension Port." Once I changed it back the problem went away.

---

### Post by Sivkumar_Reghupath on 2015-05-17
Hey there,

I have just installed Ubuntu 14.04. My ethernet conroller shows disconnected. Kindly help me. the code results a


> 
siva@siva-Presario-V3700-Notebook-PC:~$ uname -a
Linux siva-Presario-V3700-Notebook-PC 3.16.0-30-generic #40~14.04.1-Ubuntu SMP Thu Jan 15 17:43:14 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
siva@siva-Presario-V3700-Notebook-PC:~$ lspci -nnk | grep -iA2 net
05:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8039 PCI-E Fast Ethernet Controller [11ab:4353] (rev 14)
    Subsystem: Hewlett-Packard Company Device [103c:30cd]
    Kernel driver in use: sky2
07:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
    Subsystem: Hewlett-Packard Company BCM4312 802.11b/g Wireless LAN Controller [103c:137d]
    Kernel driver in use: b43-pci-bridge
siva@siva-Presario-V3700-Notebook-PC:~$ echo -e "nameserver 8.8.8.8\nnameserver 8.8.4.4" | sudo tee /etc/resolv.conf
[sudo] password for siva: 
nameserver 8.8.8.8
nameserver 8.8.4.4
siva@siva-Presario-V3700-Notebook-PC:~$ sudo service network-manager restart
network-manager stop/waiting
network-manager start/running, process 3323

Still didn't work.

Can you please provide me with a solution?

Thanks
Siva

---

### Post by Biscarri on 2015-05-21
Hi praseodym,

I would like you to help me with a similar problem concerning LAN communication of my ubuntu PC. Thank you very much in advance :-)
I attach a file with the echo to the commands you asked for to the forum user that started this thread. 
Note that there is no echo to the command   lspci -nnk | grep -iA2 net 

Before posting this message I've tried the following but it didn't work...
biscarri@biscarri-ews:~$ echo -e "nameserver 8.8.8.8\nnameserver 8.8.4.4" | sudo tee /etc/resolv.conf
[sudo] password for biscarri: 
no talloc stackframe at ../source3/param/loadparm.c:4864, leaking memory
nameserver 8.8.8.8
nameserver 8.8.4.4
biscarri@biscarri-ews:~$ sudo service network-manager restart
network-manager stop/waiting
network-manager start/running, process 11381

Once checked it didn't work, I have changed again nameserver... 

biscarri@biscarri-ews:~$ echo -e "nameserver 8.8.4.4\nnameserver 8.8.8.8" | sudo tee /etc/resolv.conf
nameserver 8.8.4.4
nameserver 8.8.8.8
biscarri@biscarri-ews:~$ sudo service network-manager restart
network-manager stop/waiting
network-manager start/running, process 11435
biscarri@biscarri-ews:~$ 



[ATTACH]262106[/ATTACH]

---

### Post by Biscarri on 2015-05-21
I've just done the following commands and then rebooted the PC and now connection LAN Ethernet works!!

Thank you very much PRASEODYM for the good job you do in the forum.

echo -e "nameserver 8.8.8.8\nnameserver 8.8.4.4" | sudo tee /etc/resolv.conf
sudo /etc/init.d/networking restart

---

### Post by Gards on 2015-08-27
Hello everybody,

I was faced at the same problem.

I'm on ubuntu 14.04 LTS and when I was connected to a ethernet plug, the OS indicated "disconnected cable".
In my case, the problem was linked to a old ethernet cable in a company.

Surprisingly, when I was in the bios, I was able to connect to internet but when Ubuntu was lauching, the green led in the back of the computer turns off.
When I put a windows computer, the connexion was ok.
I tried all solutions (conf file, drivers, etc.) on the web and none worked.
I tried to put another ethernet card => Nothing.
I tried Ubuntu 12.04 LTS => Nothing.

Finally, I found a solution (after 1 day of nightmare).

Unfortunately I'm a mac user (shame on me !) and the worst : I have a macbook air. You know a computer without ethernet plug, cd reader and vga plug (but light and with te best battery I've ever tried). So when you buy this device, you need to buy a USB/Ethernet cable, a portable cd reader and a vga adapter to use in your job. 

Any way, I took my ethernet<->usb cable and I used it on my machine (on USB 3.0 plug). It worked fine !
In my case, I think the ethernet cable in the building was bad (too long, I don't know) and the signal was not enough for Ubuntu to detect a connexion. The USB system restored the signal and Ubuntu was able to detect it. I hope Canonical will work on this problem because It's embarrassing to see that a windows can do it...

A link to the magic cable : ([http://www.fnac.com/mp12697015/Adaptateur-USB-2-0-vers-Ethernet-RJ45/w-4](http://www.fnac.com/mp12697015/Adaptateur-USB-2-0-vers-Ethernet-RJ45/w-4)).

Best

JG

---

### Post by firstname on 2015-10-21
HI i started this threat over one year ago and i came in handy more than once, ty for the effort and discussion.

BUT
I now use ubuntu 15.04. After the fresh installation, the internet connection  did not work.
    So I followed the instructions in this threat from page one to eight. From what i can gather the commands below are essential so i focused on them first.  ( i  actually tried every single line of code mentioned in this threat).
     ```
echo -e "nameserver 8.8.8.8\nnameserver 8.8.4.4" | sudo tee  /etc/resolv.conf sudo service network-manager restart  
```

this command did not work. So I downloaded the driver files and executed the following commands:
   
```

 cd ~/Downloads/ 
 sudo dpkg -i *.deb 
 sudo tar xvf 3005217-r8168-dkms-8.039.00.tar.gz -C /usr/src 
 sudo dkms add -m r8168-dkms -v 8.039.00 
 sudo dkms build -m r8168-dkms -v 8.039.00
 sudo dkms install -m r8168-dkms -v 8.039.00
 sudo depmod -a sudo update-initramfs -u  echo "blacklist r8169" | sudo tee -a /etc/modprobe.d/blacklist.conf 
```
     
the "sudo update-initramfs -u " line  says something with "error,  cannot use line with reboot... bla bla"

   anyway at some point it  worked. i dont know how or why, just the linux way i guess.
After weeks of use and without change Ubuntu suggested some updates.. i updated and guess what.. the internet connections wont work anymore.


   so i tried it again.. i used the commands below as well no luck so  far. 
Is there maybe  a new driver version like  3005217-r8168-dkms-**8.040.00.**tar.gz  ?
or do i have to install the *3005217-r8168-dkms-**8.038.00.**tar.gz*  version first then update to *3005217-r8168-dkms-**8.039.00.**tar.gz*  ?

    ```
// sudo apt-get install --reinstall linux-headers-generic linux-headers-$(uname -r) build-essential dkms 
   // sudo modprobe -rfv r8169 sudo modprobe -v r8168 sudo depmod -a  sudo update-initramfs -u
    // sudo apt-get remove --purge resolvconf sudo pppoeconf  
   // echo -e "nameserver 8.8.8.8\nnameserver 8.8.4.4" | sudo tee /etc/resolv sudo /etc/init.d/networking restart
```

---

### Post by praseodym on 2015-10-21
You dont't need to update. Download this file and save it in "Downloads":

[https://media-cdn.ubuntu-de.org/forum/attachments/28/33/3005217-r8168-dkms-8.040.00.tar.gz](https://media-cdn.ubuntu-de.org/forum/attachments/28/33/3005217-r8168-dkms-8.040.00.tar.gz)

Uninstall version 39
```

sudo dkms remove -m r8168-dkms -v 8.040.00 --all
sudo rm -r /usr/src/r8168-dkms-8.040.00 
```
and install "40" accordingly.

---

### Post by firstname on 2015-10-21
Hi praseodym,

it worked perfectly fine.
_**Thank you very much.**_

Here again the solution with he current "40" driver


**First, de-install:**

```
sudo dkms remove -m r8168-dkms -v 8.039.00 --all
sudo rm -r /usr/src/r8168-dkms-8.039.00

```

you might have to adjust the version (8.039.00) of your driver in the deinstall and install part


**Second, install:**
```
cd ~/Downloads/
sudo dpkg -i *.deb
sudo tar xvf 3005217-r8168-dkms-8.040.00.tar.gz -C /usr/src
sudo dkms add -m r8168-dkms -v 8.040.00
sudo dkms build -m r8168-dkms -v 8.040.00
sudo dkms install -m r8168-dkms -v 8.040.00
sudo depmod -a
sudo update-initramfs -u
echo "blacklist r8169" | sudo tee -a /etc/modprobe.d/blacklist.conf
```

then reboot and i should work

//you might have to adjust the version (8.039.00) of your driver in the de-install and install part

PS: could you tell where to find the newest version of the driver?
I guess i wont be the last release.

---

### Post by praseodym on 2015-10-22
Version 40 is from the Realtek homepage. The Ubuntu versions ship this driver with the package "r8168-dkms", but in 14.04 only version 37, version 39 in 15.04. I frequently update this posting for the newest driver with the dkms installer:

[http://forum.ubuntuusers.de/topic/lan-karte-funktioniert-nicht/#post-3005217](http://forum.ubuntuusers.de/topic/lan-karte-funktioniert-nicht/#post-3005217)

DKMS builds the driver for new kernels automatically

---

### Post by tobiz on 2015-11-25
[QUOTE=firstname;13376875]Hi praseodym,

it worked perfectly fine.
_**Thank you very much.**_

Here again the solution with he current "40" driver


**First, de-install:**

```
sudo dkms remove -m r8168-dkms -v 8.039.00 --all
sudo rm -r /usr/src/r8168-dkms-8.039.00

```

you might have to adjust the version (8.039.00) of your driver in the deinstall and install part


**Second, install:**
```
cd ~/Downloads/
sudo dpkg -i *.deb
sudo tar xvf 3005217-r8168-dkms-8.040.00.tar.gz -C /usr/src
sudo dkms add -m r8168-dkms -v 8.040.00
sudo dkms build -m r8168-dkms -v 8.040.00
sudo dkms install -m r8168-dkms -v 8.040.00
sudo depmod -a
sudo update-initramfs -u
echo "blacklist r8169" | sudo tee -a /etc/modprobe.d/blacklist.conf
```

then reboot and i should work

//you might have to adjust the version (8.039.00) of your driver in the de-install and install part

PS: could you tell where to find the newest version of the driver?
I guess i wont be the last release.[/QUOTE

I also have a problem with a Realtek R8168 which is built in to a PC running 14.04 and hence not changeable, it's under warrante. Eventually I gave up trying to solve the problem and bought a usb ethernet stick which has worked without problem, it uses the ax88179_178a driver.  Occasionally I return to the R8168 problem and found this thread.  What I don't understand with the above code are the lines 
cd ~/Downloads/
sudo dpkg -i *.deb

My reading of this is that it will install all .deb files in ~/Downloads.  Why would you want to do this?  I tried this sequence and found it downgraded some of my installed packages.  I checked this using syntaptic afterwards which said I needed to upgrade several packages.  So I looked at ~/Downloads and found several .deb files (I'd downloaded these for various reasons)  at some time and of course these are earlier versions than I'd previously upgraded to.  I'm no expert, so the really minor point is: why these 2 commands at the start?

---

### Post by praseodym on 2015-11-25
I assumed that no other DEB files are saved there ;)

The latest driver for manual installation (without dkms!) can be found on the Realtek-HP:

[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false#2](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false#2)

I will frequently update the installation with dkms in this thread:

[http://forum.ubuntuusers.de/topic/lan-karte-funktioniert-nicht/#post-3005217](http://forum.ubuntuusers.de/topic/lan-karte-funktioniert-nicht/#post-3005217)

Alternatively, check [http://packages.ubuntu.com/search?keywords=r8168&searchon=names&suite=all&section=all](http://packages.ubuntu.com/search?keywords=r8168&searchon=names&suite=all&section=all) for updated "r8168-dkms" packages in the repositories.

---

### Post by Biscarri on 2015-11-30
hello praseodym,

I have similar problem with the internet connection of my ubuntu PC 

It is ethernet connected to an apple AirPort Express Wi-Fi station

Here is the list of information answering your questions....

biscarri@biscarri-ews:~$ uname -a
Linux biscarri-ews 3.13.0-45-generic #74-Ubuntu SMP Tue Jan 13 19:36:28 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
biscarri@biscarri-ews:~$ lspci -nnk | grep -iA2 net
biscarri@biscarri-ews:~$ lsmod
Module                  Size  Used by
dm_crypt               23177  0 
intel_rapl             18773  0 
x86_pkg_temp_thermal    14205  0 
intel_powerclamp       14705  0 
snd_hda_codec_hdmi     46368  2 
bnep                   19624  2 
snd_hda_codec_realtek    65580  1 
snd_hda_intel          56531  5 
snd_hda_codec         192906  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm               102099  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30144  1 snd_seq_midi
coretemp               13435  0 
dcdbas                 14928  0 
nfsd                  280289  2 
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
rfcomm                 69160  0 
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
auth_rpcgss            59338  1 nfsd
snd_timer              29482  2 snd_pcm,snd_seq
nfs_acl                12837  1 nfsd
snd                    69322  21 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
nfs                   236726  0 
kvm_intel             143187  0 
kvm                   455835  1 kvm_intel
bluetooth             391136  10 bnep,rfcomm
crct10dif_pclmul       14289  0 
mei_me                 18627  0 
crc32_pclmul           13113  0 
ghash_clmulni_intel    13216  0 
soundcore              12680  1 snd
lockd                  93977  2 nfs,nfsd
parport_pc             32701  0 
mei                    82276  1 mei_me
aesni_intel            55624  0 
aes_x86_64             17131  1 aesni_intel
lrw                    13286  1 aesni_intel
lpc_ich                21080  0 
gf128mul               14951  1 lrw
serio_raw              13462  0 
glue_helper            13990  1 aesni_intel
ablk_helper            13597  1 aesni_intel
cryptd                 20359  3 ghash_clmulni_intel,aesni_intel,ablk_helper
binfmt_misc            17468  1 
ppdev                  17671  0 
sunrpc                289260  6 nfs,nfsd,auth_rpcgss,lockd,nfs_acl
fscache                63988  1 nfs
dm_multipath           22873  0 
lp                     17759  0 
mac_hid                13205  0 
scsi_dh                14882  1 dm_multipath
parport                42348  3 lp,ppdev,parport_pc
btrfs                 836001  0 
libcrc32c              12644  1 btrfs
raid10                 48128  0 
raid456                86666  0 
async_raid6_recov      12984  1 raid456
async_memcpy           12762  1 raid456
async_pq               13365  1 raid456
async_xor              13160  2 async_pq,raid456
async_tx               13509  5 async_pq,raid456,async_xor,async_memcpy,async_raid6_recov
xor                    21411  2 btrfs,async_xor
usb_storage            62209  0 
raid6_pq               97812  3 async_pq,btrfs,async_raid6_recov
raid1                  35530  0 
raid0                  17842  0 
multipath              13145  0 
linear                 12894  0 
dm_mirror              22135  0 
dm_region_hash         20862  1 dm_mirror
dm_log                 18411  2 dm_region_hash,dm_mirror
hid_generic            12548  0 
usbhid                 52659  0 
hid                   106148  2 hid_generic,usbhid
radeon               1522640  3 
ahci                   29915  2 
psmouse               106714  0 
i2c_algo_bit           13413  1 radeon
libahci                32716  1 ahci
ttm                    85150  1 radeon
drm_kms_helper         55071  1 radeon
drm                   303102  5 ttm,drm_kms_helper,radeon
biscarri@biscarri-ews:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback


biscarri@biscarri-ews:~$ cat /etc/resolv.conf
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
biscarri@biscarri-ews:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
biscarri@biscarri-ews:~$ ifconfig -a
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:1517 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1517 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:134643 (134.6 KB)  TX bytes:134643 (134.6 KB)


biscarri@biscarri-ews:~$ 


can you help me?
Thank you very much
Lluis

---

### Post by praseodym on 2015-11-30
Please check without filtering the results:
```

lspci -nnk
```
Is it a BIOS or an (U)EFI?

---

### Post by Biscarri on 2015-11-30
Hi, thank you very much for answering!

I would say it is a BIOS, but I'm not sure. Sorry but I don't know what a (U)EFI is.

lspci -nnk gives...

biscarri@biscarri-ews:~$ lspci -nnk
00:00.0 Host bridge [0600]: Intel Corporation 2nd Generation Core Processor Family DRAM Controller [8086:0100] (rev 09)
	Subsystem: Dell XPS 8300 [1028:04aa]
00:01.0 PCI bridge [0604]: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port [8086:0101] (rev 09)
	Kernel driver in use: pcieport
00:16.0 Communication controller [0780]: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 [8086:1c3a] (rev 04)
	Subsystem: Dell XPS 8300 [1028:04aa]
	Kernel driver in use: mei_me
00:1a.0 USB controller [0c03]: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 [8086:1c2d] (rev 05)
	Subsystem: Dell XPS 8300 [1028:04aa]
	Kernel driver in use: ehci-pci
00:1b.0 Audio device [0403]: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller [8086:1c20] (rev 05)
	Subsystem: Dell XPS 8300 [1028:04aa]
	Kernel driver in use: snd_hda_intel
00:1d.0 USB controller [0c03]: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 [8086:1c26] (rev 05)
	Subsystem: Dell XPS 8300 [1028:04aa]
	Kernel driver in use: ehci-pci
00:1f.0 ISA bridge [0601]: Intel Corporation H67 Express Chipset Family LPC Controller [8086:1c4a] (rev 05)
	Subsystem: Dell XPS 8300 [1028:04aa]
	Kernel driver in use: lpc_ich
00:1f.2 SATA controller [0106]: Intel Corporation 6 Series/C200 Series Chipset Family SATA AHCI Controller [8086:1c02] (rev 05)
	Subsystem: Dell XPS 8300 [1028:04aa]
	Kernel driver in use: ahci
00:1f.3 SMBus [0c05]: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller [8086:1c22] (rev 05)
	Subsystem: Dell XPS 8300 [1028:04aa]
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Juniper XT [Radeon HD 5770] [1002:68b8]
	Subsystem: Advanced Micro Devices, Inc. [AMD/ATI] Device [1002:3000]
	Kernel driver in use: radeon
01:00.1 Audio device [0403]: Advanced Micro Devices, Inc. [AMD/ATI] Juniper HDMI Audio [Radeon HD 5700 Series] [1002:aa58]
	Subsystem: Advanced Micro Devices, Inc. [AMD/ATI] Juniper HDMI Audio [Radeon HD 5700 Series] [1002:aa58]
	Kernel driver in use: snd_hda_intel
biscarri@biscarri-ews:~$

---

### Post by praseodym on 2015-11-30
No card shows up. Please show:
```

[ -d /sys/firmware/efi ] && echo UEFI || echo BIOS
```

---

### Post by Biscarri on 2015-11-30
Bios

---

### Post by praseodym on 2015-11-30
Reset it to default settings here it is F9. Save and close, here F10

---

### Post by Biscarri on 2015-11-30
BIOS reseted, here F9 and F10 as well
no internet connection after reboot
ifconfig gives same output, no reference to eth0....

---

### Post by praseodym on 2015-11-30
Please run the wireless script from the sticky thread and show the outputs.

---

### Post by Biscarri on 2015-12-01
[COLOR=#000000][/COLOR]My PC does not have wireless.

But I've managed to solve the problem; finaly I've found in this thread the solution to the same problem that I had in may 2015, then you helped me with this commands:[COLOR=#000000]

echo -e "nameserver 8.8.8.8\nnameserver 8.8.4.4" | sudo tee /etc/resolv.conf[/COLOR]
[COLOR=#000000]sudo /etc/init.d/networking restart

[/COLOR]I have entered them again and rebooted the PC. Now the internet connection through ethernet cable is OK.

But I still have a question:

I supose that the file resolv.com has been overwritten by the system, because it does not have the nameservers specified by the commands. So I think that maybe the problem will appear again if I shut down the PC. Is there any more definitive thing to do to avoid that problem?

Thank you very much!!

---

### Post by praseodym on 2015-12-01
You can uninstall the package "resolvconf", reboot and may need to repeat those commands.

---

### Post by Biscarri on 2015-12-02
Thank you very much, praseodym!!
Best regards,
Lluís

---

### Post by margazhang on 2015-12-08
The following simply method worked for me:

sudo gedit /etc/NetworkManager/NetworkManager.conf

Change "false" in the file to "true" and then save and reboot. The problem was gone!

---

### Post by Lluis_M._Biscarri on 2016-01-11
thank U [[COLOR=#000000]margazhang[/COLOR]]("http://ubuntuforums.org/member.php?u=637606")

it worked for me as well   :-)

---

### Post by Nick1211 on 2016-03-23
I have the similar problem and my log:

root@ubuntu1204-CoverityAnalizer:~# uname -a
Linux ubuntu1204-CoverityAnalizer 3.11.0-20-generic #35~precise1-Ubuntu SMP Fri May 2 21:32:55 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
###########################
root@ubuntu1204-CoverityAnalizer:~# lspci -nnk | grep -iA2 net
00:19.0 Ethernet controller [0200]: Intel Corporation 82579LM Gigabit Network Connection [8086:1502] (rev 06)
        Subsystem: Dell Device [1028:05d2]
        Kernel driver in use: e1000e
###########################
root@ubuntu1204-CoverityAnalizer:~# lsmod
Module                  Size  Used by
bnep                   24107  2
rfcomm                 74718  0
bluetooth             391726  10 bnep,rfcomm
parport_pc             32866  0
ppdev                  17711  0
snd_hda_codec_hdmi     41773  1
snd_hda_codec_realtek    57219  1
snd_hda_intel          57134  0
snd_hda_codec         194817  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13613  1 snd_hda_codec
snd_pcm               107140  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0
snd_rawmidi            30416  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                66061  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29989  2 snd_pcm,snd_seq
nouveau               979931  1
snd_seq_device         14497  3 snd_seq_midi,snd_rawmidi,snd_seq
ttm                    84837  1 nouveau
drm_kms_helper         53237  1 nouveau
psmouse               104093  0
drm                   306660  3 nouveau,ttm,drm_kms_helper
snd                    73753  11 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_seq_midi,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_algo_bit           13564  1 nouveau
mxm_wmi                13021  1 nouveau
video                  19574  1 nouveau
serio_raw              13413  0
dcdbas                 14936  0
gpio_ich               13526  0
soundcore              12680  1 snd
snd_page_alloc         18798  2 snd_hda_intel,snd_pcm
mei_me                 18418  0
mei                    78537  1 mei_me
wmi                    19256  2 nouveau,mxm_wmi
lpc_ich                21163  0
mac_hid                13253  0
rpcsec_gss_krb5        40513  1
nfsd                  296463  0
binfmt_misc            17508  1
nfsv4                 278861  2
nfs_acl                12883  1 nfsd
auth_rpcgss            55349  4 rpcsec_gss_krb5,nfsd
nfs                   187717  2 nfsv4
fscache                63355  2 nfsv4,nfs
lockd                  95174  2 nfsd,nfs
sunrpc                278885  12 rpcsec_gss_krb5,nfsd,nfsv4,nfs_acl,auth_rpcgss,nfs,lockd
lp                     17799  0
parport                42466  3 parport_pc,ppdev,lp
hid_generic            12548  0
usbhid                 53329  0
hid                   106315  2 hid_generic,usbhid
e1000e                257955  0
ahci                   30063  2
ptp                    18627  1 e1000e
libahci                32118  1 ahci
pps_core               19056  1 ptp


######################
root@ubuntu1204-CoverityAnalizer:~# cat /etc/network/interfaces
# This file describes the network interfaces available on your system # and how to activate them. For more information, see interfaces(5).


# The loopback network interface
auto lo
iface lo inet loopback


# The primary network interfa


#####################
root@ubuntu1204-CoverityAnalizer:~# cat /etc/resolv.conf
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.0.1
####################
root@ubuntu1204-CoverityAnalizer:~# route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         43.2.68.1       0.0.0.0         UG    0      0        0 eth0
43.2.68.0       0.0.0.0         255.255.252.0   U     1      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0


####################
root@ubuntu1204-CoverityAnalizer:~# ifconfig -a
eth0      Link encap:Ethernet  HWaddr f8:b1:56:d0:c0:5a
          inet addr:43.2.68.198  Bcast:43.2.71.255  Mask:255.255.252.0
          inet6 addr: fe80::fab1:56ff:fed0:c05a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:347266 errors:0 dropped:38116 overruns:0 frame:0
          TX packets:158362 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:81199478 (81.1 MB)  TX bytes:40439337 (40.4 MB)
          Interrupt:20 Memory:fb200000-fb220000


lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:211088 errors:0 dropped:0 overruns:0 frame:0
          TX packets:211088 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:251622392 (251.6 MB)  TX bytes:251622392 (251.6 MB)
####################
root@ubuntu1204-CoverityAnalizer:~#  ethtool eth0
Settings for eth0:
        Supported ports: [ TP ]
        Supported link modes:   10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Full
        Supported pause frame use: No
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Full
        Advertised pause frame use: No
        Advertised auto-negotiation: Yes
        Speed: 100Mb/s
        Duplex: Full
        Port: Twisted Pair
        PHYAD: 2
        Transceiver: internal
        Auto-negotiation: on
        MDI-X: on
        Supports Wake-on: pumbg
        Wake-on: g
        Current message level: 0x00000007 (7)
                               drv probe link
        Link detected: yes

Who can support it ??

---

### Post by praseodym on 2016-03-25
Add "1500" as mtu value instead of automatic in the profile. Reconnect or reboot

---

### Post by Biscarri on 2016-11-15
Hi,

I come back to this thread because my ubuntu workstation has lost again ethernet connection.

I've tried the solution given by **praseodym**, that worked for me in the past:

```
[SIZE=3]echo -e "nameserver 8.8.8.8\nnameserver 8.8.4.4" | sudo tee /etc/resolv.conf
sudo service network-manager restart[/SIZE]
```

But it does not fix the problem now in my workstation.

I have collected the information asked by **praseodym** in one of his first entries to the thread:

```
[SIZE=3]uname -a
lspci -nnk | grep -iA2 net
lsmod
cat /etc/network/interfaces
cat /etc/resolv.conf
route -n
ifconfig -a[/SIZE]
```

The listings of these commands are contained in the attached **list.txt** file. 

I have included also the listings of the following commands that I've seen in other entries to this and other threads dealing with the same connectivity problem:

```
[SIZE=3]cat /etc/NetworkManager/NetworkManager.conf
cat /etc/udev/rules.d/70-persistent-net.rules[/SIZE]
```

I have read about problems with NetworkManager application. I have tried without succes to change '**managed=true**' by '**managed=false**' in **/etc/NetworkManager/NetworkManager.conf**, and to add in **/etc/network/interfaces** the following lines:

```
[SIZE=3]auto ethX
iface ethX inet dhcp[/SIZE]
```

Please, can you help me?
Thank you very much!

---

### Post by Biscarri on 2016-11-16
Hi,

I've found an indication here ([http://askubuntu.com/questions/394217/my-eth0-has-gone-and-i-dont-have-internet-and-network-connection](http://askubuntu.com/questions/394217/my-eth0-has-gone-and-i-dont-have-internet-and-network-connection)) that has worked and now I have ethernet connection again :D

Simply executing the following command:

```
[SIZE=3]sudo dpkg-reconfigure network-manager[/SIZE]

```

and rebooting the workstation.

Hope this helps!

---

### Post by sherriherb on 2016-11-29
For Praseodym answer Aug. 11, 2014....Do you mean that I get another computer with Ubuntu OS, download these 2 files, pass them over via flashdrive to the computer that has no internet capabilities and run the downloads there? Will that fix the driver problem?

---

