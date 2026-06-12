---
title: "Lenovo G50-45 Wireless Driver connects and disconnects loop"
date: 2014-09-09
forum: Networking &amp; Wireless
---

### Post by stratophone2112 on 2014-09-09
I have a Lenovo G50-45, and ever since I've installed Ubuntu on it it's been crazy trying to get the WiFi to connect and stay connected. 

Whenever I log onto the WiFi at my university it will stay working for about a half hour, then the browser pages won't load and it says connection lost even though it's still connected. 
And whenever I try to get back on the WiFi it will flash until it says it's disconnected and loops like that continuously. More often than not I have to reboot my machine to get it to work again. 

I'm aware of the commands that show the information for the WiFi, but I have no idea how to interpret the output for it.

---

### Post by stratophone2112 on 2014-09-09
These are the commands I used 
```

cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
iwconfig
rfkill list all
lsmod

```
```

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=14.04
DISTRIB_CODENAME=trusty
DISTRIB_DESCRIPTION="Ubuntu 14.04.1 LTS"
Linux Lenovo-G50-45 3.13.0-35-generic #62-Ubuntu SMP Fri Aug 15 01:58:42 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
dublin@Lenovo-G50-45:~$ 
dublin@Lenovo-G50-45:~$ lspci -nnk | grep -iA2 net
01:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter [10ec:b723]
	Subsystem: Lenovo Device [17aa:b736]
	Kernel driver in use: rtl8723be
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
	Subsystem: Lenovo Device [17aa:3812]
	Kernel driver in use: r8169
dublin@Lenovo-G50-45:~$ iwconfig
eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:"UARK Guest Wi-Fi"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 44:E4:D9:00:01:F4   
          Bit Rate=72.2 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=50/70  Signal level=-60 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:6   Missed beacon:0
dublin@Lenovo-G50-45:~$ rfkill list all
0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
dublin@Lenovo-G50-45:~$ lsmod
Module                  Size  Used by
rfcomm                 69160  8 
bnep                   19624  2 
nls_iso8859_1          12713  1 
uvcvideo               80885  0 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
videobuf2_core         40664  1 uvcvideo
rts5139               335409  0 
videodev              134688  2 uvcvideo,videobuf2_core
arc4                   12608  2 
kvm                   451511  0 
crct10dif_pclmul       14289  0 
crc32_pclmul           13113  0 
ghash_clmulni_intel    13216  0 
snd_seq_midi           13324  0 
snd_hda_codec_conexant    57441  1 
snd_seq_midi_event     14899  1 snd_seq_midi
aesni_intel            55624  0 
snd_rawmidi            30144  1 snd_seq_midi
snd_hda_codec_hdmi     46368  1 
aes_x86_64             17131  1 aesni_intel
lrw                    13286  1 aesni_intel
gf128mul               14951  1 lrw
glue_helper            13990  1 aesni_intel
ablk_helper            13597  1 aesni_intel
cryptd                 20359  3 ghash_clmulni_intel,aesni_intel,ablk_helper
snd_hda_intel          56451  5 
snd_hda_codec         192906  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
joydev                 17381  0 
snd_pcm               102099  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
rtl8723be              85118  0 
serio_raw              13462  0 
btusb                  32412  0 
btcoexist              50304  1 rtl8723be
bluetooth             391136  22 bnep,btusb,rfcomm
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
rtl8723_common         23361  1 rtl8723be
rtl_pci                26690  1 rtl8723be
rtlwifi                63475  2 rtl_pci,rtl8723be
mac80211              630653  3 rtl_pci,rtlwifi,rtl8723be
i2c_piix4              22155  0 
snd_timer              29482  2 snd_pcm,snd_seq
cfg80211              484040  2 mac80211,rtlwifi
snd                    69322  21 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
soundcore              12680  1 snd
parport_pc             32701  0 
video                  19476  0 
ppdev                  17671  0 
mac_hid                13205  0 
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
psmouse               106678  0 
sdhci_pci              23172  0 
ahci                   25819  3 
r8169                  67581  0 
sdhci                  43015  1 sdhci_pci
libahci                32716  1 ahci
mii                    13934  1 r8169
dublin@Lenovo-G50-45:~$ 

```

---

### Post by varunendra on 2014-09-14
Welcome to the forums stratophone2112 !

Please use 'Code' tags to post the outputs. It preserves their formatting, making it look cleaner and more readable. Please follow the "Use Code Tags" link in my signature below to see a quick guide with screenshots. :)

For your wireless problem, please try what is suggested in this post : [http://ubuntuforums.org/showpost.php?p=13119513](http://ubuntuforums.org/showpost.php?p=13119513) and let us know the result.

---

