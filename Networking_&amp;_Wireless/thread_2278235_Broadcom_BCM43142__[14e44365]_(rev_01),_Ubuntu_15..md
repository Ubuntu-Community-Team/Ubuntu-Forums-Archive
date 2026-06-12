---
title: "Broadcom BCM43142  [14e4:4365] (rev 01), Ubuntu 15.04 No Wifi"
date: 2015-05-14
forum: Networking &amp; Wireless
---

### Post by erick9 on 2015-05-14
Hello,

I can't connect to wifi networks, I see the message: Wi-fi is disabled by hardware switch. (But my laptop has no physical wifi switch)

I tried to follow some of your guides but I was unsucessful.

Lspci:
```

06:00.0 Network controller [0280]: Broadcom Corporation BCM43142 802.11b/g/n [14e4:4365] (rev 01)
        Subsystem: Dell Wireless 1704 802.11n + BT 4.0 [1028:0016]
        Kernel driver in use: wl

09:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
        Subsystem: Dell Device [1028:0591]
        Kernel driver in use: r8169

```

lsusb:
```

Bus 004 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 004: ID 0bda:58c2 Realtek Semiconductor Corp. 
Bus 003 Device 003: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 003 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

PCMIA section of the wireless-info.txt was empty.

[http://ubuntuforums.org/showthread.php?t=2214110](http://ubuntuforums.org/showthread.php?t=2214110)
This guide refer me to this other link: [http://askubuntu.com/questions/175104/how-do-i-install-bcm43142-wireless-drivers-for-dell-vostro-3460-3560](http://askubuntu.com/questions/175104/how-do-i-install-bcm43142-wireless-drivers-for-dell-vostro-3460-3560)

I followed chili555 steps, but when I entered: 
```

sudo dpkg -i wire*.deb

```

I got the following error: 
```

Building initial module for 3.19.0-16-generic
ERROR (dkms apport): unable to determine source package for wireless-bcm43142-dkms
Error! Bad return status for module build on kernel: 3.19.0-16-generic (x86_64)
Consult /var/lib/dkms/wireless-bcm43142/6.20.55.19/build/make.log for more information.

```

I will appreaciate any help a lot.

---

### Post by chili555 on 2015-05-14
> This guide refer me to this other link: [http://askubuntu.com/questions/17510...stro-3460-3560](http://askubuntu.com/questions/17510...stro-3460-3560)

I followed chili555 steps, but when I entered: In the world of Ubuntu, that's ancient history. The 'special case' I refer to is for 12.04 LTS; you installed the newer 15.04. In addition, if your problem is rfkill, installing an *older *driver won't help. 

Let's see some diagnostics:```
rfkill list all
lsmod
```What brand and model laptop is it?

---

### Post by erick9 on 2015-05-14
DELL inspiron 3421

rfkill list all , gives me no output. with the clean install (before puring bcmwl-kernel-source it gave me output, no it doesn't )

lsmod:
```

