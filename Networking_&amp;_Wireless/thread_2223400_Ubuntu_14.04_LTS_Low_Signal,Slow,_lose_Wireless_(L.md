---
title: "Ubuntu 14.04 LTS: Low Signal,Slow, lose Wireless (Laptop  Acer V5p122)"
date: 2014-05-10
forum: Networking &amp; Wireless
---

### Post by jeroni2 on 2014-05-10
Hi Gurus,

I hope anyone can help me, I never had any problems with internet connection working on linux, but we bought  new laptop for my wife and is impossible to make it work properly.

I have tried a lot of thinks that I have been reading at the forums but without success.

The wireless signa only appears when I am behind the router, is very low and the navigation is also very slow. When I try to move just 1 metre I lose the internet connection I also notice that also I do not detect our neighbors connections SID. Obviously I had other devices that use the same wireless connection and all works.  I hope that this have a solution, because I do not want to reinstall Windows 8.

 
If you wan't that I send some tech information, please post the code because I not an expert on wireless settings.

I hope that anyone can help me to solve the issue.

Thansk!

---

### Post by Hadaka on 2014-05-10
Hi, please post the ouput of...
```
lspci -nn | grep 0280
lsmod
rfkill list all
```
thanks

---

### Post by jeroni2 on 2014-05-11
> **Hadaka said:**
> Hi, please post the ouput of...
```
lspci -nn | grep 0280
lsmod
rfkill list all
```
thanks

Thanks for your quick answer Katada I am a bit desperate with his issue.

Heres is the info you asked for, hope it helps to see wha happens:

01:00.0 Network controller [0280]: Broadcom Corporation BCM43142 802.11b/g/n [14e4:4365] (rev 01)
---------------------------------------------------------------------------------------------------------------------------------------------------
Module                  Size  Used by
michael_mic            12612  4 
arc4                   12608  2 
bnep                   19624  2 
rfcomm                 69160  8 
snd_hda_codec_realtek    61438  1 
snd_hda_codec_hdmi     46207  1 
joydev                 17381  0 
hid_multitouch         17407  0 
uvcvideo               80885  0 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
btusb                  32412  0 
videobuf2_core         40664  1 uvcvideo
bluetooth             395423  22 bnep,btusb,rfcomm
usbhid                 52616  0 
videodev              134688  2 uvcvideo,videobuf2_core
hid                   106148  2 hid_multitouch,usbhid
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
snd_seq_midi           13324  0 
lib80211_crypt_tkip    17619  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30144  1 snd_seq_midi
psmouse               102222  0 
snd_hda_intel          52355  5 
parport_pc             32701  0 
snd_hda_codec         192906  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
serio_raw              13462  0 
snd_hwdep              13602  1 snd_hda_codec
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
ppdev                  17671  0 
fam15h_power           13119  0 
wl                   4207846  0 
k10temp                13126  0 
snd_pcm               102099  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
radeon               1514165  3 
edac_core              62291  0 
lib80211               14381  2 wl,lib80211_crypt_tkip
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
edac_mce_amd           22617  0 
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_timer              29482  2 snd_pcm,snd_seq
i2c_piix4              22155  0 
snd                    69238  21 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
cfg80211              484040  1 wl
lp                     17759  0 
ttm                    85115  1 radeon
parport                42348  3 lp,ppdev,parport_pc
drm_kms_helper         52758  1 radeon
drm                   302817  5 ttm,drm_kms_helper,radeon
i2c_algo_bit           13413  1 radeon
soundcore              12680  1 snd
wmi                    19177  0 
mac_hid                13205  0 
video                  19476  0 
sdhci_pci              23172  0 
ahci                   25819  2 
sdhci                  43015  1 sdhci_pci
libahci                32168  1 ahci
--------------------------------------------------------------------------------------------------------
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no
--------------------------------------------------------------------------------------------------------

Thnks!
Jeroni

---

### Post by Hadaka on 2014-05-11
Hi, please do..

```
sudo apt-get remove --purge bcmwl-kernel-source
				sudo apt-get install bcmwl-kernel-source
sudo modprobe -rf wl
sudo modprobe -v wl
```
thanks.

---

### Post by jeroni2 on 2014-05-11
HI Hadaka,
Sorry but still the same problem. Very low signal, so I just can conect if I work near to the router.

Some information: I installed Wicd and the signal streng when I just beyond the router is 55%, when I get out of the room goes just cross the door it goes down to 22%.  If i move 2 meters out of the room then I can not connect.

Any Idea?

Thnks!

---

### Post by jeroni2 on 2014-05-13
Finaly I decide to buy a compatible Usb Wireless adapter, and it works perfectly.

Anyway, thanks.

---

