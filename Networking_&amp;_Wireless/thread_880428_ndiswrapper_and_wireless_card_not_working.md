---
title: "ndiswrapper and wireless card not working"
date: 2008-08-05
forum: Networking &amp; Wireless
---

### Post by nodnarb83 on 2008-08-05
I have a Belkin Wireless N F5D8073 Express Card for my laptop.  I found this tutorial in the forums:

[I]THIS CARD WORKS!!!!! YAY! Right out of the box on Gutsy. I popped it in, put the CD in, copied the XP driver folder to my hard drive, then used the GUI NDISWRAPPER to load the driver. It could not have been easier! (well, I guess plug-n-play would have been easier)

Exact steps.
1) Put Card in computer.
2) Put CD in drive
3) Browse to XP Driver, and copy driver folder with all contents to your hard drive.
4) Go to ADD/Remove Programs and search for NDISWRAPPER
5) Load the WINDOWS WIRELESS DRIVERS Tool.
6) Go To SYSTEM, ADMINISTRATION, WINDOWS WIRELESS DRIVERS
7)Click on Install New Driver
Browse to XP folder and load *.INF file
9) You should then see the driver loaded and hardware present in the window.
10) Click Configure Network
11) Setup your wireless network info.
12) After all of that, you need to make sure you hit the checkbox that enables the wireless network.
[/I]
However, when I get to step number nine the ndiswrapper states that the hardware is not present and when I click on "Configure Network" an option for a wireless network is not even present.  I have scoured the forums and ndswrappers site to find out any info on what I can do but I have not had any luck.  Any ideas?

---

### Post by nodnarb83 on 2008-08-05
Sorry, I hate to bump this back up to the front but I cannot find any info on this problem.  I have done everything step by step and other people have said that this works.  Where have I gone wrong?  Oh yeah, I also blacklisted default drivers as well.

---

### Post by nodnarb83 on 2008-08-05
Still here...](*,)

I have been trying EVERYTHING I can think of...

Reinstall, extracted driver straigt from iso file, mounted iso and installed driver from mount, etc.

---

### Post by caljohnsmith on 2008-08-06
Nodnarb83, how about posting the output of:
```
ndiswrapper -l
ifconfig
iwconfig
lsmod
sudo lshw -C network
```
That will give us a good place to start. :)

---

### Post by K_REY_C on 2009-07-26
> **caljohnsmith said:**
> Nodnarb83, how about posting the output of:
```
ndiswrapper -l
ifconfig
iwconfig
lsmod
sudo lshw -C network
```
That will give us a good place to start. :)

Same Problem... Same card... here's output:

> ~$ ndiswrapper -l

WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.

netr28 : driver installed

	device (1814:0781) present (alternate driver: rt2860sta)

rt2860 : invalid driver!


 ~$ ifconfig

eth0      Link encap:Ethernet  HWaddr 00:16:41:10:c1:2d  

          inet addr:192.168.1.64  Bcast:192.168.1.255  Mask:255.255.255.0

          inet6 addr: fe80::216:41ff:fe10:c12d/64 Scope:Link

          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

          RX packets:2834 errors:0 dropped:0 overruns:0 frame:0

          TX packets:1000 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:801556 (801.5 KB)  TX bytes:186930 (186.9 KB)

          Interrupt:16 



lo        Link encap:Local Loopback  

          inet addr:127.0.0.1  Mask:255.0.0.0

          inet6 addr: ::1/128 Scope:Host

          UP LOOPBACK RUNNING  MTU:16436  Metric:1

          RX packets:8 errors:0 dropped:0 overruns:0 frame:0

          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:0 

          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

~$ iwconfig

lo        no wireless extensions.



eth0      no wireless extensions.



irda0     no wireless extensions.



pan0      no wireless extensions.

~$ lsmod

Module                  Size  Used by

i915                   65668  2 

drm                    96296  3 i915

binfmt_misc            16776  1 

bridge                 56340  0 

stp                    10500  1 bridge

bnep                   20224  2 

input_polldev          11912  0 

wl                   1281236  0 

ieee80211_crypt        13444  1 wl

lp                     17156  0 

joydev                 18368  0 

pcmcia                 44748  0 

snd_intel8x0           37532  3 

snd_ac97_codec        112292  1 snd_intel8x0

ac97_bus                9856  1 snd_ac97_codec

snd_pcm_oss            46336  0 

snd_mixer_oss          22656  1 snd_pcm_oss

