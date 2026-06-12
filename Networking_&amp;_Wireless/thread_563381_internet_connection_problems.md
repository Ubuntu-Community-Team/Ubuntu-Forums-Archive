---
title: "internet connection problems"
date: 2007-09-29
forum: Networking &amp; Wireless
---

### Post by Tanchistu on 2007-09-29
I can't connect to Internet using my usual settings.

This is what I've done: static IP, subnet mask , gateway, DNS server address. Are the very same settings I'm using right now in windows, the same I'm using for a few years. I'm using ubuntu 7.04

I have double check everything.

There seems to be some network activity, especially incoming packets.

thank you.

---

### Post by handydan918 on 2007-09-29
> **Tanchistu said:**
> I can't connect to Internet using my usual settings.

This is what I've done: static IP, subnet mask , gateway, DNS server address. Are the very same settings I'm using right now in windows, the same I'm using for a few years. I'm using ubuntu 7.04

I have double check everything.

There seems to be some network activity, especially incoming packets.

thank you.
Post the out put of:
 ```
lspci | grep -i net
```
and
```
lsmod
```
and 
```
ifconfig
```

That should be enough to start some trouble...

---

### Post by Tanchistu on 2007-09-29
radu@radu-desktop:~$ lspci | grep -i net
02:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)


radu@radu-desktop:~$ lsmod
Module                  Size  Used by
nls_iso8859_1           5120  1 
nls_cp437               6784  1 
vfat                   14208  1 
fat                    53916  1 vfat
ipv6                  268704  10 
binfmt_misc            12680  1 
rfcomm                 40856  0 
l2cap                  25728  5 rfcomm
bluetooth              55908  4 rfcomm,l2cap
ppdev                  10116  0 
cpufreq_userspace       5408  0 
cpufreq_conservative     8200  0 
cpufreq_ondemand        9228  0 
cpufreq_stats           7360  0 
freq_table              5792  2 cpufreq_ondemand,cpufreq_stats
cpufreq_powersave       2688  0 
dev_acpi               12292  0 
sony_acpi               6284  0 
tc1100_wmi              8068  0 
pcc_acpi               13184  0 
container               5248  0 
video                  16388  0 
dock                   10268  0 
battery                10756  0 
asus_acpi              17308  0 
button                  8720  0 
sbs                    15652  0 
i2c_ec                  5888  1 sbs
ac                      6020  0 
backlight               7040  1 asus_acpi
af_packet              23816  0 
nls_utf8                3072  2 
ntfs                  107764  2 
lp                     12452  0 
fuse                   46612  0 
snd_emu10k1_synth       8192  0 
snd_emux_synth         35456  1 snd_emu10k1_synth
snd_seq_virmidi         7936  1 snd_emux_synth
snd_seq_midi_emul       7680  1 snd_emux_synth
snd_emu10k1           121248  1 snd_emu10k1_synth
snd_intel8x0           34204  1 
snd_ac97_codec         98336  2 snd_emu10k1,snd_intel8x0
ac97_bus                3200  1 snd_ac97_codec
snd_util_mem            5760  2 snd_emux_synth,snd_emu10k1
snd_pcm_oss            44544  0 
snd_mixer_oss          17408  1 snd_pcm_oss
tuner                  61864  0 
snd_hwdep               9988  2 snd_emux_synth,snd_emu10k1
snd_pcm                79876  4 snd_emu10k1,snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            32896  0 
snd_seq_midi            9600  0 
snd_rawmidi            25472  3 snd_seq_virmidi,snd_emu10k1,snd_seq_midi
snd_seq_midi_event      8448  3 snd_seq_virmidi,snd_seq_oss,snd_seq_midi
snd_seq                52592  9 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23684  3 snd_emu10k1,snd_pcm,snd_seq
snd_seq_device          9100  8 snd_emu10k1_synth,snd_emux_synth,snd_emu10k1,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
cx8800                 35212  0 
cx88xx                 67364  1 cx8800
ir_common              31236  1 cx88xx
i2c_algo_bit            8712  1 cx88xx
video_buf              26116  2 cx8800,cx88xx
tveeprom               15888  1 cx88xx
i2c_core               22784  5 i2c_ec,tuner,cx88xx,i2c_algo_bit,tveeprom
compat_ioctl32          2304  1 cx8800
btcx_risc               5896  2 cx8800,cx88xx
videodev               28160  2 cx8800,cx88xx
iTCO_wdt               11812  0 
iTCO_vendor_support     4868  1 iTCO_wdt
snd                    54020  16 snd_emux_synth,snd_seq_virmidi,snd_emu10k1,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_hwdep,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
v4l2_common            25216  3 tuner,cx8800,videodev
v4l1_compat            15236  2 cx8800,videodev
psmouse                38920  0 
emu10k1_gp              4736  0 
gameport               16520  2 emu10k1_gp
parport_pc             36388  1 
parport                36936  3 ppdev,lp,parport_pc
soundcore               8672  1 snd
snd_page_alloc         10888  3 snd_emu10k1,snd_intel8x0,snd_pcm
shpchp                 34324  0 
pci_hotplug            32576  1 shpchp
pcspkr                  4224  0 
intel_agp              25116  1 
agpgart                35400  1 intel_agp
serio_raw               7940  0 
tsdev                   8768  0 
evdev                  11008  3 
ext3                  133128  1 
jbd                    59816  1 ext3
mbcache                 9604  1 ext3
sg                     36252  0 
sd_mod                 23428  6 
sr_mod                 17060  0 
cdrom                  37664  1 sr_mod
ata_piix               15492  5 
ata_generic             9092  0 
8139cp                 25088  0 
libata                125720  2 ata_piix,ata_generic
scsi_mod              142348  4 sg,sd_mod,sr_mod,libata
8139too                27648  0 
mii                     6528  2 8139cp,8139too
floppy                 59524  0 
generic                 5124  0 [permanent]
ehci_hcd               34188  0 
uhci_hcd               25360  0 
usbcore               134280  3 ehci_hcd,uhci_hcd
thermal                14856  0 
processor              31048  1 thermal
fan                     5636  0 
fbcon                  42656  0 
tileblit                3584  1 fbcon
font                    9216  1 fbcon
bitblit                 6912  1 fbcon
softcursor              3200  1 bitblit
vesafb                  9220  0 
capability              5896  0 
commoncap               8192  1 capability


