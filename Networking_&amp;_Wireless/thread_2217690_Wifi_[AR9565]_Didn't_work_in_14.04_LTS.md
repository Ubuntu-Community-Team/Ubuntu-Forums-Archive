---
title: "Wifi [AR9565] Didn't work in 14.04 LTS"
date: 2014-04-18
forum: Networking &amp; Wireless
---

### Post by overbid on 2014-04-18
It's work on Debian 7 but not on ubuntu how do I fix it. I can't enable it.

```
rfkill list
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: acer-wireless: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
```

```
lsmod | grep -E 'ath|brcmsmac'
ath9k                 164164  0 
ath9k_common           13551  1 ath9k
ath9k_hw              453856  2 ath9k_common,ath9k
ath                    28698  3 ath9k_common,ath9k,ath9k_hw
mac80211              626489  1 ath9k
cfg80211              484040  3 ath,ath9k,mac80211
ath3k                  13318  0 
bluetooth             395423  23 bnep,ath3k,btusb,rfcomm
```

```
dmesg | grep -E 'cfg|ath|wlan'
[    0.930410] Loaded X.509 cert 'Magrathea: Glacier signing key: 00a5a65759de474bc5c43120880c1b94a539f431'
[    9.291368] usbcore: registered new interface driver ath3k
[    9.300678] cfg80211: Calling CRDA to update world regulatory domain
[    9.320226] ath: phy0: Disable PLL PowerSave
[    9.328827] ath: phy0: ASPM enabled: 0x43
[    9.328831] ath: EEPROM regdomain: 0x60
[    9.328832] ath: EEPROM indicates we should expect a direct regpair map
[    9.328834] ath: Country alpha2 being used: 00
[    9.328835] ath: Regpair used: 0x60
[    9.454629] cfg80211: World regulatory domain updated:
[    9.454633] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[    9.454634] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    9.454636] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    9.454638] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    9.454639] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    9.454640] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.225331] SKU: Nid=0x1d sku_cfg=0x40e5812d
[   10.225566] realtek: No valid SSID, checking pincfg 0x40e5812d for NID 0x1d
[   13.027048] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   23.211611] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   86.586843] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  277.391415] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  290.307430] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  293.017900] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  475.096690] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
```

```

lspci -nn | grep Network
03:00.0 Network controller [0280]: Qualcomm Atheros AR9485 Wireless Network Adapter [168c:0032] (rev 01)
```

---

### Post by varunendra on 2014-04-19
Welcome to the forums overbid!

Noticing this -
> **overbid said:**
> ```

2: acer-wireless: Wireless LAN
    **Soft blocked: [COLOR="#FF0000"]yes[/COLOR]**
    Hard blocked: no
```

..what happens if you do -
```
sudo rfkill unblock all
```??

If this can't remove the Soft block, please follow the "Wireless Script" link in my signature below, download and run the script as per instructions in the linked post, and post back the report it generates. Along with the report, please also post the _FULL_ output of "lsmod" command.

---