Module                  Size  Used by
cpuid                  16384  0 
cfg80211              540672  0 
rtsx_usb_ms            20480  0 
memstick               20480  1 rtsx_usb_ms
uvcvideo               90112  0 
videobuf2_vmalloc      16384  1 uvcvideo
videobuf2_memops       16384  1 videobuf2_vmalloc
snd_hda_codec_hdmi     53248  1 
videobuf2_core         49152  1 uvcvideo
v4l2_common            16384  1 videobuf2_core
videodev              159744  3 uvcvideo,v4l2_common,videobuf2_core
snd_hda_codec_realtek    86016  1 
media                  24576  2 uvcvideo,videodev
snd_hda_codec_generic    69632  1 snd_hda_codec_realtek
intel_rapl             20480  0 
iosf_mbi               16384  1 intel_rapl
snd_hda_intel          32768  3 
snd_hda_controller     32768  1 snd_hda_intel
x86_pkg_temp_thermal    16384  0 
intel_powerclamp       20480  0 
snd_hda_codec         143360  5 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel,snd_hda_controller
snd_hwdep              20480  1 snd_hda_codec
coretemp               16384  0 
snd_pcm               106496  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller
kvm_intel             151552  0 
dell_wmi               16384  0 
kvm                   483328  1 kvm_intel
snd_seq_midi           16384  0 
sparse_keymap          16384  1 dell_wmi
snd_seq_midi_event     16384  1 snd_seq_midi
crct10dif_pclmul       16384  0 
crc32_pclmul           16384  0 
snd_rawmidi            32768  1 snd_seq_midi
ghash_clmulni_intel    16384  0 
snd_seq                69632  2 snd_seq_midi_event,snd_seq_midi
aesni_intel           172032  0 
aes_x86_64             20480  1 aesni_intel
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
i915                 1052672  3 
lrw                    16384  1 aesni_intel
dell_laptop            16384  0 
dcdbas                 16384  1 dell_laptop
drm_kms_helper        122880  1 i915
snd_timer              32768  2 snd_pcm,snd_seq
gf128mul               16384  1 lrw
glue_helper            16384  1 aesni_intel
i8k                    16384  0 
ablk_helper            16384  1 aesni_intel
snd                    90112  17 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
joydev                 20480  0 
cryptd                 20480  3 ghash_clmulni_intel,aesni_intel,ablk_helper
serio_raw              16384  0 
drm                   344064  5 i915,drm_kms_helper
soundcore              16384  2 snd,snd_hda_codec
mei_me                 20480  0 
shpchp                 40960  0 
i2c_algo_bit           16384  1 i915
lpc_ich                24576  0 
mei                    90112  1 mei_me
mac_hid                16384  0 
video                  20480  1 i915
wmi                    20480  1 dell_wmi
parport_pc             32768  0 
ppdev                  20480  0 
lp                     20480  0 
parport                45056  3 lp,ppdev,parport_pc
autofs4                40960  2 
rtsx_usb_sdmmc         28672  0 
rtsx_usb               24576  2 rtsx_usb_sdmmc,rtsx_usb_ms
psmouse               118784  0 
ahci                   36864  2 
r8169                  81920  0 
libahci                32768  1 ahci
mii                    16384  1 r8169

```

edit: here is my history:
```

    1  sudo apt-get update
    2  sudo apt-get dist-upgrade
    3  wget -N -t 5 -T 10 https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info && chmod +x wireless-info && ./wireless-info
    4  ls
    5  less wireless-info
    6  less wireless-info.txt
    7  cat wireless-info.txt
    8  cat wireless-info.txt | grep lspci
    9  less wireless-info.txt
   10  lspci -nn -d 14e4
   11  lspci -nn -d 14e4:
   12  sudo apt-get purge bcmwl-kernel-source
   13  ls
   14  less wireless-info.txt
   15  lspci -nn -d 14e4:
   16  less wireless-info.txt
   17  sudo apt-get purge bcmwl-kernel-source
   18  sudo apt-get autoremove dkms
   19  sudo apt-get purge bcmwl-kernel-source
   20  sudo apt-get update
   21  rfkill unblock all
   22  rfkill list all
   23  sudo rfkill unblock wifi
   24  rfkill list all
   25  ls
   26  cd Downloads/
   27  ls
   28  wget http://semprefidelis.pl/wireless-bcm43142-oneiric-dkms_6.20.55.19~bdcom0602.0400.1000.0400-0somerville1_amd64.deb
   29  sudo apt-get install linux-headers-generic build-essential dkms
   30  ls
   31  sudo dpkg -i wire*.deb
   32  cd .. 
   33  ls
   34  less wireless-info.txt
   35  sudo add-apt-repository ppa:gwendal-lebihan-dev/hexchat-stable
   36  sudo apt-get update
   37  sudo apt-get update hexchat
   38  sudo apt-get install hexchat
   39  hexchat
   40  gedit &
   41  kill %1
   42  gedit
   43  sudo apt-get purge bcmwl-kernel-source
   44  sudo apt-get install firmware-b43-installer
   45  sudo apt-get remove firmware-b43-installer
   46  sudo apt-get remove wireless-bcm43142-dkms
   47  sudo apt-get purge bcmwl-kernel-source
   48  sudo apt-get update
   49  rfkill --list
   50  rfkill list all
   51  history
   52  rfkill list all
   53  lsmod
   54  rfkill list all
   55  history

