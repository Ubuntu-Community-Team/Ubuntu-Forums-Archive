---
title: "Cannot turn on Qualcomm Atheros AR9287 Wireless Network Adapter"
date: 2015-06-27
forum: Networking &amp; Wireless
---

### Post by Darrell_Tay on 2015-06-27
Hello everyone, I'm new to Lubuntu, and even newer to the forums so please forgive me if I somehow overlooked some conventions with regards to posting in forums. 

I am using Lubuntu 15.04, installed on an Acer Aspire 4752G, with the wireless network adapter mentioned above. I understand that several others have experienced somewhat similar issues, but it doesn't seem to apply in my case... It's a long post, so I apologise in advance.

The Problem(s):

1. According to the Network icon on the taskbar it says "WiFi is  disabled by hardware switch." I therefore searched the net for methods  to turn it on. I tried doing ```
rfkill unblock all
``` but it did not unblock my network adapter, and it remains hard blocked (though not soft-blocked). When I ran ```
sudo lsmod
``` it seemed that the driver was installed, though I can't be sure because I couldn't make sense of the output. Here is the output:

```
Module                  Size  Used by
bbswitch               16384  0 
rfcomm                 69632  8 
bnep                   20480  2 
nls_iso8859_1          16384  1 
nvidia               8380416  35 
arc4                   16384  2 
ath9k                 147456  0 
intel_rapl             20480  0 
iosf_mbi               16384  1 intel_rapl
ath9k_common           32768  1 ath9k
x86_pkg_temp_thermal    16384  0 
ath9k_hw              458752  2 ath9k_common,ath9k
intel_powerclamp       20480  0 
snd_hda_codec_hdmi     53248  1 
coretemp               16384  0 
snd_hda_codec_realtek    86016  1 
kvm_intel             151552  0 
ath                    32768  3 ath9k_common,ath9k,ath9k_hw
snd_hda_codec_generic    69632  1 snd_hda_codec_realtek
uvcvideo               90112  0 
mac80211              724992  1 ath9k
kvm                   483328  1 kvm_intel
videobuf2_vmalloc      16384  1 uvcvideo
snd_hda_intel          32768  1 
snd_hda_controller     32768  1 snd_hda_intel
videobuf2_memops       16384  1 videobuf2_vmalloc
snd_hda_codec         143360  5 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel,snd_hda_controller
videobuf2_core         49152  1 uvcvideo
v4l2_common            16384  1 videobuf2_core
snd_hwdep              20480  1 snd_hda_codec
i915                 1052672  3 
videodev              159744  3 uvcvideo,v4l2_common,videobuf2_core
media                  24576  2 uvcvideo,videodev
crct10dif_pclmul       16384  0 
snd_pcm               106496  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller
ath3k                  16384  0 
acer_wmi               20480  0 
crc32_pclmul           16384  0 
cfg80211              540672  4 ath,ath9k_common,ath9k,mac80211
btusb                  32768  0 
sparse_keymap          16384  1 acer_wmi
ghash_clmulni_intel    16384  0 
snd_seq_midi           16384  0 
bluetooth             491520  23 bnep,ath3k,btusb,rfcomm
aesni_intel           172032  1 
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            32768  1 snd_seq_midi
snd_seq                69632  2 snd_seq_midi_event,snd_seq_midi
drm_kms_helper        122880  1 i915
drm                   344064  7 i915,drm_kms_helper,nvidia
aes_x86_64             20480  1 aesni_intel
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
lrw                    16384  1 aesni_intel
snd_timer              32768  2 snd_pcm,snd_seq
snd                    90112  13 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
gf128mul               16384  1 lrw
i2c_algo_bit           16384  1 i915
glue_helper            16384  1 aesni_intel
soundcore              16384  2 snd,snd_hda_codec
joydev                 20480  0 
mei_me                 20480  0 
shpchp                 40960  0 
ablk_helper            16384  1 aesni_intel
serio_raw              16384  0 
mei                    90112  1 mei_me
cryptd                 20480  3 ghash_clmulni_intel,aesni_intel,ablk_helper
lpc_ich                24576  0 
video                  20480  2 i915,acer_wmi
mac_hid                16384  0 
wmi                    20480  1 acer_wmi
parport_pc             32768  0 
ppdev                  20480  0 
lp                     20480  0 
parport                45056  3 lp,ppdev,parport_pc
autofs4                40960  2 
hid_generic            16384  0 
usbhid                 53248  0 
hid                   110592  2 hid_generic,usbhid
uas                    24576  0 
usb_storage            69632  4 uas
psmouse               118784  0 
tg3                   167936  0 
ahci                   36864  0 
sdhci_pci              24576  0 
ptp                    20480  1 tg3
libahci                32768  1 ahci
sdhci                  45056  1 sdhci_pci
pps_core               20480  1 ptp
```

