---
title: "Cable nor wireless working?"
date: 2013-11-01
forum: Networking &amp; Wireless
---

### Post by danielfriang on 2013-11-01
Hello, Im a new Ubuntu user, and I stumbled upon a problem with my internet. When I installed Ubuntu I was able to connect to my wireless internet, but when the installation was done, and I had restarted my compluter, I couldn't connect. I tried with an cable, and using wireless, but nothing works. I have no clue what can cause this, so I hope that someone here does know!

I do get an error when I restart, which says ExecutablePath /sbin/wpa_supplicant

maybe that has something to do with the problem?

---

### Post by Hadaka on 2013-11-01
Hi,please post the output of..
```
lspci -nnk | grep -iA3 net
lsmod
rfkill list all
```
thanks
since you dont have internet connection..
please try first..
```
sudo apt-get remove --purge bcmwl-kernel-source
```
boot...*if this activates your wired connection..then post the above.
thanks.

---

### Post by danielfriang on 2013-11-01
> **Hadaka said:**
> Hi,please post the output of..
```
lspci -nnk | grep -iA3 net
lsmod
rfkill list all
```
thanks
since you dont have internet connection..
please try first..
```
sudo apt-get remove --purge bcmwl-kernel-source
```
boot...*if this activates your wired connection..then post the above.
thanks.

For the apt-get remove part, it says the package is not installed.

lspci part says

```
03:00.0 ethernet controller [0200]: broadcom corporation netlink bcm57780 gigabit ethernet PCIe [14e4:1692] (rev 01)
Subsystem: acer incorporated [ALI] aspire 7740G [1025:033d]
kernel driver in use: tg3
06:00.0 network controller [0280]: qualcomm atheros AR9287 wireless network adapter (PCI-express) [168c:002e] (rev 01)
subsystem: lite-on communications inc device [11ad:6603]
kernel driver in use: ath9k

```

rfkill list all says

```

0: phy0: wireless lan

soft blocked: no
hard blocked: no

1: acer-wireless: wireless lan

soft blocked: no
hard blocked: no

```

I'll send the rest later, as I'm writing this through an Ipad.. :)

---

### Post by venkateshreddy.bur on 2013-11-01
I too have the same issue...
couldn't connect to internet from both wifi and cable..
and rfkill list all ..
shows the same response....
please help me...

---

### Post by danielfriang on 2013-11-01
Currently now I'm using the same computer, but I'm in "Try Linux", and as you can see, that works just fine? This makes absolutely no sense for me.

Here's my lsmod output:

```

Module                  Size  Used by
parport_pc             31981  0 
ppdev                  17391  0 
rfcomm                 53664  0 
bnep                   18893  2 
bluetooth             323534  10 bnep,rfcomm
snd_hda_codec_hdmi     40508  1 
snd_usb_audio         119227  1 
snd_usbmidi_lib        24326  1 snd_usb_audio
hid_generic            12492  0 
joydev                 17097  0 
usbhid                 47361  0 
hid                    87192  2 hid_generic,usbhid
acer_wmi               31735  0 
sparse_keymap          13708  1 acer_wmi
uvcvideo               71309  0 
videobuf2_vmalloc      13048  1 uvcvideo
videobuf2_memops       13170  1 videobuf2_vmalloc
videobuf2_core         39125  1 uvcvideo
videodev              107508  2 uvcvideo,videobuf2_core
kvm_amd                50537  0 
kvm                   364766  1 kvm_amd
arc4                   12536  2 
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_hda_codec_realtek    45473  1 
snd_rawmidi            25094  2 snd_usbmidi_lib,snd_seq_midi
ath9k                 135969  0 
ath9k_common           13619  1 ath9k
ath9k_hw              429197  2 ath9k_common,ath9k
microcode              18830  0 
ath                    19187  3 ath9k_common,ath9k,ath9k_hw
snd_seq                55383  2 snd_seq_midi_event,snd_seq_midi
snd_hda_intel          42658  5 
snd_hda_codec         164003  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13272  2 snd_usb_audio,snd_hda_codec
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_pcm                89488  4 snd_usb_audio,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
psmouse                90642  0 
serio_raw              13189  0 
radeon               1307301  3 
mac80211              513247  1 ath9k
sp5100_tco             13643  0 
k10temp                12958  0 
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
snd_timer              24447  2 snd_pcm,snd_seq
i2c_piix4              17682  0 
cfg80211              401436  3 ath,ath9k,mac80211
snd                    60790  25 snd_hda_codec_realtek,snd_usb_audio,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_usbmidi_lib,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
ttm                    71886  1 radeon
drm_kms_helper         46867  1 radeon
drm                   242354  5 ttm,drm_kms_helper,radeon
soundcore              12600  1 snd
i2c_algo_bit           13197  1 radeon
wmi                    18590  1 acer_wmi
video                  18777  1 acer_wmi
ohci_pci               13305  0 
mac_hid                13037  0 
lp                     13299  0 
parport                40795  3 lp,ppdev,parport_pc
tg3                   152066  0 
ptp                    18156  1 tg3
pps_core               18546  1 ptp
ahci                   25579  2 
libahci                26554  1 ahci

```

---

### Post by venkateshreddy.bur on 2013-11-01
When I do Ubuntu System testing on Networking and Internet it fails
and in wireless Network test shows ,could not find device_category = WIRELESS

---

### Post by Hadaka on 2013-11-01
Hi dan
what are you using to boot live...usb or dvd?
If all is well live, i would suspect a corrupted load,
the wired tg3 should just work.Be sure to run all the
updates when and if you reload.
thanks.
@ the other person on here attempting to hijack
the thread,please start your own thread.
thanks.

---

### Post by danielfriang on 2013-11-01
I booted it through an USB, how do you mean "corrupted load"?

---

### Post by Hadaka on 2013-11-01
Hi, there is "try Ubuntu" and "load Ubuntu"
It seems when you boot to the live usb,and use
"try Ubuntu" at least the wired part works. But
when you try to connect after loading,it doesnt.
Is this correct? Have you loaded Ubunutu after
you booted to the live usb?

---

### Post by danielfriang on 2013-11-01
I just installed ubuntu 12.04 and now it works

---

### Post by Hadaka on 2013-11-01
Great !...magic,smoke and mirrors, GLAD
it working! dont forget to do..
```
sudo apt-get update
sudo apt-get upgrade
```
ignore any offers of any other drivers.
and please mark solved.
How to->[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)
thanks.

---

