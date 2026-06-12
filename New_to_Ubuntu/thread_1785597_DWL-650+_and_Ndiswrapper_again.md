---
title: "DWL-650+ and Ndiswrapper again"
date: 2011-06-18
forum: New to Ubuntu
---

### Post by mattman5 on 2011-06-18
First post, sorry if this is in the wrong place. I have read through pretty much every post on this forum about the D-Link DWL-650+ AirPlus wifi card and have yet to find my solution. 

First the specs:
I have a compaq presario 2100 with ubuntu 10.04 running on it. I have used this same laptop with ubuntu 10.04 where it has worked.

What I did:
Before, I would install ndisgtk on my system, install the Windows XP drivers (available here: [http://www.dlink.com/products/?pid=DWL-650%2b](http://www.dlink.com/products/?pid=DWL-650%2b)), and voila, it would work, giving me a list of wifi networks at the top. Now, this says that hardware is present but it isn't giving me a list of networks. 

Here are a bunch of outputs that are relevant:

lshw -C network:
```
*-network UNCLAIMED
       description: Network controller
       product: ACX 100 22Mbps Wireless Interface
       vendor: Texas Instruments
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=64
       resources: ioport:1800(size=32) memory:40010000-40010fff memory:40000000-4000ffff
```
This one was interesting, with an UNCLAIMED next to my card.

lspci:
```
02:00.0 Network controller: Texas Instruments ACX 100 22Mbps Wireless Interface

```
This one confused me a little. It called it an acx100 card, but I remember ndiswrapper working with it before.

ifconfig:
```
eth0      Link encap:Ethernet  HWaddr 00:0b:cd:88:06:6e  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20b:cdff:fe88:66e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5047 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3776 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4838618 (4.8 MB)  TX bytes:700012 (700.0 KB)
          Interrupt:10 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

```
No wlan0 here. Any help will be greatly appreciated as I can't use an Ethernet cable forever!

---

### Post by mikewhatever on 2011-06-18
The ndiswrapper module is not loaded, try running **sudo modprobe ndiswrapper**.

---

### Post by mattman5 on 2011-06-18
Should I do a restart after this? This is my terminal now:

```
matthew@matthew-laptop:~$ sudo modprobe ndiswrapper
[sudo] password for matthew: 
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
matthew@matthew-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.


```

Basically: what should I do afterwards? Sorry if this is a n00by question.

---

### Post by mikewhatever on 2011-06-18
If it doesn't work after that, post the output of **lsmod**. The goal is to have the module loaded and to see see a wireless interface in the output of ifconfig/iwconfig.

---

### Post by mattman5 on 2011-06-18
Ok, I get it now. 

lsmod:
```
matthew@matthew-laptop:~/Downloads$ lsmod
Module                  Size  Used by
binfmt_misc             6587  1 
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
snd_ali5451            15799  2 
softcursor              1189  1 bitblit
snd_ac97_codec        100646  1 snd_ali5451
ac97_bus                1002  1 snd_ac97_codec
vga16fb                11385  0 
vgastate                8961  1 vga16fb
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_ali5451,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
radeon                677684  3 
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
ttm                    49943  1 radeon
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
ndiswrapper           184677  0 
snd_timer              19098  2 snd_pcm,snd_seq
drm_kms_helper         29329  1 radeon
joydev                  8740  0 
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54244  14 snd_ali5451,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
pcmcia                 30784  0 
drm                   162377  5 radeon,ttm,drm_kms_helper
soundcore               6620  1 snd
ati_agp                 5094  1 
video                  17375  0 
yenta_socket           20408  2 
agpgart                31724  3 ttm,drm,ati_agp
psmouse                63245  0 
rsrc_nonstatic         10015  1 yenta_socket
i2c_algo_bit            5028  1 radeon
ppdev                   5259  0 
output                  1871  1 video
shpchp                 28835  0 
parport_pc             25962  1 
i2c_ali15x3             5050  0 
snd_page_alloc          7076  1 snd_pcm
lp                      7028  0 
i2c_ali1535             4725  0 
serio_raw               3978  0 
pcmcia_core            32964  3 pcmcia,yenta_socket,rsrc_nonstatic
parport                32635  3 ppdev,parport_pc,lp
pata_ali                7932  2 
natsemi                23934  0 

```

---

### Post by mikewhatever on 2011-06-18
Not sure really. Were there any errors when installing?
Here is what the howto suggests: [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)
```
sudo rmmod ndiswrapper
sudo depmod -a
sudo modprobe ndiswrapper
```

---

### Post by mattman5 on 2011-06-18
Still no, *sigh*

```
matthew@matthew-laptop:~/Downloads$ sudo rmmod ndiswrapper
[sudo] password for matthew: 
matthew@matthew-laptop:~/Downloads$ sudo depmod -a
matthew@matthew-laptop:~/Downloads$ sudo modprobe ndiswrapper
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
matthew@matthew-laptop:~/Downloads$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

```

As for the problems, I did get a point where it said hardware present:no, but it is fixed now. Not sure how I did that, though.

---

### Post by mattman5 on 2011-06-18
*Bump* Anyone?

---

### Post by mikewhatever on 2011-06-18
Not sure really. You might want to ask the mods to move the thread to the Networking & Wireless section where experts can see it. Troubleshooting Ndiswrapper is not exactly fit for the Absolute Beginners.

---

### Post by mattman5 on 2011-06-18
Yeah, I knew I shouldn't have put it here. Thanks for your help.
 
EDIT: already moved it

---

