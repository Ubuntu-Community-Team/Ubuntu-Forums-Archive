---
title: "cd\dvd drive does not work since i upgraded to 9.10"
date: 2010-03-24
forum: New to Ubuntu
---

### Post by unknown23 on 2010-03-24
look here and please help me solve the problem

my dvd drive worked fine until i upgraded to 9.10

i can not find any solutions for this

and when you replay i am a beginner, so simplest instruction is best

00:00.0 Host bridge: VIA Technologies, Inc. VT8378 [KM400/A] Chipset Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8235 PCI Bridge
00:07.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 02)
00:08.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
01:00.0 VGA compatible controller: VIA Technologies, Inc. KM400/KN400/P4M800 [S3 UniChrome] (rev 01)
Module                  Size  Used by
binfmt_misc             8356  1 
ipt_MASQUERADE          2204  1 
iptable_nat             5500  1 
bridge                 47952  0 
stp                     2272  1 bridge
via                    40192  2 
drm                   159584  3 via
sha256_generic         11580  0 
aes_i586                8124  86 
aes_generic            27484  1 aes_i586
cbc                     3516  83 
dm_crypt               12928  1 
ipt_REJECT              2812  3 
ipt_LOG                 5344  1 
xt_limit                2176  2 
xt_tcpudp               2780  11 
xt_state                1820  9 
ipt_addrtype            2204  4 
ip6table_filter         3164  1 
ip6_tables             13004  1 ip6table_filter
snd_via82xx            23608  6 
arc4                    1660  2 
ecb                     2524  3 
gameport               11368  1 snd_via82xx
snd_mpu401_uart         6940  1 snd_via82xx
snd_via82xx_modem      11204  7 
nf_nat_irc              2012  0 
snd_seq_dummy           2656  0 
nf_conntrack_irc        4992  1 nf_nat_irc
snd_ac97_codec        101216  2 snd_via82xx,snd_via82xx_modem
snd_seq_oss            28576  0 
nf_nat_ftp              2652  0 
rt73usb                26336  0 
nf_nat                 17808  4 ipt_MASQUERADE,iptable_nat,nf_nat_irc,nf_nat_ftp
crc_itu_t               1852  1 rt73usb
i2c_viapro              7312  0 
snd_seq_midi            6432  0 
nf_conntrack_ipv4      13352  12 iptable_nat,nf_nat
rt2500usb              21152  0 
snd_rawmidi            22208  2 snd_mpu401_uart,snd_seq_midi
ac97_bus                1532  1 snd_ac97_codec
nf_defrag_ipv4          1756  1 nf_conntrack_ipv4
rt2x00usb              11548  2 rt73usb,rt2500usb
joydev                 10272  0 
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_pcm_oss            37920  0 
nf_conntrack_ftp        6880  1 nf_nat_ftp
rt2x00lib              29756  3 rt73usb,rt2500usb,rt2x00usb
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_mixer_oss          16028  3 snd_pcm_oss
nf_conntrack           67608  9 ipt_MASQUERADE,iptable_nat,xt_state,nf_nat_irc,nf_conntrack_irc,nf_nat_ftp,nf_nat,nf_conntrack_ipv4,nf_conntrack_ftp
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
via_ircc               24016  0 
input_polldev           3716  1 rt2x00lib
snd_pcm                75296  6 snd_via82xx,snd_via82xx_modem,snd_ac97_codec,snd_pcm_oss
iptable_filter          3100  1 
pcmcia                 36808  0 
ip_tables              11692  2 iptable_nat,iptable_filter
snd_timer              22276  2 snd_seq,snd_pcm
mac80211              181236  2 rt2x00usb,rt2x00lib
snd_page_alloc          9156  3 snd_via82xx,snd_via82xx_modem,snd_pcm
snd                    59204  32 snd_via82xx,snd_mpu401_uart,snd_via82xx_modem,snd_ac97_codec,snd_seq_oss,snd_rawmidi,snd_pcm_oss,snd_seq,snd_mixer_oss,snd_seq_device,snd_pcm,snd_timer
irda                  189564  1 via_ircc
yenta_socket           24168  1 
psmouse                56180  0 
soundcore               7264  3 snd
cfg80211               93052  2 rt2x00lib,mac80211
x_tables               16544  10 ipt_MASQUERADE,iptable_nat,ipt_REJECT,ipt_LOG,xt_limit,xt_tcpudp,xt_state,ipt_addrtype,ip6_tables,ip_tables
rsrc_nonstatic         11644  1 yenta_socket
pcmcia_core            35792  3 pcmcia,yenta_socket,rsrc_nonstatic
ppdev                   6688  0 
serio_raw               5280  0 
parport_pc             31940  1 
shpchp                 32272  0 
lp                      8964  0 
crc_ccitt               1852  1 irda
parport                35340  3 ppdev,parport_pc,lp
led_class               4096  1 rt2x00lib
ohci1394               29900  0 
video                  19188  0 
via_rhine              22212  0 
mii                     5212  1 via_rhine
floppy                 54916  0 
output                  2780  1 video
ieee1394               86596  1 ohci1394
via_agp                 7932  1 
agpgart                34988  2 drm,via_agp

---

### Post by jrev on 2010-03-24
the best is to check whether the driver has been changed with the new issue

Never update when everything works fine

---

### Post by unknown23 on 2010-03-24
how do i do this?

---

### Post by unknown23 on 2010-03-24
ok, i searched everywhere on the web to find a solution for this

many have the same problem

but no one has an answer on how to fix

my dvd drive worked just fine before i upgraded, now it does not

whats the deal, it should not be such a big deal to have your dvd drive work with your operating system

someone, please help

---

### Post by unknown23 on 2010-03-30
wow!

something so necessary and no one who really understands linux knows how to solve
!
wtf is that about?

---

