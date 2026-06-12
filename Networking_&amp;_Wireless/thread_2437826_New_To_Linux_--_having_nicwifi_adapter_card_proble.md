---
title: "New To Linux -- having nic/wifi adapter card problems!"
date: 2020-03-01
forum: Networking &amp; Wireless
---

### Post by djtehnoob on 2020-03-01
First I would like to say excuse me for the great extent of my ignorance  that I am about to make apparent with the next few questions.... 

My question is about my network card and why the Wi-Fi has become so  slow lately. I am simply guessing that it is a problem with my driver or  configuration but no nothing for certain.

> Here is some information before I begin asking:
My NIC is a Intel Wireless AC 3165 and has in the past brought me 5G at speeds equaling hardwired internet. 

Is my radio signal set to 5g? Yes.

My plan is 250 Mbps. My Wi-fi, which as I said before usually produces at or near 250 Mbps, is getting anywhere from 20-40.

Is my laptop by my router? Yes. In fact the router is directly under my  desk, the placement has not changed between my card working properly and  it failing to deliver quality Wi-Fi speed.

The router is a TC 8715. I am not a fan of it nor my provider, but as  for the network speed it has delivered consistenly for the past 8  months.

Is my Wi-Fi struggling only at home? No. I have the same connection problems at work.


First off, how do I correctly view the list of drivers that my system is currently using for its' hardware?

I used lsmod and got this:
```
Module                  Size  Used by
rfcomm                 81920  16
bnep                   24576  2
nls_iso8859_1          16384  1
intel_rapl_msr         20480  0
intel_rapl_common      24576  1 intel_rapl_msr
x86_pkg_temp_thermal    20480  0
intel_powerclamp       20480  0
coretemp               20480  0
snd_hda_codec_hdmi     57344  1
snd_hda_codec_realtek   118784  1
kvm_intel             241664  0
snd_hda_codec_generic    81920  1 snd_hda_codec_realtek
ledtrig_audio          16384  2 snd_hda_codec_generic,snd_hda_codec_realtek
kvm                   651264  1 kvm_intel
irqbypass              16384  1 kvm
crct10dif_pclmul       16384  1
crc32_pclmul           16384  0
ghash_clmulni_intel    16384  0
mei_hdcp               24576  0
snd_hda_intel          49152  6
snd_hda_codec         131072  4 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec_realtek
snd_hda_core           90112  5 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hda_codec_realtek
snd_hwdep              20480  1 snd_hda_codec
iwlmvm                397312  0
aesni_intel           372736  0
snd_pcm               102400  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hda_core
mac80211              847872  1 iwlmvm
snd_seq_midi           20480  0
snd_seq_midi_event     16384  1 snd_seq_midi
aes_x86_64             20480  1 aesni_intel
crypto_simd            16384  1 aesni_intel
nouveau              1892352  0
cryptd                 24576  2 crypto_simd,ghash_clmulni_intel
snd_rawmidi            36864  1 snd_seq_midi
glue_helper            16384  1 aesni_intel
joydev                 28672  0
snd_seq                69632  2 snd_seq_midi,snd_seq_midi_event
snd_seq_device         16384  3 snd_seq,snd_seq_midi,snd_rawmidi
libarc4                16384  1 mac80211
snd_timer              36864  2 snd_seq,snd_pcm
input_leds             16384  0
intel_cstate           20480  0
i915                 1937408  25
intel_rapl_perf        20480  0
intel_wmi_thunderbolt    20480  0
serio_raw              20480  0
snd                    86016  23  snd_hda_codec_generic,snd_seq,snd_seq_device,snd_hda_codec_hdmi,snd_hwdep,snd_hda_intel,snd_hda_codec,snd_hda_codec_realtek,snd_timer,snd_pcm,snd_rawmidi
msi_wmi                20480  0
sparse_keymap          16384  1 msi_wmi
mxm_wmi                16384  1 nouveau
ttm                   102400  1 nouveau
iwlwifi               348160  1 iwlmvm
soundcore              16384  1 snd
btusb                  57344  0
btrtl                  20480  1 btusb
btbcm                  16384  1 btusb
btintel                24576  1 btusb
drm_kms_helper        180224  2 i915,nouveau
cfg80211              704512  3 iwlmvm,iwlwifi,mac80211
bluetooth             573440  43 btrtl,btintel,btbcm,bnep,btusb,rfcomm
drm                   491520  19 drm_kms_helper,i915,ttm,nouveau
mei_me                 40960  1
i2c_algo_bit           16384  2 i915,nouveau
fb_sys_fops            16384  1 drm_kms_helper
rtsx_usb_ms            24576  0
syscopyarea            16384  1 drm_kms_helper
ecdh_generic           16384  1 bluetooth
sysfillrect            16384  1 drm_kms_helper
memstick               20480  1 rtsx_usb_ms
ecc                    32768  1 ecdh_generic
mei                   102400  3 mei_hdcp,mei_me
intel_pch_thermal      16384  0
sysimgblt              16384  1 drm_kms_helper
acpi_pad              184320  0
mac_hid                16384  0
sch_fq_codel           20480  5
parport_pc             40960  0
ppdev                  24576  0
lp                     20480  0
parport                53248  3 parport_pc,lp,ppdev
ip_tables              32768  0
x_tables               40960  1 ip_tables
autofs4                45056  2
hid_generic            16384  0
rtsx_usb_sdmmc         28672  0
usbhid                 53248  0
hid                   131072  2 usbhid,hid_generic
rtsx_usb               28672  2 rtsx_usb_sdmmc,rtsx_usb_ms
ahci                   40960  4
alx                    49152  0
psmouse               151552  0
mdio                   16384  1 alx
libahci                32768  1 apasthci
wmi                    32768  4 intel_wmi_thunderbolt,msi_wmi,mxm_wmi,nouveau
video                  49152  3 msi_wmi,i915,nouveau
```


