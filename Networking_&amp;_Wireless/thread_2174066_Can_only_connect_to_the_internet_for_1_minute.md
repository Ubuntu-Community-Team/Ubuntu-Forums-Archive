---
title: "Can only connect to the internet for 1 minute"
date: 2013-09-12
forum: Networking &amp; Wireless
---

### Post by Socrat3s on 2013-09-12
As the title says on Ubuntu 12.04 using my netgear wireless WNA3100 card I can only connect to the internet using firefox for about 1 minute. During that time I can surf the web as usual , but after that, web pages won't load anymore. I tried pinging sites in the terminal to no avail . I just recently installed ndiswrapper for my wireless card but that's about the only change I've made to the system. I'm not sure if it's a DNS error or something but I have no clue. Please help :(

---

### Post by Socrat3s on 2013-09-12
Bump . Anyone ?

---

### Post by varunendra on 2013-09-13
Please post the outputs of -
```
lspci -nnk | grep -iA2 net
lsmod
iwconfig
nm-tool
```

---

### Post by mörgæs on 2013-09-13
- and please don't bump a thread.

---

### Post by Socrat3s on 2013-09-13
> **varunendra said:**
> Please post the outputs of -
```
lspci -nnk | grep -iA2 net
lsmod
iwconfig
nm-tool
```

I ended up switching to mint to see if it was just an ubuntu problem i'm experiencing the same thing. Not sure if you can help since i'm on mint but here is the output from the lines you told me to enter. 

Edit. Not sure why the smiley faces are in the output. 

quay@linuxmint ~ $ lspci -nnk | grep -iA2 net
00:19.0 Ethernet controller [0200]: Intel Corporation 82579LM Gigabit Network Connection [8086:1502] (rev 04)
    Subsystem: Lenovo Device [17aa:3086]
    Kernel driver in use: e1000e
quay@linuxmint ~ $ lsmod
Module                  Size  Used by
ndiswrapper           283340  0 
snd_hda_codec_hdmi     32474  1 
snd_hda_codec_realtek   223867  1 
rfcomm                 47604  0 
parport_pc             32866  0 
ppdev                  17113  0 
bnep                   18281  2 
bluetooth             180104  10 rfcomm,bnep
binfmt_misc            17540  1 
snd_hda_intel          33773  3 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                97188  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
psmouse                87603  0 
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
serio_raw              13211  0 
tpm_tis                18804  0 
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    78855  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
wmi                    19256  0 
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
mac_hid                13253  0 
i915                  468651  3 
mei                    41616  0 
drm_kms_helper         46978  1 i915
drm                   242038  4 i915,drm_kms_helper
i2c_algo_bit           13423  1 i915
video                  19596  1 i915
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
usbhid                 47199  0 
hid                    99559  1 usbhid
e1000e                156693  0 
quay@linuxmint ~ $ iwconfig
lo        no wireless extensions.


wlan0     IEEE 802.11g  ESSID:"HOME-1708"  
          Mode:Managed  Frequency:2.452 GHz  Access Point: 00:26:F3:5C:17:08   
          Bit Rate=162 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:65/100  Signal level:-54 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:412  Invalid misc:58159   Missed beacon:0


eth0      no wireless extensions.


quay@linuxmint ~ $ nm-tool


NetworkManager Tool


State: connected (global)


- Device: wlan0  [Auto HOME-1708] ----------------------------------------------
  Type:              802.11 WiFi
  Driver:            ndiswrapper
  State:             connected
  Default:           yes
  HW Address:        4C:60:DE:7D:7E:69


  Capabilities:
    Speed:           162 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    bri:             Infra, 2C:B0:5D:31:D6:0E, Freq 2412 MHz, Rate 54 Mb/s, Strength 45 WPA2
    NETGEAR46:       Infra, 4C:60:DE:DD:78:9A, Freq 2417 MHz, Rate 54 Mb/s, Strength 39 WPA2
    Judy:            Infra, 00:22:75:B7:DF:35, Freq 2437 MHz, Rate 54 Mb/s, Strength 30 WPA
    Spirit Creek:    Infra, 00:27:22:14:6C:91, Freq 2412 MHz, Rate 54 Mb/s, Strength 30 WPA2
    linksys:         Infra, 00:1C:10:91:E3:51, Freq 2437 MHz, Rate 11 Mb/s, Strength 75
    NETGEAR:         Infra, 00:24:B2:02:97:22, Freq 2412 MHz, Rate 54 Mb/s, Strength 34
    *HOME-1708:      Infra, 00:26:F3:5C:17:08, Freq 2462 MHz, Rate 54 Mb/s, Strength 67 WPA WPA2


  IPv4 Settings:
    Address:         10.0.0.6
    Prefix:          24 (255.255.255.0)
    Gateway:         10.0.0.1


    DNS:             75.75.76.76




- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            e1000e
  State:             unavailable
  Default:           no
  HW Address:        00:23:24:37:97:7E


  Capabilities:
    Carrier Detect:  yes


  Wired Properties
    Carrier:         off

---

### Post by varunendra on 2013-09-13
> **Socrat3s said:**
> Edit. Not sure why the smiley faces are in the output.
Because parsing certain character-sets as smileys is the default behaviour of the forum software. To avoid that, and to preserve the output's formatting, you can (and 'should') use 'Code' tags whenever posting commands and their outputs.

Please follow the "Using Code Tags" link in my signature to see how, and edit your post to wrap the output part in code tags now.

About your problem - I'm not good with ndiswrapper driver (not that I'm too good at others ;)), although there seem to be a few things that you may try changing.
> **Socrat3s said:**
> 
    *HOME-1708:      Infra, 00:26:F3:5C:17:08, Freq 2462 MHz, Rate 54 Mb/s, Strength 67 **[COLOR="#FF0000"]WPA WPA2[/COLOR]**


Usually, WPA/WPA2 mixed mode is not recommended for Linux drivers, but since you are using windows driver, I'm not sure if that matters.

The connection speed shows up as 162 Mb/s. I don't think an ndiswapper driver can handle that much. If your router supports N-channel, and it is enabled, you should try turning it off if you can (select b/g only mode).

If these don't help, please post the output of -
```
lsusb
```
So we can see your device and if there exists a linux driver that we may try.

---

