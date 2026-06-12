---
title: "Frequent deauthentication from Wifi (Reason: 6) in Ubuntu 14.04"
date: 2014-05-16
forum: Networking &amp; Wireless
---

### Post by derpthan on 2014-05-16
Hi!

[COLOR=#333333][FONT=UbuntuRegular]For a few days now, my wifi is getting disrupted every few minutes. I use a 'vanilla' Ubuntu installation (i.e Unity, NetworkManager etc.). After an hour or so, the connection gets severed completely and NetworkManager can't find the network anymore. Toggling "Enable Wi-Fi" in the NetworkManager-menu allows me to find and connect to the network again.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]This is an excerpt from /var/log/syslog:


```
[FONT=Ubuntu Mono]May 14 16:50:51 terminus kernel: [ 4208.006043] wlan0: deauthenticated from 00:24:fe:a3:98:f6 (Reason: 6)[/FONT]
```[/FONT][/COLOR]```

May 14 16:50:51 terminus wpa_supplicant[907]: wlan0: CTRL-EVENT-DISCONNECTED bssid=00:24:fe:a3:98:f6 reason=6
May 14 16:50:51 terminus NetworkManager[868]:  Connection disconnected (reason 6)
May 14 16:50:51 terminus wpa_supplicant[907]: wlan0: SME: Trying to authenticate with 00:24:fe:a3:98:f6 (SSID='FRITZ!Box Fon WLAN 7270' freq=2447 MHz)
May 14 16:50:51 terminus kernel: [ 4208.034507] cfg80211: Calling CRDA to update world regulatory domain
May 14 16:50:51 terminus kernel: [ 4208.035050] wlan0: authenticate with 00:24:fe:a3:98:f6
May 14 16:50:51 terminus kernel: [ 4208.042178] wlan0: send auth to 00:24:fe:a3:98:f6 (try 1/3)
May 14 16:50:51 terminus NetworkManager[868]:  (wlan0): supplicant interface state: completed -> authenticating
May 14 16:50:51 terminus wpa_supplicant[907]: wlan0: Trying to associate with 00:24:fe:a3:98:f6 (SSID='FRITZ!Box Fon WLAN 7270' freq=2447 MHz)
May 14 16:50:51 terminus kernel: [ 4208.042526] cfg80211: World regulatory domain updated:
May 14 16:50:51 terminus kernel: [ 4208.042533] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
May 14 16:50:51 terminus kernel: [ 4208.042539] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
May 14 16:50:51 terminus kernel: [ 4208.042543] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
May 14 16:50:51 terminus kernel: [ 4208.042547] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
May 14 16:50:51 terminus kernel: [ 4208.042550] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
May 14 16:50:51 terminus kernel: [ 4208.042554] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
May 14 16:50:51 terminus kernel: [ 4208.044622] wlan0: authenticated
May 14 16:50:51 terminus kernel: [ 4208.046291] wlan0: associate with 00:24:fe:a3:98:f6 (try 1/3)
May 14 16:50:51 terminus NetworkManager[868]:  (wlan0): supplicant interface state: authenticating -> associating
May 14 16:50:51 terminus kernel: [ 4208.056055] wlan0: RX AssocResp from 00:24:fe:a3:98:f6 (capab=0x431 status=0 aid=1)
May 14 16:50:51 terminus wpa_supplicant[907]: wlan0: Associated with 00:24:fe:a3:98:f6
May 14 16:50:51 terminus kernel: [ 4208.065893] wlan0: associated
May 14 16:50:51 terminus NetworkManager[868]:  (wlan0): supplicant interface state: associating -> 4-way handshake
May 14 16:50:51 terminus wpa_supplicant[907]: wlan0: WPA: Key negotiation completed with 00:24:fe:a3:98:f6 [PTK=CCMP GTK=TKIP]
May 14 16:50:51 terminus wpa_supplicant[907]: wlan0: CTRL-EVENT-CONNECTED - Connection to 00:24:fe:a3:98:f6 completed [id=0 id_str=]
May 14 16:50:51 terminus NetworkManager[868]:  (wlan0): supplicant interface state: 4-way handshake -> completed
May 14 16:51:55 terminus wpa_supplicant[907]: wlan0: CTRL-EVENT-SCAN-STARTED 
May 14 16:52:27 terminus kernel: [ 4304.188238] wlan0: deauthenticated from 00:24:fe:a3:98:f6 (Reason: 6)
May 14 16:52:27 terminus wpa_supplicant[907]: wlan0: CTRL-EVENT-DISCONNECTED bssid=00:24:fe:a3:98:f6 reason=6
May 14 16:52:27 terminus NetworkManager[868]:  Connection disconnected (reason 6)
May 14 16:52:27 terminus wpa_supplicant[907]: wlan0: SME: Trying to authenticate with 00:24:fe:a3:98:f6 (SSID='FRITZ!Box Fon WLAN 7270' freq=2447 MHz)
May 14 16:52:27 terminus kernel: [ 4304.215024] cfg80211: Calling CRDA to update world regulatory domain
May 14 16:52:27 terminus kernel: [ 4304.215540] wlan0: authenticate with 00:24:fe:a3:98:f6
May 14 16:52:27 terminus NetworkManager[868]:  (wlan0): supplicant interface state: completed -> authenticating
May 14 16:52:27 terminus wpa_supplicant[907]: wlan0: Trying to associate with 00:24:fe:a3:98:f6 (SSID='FRITZ!Box Fon WLAN 7270' freq=2447 MHz)
May 14 16:52:27 terminus kernel: [ 4304.219680] wlan0: send auth to 00:24:fe:a3:98:f6 (try 1/3)
May 14 16:52:27 terminus kernel: [ 4304.222003] wlan0: authenticated
May 14 16:52:27 terminus kernel: [ 4304.222790] wlan0: associate with 00:24:fe:a3:98:f6 (try 1/3)
May 14 16:52:27 terminus kernel: [ 4304.223063] cfg80211: World regulatory domain updated:
May 14 16:52:27 terminus kernel: [ 4304.223072] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
May 14 16:52:27 terminus kernel: [ 4304.223078] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
May 14 16:52:27 terminus kernel: [ 4304.223083] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
May 14 16:52:27 terminus kernel: [ 4304.223087] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
May 14 16:52:27 terminus kernel: [ 4304.223090] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
May 14 16:52:27 terminus kernel: [ 4304.223094] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
May 14 16:52:27 terminus kernel: [ 4304.226833] wlan0: RX AssocResp from 00:24:fe:a3:98:f6 (capab=0x431 status=0 aid=1)
May 14 16:52:27 terminus NetworkManager[868]:  (wlan0): supplicant interface state: authenticating -> associating
May 14 16:52:27 terminus wpa_supplicant[907]: wlan0: Associated with 00:24:fe:a3:98:f6
May 14 16:52:27 terminus kernel: [ 4304.232953] wlan0: associated
May 14 16:52:27 terminus NetworkManager[868]:  (wlan0): supplicant interface state: associating -> 4-way handshake
May 14 16:52:27 terminus wpa_supplicant[907]: wlan0: WPA: Key negotiation completed with 00:24:fe:a3:98:f6 [PTK=CCMP GTK=TKIP]
May 14 16:52:27 terminus wpa_supplicant[907]: wlan0: CTRL-EVENT-CONNECTED - Connection to 00:24:fe:a3:98:f6 completed [id=0 id_str=]
May 14 16:52:27 terminus NetworkManager[868]:  (wlan0): supplicant interface state: 4-way handshake -> completed
May 14 16:53:55 terminus wpa_supplicant[907]: wlan0: CTRL-EVENT-SCAN-STARTED 
May 14 16:54:00 terminus wpa_supplicant[907]: nl80211: send_and_recv->nl_recvmsgs failed: -33 [COLOR=#333333][FONT=UbuntuRegular][FONT=Ubuntu Mono]May 14 16:54:05 terminus wpa_supplicant[907]: wlan0: WPA: Group rekeying completed with 00:24:fe:a3:98:f6 [GTK=TKIP][/FONT][/FONT][/COLOR]
```[COLOR=#333333][FONT=UbuntuRegular]

[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Other relevant information:[/FONT][/COLOR]
```

root@terminus:~# lshw -c network
  *-network               
       description: Wireless interface
       product: Centrino Advanced-N 6230 [Rainbow Peak]
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 34
       serial: 88:53:2e:42:0b:71
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.13.0-24-generic firmware=18.168.6.1 ip=192.168.3.22 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
       resources: irq:52 memory:f1b00000-f1b01fff

```


```

root@terminus:~# lsmod 
Module                  Size  Used by
btrfs                 835954  0 
raid6_pq               97812  1 btrfs
xor                    21411  1 btrfs
ufs                    74890  0 
qnx4                   13317  0 
hfsplus               107516  0 
hfs                    54677  0 
minix                  36140  0 
ntfs                   97369  0 
msdos                  17332  0 
jfs                   181348  0 
xfs                   912173  0 
libcrc32c              12644  2 xfs,btrfs
ctr                    13049  1 
ccm                    17773  1 
nls_iso8859_1          12713  0 
snd_hda_codec_hdmi     46207  1 
snd_hda_codec_realtek    61438  1 
joydev                 17381  0 
intel_rapl             18773  0 
x86_pkg_temp_thermal    14205  0 
intel_powerclamp       14705  0 
coretemp               13435  0 
kvm_intel             143060  0 
kvm                   451511  1 kvm_intel
dell_laptop            18168  0 
dcdbas                 14928  1 dell_laptop
crct10dif_pclmul       14289  0 
crc32_pclmul           13113  0 
ghash_clmulni_intel    13259  0 
aesni_intel            55624  2 
uvcvideo               80885  0 
aes_x86_64             17131  1 aesni_intel
lrw                    13286  1 aesni_intel
gf128mul               14951  1 lrw
videobuf2_vmalloc      13216  1 uvcvideo
glue_helper            13990  1 aesni_intel
ablk_helper            13597  1 aesni_intel
videobuf2_memops       13362  1 videobuf2_vmalloc
cryptd                 20359  3 ghash_clmulni_intel,aesni_intel,ablk_helper
psmouse               102222  0 
videobuf2_core         40664  1 uvcvideo
serio_raw              13462  0 
videodev              134688  2 uvcvideo,videobuf2_core
rfcomm                 69160  8 
arc4                   12608  2 
bnep                   19624  2 
snd_hda_intel          52355  3 
iwldvm                232285  0 
snd_hda_codec         192906  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
mac80211              626489  1 iwldvm
nouveau              1097199  1 
snd_hwdep              13602  1 snd_hda_codec
snd_pcm               102099  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
btusb                  32412  0 
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
bluetooth             395423  22 bnep,btusb,rfcomm
iwlwifi               169932  1 iwldvm
snd_rawmidi            30144  1 snd_seq_midi
i915                  783485  3 
dell_wmi               12761  0 
lpc_ich                21080  0 
sparse_keymap          13948  1 dell_wmi
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
mxm_wmi                13021  1 nouveau
snd_timer              29482  2 snd_pcm,snd_seq
cfg80211              484040  3 iwlwifi,mac80211,iwldvm
ttm                    85115  1 nouveau
snd                    69238  17 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
drm_kms_helper         52758  2 i915,nouveau
wmi                    19177  3 dell_wmi,mxm_wmi,nouveau
drm                   302817  7 ttm,i915,drm_kms_helper,nouveau
i2c_algo_bit           13413  2 i915,nouveau
soundcore              12680  1 snd
mei_me                 18627  0 
mei                    82274  1 mei_me
mac_hid                13205  0 
video                  19476  2 i915,nouveau
parport_pc             32701  0 
ppdev                  17671  0 
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
hid_generic            12548  0 
usbhid                 52616  0 
hid                   106148  2 hid_generic,usbhid
usb_storage            62209  0 
ahci                   25819  1 
r8169                  67581  0 
libahci                32168  1 ahci
mii                    13934  1 r8169

```


[COLOR=#333333][FONT=UbuntuRegular]I guess it could be a hardware-related issue, but as far as I know, the problem does not occur on Windows (8, 64bit). However, since the reconnect is so fast on windows, I might have missed it so far.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Any idea what the issue could be? What is "Reason 6" and what can cause it? How can I debug the problem further?[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Thanks![/FONT][/COLOR]

---

### Post by Professor Frink on 2014-08-05
Did you ever resolve this?  I have the same issue

---

### Post by derpthan on 2014-08-06
No, so far I had no luck.
I posted this as well on askubuntu.com: [http://askubuntu.com/questions/465848/frequent-deauthentication-from-wifi-reason-6-in-ubuntu-14-04](http://askubuntu.com/questions/465848/frequent-deauthentication-from-wifi-reason-6-in-ubuntu-14-04).
There is also this thread with the same issue (i think): [http://askubuntu.com/questions/454427/network-issues-since-trusty/471458#471458](http://askubuntu.com/questions/454427/network-issues-since-trusty/471458#471458)

In short, you can try to disable draft-n wireless as described at the askubuntu thread. This lead to more infrequent deauthentications, but the issue still prevails.

I also tried to use an upstream kernel version ([https://wiki.ubuntu.com/Kernel/MainlineBuilds](https://wiki.ubuntu.com/Kernel/MainlineBuilds)) but had no success.

---

### Post by praseodym on 2014-08-06
Try to deactivate the N-mode and the queue of the network:
```

echo "options iwlwifi 11n_disable=1 wd_disable=1" | sudo tee /etc/modprobe.d/iwlwifi.conf
sudo modprobe -rfv iwlwifi
sudo modprobe -v iwlwifi
```
Reason 6 is: " class2FrameFromNonAuthStation - Client attempted to transfer data before it was authenticated. "

[http://wiki.ubuntuusers.de/WLAN#Logbucheintraege-auswerten](http://wiki.ubuntuusers.de/WLAN#Logbucheintraege-auswerten)

Try to change the ESSID to sth. without blanks (maybe othe Fritz!boxes are around?!). Check
```

sudo iwlist scan
```

---

