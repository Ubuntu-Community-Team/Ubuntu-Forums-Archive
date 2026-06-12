---
title: "Can't enable wifi on Asus X550CA"
date: 2014-04-22
forum: Networking &amp; Wireless
---

### Post by paulo10 on 2014-04-22
> **varunendra said:**
> Please also post the output of "lsmod" as I asked before.

Along with "lsmod", I would now like to see the output of the following as well -
```
grep [[:alnum:]] /sys/module/ath*/parameters/*
```

By the way, please remove ALL the blacklist entries below these last default entries -
```
....
blacklist pcspkr
blacklist amd76x_edac
```
in your /etc/blacklist.conf file, some of them are pointless and you are blocking some essential drivers as well.

Hi guys!!
This is my first message , so I don't know if I can write in a post that is already solved.....
My problem is similar, I have a Asus X550CA, with Ubuntu 14.04 and doesn't recognise my WIFI [Atheros AR9485].
I have tried different things and I haven't found the solution.......

So I will post my different things....

Code :
```

$ rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
1: asus-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: asus-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no

```

Code:
```

~$ lsmod
Module                  Size  Used by
rndis_host             14503  0 
cdc_ether              14351  1 rndis_host
usbnet                 43877  2 rndis_host,cdc_ether
nvram                  14411  0 
bnep                   19624  2 
rfcomm                 69160  0 
bluetooth             395423  10 bnep,rfcomm
uvcvideo               80885  0 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
videobuf2_core         40664  1 uvcvideo
videodev              134688  2 uvcvideo,videobuf2_core
snd_hda_codec_hdmi     46207  1 
snd_hda_codec_realtek    61438  1 
joydev                 17381  0 
nls_iso8859_1          12713  1 
asus_nb_wmi            16990  0 
asus_wmi               24191  1 asus_nb_wmi
sparse_keymap          13948  1 asus_wmi
intel_rapl             18773  0 
x86_pkg_temp_thermal    14205  0 
arc4                   12608  2 
snd_hda_intel          52355  3 
intel_powerclamp       14705  0 
coretemp               13435  0 
snd_hda_codec         192906  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
kvm_intel             143060  0 
kvm                   451511  1 kvm_intel
ath9k                 164164  0 
snd_pcm               102099  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
crct10dif_pclmul       14289  0 
ath9k_common           13551  1 ath9k
parport_pc             32701  0 
ath9k_hw              453856  2 ath9k_common,ath9k
crc32_pclmul           13113  0 
ghash_clmulni_intel    13259  0 
ath                    28698  3 ath9k_common,ath9k,ath9k_hw
aesni_intel            55624  0 
ppdev                  17671  0 
aes_x86_64             17131  1 aesni_intel
mac80211              626489  1 ath9k
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
lrw                    13286  1 aesni_intel
gf128mul               14951  1 lrw
snd_seq_midi           13324  0 
glue_helper            13990  1 aesni_intel
snd_seq_midi_event     14899  1 snd_seq_midi
ablk_helper            13597  1 aesni_intel
cryptd                 20359  3 ghash_clmulni_intel,aesni_intel,ablk_helper
snd_rawmidi            30144  1 snd_seq_midi
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29482  2 snd_pcm,snd_seq
psmouse               102222  0 
serio_raw              13462  0 
cfg80211              484040  3 ath,ath9k,mac80211
rtsx_pci_ms            18151  0 
lp                     17759  0 
snd                    69238  17 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
memstick               16966  1 rtsx_pci_ms
parport                42348  3 lp,ppdev,parport_pc
lpc_ich                21080  0 
wmi                    19177  1 asus_wmi
i915                  783485  3 
mei_me                 18627  0 
video                  19476  2 i915,asus_wmi
drm_kms_helper         52758  1 i915
mac_hid                13205  0 
mei                    82274  1 mei_me
drm                   302817  4 i915,drm_kms_helper
soundcore              12680  1 snd
i2c_algo_bit           13413  1 i915
rtsx_pci_sdmmc         23274  0 
ahci                   25819  3 
r8169                  67581  0 
libahci                32168  1 ahci
rtsx_pci               45956  2 rtsx_pci_ms,rtsx_pci_sdmmc
mii                    13934  2 r8169,usbnet

```

