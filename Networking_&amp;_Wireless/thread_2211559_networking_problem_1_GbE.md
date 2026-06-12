---
title: "networking problem 1 GbE"
date: 2014-03-16
forum: Networking &amp; Wireless
---

### Post by sulla on 2014-03-16
Dear community!

I have a strange networking problem that I am totally stuck with:

* my ubuntu server (13.10) works perfectly when connected to a 100Mbit router.
* when connected it to a 1000 Mbit switch, I constantly get networking problems: pings sometimes works in <1ms, but ~75% of pings get 2 second timeouts. SSH connections constantly drop, samba file transfers pause for several seconds.

I've tried everything:
* new cables (all cat 5, 2m in length) ==> no change in behaviour
* 3 "different" network cards: (they all use different Realtek chips)
   A) the one on my mainboard (ASRock939A785GMH128M) uses an RTL8110s chip works worst. SSH connections don't even open.
   B) a netgear GA311 PCI card, uses an RTL8168d/8111d chip. it works "quite" well.
   C) a D-Link PCI card uses a RTL8169 chip. it works less good than the netgear one.
* 2 different switches: Neither a TP-Link nor a Netgear Gigabit Ethernet switch work.
   my other 2 computers (windows7) on the gigabit switches work well...
* different ports on the switches.
* a stange thing: I also tried to slow the cards down to 100Mbit full duplex: when connected to the gigabit switches they don't work. When connected to the 100 MBit switch, it works perfectly well...

So, I don't know what to do now:
* is it some BIOS setup in the linux server?
* is it some driver problem in the realtek drivers? (this is my number one suspicion)
* is it some tweaking in linux that I can try?
* is it worth getting an intel PCIe network card, with a totally different network chip?

Thanx for any suggestions!
Sulla

---

### Post by tfrue on 2014-03-17
What is the model number of the switch and router that you are using?

---

### Post by sulla on 2014-03-18
Hi Tfrue!
The gigabit switches that I've tried are a Netgear GS105 and a TP-Link TL-SG108, both unmanaged switches.
The fast ethernet router that I use successfully is a Pirelli DSL model PRGAV4202N.
Thanx,
Sulla

---

### Post by varunendra on 2014-03-19
I suggest you try the "RTL8168d/8111d" card with Realtek's proprietary "r8168" driver. You can download it from their official site and install it with a single command "**sudo ./autorun.sh**" from the directory where you extract it.

If the problem remains the same with it, I'd doubt the switch itself. But I'd also like to see the following outputs then -
```
sudo lshw -numeric -C network
sudo ethtool eth0
```
..assuming your interface name is "eth0", if its is different, please use that one in the above command.

The "ethtool" program is not installed by default, so you'll have to install it beforehand with -
```
sudo apt-get install ethool
```

---

### Post by sulla on 2014-03-20
ok, now I'm totally confused:

I tried the stupid thing, I bought the intel gigabit PCIe network card, because I did not want to mess with proprietary Realtek driver, as I was unsure what would happen when a apt-get upgrade installed a new kernel or dist-upgrade: It causes the same kind of troubles as the 3 Realtek cards.

If my topology is:
**internet <==phone-line==> 100MBit Pirelli DSL-router <==Ethernet==> either of the 1GB switch [linux-server @100MBit or 1GBit, workstation@1Gbit, other device @100MBit]**
i.e. if I connect everything to any of my gigabit switches i have the mentioned troubles. The "other device" is a SAT-receiver that should playback videos stored on the linux server (videos will pause regularly)

If my topology is:
**internet <==phone-line==> 100MBit Pirelli DSL-router [linux server @100MBit] <==Ethernet==> either 1GB switch [workstation @ 1Gbit, other device @100MBit]**
ie. if I connect the linux server to the 100MBit router and everything else to the gigabit switches, everything works smoothly: no lags, no timeouts, no ssh aborts, no video pauses.

I don't know what I should make of this...

