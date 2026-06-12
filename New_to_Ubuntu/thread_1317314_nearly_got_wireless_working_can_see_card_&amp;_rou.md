---
title: "nearly got wireless working can see card &amp; router but cant connect"
date: 2009-11-06
forum: New to Ubuntu
---

### Post by sonny123 on 2009-11-06
nearly got wireless working can see card & router but cant connect to router
am a noob to ubuntu and have spent all day trying to do this  ](*,)

set up ndiswrapper and i think the driver is working because i now have green [power] led blinking on my card where as is wasnt before. Both LEDs lit up when i install the driver in the System>admin>windows wireless drivers. but once driver is installed power LED just blinks, it never goes solid

 I  Disabled bcm43xx driver, b43 and b43legacy,  because it will conflict with ndiswrapper.
have followed instructions here
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

used this to disable
echo -e "blacklist bcm43xx\nblacklist b43\nblacklist b43legacy\nblacklist ssb" | sudo tee -a /etc/modprobe.d/blacklist
here are all the outputs that i think are relevant
many thanks for any help

root@rock:~#** ndiswrapper -l**
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
lsmvnds : driver installed
    device (11AB:1FAA) present

i dont know what this means exactly is the driver installed? is there a problem with it?


root@rock:~# lspci
[SIZE=1]00:00.0 Host bridge: Silicon Integrated Systems [SiS] 650/M650 Host (rev 80)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS962 [MuTIOL Media IO] (rev 14)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.3 FireWire (IEEE 1394): Silicon Integrated Systems [SiS] FireWire Controller
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
00:02.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller[/SIZE]
[COLOR=Red]00:0a.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)  [this is wired and working][/COLOR]
[SIZE=1]00:0c.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 65x/M650/740 PCI/AGP VGA Display Adapter[/SIZE]
[COLOR=Red]02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03) [this is wireless card]
[/COLOR]
root@rock:~# **ifconfig**
[SIZE=1]eth0      Link encap:Ethernet  HWaddr 00:90:f5:2b:bf:a4  
          inet addr:192.168.1.65  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::290:f5ff:fe2b:bfa4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5462 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3749 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3050870 (3.0 MB)  TX bytes:682482 (682.4 KB)
          Interrupt:11 Base address:0x2000 
[/SIZE]
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1128 (1.1 KB)  TX bytes:1128 (1.1 KB)

wlan1     Link encap:Ethernet  HWaddr 00:14:bf:bc:b6:9a  
          inet6 addr: fe80::214:bfff:febc:b69a/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:5 Memory:14010000-14020000 

root@rock:~#** iwconfig**
[SIZE=1]lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.
[/SIZE]
wlan1     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  [COLOR=Red]Access Point: Not-Associated[/COLOR]   
          Bit Rate:1 Mb/s   Sensitivity=-200 dBm  
          RTS thr=2346 B   Fragment thr=2346 B   
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


root@rock:~# **lshw -C network**
  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: 10
       serial: 00:90:f5:2b:bf:a4
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.65 latency=64 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
  *-network
       description: 88W8300 802.11b Cardbus PC Card
       product: 83
       vendor: Marvell Semiconductor
       physical id: 0
       version: 01
       slot: Socket 0
       resources: irq:5
  *-network
       description: Wireless interface
       product: 88w8335 [Libertas] 802.11b/g Wireless
       vendor: Marvell Technology Group Ltd.
       physical id: 1
       bus info: pci@0000:02:00.0
       logical name: wlan1
       version: 03
       serial: 00:14:bf:bc:b6:9a
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+lsmvnds driverversion=1.53+Linksys,10/13/2004,3.1.0.36 latency=64 link=no module=ndiswrapper multicast=yes wireless=IEEE 802.11g
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 2a:19:42:ca:87:c9
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

root@rock:~# iwlist scan
[SIZE=1]lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning[/SIZE].

wlan1     Scan completed :
          Cell 01 - Address: 00:24:17:31:B2:81
                    ESSID:"O2wirelessC30B56"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:62/100  Signal level:-56 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 02 - Address: 00:21:04:CE:05:1A  [THIS IS NOT MY ROUTER POSS NEIGHBOURS ROUTER]
                    ESSID:"BTHomeHub2-JNGR"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:7/100  Signal level:-91 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK

---

### Post by lkraemer on 2009-11-07
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.

lsmvnds : driver installed
device (11AB:1FAA) present

The messages are telling you that there has been a system change in what
the filenames are.  Before Version 9.04 the blacklist filename was:
blacklist.  For version 9.04 and later the name is blacklist.conf

Your driver (lsmvnds) is installed and the device is present.

You might want to open a terminal window and do:
```

lsmod
dmesg | tail

```
to have a look at the modules, and make sure the ones you blacklisted
have not been loaded........They haven't been.... But, do you have all
installed that are required?

Searching through dmesg will give you more information.....

iwconfig shows your wireless is detected as......wlan1.

Once this is all straightened up..........
I'd reboot or try:
```

sudo /etc/init.d/networking restart

```
And wait a few minutes......

If you know the routers essid and the correct <interface>,
shown by using iwconfig ie wlan0, ath0, etc.... replace that
as the <interface> below, if you want to do it manually:
(Assume your routers ESSID is "Airlink")
```

sudo ifconfig <interface> down
sudo dhclient -r <interface>
sudo iwconfig <interface> essid "Airlink"
sudo iwconfig <interface> mode Managed
sudo ifconfig <interface> up
sudo dhclient <interface>
iwconfig

```
Post the output of iwconfig above.

