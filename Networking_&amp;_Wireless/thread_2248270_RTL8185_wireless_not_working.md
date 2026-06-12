---
title: "RTL8185 wireless not working"
date: 2014-10-13
forum: Networking &amp; Wireless
---

### Post by uPatrick on 2014-10-13
Hi,

I install lubuntu 14.04. I have a problem on my interface wireless.
I can get the IP from my router but, connect to internet is very slow.

couls you help ? is there any issue for wireless driver on rtl8185 ?

My system info
Linux patrick-VT82C694X 3.13.0-37-generic #64-Ubuntu SMP Mon Sep 22 21:30:01 UTC 2014 i686 i686 i686 GNU/Linux
Module                  Size  Used by
ctr                    12905  3 
ccm                    17496  3 
bnep                   18895  2 
rfcomm                 53664  0 
bluetooth             342208  10 bnep,rfcomm
snd_via82xx            28455  1 
snd_mpu401_uart        13865  1 snd_via82xx
snd_ac97_codec        105709  1 snd_via82xx
ac97_bus               12642  1 snd_ac97_codec
gameport               15189  1 snd_via82xx
snd_pcm                85501  2 snd_via82xx,snd_ac97_codec
snd_page_alloc         14230  2 snd_via82xx,snd_pcm
radeon               1420614  2 
snd_seq_midi           13132  0 
arc4                   12536  2 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_rawmidi            25135  2 snd_mpu401_uart,snd_seq_midi
rtl8180                35544  0 
snd_seq                55383  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
ttm                    72725  1 radeon
mac80211              546051  1 rtl8180
snd_timer              28584  2 snd_pcm,snd_seq
drm_kms_helper         48868  1 radeon
drm                   244037  4 ttm,drm_kms_helper,radeon
cfg80211              409394  2 mac80211,rtl8180
snd                    60939  11 snd_via82xx,snd_ac97_codec,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_mpu401_uart,snd_seq_device,snd_seq_midi
i2c_algo_bit           13197  1 radeon
eeprom_93cx6           13168  1 rtl8180
soundcore              12600  1 snd
via686a                19413  0 
i2c_viapro             13096  0 


00:00.0 Host bridge: VIA Technologies, Inc. VT82C693A/694x [Apollo PRO133x] (rev c4)
00:01.0 PCI bridge: VIA Technologies, Inc. VT82C598/694x [Apollo MVP3/Pro133x AGP]
00:07.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (rev 40)
00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:07.2 USB controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1a)
00:07.3 USB controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1a)
00:07.4 Bridge: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 40)
00:07.5 Multimedia audio controller: VIA Technologies, Inc. VT82C686 AC97 Audio Controller (rev 50)
00:09.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller (rev 20)
00:0b.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8100/8101L/8139 PCI Fast Ethernet Adapter (rev 10)
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] R100 [Radeon 7200 / All-In-Wonder Radeon]

wlan0     IEEE 802.11bg  ESSID:"BlackBean"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:14:D1:B1:64:1F   
          Bit Rate=24 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=65/100  Signal level=65/100  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:12  Invalid misc:11   Missed beacon:0

lo        no wireless extensions.

eth1      no wireless extensions.

---

### Post by howefield on 2014-10-13
You'll probably get more help in here "*Networking & Wireless*"

---

### Post by uPatrick on 2014-10-14
Any help ?

---