With that being the output 

Question  1: Why are so many wmi drivers running? Yes, I do duel boot  with my priority boot being Ubuntu. However they are entirely on two  different hard drives with no overlap. And also, no Windows 10 (should  not) isn't running in anyway either. Maybe it is appropriate for wmi to  be run since the laptop brand, which is MSI, came with windows and not  linux and therefore it is used to read the computers factory hardware?
And also why are there so many bt(bluetooth drivers) present? I disable bluetooth most of the time because I had an issue with bluetooth a while back where someone found a way to install a trojan on my computer OVER and OVER and OVER with bluetooth. The computer would re-enable bluetooth constantly, make me part of a domain and limit my rights as a user, reconfigure my DNS... it was a pain in the ass and I hated the experience so I tend to leave bluetooth off unless I am using wireless headphones. But afterwards, it immediately goes back off.

Question  2: where do I find my current nic driver? I can't even tell  with linux terminology what I am looking for. I am a long-time computer  user, long enough to consider myself a beginner as a windows  "super-user" but when it comes down to it, amongst real "computer guys"  and legit geeks, I am a noob. I'm eager to learn but I need guidance  from guys and gals like you all, because as of right now Linux might as  well be written in Egyptian Hieroglyphics. 

Question  3: How do I *(preferably from the terminal since I am  trying to learn it. I understand the importance of it, just don't  understand IT worth a damn  :razz:) *reset  all my network setting to default AND if you feel like explaining or have a  link to a quality guide written for beginners do I then configure it for  optimal speed.



So a big thanks ahead of time to all you guys who I just know are going to welcome me into the community and be of help with my issue! And for everyone out there like me I look forward to learing with you and eventually helping others just like us, learning linux and computers all over again from scratch! :-D

---

### Post by wildmanne39 on 2020-03-01
*Thread moved to **Networking & Wireless a more appropriate sub-forum**.*

Hi, please click on the wireless script in my signature, follow the directions for running it and posting the results back here using the pastebin link created and someone should be able to help.

---