This should make it work.

lk

---

### Post by sonny123 on 2009-11-07
Many thanks for reply


here are the outputs not sure what to make of them am new to linux and only an average windows user
iw config tells me the access point of wlan1 is not associated which i guess is one of the problems. will follow the other directions and post results
[SIZE=1]
sonny@rock:~$ lsmod
Module                  Size  Used by
binfmt_misc            16776  1 
bridge                 56212  0 
stp                    10500  1 bridge
bnep                   20224  2 
video                  25872  0 
output                 11008  1 video
input_polldev          11912  0 
lp                     17156  0 
ndiswrapper           193436  0 
snd_intel8x0           37532  3 
snd_ac97_codec        112292  1 snd_intel8x0
pcmcia                 44748  0 
ac97_bus                9856  1 snd_ac97_codec
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                83076  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    62756  16 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15200  1 snd
yenta_socket           32396  2 
rsrc_nonstatic         19328  1 yenta_socket
joydev                 18368  0 
sis_agp                15360  1 
i2c_sis96x             12420  0 
snd_page_alloc         16904  2 snd_intel8x0,snd_pcm
pcmcia_core            43540  3 pcmcia,yenta_socket,rsrc_nonstatic
shpchp                 40212  0 
agpgart                42696  1 sis_agp
ppdev                  15620  0 
pcspkr                 10496  0 
parport_pc             40100  1 
irda                  197308  0 
crc_ccitt              10112  1 irda
psmouse                61972  0 
serio_raw              13444  0 
parport                42220  3 lp,ppdev,parport_pc
8139too                32128  0 
8139cp                 27776  0 
mii                    13312  2 8139too,8139cp
ohci1394               38576  0 
ieee1394               94660  1 ohci1394
floppy                 64324  0 
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
sonny@rock:~$ dmesg | tail
[   26.483961] Bluetooth: BNEP filters: protocol multicast
[   26.735738] Bridge firewalling registered
[   33.115264] eth0: link down
[   33.115344] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   35.115166] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[   37.211233] ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[   47.304027] wlan1: no IPv6 routers present
[  342.600685] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[  342.600731] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  352.692024] eth0: no IPv6 routers present
sonny@rock:~$ 
[/SIZE]
here are the outputs not sure what to make of them
iw config tells me the access point of wlan1 is not associated

---

### Post by sonny123 on 2009-11-07
WELL i guess i havent fixed it i get the following msg at he end of dhclient output
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
 * Reloading /etc/samba/smb.conf smbd only
   ...done.


here is full output....


sonny@rock:~$ sudo ifconfig wlan1 down
sonny@rock:~$ sudo dhclient -r wlan1
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan1/00:14:bf:bc:b6:9a
Sending on   LPF/wlan1/00:14:bf:bc:b6:9a
Sending on   Socket/fallback

sonny@rock:~$ sudo iwconfig wlan1 essid "O2wirelessC30B56"

sonny@rock:~$ sudo iwconfig wlan1 mode Managed

sonny@rock:~$ sudo ifconfig wlan1 up

sonny@rock:~$ sudo dhclient wlan1
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan1/00:14:bf:bc:b6:9a
Sending on   LPF/wlan1/00:14:bf:bc:b6:9a
Sending on   Socket/fallback
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 6
[B]No DHCPOFFERS received.
No working leases in persistent database - sleeping.
 * Reloading /etc/samba/smb.conf smbd only
   ...done.[/B]
sonny@rock:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan1     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   Sensitivity=-200 dBm  
          RTS thr=2346 B   Fragment thr=2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

---

### Post by lkraemer on 2009-11-07
Try a power off, and after a few minutes power back up.
Then post the output of iwconfig after trying to establish
a connection to your wifi again.  For some reason I don't see
any references to your driver in the lsmod command. Are
you using ndiswrapper to load your driver?

If this is a PCMCIA card, plug it in and then power up,
then post lsmod output.

lk

---

### Post by sonny123 on 2009-11-08
> **lkraemer said:**
> Try a power off, and after a few minutes power back up.
Then post the output of iwconfig after trying to establish
a connection to your wifi again.  For some reason I don't see
any references to your driver in the lsmod command. Are
you using ndiswrapper to load your driver?

If this is a PCMCIA card, plug it in and then power up,
then post lsmod output.

lk

Thanks Lk, sorry dont have much time to reply at weekends,
tried power to re popwer up but to no avail,

i have noticed the entries in etc/modporobe.d

alias pci:v000011ABd00001FAAsv00000040sd00001737bc*sc*i* ndiswrapper
alias pci:v000011ABd00001FAAsv*sd*bc*sc*i* ndiswrapper

and in the entries listed in etc/module
lp
ndiswrapper

I cant remember which forum i read it, but i suspect that this is not correct and there are too many entries but i dont know why, or what should actually be there.

any help greatly appreciated
Sonny

---

### Post by Klemts on 2009-12-03
sonny123,

I have a similar problem (the same potentially; my outputs look mostly like yours), but have discovered that Wicd Network Manager will connect to WPA2 encrypted networks. It takes a while to connect, and sometimes needs a few tries. However it will work for me. 

Hope this helps; kindly post a better solution if you come across one. 

-K

---