```

---

### Post by chili555 on 2015-05-14
> sudo apt-get purge bcmwl-kernel-sourceThat's the only viable driver for your device, so I suggest you reinstall it. It can be tricky, so post back if you get stuck.

---

### Post by erick9 on 2015-05-14
purged bcmwl-kernel-source , then installed it.

Wifi option didn't appeared before installing it, now it says that "Wi-Fi is disabled by hardware switch"

rfkill list all:
```

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

```

lsmod
```

Module                  Size  Used by
wl                   6369280  0 
cpuid                  16384  0 
cfg80211              540672  1 wl
rtsx_usb_ms            20480  0 
memstick               20480  1 rtsx_usb_ms
uvcvideo               90112  0 
videobuf2_vmalloc      16384  1 uvcvideo
videobuf2_memops       16384  1 videobuf2_vmalloc
snd_hda_codec_hdmi     53248  1 
videobuf2_core         49152  1 uvcvideo
v4l2_common            16384  1 videobuf2_core
videodev              159744  3 uvcvideo,v4l2_common,videobuf2_core
snd_hda_codec_realtek    86016  1 
media                  24576  2 uvcvideo,videodev
snd_hda_codec_generic    69632  1 snd_hda_codec_realtek
intel_rapl             20480  0 
iosf_mbi               16384  1 intel_rapl
snd_hda_intel          32768  3 
snd_hda_controller     32768  1 snd_hda_intel
x86_pkg_temp_thermal    16384  0 
intel_powerclamp       20480  0 
snd_hda_codec         143360  5 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel,snd_hda_controller
snd_hwdep              20480  1 snd_hda_codec
coretemp               16384  0 
snd_pcm               106496  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller
kvm_intel             151552  0 
dell_wmi               16384  0 
kvm                   483328  1 kvm_intel
snd_seq_midi           16384  0 
sparse_keymap          16384  1 dell_wmi
snd_seq_midi_event     16384  1 snd_seq_midi
crct10dif_pclmul       16384  0 
crc32_pclmul           16384  0 
snd_rawmidi            32768  1 snd_seq_midi
ghash_clmulni_intel    16384  0 
snd_seq                69632  2 snd_seq_midi_event,snd_seq_midi
aesni_intel           172032  0 
aes_x86_64             20480  1 aesni_intel
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
i915                 1052672  3 
lrw                    16384  1 aesni_intel
dell_laptop            16384  0 
dcdbas                 16384  1 dell_laptop
drm_kms_helper        122880  1 i915
snd_timer              32768  2 snd_pcm,snd_seq
gf128mul               16384  1 lrw
glue_helper            16384  1 aesni_intel
i8k                    16384  0 
ablk_helper            16384  1 aesni_intel
snd                    90112  17 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
joydev                 20480  0 
cryptd                 20480  3 ghash_clmulni_intel,aesni_intel,ablk_helper
serio_raw              16384  0 
drm                   344064  5 i915,drm_kms_helper
soundcore              16384  2 snd,snd_hda_codec
mei_me                 20480  0 
shpchp                 40960  0 
i2c_algo_bit           16384  1 i915
lpc_ich                24576  0 
mei                    90112  1 mei_me
mac_hid                16384  0 
video                  20480  1 i915
wmi                    20480  1 dell_wmi
parport_pc             32768  0 
ppdev                  20480  0 
lp                     20480  0 
parport                45056  3 lp,ppdev,parport_pc
autofs4                40960  2 
rtsx_usb_sdmmc         28672  0 
rtsx_usb               24576  2 rtsx_usb_sdmmc,rtsx_usb_ms
psmouse               118784  0 
ahci                   36864  2 
r8169                  81920  0 
libahci                32768  1 ahci
mii                    16384  1 r8169

```

---

### Post by chili555 on 2015-05-14
May I assume you have tried the switch or key combination repeatedly with no effect?

If so, please try:```
sudo modprobe -r dell_laptop
sudo modprobe dell_laptop force_rfkill=Y
```Now try the switch; any improvement?

---

### Post by erick9 on 2015-05-14
With switch do you mean ?
```

rfkill unblock all

