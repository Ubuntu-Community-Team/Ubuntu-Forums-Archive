---
title: "How to make USB wireless antenna work?"
date: 2013-11-17
forum: Networking &amp; Wireless
---

### Post by rva1945 on 2013-11-17
As the laptop (Lenovo G560) now refuses to connect via its internal wireles antenna, I want to use a USB TP-Link TL-WN722N, that runs fine in a W7.

I remember it was plugged in a desktop PC when I installed Ubuntu 12.04 using the Live CD, the antenna was detected during installation and then it has been working ok in Ubuntu.

But now it seems not to be detected by an already installed Ubuntu 12.04 that never used that USB wireless antenna.

I tried to use it in a live Ubuntu but no, it will be detected only during installation.

So, how do I make it run without re-installing Ubuntu?

---

### Post by praseodym on 2013-11-17
Please show the terminal outputs of these commands:
```

uname -a
lspci -nnk | grep -iA2 net
lsusb # with the stick plugged in
lsmod
iwconfig
rfkill list
cat /etc/resolv.conf
```

---

### Post by rva1945 on 2013-11-17
Ok, here it goes (all with the stick plugged in):

uname -a
Linux robert-Lenovo-G560 3.2.0-56-generic-pae #86-Ubuntu SMP Wed Oct 23 17:51:27 UTC 2013 i686 i686 i386 GNU/Linux

lspci -nnk | grep -iA2 net
05:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)
	Subsystem: Broadcom Corporation Device [14e4:0510]
	Kernel driver in use: wl
--
06:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
	Subsystem: Lenovo Device [17aa:392e]
	Kernel driver in use: r8169

lsusb #
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 006: ID 0cf3:9271 Atheros Communications, Inc. AR9271 802.11n
Bus 002 Device 004: ID 04f2:b1c1 Chicony Electronics Co., Ltd 
Bus 002 Device 005: ID 0458:003a KYE Systems Corp. (Mouse Systems) NetScroll+ Mini Traveler / Genius NetScroll 120

lsmod
Module                  Size  Used by
arc4                   12473  2 
joydev                 17393  0 
ath9k_htc              90811  0 
mac80211              436493  1 ath9k_htc
ath9k_common           13781  1 ath9k_htc
snd_hda_codec_hdmi     31775  1 
snd_hda_codec_conexant    52521  1 
ath9k_hw              391626  2 ath9k_htc,ath9k_common
ath                    19387  3 ath9k_htc,ath9k_common,ath9k_hw
parport_pc             32114  0 
ppdev                  12849  0 
rfcomm                 38139  0 
bnep                   17830  2 
bluetooth             158447  10 rfcomm,bnep
lib80211_crypt_tkip    17275  0 
snd_hda_intel          32719  3 
snd_hda_codec         109562  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80916  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
binfmt_misc            17292  1 
wl                   2906597  0 
psmouse                86546  0 
i915                  428127  3 
uvcvideo               67203  0 
drm_kms_helper         45466  1 i915
drm                   197641  4 i915,drm_kms_helper
serio_raw              13027  0 
videodev               86588  1 uvcvideo
i2c_algo_bit           13199  1 i915
intel_ips              17822  0 
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
cfg80211              178877  4 ath9k_htc,mac80211,ath,wl
snd                    62218  16 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
lib80211               14040  2 lib80211_crypt_tkip,wl
ideapad_laptop         17890  0 
sparse_keymap          13658  1 ideapad_laptop
soundcore              14635  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
mei                    36570  0 
video                  19115  1 i915
wmi                    18744  0 
mac_hid                13077  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usbhid                 41937  0 
hid                    77428  1 usbhid
r8169                  56396  0 

iwconfig
lo        no wireless extensions.


wlan1     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
eth1      IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
eth0      no wireless extensions.

rfkill list
0: ideapad_wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: brcmwl-0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
3: phy2: Wireless LAN
	Soft blocked: no
	Hard blocked: no

cat /etc/resolv.conf
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 192.168.1.1

---

### Post by praseodym on 2013-11-17
Your wireless is "hard blocked", any button/switch/key/key combination? Please also check here for this:

[http://ubuntuforums.org/showthread.php?t=2111690&p=12490285#post12490285](http://ubuntuforums.org/showthread.php?t=2111690&p=12490285#post12490285)

For your internal card, see here:

[http://ubuntuforums.org/showthread.php?t=2188193&p=12850102#post12850102](http://ubuntuforums.org/showthread.php?t=2188193&p=12850102#post12850102)

For the stick, deactivate the hardware encryption:
```

echo "options ath9k_htc nohwcrypt=1" | sudo tee -a /etc/modprobe.d/ath9k.conf
sudo modprobe -rfv ath9k_htc
sudo modprobe -v ath9k_htc
```

---

### Post by rva1945 on 2013-11-17
I know that the internal wireless is not working, it is enabled in BIOS and the Fn+F5 option does nothing.

I ran the commands for the stick and got this:

echo "options ath9k_htc nohwcrypt=1" | sudo tee -a /etc/modprobe.d/ath9k.conf
[sudo] password for robert: 
options ath9k_htc nohwcrypt=1
robert@robert-Lenovo-G560:~$ sudo modprobe -rfv ath9k_htc
rmmod /lib/modules/3.2.0-56-generic-pae/kernel/drivers/net/wireless/ath/ath9k/ath9k_htc.ko
rmmod /lib/modules/3.2.0-56-generic-pae/kernel/net/mac80211/mac80211.ko
rmmod /lib/modules/3.2.0-56-generic-pae/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
rmmod /lib/modules/3.2.0-56-generic-pae/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
rmmod /lib/modules/3.2.0-56-generic-pae/kernel/drivers/net/wireless/ath/ath.ko
robert@robert-Lenovo-G560:~$ sudo modprobe -v ath9k_htc
insmod /lib/modules/3.2.0-56-generic-pae/kernel/drivers/net/wireless/ath/ath.ko 
insmod /lib/modules/3.2.0-56-generic-pae/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko 
insmod /lib/modules/3.2.0-56-generic-pae/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko 
insmod /lib/modules/3.2.0-56-generic-pae/kernel/net/mac80211/mac80211.ko 
insmod /lib/modules/3.2.0-56-generic-pae/kernel/drivers/net/wireless/ath/ath9k/ath9k_htc.ko nohwcrypt=1

and it is frozen in that last line.

The stick is plugged, should I ran those commands without it being plugged?

---

### Post by praseodym on 2013-11-17
Update all the drivers after uninstalling the STA via:
```

sudo apt-get install linux-backports-modules-cw-3.6-precise-generic-pae build-essential linux-headers-generic-pae
```
Reboot. Check after that
```

lsmod
iwconfig
rfkill list
```

---

### Post by rva1945 on 2013-11-17
What will this fix? The issue with the USB wireless antenna or the problem with the internal antenna?

---

### Post by praseodym on 2013-11-17
The internal one. The module parameter should fix the USB

---

### Post by rva1945 on 2013-11-17
Done. This is the output after the commands:

lsmod
Module                  Size  Used by
joydev                 17393  0 
arc4                   12473  2 
ath9k_htc              90811  0 
rfcomm                 38139  0 
mac80211              436493  1 ath9k_htc
parport_pc             32114  0 
bnep                   17830  2 
ppdev                  12849  0 
bluetooth             158447  10 rfcomm,bnep
ath9k_common           13781  1 ath9k_htc
ath9k_hw              391626  2 ath9k_htc,ath9k_common
snd_hda_codec_hdmi     31775  1 
snd_hda_codec_conexant    52521  1 
ath                    19387  3 ath9k_htc,ath9k_common,ath9k_hw
binfmt_misc            17292  1 
uvcvideo               67203  0 
psmouse                86546  0 
videodev               86588  1 uvcvideo
serio_raw              13027  0 
ideapad_laptop         17890  0 
sparse_keymap          13658  1 ideapad_laptop
wmi                    18744  0 
snd_hda_intel          32719  3 
snd_hda_codec         109562  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80916  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
lib80211_crypt_tkip    17275  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
wl                   2906597  0 
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
i915                  428127  3 
intel_ips              17822  0 
mac_hid                13077  0 
cfg80211              178877  4 ath9k_htc,mac80211,ath,wl
drm_kms_helper         45466  1 i915
snd                    62218  16 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm                   197641  4 i915,drm_kms_helper
lib80211               14040  2 lib80211_crypt_tkip,wl
soundcore              14635  1 snd
i2c_algo_bit           13199  1 i915
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
video                  19115  1 i915
mei                    36570  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usbhid                 41937  0 
hid                    77428  1 usbhid
r8169                  56396  0 

iwconfig
lo        no wireless extensions.


wlan1     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
eth1      IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
eth0      no wireless extensions.

rfkill list
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: brcmwl-0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: ideapad_wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
3: phy1: Wireless LAN
	Soft blocked: yes
	Hard blocked: no

what next?

---

### Post by rva1945 on 2013-11-17
Anyway I ran the commands without rebooting, now I did it after reboot and this is the output:

lsmod
Module                  Size  Used by
joydev                 17393  0 
arc4                   12473  2 
snd_hda_codec_hdmi     31775  1 
snd_hda_codec_conexant    52521  1 
rfcomm                 37433  0 
bnep                   17711  2 
bluetooth             183359  10 rfcomm,bnep
parport_pc             32114  0 
ppdev                  12849  0 
ath9k_htc              85330  0 
mac80211              474589  1 ath9k_htc
binfmt_misc            17292  1 
ath9k_common           13781  1 ath9k_htc
ath9k_hw              376205  2 ath9k_htc,ath9k_common
ath                    19187  3 ath9k_htc,ath9k_common,ath9k_hw
snd_hda_intel          32719  3 
snd_hda_codec         109562  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80916  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
uvcvideo               67203  0 
videodev               86588  1 uvcvideo
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
ideapad_laptop         17890  0 
psmouse                86546  0 
sparse_keymap          13658  1 ideapad_laptop
serio_raw              13027  0 
snd                    62218  16 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cfg80211              188000  3 ath9k_htc,mac80211,ath
wmi                    18744  0 
lib80211               14040  0 
compat                 19507  9 rfcomm,bnep,bluetooth,ath9k_htc,mac80211,ath9k_common,ath9k_hw,cfg80211,lib80211
i915                  428127  3 
drm_kms_helper         45466  1 i915
mei                    36570  0 
drm                   197641  4 i915,drm_kms_helper
intel_ips              17822  0 
i2c_algo_bit           13199  1 i915
soundcore              14635  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
video                  19115  1 i915
mac_hid                13077  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usbhid                 41937  0 
hid                    77428  1 usbhid
r8169                  56396  0 

iwconfig
lo        no wireless extensions.


wlan1     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
eth0      no wireless extensions.

rfkill list
0: ideapad_wlan: Wireless LAN
	Soft blocked: yes
	Hard blocked: yes
1: phy0: Wireless LAN
	Soft blocked: yes
	Hard blocked: no

still no wireless.

---

### Post by praseodym on 2013-11-17
Blacklist the following module```

echo "blacklist brcm80211" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
Reboot and
```

sudo rfkill unblock all
rfkill list
```
Check the BIOS-reset options

---

### Post by rva1945 on 2013-11-17
I followed the steps, blacklist, reboot, unblock and

rfkill list
0: ideapad_wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: yes

---

### Post by rva1945 on 2013-11-17
WOW to my surprise, I plugged the stick and I am now connected with the USB antenna.
I will now reboot with the stick plugged to see what happens.

Thanks

---

### Post by rva1945 on 2013-11-17
rfkill list gives
0: ideapad_wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
3: phy2: Wireless LAN
	Soft blocked: no
	Hard blocked: no

they I press Fn + F5, that should switch wireless off/on, the LED remains off but now rfkill list gives
0: ideapad_wlan: Wireless LAN
	Soft blocked: yes
	Hard blocked: yes
3: phy2: Wireless LAN
	Soft blocked: yes
	Hard blocked: no

and so again if I press Fn+F5 keys.

But no wireless.

AS told, in a moment the stick was working but it stopped working after rebooting, and no way to make it work again. This is so sad, the laptop had been working ok for a couple of years, then suddenly no more wireless.

---

### Post by rva1945 on 2013-11-17
iwconfig
wlan2     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
lo        no wireless extensions.


eth0      no wireless extensions.

then

sudo ifconfig wlan2 up
and the usb stick light turns on, but it remains on, no blinking, no network activity, and no wireless. I think I have to do something to make it connect.

---

### Post by praseodym on 2013-11-17
Try to permanently press Fn+F5 during boot-up or, alternatively, repeatedly

---

