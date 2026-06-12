---
title: "dropped eth0 (and the never claim) after a while"
date: 2011-06-24
forum: New to Ubuntu
---

### Post by MysticMetal on 2011-06-24
I've encountered a similar problem with my older desktop;  My situation  is different however.  I installed ubuntu and after I updated the whole  list of stuff I needed to restart so I did and then the ethernet  connection (wired lan into router) stopped working and said it was last  used never (which was not true).  So I fiddled with it a bid and then  restarted and it worked again (although the settings were the same; I  fiddled it back).  Just recently it has stopped working again.  The only  thing I've installed lately was cream.    

I'm going to install a 2TB hard drive and put ubuntu on it, and wipe my  other drives and put windows on one, fat32 on the other but  thought  this predicament worth mentioning.



I  won't be doing that for a while though, so if anyone has any ideas on how to fix this problem I'dlike to explore them.

---

### Post by jtarin on 2011-06-24
What type of connection do you have? Cable, DSL other? Run these commands in a terminal and post the results. ```
ifconfig
```then the command ```
lspci
``` the ```
lsmod
```post 'em':p

---

### Post by MysticMetal on 2011-06-26
I connect through a router to a cable modem.  After booting from the ubuntu live cd and also knoppix and not being able to connect there either I'm beginning to think I have a hardware issue.

here's the stuff:

@calculator:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:01:29:d1:aa:f3  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:23 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)




@calculator:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. K8T800Pro Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. K8T800Pro Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. K8T800Pro Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. K8T800Pro Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. K8T800Pro Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. K8T800Pro Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South]
00:0f.0 RAID bus controller: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
00:13.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev 80)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation NV11DDR [GeForce2 MX200] (rev b2)
@calculator:~$ 



@calculator:~$ lsmod
Module                  Size  Used by
nls_utf8                1069  1 
isofs                  29250  1 
binfmt_misc             6587  1 
xfs                   513478  1 
exportfs                3437  1 xfs
snd_via82xx            20058  2 
gameport                9089  1 snd_via82xx
snd_ac97_codec        100646  1 snd_via82xx
ac97_bus                1002  1 snd_ac97_codec
snd_pcm_oss            35308  0 
fbcon                  35102  71 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_via82xx,snd_ac97_codec,snd_pcm_oss
tileblit                1999  1 fbcon
font                    7557  1 fbcon
snd_page_alloc          7076  2 snd_via82xx,snd_pcm
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
snd_mpu401_uart         5617  1 snd_via82xx
vga16fb                11385  0 
snd_seq_dummy           1338  0 
vgastate                8961  1 vga16fb
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  2 snd_mpu401_uart,snd_seq_midi
nouveau               467048  2 
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
ttm                    49943  1 nouveau
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
lp                      7028  0 
snd_timer              19098  2 snd_pcm,snd_seq
ppdev                   5259  0 
drm_kms_helper         29329  1 nouveau
parport_pc             25962  1 
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
joydev                  8740  0 
psmouse                63245  0 
amd64_agp               7165  1 
parport                32635  3 lp,ppdev,parport_pc
drm                   162377  4 nouveau,ttm,drm_kms_helper
snd                    54244  15 snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_mpu401_uart,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
agpgart                31724  3 ttm,amd64_agp,drm
usbhid                 36110  0 
i2c_algo_bit            5028  1 nouveau
k8temp                  3152  0 
serio_raw               3978  0 
hid                    67096  1 usbhid
shpchp                 28835  0 
i2c_viapro              5573  0 
soundcore               6620  1 snd
ohci1394               26950  0 
via_rhine              19154  0 
usb_storage            39841  0 
ieee1394               81181  1 ohci1394
mii                     4381  1 via_rhine
pata_via                7272  4 
sata_via                7009  0 
floppy                 53016  0

---

### Post by varunendra on 2011-06-26
Please also post the result of :
```
sudo lshw -C network
```Apparently, there is some bug with VIA VT6102 [Rhine-II] adapter. Just need details (would be included in above command's result) to confirm.

Also, the result of:
```
uname -a
```

---

### Post by MysticMetal on 2011-06-27
@calculator:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 78
       serial: 00:01:29:d1:aa:f3
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=half latency=32 link=no maxlatency=8 mingnt=3 multicast=yes port=MII speed=10MB/s
       resources: irq:23 ioport:ec00(size=256) memory:fa001000-fa0010ff
joshuamichaelsuggs@calculator:~$

joshuamichaelsuggs@calculator:~$ uname -a
Linux calculator 2.6.32-32-generic #62-Ubuntu SMP Wed Apr 20 21:54:21 UTC 2011 i686 GNU/Linux
joshuamichaelsuggs@calculator:~$

---

### Post by jtarin on 2011-06-27
Try starting Ubuntu with the boot option: acpi=noirq

---

### Post by MysticMetal on 2011-06-28
Unfortuanately this did not work.  That is, I opened /etc/default/grub and added the line acpi=noirq to it, then ran update-grub and restarted.  No network.

There was a storm the other night and the power went out, but the router isn't fried.  I'm thinking I need to find a way to flash the onboard device.  what do you think?

---

### Post by jtarin on 2011-06-28
I have a D-link router that is several years old (2005)that was dropping connections about a month ago and found an update to the software and installed it. It's made a difference for me and it sure couldn't hurt. if you can get the manufactures software great...if not there are alternatives but a little tricky for a novice to get up and running. Not impossible though.

[http://lifehacker.com/178132/hack-attack-turn-your-60-router-into-a-600-router](http://lifehacker.com/178132/hack-attack-turn-your-60-router-into-a-600-router)

[http://www.dd-wrt.com/site/index](http://www.dd-wrt.com/site/index)

---

### Post by MysticMetal on 2011-08-01
Sorry it took me so long to write this.

I tried the ethernet on another network with no success and so determined that my card was fried.  So then I bought a usb-ethernet box for around $15 and it's working great now.

thanks everyone.

---

