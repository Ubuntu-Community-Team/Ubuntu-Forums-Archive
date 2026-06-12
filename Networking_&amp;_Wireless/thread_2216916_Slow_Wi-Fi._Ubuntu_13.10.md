---
title: "Slow Wi-Fi. Ubuntu 13.10"
date: 2014-04-14
forum: Networking &amp; Wireless
---

### Post by nikita3 on 2014-04-14
I installed Ubuntu 13.10 and it worked well, Internet speed was 6Mbps, but then it updated and speed became 300Kbps and less. Here are some logs 


```

[COLOR=#000000][FONT=Ubuntu Beta]nikita@nikita-KX685AA-ACB-a6551-ru:~$ iwconfig[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]eth0      no wireless extensions.[/FONT][/COLOR]

[COLOR=#000000][FONT=Ubuntu Beta]lo        no wireless extensions.[/FONT][/COLOR]

[COLOR=#000000][FONT=Ubuntu Beta]wlan0     IEEE 802.11bgn  ESSID:"*********"  [/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]          Mode:Managed  Frequency:2.412 GHz  Access Point: **********   [/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]          Bit Rate=65 Mb/s   Tx-Power=20 dBm   [/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]          Retry  long limit:7   RTS thr:off   Fragment thr:off[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]          Power Management:off[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]          Link Quality=62/70  Signal level=-48 dBm  [/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]          Tx excessive retries:1  Invalid misc:369   Missed beacon:0[/FONT][/COLOR]
```

```
[COLOR=#000000][FONT=Ubuntu Beta]~$ lspci -nnk | grep -iA2 net[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]01:00.0 Network controller [0280]: Qualcomm Atheros AR922X Wireless Network Adapter [168c:0029] (rev 01)[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]   Subsystem: D-Link System Inc Device [1186:3a78][/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]   Kernel driver in use: ath9k[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]--[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 02)[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]   Subsystem: Hewlett-Packard Company Device [103c:2a6f][/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]   Kernel driver in use: r8169[/FONT][/COLOR]
```

```
[COLOR=#000000][FONT=Ubuntu Beta]~$ lsmod[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]Module                  Size  Used by[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]ath9k                 155907  0 [/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]parport_pc             32701  0 [/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]ppdev                  17671  0 [/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]rfcomm                 69130  0 [/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]bnep                   19704  2 [/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]bluetooth             372041  10 bnep,rfcomm[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]vesafb                 13828  0 [/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]coretemp               13435  0 [/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]arc4                   12608  2 [/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]kvm                   431754  0 [/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]gpio_ich               13476  0 [/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]joydev                 17377  0 [/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]snd_hda_codec_realtek    56475  1 [/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]snd_hda_intel          52267  3 [/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]snd_hda_codec         188738  2 snd_hda_codec_realtek,snd_hda_intel[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]snd_hwdep              13602  1 snd_hda_codec[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]snd_pcm               102033  2 snd_hda_codec,snd_hda_intel[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]snd_page_alloc         18710  2 snd_pcm,snd_hda_intel[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]snd_seq_midi           13324  0 [/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]snd_seq_midi_event     14899  1 snd_seq_midi[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]snd_rawmidi            30095  1 snd_seq_midi[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]microcode              23656  0 [/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]ath9k_common           13859  1 ath9k[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]ath9k_hw              444732  2 ath9k_common,ath9k[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]serio_raw              13413  0 [/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]ath                    23827  3 ath9k_common,ath9k,ath9k_hw[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]snd_timer              29433  2 snd_pcm,snd_seq[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]mac80211              597268  1 ath9k[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]lpc_ich                21080  0 [/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]cfg80211              480503  3 ath,ath9k,mac80211[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]nouveau               943749  4 [/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]snd                    69141  16 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]lp                     17759  0 [/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]parport                42299  3 lp,ppdev,parport_pc[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]mxm_wmi                13021  1 nouveau[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]soundcore              12680  1 snd[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]wmi                    19070  2 mxm_wmi,nouveau[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]video                  19318  1 nouveau[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]ttm                    84169  1 nouveau[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]drm_kms_helper         52710  1 nouveau[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]drm                   297056  6 ttm,drm_kms_helper,nouveau[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]i2c_algo_bit           13413  1 nouveau[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]mac_hid                13205  0 [/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]hid_generic            12548  0 [/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]usbhid                 53014  0 [/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]hid                   101762  2 hid_generic,usbhid[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]usb_storage            62062  0 [/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]ahci                   25819  2 [/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]firewire_ohci          40327  0 [/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]libahci                32009  1 ahci[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]firewire_core          64534  1 firewire_ohci[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]crc_itu_t              12707  1 firewire_core[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]r8169                  67581  0 [/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]mii                    13934  1 r8169[/FONT][/COLOR]
```

---

### Post by evan8 on 2014-04-14
Try this on terminal  

echo "options RTL8111 swenc=1 ips=0 fwlps=0" | sudo tee /etc/modprobe.d/RTL8111.confswenc=1 ips=0 fwlps=0" | sudo tee /etc/modprobe.d/rtl8192ce.conf


or this one works for me but i guess different driver or whatever

echo "options rtl8192ce swenc=1 ips=0 fwlps=0" | sudo tee /etc/modprobe.d/rtl8192ce.conf

I had same issue where it would never go past 250-300. this fixes it for me right away. It seemed to only happen mostly on unity ubuntu and ubuntu gnome I think

---

### Post by wildmanne39 on 2014-04-14
Please do not do what evan8 recommends because that is for a different driver that you do not have.

Try:
```
echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
sudo modprobe -rfv ath9k
sudo modprobe -v ath9k
```
Thanks

---