```

cause my laptop has no physical switch

I runned 
```

sudo modprobe -r dell_laptop
sudo modprobe dell_laptop force_rfkill=Y

```

those commands gave no output, what do I do next? :S

EDIT
i runned 
```

rfkill unblock wifi
rfkill list all

```

output:
```

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
2: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
3: dell-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: yes



```

---

### Post by chili555 on 2015-05-14
> cause my laptop has no physical switchNo??

[ATTACH=CONFIG]261977[/ATTACH]

---

### Post by erick9 on 2015-05-14
I don't know what is greater, my desire to hug you or my desire to punch myself xD.

Thanks for your time and help, it is working now.

---

### Post by chili555 on 2015-05-14
No punches, please. I am glad it's working by whatever means. Have fun!

---

### Post by RV58 on 2015-09-11
> **chili555 said:**
> No??

[ATTACH=CONFIG]261977[/ATTACH]

Sir,

The image that you posted is not very clear. Is it to press Fn+F3 ?

On my Dell, core i3, Inspiron 15 : The Fn+any function key does not turn
ON my wireless.

The 'rfkill list all' command still shows:
1: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

Is there a problem with my BCM43142 ?

Thank you
RV58

---

### Post by RV58 on 2015-09-11
Sir,

The image that you posted is not very clear. Is it to press Fn+F3 ?

On my Dell, core i3, Inspiron 15 : The Fn+any function key does not turn
ON my wireless.

The 'rfkill list all' command still shows:
1: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

Is there a problem with my BCM43142 ?

Thank you
RV58

---

### Post by chili555 on 2015-09-11
Do you have the exact same make and model laptop as the original poster? What is it?

---

### Post by RV58 on 2015-09-12
Sir (Chili555),
I cannot get WiFi to come ON.
The image that you sent 3421_wireless.png is not very clear.
Is it Fn+F1 (or F2,F3 etc) ? It does not work for my Dell, Inspirion 15, i3.
rfkill list all:
2: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
Is there a problem with my BCM43142 ?
ThankYou

---

### Post by chili555 on 2015-09-12
> It does not work for my Dell, Inspirion 15, i3.Is it an Inspiron 15 3520 or 3521 or 3541 or ...some other?

If it is a 3520, it is probably just F2. That is, _without_ the Fn key. Please try it and run again:```
rfkill list all
```Is there any change?

---

### Post by wiseprt on 2015-10-04
Hello there,


I have problems with wifi in my sony vaio laptop after upgraded to 15.04. As i noticed have the BCM43142


Here is my output for rfkill list all:


```

0: sony-wifi: Wireless LAN 
Soft blocked: no 
Hard blocked: no


1: sony-bluetooth: Bluetooth 
Soft blocked: yes 
Hard blocked: no


2: nfc0: NFC 
Soft blocked: no 
Hard blocked: no



```


and the output for lsmod:


```

