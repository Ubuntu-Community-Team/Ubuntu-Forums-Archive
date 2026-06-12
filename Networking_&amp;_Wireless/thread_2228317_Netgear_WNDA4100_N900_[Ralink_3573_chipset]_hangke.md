---
title: "Netgear WNDA4100 N900 [Ralink 3573 chipset] hang/kernel panic - replaced ASUS N13"
date: 2014-06-06
forum: Networking &amp; Wireless
---

### Post by Andrew F in Australia on 2014-06-06
Running 64-bit Ubuntu 13.10

I gave up on fiddling with a ASUS N13 Wireless USB (the problematic R8169) and bought something with a different chipset. Not a cheap solution ($99) but I got sick of fiddling with the chipset - took up about 16 hours of my time at least. I went into the local computer store and took about 15 wireless adapters off the wall and searched up the chipset used in each inside the store.  14 were R8169 chip - thanks but no thanks, and one ran on the Ralink 3573 chipset that had a successful driver.

The Ralink (now MediaTek) RT3573 drivers hang in 64-bit. Plug the wireless dongle in, and it detects perfectly.  Open any page on the internet and system crash (kernel panic, I believe) occurs - entire system hangs and needs a hard reboot.

Fixed it following a lot of help from past posts:
[http://ubuntuforums.org/showthread.php?t=1942689](http://ubuntuforums.org/showthread.php?t=1942689)
[http://ubuntuforums.org/showthread.php?t=2198866](http://ubuntuforums.org/showthread.php?t=2198866)

aschaeffer has fixed this bug -> downloaded the altered driver from here:
[https://github.com/ashaffer/rt3573sta/archive/master.zip](https://github.com/ashaffer/rt3573sta/archive/master.zip)

Extracted this zip file and navigated in a terminal window to the extracted directory (Terminal window = ctrl+alt+T for those that are new to Linux) and installed using the following commands [yes, I know that I could have just typed sudo su at the start, but the below were the exact commands entered]

sudo make clean
sudo make
sudo make install
sudo su
modprobe rt3573sta
exit

See the blacklist.conf listing below. I don't know if the RT73 drivers were an issue, but as I didn't need them, I blacklisted them to avoid possible conflict based on past hassles with the 8169 chipset

Full details below of installation setup for others having hassles.

I'm no expert by any means but this worked for me - posting so that others might benefit

[am going to upgrade to 14.0 after posting this and recompile to see if there's a hassle there, if not, I'll revert back to 13.10]

Cheers,

AF


```
horace-music@horacemusic-GA-970A-D3:~$ uname -a
Linux horacemusic-GA-970A-D3 3.11.0-23-generic #40-Ubuntu SMP Wed Jun 4 21:05:23 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
horace-music@horacemusic-GA-970A-D3:~$ lsusb
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 058f:6362 Alcor Micro Corp. Flash Card Reader/Writer
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 002: ID 15c2:0034 SoundGraph Inc. 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0846:9012 NetGear, Inc. WNDA4100 802.11abgn 3x3:3 [Ralink RT3573]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
horace-music@horacemusic-GA-970A-D3:~$ iwconfig
ra0       Ralink STA  ESSID:"Good Morning"  Nickname:"RT2870STA"
          Mode:Managed  Frequency=2.437 GHz  Access Point: 08:BD:43:7A:2D:AC   
          Bit Rate=130 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=100/100  Signal level:-58 dBm  Noise level:-70 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

eth1      no wireless extensions.

lo        no wireless extensions.

horace-music@horacemusic-GA-970A-D3:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr f8:1a:67:00:66:f1  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:41 Base address:0xa000 

eth1      Link encap:Ethernet  HWaddr 90:2b:34:a1:db:84  
          inet addr:10.0.1.1  Bcast:10.0.1.255  Mask:255.255.255.0
          inet6 addr: fe80::922b:34ff:fea1:db84/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2134 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3214 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:240333 (240.3 KB)  TX bytes:228918 (228.9 KB)
          Interrupt:42 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:18343 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18343 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:7292522 (7.2 MB)  TX bytes:7292522 (7.2 MB)

ra0       Link encap:Ethernet  HWaddr 44:94:fc:70:c5:1a  
          inet addr:192.168.0.8  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::4694:fcff:fe70:c51a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:168875 errors:0 dropped:1 overruns:0 frame:0
          TX packets:81638 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:96016015 (96.0 MB)  TX bytes:17222458 (17.2 MB)

horace-music@horacemusic-GA-970A-D3:~$ lsmod
Module                  Size  Used by
cfg80211              480503  0 
bnep                   19704  2 
rfcomm                 69130  0 
bluetooth             372041  10 bnep,rfcomm
parport_pc             32701  0 
ppdev                  17671  0 
binfmt_misc            17468  1 
snd_hda_codec_hdmi     41154  1 
kvm                   431746  0 
crct10dif_pclmul       14289  0 
crc32_pclmul           13113  0 
ghash_clmulni_intel    13216  0 
aesni_intel            55624  0 
snd_ice1724           151909  4 
aes_x86_64             17131  1 aesni_intel
lrw                    13286  1 aesni_intel
gf128mul               14951  1 lrw
glue_helper            13990  1 aesni_intel
snd_ak4113             14667  1 snd_ice1724
snd_hda_codec_via      27860  1 
snd_pt2258             13091  1 snd_ice1724
snd_ak4114             14648  1 snd_ice1724
snd_i2c                14147  2 snd_pt2258,snd_ice1724
snd_ice17xx_ak4xxx     13315  1 snd_ice1724
ablk_helper            13597  1 aesni_intel
nouveau               943749  7 
rt3573sta             713075  1 
snd_ak4xxx_adda        18703  2 snd_ice1724,snd_ice17xx_ak4xxx
cryptd                 20359  3 ghash_clmulni_intel,aesni_intel,ablk_helper
rc_imon_pad            12505  0 
mxm_wmi                13021  1 nouveau
snd_hda_intel          52267  10 
snd_ac97_codec        130236  1 snd_ice1724
snd_hda_codec         188738  3 snd_hda_codec_hdmi,snd_hda_codec_via,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
ac97_bus               12730  1 snd_ac97_codec
video                  19318  1 nouveau
snd_pcm               102033  7 snd_ice1724,snd_ac97_codec,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_ak4113,snd_ak4114
ttm                    84169  1 nouveau
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
drm_kms_helper         52710  1 nouveau
snd_seq_midi           13324  0 
drm                   297056  9 ttm,drm_kms_helper,nouveau
imon                   33324  0 
fam15h_power           13119  0 
i2c_algo_bit           13413  1 nouveau
rc_core                27718  3 imon,rc_imon_pad
microcode              23656  0 
sp5100_tco             13979  0 
lp                     17759  0 
serio_raw              13413  0 
joydev                 17377  0 
i2c_piix4              22106  0 
k10temp                13126  0 
mac_hid                13205  0 
edac_core              62291  0 
edac_mce_amd           22617  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30095  2 snd_ice1724,snd_seq_midi
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
parport                42299  3 lp,ppdev,parport_pc
snd_timer              29433  2 snd_pcm,snd_seq
snd                    69141  46 snd_pt2258,snd_ice1724,snd_ac97_codec,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_via,snd_i2c,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_ak4xxx_adda,snd_hda_intel,snd_seq_device,snd_ak4113,snd_ak4114,snd_seq_midi
soundcore              12680  1 snd
wmi                    19070  2 mxm_wmi,nouveau
hid_logitech_dj        18581  0 
pata_acpi              13038  0 
usbhid                 53014  0 
hid                   101762  4 usbhid,hid_logitech_dj
usb_storage            62062  0 
pata_atiixp            13271  0 
ahci                   25819  6 
libahci                32009  1 ahci
r8168                 400910  0 
horace-music@horacemusic-GA-970A-D3:~$ lsb_release -a
LSB Version:    core-2.0-amd64:core-2.0-noarch:core-3.0-amd64:core-3.0-noarch:core-3.1-amd64:core-3.1-noarch:core-3.2-amd64:core-3.2-noarch:core-4.0-amd64:core-4.0-noarch:core-4.1-amd64:core-4.1-noarch:cxx-3.0-amd64:cxx-3.0-noarch:cxx-3.1-amd64:cxx-3.1-noarch:cxx-3.2-amd64:cxx-3.2-noarch:cxx-4.0-amd64:cxx-4.0-noarch:cxx-4.1-amd64:cxx-4.1-noarch:desktop-3.1-amd64:desktop-3.1-noarch:desktop-3.2-amd64:desktop-3.2-noarch:desktop-4.0-amd64:desktop-4.0-noarch:desktop-4.1-amd64:desktop-4.1-noarch:graphics-2.0-amd64:graphics-2.0-noarch:graphics-3.0-amd64:graphics-3.0-noarch:graphics-3.1-amd64:graphics-3.1-noarch:graphics-3.2-amd64:graphics-3.2-noarch:graphics-4.0-amd64:graphics-4.0-noarch:graphics-4.1-amd64:graphics-4.1-noarch:languages-3.2-amd64:languages-3.2-noarch:languages-4.0-amd64:languages-4.0-noarch:languages-4.1-amd64:languages-4.1-noarch:multimedia-3.2-amd64:multimedia-3.2-noarch:multimedia-4.0-amd64:multimedia-4.0-noarch:multimedia-4.1-amd64:multimedia-4.1-noarch:printing-3.2-amd64:printing-3.2-noarch:printing-4.0-amd64:printing-4.0-noarch:printing-4.1-amd64:printing-4.1-noarch:qt4-3.1-amd64:qt4-3.1-noarch:security-4.0-amd64:security-4.0-noarch:security-4.1-amd64:security-4.1-noarch
Distributor ID:    Ubuntu
Description:    Ubuntu 13.10
Release:    13.10
Codename:    saucy


```

change 
/etc/modules/blacklist.conf

to include: ```


# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

#MANUAL BLACKLIST RTL8192 DRIVERS
blacklist rtl8192cu
blacklist rtl8192c_common
blacklist rtlwifi

#MANUAL blacklist R8169 driver so the R8168 loads for the ethernet card
blacklist r8169

#7 June 2014 blacklist the RT73 drivers
blacklist rt73usb
blacklist rt2x00usb
blacklist rt2x00lib


```

contents of the /etc/modules file

```

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.
# Parameters can be specified after the module name.

lp
rtc
#&#8220;r8168&#8243;
r8168
#8192CU
#8192cu
#R8168
rt3573sta


```

---

