---
title: "Shows connection to working wi-fi but stopped connecting to internet"
date: 2015-05-09
forum: Networking &amp; Wireless
---

### Post by comutiny on 2015-05-09
I have been running Ubuntu 12.04 for several years, and it suddenly will not connect to our wireless internet. Firefox says the server was not found, and when I tried installing another browser through the software center, it could not connect to the internet. Other devices are able to connect, so it is not the router's fault. 

I don't have an ethernet cable handy, so I'm using another device to troubleshoot. 

Here's what I entered so far: 

cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
iwconfig
rfkill list all
lsmod


```
cat /etc/lsb-release; uname -alspci -nnk | grep -iA2 net
iwconfig
rfkill list all
lsmod


zora@zora-Aspire-3000:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.5 LTS"
Linux zora-Aspire-3000 3.2.0-83-generic-pae #120-Ubuntu SMP Wed Apr 29 15:55:27 UTC 2015 i686 athlon i386 GNU/Linux
zora@zora-Aspire-3000:~$ lspci -nnk | grep -iA2 net
00:04.0 Ethernet controller [0200]: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet [1039:0900] (rev 91)
    Subsystem: Acer Incorporated [ALI] Device [1025:0083]
    Kernel driver in use: sis900
--
00:0b.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
    Subsystem: AMBIT Microsystem Corp. TravelMate 2410 [1468:0312]
    Kernel driver in use: b43-pci-bridge
zora@zora-Aspire-3000:~$ iwconfig
lo        no wireless extensions.


wlan0     IEEE 802.11bg  ESSID:"fbi-surveilance-van"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: FE:F5:28:94:BE:7C   
          Bit Rate=48 Mb/s   Tx-Power=27 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-40 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:3   Missed beacon:0


eth0      no wireless extensions.


zora@zora-Aspire-3000:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
zora@zora-Aspire-3000:~$ lsmod
Module                  Size  Used by
nls_iso8859_1          12617  0 
nls_cp437              12751  0 
vfat                   17308  0 
fat                    55605  1 vfat
usb_storage            39646  0 
nls_utf8               12493  1 
udf                    84588  1 
crc_itu_t              12627  1 udf
vesafb                 13516  1 
joydev                 17393  0 
arc4                   12473  2 
snd_intel8x0           33455  3 
snd_ac97_codec        110213  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
b43                   342801  0 
snd_pcm                80916  3 snd_intel8x0,snd_ac97_codec
mac80211              436493  1 b43
snd_seq_midi           13132  0 
pcmcia                 39826  0 
psmouse                87048  0 
snd_rawmidi            25424  1 snd_seq_midi
serio_raw              13027  0 
cfg80211              178877  2 b43,mac80211
snd_seq_midi_event     14475  1 snd_seq_midi
k8temp                 12905  0 
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
yenta_socket           27465  0 
rfcomm                 38139  0 
pcmcia_rsrc            18367  1 yenta_socket
bnep                   17830  2 
parport_pc             32114  0 
bcma                   25651  1 b43
ppdev                  12849  0 
bluetooth             158447  10 rfcomm,bnep
binfmt_misc            17292  1 
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    62250  12 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              14635  1 snd
snd_page_alloc         14108  2 snd_intel8x0,snd_pcm
mac_hid                13077  0 
shpchp                 32265  0 
i2c_sis96x             12743  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
sis900                 22729  0 
ssb                    50691  1 b43




```

Next steps? Thanks!

---

### Post by praseodym on 2015-05-10
Please run the wireless-script from the sticky thread and show the outputs

Thanks

---

### Post by comutiny on 2015-05-10
I located an ethernet cable to connect to wired internet and then installed updates. Wi-fi is currently working. (Sorry, I'm new to forums and didn't see the sticky thread earlier.) Thank you

---

