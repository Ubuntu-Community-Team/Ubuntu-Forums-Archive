---
title: "RT3290, System crashes while trying to access Internet"
date: 2014-03-03
forum: Networking &amp; Wireless
---

### Post by Porta-Chaves on 2014-03-03
Hi, I'm having the exact same problem on my Asus k450j, except that it has a Ralink RT3290 wireless device.

Employing the fix proposed here allows me to connect to a wireless network, but if I try to access the internet through a browser or the console the system crashes and/or kernel panics.

Any sugesstions?

output:

```
0: acer-wireless: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
```

```

Module                  Size  Used by
rfcomm                 74718  0 
bnep                   24107  2 
bluetooth             391726  10 rfcomm,bnep
parport_pc             32866  0 
ppdev                  17711  0 
snd_hda_codec_realtek    56448  1 
snd_hda_codec_hdmi     41736  1 
uvcvideo               82247  0 
videobuf2_core         40815  1 uvcvideo
videodev              138562  2 uvcvideo,videobuf2_core
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
nouveau               979899  0 
snd_hda_intel          53038  5 
snd_hda_codec         194727  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
ttm                    84837  1 nouveau
i915                  688281  5 
drm_kms_helper         53237  2 nouveau,i915
drm                   306660  6 nouveau,ttm,i915,drm_kms_helper
snd_hwdep              13613  1 snd_hda_codec
snd_pcm               107140  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
joydev                 17613  0 
snd_seq_midi           13324  0 
snd_rawmidi            30416  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
acer_wmi               32938  0 
snd_seq                66061  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29989  2 snd_pcm,snd_seq
snd_seq_device         14497  3 snd_seq_midi,snd_rawmidi,snd_seq
asus_nb_wmi            16990  0 
asus_wmi               24794  1 asus_nb_wmi
sparse_keymap          13890  2 acer_wmi,asus_wmi
mxm_wmi                13021  1 nouveau
mac_hid                13253  0 
i2c_algo_bit           13564  2 nouveau,i915
psmouse               104093  0 
mei_me                 18418  0 
wmi                    19256  4 nouveau,acer_wmi,asus_wmi,mxm_wmi
snd                    73753  21 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_seq_midi,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mei                    78537  1 mei_me
serio_raw              13413  0 
soundcore              12680  1 snd
rt3290sta            1178340  0 
lpc_ich                21163  0 
snd_page_alloc         18798  2 snd_hda_intel,snd_pcm
video                  19574  4 nouveau,i915,acer_wmi,asus_wmi
lp                     17799  0 
parport                42466  3 parport_pc,ppdev,lp
ahci                   30063  2 
alx                    32936  0 
libahci                32118  1 ahci
mdio                   13807  1 alx

```

---

### Post by varunendra on 2014-03-04
@ Porta-Chaves,

Are the above outputs from before implementing the fix? Because the "acer_wmi" is still loaded as per above lsmod, and clearly fighting with "asus_nb_wmi".

Although the crashing problem may be caused by the rt3290sta driver alone - that's a known bug with that driver that appears on some systems with newer kernels. It works nicely for some people, but unfortunately not for everyone.

---

### Post by Porta-Chaves on 2014-03-07
> **varunendra said:**
> @ Porta-Chaves,

Are the above outputs from before implementing the fix? Because the "acer_wmi" is still loaded as per above lsmod, and clearly fighting with "asus_nb_wmi".

Although the crashing problem may be caused by the rt3290sta driver alone - that's a known bug with that driver that appears on some systems with newer kernels. It works nicely for some people, but unfortunately not for everyone.

Yes, the output is before the fix. 

after the fix:

```
Module                  Size  Used by
bnep                   24107  2 
rfcomm                 74718  0 
bluetooth             391726  10 bnep,rfcomm
parport_pc             32866  0 
ppdev                  17711  0 
snd_hda_codec_realtek    56448  1 
snd_hda_codec_hdmi     41736  1 
joydev                 17613  0 
uvcvideo               82247  0 
videobuf2_core         40815  1 uvcvideo
videodev              138562  2 uvcvideo,videobuf2_core
snd_hda_intel          53038  5 
videobuf2_vmalloc      13216  1 uvcvideo
snd_hda_codec         194727  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
videobuf2_memops       13362  1 videobuf2_vmalloc
snd_hwdep              13613  1 snd_hda_codec
snd_pcm               107140  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30416  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                66061  2 snd_seq_midi,snd_seq_midi_event
nouveau               979899  0 
snd_timer              29989  2 snd_pcm,snd_seq
i915                  688281  5 
snd_seq_device         14497  3 snd_seq_midi,snd_rawmidi,snd_seq
ttm                    84837  1 nouveau
asus_nb_wmi            16990  0 
asus_wmi               24794  1 asus_nb_wmi
snd                    73753  21 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_seq_midi,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm_kms_helper         53237  2 nouveau,i915
sparse_keymap          13890  1 asus_wmi
drm                   306660  6 nouveau,i915,ttm,drm_kms_helper
mxm_wmi                13021  1 nouveau
soundcore              12680  1 snd
psmouse               104093  0 
mei_me                 18418  0 
rt3290sta            1178340  1 
i2c_algo_bit           13564  2 nouveau,i915
mei                    78537  1 mei_me
wmi                    19256  3 nouveau,asus_wmi,mxm_wmi
snd_page_alloc         18798  2 snd_hda_intel,snd_pcm
video                  19574  3 nouveau,i915,asus_wmi
serio_raw              13413  0 
lp                     17799  0 
mac_hid                13253  0 
parport                42466  3 parport_pc,ppdev,lp
lpc_ich                21163  0 
ahci                   30063  2 
libahci                32118  1 ahci
alx                    32936  0 
mdio                   13807  1 alx

```

---

### Post by bapoumba on 2014-03-07
Moved to its own thread. Originally here : [http://ubuntuforums.org/showthread.php?t=2201597](http://ubuntuforums.org/showthread.php?t=2201597)

---

### Post by varunendra on 2014-03-07
Thanks for the quick response and the link bapoumba, always pleasant to see the bee on the threads. :)

**@Porta-Chaves,**

For now I am assuming it is indeed the problem related to the sta driver as I mentioned previously. Could you please give me the link to the post/guide/blog-post that you followed to install it?

Unless you got some latest and better patch for it, I believe our best shot (and probably the only promising one) is to remove it and try the native drivers again, a new one if the default one doesn't work.

Apart from the link to the post/guide as asked above, please also post a detailed report generated by "wireless_script" of Wild Man. You can find the instructions to download and run it in the "Wireless Script" link in my signature below. It will help me getting a more complete picture of your setup and be able to advise more precisely.

---