Code:
```

~$ lsmod | grep asus
asus_nb_wmi            16990  0 
asus_wmi               24191  1 asus_nb_wmi
sparse_keymap          13948  1 asus_wmi
wmi                    19177  1 asus_wmi
video                  19476  2 i915,asus_wmi

```

My file blacklist.conf is the next, I delete the last line wich was "asus_wmi"

```

# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac

```

Code
```

~$ grep [[:alnum:]] /sys/module/ath*/parameters/*
/sys/module/ath9k/parameters/blink:0
/sys/module/ath9k/parameters/bt_ant_diversity:0
/sys/module/ath9k/parameters/btcoex_enable:0
/sys/module/ath9k/parameters/nohwcrypt:0
/sys/module/ath9k/parameters/ps_enable:0

```

This is everything, I am new in ubuntu....
Thank you for you time!

---

### Post by slickymaster on 2014-04-22
> **paulo10 said:**
> Hi guys!!
This is my first message , so I don't know if I can write in a post that is already solved.....
My problem is similar, I have a Asus X550CA, with Ubuntu 14.04 and doesn't recognise my WIFI [Atheros AR9485].
I have tried different things and I haven't found the solution.......

So I will post my different things....

Code :
```

$ rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
1: asus-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: asus-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no

```

Code:
```

~$ lsmod
Module                  Size  Used by
rndis_host             14503  0 
cdc_ether              14351  1 rndis_host
usbnet                 43877  2 rndis_host,cdc_ether
nvram                  14411  0 
bnep                   19624  2 
rfcomm                 69160  0 
bluetooth             395423  10 bnep,rfcomm
uvcvideo               80885  0 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
videobuf2_core         40664  1 uvcvideo
videodev              134688  2 uvcvideo,videobuf2_core
snd_hda_codec_hdmi     46207  1 
snd_hda_codec_realtek    61438  1 
joydev                 17381  0 
nls_iso8859_1          12713  1 
asus_nb_wmi            16990  0 
asus_wmi               24191  1 asus_nb_wmi
sparse_keymap          13948  1 asus_wmi
intel_rapl             18773  0 
x86_pkg_temp_thermal    14205  0 
arc4                   12608  2 
snd_hda_intel          52355  3 
intel_powerclamp       14705  0 
coretemp               13435  0 
snd_hda_codec         192906  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
kvm_intel             143060  0 
kvm                   451511  1 kvm_intel
ath9k                 164164  0 
snd_pcm               102099  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
crct10dif_pclmul       14289  0 
ath9k_common           13551  1 ath9k
parport_pc             32701  0 
ath9k_hw              453856  2 ath9k_common,ath9k
crc32_pclmul           13113  0 
ghash_clmulni_intel    13259  0 
ath                    28698  3 ath9k_common,ath9k,ath9k_hw
aesni_intel            55624  0 
ppdev                  17671  0 
aes_x86_64             17131  1 aesni_intel
mac80211              626489  1 ath9k
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
lrw                    13286  1 aesni_intel
gf128mul               14951  1 lrw
snd_seq_midi           13324  0 
glue_helper            13990  1 aesni_intel
snd_seq_midi_event     14899  1 snd_seq_midi
ablk_helper            13597  1 aesni_intel
cryptd                 20359  3 ghash_clmulni_intel,aesni_intel,ablk_helper
snd_rawmidi            30144  1 snd_seq_midi
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29482  2 snd_pcm,snd_seq
psmouse               102222  0 
serio_raw              13462  0 
cfg80211              484040  3 ath,ath9k,mac80211
rtsx_pci_ms            18151  0 
lp                     17759  0 
snd                    69238  17 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
memstick               16966  1 rtsx_pci_ms
parport                42348  3 lp,ppdev,parport_pc
lpc_ich                21080  0 
wmi                    19177  1 asus_wmi
i915                  783485  3 
mei_me                 18627  0 
video                  19476  2 i915,asus_wmi
drm_kms_helper         52758  1 i915
mac_hid                13205  0 
mei                    82274  1 mei_me
drm                   302817  4 i915,drm_kms_helper
soundcore              12680  1 snd
i2c_algo_bit           13413  1 i915
rtsx_pci_sdmmc         23274  0 
ahci                   25819  3 
r8169                  67581  0 
libahci                32168  1 ahci
rtsx_pci               45956  2 rtsx_pci_ms,rtsx_pci_sdmmc
mii                    13934  2 r8169,usbnet

```

