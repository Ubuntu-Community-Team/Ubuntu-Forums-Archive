---
title: "Intel Centrino Advanced-N 6235 / Ubuntu 12.04 LTS Wi-Fi Problem"
date: 2013-09-17
forum: Networking &amp; Wireless
---

### Post by Dibyajit on 2013-09-17
My HP ProBook 4440s with Ubuntu 12.04 is unable to connect to the internet through wi-fi. When I try to connect, it asks for my log-in crednetials every 2 minutes, but is unable to connect.
The following are the codes:
```
kiit@kiit-HP-ProBook-4440s:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.2 LTS"
Linux kiit-HP-ProBook-4440s 3.2.0-29-generic-pae #46-Ubuntu SMP Fri Jul 27 17:25:43 UTC 2012 i686 i686 i386 GNU/Linux
kiit@kiit-HP-ProBook-4440s:~$ 
kiit@kiit-HP-ProBook-4440s:~$ lspci -nnk | grep -iA2 net
03:00.0 Network controller [0280]: Intel Corporation Centrino Advanced-N 6235 [8086:088e] (rev 24)
    Subsystem: Intel Corporation Centrino Advanced-N 6235 AGN [8086:4060]
    Kernel driver in use: iwlwifi
--
04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 07)
    Subsystem: Hewlett-Packard Company Device [103c:17f3]
    Kernel driver in use: r8169
kiit@kiit-HP-ProBook-4440s:~$ 
kiit@kiit-HP-ProBook-4440s:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 002: ID 046d:c52f Logitech, Inc. Wireless Mouse M305
Bus 001 Device 003: ID 138a:003d Validity Sensors, Inc. 
Bus 001 Device 004: ID 04f2:b372 Chicony Electronics Co., Ltd 
Bus 002 Device 003: ID 8087:07da Intel Corp. 
kiit@kiit-HP-ProBook-4440s:~$ 
kiit@kiit-HP-ProBook-4440s:~$ iwconfig
lo        no wireless extensions.


wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
eth0      no wireless extensions.


kiit@kiit-HP-ProBook-4440s:~$ 
kiit@kiit-HP-ProBook-4440s:~$ rfkill list all
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
3: hp-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
kiit@kiit-HP-ProBook-4440s:~$ 
kiit@kiit-HP-ProBook-4440s:~$ lsmod
Module                  Size  Used by
snd_hda_codec_hdmi     31775  1 
snd_hda_codec_idt      60251  1 
parport_pc             32114  0 
ppdev                  12849  0 
rfcomm                 38139  12 
bnep                   17830  2 
binfmt_misc            17292  1 
arc4                   12473  2 
hp_wmi                 13652  0 
sparse_keymap          13658  1 hp_wmi
snd_hda_intel          32765  3 
snd_hda_codec         109562  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80845  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
hp_accel               25728  0 
lis3lv02d              19268  1 hp_accel
input_polldev          13648  1 lis3lv02d
psmouse                72919  0 
serio_raw              13027  0 
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
btusb                  17912  2 
bluetooth             158438  23 rfcomm,bnep,btusb
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
wmi                    18744  1 hp_wmi
uvcvideo               67203  0 
videodev               86588  1 uvcvideo
jmb38x_ms              17406  0 
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
memstick               15857  1 jmb38x_ms
iwlwifi               291907  0 
mac80211              436455  1 iwlwifi
snd                    62064  16 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i915                  414739  3 
soundcore              14635  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
joydev                 17393  0 
mac_hid                13077  0 
cfg80211              178679  2 iwlwifi,mac80211
mei                    36570  0 
drm_kms_helper         45466  1 i915
drm                   197692  4 i915,drm_kms_helper
i2c_algo_bit           13199  1 i915
video                  19068  1 i915
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usbhid                 41906  0 
hid                    77367  1 usbhid
r8169                  56321  0 
sdhci_pci              18324  0 
sdhci                  28241  1 sdhci_pci



```
Can anyone please help? The Wi-fi works just fine with Windows 7, but Ubuntu just does not manage to connect.

---

