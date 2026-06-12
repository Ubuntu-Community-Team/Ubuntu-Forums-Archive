---
title: "Wifi Problem -.-"
date: 2011-07-18
forum: New to Ubuntu
---

### Post by Kenta15 on 2011-07-18
Ok so yesterday i install ubuntu 11.04 on my laptop (e-machines) but first of all hi to all and sorry for my bad english (i speak spanish) my problem is not finding the wifi i can see it and connect to it too but in a couple of minute the wifi disconnect i try to connect again but it does the same thing it disconnect on a couple of minutes (Like 2 minutes or 1) i try using a diferent Wireles Manager like Wicd but the problem keeps going on and on can anyone recomend me something i'm almost frustated my classes are going to start soon and the only way to connect in the internet is via wifi please help

My wireless card is the following
> 00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
00:06.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2)
00:07.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 3)
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series]
02:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)
05:00.0 Ethernet controller: Atheros Communications AR8132 Fast Ethernet (rev c0)


Sincerely, Kenta15

---

### Post by computerandu on 2011-07-18
See,,if this post can help you:
[http://linux4every1.blogspot.com/2011/06/no-wireless-networks-in-ubuntu-1104.html](http://linux4every1.blogspot.com/2011/06/no-wireless-networks-in-ubuntu-1104.html)

---

### Post by Kenta15 on 2011-07-18
> **computerandu said:**
> See,,if this post can help you:
[http://linux4every1.blogspot.com/2011/06/no-wireless-networks-in-ubuntu-1104.html](http://linux4every1.blogspot.com/2011/06/no-wireless-networks-in-ubuntu-1104.html)

Ok thanks for replying i tried the first option and then restart my computer and even shutdown and it shows the same problem it connects then for a couple of minute the wifi is disconnected so i'm now trying the Alternate Solution #1 ill give the details of what happen when im done

EDIT: An error occur while trying to install firmware-b43-installer t show this
> E: firmware-b43-installer: subprocess installed post-installation script returned error exit status 1
is this soppuse to happen?

EDIT #2: I gave the restart anyways to complete the "update" but now i cant find the wifi around me its say " Device Not ready (firmware missing)

EDIT #3: I tried the Alternative #2 but i cant seen to find the "**blacklist bcm43xx"**

---

### Post by Kenta15 on 2011-07-18
Is there any other way?

---

### Post by computerandu on 2011-07-18
What is the output of: 
sudo rfkill list 

If there is any kind of block you may need to unblock it. Further info here: [http://computerandu.wordpress.com/2011/05/24/how-to-solve-no-wireless-network-in-ubuntu-11-04-centrino-wireless-n-1000/](http://computerandu.wordpress.com/2011/05/24/how-to-solve-no-wireless-network-in-ubuntu-11-04-centrino-wireless-n-1000/)

---

### Post by Kenta15 on 2011-07-18
It seen's that there's no kind of block
look:
> 1: brcmwl-1: Wireless LAN
    Soft blocked: no
    Hard blocked: no

---

### Post by robertc36 on 2011-07-18
I had a similar error with my wireless device and I found installing an updated kernel  helped.
I have this installed instead [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.39-rc5-oneiric/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.39-rc5-oneiric/)

You need to install headers all 
then headers for your architecture and then the image.

You need to remove the b43 installer first > sudo apt-get purge firmware-b43-installer

Hope that helps.

---

### Post by Kenta15 on 2011-07-18
> **robertc36 said:**
> I had a similar error with my wireless device and I found installing an updated kernel  helped.
I have this installed instead [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.39-rc5-oneiric/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.39-rc5-oneiric/")

You need to install headers all 
then headers for your architecture and then the image.

You need to remove the b43 installer first 

Hope that helps.
I remove the b43 installer and install the header all and the header for my architecture + the image but it keeps disconnecting from the wifi  and now asking me for the password i know im typing the password right so the password is not the problem :(

---

### Post by Kenta15 on 2011-07-18
What could i do?

---

### Post by Kenta15 on 2011-07-18
So no one cant help me?

---

### Post by Peter09 on 2011-07-19
Can you send the output of:
 
```
 
nm-tool

```

---

### Post by Kenta15 on 2011-07-19
Ok so i haded two results one while the wifi is connected and one while is gone disconected

While connected:
> NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            atl1c
  State:             connected
  Default:           yes
  HW Address:        00:23:5A:54:3F:F7

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.145
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             206.248.95.217
    DNS:             206.248.79.242


- Device: eth1  [Auto wifi] ----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            wl
  State:             connected
  Default:           no
  HW Address:        00:24:2B:91:CD:0F

  Capabilities:
    Speed:           54 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    *wifi:           Infra, 68:7F:74:52:C3:C4, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2
    wifi-guest:      Infra, 68:7F:74:52:C3:C5, Freq 2437 MHz, Rate 0 Mb/s, Strength 100
    RUTH/PC:         Infra, 94:0C:6D:FB:D2:D6, Freq 2437 MHz, Rate 54 Mb/s, Strength 40 WPA2

  IPv4 Settings:
    Address:         192.168.1.144
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             206.248.95.217
    DNS:             206.248.79.242


While Disconnected:
> NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            atl1c
  State:             connected
  Default:           yes
  HW Address:        00:23:5A:54:3F:F7

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.145
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             206.248.95.217
    DNS:             206.248.79.242


- Device: eth1 -----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            wl
  State:             disconnected
  Default:           no
  HW Address:        00:24:2B:91:CD:0F

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    wifi-guest:      Infra, 68:7F:74:52:C3:C5, Freq 2437 MHz, Rate 0 Mb/s, Strength 100
    RUTH/PC:         Infra, 94:0C:6D:FB:D2:D6, Freq 2437 MHz, Rate 54 Mb/s, Strength 40 WPA2
    wifi:            Infra, 68:7F:74:52:C3:C4, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2


---

### Post by Peter09 on 2011-07-19
Normally you will not get a wireless connection while you wired connection is established. From the data it shows that you have a wireless connection and that it is working. If you are having disconnections it may be because the signal is too weak. have you tried a different router / access point.

---

### Post by Kenta15 on 2011-07-19
Hmm that cant be it i'm right beside's the router
and no i havent try any other acces point cause i dont have another one

---

### Post by Kenta15 on 2011-07-20
If this help i have a wireless adapter from linksys cisco E1000 is that may be it?

---

### Post by Kenta15 on 2011-07-21
I change the security of my router thinking and hoping that the router was the problem but it seen that is not it keeps doing the same thing

---

### Post by Peter09 on 2011-07-21
Try deleting the access point from network manager. Click on the wireless icon and select edit connection. delete your wifi access point from the list. 

Iy should then go through the routine of establishing a connection again.

---

### Post by Kenta15 on 2011-07-21
Wow thanks Peter i deleted the access point and put it again, the wifi haven't disconnect in 10 minutes lets see if it stay like that... i didn't know the solution was that simple

---

### Post by Kenta15 on 2011-07-21
It got disconnect again >.<

---

### Post by Kenta15 on 2011-07-21
This are the driver's i have right now
> Module                  Size  Used by
ipt_MASQUERADE         12663  1 
xt_state               12514  1 
ipt_REJECT             12512  2 
xt_tcpudp              12531  4 
iptable_filter         12706  1 
nf_nat_h323            12749  0 
nf_conntrack_h323      52200  1 nf_nat_h323
nf_nat_pptp            12536  0 
nf_conntrack_pptp      13562  1 nf_nat_pptp
nf_conntrack_proto_gre    13353  1 nf_conntrack_pptp
nf_nat_proto_gre       12671  1 nf_nat_pptp
nf_nat_tftp            12420  0 
nf_conntrack_tftp      12817  1 nf_nat_tftp
nf_nat_sip             16922  0 
nf_conntrack_sip       24652  1 nf_nat_sip
nf_nat_irc             12542  0 
nf_conntrack_irc       13138  1 nf_nat_irc
nf_nat_ftp             12548  0 
nf_conntrack_ftp       13106  1 nf_nat_ftp
iptable_nat            12977  1 
nf_nat                  24827  9  ipt_MASQUERADE,nf_nat_h323,nf_nat_pptp,nf_nat_proto_gre,nf_nat_tftp,nf_nat_sip,nf_nat_irc,nf_nat_ftp,iptable_nat
nf_conntrack_ipv4      19024  4 iptable_nat,nf_nat
nf_conntrack            69744  18  ipt_MASQUERADE,xt_state,nf_nat_h323,nf_conntrack_h323,nf_nat_pptp,nf_conntrack_pptp,nf_conntrack_proto_gre,nf_nat_tftp,nf_conntrack_tftp,nf_nat_sip,nf_conntrack_sip,nf_nat_irc,nf_conntrack_irc,nf_nat_ftp,nf_conntrack_ftp,iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4         12649  1 nf_conntrack_ipv4
ip_tables              18125  2 iptable_filter,iptable_nat
x_tables               21907  7 ipt_MASQUERADE,xt_state,ipt_REJECT,xt_tcpudp,iptable_filter,iptable_nat,ip_tables
binfmt_misc            13213  1 
parport_pc             32111  0 
ppdev                  12849  0 
dm_crypt               22463  0 
snd_hda_codec_realtek   255820  1 
snd_hda_intel          24140  2 
snd_hda_codec          90901  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80244  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
lib80211_crypt_tkip    17203  0 
wl                   2642531  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
joydev                 17322  0 
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                     55295  13  snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                73312  0 
soundcore              12600  1 snd
sp5100_tco             13456  0 
serio_raw              12990  0 
k8temp                 12872  0 
i2c_piix4              13095  0 
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
lib80211               14570  2 lib80211_crypt_tkip,wl
shpchp                 32345  0 
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
dm_raid45              88410  0 
xor                    21860  1 dm_raid45
btrfs                 527341  0 
zlib_deflate           26594  1 btrfs
libcrc32c              12543  1 btrfs
radeon                896428  2 
ttm                    65184  1 radeon
drm_kms_helper         40745  1 radeon
pata_atiixp            12968  0 
drm                   180037  4 radeon,ttm,drm_kms_helper
ahci                   21591  2 
atl1c                  36237  0 
video                  18951  0 
libahci                25548  1 ahci
ati_agp                13202  0 
i2c_algo_bit           13184  1 radeon

---

### Post by Peter09 on 2011-07-22
Looking at the output of nm-tool

> Wireless Access Points (* = current AP)
*wifi: Infra, 68:7F:74:52:C3:C4, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2
wifi-guest: Infra, 68:7F:74:52:C3:C5, Freq 2437 MHz, Rate 0 Mb/s, Strength 100
RUTH/PC: Infra, 94:0C:6D:FB26, Freq 2437 MHz, Rate 54 Mb/s, Strength 40 WPA2

It suggests that you have  other access points within range, it may be worth changing the 'channel' parameter in your router to see if its an interference problem.

You will 'most probably' need to do the 'delete from network manager' thing again - a long shot but its worth a try.

---

### Post by Kenta15 on 2011-07-22
ok so ill try to change the 'channel' of the router  but i dont know how to... ill look it up and see what i can find

---

### Post by Kenta15 on 2011-07-22
Ok i manage to change the channel of my router now im testing the wifi... lets see if it improves

EDIT: Ok so it took more time to disconnect (4 minutes) but it still disconnect =|

---

