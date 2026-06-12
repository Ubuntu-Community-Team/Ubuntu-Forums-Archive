---
title: "Connected to network but no internet connection"
date: 2014-07-24
forum: Networking &amp; Wireless
---

### Post by FDRmz4Y on 2014-07-24
I'm connected to my network but can't go to any web page on the internet. Here are some outputs:

```
DISTRIB_ID=UbuntuDISTRIB_RELEASE=14.04
DISTRIB_CODENAME=trusty
DISTRIB_DESCRIPTION="Ubuntu 14.04 LTS"
Linux terence-ThinkPad-Edge-E545 3.13.0-24-generic #46-Ubuntu SMP Thu Apr 10 19:11:08 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux




01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 07)
    Subsystem: Lenovo Device [17aa:5100]
    Kernel driver in use: r8169
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188EE Wireless Network Adapter [10ec:8179] (rev 01)
    Subsystem: Lenovo Device [17aa:0179]
    Kernel driver in use: rtl8188ee




eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:"ppa4"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: E8:89:2C:29:4D:50   
          Bit Rate=135 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=30 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:8   Missed beacon:0


0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no




nls_iso8859_1          12713  1 
usb_storage            62209  1 
brcmsmac              563041  0 
cordic                 12574  1 brcmsmac
brcmutil               15618  1 brcmsmac
bcma                   52096  1 brcmsmac
ctr                    13049  1 
ccm                    17773  1 
bnep                   19624  2 
rfcomm                 69160  0 
bluetooth             395423  10 bnep,rfcomm
snd_hda_codec_conexant    57441  1 
snd_hda_codec_hdmi     46207  1 
joydev                 17381  0 
uvcvideo               80885  0 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
videobuf2_core         40664  1 uvcvideo
videodev              134688  2 uvcvideo,videobuf2_core
kvm_amd                59987  0 
arc4                   12608  2 
kvm                   451511  1 kvm_amd
crct10dif_pclmul       14289  0 
crc32_pclmul           13113  0 
ghash_clmulni_intel    13259  0 
aesni_intel            55624  2 
aes_x86_64             17131  1 aesni_intel
lrw                    13286  1 aesni_intel
gf128mul               14951  1 lrw
glue_helper            13990  1 aesni_intel
ablk_helper            13597  1 aesni_intel
cryptd                 20359  3 ghash_clmulni_intel,aesni_intel,ablk_helper
psmouse               102222  0 
serio_raw              13462  0 
rtl8188ee              89601  0 
rtl_pci                26690  1 rtl8188ee
rtlwifi                63475  2 rtl_pci,rtl8188ee
snd_hda_intel          52355  5 
mac80211              626489  4 brcmsmac,rtl_pci,rtlwifi,rtl8188ee
snd_hda_codec         192906  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
k10temp                13126  0 
snd_hwdep              13602  1 snd_hda_codec
i2c_piix4              22155  0 
radeon               1514165  3 
snd_pcm               102099  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
cfg80211              484040  3 brcmsmac,mac80211,rtlwifi
rtsx_pci_ms            18151  0 
ttm                    85115  1 radeon
drm_kms_helper         52758  1 radeon
memstick               16966  1 rtsx_pci_ms
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
drm                   302817  5 ttm,drm_kms_helper,radeon
i2c_algo_bit           13413  1 radeon
wmi                    19177  0 
thinkpad_acpi          80817  1 
nvram                  14411  1 thinkpad_acpi
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30144  1 snd_seq_midi
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29482  2 snd_pcm,snd_seq
snd                    69238  22 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,thinkpad_acpi,snd_seq_device,snd_seq_midi
soundcore              12680  1 snd
video                  19476  0 
mac_hid                13205  0 
parport_pc             32701  0 
ppdev                  17671  0 
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
hid_generic            12548  0 
usbhid                 52616  0 
hid                   106148  2 hid_generic,usbhid
rtsx_pci_sdmmc         23274  0 
ahci                   25819  2 
libahci                32168  1 ahci
rtsx_pci               45956  2 rtsx_pci_ms,rtsx_pci_sdmmc
r8169                  67581  0 
mii                    13934  1 r8169



```

EDIT: Sorry I posted to the wrong section of the forum, could someone please move this over to networking?

---

### Post by varunendra on 2014-07-24
Please post the output of -
```
nm-tool
```

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Use Code Tags" link in my signature.

**PS:**
You can always use the "Report Post" button below any post to directly communicate with the forum moderators. It is meant to report anything that needs attention or action from the admins/moderators. For example, to move your thread to the correct section.

I am going to request the mods using the same button to move your thread. :)

---

### Post by sisco311 on 2014-07-24
Thread moved to **Networking & Wireless.**

---

### Post by anspectrum on 2014-07-24
> **FDRmz4Y said:**
> I'm connected to my network but can't go to any web page on the internet........

This is a very generic statement. Please check following:

```

1. ifconfig -a           //To check the correct IP address related information on your desired interface

2. route -n              //To check whether your machine has correct default route pointed towards the gateway (your router / modem)

3. ping 8.8.8.8         //To check if you can reach IPs outside your network.

4. cat /etc/resolve.conf     //To check if proper DNS resolver entries exist.


```

Also check your browser settings for any proxies etc.

If you are unable to get the browser working, please share output of above commands and we will try to help.

Cheers.

---

### Post by Bucky Ball on 2014-07-24
Are you using a static IP address? If so, do you have it set up in Network Manager? Do you have the correct DNS set or a DNS IP set at all?

---

