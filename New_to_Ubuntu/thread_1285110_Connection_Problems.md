---
title: "Connection Problems"
date: 2009-10-07
forum: New to Ubuntu
---

### Post by Roger Allott on 2009-10-07
About a week ago, I got virgin media set up for broadband internet access. For the first few days I had no problems, but over the past couple of days I've had a recurring problem that I hope someone here can help me with.

It seems to be a problem only when I'm running ubuntu (jaunty 9.04) on my machine. I've thus far had no problems when I boot up in Windows Vista, which I'm obviously using right now to post this.

First of all, when I boot up ubuntu, I get the screen that says:
> **Unlock Keyring**
Enter password for default keyring to unlock

The application 'NetworkManager Applet' (usr/bin/nm-applet) wants access to the default keyring, but it is locked

Password: _____________

That's not too much of a grumble, but it would be nice for ubuntu to have access to this without me having to enter my keyring password every time I boot.

But the main problem is that it has problems connecting me. Sometimes it does, but many times it doesn't. And when it does, I can surf and do stuff online for a while (anything from a few minutes to quite a few hours), but then the internet crashes and I get the screen (see attachment) to try to reconnect.

It sometimes succeeds in reconnecting, but most of the time it doesn't, leaving me to reboot the PC (and sometimes the router) in order to continue online.

I ran some commands in terminal, and someone might find the output helpful in diagnosing my problem.

lshw -C network
```
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wmaster0
       version: 02
       serial: 00:1c:bf:67:45:74
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11abg
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: 01
       serial: 00:03:0d:89:33:d7
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI latency=0 module=r8169 multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: be:81:04:eb:19:56
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
```


lsmod
```
Module                  Size  Used by
i915                   67844  2 
drm                    96424  3 i915
binfmt_misc            16776  1 
ppdev                  15620  0 
bridge                 56212  0 
stp                    10500  1 bridge
bnep                   20224  2 
input_polldev          11912  0 
joydev                 18368  0 
lp                     17156  0 
parport                42220  2 ppdev,lp
snd_hda_intel         435252  8 
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                83076  5 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
arc4                    9856  2 
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi
ecb                    10752  2 
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                56880  7 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
iTCO_wdt               19108  0 
iTCO_vendor_support    11652  1 iTCO_wdt
pcspkr                 10496  0 
psmouse                61972  0 
intel_agp              34108  1 
agpgart                42696  3 drm,intel_agp
video                  25872  0 
output                 11008  1 video
serio_raw              13444  0 
snd                    62756  23 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15200  1 snd
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm
iwl3945                97912  0 
mac80211              217592  1 iwl3945
led_class              12036  1 iwl3945
cfg80211               38288  2 iwl3945,mac80211
usbhid                 42336  0 
usb_storage            99648  4 
r8169                  40836  0 
mii                    13312  1 r8169
vesafb                 13828  1 
fbcon                  46112  72 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
```


ndiswrapper -l
```
The program 'ndiswrapper' is currently not installed.  You can install it by typing:
sudo apt-get install ndiswrapper-common
bash: ndiswrapper: command not found
```


cat /etc/modprobe.d/blacklist
```
cat: /etc/modprobe.d/blacklist: No such file or directory
```


iwconfig
```
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:""  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Tx-Power=15 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.
```

---

### Post by ohzopants on 2009-10-07
I find that wicd is a terrific replacement for the gnome network manager.

It will solve your keyring prompt problem and I've found that it works a lot better than the gnome one when WPA and/or WPA2 are in use.

Give it a try:
```
 sudo apt-get install wicd
```

---

### Post by Roger Allott on 2009-10-08
> **ohzopants said:**
> I find that wicd is a terrific replacement for the gnome network manager.

It will solve your keyring prompt problem and I've found that it works a lot better than the gnome one when WPA and/or WPA2 are in use.

Give it a try:
```
 sudo apt-get install wicd
```

Thanks. That's certainly nicer that the gnome network manager, but it hasn't of course resolved my bigger problems regarding connection persistency.

---

### Post by ohzopants on 2009-10-09
"wireless connection persistency"... man, when you get that figured out please share!

Most of the time my laptop connects just fine, but other times I need to reboot a couple times for it to connect.

---