**here are the requested outputs of the commands given, when the server is connected to the 100MBit ADSL-router:**

```
sulla@freedom:~$ sudo lshw -numeric -C network
  *-network
       description: Ethernet interface
       product: 82574L Gigabit Network Connection [8086:10D3]
       vendor: Intel Corporation [8086]
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth3
       version: 00
       serial: 68:05:ca:23:2d:ac
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=2.3.2-k duplex=full firmware=1.8-0 ip=192.168.0.1 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:17 memory:fe9e0000-fe9fffff memory:fe900000-fe97ffff ioport:c800(size=32) memory:fe9dc000-fe9dffff memory:fe980000-fe9bffff
  *-network DISABLED
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10EC:8168]
       vendor: Realtek Semiconductor Co., Ltd. [10EC]
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth1
       version: 03
       serial: 00:25:22:33:d3:97
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:45 ioport:d800(size=256) memory:fdfff000-fdffffff memory:fdff8000-fdffbfff memory:feae0000-feafffff
  *-network DISABLED
       description: Ethernet interface
       product: DGE-528T Gigabit Ethernet Adapter [1186:4300]
       vendor: D-Link System Inc [1186]
       physical id: 5
       bus info: pci@0000:04:05.0
       logical name: eth2
       version: 10
       serial: 00:24:01:ed:33:c4
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=32 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10Mbit/s
       resources: irq:20 ioport:e800(size=256) memory:febffc00-febffcff memory:febc0000-febdffff
```


```
sulla@freedom:~$ sudo ethtool eth3
Settings for eth3:
        Supported ports: [ TP ]
        Supported link modes:   10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Full
        Supported pause frame use: No
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Full
        Advertised pause frame use: No
        Advertised auto-negotiation: Yes
        Speed: 100Mb/s
        Duplex: Full
        Port: Twisted Pair
        PHYAD: 1
        Transceiver: internal
        Auto-negotiation: on
        MDI-X: on (auto)
        Supports Wake-on: pumbg
        Wake-on: g
        Current message level: 0x00000007 (7)
                               drv probe link
        Link detected: yes
```





**here are the requested outputs of the commands given, when the server is connected to the the gigabit switch:**

```
sulla@freedom:~$ sudo lshw -numeric -C network
  *-network
       description: Ethernet interface
       product: 82574L Gigabit Network Connection [8086:10D3]
       vendor: Intel Corporation [8086]
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth3
       version: 00
       serial: 68:05:ca:23:2d:ac
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=2.3.2-k duplex=full firmware=1.8-0 ip=192.168.0.1 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:17 memory:fe9e0000-fe9fffff memory:fe900000-fe97ffff ioport:c800(size=32) memory:fe9dc000-fe9dffff memory:fe980000-fe9bffff
  *-network DISABLED
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10EC:8168]
       vendor: Realtek Semiconductor Co., Ltd. [10EC]
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth1
       version: 03
       serial: 00:25:22:33:d3:97
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:45 ioport:d800(size=256) memory:fdfff000-fdffffff memory:fdff8000-fdffbfff memory:feae0000-feafffff
  *-network DISABLED
       description: Ethernet interface
       product: DGE-528T Gigabit Ethernet Adapter [1186:4300]
       vendor: D-Link System Inc [1186]
       physical id: 5
       bus info: pci@0000:04:05.0
       logical name: eth2
       version: 10
       serial: 00:24:01:ed:33:c4
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=32 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10Mbit/s
       resources: irq:20 ioport:e800(size=256) memory:febffc00-febffcff memory:febc0000-febdffff
```


```
sulla@freedom:~$ sudo ethtool eth3
Settings for eth3:
        Supported ports: [ TP ]
        Supported link modes:   10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Full
        Supported pause frame use: No
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Full
        Advertised pause frame use: No
        Advertised auto-negotiation: Yes
        Speed: 1000Mb/s
        Duplex: Full
        Port: Twisted Pair
        PHYAD: 1
        Transceiver: internal
        Auto-negotiation: on
        MDI-X: on (auto)
        Supports Wake-on: pumbg
        Wake-on: g
        Current message level: 0x00000007 (7)
                               drv probe link
        Link detected: yes
```