Module Size Used by
bbswitch 16384 0 
binfmt_misc 20480 1 
microread_mei 16384 0 
microread 16384 1 microread_mei
mei_phy 16384 1 microread_mei
crc_ccitt 16384 1 microread
hci 45056 2 mei_phy,microread
nfc 102400 2 hci,microread
intel_rapl 20480 0 
uvcvideo 94208 0 
iosf_mbi 16384 1 intel_rapl
videobuf2_vmalloc 16384 1 uvcvideo
videobuf2_memops 16384 1 videobuf2_vmalloc
videobuf2_core 53248 1 uvcvideo
v4l2_common 16384 1 videobuf2_core
videodev 163840 3 uvcvideo,v4l2_common,videobuf2_core
x86_pkg_temp_thermal 16384 0 
media 24576 2 uvcvideo,videodev
intel_powerclamp 20480 0 
snd_hda_codec_hdmi 53248 1 
snd_hda_codec_realtek 81920 1 
nvidia 10563584 35 
snd_hda_codec_generic 73728 1 snd_hda_codec_realtek
coretemp 16384 0 
hid_logitech_hidpp 20480 0 
snd_hda_intel 32768 3 
snd_hda_controller 36864 1 snd_hda_intel
kvm_intel 159744 0 
kvm 512000 1 kvm_intel
snd_hda_codec 147456 5 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel,snd_hda_controller
i915 1126400 3 
crct10dif_pclmul 16384 0 
snd_hwdep 16384 1 snd_hda_codec
crc32_pclmul 16384 0 
ghash_clmulni_intel 16384 0 
aesni_intel 172032 0 
snd_pcm 110592 4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller
snd_seq_midi 16384 0 
aes_x86_64 20480 1 aesni_intel
snd_seq_midi_event 16384 1 snd_seq_midi
lrw 16384 1 aesni_intel
snd_rawmidi 32768 1 snd_seq_midi
gf128mul 16384 1 lrw
glue_helper 16384 1 aesni_intel
ablk_helper 16384 1 aesni_intel
drm_kms_helper 126976 1 i915
drm 352256 7 i915,drm_kms_helper,nvidia
snd_seq 69632 2 snd_seq_midi_event,snd_seq_midi
rtsx_pci_ms 20480 0 
memstick 20480 1 rtsx_pci_ms
cryptd 24576 3 ghash_clmulni_intel,aesni_intel,ablk_helper
snd_seq_device 16384 3 snd_seq,snd_rawmidi,snd_seq_midi
joydev 20480 0 
snd_timer 32768 2 snd_pcm,snd_seq
snd 86016 17 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
serio_raw 16384 0 
soundcore 16384 2 snd,snd_hda_codec
shpchp 40960 0 
mei_me 20480 0 
sony_laptop 61440 0 
mei 90112 3 mei_phy,mei_me,microread_mei
i2c_algo_bit 16384 1 i915
video 28672 1 i915
lpc_ich 24576 0 
mac_hid 16384 0 
b43 434176 0 
bcma 61440 1 b43
mac80211 774144 1 b43
cfg80211 581632 2 b43,mac80211
ssb 69632 1 b43
parport_pc 36864 0 
ppdev 20480 0 
lp 20480 0 
parport 45056 3 lp,ppdev,parport_pc
autofs4 40960 2 
hid_logitech_dj 20480 0 
usbhid 53248 0 
hid 114688 3 usbhid,hid_logitech_dj,hid_logitech_hidpp
rtsx_pci_sdmmc 24576 0 
psmouse 126976 0 
ahci 36864 1 
libahci 32768 1 ahci
r8169 90112 0 
rtsx_pci 53248 2 rtsx_pci_ms,rtsx_pci_sdmmc
mii 16384 1 r8169





```


and from the ifconfig (as you can see there is no wlan0). 


```

eth0 Link encap:Ethernet HWaddr 30:f9:ed:ab:dd:bb 
inet addr:192.168.1.55 Bcast:192.168.1.255 Mask:255.255.255.0
inet6 addr: 2a02:2149:8826:7400:65da:838e:1953:26e/64 Scope:Global
inet6 addr: fe80::32f9:edff:feab:ddbb/64 Scope:Link
inet6 addr: 2a02:2149:8826:7400:32f9:edff:feab:ddbb/64 Scope:Global
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:10491 errors:0 dropped:0 overruns:0 frame:0
TX packets:10004 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:9496654 (9.4 MB) TX bytes:2022268 (2.0 MB)




lo Link encap:Local Loopback 
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:65536 Metric:1
RX packets:529 errors:0 dropped:0 overruns:0 frame:0
TX packets:529 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0 
RX bytes:113072 (113.0 KB) TX bytes:113072 (113.0 KB)





```


and a last one, when i try with "sudo modprobe wl" got this


```
modprobe: FATAL: Module wl not found.

```


Please help me asap cause is important to have wifi connection back.


Best Regards

---

### Post by jeremy31 on 2015-10-04
You likely have the old version of bcmwl-kernel-source
```
sudo apt-get purge bcmwl-kernel-source
sudo apt-get install bcmwl-kernel-source
```

Reboot

---

### Post by wiseprt on 2015-10-04
Hello, thanks for quick reply.

Unfortunately nothing change.

Here is what i got with these sudo...

```

Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  bcmwl-kernel-source*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 8038 kB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 243011 files and directories currently installed.)
Removing bcmwl-kernel-source (6.30.223.248+bdcom-0ubuntu2) ...
Removing all DKMS Modules
Done.
update-initramfs: deferring update (trigger activated)
Purging configuration files for bcmwl-kernel-source (6.30.223.248+bdcom-0ubuntu2) ...
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools (0.103ubuntu15) ...
update-initramfs: Generating /boot/initrd.img-4.0.3-040003-generic
N: Ignoring file 'canonical_partner.list&#8217;' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'canonical_partner.list&#8217;' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension




