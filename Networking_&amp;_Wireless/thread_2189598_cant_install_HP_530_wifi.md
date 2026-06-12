---
title: "cant install HP 530 wifi"
date: 2013-11-23
forum: Networking &amp; Wireless
---

### Post by mhsoliman on 2013-11-23
Hi,

  I am not able to get install the wifi for HP 530 laptop.  I had ubuntu 10 and I instaled 12.04.3 and selected the upgrade option to keep the application and drivers, but when the installation finished, the wifi driver is not there.
I tried to follow the steps in the post [http://askubuntu.com/questions/367172/hp-530-ubuntu-12-04-no-wireless](http://askubuntu.com/questions/367172/hp-530-ubuntu-12-04-no-wireless) but this leaded me to another problem and ddint resolve the wifi.
Now i keep getting this error : " Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?"

And the wifi driver is still not there.

Any help pls.

---

### Post by praseodym on 2013-11-23
For the error: Reboot.

For wireless, please show the terminal outputs of
```

uname -a
lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
rfkill list
```Does LAN work?

---

### Post by varunendra on 2013-11-24
..and if a simple reboot doesn't make the "lock" error go away, delete the lock file -
```
sudo rm /var/lib/dpkg/lock
```

But for the wireless issue, just post what praseodym asked

---

### Post by mhsoliman on 2013-12-12
Hi [**[COLOR=#000000]praseodym[/COLOR]**]("http://ubuntuforums.org/member.php?u=1411497"), 
The output of the file code:
Linux soliman-HP-530-Notebook-PC-GU324AA-ABV 3.8.0-33-generic #48~precise1-Ubuntu SMP Thu Oct 24 16:31:16 UTC 2013 i686 i686 i386 GNU/Linux
02:08.0 Ethernet controller [0200]: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller Mobile [8086:1068] (rev 01)
    Subsystem: Hewlett-Packard Company Device [103c:30d5]
    Kernel driver in use: e100
--
10:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
    Subsystem: Hewlett-Packard Company BCM4311 802.11b/g Wireless LAN Controller [103c:1364]
    Kernel driver in use: wl
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Module                  Size  Used by
bnep                   17852  2 
rfcomm                 38400  0 
bluetooth             211552  10 bnep,rfcomm
parport_pc             27612  0 
ppdev                  12849  0 
snd_hda_codec_conexant    52645  1 
wl                   3028038  1 
snd_hda_intel          38819  2 
snd_hda_codec         118650  2 snd_hda_codec_conexant,snd_hda_intel
coretemp               13324  0 
i915                  550464  3 
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                85934  2 snd_hda_intel,snd_hda_codec
joydev                 17329  0 
snd_seq_midi           13132  0 
pcmcia                 39854  0 
snd_rawmidi            25157  1 snd_seq_midi
drm_kms_helper         47749  1 i915
snd_seq_midi_event     14475  1 snd_seq_midi
hp_wmi                 17748  0 
drm                   233935  4 i915,drm_kms_helper
snd_seq                51593  2 snd_seq_midi,snd_seq_midi_event
sparse_keymap          13658  1 hp_wmi
snd_timer              28931  2 snd_pcm,snd_seq
yenta_socket           27427  0 
psmouse                82769  0 
snd_seq_device         14137  3 snd_seq_midi,snd_rawmidi,snd_seq
microcode              18433  0 
serio_raw              13031  0 
pcmcia_rsrc            18367  1 yenta_socket
cfg80211              453919  1 wl
lpc_ich                17048  0 
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
snd                    57014  13 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_algo_bit           13316  1 i915
soundcore              12600  1 snd
snd_page_alloc         18398  2 snd_hda_intel,snd_pcm
lib80211               14040  1 wl
wmi                    18744  1 hp_wmi
video                  19116  1 i915
mac_hid                13077  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
e100                   36175  0 
0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no

The Lan works fine.

---

### Post by mhsoliman on 2013-12-12
Thank you [B][Varun]("https://wiki.ubuntu.com/Varunendra"), the unlock worked after deleting the file.

[/B]

---

### Post by varunendra on 2013-12-12
Your wireless card is BCM4311 and the driver "wl" is incorrect for it.

While you are connected via LAN cable, please open a terminal, and do -
```
sudo apt-get purge bcmwl-kernel-source
sudo apt-get install linux-firmware-nonfree
```
..and reboot. You should have a working wifi on next boot. If not, please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates.

**PS:**
Terminal commands & outputs should always be posted within '**Code**' tags to preserve their formatting and make the post compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Using Code Tags" link in my signature.

---

### Post by mhsoliman on 2013-12-12
Thank you very much [B][Varun]("https://wiki.ubuntu.com/Varunendra"), Wifi working fine after reboot.

[/B]

---

### Post by varunendra on 2013-12-12
Fantastic!

Please mark the thread as [SOLVED]. It helps others by indicating that this thread contains a solution to its topic. :)

---