Anyway I saw the ath9k and assumed it was installed. I may be dead wrong though; I'm still trying to learn. 

2. I tried ```
sudo ifconfig wlan0 up
``` and got an error saying Operation not possible due to RF-kill.

3. I tried a third method, which was to turn on the WiFi adapter itself. I suspected it was turned off because the first two methods didn't work, but there is no way I can confirm it because there is no indicator on the laptop that tells me the adapter is on. However, my keyboard is damaged, and I am currently using a USB keyboard. I need to use Fn+F3 on the original keyboard on the laptop to turn it on, but it is damaged, and the USB keyboard does not have the Fn key. I realised there was no way I could map the Fn key to the useless Windows key on the USB keyboard anyway. So even if ti were off, I can't turn it on.

4. The fourth method was to try to turn it on through the BIOS. However, there was no way I could access the settings; it wasn't because of the need for a password, but because a dialog box with general help kept appearing, and pressing Enter (to continue) ends up reopening the same General Help box. I've attached a picture to show what it looks like when I tried to accessed BIOS. I know this problem has nothing to do with Lubuntu, since it was already like that before I installed, and it certainly gave me a hard time not being able to change the boot order to install Lubuntu. I'm just stating this here to show that I have tried a third method, but there was no way I could get around it (I think).

[ATTACH=CONFIG]262877[/ATTACH]

5. Under Additional Drivers, there's a device which remains unrecognised by Lubuntu. I'm not sure if it refers to the network adapter, since no other information is given. I've attached a picture of this as well. I have tried using the other driver, and then applying the changes, but after a while the selection reverts to the original selection (Do not use this device) and no error message was provided.

[ATTACH=CONFIG]262878[/ATTACH]

6. Finally, this computer doesn't have Windows installed... My original hard drive was physically damaged, and I installed Lubuntu on an external hard drive. I also saw methods to access Windows and turn the adapter on... Well that is impossible for me (at least I think). 

So, is there a way for me to actually configure wireless connections on this computer? I have no idea what is going on. Hope someone will be able to help me with this issue soon. I can't find alternative methods on turning the WiFi adapter on. Many thanks for any help provided.

---

### Post by uber2 on 2015-07-10
yeah that **** pissed me off for a while and then i got "Wicd Network manager" (wicked) it works in tandem with the native app. sometimes by itself, i haven't figured out how to remove or disable the native wifi controller but there is no real need with Wicd. more info [here]("https://help.ubuntu.com/community/WICD") - good luck

---

### Post by astralnysledz on 2015-08-17
For further information we would need the output of the following commands:
```
lspci -k
lsmod | grep ath
rfkill list
```

If your Atheros WiFi card is really hard-blocked, because a keyboard key was pressed, it should not even appear in the list of pci devices (lspci). Usually WiFi is the last position, though not always.

From your complete lsmod output I noticed you have both ath3k and ath9k loaded. The former is not necessary (unless you have an Ethernet card running with that module -> hence lspci -k needed!), so maybe try unloading it or unloading & blacklisting.

The last command will tell us whether the adapter is really hard-blocked.

---

### Post by Bucky Ball on 2015-08-17
Your posts will be shorter if you use code tags for terminal output. I've added them to your first post. I see you used them elsewhere so you probably just forgot. :)

---