user@laptop:~$ sudo apt-get install bcmwl-kernel-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  bcmwl-kernel-source
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/1509 kB of archives.
After this operation, 8038 kB of additional disk space will be used.
Selecting previously unselected package bcmwl-kernel-source.
(Reading database ... 242937 files and directories currently installed.)
Preparing to unpack .../bcmwl-kernel-source_6.30.223.248+bdcom-0ubuntu2_amd64.deb ...
Unpacking bcmwl-kernel-source (6.30.223.248+bdcom-0ubuntu2) ...
Setting up bcmwl-kernel-source (6.30.223.248+bdcom-0ubuntu2) ...
Loading new bcmwl-6.30.223.248+bdcom DKMS files...
First Installation: checking all kernels...
Building only for 4.0.3-040003-generic
Building for architecture x86_64
Building initial module for 4.0.3-040003-generic
ERROR (dkms apport): kernel package linux-headers-4.0.3-040003-generic is not supported
Error! Bad return status for module build on kernel: 4.0.3-040003-generic (x86_64)
Consult /var/lib/dkms/bcmwl/6.30.223.248+bdcom/build/make.log for more information.
modprobe: FATAL: Module wl not found.
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools (0.103ubuntu15) ...
update-initramfs: Generating /boot/initrd.img-4.0.3-040003-generic
N: Ignoring file 'canonical_partner.list&#8217;' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'canonical_partner.list&#8217;' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension



```

---

### Post by jeremy31 on 2015-10-04
15.04 now comes with a 4.0.3 kernel?

You could try ```
[COLOR=#000000][FONT=monospace]sudo add-apt-repository ppa:longsleep/bcmwl
sudo apt-get update
sudo apt-get install bcmwl
```[/FONT][/COLOR]

---

### Post by wiseprt on 2015-10-04
now, after the last "sudo apt-get install bcmwl" got this: 
```

 sudo apt-get install bcmwl
Reading package lists... Done
Building dependency tree       
Reading state information... Done
N: Ignoring file 'canonical_partner.list&#8217;' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'canonical_partner.list&#8217;' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
E: Unable to locate package bcmwl



```

---

### Post by jeremy31 on 2015-10-04
My mistake ```
sudo apt-get install bcmwl-kernel-source
```

Hopefully it shows it downloading from launchpad, Reboot

---

### Post by wiseprt on 2015-10-04
Great news! Working now... thanks a lot @jeremy31.
you save my day!

---

### Post by emiliano9 on 2015-11-23
Hello. I have the same problem, my ladtop is a HP Stream Notebook - 14-z050na (ENERGY STAR). I'm new in ubuntu so any further information you need to help me just ask me please. I'm sure that the computer has not a physical switch. Thanks in advance.

---

### Post by chili555 on 2015-11-23
> **emiliano9 said:**
> Hello. I have the same problem, my ladtop is a HP Stream Notebook - 14-z050na (ENERGY STAR). I'm new in ubuntu so any further information you need to help me just ask me please. I'm sure that the computer has not a physical switch. Thanks in advance.Which 'same' problem? There are 3-4 different laptops here in this thread. Some had the wrong driver, some had no driver, some couldn't find the wireless button (which I'm pretty confident yours _does_ have), etc.

Let's start here: [http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)

---

### Post by emiliano9 on 2015-11-29
Hello again. I had several problems to wire the computer to ethernet but now it's working. So I followed the indications in the link you shared, I downloaded the correspondent driver for Ubuntu 15.04 and the Broadcom Corporation BCM43142 802.11b/g/n [14e4:4365] (rev 01) wireless card and now the Wi-Fi connection is working perfectly. Thank you for the prompt and effective help @chili555.

---

