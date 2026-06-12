---
title: "Acer C7 Chromebook, 13.04, ath9k AR9462 Wireless Issues"
date: 2013-09-20
forum: Networking &amp; Wireless
---

### Post by BHzCnPm on 2013-09-20
[COLOR=#333333][FONT=UbuntuRegular]My Acer came with the Atheros AR9462 and it's giving me problems. The ath9k nohwcrypt solution seems like it helped a little bit--but only delayed the inevitable dropping networks every few minutes, unable to connect, etc.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]I've looked into compat-wireless but can't figure out how to get it installed and set up.[/FONT][/COLOR]
$ uname -r
3.4.0

$ sudo apt-get install linux-headers-generic
...
The following extra packages will be installed:
linux-headers-3.8.0-30 linux-headers-3.8.0-30-generic
[COLOR=#333333][FONT=UbuntuRegular]Is there something weird going on with my Chrubuntu install (Ubuntu on Chromebook) that's making my kernel weird? Any other suggestions?[/FONT][/COLOR]

---

### Post by Hadaka on 2013-09-20
Hi , did you build this file to make the nohwcrypt permanent?
```
sudo gedit /etc/modprobe.d/ath9k.conf
```
enter this one line of code..
```
options ath9k nohwcrypt=1
```
save and close gedit.
boot

---

### Post by BHzCnPm on 2013-09-20
Yep that was the first thing I tried. I just checked to make sure and the full contents of my ath9k.conf file are exactly as you suggested.


It definitely seems to have helped and made a stable wifi connection last longer, but it still ultimately runs into connection problems that can sometimes be solved by switching off and on the network adapter and then it eventually requires a reboot (and sometimes even the reboot doesn't help and I'm just stuck waiting it out).

I've done some research and I'd like to try updating the wireless drivers but am getting stuck. Would you like me to run anything that would give more information?

---

### Post by Hadaka on 2013-09-20
Hi, this "may" help some.
```
sudo su
echo "blacklist acer_wmi" | sudo tee -a /etc/modprobe.d/blacklist.conf
exit 0
```
and please post..
```
lsmod
uname -a
```
also..check your channel...set to 1 or 11
thanks.

---

### Post by BHzCnPm on 2013-09-20
Channel is 1. But the most problematic connection is a school one that I have no control over.

```

$ lsmodModule                  Size  Used by
fuse                   59374  2 
rfcomm                 25131  12 
snd_hda_codec_hdmi     28957  1 
snd_hda_codec_realtek    45104  1 
snd_hda_intel          20528  5 
snd_hda_codec          58216  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              12366  1 snd_hda_codec
snd_pcm                52490  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
ath9k_btcoex          105354  0 
mac80211              262422  1 ath9k_btcoex
ath9k_common_btcoex    12657  1 ath9k_btcoex
ath9k_hw_btcoex       319142  2 ath9k_btcoex,ath9k_common_btcoex
ath                    16858  3 ath9k_btcoex,ath9k_hw_btcoex,ath9k_common_btcoex
uvcvideo               54888  0 
videobuf2_core         25155  1 uvcvideo
videodev               64328  1 uvcvideo
videobuf2_vmalloc      12305  1 uvcvideo
videobuf2_memops       12372  1 videobuf2_vmalloc
memconsole             12336  0 
ath3k                  12336  0 
btusb                  16432  0 
bluetooth             142917  20 ath3k,btusb,rfcomm
sdhci_pci              16432  0 
sdhci                  24949  1 sdhci_pci
mmc_core               66279  2 sdhci,sdhci_pci
nm10_gpio              12336  0 
cfg80211              123127  3 ath,ath9k_btcoex,mac80211
tg3                   106544  0 
joydev                 16432  0 
snd_timer              20974  1 snd_pcm
snd_page_alloc         12710  2 snd_pcm,snd_hda_intel
$ 

```

```

$ uname -aLinux chrubuntu 3.4.0 #1 SMP Thu Sep 12 16:21:05 PDT 2013 i686 i686 i686 GNU/Linux
$ 

```

---

### Post by Hadaka on 2013-09-20
Hi, it looks like from your lsmod dump
you use the ath9k_btcoex module not the regular ath9k.
I'm not finding any fixes doing research on it....a few bugs
and it seems to be confined to the chrombook.  You may find
a patch somewhere by searching or perhapes someone with
abilities i dont have can guide you to patch it. sorry I was not
able to find a fix for you.

---

### Post by varunendra on 2013-09-21
> **BHzCnPm said:**
> 
```

**[COLOR="#FF0000"]ath9k_btcoex[/COLOR]**          105354  0 
mac80211              262422  1 ath9k_btcoex
ath9k_common_btcoex    12657  1 ath9k_btcoex
ath9k_hw_btcoex       319142  2 ath9k_btcoex,ath9k_common_btcoex
ath                    16858  3 ath9k_btcoex,ath9k_hw_btcoex,ath9k_common_btcoex

```

Never seen or heard of that module before, but it looks like just a slightly modified version of standard ath9k with "btcoex" enabled by default (which is optional in ath9k) : [https://groups.google.com/a/chromium.org/forum/#!topic/chromium-os-reviews/PqwwA5CikYw](https://groups.google.com/a/chromium.org/forum/#!topic/chromium-os-reviews/PqwwA5CikYw)

Please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates. Maybe we can try something if all else looks familiar.

---

