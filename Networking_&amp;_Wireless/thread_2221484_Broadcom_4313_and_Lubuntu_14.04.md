---
title: "Broadcom 4313 and Lubuntu 14.04"
date: 2014-05-02
forum: Networking &amp; Wireless
---

### Post by Matthias_Holder on 2014-05-02
Hi,

I experienced a problem similar to the one described in this thread with a Broadcom 4313: [http://ubuntuforums.org/showthread.php?t=2220830](http://ubuntuforums.org/showthread.php?t=2220830)

Wifi is now working fine and I somehow managed to solve the issue on my own. I uninstalled ndiswrapper and everything b43 related.
However, the only way for me to get to work my wifi is by running the following commands after each startup.

I am using Lubuntu 14.04 on an Asus eee PC 1018P.

```

sudo modprobe -r b43
sudo modprobe -r wl
sudo modprobe wl
```

After doing this, nm-applet is starting to establish a connection right away.

So, what I do not understand is the following: How can b43 still be sticking around although I uninstalled it? Secondly, how can I stop it from loading on startup, so I don't need to perform above commands?

Another thing I observed and may help in solving this issue. While booting, the following line appears:

```
b43.allhwsupport=1
```

Thanks in advance for your help!

---

### Post by Hadaka on 2014-05-02
Hi, thanks for opening a new thread.
lets start by seeing if we can get rid of that b43 error.
please do..
```
sudo apt-get install linux-firmware
sudo apt-get update
```
boot and report back if the b43 error goes away.
then we will decide how to best use the correct driver
thanks.

---

### Post by Matthias_Holder on 2014-05-02
Hi,

just did as suggested. Problem stays the same. I realized that the error line during startup is actually longer but I couldn't read it entirely. What I posted before is the very last part of it, starting a new line.

I think we just need to get rid of that b43 thing that shows up when I run:
```
lsmod
```

Cheers,
Matthias

---

### Post by Hadaka on 2014-05-02
ok,please do..
```
sudo modprobe -rf b43
sudo modprobe -r wl
sudo modprobe -v wl
```
this should really be running on the native driver..but..if you are happy with
it then..ok...
then do..
```
sudo su
echo "wl" >> etc/modules
exit 0
```
and please post the output of..
```
lsmod
```
let us know how that goes or if you want to
load the native driver.
thanks.

---

### Post by Matthias_Holder on 2014-05-02
Hi,

thanks for your reply. When entering 

```
[COLOR=#000000][FONT=Ubuntu Mono]echo "wl" >> etc/modules[/FONT][/COLOR]
```

it reports "No such file or directory".

I suppose this makes wl start on startup?

Directly upon entering the first three lines you suggested, my wifi connected just fine. Plus, I found out that my adaptor is not supported by the b43 package.

```
[COLOR=#000000][FONT=Ubuntu Mono]sudo modprobe -rf b43
[/FONT][/COLOR]sudo modprobe -r wl
sudo modprobe -v wl
```

---

### Post by Hadaka on 2014-05-02
Hi, my error ..i said 
[COLOR=#000000][FONT=Ubuntu Mono]echo "wl" >> etc/modules

and it should be..
```
sudo su
echo "wl" >> /etc/modules
exit 0
```
please try again and also after
you boot.post lsmod
```
lsmod
```
thanks.
[/FONT][/COLOR]

---

### Post by Matthias_Holder on 2014-05-02
Ok, now that I successfully entered the line containing "echo", it doesn't work any longer and the b43 thing appears during boot.

Whereas in the meantime, i.e. before I had run the echo line, it worked perfectly fine, like even after reboot. Please advise what I need to do to make it work yet again.

Also, how can I copy from terminal to clipboard to post lsmod?

---

### Post by SoulStreamBurst on 2014-05-02
To copy text from the terminal just highlight them with your mouse, then right-click, copy and paste it away.

---

### Post by Matthias_Holder on 2014-05-02
> **SoulStreamBurst said:**
> To copy text from the terminal just highlight them with your mouse, then right-click, copy and paste it away.

Thanks.

And I forgot to reply to one of your questions, Hadaka: What I want is to load the wl driver/module and get rid of ANYTHING b43 related. I found out that b43 is entirely incompatible with my Broadcom adaptor. Although I know that it does work for others.

---

### Post by Matthias_Holder on 2014-05-02
Here you go: lsmod after entering everything and BEFORE rebooting.

```
Module                  Size  Used bymichael_mic            12540  4 
arc4                   12536  2 
lib80211_crypt_tkip    17456  0 
wl                   3999690  0 
lib80211               14040  2 wl,lib80211_crypt_tkip
cfg80211              409394  1 wl
snd_hda_codec_realtek    51029  1 
joydev                 17101  0 
snd_hda_intel          42730  1 
snd_hda_codec         164067  2 snd_hda_codec_realtek,snd_hda_intel
eeepc_wmi              12983  0 
snd_hwdep              13272  1 snd_hda_codec
asus_wmi               23495  1 eeepc_wmi
sparse_keymap          13708  1 asus_wmi
snd_pcm                85501  2 snd_hda_codec,snd_hda_intel
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
bnep                   18895  2 
rfcomm                 53664  0 
snd_rawmidi            25135  1 snd_seq_midi
bluetooth             342263  10 bnep,rfcomm
snd_seq                55383  2 snd_seq_midi_event,snd_seq_midi
uvcvideo               71309  0 
videobuf2_vmalloc      13048  1 uvcvideo
videobuf2_memops       13170  1 videobuf2_vmalloc
videobuf2_core         39258  1 uvcvideo
i915                  705396  2 
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
videodev              108503  2 uvcvideo,videobuf2_core
snd_timer              28584  2 snd_pcm,snd_seq
coretemp               13195  0 
psmouse                91033  0 
drm_kms_helper         46907  1 i915
serio_raw              13230  0 
drm                   243792  3 i915,drm_kms_helper
parport_pc             31981  0 
ppdev                  17391  0 
snd                    60871  12 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
i2c_algo_bit           13197  1 i915
lpc_ich                16864  0 
soundcore              12600  1 snd
video                  18903  2 i915,asus_wmi
wmi                    18673  1 asus_wmi
mac_hid                13037  0 
lp                     13299  0 
parport                40836  3 lp,ppdev,parport_pc
ahci                   25579  2 
libahci                26754  1 ahci
atl1c                  40949  0 



```

---

### Post by Hadaka on 2014-05-02
ok, now post lsmod after the codes.
it is loading wl in lsmod.please do..
and post..
```
cat /etc/modules
lsmod
```
thanks.

---

### Post by Matthias_Holder on 2014-05-02
I won't have access to the netbook until Tuesday or Wednesday, I think. Will reply to this thread then.

As for the lsmod posting, this was after entering the modprobe codes and then the "wl" >> /etc/modules stuff but NOT after the reboot.

---

