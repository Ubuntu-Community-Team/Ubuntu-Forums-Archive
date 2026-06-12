---
title: "dell-wifi, phy0, and brcmwl-0: Do I have too many drivers loaded?"
date: 2013-09-30
forum: Networking &amp; Wireless
---

### Post by Kirk Schnable on 2013-09-30
I'm troubleshooting [a connectivity issue that has arisen with my Broadcom cards]("http://ubuntuforums.org/showthread.php?t=2176483").

I would like to make sure I am not making a simple mistake, such as having too many\conflicting drivers loaded on my system.

Here is the output of my "rfkill list all":
```
# rfkill list all
0: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
```

Here is the output of my "lsmod":
```
# lsmod
Module                  Size  Used by
promethean             47575  0 
nf_conntrack_ipv4      19084  1 
nf_defrag_ipv4         12649  1 nf_conntrack_ipv4
xt_state               12514  1 
nf_conntrack           73847  2 nf_conntrack_ipv4,xt_state
xt_tcpudp              12531  2 
iptable_filter         12706  1 
ip_tables              18106  1 iptable_filter
x_tables               22011  4 xt_state,xt_tcpudp,iptable_filter,ip_tables
bnep                   17830  2 
rfcomm                 38139  0 
bluetooth             158447  10 bnep,rfcomm
parport_pc             32114  0 
ppdev                  12849  0 
snd_hda_codec_realtek   174313  1 
snd_hda_intel          32719  4 
snd_hda_codec         109562  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80916  2 snd_hda_intel,snd_hda_codec
lib80211_crypt_tkip    17240  0 
snd_seq_midi           13132  0 
wl                   2906597  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
uvcvideo               67203  0 
i915                  428021  3 
snd_timer              28931  2 snd_pcm,snd_seq
videodev               86588  1 uvcvideo
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
drm_kms_helper         45466  1 i915
drm                   197641  4 i915,drm_kms_helper
cfg80211              178877  1 wl
joydev                 17393  0 
snd                    62218  17 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
dell_laptop            17767  0 
rts_pstor             353252  0 
mac_hid                13077  0 
i2c_algo_bit           13199  1 i915
lib80211               14040  2 lib80211_crypt_tkip,wl
dcdbas                 14098  1 dell_laptop
video                  19115  1 i915
sparse_keymap          13658  0 
soundcore              14635  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
psmouse                96744  0 
serio_raw              13027  0 
binfmt_misc            17292  1 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
tg3                   141465  0
```

"lshw -C network" says:  (MAC address intentionally omitted)
```
  *-network               
       description: Wireless interface
       product: BCM43228 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: eth1
       version: 00
       serial: ##:##:##:##:##:##
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=6.20.155.1 (r326264) latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:17 memory:f6cfc000-f6cfffff
```

Here are some syslog entries (with omitted information for privacy reasons) which make me suspect a driver problem:
```
Sep 30 10:26:29 Hostname wpa_supplicant[948]: Trying to associate with ##:##:##:##:##:## (SSID='OurSSID' freq=2462 MHz)
Sep 30 10:26:29 Hostname wpa_supplicant[948]: Association request to the driver failed
Sep 30 10:26:29 Hostname NetworkManager[877]: <info> (eth1): supplicant interface state: scanning -> associating
Sep 30 10:26:34 Hostname wpa_supplicant[948]: Authentication with ##:##:##:##:##:## timed out.
Sep 30 10:26:34 Hostname NetworkManager[877]: <info> (eth1): supplicant interface state: associating -> scanning
Sep 30 10:26:36 Hostname wpa_supplicant[948]: Trying to associate with ##:##:##:##:##:## (SSID='OurSSID' freq=2412 MHz)
Sep 30 10:26:36 Hostname wpa_supplicant[948]: Association request to the driver failed
Sep 30 10:26:36 Hostname NetworkManager[877]: <info> (eth1): supplicant interface state: scanning -> associating
Sep 30 10:26:41 Hostname wpa_supplicant[948]: Authentication with ##:##:##:##:##:## timed out.
Sep 30 10:26:41 Hostname NetworkManager[877]: <info> (eth1): supplicant interface state: associating -> scanning
Sep 30 10:26:44 Hostname wpa_supplicant[948]: Trying to associate with ##:##:##:##:##:## (SSID='OurSSID' freq=2412 MHz)
Sep 30 10:26:44 Hostname wpa_supplicant[948]: Association request to the driver failed
Sep 30 10:26:44 Hostname NetworkManager[877]: <info> (eth1): supplicant interface state: scanning -> associating
```


I'd really like to come up with a resolution to this, as it's affecting a lot of our machines.

Thanks in advance for any input!

---

