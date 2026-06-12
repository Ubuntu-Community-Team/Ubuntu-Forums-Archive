---
title: "Question about compiling kernel"
date: 2009-11-16
forum: New to Ubuntu
---

### Post by slughappy1 on 2009-11-16
I was just curious about several things. I wanted to know what modules my laptop was using so I used the command lsmod and this came up. ```
jason@Barnaby:~$ lsmod 
Module                  Size  Used by
cryptd                  8008  0 
aes_x86_64              8992  3 
aes_generic            28480  1 aes_x86_64
binfmt_misc            10220  1 
snd_hda_codec_idt      72976  1 
snd_hda_intel          31880  2 
snd_hda_codec          87584  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep               9352  1 snd_hda_codec
snd_pcm_oss            44704  0 
snd_mixer_oss          18976  1 snd_pcm_oss
snd_pcm                93160  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           3460  0 
snd_seq_oss            33440  0 
snd_seq_midi            8192  0 
snd_rawmidi            27360  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                60608  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
arc4                    2144  2 
ecb                     3296  2 
snd_timer              26992  2 snd_pcm,snd_seq
iptable_filter          3872  0 
iwl3945                89984  0 
snd_seq_device          8308  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    77096  16 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
iwlcore               133248  1 iwl3945
dell_wmi                3216  0 
psmouse                57124  0 
mac80211              210104  2 iwl3945,iwlcore
soundcore               9088  1 snd
sdhci_pci               8928  0 
dell_laptop             9692  0 
sdhci                  20484  1 sdhci_pci
snd_page_alloc         10928  2 snd_hda_intel,snd_pcm
cfg80211              109144  3 iwl3945,iwlcore,mac80211
serio_raw               6596  0 
ip_tables              21200  1 iptable_filter
led_class               5256  3 iwl3945,iwlcore,sdhci
joydev                 13088  0 
dcdbas                  9136  1 dell_laptop
lp                     11908  0 
x_tables               25832  1 ip_tables
parport                40528  1 lp
usbhid                 43968  0 
fbcon                  41344  72 
tileblit                3136  1 fbcon
font                    8832  1 fbcon
bitblit                 6688  1 fbcon
softcursor              2336  1 bitblit
ohci1394               33780  0 
ieee1394              100896  1 ohci1394
i915                  246984  3 
tg3                   123748  0 
drm                   193856  3 i915
i2c_algo_bit            7076  1 i915
video                  23612  1 i915
output                  3680  1 video
intel_agp              32816  2 i915
jason@Barnaby:~$ 

``` Shouldn't all of the modules loaded into the kernel be used? Why are a few of them being used by 0? Could I have them not load and would anything be harmed if I do? Would the kernel load faster, or work faster, if I included the modules into the kernel instead of having them be modules?

---

### Post by brij on 2009-11-16
my understanding is that 0 meand the modules is not being used. you can stop loading the modules by putting then into blacklist file. which is under /etc/modprobe.d/. Also building a module as kernel gives you flexibility of loading and unloading the modules but i dont think it will boot fast if you build drivers into kernel instead of modules.

---

