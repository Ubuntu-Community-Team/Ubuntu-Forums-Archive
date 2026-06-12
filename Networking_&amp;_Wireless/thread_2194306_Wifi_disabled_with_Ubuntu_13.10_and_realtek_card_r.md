---
title: "Wifi disabled with Ubuntu 13.10 and realtek card rtl8818ee"
date: 2013-12-17
forum: Networking &amp; Wireless
---

### Post by mcxime on 2013-12-17
I recently upgraded to Ubuntu 13.10 and I am facing the same problem as I had before with 12.04 - my wifi refuses to work. It is disabled by a hardware switch, as indicated by a light on my keyboard. I can not enable it in any way.

My computer:
HP envy quad core 15jt (dual boot with win 8)
Ubuntu 13.10 (64 bit)
RealTek rtl8188ee
(Ethernet works fine)

What I have tried: 
- Downloading the driver from realtek ([http://ubuntuforums.org/showthread.php?t=2162026](http://ubuntuforums.org/showthread.php?t=2162026))
- Unblocking using rfkill
- Booting in a previous kernel or in recovery mode with networking
- Editing the wakenet.sh file ([http://askubuntu.com/questions/365441/13-10-suspend-kills-wifi](http://askubuntu.com/questions/365441/13-10-suspend-kills-wifi))

Any help is appreciated. Thank you!

---

### Post by chili555 on 2013-12-17
I know I'm gonna hate myself in the morning...

Please run and post:```
lsmod | grep -e wmi -e rtl
lspci -nn | grep 0280
rfkill list all
```What make and exact model is the computer?

Thanks...I hope.

---

### Post by mcxime on 2013-12-18
The computer is a HP ENVY Touchsmart QuadCore 15j-t100 
Ouput is (respectively): 
```

hp_wmi                 14062  0 
sparse_keymap          13948  1 hp_wmi
rtl8188ee             138201  0 
rtlwifi               110108  1 rtl8188ee
snd_rawmidi            30095  1 snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
mac80211              596969  2 rtlwifi,rtl8188ee
snd                    69141  21 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_idt,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
mxm_wmi                13021  1 nouveau
cfg80211              479757  2 mac80211,rtlwifi
wmi                    19070  3 hp_wmi,mxm_wmi,nouveau



07:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188EE Wireless Network Adapter [10ec:8179] (rev 01)

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: yes


```

---

### Post by chili555 on 2013-12-19
Please try, temporarily:```
sudo modprobe -r hp-wmi
sudo rfkill unblock all
rfkill list all
```I'd also love to see:```
dmesg | grep -i -e wmi -e dmi
```This is the second case I've worked on in the last few days with an apparent issue with hp-wmi. Fascinating.

---

### Post by mcxime on 2013-12-19
That first line of code worked! Until I restarted and the same problem occurred. Is there any way to make this change persistent? 

As for the second part, output is:
```

[    0.000000] DMI: Hewlett-Packard HP ENVY TS 15 Notebook PC/1963, BIOS F.35 10/03/2013
[    6.370964] wmi: Mapper loaded
[    6.874453] input: HP WMI hotkeys as /devices/virtual/input/input6
[    8.374516] input: HDA Intel MID HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:03.0/sound/card0/input10
[    8.374563] input: HDA Intel MID HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:03.0/sound/card0/input11
[    8.374602] input: HDA Intel MID HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:03.0/sound/card0/input12

```

---

### Post by chili555 on 2013-12-19
> That first line of code worked! Until I restarted and the same problem occurred. Is there any way to make this change persistent? Why, certainly!```
sudo -i
modprobe -r hp-wmi
echo "blacklist hp-wmi"  >>  /etc/modprobe.d/blacklist.conf
exit
```You should be all set except for: [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