### Post by overbid on 2014-04-20
yes but still
acer-wireless: Wireless LAN
    **Soft blocked: [COLOR=#FF0000]yes[/COLOR]**
    Hard blocked: no

After run wireless_script it's show as in attachment.
Thanks for your reply.

---

### Post by varunendra on 2014-04-20
Please also post the output of "lsmod" as I asked before.

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

---

### Post by overbid on 2014-04-20
Thanks for help!
```

grep [[:alnum:]] /sys/module/ath*/parameters/*
/sys/module/ath9k/parameters/blink:1
/sys/module/ath9k/parameters/bt_ant_diversity:0
/sys/module/ath9k/parameters/btcoex_enable:1
/sys/module/ath9k/parameters/nohwcrypt:1
/sys/module/ath9k/parameters/ps_enable:0

```

```

lsmod
Module                  Size  Used by
snd_hda_codec_hdmi     46207  1 
snd_hda_codec_realtek    61438  1 
bnep                   19624  2 
rfcomm                 69160  0 
bluetooth             395423  10 bnep,rfcomm
joydev                 17381  0 
arc4                   12608  2 
uvcvideo               80885  0 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
videobuf2_core         40664  1 uvcvideo
videodev              134688  2 uvcvideo,videobuf2_core
asus_nb_wmi            16990  0 
asus_wmi               24191  1 asus_nb_wmi
acer_wmi               32522  0 
sparse_keymap          13948  2 acer_wmi,asus_wmi
x86_pkg_temp_thermal    14205  0 
intel_powerclamp       14705  0 
coretemp               13435  0 
kvm_intel             143060  0 
kvm                   451511  1 kvm_intel
crct10dif_pclmul       14289  0 
ath9k                 164164  0 
crc32_pclmul           13113  0 
snd_hda_intel          52355  5 
ath9k_common           13551  1 ath9k
ghash_clmulni_intel    13259  0 
snd_hda_codec         192906  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
aesni_intel            55624  0 
aes_x86_64             17131  1 aesni_intel
i915                  783485  5 
snd_hwdep              13602  1 snd_hda_codec
lrw                    13286  1 aesni_intel
gf128mul               14951  1 lrw
ath9k_hw              453856  2 ath9k_common,ath9k
glue_helper            13990  1 aesni_intel
snd_pcm               102099  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
ablk_helper            13597  1 aesni_intel
cryptd                 20359  3 ghash_clmulni_intel,aesni_intel,ablk_helper
nouveau              1097199  1 
ath                    28698  3 ath9k_common,ath9k,ath9k_hw
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
mac80211              626489  1 ath9k
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30144  1 snd_seq_midi
psmouse               102222  0 
mxm_wmi                13021  1 nouveau
ttm                    85115  1 nouveau
serio_raw              13462  0 
drm_kms_helper         52758  2 i915,nouveau
drm                   302817  7 ttm,i915,drm_kms_helper,nouveau
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
lpc_ich                21080  0 
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
cfg80211              484040  3 ath,ath9k,mac80211
snd_timer              29482  2 snd_pcm,snd_seq
snd                    69238  21 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
mei_me                 18627  0 
mei                    82274  1 mei_me
soundcore              12680  1 snd
i2c_algo_bit           13413  2 i915,nouveau
video                  19476  4 i915,acer_wmi,nouveau,asus_wmi
wmi                    19177  4 acer_wmi,mxm_wmi,nouveau,asus_wmi
mac_hid                13205  0 
parport_pc             32701  0 
ppdev                  17671  0 
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
hid_generic            12548  0 
usbhid                 52616  0 
hid                   106148  2 hid_generic,usbhid
ahci                   25819  3 
alx                    32452  0 
libahci                32168  1 ahci
mdio                   13807  1 alx

```

---

### Post by varunendra on 2014-04-20
Whoa!! What is this? :shock:
> **overbid said:**
> ```

....
asus_nb_wmi            16990  0 
**[COLOR="#FF0000"]asus_wmi[/COLOR]**               24191  1 asus_nb_wmi
**[COLOR="#FF0000"]acer_wmi[/COLOR]**               32522  0 
....

```
Is your laptop an Asus or an Acer?? The kernel can't decide and has loaded drivers for both, and now obviously both are quarreling over 'who rules the throne'!

Please post which brand/model your lappy is, so we can settle the conflict.

And have you manually set the "**btcoex_enable=1**" parameter using some conf file or command? Because its default value is (and probably should be) '0' for ath9k driver.

---

### Post by overbid on 2014-04-20
I use Asus K450J and yes I manual set it from older similar problem.

---

### Post by varunendra on 2014-04-20
Please undo the change you did to set "btcoex_enable=1".

Then, to prevent acer_wmi from loading, blacklist it -
```
echo "blacklist acer_wmi" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
Reboot, and check -
```
lsmod | grep wmi
```
You should see only asus_wmi (and asus_nb_wmi) in the output, no "acer_wmi". If yes, can you enable the wifi now?

---

### Post by overbid on 2014-04-20
"**btcoex_enable=1**" I don't know how to set to 0. and thanks for your help, now I can use wifi but I faces another problem. I can't use any USB ports now
i edit file manually nor sudo modprobe ath9k btcoex_enable=0 they didn't work.

---

### Post by varunendra on 2014-04-20
> **overbid said:**
> now I can use wifi but I faces another problem. I can't use any USB ports now

Could you use them earlier? The wmi drivers should have nothing to do with USB ports or drivers. So unless you are absolutely sure it is related, you should post the problem in a separate thread dedicated to that problem.

As for undoing the "btcoex_enable" parameter, I think you might have created a conf file in the /etc/modprobe.d directory. You simply need to edit or delete that file. If unsure, please post back the output of -
```
grep 'btcoex_enable' /etc/modprobe.d/*
```

**PS:**
Please check your laptop's BIOS. Is there an option called "IOMMU" somewhere in it? If yes, it may be related to your USB issue.

---

### Post by overbid on 2014-04-20
I delete all config in ath9k.conf and everything is fine now. Thanks Varun (This is mean rain?), you made ubuntu is ubuntu.

After clean install just use this command
```
echo "blacklist acer_wmi" | sudo tee -a /etc/modprobe.d/blacklist.conf
sudo reboot
```
and everything perfect

---

### Post by varunendra on 2014-04-21
Thanks for the compliments and the feedback.

> **overbid said:**
> Thanks Varun (This is mean rain?)..
Almost there.. "Varun" is a Hindu God - the God of Water (or Rain). :)

---

### Post by overbid on 2014-04-21
[IMG]http://upload.wikimedia.org/wikipedia/commons/d/d6/Emblem_of_MOAC%2C_Thailand.png[/IMG]

This is &#3614;&#3619;&#3632;&#3614;&#3636;&#3619;&#3640;&#3603; (varun) in Thai.

---

### Post by varunendra on 2014-04-21
Cool !! O:)

I didn't know my ride looks so scary :p

---

### Post by overbid on 2014-04-21
It's naka in thais imagination.

---