Thanx for any input...

PS: I can well live with the server connected to the 100MBit network, but I would really **like** fast file transfers to the samba-server...

---

### Post by sulla on 2014-03-20
So, I somehow rule out

* the 1GBit switches (as the problem persists with both of them, as the client-PCs and devices are connected to them and the whole setup works, plus they are both new)
* the network cards (different chip manufacturers, different drivers, different buses (PCI vs. PCIe)).
* the cable: I'v tried 3 different cat5/5e cables. Same result everytime.

can it be some network tweaking in the linux kernel (I use the one shipped by ubuntu, currently it's 3.11.0-18-generic, and I didn't recompile anything...)
can it be some misconfiguration? (all cards are on manual IPs config, no DHCP)

---

### Post by varunendra on 2014-03-21
Taking the above "ruled-out" points into consideration, the only things I can think of is to try -

**1)** Disabling IPv6 (set to "Ignore" if using Network Manager, or disabling system-wide as suggested here : [http://ubuntuforums.org/showpost.php?p=12640479](http://ubuntuforums.org/showpost.php?p=12640479)

**2)** Try setting "MTU" to a lower value (default is 1500 in Ubuntu). Values 1492 or 1392 are reported to improve things sometimes. This can be done via either Network Manager (if is installed), or with "ifconfig" command (take a look at "man ifconfig", it is probably not permanent though).

If you try these, and they don't help, I'd like to see the outputs of -
```
ifconfig -a
lsmod
```
..with above suggestions applied and the state being problematic one.

**PS:**
Terminal commands & outputs should always be posted within '**Code**' tags to preserve their formatting and make the post compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Using Code Tags" link in my signature.

---

### Post by sulla on 2014-03-21
Hi  Varunendra!

Thanx a lot for being so responsive!!
I disabled IPv6 as you suggested via /etc/sysctl.conf (not sure it was on in the first place, however): the probelms persist.
Then I reduced mtu packet size to 1400: the problems persist: when I merely ping the server from my windows-client I get already a lot package losses...

Might it be that the gigabit switches advertise some problematic connection ability that the 100MBit router doesn't offer?

heres the output you request in the problematic state, connected to my TP-Link gigabit switch: The currently connected network card is eht3 (intel, PCIe). Ifconfig lists packet losses: 11 in about a minute of connection time (~200kB of transferred data).  eth1 and eth2 are both unplugged and are the on-board chip and a PCI chip respectively. Eth0 was the netgear card which has been removed from the server a while ago. Ubuntu still reserves eth0 for it...
```

sulla@freedom:~$ ifconfig -a
eth1      Link encap:Ethernet  HWaddr 00:25:22:33:d3:97
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth2      Link encap:Ethernet  HWaddr 00:24:01:ed:33:c4
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth3      Link encap:Ethernet  HWaddr 68:05:ca:23:2d:ac
          inet addr:192.168.0.1  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1400  Metric:1
          RX packets:2286 errors:0 dropped:11 overruns:0 frame:0
          TX packets:2143 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:210793 (210.7 KB)  TX bytes:246757 (246.7 KB)
          Interrupt:17 Memory:fe9e0000-fea00000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:2210 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2210 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:368804 (368.8 KB)  TX bytes:368804 (368.8 KB)

```

and

```

sulla@freedom:~$ lsmod
Module                  Size  Used by
dm_crypt               22832  0
edac_core              62342  0
psmouse                97655  0
serio_raw              13413  0
edac_mce_amd           22617  0
k8temp                 12978  0
snd_hda_codec_hdmi     41154  1
sp5100_tco             13979  0
snd_hda_codec_realtek    56475  1
i2c_piix4              22106  0
snd_hda_intel          52267  0
snd_hda_codec         188738  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm               102033  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_timer              29433  1 snd_pcm
snd                    69141  7 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_hda_codec,snd_hda_intel
soundcore              12680  1 snd
shpchp                 37032  0
lp                     17759  0
mac_hid                13205  0
parport                42299  1 lp
btrfs                 830375  2
zlib_deflate           26914  1 btrfs
libcrc32c              12644  1 btrfs
raid10                 48079  0
raid456                77558  1
async_raid6_recov      12984  1 raid456
async_memcpy           12769  1 raid456
async_pq               13326  1 raid456
async_xor              13121  2 async_pq,raid456
async_tx               13509  5 async_pq,raid456,async_xor,async_memcpy,async_raid6_recov
xor                    21411  2 btrfs,async_xor
raid6_pq               97812  3 async_pq,btrfs,async_raid6_recov
raid1                  35557  3
raid0                  17842  0
multipath              13145  0
linear                 12894  0
radeon               1408158  1
pata_acpi              13038  0
i2c_algo_bit           13413  1 radeon
ttm                    84169  1 radeon
pata_atiixp            13271  0
e1000e                254604  0
drm_kms_helper         52710  1 radeon
drm                   297056  3 ttm,drm_kms_helper,radeon
ptp                    18580  1 e1000e
pps_core               19057  1 ptp
ahci                   25819  8
r8169                  67581  0
mii                    13934  1 r8169
wmi                    19070  0
libahci                32009  1 ahci

```

Something I don't understand (but I don't know too much of modules): the intel network card uses the e1000e driver, but lsmod lists a count of 0 on this module. But it lists "ptp" with a count of 1 on the e1000e module.

