---
title: "Not Natty for 12.04"
date: 2013-09-07
forum: Networking &amp; Wireless
---

### Post by Darren01 on 2013-09-07
Hi all

I have 12.04 with a wirless card which doesn't work.  I followed all the instructions given in this thread [https://help.ubuntu.com/community/WifiDocs/Device/Netgear_WG511v2_Natty_11.04](https://help.ubuntu.com/community/WifiDocs/Device/Netgear_WG511v2_Natty_11.04) but I didn't get any authentication.

Note that the lspci -nn command in the terminal returned the same output as described in thread.

Any help would be appreciated.

---

### Post by Bucky Ball on 2013-09-07
Post the output of these two commands:

sudo lshw -C network
iwconfig

Did you try the card before beginning a quest to install drivers, etc.?

---

### Post by Darren01 on 2013-09-07
For lshw -C network

*-network
    description:  Ethernet interface
    product:  VT6102 [Rhine-II]
    vendor:  VIA Technologies, Inc.
    physical id:  12
    bus info:  pci@0000:00:12.0
    logical name:  eth0
    version:  51
    serial:  00:c0:9f:10:81:d1
    size:  100Mbit/s
    capacity:  100Mbit/s
    width:  32 bits
    clock:  33MHz
    capabilities:  pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
    configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.5.0 duplex=full ip=192.168.0.6 latency=64 link=yes maxlatency=8 mingnt=3 multicast=yes port=MII speed=100Mbit/s
    resources: irq:9 ioport:1c00(size=256) memory:e8000000-e80000ff
*-network UNCLAIMED
    description: Network controller
    product: ISL3890 [Prism GT/Prism Duette]/ISL3886 {Prism Javelin/Prism Xbow]
    vendor: Intersil Corporation
    physical id: 1
    bus info: pci@0000@02:00.0
    version: 01
    width:  32 bits
    clock: 33MHz
    capabilities: pm cap_list
    configuration:  latency=64 maxlatency=28 mingnt=10
    resources:  memory:24000000-24001fff

for iwconfig

lo    no wireless extensions.

eth0    no wireless extensions.


Before my quest ... the machine was a windows machine.  The drivers / wireless worked within this system.  I cleaned the windows with this Ubuntu instal.

Thanks for your help thus far ...

---

### Post by Darren01 on 2013-09-07
ps  I typed the above out by hand.  Is there a way of copying in pasting from the terminal to places such as this?

---

### Post by praseodym on 2013-09-07
Save this file in "Downloads"

