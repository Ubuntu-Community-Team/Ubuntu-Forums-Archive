---
title: "Wireless connectivity disappeared. can't bring it back"
date: 2014-04-28
forum: Networking &amp; Wireless
---

### Post by Dada_Maheshvaranan on 2014-04-28
I have Ubuntu 14.04 LTS (64-bit), which I installed on April 19, and I  daily checked "Software Updater". However on April 24 my  laptop no  longer sees the wireless network (or the neighbors'  wireless networks), nor does it even recognize the ethernet cable if I  plug that in. "Network Connections" clearly shows the our wireless and  the  correct password for it, but the laptop is not "seeing" it.


Below I paste the output of lspci and ifconfig:

lspci
00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Root Complex
00:01.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Kabini [Radeon HD 8210]
00:01.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Device 9840
00:02.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Function 0
00:02.3 PCI bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Functions 5:1
00:02.4 PCI bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Functions 5:1
00:10.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB XHCI Controller (rev 01)
00:11.0 SATA controller: Advanced Micro Devices, Inc. [AMD] FCH SATA Controller [AHCI mode]
00:12.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB OHCI Controller (rev 39)
00:12.2 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB EHCI Controller (rev 39)
00:13.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB OHCI Controller (rev 39)
00:13.2 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB EHCI Controller (rev 39)
00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD] FCH SMBus Controller (rev 3a)
00:14.2 Audio device: Advanced Micro Devices, Inc. [AMD] FCH Azalia Controller (rev 02)
00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD] FCH LPC Bridge (rev 11)
00:14.7 SD Host controller: Advanced Micro Devices, Inc. [AMD] FCH SD Flash Controller (rev 01)
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Function 0
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Function 1
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Function 2
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Function 3
00:18.4 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Function 4
00:18.5 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Function 5
01:00.0 Network controller: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter (rev 01)
02:00.0 Ethernet controller: Qualcomm Atheros QCA8171 Gigabit Ethernet (rev 10)
dada@dada-Aspire-V5-123:~$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:482 errors:0 dropped:0 overruns:0 frame:0
          TX packets:482 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:47435 (47.4 KB)  TX bytes:47435 (47.4 KB)

---

### Post by nrd2 on 2014-04-29
Hi there!

