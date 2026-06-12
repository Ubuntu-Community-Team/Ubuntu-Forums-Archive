---
title: "Blutooth not working Lenovo G580"
date: 2014-08-15
forum: Networking &amp; Wireless
---

### Post by Ankush_Menat on 2014-08-15
Blutooth is listed under system settings, but whenever I turn on it just shows switch toggled. If I go to menu again its disabled. I do have bluetooh. It worked fine on Windows 7. I highly need Bluetooth tomorrow ( for presentation). Here is the out put of LSPCI and LSUSB for referance.

00:00.0 Host bridge: Intel Corporation 3rd Gen Core processor DRAM Controller (rev 09)00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4)
00:1c.1 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 2 (rev c4)
00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation HM76 Express Chipset LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller (rev 04)
01:00.0 Ethernet controller: Qualcomm Atheros AR8162 Fast Ethernet (rev 10)
02:00.0 Network controller: Qualcomm Atheros AR9485 Wireless Network Adapter (rev 01)
ankush@ankush-Lenovo-G580:~$ lsusb
Bus 002 Device 003: ID 174f:1148 Syntek 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0

Ubuntu update centre shows its 100% up-to date. Driver section is not showing any additional drivers.

---

### Post by ahmade-usa-170 on 2014-08-15
i cant find bluetooth in that list can you do lsmod and post the content?

---

### Post by Ankush_Menat on 2014-08-15
```
ankush@ankush-Lenovo-G580:~$ lsmod
Module                  Size  Used by
thinkpad_acpi          81013  0 
nvram                  14411  1 thinkpad_acpi
ctr                    13049  2 
ccm                    17773  2 
rfcomm                 69160  0 
bnep                   19624  2 
bluetooth             391196  10 bnep,rfcomm
rts5139               335409  0 
uvcvideo               80885  0 
binfmt_misc            17468  1 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
videobuf2_core         40664  1 uvcvideo
videodev              134688  2 uvcvideo,videobuf2_core
snd_hda_codec_hdmi     46254  1 
snd_hda_codec_conexant    57441  1 
intel_rapl             18773  0 
x86_pkg_temp_thermal    14205  0 
intel_powerclamp       14705  0 
coretemp               13435  0 
kvm_intel             143060  0 
snd_hda_intel          52355  3 
kvm                   451511  1 kvm_intel
snd_hda_codec         192906  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
arc4                   12608  2 
crct10dif_pclmul       14289  0 
ath9k                 164164  0 
crc32_pclmul           13113  0 
ghash_clmulni_intel    13216  0 
ath9k_common           13551  1 ath9k
ath9k_hw              453856  2 ath9k_common,ath9k
aesni_intel            55624  4 
aes_x86_64             17131  1 aesni_intel
snd_pcm               102099  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30144  1 snd_seq_midi
lrw                    13286  1 aesni_intel
gf128mul               14951  1 lrw
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
ath                    28698  3 ath9k_common,ath9k,ath9k_hw
snd_timer              29482  2 snd_pcm,snd_seq
mei_me                 18627  0 
mac80211              630653  1 ath9k
cfg80211              484040  3 ath,ath9k,mac80211
mei                    82276  1 mei_me
snd                    69238  18 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,thinkpad_acpi,snd_seq_device,snd_seq_midi
glue_helper            13990  1 aesni_intel
i915                  834436  4 
drm_kms_helper         55228  1 i915
drm                   300270  6 i915,drm_kms_helper
ablk_helper            13597  1 aesni_intel
cryptd                 20359  3 ghash_clmulni_intel,aesni_intel,ablk_helper
i2c_algo_bit           13413  1 i915
lpc_ich                21080  0 
ideapad_laptop         18216  0 
sparse_keymap          13948  1 ideapad_laptop
joydev                 17381  0 
mac_hid                13205  0 
parport_pc             32701  0 
serio_raw              13462  0 
video                  19476  1 i915
soundcore              12680  1 snd
ppdev                  17671  0 
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
hid_generic            12548  0 
usbhid                 52570  0 
hid                   106148  2 hid_generic,usbhid
psmouse               106678  0 
ahci                   25819  2 
alx                    32452  0 
libahci                32560  1 ahci
mdio                   13807  1 alx
```

---

### Post by ahmade-usa-170 on 2014-08-15
it says the bluetooth module is there try doing 
```
 sudo modprobe bluetooth 
```
to try and test it

---

### Post by Ankush_Menat on 2014-08-15
Sorry but nothing happens with this command. Went to settings to test if it works... still not working.

btw thanks for quick reply. I never got such fast reply from windows community. wink wink

---

### Post by ahmade-usa-170 on 2014-08-15
by nothing do you mean something like this 
```
 root@steamos:/home/desktop# modprobe ndiswrapper
root@steamos:/home/desktop# 


```
if so then the moudle is working
never knew there was a windows community i though they all were cracked ;)

---

### Post by donkeyoatmeal on 2014-08-15
Have you looked here? [https://help.ubuntu.com/community/BluetoothSetup](https://help.ubuntu.com/community/BluetoothSetup)

---

### Post by ahmade-usa-170 on 2014-08-15
was going to suggest that after seeing if the moudle worked or not :P

---

### Post by Ankush_Menat on 2014-08-15
> **ahmade-usa-170 said:**
> by nothing do you mean something like this 
```
 root@steamos:/home/desktop# modprobe ndiswrapper
root@steamos:/home/desktop# 


```
if so then the moudle is working
never knew there was a windows community i though they all were cracked ;)

see attached screenshot

---

### Post by Ankush_Menat on 2014-08-15
> **donkeyoatmeal said:**
> Have you looked here? [https://help.ubuntu.com/community/BluetoothSetup](https://help.ubuntu.com/community/BluetoothSetup)

Not worked for me.

---

### Post by ahmade-usa-170 on 2014-08-15
is it sorted out or do you still need help?

---

### Post by jeremy31 on 2014-08-15
I would be looking for a USB Bluetooth dongle for the presentation, as the bluetooth with the atheros is very troubled but it could be related to Lenovo.  I get lucky with mine every once in a while and it will actually work

When it doesn't work, I see errors like these on the screen during boot
```
[   39.472043] ideapad_laptop: timeout in write_ec_cmd[   39.576144] ideapad_laptop: timeout in write_ec_cmd
```
```
[   46.491770] Bluetooth: hci0 command 0x0c56 tx timeout
[   48.497951] Bluetooth: hci0 command 0x0c45 tx timeout
```

But even then it is listed in lsusb as ```
Bus 003 Device 007: ID 0cf3:3004 Atheros Communications, Inc. 
```

---

### Post by ahmade-usa-170 on 2014-08-15
oops

---

### Post by jeremy31 on 2014-08-16
You could try ```
sudo modprobe -rv thinkpad_acpi
``` and see if the bluetooth shows up in ```
hcitool dev
``` or ```
hcitool scan
```  Mine Lenovo G710 uses the ideapad_laptop module and removing it got the bluetooth so hcitool could find it and scan

But unless you can modprobe in bluetooth, btusb, and ath3k it still may not work

---

### Post by Ankush_Menat on 2014-08-24
Sorry for late reply. I found that if wifi or bluetooth is disabled by Lenovo power management under Windows, They dont work on Ubuntu at all (not get detected) 


Its working now

Cheers foss community. Thanks.

---

### Post by Ankush_Menat on 2014-08-24
presentations with Impress remote are working flawless :guitar:

---

### Post by jeremy31 on 2014-08-24
Nice to hear.  I wonder about that Lenovo power management in Windows though because I didn't have mine 30 minutes and Windows was gone and I can't say I miss it

---

