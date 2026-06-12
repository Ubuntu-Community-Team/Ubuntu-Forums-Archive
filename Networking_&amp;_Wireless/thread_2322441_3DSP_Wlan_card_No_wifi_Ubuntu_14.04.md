---
title: "3DSP Wlan card No wifi Ubuntu 14.04"
date: 2016-04-28
forum: Networking &amp; Wireless
---

### Post by gardak on 2016-04-28
EDIT: I changed the title beacouse i tought the problem was the lan adapter but the problem is thet the 3dsp  wlan card isnt even recognised by the SO

Hello! I tryed to fix this problem by myself but I couldnt (Updating drivers, kernel, etc) Im really noob in ubuntu, I just installed this yesterday in one pc with no problem and today in the next pc i cant get the wifi running, in windows 7 it works just fine, but in ubuntu its like there is no wifi hardware.
I read and try allot of solutions in the forums and nothing work
Im willing to install a diferent vertion of ubuntu or whatever can fix this problem, I really like this SO and im going to love if i can make it work, so thx for your help and sorry for my broken english!


```
########## wireless info START ##########

Report from: 28 Apr 2016 04:32 ART -0300

Booted last: 28 Apr 2016 04:29 ART -0300

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.4 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 4.2.0-35-generic #40~14.04.1-Ubuntu SMP Fri Mar 18 16:39:02 UTC 2016 i686 i686 i686 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [10ec:8136] (rev 02)
    Subsystem: Device [1991:6030]
    Kernel driver in use: r8169

04:00.0 Ethernet controller [0200]: Device [1a47:0003]

##### lsusb #############################

Bus 001 Device 003: ID eb1a:2761 eMPIA Technology, Inc. EeePC 701 integrated Webcam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 1c4f:0003 SiGma Micro HID controller
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

##### rfkill ############################

##### lsmod #############################

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.0.7  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'eth0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:460 errors:0 dropped:0 overruns:0 frame:0
          TX packets:592 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:185033 (185.0 KB)  TX bytes:73694 (73.6 KB)

##### iwconfig ##########################

lo        no wireless extensions.

eth0      no wireless extensions.

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

    NetworkManager

Running:

root       646     1  0 04:29 ?        00:00:00 NetworkManager

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: eth0  [Conexión cableada 1] -----------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.0.7
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             190.7.31.226
    DNS:             190.57.228.25

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

##### NetworkManager profiles ###########

##### iw reg get ########################

Region: America/Argentina/Buenos_Aires (based on set time zone)

country 00:
    (2402 - 2472 @ 40), (6, 20)
    (2457 - 2482 @ 40), (6, 20), PASSIVE-SCAN
    (2474 - 2494 @ 20), (6, 20), NO-OFDM, PASSIVE-SCAN
    (5170 - 5250 @ 160), (6, 20), PASSIVE-SCAN
    (5250 - 5330 @ 160), (6, 20), DFS, PASSIVE-SCAN
    (5490 - 5730 @ 160), (6, 20), DFS, PASSIVE-SCAN
    (5735 - 5835 @ 80), (6, 20), PASSIVE-SCAN
    (57240 - 63720 @ 2160), (N/A, 0)

##### iwlist channels ###################

lo        no frequency information.

eth0      no frequency information.

##### iwlist scan #######################

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

##### module infos ######################

##### module parameters #################

##### /etc/modules ######################

lp

##### modprobe options ##################

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac

[/etc/modprobe.d/blacklist-rare-network.conf]
alias net-pf-3 off
alias net-pf-6 off
alias net-pf-9 off
alias net-pf-11 off
alias net-pf-12 off
alias net-pf-19 off
alias net-pf-21 off
alias net-pf-36 off

[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8136 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

##### dmesg #############################

[   20.421616] r8169 0000:02:00.0 eth0: link down (repeated 2 times)
[   20.422447] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   22.160367] r8169 0000:02:00.0 eth0: link up
[   22.160392] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready

########## wireless info END ############



##########Plus###########
ominoreg@ominoreg-Calistoga-ICH7M-Chipset:~$ sudo lshw -C network
[sudo] password for ominoreg: 
  *-network               
       descripción: Ethernet interface
       producto: RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller
       fabricante: Realtek Semiconductor Co., Ltd.
       id físico: 0
       información del bus: pci@0000:02:00.0
       nombre lógico: eth0
       versión: 02
       serie: 00:e0:4c:75:ac:38
       tamaño: 100Mbit/s
       capacidad: 100Mbit/s
       anchura: 64 bits
       reloj: 33MHz
       capacidades: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuración: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.0.7 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       recursos: irq:26 ioport:2000(size=256) memoria:d0100000-d0100fff memoria:d0000000-d000ffff memoria:d0120000-d013ffff
  *-network NO RECLAMADO
       descripción: Ethernet controller
       id físico: 0
       información del bus: pci@0000:04:00.0
       versión: 00
       anchura: 32 bits
       reloj: 33MHz
       capacidades: pm bus_master cap_list
       configuración: latency=120 maxlatency=8 mingnt=15
       recursos: memoria:d0200000-d0207fff
```