[http://de.archive.ubuntu.com/ubuntu/pool/multiverse/l/linux-firmware-nonfree/linux-firmware-nonfree_1.14ubuntu1_all.deb](http://de.archive.ubuntu.com/ubuntu/pool/multiverse/l/linux-firmware-nonfree/linux-firmware-nonfree_1.14ubuntu1_all.deb)

and install it via
```

sudo dpkg -i ~/Downloads/*.deb
```
Reboot and check:
```

lsmod
iwconfig
dmesg | grep p5
```

---

### Post by Darren01 on 2013-09-07
lsmod

Module                  Size  Used by
savage                 31456  1 
drm                   197641  2 savage
vesafb                 13516  1 
arc4                   12473  2 
p54pci                 17098  0 
snd_via82xx            24718  2 
p54common              36909  1 p54pci
gameport               15060  1 snd_via82xx
mac80211              436493  2 p54pci,p54common
cfg80211              178877  2 p54common,mac80211
snd_mpu401_uart        13865  1 snd_via82xx
joydev                 17393  0 
snd_seq_midi           13132  0 
snd_rawmidi            25424  2 snd_mpu401_uart,snd_seq_midi
snd_via82xx_modem      18377  5 
snd_ac97_codec        110213  2 snd_via82xx,snd_via82xx_modem
snd_seq_midi_event     14475  1 snd_seq_midi
ac97_bus               12642  1 snd_ac97_codec
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
snd_pcm                80916  5 snd_via82xx,snd_via82xx_modem,snd_ac97_codec
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd_timer              28931  2 snd_seq,snd_pcm
snd_page_alloc         14108  3 snd_via82xx,snd_via82xx_modem,snd_pcm
snd                    62218  21 snd_via82xx,snd_mpu401_uart,snd_rawmidi,snd_via82xx_modem,snd_ac97_codec,snd_seq,snd_seq_device,snd_pcm,snd_timer
vt8231                 20522  0 
soundcore              14635  1 snd
psmouse                86546  0 
serio_raw              13027  0 
i2c_viapro             12969  0 
rfcomm                 38139  0 
bnep                   17830  2 
video                  19115  0 
bluetooth             158447  10 rfcomm,bnep
ppdev                  12849  0 
via_ircc               26781  0 
irda                  185517  1 via_ircc
parport_pc             32114  1 
pcmcia                 39826  0 
mac_hid                13077  0 
crc_ccitt              12627  2 p54common,irda
yenta_socket           27465  0 
pcmcia_rsrc            18367  1 yenta_socket
shpchp                 32265  0 
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
via_rhine              27413  0 
floppy                 60184  0 
pata_via               13428  2 


iwconfig

lo        no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
eth0      no wireless extensions.


dmesg | grep p5

[   30.027434] p54pci 0000:02:00.0: enabling device (0000 -> 0002)
[   30.027474] p54pci 0000:02:00.0: PCI INT A -> Link[LNKA] -> GSI 9 (level, low) -> IRQ 9
[   30.027504] p54pci 0000:02:00.0: setting latency timer to 64
[   30.263673] ieee80211 phy0: p54 detected a LM86 firmware
[   30.263689] p54: rx_mtu reduced from 3240 to 2376
[   31.290515] Registered led device: p54-phy0::assoc
[   31.290815] Registered led device: p54-phy0::tx
[   31.291176] Registered led device: p54-phy0::rx
[   31.291454] Registered led device: p54-phy0::radio
[   31.291481] p54pci 0000:02:00.0: is registered as 'phy0'


(ps remembered how to copy 'n' paste ... ctrl-shift-C ... ctrl-v)
(pps should I have re-booted without my ethernet cable plugged in?)

---

### Post by praseodym on 2013-09-08
Un-plug the cable and try to connect

---

### Post by Darren01 on 2013-09-08
lo        no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"Minnie"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:1E:2A:F6:CA:0C   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-1 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

But I don't get a connection when I unplug the cable.  When I re-boot without the ethernet cable attached I get a delayed boot-up while the instrument waits 60secs whilst it tries to find a network connection.

When I boot-up with the ethernet cable, the wireless icon appears in the usual place and it shows that there is a connection but this doesn't work when I unplug the ethernet cable.

Anythoughts?

And, thanks so far ...

---

### Post by praseodym on 2013-09-08
Yes, open this file:
```

gksudo gedit /etc/network/interfaces
```
This file should only read
```

auto lo
iface lo inet loopback
```
Save, close the editor and reboot.

---

### Post by Darren01 on 2013-09-08
That appears to have done the trick.  There were a couple of extra lines,

auto eth0
iface eth0 inet dhcp

which I hashed (ie preceded with #) out.  Saved the file and re-booted.

When I booted up again with the ethernet cable attached, the symbol for the wireless connection was replaced by two arrows facing in opposite directions.  I unplugged the ethernet cable and the two arrows were immediately replaced by the usual symbol for the wireless connection.

However, before closing this thread down as solved ... I had two laptops that I re-formatted.  I want to make sure that I can do all of the above on the other laptop.  When I can I'll post back here and ask for the thread to be close as solved.

In the mean time ... thanks for your help.

---

### Post by praseodym on 2013-09-08
Maybe your other laptop uses other hardware?!

---

### Post by Darren01 on 2013-09-08
> **praseodym said:**
> Maybe your other laptop uses other hardware?!

Very likely ... this one is an hp omnibook xe4100, the other is a Fujitsu Siemens C Series lifebook.

I will try and follow the instructions given the for hp omnibook and post the result here whether it works or not.

---

### Post by Darren01 on 2013-09-08
> **Darren01 said:**
> That appears to have done the trick.

Spoke too soon.  When I boot up the system, it works fine.  When I close the laptop (and hence put it to sleep) and after a period of time re-open it, the wifi connection doesn't re-connect.

As to why ... I don't know.

Any help would be appreciated.

---

### Post by praseodym on 2013-09-09
Check:
```

iwlist chan
iwconfig
sudo iwlist scan
route -n
cat /etc/resolv.conf
ifconfig -a
```

---

### Post by Darren01 on 2013-09-10
> **praseodym said:**
> Check:
```

iwlist chan
```
lo        no frequency information.

wlan0     13 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Current Frequency:2.462 GHz (Channel 11)

eth0      no frequency information.


> ```
iwconfig
```
lo        no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"Minnie"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:1E:2A:F6:CA:0C   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-129 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.


> ```
sudo iwlist scan
```
lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:1E:2A:F6:CA:0C
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-1 dBm  
                    Encryption key:on
                    ESSID:"Minnie"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000090c53b183
                    Extra: Last beacon: 44ms ago
                    IE: Unknown: 00064D696E6E6965
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD06001018020014
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00

eth0      Interface doesn't support scanning.

> ```
route -n
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
192.168.0.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0

> ```
cat /etc/resolv.conf
```
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.0.1

> ```
ifconfig -a
```
eth0      Link encap:Ethernet  HWaddr 00:c0:9f:10:81:d1  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:9 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:161 errors:0 dropped:0 overruns:0 frame:0
          TX packets:161 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:14908 (14.9 KB)  TX bytes:14908 (14.9 KB)

wlan0     Link encap:Ethernet  HWaddr 00:09:5b:84:a6:a7  
          inet addr:192.168.0.4  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::209:5bff:fe84:a6a7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2854 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2222 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2963996 (2.9 MB)  TX bytes:427675 (427.6 KB)

thanks again for your help.

---

### Post by praseodym on 2013-09-11
You are using WEP encryption only. Change to pure WPA2-AES (CCMP) in your router settings and to a fixed channel

---

### Post by Darren01 on 2013-09-11
> **praseodym said:**
> You are using WEP encryption only. Change to pure WPA2-AES (CCMP) in your router settings and to a fixed channel

Can I do that at the command line or do it by clicking on the wireless icon and editing the connections?

---

### Post by praseodym on 2013-09-11
You need to enter the router interface, check the manual

---