---

### Post by sulla on 2014-03-21
What I could try tomorrow: download some live-linux, boot the server from USB stick, install ssh server on the live system and see if it behaves the same. Any suggestions for an adequate live distro? Shouldn't be Ubuntu or debian based, or should it?

---

### Post by varunendra on 2014-03-21
Different distributions tend to implement the kernel a bit differently. So trying a non-debian-based distro may have its own advantage of offering the same drivers with a different 'touch' or tweaks.

For lightweight distro, you may try Knoppix or Slax. For the "bleeding-edge" kernel/drivers, you may try Fedora (I have never tried that myself though).

By the way, the Gigabit network needs some very advanced technology and a very good mutual "Shake Hand" between the NIC and the switch/router. It may be possible that both your routers are not liking the default settings of the Linux drivers, or the cables are not able to keep up with the Gigabit speeds. I remember having tested a Netgear 8-port switch once with an Asus M5A-78M-LX motherboard based PC (running Linux mint 10). It connected at Gigabit speed ONLY when connected via a cat-6 cable. The cat-5 we had only connected at 100 Mb/s speed, even if I used half meter patch cables!

To be honest, I'm out of ideas at the moment, but this part of your first post -
> I also tried to slow the cards down to 100Mbit full duplex: when connected to the gigabit switches they don't work.
..makes me suspicious of buggy firmware/implementation within the switches. If it is happening with all combination of card/switch, I'll doubt the switch more than the kernel. Of course unless your method to slow it down was itself wrong. How did you try to slow it down? The command/method?

---

### Post by sulla on 2014-03-21
I'm pretty sure I used
```

sudo ethtool -s eth3 speed 100 duplex full

```
I shall try it again in a minute.
I can  aslo try a doubly-shielded cat6 cables... I somehow assumed cat 5e cables were good enough.

But I'll have to buy them, so I can't report on this today, but there's always a need for those...

---

### Post by varunendra on 2014-03-21
Make it -
```
sudo ethtool -s eth3 speed 100 duplex full **[COLOR="#FF0000"]autoneg off[/COLOR]**
```

Although it wouldn't solve the purpose, just a test to see if things other than Gb speeds are working normally.

---

