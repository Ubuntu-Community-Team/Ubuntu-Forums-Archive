---
title: "Netgear WNA3100M via Ndiswrapper, Ubuntu 10.10 = not working"
date: 2014-05-23
forum: Networking &amp; Wireless
---

### Post by shaded3 on 2014-05-23
Hello everyone, :P

First, I must apologies for my horrible English (french speaker here). I’ll do my best anyway.
 
After hours and hours of solo research, I come here to find some help because I do not see how to get out of my problem. Obviously like many others, I bought a Netgear wifi key WNA3100M.
My Ubuntu distribution is fairly old (10.10), because I’m using some software / scripts that do not run on newer versions.
As recommended, I’ve installed "ndiswrapper". After a tons of tests (32/64 bit versions, drivers w7, w2000, etc), I found a driver that returns to me that (ndsiwrapper-l) :
 
```
netwna3100m : driver installed
device (0846:9021) present

```
 
 
Despite this, no wifi.
So I do ifconfig, and I get:
```

eth0      Link encap:Ethernet  HWaddr 00:23:54:7a:8b:21             inet adr:xxx.xxx.x.xx  Bcast:xxx.xxx.x.xxx  Masque:255.255.255.0           adr inet6: fe80::223:54ff:fe7a:8b21/64 Scope:Lien           UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1           Packets reçus:17084 erreurs:0 :0 overruns:0 frame:0           TX packets:14297 errors:0 dropped:0 overruns:0 carrier:1           collisions:0 lg file transmission:1000            Octets reçus:20614489 (20.6 MB) Octets transmis:1797053 (1.7 MB)           Interruption:46    lo        Link encap:Boucle locale             inet adr:127.0.0.1  Masque:255.0.0.0           adr inet6: ::1/128 Scope:Hôte           UP LOOPBACK RUNNING  MTU:16436  Metric:1           Packets reçus:290 erreurs:0 :0 overruns:0 frame:0           TX packets:290 errors:0 dropped:0 overruns:0 carrier:0           collisions:0 lg file transmission:0            Octets reçus:50865 (50.8 KB) Octets transmis:50865 (50.8 KB)

``` 
So, no wlan0 there :( I’ve also tried “ifconfig wlan0 up”… without any result.
For "lshw-C Network", I get:
```

*-network                       description: Ethernet interface        product: AR8121/AR8113/AR8114 Gigabit or Fast Ethernet        vendor: Atheros Communications        physical id: 0        bus info: pci@0000:02:00.0        logical name: eth0        version: b0        serial: 00:23:54:7a:8b:21        size: 100MB/s        capacity: 1GB/s        width: 64 bits        clock: 33MHz        capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation        configuration: autonegotiation=on broadcast=yes driver=ATL1E driverversion=1.0.0.7-NAPI duplex=full firmware=L1e ip=xxx.xxx.x.xx latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s        resources: irq:46 memory:fe9c0000-fe9fffff ioport:dc00(size=128)

```
 
The "modprobe ndiswrapper" and "ndiswrapper-m" commands do not return any error.

I followed several tutorials, including:
[http://ubuntuforums.org/showthread.php?t=885847](http://ubuntuforums.org/showthread.php?t=885847)
and I’ve read a lot of information on the french forum, without being able to unlock myself.

Full report here:
```

>>    cat /etc/lsb-release  DISTRIB_ID=UbuntuDISTRIB_RELEASE=10.10DISTRIB_CODENAME=maverickDISTRIB_DESCRIPTION="Ubuntu 10.10" >>    lsusb  Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hubBus 007 Device 002: ID 046d:c077 Logitech, Inc. Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hubBus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hubBus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hubBus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hubBus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hubBus 002 Device 003: ID 0846:9021 NetGear, Inc. Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hubBus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub >>    lspci -k -nn | grep -A 3 -i net  02:00.0 Ethernet controller [0200]: Atheros Communications AR8121/AR8113/AR8114 Gigabit or Fast Ethernet [1969:1026] (rev b0)        Subsystem: ASUSTeK Computer Inc. P5KPL-CM Motherboard [1043:8304]        Kernel driver in use: ATL1E        Kernel modules: atl1e >>    sudo lshw -C network    *-network       description: Ethernet interface       product: AR8121/AR8113/AR8114 Gigabit or Fast Ethernet       vendor: Atheros Communications       physical id: 0       bus info: pci@0000:02:00.0       logical name: eth0       version: b0       serial: 00:23:54:7a:8b:21       size: 100MB/s       capacity: 1GB/s       width: 64 bits       clock: 33MHz       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation       configuration: autonegotiation=on broadcast=yes driver=ATL1E driverversion=1.0.0.7-NAPI duplex=full firmware=L1e ip=xxx.xxx.x.xx latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s       resources: irq:46 memory:fe9c0000-fe9fffff ioport:dc00(size=128) >>    lsmod  Module                  Size  Used bybinfmt_misc             6599  1 parport_pc             26378  1 ppdev                   5556  0 snd_hda_codec_atihdmi     2411  1 snd_hda_codec_realtek   218460  1 snd_hda_intel          22299  0 snd_hda_codec          87552  3 snd_hda_codec_atihdmi,snd_hda_codec_realtek,snd_hda_intelfglrx                2252898  306 snd_hwdep               5040  1 snd_hda_codecsnd_pcm                71603  2 snd_hda_intel,snd_hda_codecsnd_seq_midi            4588  0 snd_rawmidi            17783  1 snd_seq_midisnd_seq_midi_event      6047  1 snd_seq_midisnd_seq                47174  2 snd_seq_midi,snd_seq_midi_eventasus_atk0110           11423  0 snd_timer              19067  2 snd_pcm,snd_seqsnd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seqndiswrapper           184384  0 intel_agp              26926  0 snd                    49102  9 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_deviceagpgart                32075  2 fglrx,intel_agpsoundcore                880  1 sndsnd_page_alloc          7216  2 snd_hda_intel,snd_pcmlp                      7342  0 parport                31492  3 parport_pc,ppdev,lpusbhid                 36978  0 firewire_ohci          21554  0 hid                    67742  1 usbhidbtrfs                 489626  0 floppy                 54343  0 firewire_core          46675  1 firewire_ohcicrc_itu_t               1383  1 firewire_corezlib_deflate           19266  1 btrfspata_jmicron            1855  0 ahci                   19326  0 atl1e                  29492  0 libahci                21792  1 ahcicrc32c                  2531  1 libcrc32c                887  1 btrfs>>    iwconfig   >>    ifconfig -a  eth0      Link encap:Ethernet  HWaddr 00:23:54:7a:8b:21            inet adr:xxx.xxx.x.xx  Bcast:xxx.xxx.x.xxx  Masque:255.255.255.0          adr inet6: fe80::223:54ff:fe7a:8b21/64 Scope:Lien          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1          Packets reçus:17689 erreurs:0 :0 overruns:0 frame:0          TX packets:14868 errors:0 dropped:0 overruns:0 carrier:1          collisions:0 lg file transmission:1000           Octets reçus:21114645 (21.1 MB) Octets transmis:1870323 (1.8 MB)          Interruption:46  lo        Link encap:Boucle locale            inet adr:127.0.0.1  Masque:255.0.0.0          adr inet6: ::1/128 Scope:Hôte          UP LOOPBACK RUNNING  MTU:16436  Metric:1          Packets reçus:405 erreurs:0 :0 overruns:0 frame:0          TX packets:405 errors:0 dropped:0 overruns:0 carrier:0          collisions:0 lg file transmission:0           Octets reçus:66130 (66.1 KB) Octets transmis:66130 (66.1 KB)  >>    sudo iwlist scan   >>    uname -r -m  2.6.35-30-generic-pae i686 >>    cat /etc/network/interfaces  auto loiface lo inet loopbackauto lo wlan0 >>    nm-tool   NetworkManager Tool State: connected - Device: eth0  [Auto eth0] ----------------------------------------------------  Type:              Wired  Driver:            ATL1E  State:             connected  Default:           yes  HW Address:        00:23:54:7A:8B:21   Capabilities:    Carrier Detect:  yes    Speed:           100 Mb/s   Wired Properties    Carrier:         on   IPv4 Settings:    Address:         xxx.xxx.x.xx    Prefix:          24 (255.255.255.0)    Gateway:        xxx.xxx.x.x     DNS:             xxx.xxx.x.x   >>    sudo rfkill list 

```
 
I’ve got the feeling that the ndiswrapper works, so perhaps the problem come from something else?
Another driver (32 bits this one) should work and is known to work, but it just give me :
bcmwlhigh5: driver installed
… and nothing else…
 
My experience on Linux is not very shiny, so I admit that your help would be *** very valuable ***. 
What should you do in your opinion please?
Thanks a lot for reading this, and thanks for any idea.
Cheers.

---

### Post by mörgæs on 2014-05-24
Hi, welcome to the fora.

I don't think people here use nor are able to give advice about 10.10, which has been obsolete for two years. Which software / scripts are keeping you away from using 14.04?

---

### Post by Matzas on 2014-06-14
Hi
Try adding text "ndiswrapper" in the file </etc/modules>

I have the same problem but with the latest Ubuntu version. It does not even recognise the driver. So you are probably better of using the older version. That wifi dongle is old, therefore cheap. Ubuntu have always had problems with old wifi hardware. Good luck.

---