radu@radu-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:19:21:46:34:0D  
          inet addr:81.181.8.231  Bcast:81.181.8.255  Mask:255.255.255.192
          inet6 addr: fe80::219:21ff:fe46:340d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4684 errors:0 dropped:0 overruns:0 frame:0
          TX packets:53 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:325602 (317.9 KiB)  TX bytes:5217 (5.0 KiB)
          Interrupt:20 Base address:0xcc00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:600 (600.0 b)  TX bytes:600 (600.0 b)


that is my IP address

it's still not working

---

### Post by HermanAB on 2007-09-29
Hmm, it looks like the one thing you haven't checked is the routing.

Do you see a default route (UG) when you type:
$ sudo route
(it may take a while, be patient)

If not, set up a default route with:
$ sudo route add default gw gate.way.ip.address

then test it with something simple like:
$ telnet [www.yahoo.com](www.yahoo.com) 80

'Hope that helps!

Cheers,

Herman

---

### Post by Tanchistu on 2007-09-29
radu@radu-desktop:~$ sudo route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
81.181.8.192    *               255.255.255.192 U     0      0        0 eth0
radu@radu-desktop:~$ sudo route add default gw 81.181.8.1
SIOCADDRT: Network is unreachable
radu@radu-desktop:~$ telnet [www.yahoo.com](www.yahoo.com) 80
telnet: could not resolve [www.yahoo.com/80:](www.yahoo.com/80:) Name or service not known
radu@radu-desktop:~$

---

### Post by Tanchistu on 2007-09-30
So? nobody knows what's the problem? Could it be my ISP? I doubt it

---

### Post by clinto on 2007-09-30
Well obviously it's not your ISP since you can connect through Windows, correct?

I'm having the same type of problem. I had DHCP set up originally and decided I wanted to go to Static IP for port forwarding reasons. I didn't really know what I was doing and couldn't get things working, tried all different approaches, finally decided to just revert back to the way it was when it was working, and I still can't connect. :/

I'll be watching this thread while I make my own thread. If there is any info I gather from mine, I'll relate it and see if it has any significance. I know there is just something real simple I'm missing.

---

### Post by noob12 on 2007-09-30
Looks to me like HermanAB was probably on the right track for Tanchistu's original problem.
However, note the netmask 255.255.255.192 .  So the gateway is probably at 81.181.8.193 or 81.181.8.254 (the lowest or highest host address).

How are you setting up the interface?  Can you post the output of the command: **cat /etc/network/interfaces**

To test that theory, try those in turn:
```

sudo route add default gw 81.181.8.193

```

Then see if you can ping an external address like one of google's:  **ping 72.14.253.99**


If that doesn't work try
```

sudo route add default gw 81.181.8.254

```
and the same ping test.

If you can get the pings working the next thing to look at is your DNS configuration.

---

### Post by Tanchistu on 2007-09-30
Right now I'm using ubuntu!

Thank you! Thank you! Thank you!

It worked with 81.181.8.193. 

But why? Network administrator gave me 81.181.8.1 gateway, and in windows it works.

And in /etc/network/interfaces its the old gw address, will this affect the connection next time I restart? Should I change it?




And sorry for that other thread.

---

### Post by noob12 on 2007-09-30
Great to hear!  You should change it in your configuration to be the correct one (81.181.8.193) otherwise you'll lose it when you reboot or next restart networking.

---

