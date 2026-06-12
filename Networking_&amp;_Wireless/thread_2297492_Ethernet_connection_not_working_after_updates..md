---
title: "Ethernet connection not working after updates."
date: 2015-10-04
forum: Networking &amp; Wireless
---

### Post by nigro.orlando on 2015-10-04
Hi,
I did some updates yesterday and now my wired connection is not working properly. I believe it's because of the updates because it changed name, before was "wired connection 1" and now is "authomatic ethernet". 
When I plug the ethernet cable, the network manager loads and never connects. I can use the internet for some short moments but it's very bad connection. The wireless works fine. 

I looked online and I found that this would have helped:

```
sudo apt-get install r8168-dkms
```
[FONT=arial]But it didn't. I hope that I didn't mess something up. I have xubuntu 15.04[/FONT]

---

### Post by praseodym on 2015-10-04
Lets check
```

lsmod
ifconfig -a
cat /etc/resolv.conf
```

---

### Post by nigro.orlando on 2015-10-04
```
orlando@orlando-Lenovo-Y50-70:~$ lsmod
Module                  Size  Used by
ctr                    16384  1 
ccm                    20480  1 
binfmt_misc            20480  1 
rfcomm                 69632  12 
bnep                   20480  2 
nls_iso8859_1          16384  1 
snd_hda_codec_realtek    86016  1 
snd_hda_codec_hdmi     53248  1 
snd_hda_codec_generic    69632  1 snd_hda_codec_realtek
arc4                   16384  2 
uvcvideo               90112  0 
videobuf2_vmalloc      16384  1 uvcvideo
videobuf2_memops       16384  1 videobuf2_vmalloc
videobuf2_core         49152  1 uvcvideo
v4l2_common            16384  1 videobuf2_core
videodev              159744  3 uvcvideo,v4l2_common,videobuf2_core
btusb                  40960  0 
bluetooth             491520  22 bnep,btusb,rfcomm
media                  24576  2 uvcvideo,videodev
snd_hda_intel          36864  6 snd_hda_codec_hdmi
snd_hda_controller     32768  1 snd_hda_intel
snd_hda_codec         143360  5 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel,snd_hda_controller
snd_hwdep              20480  1 snd_hda_codec
snd_pcm               106496  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller
iwlmvm                278528  0 
snd_seq_midi           16384  0 
snd_seq_midi_event     16384  1 snd_seq_midi
intel_rapl             20480  0 
iosf_mbi               16384  1 intel_rapl
x86_pkg_temp_thermal    16384  0 
mac80211              724992  1 iwlmvm
intel_powerclamp       20480  0 
nouveau              1400832  1 
coretemp               16384  0 
snd_rawmidi            32768  1 snd_seq_midi
kvm                   483328  0 
i915                 1060864  4 
snd_seq                69632  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
crct10dif_pclmul       16384  0 
snd_timer              32768  2 snd_pcm,snd_seq
crc32_pclmul           16384  0 
iwlwifi               196608  1 iwlmvm
mxm_wmi                16384  1 nouveau
ghash_clmulni_intel    16384  0 
snd                    90112  21 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
ttm                    98304  1 nouveau
aesni_intel           172032  3 
rtsx_pci_ms            20480  0 
drm_kms_helper        131072  2 i915,nouveau
aes_x86_64             20480  1 aesni_intel
lrw                    16384  1 aesni_intel
cfg80211              540672  3 iwlwifi,mac80211,iwlmvm
memstick               20480  1 rtsx_pci_ms
gf128mul               16384  1 lrw
glue_helper            16384  1 aesni_intel
drm                   348160  8 ttm,i915,drm_kms_helper,nouveau
ablk_helper            16384  1 aesni_intel
cryptd                 20480  3 ghash_clmulni_intel,aesni_intel,ablk_helper
soundcore              16384  2 snd,snd_hda_codec
joydev                 20480  0 
i2c_algo_bit           16384  2 i915,nouveau
shpchp                 40960  0 
ie31200_edac           16384  0 
mei_me                 20480  0 
serio_raw              16384  0 
edac_core              53248  1 ie31200_edac
lpc_ich                24576  0 
mei                    90112  1 mei_me
ideapad_laptop         20480  0 
sparse_keymap          16384  1 ideapad_laptop
wmi                    20480  2 mxm_wmi,nouveau
video                  20480  2 i915,nouveau
mac_hid                16384  0 
parport_pc             32768  0 
ppdev                  20480  0 
lp                     20480  0 
parport                45056  3 lp,ppdev,parport_pc
autofs4                40960  2 
hid_generic            16384  0 
usbhid                 53248  0 
hid                   110592  2 hid_generic,usbhid
rtsx_pci_sdmmc         24576  0 
psmouse               118784  0 
ahci                   36864  3 
libahci                32768  1 ahci
rtsx_pci               49152  2 rtsx_pci_ms,rtsx_pci_sdmmc
r8168                 421888  0 

```