### Post by sulla on 2014-03-21
ok, also without "autoneg off" it ran at 100MBit, according to ethtool: The problem persisted.

I also tried it with "autoneg off". no improvement.
I now swap cables between client PC (this cable seems reliable at 1 Gbit) and the server and I'll connect the client PC to the 100 MBit router and the server to the gigabit switch.
let's see.

---

### Post by sulla on 2014-03-21
no change with cables reversed... when connected to the gigabit switch the server loses packets, whether on 100MBit or on Gigabit speed.
GRRRRRRRR...
I'll try cat 6 cables next...

---

### Post by varunendra on 2014-03-21
> **sulla said:**
> I also tried it with "autoneg off". no improvement.
Too bad. :( To me it indicates that something is certainly not "Normal" here, means - unique to your devices or network.

Autonegotiation is essential for gigabit mode, so make sure to turn it on again to be able to test the gigabit speeds.

---

### Post by sulla on 2014-03-22
I tried it this morning with cat6 cables, doubly shielded. The link comes up at 1 Gbit, as usual, but the problems persist. Thus it's not the cables.
pinging the server from the Client yields, e.g.
```

C:\Users\sulla>ping 192.168.0.1 -t
Ping wird ausgeführt für 192.168.0.1 mit 32 Bytes Daten:
Antwort von 192.168.0.1: Bytes=32 Zeit<1ms TTL=64
Antwort von 192.168.0.1: Bytes=32 Zeit<1ms TTL=64
Antwort von 192.168.0.1: Bytes=32 Zeit<1ms TTL=64
Antwort von 192.168.0.1: Bytes=32 Zeit<1ms TTL=64
Antwort von 192.168.0.1: Bytes=32 Zeit<1ms TTL=64
Antwort von 192.168.0.1: Bytes=32 Zeit<1ms TTL=64
Antwort von 192.168.0.1: Bytes=32 Zeit<1ms TTL=64
Antwort von 192.168.0.1: Bytes=32 Zeit<1ms TTL=64
Antwort von 192.168.0.1: Bytes=32 Zeit<1ms TTL=64
Antwort von 192.168.0.1: Bytes=32 Zeit<1ms TTL=64
Antwort von 192.168.0.1: Bytes=32 Zeit<1ms TTL=64
Antwort von 192.168.0.1: Bytes=32 Zeit<1ms TTL=64
Antwort von 192.168.0.1: Bytes=32 Zeit<1ms TTL=64
Antwort von 192.168.0.1: Bytes=32 Zeit<1ms TTL=64
Antwort von 192.168.0.1: Bytes=32 Zeit<1ms TTL=64
Antwort von 192.168.0.1: Bytes=32 Zeit<1ms TTL=64
Antwort von 192.168.0.1: Bytes=32 Zeit<1ms TTL=64
Antwort von 192.168.0.1: Bytes=32 Zeit<1ms TTL=64
Antwort von 192.168.0.1: Bytes=32 Zeit<1ms TTL=64
Antwort von 192.168.0.1: Bytes=32 Zeit<1ms TTL=64
Antwort von 192.168.0.1: Bytes=32 Zeit<1ms TTL=64
Antwort von 192.168.0.1: Bytes=32 Zeit<1ms TTL=64
Antwort von 192.168.0.1: Bytes=32 Zeit<1ms TTL=64
Antwort von 192.168.0.1: Bytes=32 Zeit<1ms TTL=64
Antwort von 192.168.0.1: Bytes=32 Zeit<1ms TTL=64
Antwort von 192.168.0.1: Bytes=32 Zeit<1ms TTL=64
Antwort von 192.168.0.1: Bytes=32 Zeit<1ms TTL=64
Antwort von 192.168.0.1: Bytes=32 Zeit<1ms TTL=64
Antwort von 192.168.0.1: Bytes=32 Zeit<1ms TTL=64
Antwort von 192.168.0.1: Bytes=32 Zeit<1ms TTL=64
Antwort von 192.168.0.1: Bytes=32 Zeit<1ms TTL=64
Antwort von 192.168.0.1: Bytes=32 Zeit<1ms TTL=64
Antwort von 192.168.0.1: Bytes=32 Zeit<1ms TTL=64
Antwort von 192.168.0.1: Bytes=32 Zeit<1ms TTL=64
Antwort von 192.168.0.1: Bytes=32 Zeit<1ms TTL=64
Antwort von 192.168.0.1: Bytes=32 Zeit<1ms TTL=64
Antwort von 192.168.0.1: Bytes=32 Zeit<1ms TTL=64
Antwort von 192.168.0.1: Bytes=32 Zeit<1ms TTL=64
Antwort von 192.168.0.1: Bytes=32 Zeit<1ms TTL=64
Antwort von 192.168.0.1: Bytes=32 Zeit<1ms TTL=64
Zeitüberschreitung der Anforderung.
Zeitüberschreitung der Anforderung.
Zeitüberschreitung der Anforderung.
Antwort von 192.168.0.1: Bytes=32 Zeit<1ms TTL=64
Antwort von 192.168.0.1: Bytes=32 Zeit<1ms TTL=64
Antwort von 192.168.0.1: Bytes=32 Zeit<1ms TTL=64
Antwort von 192.168.0.1: Bytes=32 Zeit<1ms TTL=64
Antwort von 192.168.0.1: Bytes=32 Zeit<1ms TTL=64
Antwort von 192.168.0.1: Bytes=32 Zeit<1ms TTL=64
Antwort von 192.168.0.1: Bytes=32 Zeit<1ms TTL=64
Antwort von 192.168.0.1: Bytes=32 Zeit<1ms TTL=64
Antwort von 192.168.0.1: Bytes=32 Zeit<1ms TTL=64
Antwort von 192.168.0.1: Bytes=32 Zeit<1ms TTL=64
Antwort von 192.168.0.1: Bytes=32 Zeit<1ms TTL=64
Antwort von 192.168.0.1: Bytes=32 Zeit<1ms TTL=64
Antwort von 192.168.0.1: Bytes=32 Zeit<1ms TTL=64
Antwort von 192.168.0.1: Bytes=32 Zeit<1ms TTL=64
Antwort von 192.168.0.1: Bytes=32 Zeit<1ms TTL=64
Antwort von 192.168.0.1: Bytes=32 Zeit<1ms TTL=64
Antwort von 192.168.0.1: Bytes=32 Zeit<1ms TTL=64
Antwort von 192.168.0.1: Bytes=32 Zeit<1ms TTL=64
Antwort von 192.168.0.1: Bytes=32 Zeit<1ms TTL=64
Antwort von 192.168.0.1: Bytes=32 Zeit<1ms TTL=64
Antwort von 192.168.0.1: Bytes=32 Zeit<1ms TTL=64
Antwort von 192.168.0.1: Bytes=32 Zeit<1ms TTL=64
Antwort von 192.168.0.1: Bytes=32 Zeit<1ms TTL=64
Antwort von 192.168.0.1: Bytes=32 Zeit<1ms TTL=64
Zeitüberschreitung der Anforderung.
Zeitüberschreitung der Anforderung.
Zeitüberschreitung der Anforderung.
Zeitüberschreitung der Anforderung.
Zeitüberschreitung der Anforderung.
Antwort von 192.168.0.1: Bytes=32 Zeit<1ms TTL=64
Antwort von 192.168.0.1: Bytes=32 Zeit<1ms TTL=64
Antwort von 192.168.0.1: Bytes=32 Zeit<1ms TTL=64
Antwort von 192.168.0.1: Bytes=32 Zeit<1ms TTL=64
Zeitüberschreitung der Anforderung.
Antwort von 192.168.0.1: Bytes=32 Zeit<1ms TTL=64
Zeitüberschreitung der Anforderung.
Zeitüberschreitung der Anforderung.
Zeitüberschreitung der Anforderung.
Zeitüberschreitung der Anforderung.
Antwort von 192.168.0.1: Bytes=32 Zeit<1ms TTL=64
Zeitüberschreitung der Anforderung.
Zeitüberschreitung der Anforderung.
Zeitüberschreitung der Anforderung.
Zeitüberschreitung der Anforderung.
Antwort von 192.168.0.1: Bytes=32 Zeit<1ms TTL=64
Zeitüberschreitung der Anforderung.
Zeitüberschreitung der Anforderung.
Zeitüberschreitung der Anforderung.
Zeitüberschreitung der Anforderung.
Zeitüberschreitung der Anforderung.
Zeitüberschreitung der Anforderung.
Zeitüberschreitung der Anforderung.
Zeitüberschreitung der Anforderung.
Zeitüberschreitung der Anforderung.
Zeitüberschreitung der Anforderung.
Zeitüberschreitung der Anforderung.
Zeitüberschreitung der Anforderung.
Zeitüberschreitung der Anforderung.

```

So, I'll try ubuntu live CD next, so see if the live-ubuntu from USB stick treats the network stack somehow differently than my several-times-do-release-upgraded server installation. I'll report back.

---

### Post by sulla on 2014-03-22
So, it's getting stranger or clearer, depending on the viewpoint:

I started the server from USB live CD: ubuntu-13.10-desktop 64bit (just downloaded), the same as on the server (except: the server has no GUI): it runs kernel 3.11.0-12-generic (the server uses 3.11.0.18 I believe, so the kernel from the live-CD is a bit older...)

I connected the server (the PCIe intel network card, this time called eth2) to the gigabit switch, so it's in the "problematic" state, configuration by DHCP, but the parameters match.
pinging from the client PC (Windows) works now perfectly, I've done 20000 pings, not a single ping has been lost so far. Still pinging...

I added a test-user (for sshd) and installed openssh-server and connected form the client PC to the ubuntu-desktop on the server.

So, if it continues to work well from the live-CD, my suspicion is that my networking stack of my server installation is broken somewhere?? Perhaps you can find some hint in the following command outputs (the same as provided earlier)
```

$ sudo lshw -numeric -C network
  *-network
       description: Ethernet interface
       product: 82574L Gigabit Network Connection [8086:10D3]
       vendor: Intel Corporation [8086]
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth2
       version: 00
       serial: 68:05:ca:23:2d:ac
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=2.3.2-k duplex=full firmware=1.8-0 ip=192.168.0.50 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:17 memory:fe9e0000-fe9fffff memory:fe900000-fe97ffff ioport:c800(size=32) memory:fe9dc000-fe9dffff memory:fe980000-fe9bffff
  *-network
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10EC:8168]
       vendor: Realtek Semiconductor Co., Ltd. [10EC]
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 03
       serial: 00:25:22:33:d3:97
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8168d-1.fw latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:45 ioport:d800(size=256) memory:fdfff000-fdffffff memory:fdff8000-fdffbfff memory:feae0000-feafffff
  *-network
       description: Ethernet interface
       product: DGE-528T Gigabit Ethernet Adapter [1186:4300]
       vendor: D-Link System Inc [1186]
       physical id: 5
       bus info: pci@0000:04:05.0
       logical name: eth1
       version: 10
       serial: 00:24:01:ed:33:c4
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=64 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10Mbit/s
       resources: irq:20 ioport:e800(size=256) memory:febffc00-febffcff memory:febc0000-febdffff

```

```

$ sudo ethtool eth2
Settings for eth2:
        Supported ports: [ TP ]
        Supported link modes:   10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Full
        Supported pause frame use: No
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Full
        Advertised pause frame use: No
        Advertised auto-negotiation: Yes
        Speed: 1000Mb/s
        Duplex: Full
        Port: Twisted Pair
        PHYAD: 1
        Transceiver: internal
        Auto-negotiation: on
        MDI-X: off (auto)
        Supports Wake-on: pumbg
        Wake-on: g
        Current message level: 0x00000007 (7)
                               drv probe link
        Link detected: yes

```

```

$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:25:22:33:d3:97
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth1      Link encap:Ethernet  HWaddr 00:24:01:ed:33:c4
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth2      Link encap:Ethernet  HWaddr 68:05:ca:23:2d:ac
          inet addr:192.168.0.50  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::6a05:caff:fe23:2dac/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11542 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7601 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:6832681 (6.8 MB)  TX bytes:1026654 (1.0 MB)
          Interrupt:17 Memory:fe9e0000-fea00000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:804 errors:0 dropped:0 overruns:0 frame:0
          TX packets:804 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:75840 (75.8 KB)  TX bytes:75840 (75.8 KB)

```

```

$ lsmod
Module                  Size  Used by
dm_crypt               22728  0
hid_generic            12548  0
joydev                 17377  0
hid_microsoft          12805  0
usbhid                 53014  0
hid                   101512  3 hid_generic,hid_microsoft,usbhid
psmouse                97626  0
snd_hda_codec_hdmi     41276  1
snd_hda_codec_realtek    51465  1
snd_seq_midi           13324  0
snd_seq_midi_event     14899  1 snd_seq_midi
serio_raw              13413  0
snd_hda_intel          48171  5
snd_rawmidi            30095  1 snd_seq_midi
snd_hda_codec         188738  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
dm_multipath           22843  0
k8temp                 12978  0
edac_core              62312  0
edac_mce_amd           22617  0
snd_hwdep              13602  1 snd_hda_codec
scsi_dh                14882  1 dm_multipath
snd_pcm               102033  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
sp5100_tco             13979  0
i2c_piix4              22106  0
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_timer              29433  2 snd_pcm,snd_seq
snd                    69141  21 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
parport_pc             32701  0
bnep                   19564  2
soundcore              12680  1 snd
ppdev                  17671  0
rfcomm                 69070  0
lp                     17759  0
parport                42299  3 lp,ppdev,parport_pc
ohci_pci               13561  0
bluetooth             371874  10 bnep,rfcomm
shpchp                 37032  0
mac_hid                13205  0
squashfs               47663  1
overlayfs              27858  1
nls_iso8859_1          12713  2
dm_mirror              22056  0
dm_region_hash         20784  1 dm_mirror
dm_log                 18411  2 dm_region_hash,dm_mirror
usb_storage            62062  2
pata_acpi              13038  0
radeon               1402449  3
pata_atiixp            13242  0
r8169                  67341  0
mii                    13934  1 r8169
e1000e                250025  0
ptp                    18580  1 e1000e
pps_core               19027  1 ptp
i2c_algo_bit           13413  1 radeon
ttm                    83995  1 radeon
drm_kms_helper         52651  1 radeon
drm                   296739  5 ttm,drm_kms_helper,radeon
wmi                    19070  0
ahci                   25819  0
libahci                31898  1 ahci

```
Aside form reinstalling the server completely (nooooooo, I dooooooooon't want to do this, the setup is a bit complicated with RAIDs, LVM and troublesome with configurations for various servers like email, ftp, samba, LAMP...), is there anything I can fix on the server-installation??

---

### Post by sulla on 2014-03-22
The only difference I can see is that "sudo ethtool ethX" differs in one parameter: MDI-X:
desktop-CD: MDI-X: off (auto)
server-installation: MDI-X: on (auto)
but both, the old cat 5 and the new cat6 cables are straight ones, no crossover. Probably this is merely related to which end of the cable is plugged in first?
the modules are a bit different, but I don't know if this is network related and thus of any significance.

---

### Post by sulla on 2014-03-28
ok, I'll wait for the do-release-upgrade to Trusty Thar 14.04, and if this doesn't fix things, I'll reinstall

---

