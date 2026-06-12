---
title: "Ralink unclaimed after changing pci port."
date: 2013-12-05
forum: Networking &amp; Wireless
---

### Post by panthertehcat on 2013-12-05
I have an issue where I moved my Ralink card to a different pci port it now shows up as unclaimed in sudo lshw -C, itwas previously working before this change. A lot of other threads seem to involve downloading and compiling drivers, however I'd prefer to just use the defaults that came with 13.10 as they where working previously. System is a Ubuntu 13.10 32 bit. 

Outputs:
sudo lshw -C
*-network UNCLAIMED
       description: Network controller
       product: Ralink corp.
       vendor: Ralink corp.
       physical id: 2
       bus info: pci@0000:04:02.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=64 maxlatency=4 mingnt=2
       resources: memory:ceaf0000-ceafffff

lsmod
Module                  Size  Used by
vesafb                 13500  1 
gpio_ich               13229  0 
ppdev                  17391  0 
rfcomm                 53664  0 
bnep                   18893  2 
dcdbas                 14383  0 
bluetooth             323622  10 bnep,rfcomm
snd_hda_codec_hdmi     40373  1 
snd_hda_intel          42658  2 
snd_hda_codec         164003  2 snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13272  1 snd_hda_codec
snd_pcm                89488  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_rawmidi            25094  1 snd_seq_midi
microcode              18830  0 
snd_seq                55383  2 snd_seq_midi_event,snd_seq_midi
psmouse                90642  0 
serio_raw              13189  0 
lpc_ich                16864  0 
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
joydev                 17097  0 
snd_timer              24447  2 snd_pcm,snd_seq
fglrx                6984493  108 
snd                    60790  14 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
soundcore              12600  1 snd
parport_pc             31981  1 
mac_hid                13037  0 
lp                     13299  0 
parport                40795  3 lp,ppdev,parport_pc
hid_microsoft          12693  0 
hid_generic            12492  0 
usbhid                 47361  0 
hid                    87370  3 hid_generic,hid_microsoft,usbhid
tg3                   152066  0 
ptp                    18156  1 tg3
pps_core               18546  1 ptp

lspci -v
04:02.0 Network controller: Ralink corp. Device 2062
    Subsystem: Ralink corp. Device 2062
    Flags: bus master, slow devsel, latency 64, IRQ 3
    Memory at ceaf0000 (32-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>

---

### Post by panthertehcat on 2013-12-05
must have been something up with the connection as I unplugged and replugged the pci card a couple of times and wiped down the contacts. Or it could have been the 6 reboots. It seems to work now go figure.

---