Have you tried searching in the forums for similar problems?
This one is quite recent: [http://ubuntuforums.org/showthread.php?t=2220454](http://ubuntuforums.org/showthread.php?t=2220454)
maybe the solution works out for you too.

---

### Post by Dada_Maheshvaranan on 2014-04-29
Thanks, but tried these solutions, but neither the ethernet cable nor wireless are working still.


> **nrd2 said:**
> Hi there!

Have you tried searching in the forums for similar problems?
This one is quite recent: [http://ubuntuforums.org/showthread.php?t=2220454](http://ubuntuforums.org/showthread.php?t=2220454)
maybe the solution works out for you too.

---

### Post by nrd2 on 2014-04-30
> **Dada_Maheshvaranan said:**
> Thanks, but tried these solutions, but neither the ethernet cable nor wireless are working still.

hum... just to make sure, you do have your wireless on, right? I mean, a physical switch on your laptop?
Can you also paste here the output of 'lsmod'?

---

### Post by Dada_Maheshvaranan on 2014-05-01
Thanks for your help. No physical wireless switch on the laptop.

dada@dada-Aspire-V5-123:~$ lsmod
Module                  Size  Used by
nls_iso8859_1          12713  0 
joydev                 17381  0 
rfcomm                 69160  8 
bnep                   19624  2 
hid_generic            12548  0 
acer_wmi               32522  0 
sparse_keymap          13948  1 acer_wmi
snd_hda_codec_realtek    61438  1 
snd_hda_codec_hdmi     46207  1 
amd_freq_sensitivity    12589  0 
kvm                   451511  0 
crct10dif_pclmul       14289  0 
crc32_pclmul           13113  0 
ghash_clmulni_intel    13259  0 
aesni_intel            55624  0 
aes_x86_64             17131  1 aesni_intel
lrw                    13286  1 aesni_intel
gf128mul               14951  1 lrw
glue_helper            13990  1 aesni_intel
ablk_helper            13597  1 aesni_intel
cryptd                 20359  3 ghash_clmulni_intel,aesni_intel,ablk_helper
usbhid                 52616  0 
arc4                   12608  2 
psmouse               102222  0 
serio_raw              13462  0 
ath9k                 164164  0 
uvcvideo               80885  0 
usb_storage            62209  0 
hid                   106148  2 hid_generic,usbhid
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_hda_intel          52355  5 
ath9k_common           13551  1 ath9k
videobuf2_vmalloc      13216  1 uvcvideo
snd_rawmidi            30144  1 snd_seq_midi
videobuf2_memops       13362  1 videobuf2_vmalloc
ath9k_hw              453856  2 ath9k_common,ath9k
videobuf2_core         40664  1 uvcvideo
k10temp                13126  0 
snd_hda_codec         192906  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
fam15h_power           13119  0 
edac_core              62291  0 
videodev              134688  2 uvcvideo,videobuf2_core
ath                    28698  3 ath9k_common,ath9k,ath9k_hw
snd_pcm               102099  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
edac_mce_amd           22617  0 
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
btusb                  32412  0 
mac80211              626489  1 ath9k
bluetooth             395423  22 bnep,btusb,rfcomm
i2c_piix4              22155  0 
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29482  2 snd_pcm,snd_seq
snd                    69238  21 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
radeon               1514165  4 
cfg80211              484040  3 ath,ath9k,mac80211
ttm                    85115  1 radeon
drm_kms_helper         52758  1 radeon
drm                   302817  6 ttm,drm_kms_helper,radeon
soundcore              12680  1 snd
i2c_algo_bit           13413  1 radeon
wmi                    19177  1 acer_wmi
parport_pc             32701  0 
ppdev                  17671  0 
lp                     17759  0 
video                  19476  1 acer_wmi
parport                42348  3 lp,ppdev,parport_pc
mac_hid                13205  0 
sdhci_pci              23172  0 
sdhci                  43015  1 sdhci_pci
ahci                   25819  2 
libahci                32168  1 ahci
alx                    32452  0 
mdio                   13807  1 alx

---

### Post by nrd2 on 2014-05-02
Strange, everything seems ok.
If you boot with the LiveCD again, do you have connectivity?

---

### Post by Dada_Maheshvaranan on 2014-05-02
I rebooted with the LiveCD, and even before choosing "Try Ubuntu" I was informed there was a wireless network to connect to, and it worked perfectly. I shut down, restarted from the harddrive, and, alas, no wireless. :-(  Is the only solution then reinstalling Ubuntu (several hours of work copying over all my files again)?

---

### Post by drink1297 on 2014-05-02
Try booting into your bios, choose restore defaults and then boot into the OS...that worked when my wireless went MIA.

---

### Post by nrd2 on 2014-05-02
> **Dada_Maheshvaranan said:**
> I rebooted with the LiveCD, and even before choosing "Try Ubuntu" I was informed there was a wireless network to connect to, and it worked perfectly. I shut down, restarted from the harddrive, and, alas, no wireless. :-(  Is the only solution then reinstalling Ubuntu (several hours of work copying over all my files again)?

can you boot with the livecd and post here the lspci and lsmod output, maybe we can spot some differences and understand what is missing... reinstalling is a pain :/

---

### Post by Dada_Maheshvaranan on 2014-05-02
> **nrd2 said:**
> can you boot with the livecd and post here the lspci and lsmod output, maybe we can spot some differences and understand what is missing... reinstalling is a pain :/

Thanks. I booted with the Ubuntu StartupCD, chose Try Ubuntu, opened terminal, and here are the outputs:

ubuntu@ubuntu:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Root Complex
00:01.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Kabini [Radeon HD 8210]
00:01.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Device 9840
00:02.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Function 0
00:02.3 PCI bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Functions 5:1
00:02.4 PCI bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Functions 5:1
00:10.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB XHCI Controller (rev 01)
00:11.0 SATA controller: Advanced Micro Devices, Inc. [AMD] FCH SATA Controller [AHCI mode]
00:12.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB OHCI Controller (rev 39)
00:12.2 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB EHCI Controller (rev 39)
00:13.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB OHCI Controller (rev 39)
00:13.2 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB EHCI Controller (rev 39)
00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD] FCH SMBus Controller (rev 3a)
00:14.2 Audio device: Advanced Micro Devices, Inc. [AMD] FCH Azalia Controller (rev 02)
00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD] FCH LPC Bridge (rev 11)
00:14.7 SD Host controller: Advanced Micro Devices, Inc. [AMD] FCH SD Flash Controller (rev 01)
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Function 0
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Function 1
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Function 2
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Function 3
00:18.4 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Function 4
00:18.5 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Function 5
01:00.0 Network controller: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter (rev 01)
02:00.0 Ethernet controller: Qualcomm Atheros QCA8171 Gigabit Ethernet (rev 10)
ubuntu@ubuntu:~$ lsmod
Module                  Size  Used by
ctr                    13049  1 
ccm                    17773  1 
amd_freq_sensitivity    12589  0 
arc4                   12608  2 
kvm                   451511  0 
ath9k                 164164  0 
dm_crypt               23177  0 
ath9k_common           13551  1 ath9k
crct10dif_pclmul       14289  0 
crc32_pclmul           13113  0 
ath9k_hw              453856  2 ath9k_common,ath9k
acer_wmi               32522  0 
uvcvideo               80885  0 
ghash_clmulni_intel    13259  0 
joydev                 17381  0 
videobuf2_vmalloc      13216  1 uvcvideo
aesni_intel            55624  2 
sparse_keymap          13948  1 acer_wmi
snd_hda_codec_realtek    61438  1 
videobuf2_memops       13362  1 videobuf2_vmalloc
aes_x86_64             17131  1 aesni_intel
lrw                    13286  1 aesni_intel
videobuf2_core         40664  1 uvcvideo
dm_multipath           22873  0 
snd_hda_codec_hdmi     46207  1 
videodev              134688  2 uvcvideo,videobuf2_core
gf128mul               14951  1 lrw
ath                    28698  3 ath9k_common,ath9k,ath9k_hw
snd_hda_intel          52355  5 
glue_helper            13990  1 aesni_intel
scsi_dh                14882  1 dm_multipath
mac80211              626489  1 ath9k
ablk_helper            13597  1 aesni_intel
snd_hda_codec         192906  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
psmouse               102222  0 
cryptd                 20359  3 ghash_clmulni_intel,aesni_intel,ablk_helper
snd_hwdep              13602  1 snd_hda_codec
snd_pcm               102099  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
serio_raw              13462  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30144  1 snd_seq_midi
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
cfg80211              484040  3 ath,ath9k,mac80211
btusb                  32412  0 
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
fam15h_power           13119  0 
edac_core              62291  0 
snd_timer              29482  2 snd_pcm,snd_seq
k10temp                13126  0 
edac_mce_amd           22617  0 
i2c_piix4              22155  0 
bnep                   19624  2 
snd                    69238  21 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
rfcomm                 69160  8 
soundcore              12680  1 snd
bluetooth             395423  22 bnep,btusb,rfcomm
mac_hid                13205  0 
parport_pc             32701  0 
ppdev                  17671  0 
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
squashfs               48362  1 
overlayfs              27916  1 
nls_utf8               12557  1 
isofs                  39835  1 
dm_mirror              22135  0 
dm_region_hash         20862  1 dm_mirror
dm_log                 18411  2 dm_region_hash,dm_mirror
hid_generic            12548  0 
usbhid                 52616  0 
hid                   106148  2 hid_generic,usbhid
usb_storage            62209  1 
sdhci_pci              23172  0 
radeon               1514165  3 
sdhci                  43015  1 sdhci_pci
ahci                   25819  1 
libahci                32168  1 ahci
alx                    32452  0 
mdio                   13807  1 alx
wmi                    19177  1 acer_wmi
i2c_algo_bit           13413  1 radeon
ttm                    85115  1 radeon
drm_kms_helper         52758  1 radeon
drm                   302817  5 ttm,drm_kms_helper,radeon
video                  19476  1 acer_wmi

---

### Post by Dada_Maheshvaranan on 2014-05-02
We've got a problem, Houston.

After posting the above and restoring default settings in my bios, the laptop is no longer able to boot up on its own:

"Default Boot Device Missing or Boot Failed.
Insert Recovery Media and Hit any key
Then Select 'Boot Manager' to choose a new Boot Device or to Boot Recovery Media"

Perhaps I HAVE TO reinstall Ubuntu to get my laptop back. :-(

---

### Post by nrd2 on 2014-05-03
You can repare the boot issue with the Boot Repair tool, which can be run from the live cd: [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) (check the 2nd option)

---

### Post by Dada_Maheshvaranan on 2014-05-04
Boot-repair project team showed me how to resolve the boot problem. But still cannot read wireless or get a network cable to function. :-(

---

### Post by wildmanne39 on 2014-05-04
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
 wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a file named (wireless-info.txt, or wireless-info.txt.tar.gz)depending on the size of the file and it will be placed in your home folder. The wireless information will help to diagnose your wireless issue, the Mac address, WPA key and WEP key are removed for your security, then reply back, click on the paper clip and attach the (wireless-info.txt, or wireless-info.txt.tar.gz) file as a zip file. 

If you do not have ethernet connection then follow the directions at this link for running the script without internet.
[http://ubuntuforums.org/showpost.php?p=12350385](http://ubuntuforums.org/showpost.php?p=12350385).
Thanks

---

### Post by Dada_Maheshvaranan on 2014-05-04
```

########## wireless info START ##########

##### release #####

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04 LTS
Release:    14.04
Codename:    trusty

##### kernel #####

Linux dada-Aspire-V5-123 3.13.0-24-generic #46-Ubuntu SMP Thu Apr 10 19:11:08 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

##### lspci #####

01:00.0 Network controller [0280]: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter [168c:0036] (rev 01)
    Subsystem: Foxconn International, Inc. Device [105b:e07f]
    Kernel driver in use: ath9k
02:00.0 Ethernet controller [0200]: Qualcomm Atheros QCA8171 Gigabit Ethernet [1969:10a1] (rev 10)
    Subsystem: Acer Incorporated [ALI] Device [1025:0834]
    Kernel driver in use: alx

##### lsusb #####

Bus 002 Device 003: ID 05dc:a815 Lexar Media, Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 0489:e078 Foxconn / Hon Hai 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 04f2:b3f6 Chicony Electronics Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 04f3:0212 Elan Microelectronics Corp. Laser Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 003: ID 4971:1006 SimpleTech 
Bus 005 Device 002: ID 4971:1005 SimpleTech 
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA Card Info #####

##### rfkill #####

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no
3: acer-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no

##### iw reg get #####

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### interfaces #####

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

##### iwconfig #####

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

##### route #####

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

##### resolv.conf #####

##### nm-tool #####

NetworkManager Tool

State: asleep

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            alx
  State:             unmanaged
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             unmanaged
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 

##### NetworkManager.state #####

[main]
NetworkingEnabled=false
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager.conf #####

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

##### iwlist #####

No way to aquire root rights found.

##### iwlist channel #####

wlan0     13 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz

##### lsmod #####

ath9k                 164164  0 
ath9k_common           13551  1 ath9k
ath9k_hw              453856  2 ath9k_common,ath9k
ath                    28698  3 ath9k_common,ath9k,ath9k_hw
mac80211              626489  1 ath9k
cfg80211              484040  3 ath,ath9k,mac80211

##### modinfo #####

filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     BAF225EEB618908380B28DA
alias:          platform:qca955x_wmac
alias:          platform:ar934x_wmac
alias:          platform:ar933x_wmac
alias:          platform:ath9k
alias:          pci:v0000168Cd00000036sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000036sv0000185Fsd00003027bc*sc*i*
alias:          pci:v0000168Cd00000036sv00001B9Asd00002810bc*sc*i*
alias:          pci:v0000168Cd00000036sv0000144Fsd00007202bc*sc*i*
alias:          pci:v0000168Cd00000036sv00001A3Bsd00002130bc*sc*i*
alias:          pci:v0000168Cd00000036sv000011ADsd00000612bc*sc*i*
alias:          pci:v0000168Cd00000036sv000011ADsd00000652bc*sc*i*
alias:          pci:v0000168Cd00000036sv000011ADsd00000642bc*sc*i*
alias:          pci:v0000168Cd00000036sv0000168Csd0000302Cbc*sc*i*
alias:          pci:v0000168Cd00000036sv0000168Csd00003027bc*sc*i*
alias:          pci:v0000168Cd00000036sv0000144Dsd0000411Ebc*sc*i*
alias:          pci:v0000168Cd00000036sv0000144Dsd0000411Dbc*sc*i*
alias:          pci:v0000168Cd00000036sv0000144Dsd0000411Cbc*sc*i*
alias:          pci:v0000168Cd00000036sv0000144Dsd0000411Bbc*sc*i*
alias:          pci:v0000168Cd00000036sv0000144Dsd0000411Abc*sc*i*
alias:          pci:v0000168Cd00000036sv00001028sd0000020Ebc*sc*i*
alias:          pci:v0000168Cd00000036sv0000103Csd0000217Fbc*sc*i*
alias:          pci:v0000168Cd00000036sv0000103Csd000018E3bc*sc*i*
alias:          pci:v0000168Cd00000036sv000017AAsd00003026bc*sc*i*
alias:          pci:v0000168Cd00000036sv00001A3Bsd0000213Abc*sc*i*
alias:          pci:v0000168Cd00000036sv000011ADsd00000662bc*sc*i*
alias:          pci:v0000168Cd00000036sv000011ADsd00000672bc*sc*i*
alias:          pci:v0000168Cd00000036sv000011ADsd00000622bc*sc*i*
alias:          pci:v0000168Cd00000036sv0000185Fsd00003028bc*sc*i*
alias:          pci:v0000168Cd00000036sv0000105Bsd0000E069bc*sc*i*
alias:          pci:v0000168Cd00000036sv0000168Csd0000302Bbc*sc*i*
alias:          pci:v0000168Cd00000036sv0000168Csd00003026bc*sc*i*
alias:          pci:v0000168Cd00000036sv0000168Csd00003025bc*sc*i*
alias:          pci:v0000168Cd00000036sv00001B9Asd00002812bc*sc*i*
alias:          pci:v0000168Cd00000036sv00001B9Asd00002811bc*sc*i*
alias:          pci:v0000168Cd00000036sv000011ADsd00006671bc*sc*i*
alias:          pci:v0000168Cd00000036sv000011ADsd00000632bc*sc*i*
alias:          pci:v0000168Cd00000036sv0000185Fsd0000A119bc*sc*i*
alias:          pci:v0000168Cd00000036sv0000105Bsd0000E068bc*sc*i*
alias:          pci:v0000168Cd00000036sv00001A3Bsd00002176bc*sc*i*
alias:          pci:v0000168Cd00000036sv0000168Csd00003028bc*sc*i*
alias:          pci:v0000168Cd00000037sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000034sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000034sv000010CFsd00001783bc*sc*i*
alias:          pci:v0000168Cd00000034sv000014CDsd00000064bc*sc*i*
alias:          pci:v0000168Cd00000034sv000014CDsd00000063bc*sc*i*
alias:          pci:v0000168Cd00000034sv0000103Csd00001864bc*sc*i*
alias:          pci:v0000168Cd00000034sv000011ADsd00006641bc*sc*i*
alias:          pci:v0000168Cd00000034sv000011ADsd00006631bc*sc*i*
alias:          pci:v0000168Cd00000034sv00001043sd0000850Ebc*sc*i*
alias:          pci:v0000168Cd00000034sv00001A3Bsd00002110bc*sc*i*
alias:          pci:v0000168Cd00000034sv00001969sd00000091bc*sc*i*
alias:          pci:v0000168Cd00000034sv000017AAsd00003214bc*sc*i*
alias:          pci:v0000168Cd00000034sv0000168Csd00003117bc*sc*i*
alias:          pci:v0000168Cd00000034sv000011ADsd00006661bc*sc*i*
alias:          pci:v0000168Cd00000034sv00001A3Bsd00002116bc*sc*i*
alias:          pci:v0000168Cd00000033sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000032sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001043sd0000850Dbc*sc*i*
alias:          pci:v0000168Cd00000032sv00001B9Asd00001C01bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001B9Asd00001C00bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00001F95bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00001195bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00001F86bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00001186bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001B9Asd00002001bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001B9Asd00002000bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000144Fsd00007197bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000105Bsd0000E04Fbc*sc*i*
alias:          pci:v0000168Cd00000032sv0000105Bsd0000E04Ebc*sc*i*
alias:          pci:v0000168Cd00000032sv000011ADsd00006628bc*sc*i*
alias:          pci:v0000168Cd00000032sv000011ADsd00006627bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001C56sd00004001bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00002100bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00002C97bc*sc*i*
alias:          pci:v0000168Cd00000032sv000017AAsd00003219bc*sc*i*
alias:          pci:v0000168Cd00000032sv000017AAsd00003218bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000144Dsd0000C708bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000144Dsd0000C680bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000144Dsd0000C706bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000144Dsd0000410Fbc*sc*i*
alias:          pci:v0000168Cd00000032sv0000144Dsd0000410Ebc*sc*i*
alias:          pci:v0000168Cd00000032sv0000144Dsd0000410Dbc*sc*i*
alias:          pci:v0000168Cd00000032sv0000144Dsd00004106bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000144Dsd00004105bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000185Fsd00003027bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000185Fsd00003119bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000168Csd00003122bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000168Csd00003119bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000105Bsd0000E075bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00002152bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd0000126Abc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00002126bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00001237bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00002086bc*sc*i*
alias:          pci:v0000168Cd00000030sv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Esv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Dsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Csv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Bsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Bsv00001A3Bsd00002C37bc*sc*i*
alias:          pci:v0000168Cd0000002Asv000010CFsd00001536bc*sc*i*
alias:          pci:v0000168Cd0000002Asv000010CFsd0000147Dbc*sc*i*
alias:          pci:v0000168Cd0000002Asv000010CFsd0000147Cbc*sc*i*
alias:          pci:v0000168Cd0000002Asv0000185Fsd0000309Dbc*sc*i*
alias:          pci:v0000168Cd0000002Asv00001A32sd00000306bc*sc*i*
alias:          pci:v0000168Cd0000002Asv000011ADsd00006642bc*sc*i*
alias:          pci:v0000168Cd0000002Asv000011ADsd00006632bc*sc*i*
alias:          pci:v0000168Cd0000002Asv0000105Bsd0000E01Fbc*sc*i*
alias:          pci:v0000168Cd0000002Asv00001A3Bsd00001C71bc*sc*i*
alias:          pci:v0000168Cd0000002Asv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000029sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000027sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000024sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000023sv*sd*bc*sc*i*
depends:        ath9k_hw,mac80211,ath9k_common,cfg80211,ath
intree:         Y
vermagic:       3.13.0-24-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:47:4B:C5:C4:31:20:88:0C:1B:94:A5:39:F4:31
sig_hashalgo:   sha512
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           bt_ant_diversity:Enable WLAN/BT RX antenna diversity (int)
parm:           ps_enable:Enable WLAN PowerSave (int)

filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless 802.11n LAN cards.
author:         Atheros Communications
srcversion:     696B00A6C59713EC0966997
depends:        ath,ath9k_hw
intree:         Y
vermagic:       3.13.0-24-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:47:4B:C5:C4:31:20:88:0C:1B:94:A5:39:F4:31
sig_hashalgo:   sha512

filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     4809F3842A0542CD6B556D3
depends:        ath
intree:         Y
vermagic:       3.13.0-24-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:47:4B:C5:C4:31:20:88:0C:1B:94:A5:39:F4:31
sig_hashalgo:   sha512

filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     88A67C5359B02C5A710AFCF
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-24-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:47:4B:C5:C4:31:20:88:0C:1B:94:A5:39:F4:31
sig_hashalgo:   sha512

##### modules #####

lp
rtc

##### blacklist #####

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac

[/etc/modprobe.d/fbdev-blacklist.conf]
blacklist arkfb
blacklist aty128fb
blacklist atyfb
blacklist radeonfb
blacklist cirrusfb
blacklist cyber2000fb
blacklist gx1fb
blacklist gxfb
blacklist kyrofb
blacklist matroxfb_base
blacklist mb862xxfb
blacklist neofb
blacklist nvidiafb
blacklist pm2fb
blacklist pm3fb
blacklist s3fb
blacklist savagefb
blacklist sisfb
blacklist tdfxfb
blacklist tridentfb
blacklist viafb
blacklist vt8623fb

##### udev rules #####

# PCI device 0x1969:0x10a1 (alx)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x168c:0x0036 (ath9k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #####

[   13.231194] ath: phy0: Set BT/WLAN RX diversity capability
[   13.240103] ath: phy0: Enable LNA combining
[   13.241269] ath: phy0: ASPM enabled: 0x42
[   13.241277] ath: EEPROM regdomain: 0x6c
[   13.241281] ath: EEPROM indicates we should expect a direct regpair map
[   13.241289] ath: Country alpha2 being used: 00
[   13.241292] ath: Regpair used: 0x6c
[   14.259217] psmouse serio2: elantech: assuming hardware version 3 (with firmware version 0x550f00)

########## wireless info END ############


```

---

### Post by Dada_Maheshvaranan on 2014-05-05
My friends with Windows or Mac tell me I'm a masochist for using Ubuntu,  whose support community in six days is either incapable or unwilling to  solve a simple connectivity problem caused by the program itself.

---

### Post by Dada_Maheshvaranan on 2014-05-05
i apologize for the previous nasty expresion of my frustration. I'm reinstalling Ubuntu. Problem will no doubt be solved.

---

### Post by Dada_Maheshvaranan on 2014-05-05
A fresh install, erasing everything, worked great, I can access the internet again. Thanks to everyone who tried to help.

---

