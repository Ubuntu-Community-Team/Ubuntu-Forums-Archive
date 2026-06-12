---
title: "USB SpeedStream 5200 + Warty"
date: 2004-12-11
forum: Networking &amp; Wireless
---

### Post by notos on 2004-12-11
hi i am new to the linux world 

my first linux was redhat 7.0 (i didn't know that was linux :P)
the i used Mandrake 9.0b but i didn't learned anything of linux

then i tried with debian but was to hard to install now i am using Ubuntu Warty ^_^ i Happy its pretty user Friendly but now i have a problem

I cant connect to INTERNET i am using a National provider (I live in Mexico) called Telmex/telnor - infinitum it is basically an ADSL provider the gave me an modem but they dont give suport for linux :'( 

SO  now i don't know where to start in the configuration of my linux

I am using a Efficient Networks Speed Stream 5200 modem With interface for USB and Ethernet (I'm using the USB interfase because i don't have money for a ETH card :'()

So please don't say me to go and buy an ETH card :D

i readem some things and its suposed that my Card mus be in the dev directory en the /dev/usb/ttyASM0 (i think) but is not 

My Device is an On-board USB device 

does any one know how to Configure it?
Help some Advice will be Appreciated :D

i ve run  these command if it help ... to you to help me (wa? :P)

this is lsmod 
```
Module                  Size  Used by
proc_intf               3968  0 
freq_table              4356  0 
cpufreq_userspace       5336  0 
cpufreq_powersave       2048  0 
ipv6                  230020  12 
snd_maestro3           22824  3 
snd_ac97_codec         59268  1 snd_maestro3
snd_pcm_oss            48168  0 
snd_mixer_oss          16640  3 snd_pcm_oss
snd_pcm                85540  2 snd_maestro3,snd_pcm_oss
snd_page_alloc         11144  1 snd_pcm
snd_timer              23172  1 snd_pcm
snd                    50660  8 snd_maestro3,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9824  3 snd
uhci_hcd               29328  0 
usbcore               104292  3 uhci_hcd
pci_hotplug            30640  0 
via_agp                 8832  1 
agpgart                31784  1 via_agp
floppy                 54996  0 
pcspkr                  3816  0 
rtc                    12216  0 
md                     44744  0 
dm_mod                 51068  1 
capability              4872  0 
commoncap               7168  1 capability
parport_pc             32064  1 
lp                     10436  0 
parport                37320  2 parport_pc,lp
tsdev                   7168  0 
evdev                   9088  0 
ide_cd                 38276  0 
cdrom                  35872  1 ide_cd
mousedev               10124  1 
psmouse                17800  0 
ext3                  109544  1 
jbd                    54552  1 ext3
ide_generic             1664  0 
via82cxxx              13084  1 
ide_disk               16768  3 
ide_core              125272  4 ide_cd,ide_generic,via82cxxx,ide_disk
unix                   25904  655 
font                    8576  0 
vesafb                  6688  0 
cfbcopyarea             3968  1 vesafb
cfbimgblt               3200  1 vesafb
cfbfillrect             3712  1 vesafb

```

this is lsusb ^_^
```
Bus 001 Device 002: ID 067c:e240 Efficient Networks, Inc. 
Bus 001 Device 001: ID 0000:0000  

```

THX  in advance :D

---

### Post by notos on 2004-12-12
nobody  knows?

---

### Post by charleyramm on 2004-12-25
[QUOTE=notos]to go and buy an ETH card :D[/QUOTE]

 Sorry, but seriously. How much does an ethernet card cost over there? I am trying to setup a USB adsl modem right now, and it is a horrible experience.
 Good luck. 
 [-o<

---

