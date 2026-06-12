---
title: "trouble netwoking 10.4 lts on PC to 11.4 on netbook, suggestions/"
date: 2011-07-23
forum: New to Ubuntu
---

### Post by SUperougi on 2011-07-23
[SIZE=2]I have a PC with 10.4 LTS installed and working good and a Netbook with 11.4 installed also working good. Trying to connect  netbook wireless to wired PC through Belkin N router. Tried using the wizard but no help, tried doing it manually but still no go. Need some new ideas. Thanks in advance.[/SIZE]

---

### Post by wildmanne39 on 2011-07-23
Hi, run these commands in terminal please
```
lspci -nn | grep 0280
```
```
lsmod
```
```
iwconfig
```
```
rfkill list All
```
and post the outcome  here by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by SUperougi on 2011-07-24
[SIZE=2]OK, Which computer?[/SIZE]

---

### Post by SUperougi on 2011-07-24
[SIZE=2]Signing off shortly will work on it tomorrow. Will post results tomorrow.[/SIZE]

---

### Post by SUperougi on 2011-07-24
Netbook Info
#[doug@ubuntu:~$ lspci -nn | grep 0280
02:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
doug@ubuntu:~$ lsmod
Module                  Size  Used by
cryptd                 20510  0 
aes_x86_64             17208  2 
aes_generic            38279  1 aes_x86_64
binfmt_misc            17565  1 
parport_pc             36959  0 
ppdev                  17113  0 
snd_hda_codec_realtek   336771  1 
snd_hda_intel          33211  2 
snd_hda_codec         103804  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13604  1 snd_hda_codec
arc4                   12529  2 
snd_pcm                96391  2 snd_hda_intel,snd_hda_codec
ath9k                 118238  0 
snd_seq_midi           13324  0 
snd_rawmidi            30486  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
mac80211              294370  1 ath9k
snd_timer              29602  2 snd_pcm,snd_seq
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
i915                  514975  3 
ath9k_common           13851  1 ath9k
joydev                 17606  0 
snd                    67382  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ath9k_hw              323077  2 ath9k,ath9k_common
drm_kms_helper         42136  1 i915
uvcvideo               72195  0 
psmouse                73535  0 
ath                    23773  2 ath9k,ath9k_hw
videodev               82052  1 uvcvideo
drm                   227495  4 i915,drm_kms_helper
soundcore              12680  1 snd
v4l2_compat_ioctl32    17078  1 videodev
cfg80211              178528  3 ath9k,mac80211,ath
serio_raw              13166  0 
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13400  1 i915
video                  19438  1 i915
lp                     17825  0 
parport                46458  3 parport_pc,ppdev,lp
ahci                   25951  1 
libahci                26642  1 ahci
atl1c                  41171  0 
doug@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"home 3"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:22:75:CD:B0:26   
          Bit Rate=150 Mb/s   Tx-Power=13 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=57/70  Signal level=-53 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:6  Invalid misc:0   Missed beacon:0

doug@ubuntu:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
doug@ubuntu:~$ ^C
doug@ubuntu:~$ ^C
doug@ubuntu:~$ ]

---

### Post by wildmanne39 on 2011-07-24
Hi, I need to clarify something. The one your are trying to get the wireless working on does it connect to the internet? is it just a matter of trying to get it to share data with the other computer? If that is the case then I can not help you with that.

If you need to get the wireless working to get to the internet then I can help.

---

### Post by SUperougi on 2011-07-24
I can get on the net with either computer, wired or wirelessly. I would like to get both computers to talk to each other. I understand you can not help me with this, Thanks for you help.

---

### Post by SUperougi on 2011-08-02
I still need some help with this one. Suggestions anyone? Thanks

---

