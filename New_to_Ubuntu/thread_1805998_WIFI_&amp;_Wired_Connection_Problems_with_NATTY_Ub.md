---
title: "WIFI &amp; Wired Connection Problems with NATTY Ubuntu 11.04"
date: 2011-07-17
forum: New to Ubuntu
---

### Post by novelty07 on 2011-07-17
Hi Doctor
Relatively new-ish to Ubuntu and Linux systems. I just upgraded from 10.10 LTS (lucid) to 11.04 Natty (complete re-partition from scratch- so no leftovers). Now I have some pretty serious problems with NATTY 's wifi

1. I could not signal in the rooms I was getting wifi signal previously with 10.10 LTS. I rummaged around the forums and the internet a lot. Tried several things but nothing worked.

2. So I resigned myself to using the laptop in the same room as my wifi router (pointless tho). Now yesterday after downloading some files overnight. I switched it on and it will not connect to the router at all & not even the wired connection.

PLEASE HELP ME.. From my 2 weeks of reading and re-reading on the net about wifi & natty . I have put in the outputs of lspci & lsmod commands


lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
06:08.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
06:09.0 CardBus bridge: Texas Instruments PCI7420 CardBus Controller
06:09.2 FireWire (IEEE 1394): Texas Instruments PCI7x20 1394a-2000 OHCI Two-Port PHY/Link-Layer Controller
06:09.3 Mass storage controller: Texas Instruments PCI7420/7620 Combo CardBus, 1394a-2000 OHCI and SD/MS-Pro Controller
06:0a.0 Ethernet controller: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter (rev 01)



lsmod
Module                  Size  Used by
usb_storage            43946  0 
uas                    17676  0 
binfmt_misc            13213  1 
parport_pc             32111  0 
ppdev                  12849  0 
snd_hda_codec_realtek   255820  1 
snd_hda_intel          24140  2 
snd_hda_codec          90901  2 snd_hda_codec_realtek,snd_hda_intel
arc4                   12473  2 
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80244  2 snd_hda_intel,snd_hda_codec
i915                  450944  3 
snd_seq_midi           13132  0 
ath5k                 144412  0 
snd_rawmidi            25269  1 snd_seq_midi
ath                    19141  1 ath5k
mac80211              257001  1 ath5k
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
drm_kms_helper         40745  1 i915
tifm_sd                17415  0 
pcmcia                 39671  0 
joydev                 17322  0 
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
drm                   180037  4 i915,drm_kms_helper
cfg80211              156212  3 ath5k,ath,mac80211
tifm_7xx1              12898  0 
yenta_socket           27230  0 
sony_laptop            34432  0 
snd                    55295  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
tifm_core              15040  2 tifm_sd,tifm_7xx1
psmouse                73312  0 
pcmcia_rsrc            18292  1 yenta_socket
pcmcia_core            21505  3 pcmcia,yenta_socket,pcmcia_rsrc
i2c_algo_bit           13184  1 i915
serio_raw              12990  0 
soundcore              12600  1 snd
video                  18951  1 i915
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
firewire_ohci          31504  0 
8139too                23208  0 
firewire_core          56138  1 firewire_ohci
8139cp                 22497  0 
crc_itu_t              12627  1 firewire_core

---

### Post by wildmanne39 on 2011-07-17
Hi, try this in a terminal
```
rfkill unblock wifi
```
```
sudo ifconfig wlan0 down
```
```
sudo ifconfig wlan0 up
```
and post the outcome  here by clicking on new reply and click # and paste the information between the brackets.

that should turn the wireless back on.
There is a bug report on that wireless card where it turns its self off and has to be manually turned back on.

---

### Post by novelty07 on 2011-07-17
Thanks for this buddy.

But I lost my patience a few hours back and re-installed Natty. WiFi is now working in the same room.

I am still updating the system (i.e. installing vlc, chrome, vuze, wine , etc) . So I will take it to the other room in a while.

Would you have any suggestions as to why the signal would be poor (not able to catch or detect it) in another room. Where I used to get excellent signal with Lucid?

Thanks again.

---

### Post by amjjawad on 2011-07-17
> **novelty07 said:**
> Would you have any suggestions as to why the signal would be poor (not able to catch or detect it) in another room. Where I used to get excellent signal with Lucid?

Thanks again.

It could be the driver. I have had an issue with a previous driver, I think was rt2800 or something. I then removed it and I'm now using another driver. MUCH better than the previous one. I used to have lots of disconnections and slow internet with the old driver.

---

### Post by novelty07 on 2011-07-17
Its official.

It does not work in the other room. Any help dude?

Btw, you mentioned you changed the drivers? how did you do that? Please explain step by step as I am relatively a noob.

Thanks in advance.

LostInNatty Gone Nutty

---

### Post by amjjawad on 2011-07-17
> **novelty07 said:**
> Btw, you mentioned you changed the drivers? how did you do that? Please explain step by step as I am relatively a noob.


This is how.
[http://ubuntuforums.org/showthread.php?t=1643545](http://ubuntuforums.org/showthread.php?t=1643545)

**Note that, the driver in your case may be different.**

---

### Post by novelty07 on 2011-07-17
YES .. This WORKED

Finally.. It is still a bit weak in the room. BUT IT WORKS LIKE A CHARM..

here is the solution - 
The problem is with the Atheros 5001x onboard card conflict.```
sudo su
apt-get install subversion
cd /usr/src
svn checkout http://madwifi-project.org/svn/madwifi/trunk madwifi
tar cfvz madwifi.tgz 
cd madwifi
make && make install
 
echo "blacklist ath5k" >> /etc/modprobe.d/blacklist.conf
echo "ath_pci" >> /etc/modules
 
modprobe ath_pci

sudo reboot
```

original thread [http://ubuntuforums.org/showthread.php?p=10884683](http://ubuntuforums.org/showthread.php?p=10884683)

Hope this works for you all.. Thanks very very much guys for your help..

Now if I can get the sound to work as loudly as in Lucid & Graphics in VLC improve.. I am sorted.. yay!!!

---

### Post by amjjawad on 2011-07-17
Congratulation :)

Well done!

---

### Post by wildmanne39 on 2011-07-17
Hi, I am glad you got it fixed nice job amjjawad.

---

### Post by amjjawad on 2011-07-17
> **wildmanne39 said:**
> Hi, I am glad you got it fixed nice job amjjawad.

I'm still learning my friend :)

---

### Post by novelty07 on 2011-10-26
Just wanted to update you guys.

This fix works for Oneiric Ocelot as well.

Good luck

---

### Post by amjjawad on 2011-10-26
> **novelty07 said:**
> Just wanted to update you guys.

This fix works for Oneiric Ocelot as well.

Good luck

Glad to know that :)
Thanks a lot for keeping us updated, appreciate that :)

---

