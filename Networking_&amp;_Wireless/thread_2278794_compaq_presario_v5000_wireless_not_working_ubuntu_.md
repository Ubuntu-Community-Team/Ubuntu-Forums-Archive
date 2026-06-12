---
title: "compaq presario v5000 wireless not working ubuntu 10.04"
date: 2015-05-19
forum: Networking &amp; Wireless
---

### Post by dena_izbornik on 2015-05-19
Hi everyone
First I tried to install ubuntu 14.04, on my very old compaq presario  v5000, but computer was very slow(0nly 512 mb ram, 128MB shared for video card), but with 10.04 everything works fine  except  wireless card.
I reed all posts here regarding that matter, but without success.

Here are results from terminal

```

peder@peder-laptop:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.4 LTS"
Linux peder-laptop 2.6.32-74-generic #142-Ubuntu SMP Tue Apr 28 10:02:35 UTC 2015 i686 GNU/Linux
peder@peder-laptop:~$ sudo lshw -C network
[sudo] password for peder: 
  *-network:0             
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:06:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64
       resources: irq:21 memory:c0200000-c0201fff
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 6
       bus info: pci@0000:06:06.0
       logical name: eth0
       version: 10
       serial: 00:16:d4:45:f5:ec
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.5 latency=128 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
       resources: irq:22 ioport:a000(size=256) memory:c0202000-c02020ff
  *-network DISABLED
       description: Wireless interface
       physical id: 3
       logical name: wlan0
       serial: 00:14:a5:ef:28:c9
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
peder@peder-laptop:~$ lspci -nn | grep -e 0280 -e 0200
06:02.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
06:06.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
``````

peder@peder-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
``````

peder@peder-laptop:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
peder@peder-laptop:~$ lsmod
Module                  Size  Used by
binfmt_misc             6523  1 
ppdev                   5259  0 
snd_atiixp             12446  2 
snd_atiixp_modem        9103  5 
snd_ac97_codec        100646  2 snd_atiixp,snd_atiixp_modem
arc4                    1153  2 
ac97_bus                1002  1 snd_ac97_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_seq_dummy           1338  0 
snd_pcm                70694  6 snd_atiixp,snd_atiixp_modem,snd_ac97_codec,snd_pcm_oss
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
snd_seq_oss            26722  0 
b43                   163556  0 
vgastate                8961  1 vga16fb
snd_seq_midi            4557  0 
mac80211              205434  1 b43
snd_rawmidi            19056  1 snd_seq_midi
radeon                678607  3 
cfg80211              126528  2 b43,mac80211
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
ttm                    49847  1 radeon
snd_seq                47295  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
drm_kms_helper         29361  1 radeon
snd_timer              19130  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54696  23 snd_atiixp,snd_atiixp_modem,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm                   163779  5 radeon,ttm,drm_kms_helper
i2c_algo_bit            5028  1 radeon
soundcore               6620  1 snd
i2c_piix4               8335  0 
ati_agp                 5094  0 
shpchp                 28835  0 
snd_page_alloc          7076  3 snd_atiixp,snd_atiixp_modem,snd_pcm
k8temp                  3152  0 
led_class               2864  1 b43
psmouse                63677  0 
agpgart                31724  3 ttm,drm,ati_agp
video                  17375  0 
output                  1871  1 video
serio_raw               3978  0 
joydev                  8740  0 
lp                      7028  0 
parport                32635  2 ppdev,lp
usbhid                 36110  0 
hid                    68295  1 usbhid
8139too                18545  0 
8139cp                 16186  0 
pata_atiixp             3148  2 
mii                     4381  2 8139too,8139cp
ssb                    38934  1 b43
peder@peder-laptop:~$ 

```

Any help is highly appreciated.

Thanks

---

### Post by mörgæs on 2015-05-19
Hi, welcome to the fora.
Don't use 10.04, not even for old hardware. Please see the link in my signature for more info.

---

### Post by ajgreeny on 2015-05-19
Lubuntu will run reasonably well on that machine; Ubuntu has no chance!

---

### Post by dena_izbornik on 2015-05-19
thanks for answers, and suggestions, but I would like to stick to 10.04, because everything working really good except  WLAN

---

### Post by mörgæs on 2015-05-19
Then chances are that it also works good in Lubuntu 14.04.2 / 15.04.

---

### Post by dena_izbornik on 2015-05-19
I tried already to install 14.04, but comp is very, very slow - almost useless, and WLAN was not working as well.
As per minimum system requirements, latest ubuntu which matching my hardware is 10.04 - that's why I installed it, and is working really good, except WLAN.

---

### Post by Pilot6 on 2015-05-19
Lubuntu 14.04 also matches your requirements, and it wont't be slower that Ubuntu 10.04.

---

### Post by dena_izbornik on 2015-05-19
ok will try with lubuntu, if no alternatives.
Anyway it will be nice if someone can take a look in terminal output, and give mi some tips, or advice that I can continue digging.

Thanks

---

### Post by ajgreeny on 2015-05-19
I'm afraid you will set yourself an insoluble problem if you insist on keeping 10.04 as you will not be able to install any packages from the repos without rewriting the sources.list file to the end-of -life URLs, and even then you will not find any more updates.

---

### Post by dena_izbornik on 2015-05-20
OK
I installed Lubuntu 14.04, but WLAN still not working.
Any advice about next step?

thanks

---

### Post by ajgreeny on 2015-05-20
Try running a full update with an ethernet cable, then try wifi again.

---

### Post by dena_izbornik on 2015-05-20
done already - still not working
on network menager is written "disabled by hardware switch". I tried to start it on WLAN switch, as wel as all known (to me) combination of buttons, but nothing happened.
Any ideas?

Thanks

---

### Post by dena_izbornik on 2015-05-21
All ok now.
Somehow WLAN was disabled in BIOS](*,)](*,)](*,):biggrin:.

Thanks for attention

---

### Post by ajgreeny on 2015-05-21
Great!

Please mark as **SOLVED** from the **Thread Tools** menu at top.

---

### Post by dena_izbornik on 2015-05-22
soory
done
thanks to all

---