---

### Post by ajgreeny on 2016-04-28
You have no wireless device shown at all, unfortunately.

You obviously are certain there is one as it works in Windows properly, but it would be good to know what adapter it is; can you find that information when using Windows?

---

### Post by gardak on 2016-04-29
3DSP WLAN (and bluetooth) CARD I tyied this "https://github.com/Alamot/3dsp" but still isn't working. Insted of 
sudo bash Install_3DSP.sh  I used sudo bash Install_3DSPUSB.sh beaocuse there werent any file like that in the directory 

So, nothing yet.

```
ominoreg@ominoreg-Calistoga-ICH7M-Chipset:~$ lspci -nnk | grep -iA2 net
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [10ec:8136] (rev 02)
    Subsystem: Device [1991:6030]
    Kernel driver in use: r8169
--
04:00.0 Ethernet controller [0200]: Device [1a47:0003]
ominoreg@ominoreg-Calistoga-ICH7M-Chipset:~$ lsusb
Bus 001 Device 003: ID eb1a:2761 eMPIA Technology, Inc. EeePC 701 integrated Webcam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 1c4f:0003 SiGma Micro HID controller
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
ominoreg@ominoreg-Calistoga-ICH7M-Chipset:~$ lsmod
Module                  Size  Used by
3dspusbbt              24576  0 
3dspusbbtpriv         577536  1 3dspusbbt
3dspusbwlan            36864  0 
3dspusbwlanpriv       307200  1 3dspusbwlan
3dspusbbus             16384  2 3dspusbwlan,3dspusbbt
snd_hda_codec_realtek    77824  1 
snd_hda_codec_generic    69632  1 snd_hda_codec_realtek
snd_hda_intel          32768  5 
snd_hda_codec         114688  3 snd_hda_codec_realtek,snd_hda_codec_generic,snd_hda_intel
snd_hda_core           57344  4 snd_hda_codec_realtek,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel
snd_hwdep              16384  1 snd_hda_codec
snd_pcm                94208  4 snd_hda_codec,snd_hda_intel,snd_hda_core
snd_seq_midi           16384  0 
snd_seq_midi_event     16384  1 snd_seq_midi
uvcvideo               73728  0 
snd_rawmidi            28672  1 snd_seq_midi
videobuf2_vmalloc      16384  1 uvcvideo
videobuf2_memops       16384  1 videobuf2_vmalloc
snd_seq                57344  2 snd_seq_midi_event,snd_seq_midi
videobuf2_core         49152  1 uvcvideo
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
v4l2_common            16384  1 videobuf2_core
snd_timer              28672  2 snd_pcm,snd_seq
videodev              143360  3 uvcvideo,v4l2_common,videobuf2_core
coretemp               16384  0 
i915                 1036288  3 
bnep                   20480  2 
rfcomm                 65536  0 
media                  24576  2 uvcvideo,videodev
input_leds             16384  0 
snd                    69632  19 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
bluetooth             454656  11 bnep,rfcomm,3dspusbbt
joydev                 20480  0 
drm_kms_helper        114688  1 i915
serio_raw              16384  0 
lpc_ich                20480  0 
drm                   303104  5 i915,drm_kms_helper
i2c_algo_bit           16384  1 i915
shpchp                 32768  0 
soundcore              16384  1 snd
topstar_laptop         16384  0 
sparse_keymap          16384  1 topstar_laptop
video                  24576  1 i915
parport_pc             32768  0 
ppdev                  20480  0 
lp                     16384  0 
mac_hid                16384  0 
parport                45056  3 lp,ppdev,parport_pc
hid_generic            16384  0 
usbhid                 49152  0 
hid                    98304  2 hid_generic,usbhid
psmouse               114688  0 
r8101                 172032  0 
r8169                  73728  0 
pata_acpi              16384  0 
mii                    16384  1 r8169
ominoreg@ominoreg-Calistoga-ICH7M-Chipset:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ominoreg@ominoreg-Calistoga-ICH7M-Chipset:~$ ifconfig -a
eth0      Link encap:Ethernet  direcciónHW 00:e0:4c:75:ac:38  
          ACTIVO DIFUSIÓN MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:0 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:0 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:1000 
          Bytes RX:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Bucle local  
          Direc. inet:127.0.0.1  Másc:255.0.0.0
          Dirección inet6: ::1/128 Alcance:Anfitrión
          ACTIVO BUCLE FUNCIONANDO  MTU:65536  Métrica:1
          Paquetes RX:1021 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:1021 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:0 
          Bytes RX:63726 (63.7 KB)  TX bytes:63726 (63.7 KB)

ominoreg@ominoreg-Calistoga-ICH7M-Chipset:~$ rfkill list
ominoreg@ominoreg-Calistoga-ICH7M-Chipset:~$ rfkill list all
ominoreg@ominoreg-Calistoga-ICH7M-Chipset:~$ rfkill ls
Usage:    rfkill [options] command
Options:
    --version    show version (0.5-1ubuntu1 (Ubuntu))
Commands:
    help
    event
    list [IDENTIFIER]
    block IDENTIFIER
    unblock IDENTIFIER
where IDENTIFIER is the index no. of an rfkill switch or one of:
    <idx> all wifi wlan bluetooth uwb ultrawideband wimax wwan gps fm nfc
ominoreg@ominoreg-Calistoga-ICH7M-Chipset:~$ rfkill list
ominoreg@ominoreg-Calistoga-ICH7M-Chipset:~$ sudo su 
[sudo] password for ominoreg: 
root@ominoreg-Calistoga-ICH7M-Chipset:/home/ominoreg# rfkill
Usage:    rfkill [options] command
Options:
    --version    show version (0.5-1ubuntu1 (Ubuntu))
Commands:
    help
    event
    list [IDENTIFIER]
    block IDENTIFIER
    unblock IDENTIFIER
where IDENTIFIER is the index no. of an rfkill switch or one of:
    <idx> all wifi wlan bluetooth uwb ultrawideband wimax wwan gps fm nfc
root@ominoreg-Calistoga-ICH7M-Chipset:/home/ominoreg# rfkill list
root@ominoreg-Calistoga-ICH7M-Chipset:/home/ominoreg# cat/etc/resolv.conf
bash: cat/etc/resolv.conf: No existe el archivo o el directorio
root@ominoreg-Calistoga-ICH7M-Chipset:/home/ominoreg# cat /etc/resolv.conf
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
root@ominoreg-Calistoga-ICH7M-Chipset:/home/ominoreg# route -n
Tabla de rutas IP del núcleo
Destino         Pasarela        Genmask         Indic Métric Ref    Uso Interfaz
root@ominoreg-Calistoga-ICH7M-Chipset:/home/ominoreg# 


```

---

### Post by gardak on 2016-04-30
If I change the ubuntu vertion it would be the same?

---

### Post by gardak on 2016-04-30
OK, windows will be on that pc, never mind xD

---

