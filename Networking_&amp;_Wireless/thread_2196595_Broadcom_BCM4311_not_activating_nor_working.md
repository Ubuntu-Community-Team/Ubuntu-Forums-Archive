---
title: "Broadcom BCM4311 not activating nor working"
date: 2013-12-30
forum: Networking &amp; Wireless
---

### Post by dafuqmanlolz on 2013-12-30
Hey since i been installing ubuntu I've tryed to activate wireless but it won't work.

I keep pressing on the wireless button but it doesn't function on windows 7 it worked? What i do plz help.

---

### Post by praseodym on 2013-12-30
Please open a terminal with CTRL+ALT+T and show the outputs of these commands
```

uname -a
lspci -nnk | grep -iA2 net
lsmod
iwconfig
rfkill list
```
Does LAN work? What kind of computer is it?

---

### Post by dafuqmanlolz on 2013-12-30
ovidiu@ovidiu-HP-Compaq-nx7400-RW215US-ABA:~$ ```
uname -a
Linux ovidiu-HP-Compaq-nx7400-RW215US-ABA 3.8.0-29-generic #42~precise1-Ubuntu SMP Wed Aug 14 15:31:16 UTC 2013 i686 i686 i386 GNU/Linux
ovidiu@ovidiu-HP-Compaq-nx7400-RW215US-ABA:~$ lspci -nnk | grep -iA2 net

02:0e.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
    Subsystem: Hewlett-Packard Company NX7300 laptop [103c:30a2]
    Kernel driver in use: b44
--
10:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
    Subsystem: Hewlett-Packard Company BCM4311 802.11b/g Wireless LAN Controller [103c:1363]
    Kernel driver in use: b43-pci-bridge
ovidiu@ovidiu-HP-Compaq-nx7400-RW215US-ABA:~$ lsmod
Module                  Size  Used by
b44                    31223  0 
ssb_hcd                12781  0 
ssb                    51554  2 b44,ssb_hcd
bnep                   17852  2 
rfcomm                 38400  0 
bluetooth             211435  10 bnep,rfcomm
snd_hda_codec_si3054    12864  1 
snd_hda_codec_analog    75716  1 
snd_hda_intel          38819  2 
snd_hda_codec         118613  3 snd_hda_codec_si3054,snd_hda_codec_analog,snd_hda_intel
hp_wmi                 17748  0 
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                85934  3 snd_hda_codec_si3054,snd_hda_intel,snd_hda_codec
sparse_keymap          13658  1 hp_wmi
snd_seq_midi           13132  0 
coretemp               13324  0 
joydev                 17329  0 
snd_rawmidi            25157  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51593  2 snd_seq_midi,snd_seq_midi_event
pcmcia                 39854  0 
snd_timer              28931  2 snd_pcm,snd_seq
wmi                    18744  1 hp_wmi
snd_seq_device         14137  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    57014  14 snd_hda_codec_si3054,snd_hda_codec_analog,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i915                  550346  3 
ppdev                  12849  0 
lpc_ich                17048  0 
soundcore              12600  1 snd
snd_page_alloc         18398  2 snd_hda_intel,snd_pcm
drm_kms_helper         47749  1 i915
microcode              18433  0 
drm                   233935  4 i915,drm_kms_helper
i2c_algo_bit           13316  1 i915
parport_pc             27612  1 
yenta_socket           27427  0 
mac_hid                13077  0 
psmouse                82769  0 
serio_raw              13031  0 
pcmcia_rsrc            18367  1 yenta_socket
video                  19116  1 i915
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
hid_generic            12484  0 
usbhid                 46125  0 
hid                    83037  2 hid_generic,usbhid
usb_storage            48053  0 
ahci                   25631  2 
libahci                26336  1 ahci
firewire_ohci          35914  0 
firewire_core          62086  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
ovidiu@ovidiu-HP-Compaq-nx7400-RW215US-ABA:~$ iwconfig
lo        no wireless extensions.

eth4      no wireless extensions.

ovidiu@ovidiu-HP-Compaq-nx7400-RW215US-ABA:~$ rfkill list
0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
ovidiu@ovidiu-HP-Compaq-nx7400-RW215US-ABA:~$ rfkill list
0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
ovidiu@ovidiu-HP-Compaq-nx7400-RW215US-ABA:~$ no
no: command not found
ovidiu@ovidiu-HP-Compaq-nx7400-RW215US-ABA:~$ ^C
ovidiu@ovidiu-HP-Compaq-nx7400-RW215US-ABA:~$
```



It HP - Compaq-nx7400 on windows 7 wireless worked just by pressing the button to switch wireless and then enter the security code and thats all. 

Here it won't work please help I don't want to stick with windows!

---

### Post by praseodym on 2013-12-31
Install the package "linux-firmware-nonfree" via software-center and reboot

---

### Post by dafuqmanlolz on 2013-12-31
I got it in terminal cause it didn't exist in Software center then reboot?

---

### Post by praseodym on 2013-12-31
Yes

---

### Post by GeorgeLSpencer on 2013-12-31
I could not get this chipset to work with my Telstra modem using WPA-PSK, so instead I purchased a cheap Netgear WN2000RPT and obtain wireless through an ethernet connection. This is a bit roundabout, but works. The Netgear WN2000RPT is sold as a wireless network extender, but one of the modes allows wireles to connect with three ethernet hosts and this is the mode I used for the connection. If you follow this pathway, I suggest that you look for the extender on ebay, or similar, as I was able to obtain mine for thirty dollars.

---

### Post by wildmanne39 on 2013-12-31
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