snd_pcm                82948  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss

snd_seq_dummy          10756  0 

snd_seq_oss            37760  0 

snd_seq_midi           14336  0 

snd_rawmidi            29696  1 snd_seq_midi

snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi

snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event

snd_timer              29704  2 snd_pcm,snd_seq

snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq

thinkpad_acpi          66560  0 

nsc_ircc               29328  0 

iTCO_wdt               19108  0 

iTCO_vendor_support    11652  1 iTCO_wdt

yenta_socket           32396  1 

rsrc_nonstatic         19328  1 yenta_socket

led_class              12036  1 thinkpad_acpi

snd                    62628  16 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device

soundcore              15200  1 snd

psmouse                61972  0 

intel_agp              34108  1 

video                  25360  0 

pcmcia_core            43540  3 pcmcia,yenta_socket,rsrc_nonstatic

nvram                  16396  1 thinkpad_acpi

ppdev                  15620  0 

snd_page_alloc         16904  2 snd_intel8x0,snd_pcm

irda                  197180  1 nsc_ircc

serio_raw              13316  0 

pcspkr                 10496  0 

agpgart                42696  3 drm,intel_agp

output                 11008  1 video

ndiswrapper           193436  0 

parport_pc             40100  1 

parport                42220  3 lp,ppdev,parport_pc

crc_ccitt              10112  1 irda

tg3                   131204  0 

floppy                 64324  0 

fbcon                  46112  0 

tileblit               10752  1 fbcon

font                   16384  1 fbcon

bitblit                13824  1 fbcon

softcursor              9984  1 bitblit


~$ sudo lshw -C network

  *-network               

       description: Ethernet interface

       product: NetXtreme BCM5751M Gigabit Ethernet PCI Express

       vendor: Broadcom Corporation

       physical id: 0

       bus info: pci@0000:02:00.0

       logical name: eth0

       version: 11

       serial: 00:16:41:10:c1:2d

       size: 100MB/s

       capacity: 1GB/s

       width: 64 bits

       clock: 33MHz

       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation

       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.94 duplex=full firmware=5751m-v3.46a ip=192.168.1.64 latency=0 link=yes module=tg3 multicast=yes port=twisted pair speed=100MB/s

  *-network UNCLAIMED

       description: Network controller

       product: RT2860

       vendor: RaLink

       physical id: 0

       bus info: pci@0000:03:00.0

       version: 00

       width: 32 bits

       clock: 33MHz

       capabilities: pm msi pciexpress cap_list

       configuration: latency=0

  *-network DISABLED

       description: Ethernet interface

       physical id: 1

       logical name: pan0

       serial: 52:1f:f9:22:e4:a9

       capabilities: ethernet physical

       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes


---

### Post by K_REY_C on 2009-07-27
Anybody with any ideas about the above? I've got a sister in town who's leaving tomorrow and I'd really like to get this working for her. I'll direct her to this thread (of course)... but if anyone has any ideas they would be more than welcome. As far as I can tell the OS isn't even recognizing the existence of the wireless expresscard, despite the light coming on when it's inserted. 

Thanks! KYLE

---

### Post by ManyBeers on 2009-07-27
> **K_REY_C said:**
> Anybody with any ideas about the above? I've got a sister in town who's leaving tomorrow and I'd really like to get this working for her. I'll direct her to this thread (of course)... but if anyone has any ideas they would be more than welcome. As far as I can tell the OS isn't even recognizing the existence of the wireless expresscard, despite the light coming on when it's inserted. 

Thanks! KYLE
If I was you I would start over from scratch. Only this time leave the card out of the slot until you have reinstalled the drivers with ndis and then reboot with the card in.

---

### Post by K_REY_C on 2009-12-30
Okay... so I took the advice to start from scratch and the card did exist... as did the wireless connection in the network manager. When trying to connect to the router, though, it failed to complete that task. 

Also, upon reboot, neither the wireless card nor the wireless network remained visible/working in the network manager. 

If, however, I take out the card prior to shutting down/rebooting the network card will be re-recognized.

Any chance anyone can help me get the next step in this project completed for my sister before return to my home 1000 miles away?

Thanks very much.

---

### Post by SeaJayEmm on 2009-12-30
blacklist the rt2870sta, and it should work....or if you have an old router sitting around not being used you can put the dd-wrt firmware on it, make it a repeater which will get wireless signal and you can hard wire your computer into it

---

