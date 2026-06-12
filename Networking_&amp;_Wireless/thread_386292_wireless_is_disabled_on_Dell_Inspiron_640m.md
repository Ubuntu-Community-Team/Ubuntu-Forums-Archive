---
title: "wireless is disabled on Dell Inspiron 640m"
date: 2007-03-16
forum: Networking &amp; Wireless
---

### Post by orengolan on 2007-03-16
I am new to Linux, installed Ubuntu on a friend's laptop - Dell Inspiron 640m.
I can't connect with wireless (i can using LAN cable).
when i run lshw I get **'*-network DISABLED'**.
I tried enabling the wirless by clicking on Fn+F2 but i don't see any change.
is there anything I can do in the bios to enable the Function keys?
(if yes - how do i get to the bios?)

I searched for this issue here and on other places and could't find an answer, 
I am really new so be easy with crazy tchnical terms.

here are the results i get when running some commands:   

**yuka@yuka-laptop:~$ lshw**
WARNING: you should run this program as super-user.
yuka-laptop               
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 502MB
     *-cpu:0
          product: Genuine Intel(R) CPU           T2400  @ 1.83GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 6.14.8
          serial: 0000-06E8-0000-0000-0000-0000
          size: 1GHz
          capacity: 1GHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc pni monitor vmx est tm2 xtpr cpufreq
          configuration: id=1
        *-logicalcpu:0
             description: Logical CPU
             physical id: 1.1
             width: 32 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 1.2
             width: 32 bits
             capabilities: logical
     *-cpu:1
          product: Genuine Intel(R) CPU           T2400  @ 1.83GHz
          vendor: Intel Corp.
          physical id: 2
          bus info: cpu@1
          version: 6.14.8
          serial: 0000-06E8-0000-0000-0000-0000
          size: 1GHz
          capacity: 1GHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc pni monitor vmx est tm2 xtpr cpufreq
          configuration: id=1
        *-logicalcpu:0
             description: Logical CPU
             physical id: 1.1
             width: 32 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 1.2
             width: 32 bits
             capabilities: logical
     *-pci
          description: Host bridge
          product: Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
        *-display:0
             description: VGA compatible controller
             product: Mobile 945GM/GMS/940GML Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@00:02.0
             version: 03
             size: 256MB
             width: 32 bits
             clock: 33MHz
             capabilities: vga bus_master cap_list
             resources: iomemory:dff00000-dff7ffff ioport:eff8-efff iomemory:c0000000-cfffffff iomemory:dfec0000-dfefffff irq:169
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile 945GM/GMS/940GML Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@00:02.1
             version: 03
             size: 512KB
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             resources: iomemory:dff80000-dfffffff
        *-multimedia
             description: Audio device
             product: 82801G (ICH7 Family) High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@00:1b.0
             version: 01
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=HDA Intel
             resources: iomemory:dfebc000-dfebffff irq:233
        *-pci:0
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@00:1c.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:1
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@00:1c.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-network DISABLED
                description: Wireless interface
                product: Broadcom Corporation
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0c:00.0
                logical name: eth1
                version: 01
                serial: 00:16:ce:63:60:bd
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=bcm43xx multicast=yes wireless=IEEE 802.11b/g
                resources: iomemory:dfdfc000-dfdfffff irq:177
        *-pci:2
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@00:1c.3
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-usb:0
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@00:1d.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd
             resources: ioport:bf80-bf9f irq:225
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.17-11-generic uhci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:1
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@00:1d.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd
             resources: ioport:bf60-bf7f irq:233
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.17-11-generic uhci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:2
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@00:1d.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd
             resources: ioport:bf40-bf5f irq:50
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.17-11-generic uhci_hcd
                physical id: 1
                bus info: usb@3
                logical name: usb3
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:3
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@00:1d.3
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd
             resources: ioport:bf20-bf3f irq:58
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.17-11-generic uhci_hcd
                physical id: 1
                bus info: usb@4
                logical name: usb4
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:4
             description: USB Controller
             product: 82801G (ICH7 Family) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@00:1d.7
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd
             resources: iomemory:ffa80000-ffa803ff irq:225
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 2.6.17-11-generic ehci_hcd
                physical id: 1
                bus info: usb@5
                logical name: usb5
                version: 2.06
                capabilities: usb-2.00
                configuration: driver=hub maxpower=0mA slots=8 speed=480.0MB/s
        *-pci:3
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@00:1e.0
             version: e1
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
           *-network
                description: Ethernet interface
                product: BCM4401-B0 100Base-TX
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@02:00.0
                logical name: eth0
                version: 02
                serial: 00:14:22:a8:28:66
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=b44 multicast=yes
                resources: iomemory:df9fe000-df9fffff irq:177
           *-firewire
                description: FireWire (IEEE 1394)
                product: Ricoh Co Ltd
                vendor: Ricoh Co Ltd
                physical id: 1
                bus info: pci@02:01.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: ohci bus_master cap_list
                configuration: driver=ohci1394
                resources: iomemory:df9fd800-df9fdfff irq:185
           *-system:0
                description: Generic system peripheral
                product: R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter
                vendor: Ricoh Co Ltd
                physical id: 1.1
                bus info: pci@02:01.1
                version: 19
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=sdhci
                resources: iomemory:df9fd400-df9fd4ff irq:66
           *-system:1 UNCLAIMED
                description: System peripheral
                product: Ricoh Co Ltd
                vendor: Ricoh Co Ltd
                physical id: 1.2
                bus info: pci@02:01.2
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                resources: iomemory:df9fd500-df9fd5ff irq:11
           *-system:2 UNCLAIMED
                description: System peripheral
                product: R5C592 Memory Stick Bus Host Adapter
                vendor: Ricoh Co Ltd
                physical id: 1.3
                bus info: pci@02:01.3
                version: 0a
                width: 32 bits
                clock: 33MHz
                capabilities: cap_list
                resources: iomemory:df9fd600-df9fd6ff irq:11
           *-system:3 UNCLAIMED
                description: System peripheral
                product: xD-Picture Card Controller
                vendor: Ricoh Co Ltd
                physical id: 1.4
                bus info: pci@02:01.4
                version: 05
                width: 32 bits
                clock: 33MHz
                capabilities: cap_list
                resources: iomemory:df9fd700-df9fd7ff irq:11
        *-isa UNCLAIMED
             description: ISA bridge
             product: 82801GBM (ICH7-M) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@00:1f.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
        *-ide
             description: IDE interface
             product: 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller IDE
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@00:1f.2
             logical name: scsi0
             logical name: scsi1
             version: 01
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master cap_list scsi-host
             configuration: driver=ata_piix
             resources: ioport:bfa0-bfaf irq:177
        *-serial UNCLAIMED
             description: SMBus
             product: 82801G (ICH7 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@00:1f.3
             version: 01
             width: 32 bits
             clock: 33MHz
             resources: ioport:10c0-10df irq:4[B]

yuka@yuka-laptop:~$ iwconfig[/B]
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:""  Nickname:"Broadcom 4311"
          Mode:Managed  Access Point: Invalid   
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.[B]

yuka@yuka-laptop:~$ lsmod[/B]
Module                  Size  Used by
ipv6                  272288  10 
binfmt_misc            13448  1 
rfcomm                 42260  0 
l2cap                  27136  5 rfcomm
bluetooth              53476  4 rfcomm,l2cap
i915                   21632  2 
drm                    74644  3 i915
speedstep_centrino      9760  1 
cpufreq_userspace       5408  0 
cpufreq_stats           7744  0 
freq_table              6048  2 speedstep_centrino,cpufreq_stats
cpufreq_powersave       2944  0 
cpufreq_ondemand        8876  2 
cpufreq_conservative     8712  0 
video                  17540  0 
tc1100_wmi              8324  0 
sbs                    16804  0 
sony_acpi               6412  0 
pcc_acpi               14080  0 
i2c_ec                  6272  1 sbs
i2c_core               23424  1 i2c_ec
hotkey                 11556  0 
dev_acpi               12292  0 
button                  7952  0 
battery                11652  0 
container               5632  0 
ac                      6788  0 
asus_acpi              17688  0 
nls_iso8859_1           5248  1 
nls_cp437               6912  1 
vfat                   14720  1 
fat                    56348  1 vfat
af_packet              24584  2 
sbp2                   24584  0 
parport_pc             37796  0 
lp                     12964  0 
parport                39496  2 parport_pc,lp
arc4                    3200  0 
ieee80211_crypt_wep     6528  0 
bcm43xx               127252  0 
joydev                 11200  0 
sr_mod                 18212  0 
cdrom                  38944  1 sr_mod
ieee80211softmac       33792  1 bcm43xx
sg                     37404  0 
b44                    26764  0 
sdhci                  20108  0 
tsdev                   9152  0 
mmc_core               32136  1 sdhci
ieee80211              35272  2 bcm43xx,ieee80211softmac
ieee80211_crypt         7552  2 ieee80211_crypt_wep,ieee80211
mii                     6912  1 b44
snd_hda_intel          20116  1 
snd_hda_codec         164608  1 snd_hda_intel
snd_pcm_oss            47360  0 
snd_mixer_oss          19584  1 snd_pcm_oss
snd_pcm                84612  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_timer              25348  1 snd_pcm
snd                    58372  8 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
serio_raw               8452  0 
intel_agp              26012  1 
agpgart                34888  3 drm,intel_agp
evdev                  11392  2 
hw_random               7320  0 
psmouse                41352  0 
pcspkr                  4352  0 
shpchp                 42144  0 
pci_hotplug            32828  1 shpchp
soundcore              11232  1 snd
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
ext3                  142856  1 
jbd                    62228  1 ext3
ohci1394               37040  0 
ieee1394              306104  2 sbp2,ohci1394
ehci_hcd               34696  0 
uhci_hcd               24968  0 
ide_generic             2432  0 
usbcore               134912  3 ehci_hcd,uhci_hcd
sd_mod                 22656  4 
generic                 6276  0 
ata_piix               11780  3 
libata                 74892  1 ata_piix
scsi_mod              144648  5 sbp2,sr_mod,sg,sd_mod,libata
thermal                15624  0 
processor              31560  2 speedstep_centrino,thermal
fan                     6020  0 
fbcon                  41504  0 
tileblit                3840  1 fbcon
font                    9344  1 fbcon
bitblit                 7168  1 fbcon
softcursor              3328  1 bitblit
vesafb                  9244  0 
capability              5896  0 
commoncap               8704  1 capability



thanks in advance!
Oren

---

### Post by Floppyjoe on 2007-03-16
You need to do  search in the forum for Broadcom 4311

---

### Post by dbott67 on 2007-03-17
I've got a Dell Inspiron 6400 with similar specs.  Here's how I got wireless working:
[Btw, you can check out all of my config issues here: [http://www.ubuntuforums.org/showthread.php?t=274915]](http://www.ubuntuforums.org/showthread.php?t=274915])
[B][U]
Broadcom 4311 Wireless:[/U][/B]

I was able to get the wireless card working, however, I needed to blacklist the existing bcm43xx module and use ndiswrapper:

1. Install **build-essential** from Synaptic (for compiling ndiswrapper)

2. Download latest stable version of **ndiswrapper** from [http://sourceforge.net/projects/ndiswrapper/](http://sourceforge.net/projects/ndiswrapper/)

3. Compile **ndiswrapper** according to [http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation)

4.  Blacklist the bcm43xx module:
```
echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
sudo rmmod bcm43xx
sudo rmmod ndiswrapper
sudo modprobe ndiswrapper
```5. In order to get 'iwlist scanning' to display results, I needed to edit my /etc/network/interfaces file to contain the appropriate settings for my AP:
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp
[COLOR=Red]wireless-essid MYSSID
wireless-key s:mysecretwepkey
[/COLOR]
auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
```I'm not sure why my wireless card is now using eth1 (it used to be wlan0 in Dapper), but hey, it's working! :)

```
dbott@edgy:~$ iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

sit0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:40:05:B2:AF:45
                    ESSID:"bott"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:92/100  Signal level:-37 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

```[COLOR=Red]Note: any kernel updates will require that ndiswrapper be recompiled[/COLOR]

**_February 24, 2007 - Wireless Update_**

Regarding the eth1 issue, I believe it was related to an entry in my iftab file that contained the following line:
```
eth1 mac 00:16:ce:31:88:XX arp 1 
```I changed the file to read:
```
dbott@edgy:~$ cat /etc/iftab
# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

eth0 mac 00:15:c5:0c:ad:XX arp 1
[COLOR=Red]wlan0[/COLOR] mac 00:16:ce:31:88:XX arp 1

```And then I installed **network-manager-gnome** and it seems to have cured all my problems.  The card is now recognized as **wlan0** and the network manager handles all the settings (WEP, scanning, etc.).

---

### Post by orengolan on 2007-03-17
I followed your instructions but decided to start from the end...
I Blacklist the bcm43xx module and changed my /etc/network/interfaces to look like yours and i couldn't see the wireless section in the 'networking' section under System->Administration. 

than I followed the steps you did and when i got to th point where i need to install the windows driver.  I couldn't find it on th wiki entry list so i boot to windows to find the driver (inf+sys files).
i did it because i know that i have wireless connection under windows.

I discovered that my windows use Broadcom Corporation Dell Wireless 1390 WLAN Mini-PCI.

I found the ini file and the sys file, moved them to Ubuntu, 
I created a folder on the desktop and put the files inside.
than i run this command ndiswrapper -i bcmwl5.inf
but i am not sure what happend:

```
yuka@yuka-laptop:~/Desktop/wirless_driver$ sudo ndiswrapper -i bcmwl5.inf
Password:
installing bcmwl5 ...
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
yuka@yuka-laptop:~/Desktop/wirless_driver$ iwlist
Usage: iwlist [interface] scanning
              [interface] frequency
              [interface] channel
              [interface] bitrate
              [interface] rate
              [interface] encryption
              [interface] key
              [interface] power
              [interface] txpower
              [interface] retry
              [interface] ap
              [interface] accesspoints
              [interface] peers
              [interface] event
yuka@yuka-laptop:~/Desktop/wirless_driver$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.


``` 

I am totally confused since it's my first linux experience...sorry if i messed up your
guidance.

---

### Post by Floppyjoe on 2007-03-17
> **orengolan said:**
> I followed your instructions but decided to start from the end...
I Blacklist the bcm43xx module and changed my /etc/network/interfaces to look like yours and i couldn't see the wireless section in the 'networking' section under System->Administration. 

than I followed the steps you did and when i got to th point where i need to install the windows driver.  I couldn't find it on th wiki entry list so i boot to windows to find the driver (inf+sys files).
i did it because i know that i have wireless connection under windows.

I discovered that my windows use Broadcom Corporation Dell Wireless 1390 WLAN Mini-PCI.

I found the ini file and the sys file, moved them to Ubuntu, 
I created a folder on the desktop and put the files inside.
than i run this command ndiswrapper -i bcmwl5.inf
but i am not sure what happend:

```
yuka@yuka-laptop:~/Desktop/wirless_driver$ sudo ndiswrapper -i bcmwl5.inf
Password:
installing bcmwl5 ...
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
yuka@yuka-laptop:~/Desktop/wirless_driver$ iwlist
Usage: iwlist [interface] scanning
              [interface] frequency
              [interface] channel
              [interface] bitrate
              [interface] rate
              [interface] encryption
              [interface] key
              [interface] power
              [interface] txpower
              [interface] retry
              [interface] ap
              [interface] accesspoints
              [interface] peers
              [interface] event
yuka@yuka-laptop:~/Desktop/wirless_driver$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.


``` 

I am totally confused since it's my first linux experience...sorry if i messed up your
guidance.

did you check if your driver is setup right?
```
ndiswrapper -l
```
if it says hardware present the you are ok.
then make sure you modprobe ndiswrapper
```
sudo modprobe ndiswrapper
```
then check network interfaces.
```
iwconfig
```
then scan.
```
sudo iwlist interface# scan
```
where interface# could be eth1 or wlan0 probably.

---

### Post by orengolan on 2007-03-17
how said Linux is not easy to use? 

Thanks guys, i am amazed. I have a laptop with Ubuntu.


on my todo list: 
1.install Ruby on rails
2.play with GNUcash to see if it can replace my quickbooks
3.find a way to use microsoft apps like sql enterprise manager and OneNote in Ubuntu.

is it risky to use Wine, and what apps can i use it with?
if wine will not help me what else can I do to use the above apps?
(virtual machine?)

thanks again!

---

### Post by orengolan on 2007-03-17
one issue - when i restart i don't have connection untill i run the **sudo modprobe ndiswrapper**.


any ideas?

---

### Post by Floppyjoe on 2007-03-17
Open up your /etc/modules file.
```
sudo gedit /etc/modules
```
Add the word ndiswrapper at the end and save this file.

Vmware server is a very nice program for using other operating systems to test things out in. There is a nice tutorial for this in the tutorial and howto's section of the forum.

---

### Post by orengolan on 2007-03-18
thanks.

---

### Post by orengolan on 2007-03-20
The wireless is working great in my house, but the laptop is not mine, so
my friend took it to her home, where she has Linksys WRT300N router (i have D-link).
the encryption is active.

the problem - I can't connect to the internet.
iwconfig shows Access Point: Not-Associated.
iwlist eth1 scan recognizes the network.
any ideas? 
 
yuka@yuka-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.


yuka@yuka-laptop:~$ sudo iwlist eth1 scan
eth1      Scan completed :
 
          Cell 02 - Address: 00:18:39:B9:CB:4E
                    ESSID:"Penara (N)"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.447 GHz (Channel 8)
                    Quality:57/100  Signal level:-59 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (1) : TKIP 
                        Authentication Suites (1) : PSK

---

### Post by dbott67 on 2007-03-20
There are a few different types of wireless security (WEP, WPA1, WPA2, etc.) and it appears as though your friend is using WPA.  You'll probably need to install the wpasupplicant package.

WPA can be a bit tricky to setup:
[http://ubuntuforums.org/showthread.php?t=202834&highlight=wpa](http://ubuntuforums.org/showthread.php?t=202834&highlight=wpa).
(you can also search the forums for WPA and get a number of different howtos)

I've never connected to a WPA-enabled network, so my help will be limited but I'm sure that there are others that will be able to help.

What version of Ubuntu are you running?

-Dave

---

### Post by orengolan on 2007-03-20
thanks, i'll check it out.
I am using 6.10. (hope to upgrade in a month to the new one)

I hope that it will be easy (automatcally) to move from WPA1 back to the encryption i have in my house (WEP?)

thanks!

---

### Post by orengolan on 2007-03-20
I think that the tutorial you refered me is too complicated..
I'll have to search for basic stuff. i want to try the IRC channels.

i also want to connect while the laptop is at the office.
here is my office network- 


yuka@yuka-laptop:~$ iwlist eth1 scan
eth1      Scan completed :
          Cell 01 - Address: 00:16:B6:F7:3C:29
                    ESSID:"CSS-OFFICE"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:100/100  Signal level:-29 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0


this is not WEP1, is it WAP?
how do I connect to this network?
why Windows can detect all 3 networks easily (my house, my friend's house and the office)?

---

### Post by dbott67 on 2007-03-20
Try installing network-manager-gnome:
```
sudo apt-get install network-manager-gnome
```

I installed it a few weeks ago and was over at my dad's house tonight setting up his new router.  It has WPA1 & WPA2 and I was able to connect to it using **network-manager-gnome.  **It was simple... point, click, add passkey and surf!

[http://www.gnome.org/projects/NetworkManager/](http://www.gnome.org/projects/NetworkManager/)

---

### Post by orengolan on 2007-03-21
I'll try it tomorrow at the office.

you are really helpful. thanks to you we will convert my friend to ubuntu, 

my friend need this laptop at her house (the WAP1 problem) and at the office.
She uses QuickBooks for the company's accounting so I installed GNUcash on her laptop and she will try to see if it has all the needed functions.
I also installed VMWare (with XP) so she can use QB if GNUcash will not meet her needs.

I really want to solve the wireless issue so she can start working with it.
It might cause  a chain reaction in the company,
the CEO/CTO understand the value of using Ubuntu,
and i showed him Evolution (i wonder if it can replace the outlook)
and some other cool stuff.

Thanks!

---

### Post by orengolan on 2007-03-21
it seems like I already have it. it's an icon that start rotate when i connect the DSL cable.
when i click on properties i see NetworkManager applet 0.6.3.

---

### Post by truthwork on 2007-07-16
hi there, im having quite a bit of trouble setting up wireless on my Dell Inspiron 640m with Broadcom 4311 card. Wondering if you can help me with this...I'm a total newbie:

When I run the Network Manager it doesn't show me that I have even a possiblity of configuring a Wireless Connection. :-( Not too sure how I could set up a new connection on this manager...

Also, when I run the "ndiswrapper -l" I get..."bcmwl5 : invalid driver!" message.

when i do "iwlist scanning", I get:
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.


I've got the latest version of ndiswrapper-1.47 on my desktop and I'm not totally sure how to install it.

Any tips? Thanks!

---