Code:
```

~$ lsmod | grep asus
asus_nb_wmi            16990  0 
asus_wmi               24191  1 asus_nb_wmi
sparse_keymap          13948  1 asus_wmi
wmi                    19177  1 asus_wmi
video                  19476  2 i915,asus_wmi

```

My file blacklist.conf is the next, I delete the last line wich was "asus_wmi"

```

# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac

```

Code
```

~$ grep [[:alnum:]] /sys/module/ath*/parameters/*
/sys/module/ath9k/parameters/blink:0
/sys/module/ath9k/parameters/bt_ant_diversity:0
/sys/module/ath9k/parameters/btcoex_enable:0
/sys/module/ath9k/parameters/nohwcrypt:0
/sys/module/ath9k/parameters/ps_enable:0

```

This is everything, I am new in ubuntu....
Thank you for you time!

I would advise you to start your own thread. Chances are you'll get much more help on a new one rather than in one already marked as solved.

---

### Post by varunendra on 2014-04-22
Welcome to the forums paulo10 !
> **paulo10 said:**
> ```

$ rfkill list
**0: phy0:** Wireless LAN
    Soft blocked: no
    **Hard blocked: [COLOR="#FF0000"]yes[/COLOR]**
1: asus-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```

I think the above hint combined with the fact that it is an Asus is sufficient for me to see a possible culprit. Please take a look at this thread and try what is suggested there : [http://ubuntuforums.org/showthread.php?t=2181558](http://ubuntuforums.org/showthread.php?t=2181558)

In the meanwhile, I'd request the mods to move your post along with the responses to it to its own thread. :)

---

### Post by cariboo on 2014-04-22
Moved to a thread of it's own.

---

### Post by varunendra on 2014-04-22
Thanks cariboo907!

By the way, I'm posting this so that the thread starts appearing in my search results *(Advanced Search (type 1) > search by user ID 'varunendra')*. So far it doesn't, *(as I've already reported many times before - definitely a forum bug, probably affecting only a few users like me, due to which threads created by moving posts don't appear in search results unless I make a fresh post in them AFTER they've been moved)*.

---

### Post by paulo10 on 2014-04-22
> **varunendra said:**
> Thanks cariboo907!

By the way, I'm posting this so that the thread starts appearing in my search results *(Advanced Search (type 1) > search by user ID 'varunendra')*. So far it doesn't, *(as I've already reported many times before - definitely a forum bug, probably affecting only a few users like me, due to which threads created by moving posts don't appear in search results unless I make a fresh post in them AFTER they've been moved)*.

Thanks thanks and thanks!!!
I have followed the instructions from this post : [http://ubuntuforums.org/showthread.php?t=2181558](http://ubuntuforums.org/showthread.php?t=2181558) , and the solution was 

Code
```
echo "options asus_nb_wmi wapf=1" | sudo tee /etc/modprobe.d/asus_nb_wmi.conf
```

I'm struggling with this new laptop and with Ubuntu 14.04, it will be pretty hard configurate everything....I 've seen that you have the distro 12.04.  I am begginer, so, Should I use the distro 12.04? any advice is welcome!

---

### Post by varunendra on 2014-04-22
I didn't upgrade because I had a very slow internet connection (max download speed upto 4 KB/s !!). Now I do have a faster connection, but don't have enough time to try a newer version (I am thinking of switching to Xubuntu for faster performance). Since my current setup is working fine for me, I am not bothering much about upgrades and it may take me a few more days (or weeks, or months! ;)) before I try out the latest LTS (14.04).

Right now 14.04 is very new and may have some initial bugs that will be ironed out soon. So yeah, in some particular cases, 12.04 *may be* a better choice. Although in a few days, the latest "Point Release" of 12.04 will be released (if it hasn't been already). It will contain the same kernel version and xorg stack as 14.04, so won't be much different than 14.04.

If you are having problems with 14.04, I suggest you start a new thread (one thread per issue, unless the issues are similar or closely related), post the problems there and ask for suggestions. If it is the hardware limitations causing the problems, you'll get suggestions about using a lighter variant of Ubuntu (or a different distro altogether).

---