```
orlando@orlando-Lenovo-Y50-70:~$ ifconfig -a
eth0      Link encap:Ethernet  IndirizzoHW f8:a9:63:3d:48:60  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:159 errors:0 dropped:0 overruns:0 carrier:0
          collisioni:0 txqueuelen:1000 
          Byte RX:0 (0.0 B)  Byte TX:31021 (31.0 KB)
          Interrupt:28 Indirizzo base:0x6000 

lo        Link encap:Loopback locale  
          indirizzo inet:127.0.0.1  Maschera:255.0.0.0
          indirizzo inet6: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:12130 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12130 errors:0 dropped:0 overruns:0 carrier:0
          collisioni:0 txqueuelen:0 
          Byte RX:847218 (847.2 KB)  Byte TX:847218 (847.2 KB)

wlan0     Link encap:Ethernet  IndirizzoHW a0:88:69:77:23:ba  
          indirizzo inet:192.168.0.103  Bcast:192.168.0.255  Maschera:255.255.255.0
          indirizzo inet6: fe80::a288:69ff:fe77:23ba/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1188 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1204 errors:0 dropped:0 overruns:0 carrier:0
          collisioni:0 txqueuelen:1000 
          Byte RX:628950 (628.9 KB)  Byte TX:200918 (200.9 KB)


```

```
orlando@orlando-Lenovo-Y50-70:~$ cat /etc/resolv.conf
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.1.1


```

I think that this has something to do with the homeplug that I uses because when I take the ethernet cable directly from the router it works. But the homeplug that comes from other wall sockets doesn't work.
Still, it's weird that this happened just suddenly

---

### Post by praseodym on 2015-10-04
Which ubuntu version is it? Try the driver version 40:
```

sudo apt-get remove --purge r8168-dkms
sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms
wget https://media-cdn.ubuntu-de.org/forum/attachments/28/33/3005217-r8168-dkms-8.040.00.tar.gz
sudo tar xvf 3005217-r8168-dkms-8.040.00.tar.gz -C /usr/src
sudo dkms add -m r8168-dkms -v 8.040.00
sudo dkms build -m r8168-dkms -v 8.040.00
sudo dkms install -m r8168-dkms -v 8.040.00
sudo depmod -a
sudo update-initramfs -u
```Reboot

---

### Post by Inti_Amaru on 2015-10-05
Hi, I have the same problem. After updating to Ubuntu 14.04, WiFi & Ethernet connections stop. By installing modprobe b43, WiFi works now, but on Ethernet (cable connected through USB 2.0 Fast Ethernet Adapter JP 208B No. 88772A) only google & gmail work. Other sites no.

Code:
ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:2809 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2809 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:247766 (247.7 KB)  TX bytes:247766 (247.7 KB)


wlan0     Link encap:Ethernet  HWaddr c4:85:08:22:77:7f  
          inet addr:192.168.1.5  Bcast:192.168.1.63  Mask:255.255.255.192
          inet6 addr: fd14:b968:28a2:d500:c685:8ff:fe22:777f/64 Scope:Global
          inet6 addr: fe80::c685:8ff:fe22:777f/64 Scope:Link
          inet6 addr: fd14:b968:28a2:d500:ad5b:8d42:9f01:912f/64 Scope:Global
          inet6 addr: 2800:370:4f:c530:c685:8ff:fe22:777f/64 Scope:Global
          inet6 addr: 2800:370:4f:c530:ad5b:8d42:9f01:912f/64 Scope:Global
          inet6 addr: 2800:370:4f:c530::4/128 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:18935 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15747 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:11891994 (11.8 MB)  TX bytes:2414329 (2.4 MB)

---

### Post by nigro.orlando on 2015-10-06
@praseodym I have ubuntu 15.04

---

### Post by nigro.orlando on 2015-10-06
I'm starting to think that the problem is the hardware, and I means the homeplugs. My partners computer also can't connect with the ethernet-cable that goes through the homeplug. She has Ubuntu 14.04. Either is that or an update from Ubuntu that messed up also hers version. Or it could be the router... no idea.

---

### Post by praseodym on 2015-10-06
Tried version 40?

---

