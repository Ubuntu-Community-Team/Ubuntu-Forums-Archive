---
title: "Slow WIFI connection"
date: 2011-05-17
forum: New to Ubuntu
---

### Post by Babyshark on 2011-05-17
Hi there,
 
I'm very new to Ubuntu. Last week I upgraded to Ubuntu 11.04 from 10.10. I noticed that the wifi connection is very slow. I don't think I have the right driver. I got a Linksys usb. I'm willing to take any suggestion. Thanks.

---

### Post by josephmills on 2011-05-17
> **Babyshark said:**
> Hi there,
 
I'm very new to Ubuntu. Last week I upgraded to Ubuntu 11.04 from 10.10. I noticed that the wifi connection is very slow. I don't think I have the right driver. I got a Linksys usb. I'm willing to take any suggestion. Thanks.

hi there could you please open up your terminal (ctrl+alt+t ) and type in ```
lsusb
``` this next one take some time to load bu it will ```
sudo lshw -C network
``` and paste here thanks

---

### Post by jtarin on 2011-05-18
> **Babyshark said:**
> Hi there,
 
I'm very new to Ubuntu. Last week I upgraded to Ubuntu 11.04 from 10.10. I noticed that the wifi connection is very slow. I don't think I have the right driver. I got a Linksys usb. I'm willing to take any suggestion. Thanks.After you respond to josephmills questions could you tell me what your speed was in 10.10 and what is now? Did you notice the speed difference immediatly or gradually? Who is your ISP? Can you also hardwire to them?

---

### Post by Babyshark on 2011-05-18
> **josephmills said:**
> hi there could you please open up your terminal (ctrl+alt+t ) and type in ```
lsusb
``` this next one take some time to load bu it will ```
sudo lshw -C network
``` and paste here thanks


usrpc04@PC04:~$ lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 13b1:0020 Linksys WUSB54GC v1 802.11g Adapter [Ralink RT73]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
usrpc04@PC04:~$ sudo lshw -C network
[sudo] password for usrpc04: 
  *-network               
       description: Ethernet interface
       product: 82801DB PRO/100 VE (LOM) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 81
       serial: 00:09:6b:e1:d7:52
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=half firmware=N/A latency=66 link=no maxlatency=56 mingnt=8 multicast=yes port=MII speed=10Mbit/s
       resources: irq:20 memory:c0100000-c0100fff ioport:2000(size=64)
  *-network
       description: Wireless interface
       physical id: 2
       bus info: usb@1:4
       logical name: wlan0
       serial: 00:1d:7e:94:57:72
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rt73usb driverversion=2.6.38-8-generic firmware=1.7 ip=192.168.1.2 link=yes multicast=yes wireless=IEEE 802.11bg
usrpc04@PC04:~$

---

### Post by josephmills on 2011-05-18
after jtarin ? could we see a ```
dmesg | grep rt
``` then a ```
lsmod
``` thanks

---

### Post by Babyshark on 2011-05-18
> **jtarin said:**
> After you respond to josephmills questions could you tell me what your speed was in 10.10 and what is now? Did you notice the speed difference immediatly or gradually? Who is your ISP? Can you also hardwire to them?


Hi jtarin i didn't record the speed when I was in 10.10, but I noticed when I load the web browser (firefox 4.0.1) in 10.10, it loaded within 1 or 2 second and in 11.04 it takes about 10 to 15 second or longer.  The speed different is noticeable. I have Rogers as ISP.

---

### Post by Babyshark on 2011-05-18
> **josephmills said:**
> after jtarin ? could we see a ```
dmesg | grep rt
``` then a ```
lsmod
``` thanks

usrpc04@PC04:~$ dmesg | grep rt
[10262.282948] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[11256.832133] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[11359.232098] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[19249.547451] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[24565.752118] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[26061.090728] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[27495.466629] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[27674.606152] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[27816.728577] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[27863.728466] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[28112.016521] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[28216.995275] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[28450.862781] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[28638.260550] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[29677.421666] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[30573.555917] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[31401.868421] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[33085.633599] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[34089.019164] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[37625.918263] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[37756.831780] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[37807.235134] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[39203.244386] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[41603.207972] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[42582.411351] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[42638.008158] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[44192.204364] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[47495.168571] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[47676.133026] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[47791.939457] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[47851.342699] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[48016.119964] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
usrpc04@PC04:~$ lsmod
Module                  Size  Used by
cryptd                 19801  0 
aes_i586               16956  1 
aes_generic            38023  1 aes_i586
binfmt_misc            13213  1 
arc4                   12473  2 
snd_intel8x0           33213  2 
snd_ac97_codec        105614  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80244  2 snd_intel8x0,snd_ac97_codec
rt73usb                26854  0 
snd_seq_midi           13132  0 
i915                  450944  2 
crc_itu_t              12627  1 rt73usb
snd_rawmidi            25269  1 snd_seq_midi
rt2x00usb              19693  1 rt73usb
rt2x00lib              39075  2 rt73usb,rt2x00usb
mac80211              257001  2 rt2x00usb,rt2x00lib
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
ppdev                  12849  0 
drm_kms_helper         40745  1 i915
snd_timer              28659  2 snd_pcm,snd_seq
cfg80211              156212  2 rt2x00lib,mac80211
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
drm                   180037  2 i915,drm_kms_helper
psmouse                73312  0 
parport_pc             32111  1 
snd                    55295  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw              12990  0 
soundcore              12600  1 snd
i2c_algo_bit           13184  1 i915
shpchp                 32345  0 
snd_page_alloc         14073  2 snd_intel8x0,snd_pcm
video                  18951  1 i915
lp                     13349  0 
parport                36746  3 ppdev,parport_pc,lp
e100                   40108  0 
floppy                 60032  0 
usrpc04@PC04:~$ dmesg | grep rtdmesg | grep rtdmesg | grep rtdmesg | grep rtdmesg | grep rt

---

### Post by jtarin on 2011-05-18
Yea they did an update to 10.10 about the 19th of April that was a noticeable speed and accuracy improvment. I would be hard pressed to give up 10.10 now. You guys can have 11.o4 and be welcome to it.

---

### Post by Babyshark on 2011-05-18
> **jtarin said:**
> Yea they did an update to 10.10 about the 19th of April that was a noticeable speed and accuracy improvment. I would be hard pressed to give up 10.10 now. You guys can have 11.o4 and be welcome to it.
 
 
So your suggestion is to stick with 10.10 for now?  Anyway, thank you guys (**josephmills and jtarin) **for your help.

---

### Post by jtarin on 2011-05-18
> **Babyshark said:**
> So your suggestion is to stick with 10.10 for now?  Anyway, thank you guys (**josephmills and jtarin) **for your help.
Unless there is something you can't live without in 11.04 at this point I see no reason for me.....to upgrade, unless it's the eyecandy. I was hesitant in upgrading to 10.10 from 10.04, but glad I did after several months of it being tested and not seeing the problems that 11.04 is encountering.

---

