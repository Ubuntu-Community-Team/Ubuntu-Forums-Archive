---
title: "Wi-Fi is disabled by hardware switch"
date: 2014-05-18
forum: Networking &amp; Wireless
---

### Post by sonny6 on 2014-05-18
I have an AWUS036H USB wireless adapter but when I plug it  into my computer, it doesn't work and in the Ubuntu it says 'WiFi is  disabled by hardware switch.' I've googled the problem and read some  solutions but not one worked for me.. In my situation there is something  "extra", I spilled beer onto my laptop; thank god it still works but  the keyboard doesn't work, so now I have to use a USB keyboard. The wifi  button on the laptop is F2. I try to press F2 and FN + F2 on the USB  keyboard but nothing happens. I wonder if this is fixable or is it an hardware problem.


  When I do ```
rfkill list all
```, I get 

  ```
0: phy0: Wireless LAN     Soft blocked: no     Hard blocked: yes 
1: phy1: Wireless LAN     Soft blocked: no     Hard blocked: no 




```  Can someone help me fix this please.

---

### Post by praseodym on 2014-05-18
Hi,

what computer is it (brand, model)? Have you tried to reset the BIOS to default? Or is it an (U)EFI?

---

### Post by sonny6 on 2014-05-18
My laptop is a Dell Inspiron 15-3521. I went to my BIOS and did "Load optimal default".

---

### Post by praseodym on 2014-05-18
Lets check:
```

lsmod
dmesg | egrep 'dell|switch'
```

---

### Post by sonny6 on 2014-05-18
I get..

```
sn@s1:~/Downloads$ dmesg | egrep 'dell|switch'
[    2.510992] Console: switching to colour frame buffer device 128x48
[   14.177144] Console: switching to colour dummy device 80x25
[   15.270758] Console: switching to colour frame buffer device 170x48
[   15.908885] rtl8187: wireless switch is on
[ 1364.597033] rtl8187: wireless switch is on

```

---

### Post by praseodym on 2014-05-18
```
[ 1364.597033] rtl8187: wireless switch is on
```
Hmmmm, please show
```

lsmod
```
Normally USB devices are not switchable by "rfkill".

---

### Post by sonny6 on 2014-05-18
```

sn@s1:~$ lsmod
Module                  Size  Used by
bnep                   19624  2 
rfcomm                 69160  0 
bluetooth             395423  10 bnep,rfcomm
binfmt_misc            17468  1 
rtl8187                64909  0 
nls_iso8859_1          12713  1 
snd_hda_codec_hdmi     46207  1 
snd_hda_codec_realtek    61438  1 
eeprom_93cx6           13344  1 rtl8187
dell_wmi               12761  0 
sparse_keymap          13948  1 dell_wmi
uvcvideo               80885  0 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
videobuf2_core         40664  1 uvcvideo
videodev              134688  2 uvcvideo,videobuf2_core
rts5139               335409  0 
arc4                   12608  4 
iwldvm                232285  0 
mac80211              626489  2 rtl8187,iwldvm
snd_hda_intel          52355  3 
dell_laptop            18168  0 
dcdbas                 14928  1 dell_laptop
snd_hda_codec         192906  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm               102099  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
intel_rapl             18773  0 
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
x86_pkg_temp_thermal    14205  0 
intel_powerclamp       14705  0 
coretemp               13435  0 
snd_seq_midi           13324  0 
kvm_intel             143060  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30144  1 snd_seq_midi
kvm                   451511  1 kvm_intel
crct10dif_pclmul       14289  0 
crc32_pclmul           13113  0 
ghash_clmulni_intel    13259  0 
cryptd                 20359  1 ghash_clmulni_intel
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
joydev                 17381  0 
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29482  2 snd_pcm,snd_seq
serio_raw              13462  0 
iwlwifi               169932  1 iwldvm
snd                    69238  17 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
cfg80211              484040  4 iwlwifi,mac80211,rtl8187,iwldvm
mei_me                 18627  0 
lpc_ich                21080  0 
soundcore              12680  1 snd
mei                    82274  1 mei_me
wmi                    19177  1 dell_wmi
i915                  783485  5 
video                  19476  1 i915
drm_kms_helper         52758  1 i915
drm                   302817  6 i915,drm_kms_helper
mac_hid                13205  0 
i2c_algo_bit           13413  1 i915
parport_pc             32701  0 
ppdev                  17671  0 
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
hid_generic            12548  0 
usbhid                 52616  0 
hid                   106148  2 hid_generic,usbhid
r8169                  67581  0 
psmouse               102222  0 
ahci                   25819  3 
libahci                32168  1 ahci
mii                    13934  1 r8169


```

---

### Post by praseodym on 2014-05-18
Try to blacklist this module:
```

echo "blacklist dell_laptop" | sudo tee -a /etc/modprobe.d/blacklist-dell.conf 
```
Reboot and check the buttons and "rfkill list" again. If it doesnt work, remove the file and reboot again:

```
sudo rm /etc/modprobe.d/blacklist-dell.conf
```

---

### Post by sonny6 on 2014-05-18
doesn't seem to work.

```
sn@s1:~$ rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
1: phy1: Wireless LAN
    Soft blocked: no
    Hard blocked: no


```

---

### Post by praseodym on 2014-05-19
What about the internal Intel card? Unplug the stick and
```

sudo modprobe -rfv iwlwifi
sudo modprobe -rfv rtl8187
sudo rfkill unblock all
```
Replug it and check
```
lspci -nnk | grep -iA2 net
rfkill list
iwconfig
lsmod
```

---

