---
title: "no sound on 1525, since 8.04 LTS, now: jaunty"
date: 2009-07-05
forum: New to Ubuntu
---

### Post by risa on 2009-07-05
I give up searching alone and I need your help. On my dell inspiron 1525 sound doesn't work at all, since 8.04 LTS. I tried a lot, without success; my last hope: jaunty - but no sound. What else can I do?

---

### Post by llamakc on 2009-07-05
Are you positive it isn't muted? My 1525 has sound. Run alsamixer and make sure your levels are up.

Do you know if snd_hda-intel is loaded? Open a Terminal and type:

```

lsmod

```

Cut/paste the results back HERE inside of the [ code ] blocks, please.

---

### Post by risa on 2009-07-11
Hello, Ilamakc,
thanks for your reply.
Sound isn't muted. 
Alsamixer doesn't run - I think ALSA is in conflict with pulseaudio.
And some more infos from:
  	 	 	 	 	   	 	 	 	 	 	      	 	 	 	 	 
  	 	 	 	 	Codec: SigmaTel STAC9227 
  	 	 	 	 	Sound Servers on this system[FONT=monospace]
[/FONT]Pulseaudio: Installed - Yes (/usr/bin/pulseaudio) Running - Yes[FONT=monospace]
[/FONT]ESound Daemon:[FONT=monospace] [/FONT]Installed - Yes (/usr/bin/esd)[FONT=monospace] [/FONT]Running - No[FONT=monospace]
[/FONT]Soundcards recognised by ALSA 0 [Intel          ]: HDA-Intel - HDA Intel[FONT=monospace]
[/FONT]HDA Intel at 0xdffdc000 irq 2299[FONT=monospace]
[/FONT]PCI Soundcards installed in the system
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02) [FONT=monospace]

lsmod resulted in:
Module                  Size  Used by
i915                   65668  2 
drm                    96296  3 i915
ppdev                  15620  0 
bridge                 56340  0 
stp                    10500  1 bridge
bnep                   20224  2 
xt_TCPMSS              12032  1 
xt_tcpmss              10112  1 
xt_tcpudp              11008  1 
iptable_mangle         10880  1 
ip_tables              19472  1 iptable_mangle
x_tables               23044  4 xt_TCPMSS,xt_tcpmss,xt_tcpudp,ip_tables
pppoe                  18112  2 
pppox                  11276  1 pppoe
slamr                 435496  0 
input_polldev          11912  0 
joydev                 18368  0 
sbp2                   30476  0 
lp                     17156  0 
parport                42220  2 ppdev,lp
arc4                    9856  2 
ecb                    10752  2 
iwl3945                84100  0 
iwlcore               112768  1 iwl3945
lbm_cw_mac80211       227492  2 iwl3945,iwlcore
video                  25360  0 
sdhci_pci              15232  0 
psmouse                61972  0 
iTCO_wdt               19108  0 
lbm_cw_cfg80211        73760  3 iwl3945,iwlcore,lbm_cw_mac80211
output                 11008  1 video
dcdbas                 15264  0 
sdhci                  23940  1 sdhci_pci
serio_raw              13316  0 
iTCO_vendor_support    11652  1 iTCO_wdt
pcspkr                 10496  0 
led_class              12036  2 iwl3945,iwlcore
intel_agp              34108  1 
agpgart                42696  3 drm,intel_agp
usbhid                 42336  0 
ohci1394               38576  0 
ieee1394               94660  2 sbp2,ohci1394
sky2                   54916  0 
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
[/FONT]
I've been looking for a solution for months. In the meanwhile I learnt: it's not only me who is so much frustrated.

---