### Post by Hadaka on 2013-09-17
Hi, give this a read and see if it helps
[http://ubuntuforums.org/showthread.php?t=1996768](http://ubuntuforums.org/showthread.php?t=1996768)
thanks.

---

### Post by Dibyajit on 2013-09-17
Thanks, but what am I supposed to do from the link you gave? Should I use the codes in that page on my machine?

---

### Post by Hadaka on 2013-09-17
Yes...do this first..
```
sudo modprobe -r iwlwifi
sudo modprobe iwlwifi 11n_disable=1
```
Don't boot..test to see if this fixes your problem.
*IF and only if it does..then to make the fix permanent
then do..
```
sudo gedit /etc/modprobe.d/iwlwifi.conf
```
add this one line..
```
options iwlwifi 11n_disable=1
```
save and close gedit...boot

---

### Post by Dibyajit on 2013-09-17
Nope.. Sorry, but this doesn't seem to work. It continues to ask for my credentials every two minutes and is unable to connect to the net. Any other suggestions?

---

### Post by Hadaka on 2013-09-17
Hi,have you checked your network manager wireless settings?
as in edit your connection and verify all is correct?

---

### Post by mörgæs on 2013-09-18
New hardware and old software is a bad combination. 

A number of bug fixes has been added in 12.10 and 13.04, for example
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1180256](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1180256)

As a first step I would recommend 13.04 (or 13.10 beta, if you want to see what the near future will bring).

---

### Post by Dibyajit on 2013-09-19
> [COLOR=#000000]Hi,have you checked your network manager wireless settings?[/COLOR]
[COLOR=#000000]as in edit your connection and verify all is correct?[/COLOR]
Ya, I have checked it, and all is well. I can say this as it used to work earlier with another wi-fi router. The earlier router had a WEP type security, but this one has a WPA2-Enterprise type security. That is about all the difference that I can find between the two.

> [COLOR=#000000]New hardware and old software is a bad combination. [/COLOR]

[COLOR=#000000]A number of bug fixes has been added in 12.10 and 13.04, for example[/COLOR]
[https://bugs.launchpad.net/ubuntu/+s...x/+bug/1180256]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1180256")

[COLOR=#000000]As a first step I would recommend 13.04 (or 13.10 beta, if you want to see what the near future will bring).[/COLOR]
I understand, but to get that update, I need to get connected to the internet. I can download the file from Windows, but I don't know how to install the file without removing my Windows 7 version.

---

### Post by mörgæs on 2013-09-19
You can download the 13.04 ISO in Windows or Buntu as you prefer. Unetbootin, which creates the USB stick, also works in both. 

Please post again when you have that working.

---

### Post by Dibyajit on 2013-10-09
Sorry for the late reply, got busy...
Yeah, I have that iso file and the disc image up and running. There are a few folders and there is a wubi.exe file. Some autorun file is also there. I ran the wubi application, but it is asking me to choose where to create the ubuntu partition. I want to replace my ubuntu 12.04 with this new version. So, what do I do? Do I install it with a new partition or do I have to free up my previous ubuntu partition. If so, how?

---

### Post by mörgæs on 2013-10-09
Your existing install is not Wubi, is it?

---

### Post by Dibyajit on 2013-10-10
I have windows and ubuntu installed, so I guess it it wubi...

---

### Post by mörgæs on 2013-10-10
If Buntu is next to Windows it's a dual boot. If Buntu runs within Windows you are using Wubi.

---

### Post by varunendra on 2013-10-10
> **Dibyajit said:**
> but this one has a WPA2-Enterprise type security.

Please check -
```
sudo cat /etc/NetworkManager/system-connections/<your connection's name>
```
..and see if there is a line "system-ca-certs=true". If there is, you need to change it to "false" -
```
sudo sed -i '/system-ca-certs/ s:[Tt]rue:false:' /etc/NetworkManager/system-connections/<your connection name>
```

Recheck with the first command to make sure it changed to "false", then try connecting again.

**PS:**
Although it does not change the matters with wifi, it is highly recommended to do a proper installation, not WUBI. WUBI breaks often with a potential loss of data (within the Ubuntu virtual disk).

---

