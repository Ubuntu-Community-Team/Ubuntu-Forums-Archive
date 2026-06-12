---
title: "Actiontec Prism2.5 USB issues"
date: 2006-09-06
forum: Networking &amp; Wireless
---

### Post by NoIdentity on 2006-09-06
Hi,

I am having difficulty setting up my Actiontec Prism2.5 wireless card under Ubuntu.  I have read this  [thread]("http://www.ubuntuforums.org/showthread.php?t=209351&highlight=linux-wlan-ng+prism2.5"), which discusses similar issues but does not help me.  Maybe it does help but I am relatively new to linux and therefore the answer does not seem obvious to me.

I am running Ubuntu (Hoary, kernel 2.6.10) on a hp omnibook 510.  I have installed linux-wlan-ng using synaptic.  Below are the responeses I get to lsusb, lshw and lsmod:

```

root@BigWilly:/home/wilson # lsusb
Bus 003 Device 002: ID 1668:0408 Actiontec Electronics, Inc. [hex] Prism2.5 802.11b Adapter
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000

root@BigWilly:/home/wilson # lshw
bigwilly
    description: Computer
    product: HP OmniBook PC
    vendor: Hewlett-Packard
    version: HP OmniBook 510 FB
    serial: TW21706886
    capabilities: smbios-2.3 dmi-2.3
  *-core
       description: Motherboard
       product: HP OmniBook PC
       vendor: Hewlett-Packard
       physical id: 0
       version: 510FB
       serial: None
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies Ltd.
          physical id: 0
          version: FB.M1.20 (04/12/02  )
          size: 116KB
          capacity: 448KB
          capabilities: isa pci pcmcia pnp apm upgrade shadowing escd cdboot acpi usb agp smartbattery biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) III Mobile CPU      1133MHz
          vendor: Intel Corp.
          physical id: 4
          version: 6.11.1
          slot: U1
          size: 1133MHz
          capacity: 1133MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr sse
        *-cache:0
             description: L1 cache
             physical id: 8
             slot: L1 Cache
             size: 32KB
             capacity: 16KB
             capabilities: asynchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 9
             slot: L2 Cache
             size: 512KB
             capacity: 512KB
             capabilities: burst external write-back
     *-memory
          description: System Memory
          physical id: 16
          slot: System board or motherboard
          size: 256MB
          capacity: 512MB
        *-bank:0
             description: DIMM DRAM Synchronous
             physical id: 0
             slot: M1
        *-bank:1
             description: DIMM DRAM Synchronous
             physical id: 1
             slot: M2
             size: 256MB
             configuration: width=32
     *-pci
          physical id: 100
          bus info: pci@00:00.0
          version: 04
          clock: 33MHz
        *-display:0 UNCLAIMED
             physical id: 2
             bus info: pci@00:02.0
             version: 04
             size: 128MB
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: irq=10
        *-display:1 UNCLAIMED
             physical id: 2.1
             bus info: pci@00:02.1
             version: 00
             size: 128MB
             clock: 33MHz
             capabilities: cap_list
        *-usb:0
             physical id: 1d
             bus info: pci@00:1d.0
             version: 02
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd irq=10
        *-usb:1
             physical id: 1d.1
             bus info: pci@00:1d.1
             version: 02
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd irq=10
        *-usb:2
             physical id: 1d.2
             bus info: pci@00:1d.2
             version: 02
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd irq=5
        *-pci
             physical id: 1e
             bus info: pci@00:1e.0
             version: 42
             clock: 33MHz
             capabilities: pci bus_master
           *-multimedia
                physical id: 3
                bus info: pci@01:03.0
                version: 12
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=Maestro3 irq=5
           *-communication UNCLAIMED
                physical id: 4
                bus info: pci@01:04.0
                version: 01
                clock: 33MHz
                capabilities: cap_list
                configuration: irq=10
           *-pcmcia
                physical id: 5
                bus info: pci@01:05.0
                version: 01
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus irq=10
           *-network
                physical id: 8
                bus info: pci@01:08.0
                version: 42
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=e100 irq=10
           *-ide UNCLAIMED
                physical id: c
                bus info: pci@01:0c.0
                version: 02
                clock: 33MHz
                capabilities: cap_list
                configuration: irq=15
        *-isa UNCLAIMED
             physical id: 1f
             bus info: pci@00:1f.0
             version: 02
             clock: 33MHz
             capabilities: isa bus_master
        *-ide
             physical id: 1f.1
             bus info: pci@00:1f.1
             version: 02
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=PIIX_IDE irq=5
        *-serial
             physical id: 1f.3
             bus info: pci@00:1f.3
             version: 02
             clock: 33MHz
             configuration: driver=i801_smbus irq=10
  *-network:0 DISABLED
       description: Ethernet controller
       physical id: 1
       logical name: wlan0
       capabilities: ethernet
       configuration: broadcast=yes driver=p80211_prism2_usb driverversion=0.2.1-pre25 multicast=yes
  *-network:1
       description: Ethernet controller
       physical id: 2
       logical name: eth0
       serial: 00:c0:9f:09:d8:bb
       capabilities: mii autonegotiation 100bt-fd 100bt 10bt-fd 10bt ethernet
       configuration: autonegociated=100bt broadcast=yes driver=e100 driverversion=3.2.3-k2-NAPI duplex=full firmware=N/A ip=10.220.3.24 link=yes multicast=yes
  *-network:2 DISABLED
       description: controller
       physical id: 3
       logical name: sit0


root@BigWilly:/home/wilson # lsmod --help
Usage: lsmod
root@BigWilly:/home/wilson # lsmod
Module                  Size  Used by
acpi_cpufreq            5892  1
speedstep_lib           4228  0
proc_intf               4100  0
freq_table              4100  1 acpi_cpufreq
cpufreq_userspace       4572  1
cpufreq_ondemand        6172  0
cpufreq_powersave       1920  0
pcmcia                 21380  2
i915                   18304  1
drm                    59412  2 i915
video                  16260  0
sony_acpi               6280  0
pcc_acpi               11264  0
button                  6800  0
battery                10244  0
container               4608  0
ac                      4996  0
ipv6                  229504  9
af_packet              20744  4
e100                   32384  0
mii                     4736  1 e100
yenta_socket           19584  0
pcmcia_core            53568  2 pcmcia,yenta_socket
snd_maestro3           21796  2
snd_ac97_codec         64608  1 snd_maestro3
snd_pcm_oss            47652  1
snd_mixer_oss          16768  2 snd_pcm_oss
snd_pcm                84872  3 snd_maestro3,snd_ac97_codec,snd_pcm_oss
snd_timer              23300  1 snd_pcm
snd_page_alloc          9604  1 snd_pcm
snd                    50276  6 snd_maestro3,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9824  3 snd
i2c_i801                8076  0
i2c_core               21264  1 i2c_i801
hw_random               5524  0
prism2_usb             70532  0
p80211                 30608  1 prism2_usb
shpchp                 86116  0
pci_hotplug            30512  1 shpchp
uhci_hcd               30224  0
usbcore               107512  3 prism2_usb,uhci_hcd
intel_agp              20636  1
agpgart                31784  3 drm,intel_agp
floppy                 54864  0
pcspkr                  3816  0
rtc                    12216  0
evdev                   9088  0
md                     43856  0
tsdev                   7488  0
dm_mod                 53116  1
capability              5000  0
commoncap               7808  1 capability
psmouse                19336  0
mousedev               11160  1
parport_pc             34372  1
lp                     10792  0
parport                33480  2 parport_pc,lp
ide_cd                 38532  0
cdrom                  36508  1 ide_cd
ext3                  120968  1
jbd                    54168  1 ext3
ide_generic             1664  0
piix                    9988  1
ide_disk               18176  3
ide_core              118988  4 ide_cd,ide_generic,piix,ide_disk
unix                   26164  806
thermal                13576  0
processor              22708  2 acpi_cpufreq,thermal
fan                     4612  0
fbcon                  34048  0
font                    8448  1 fbcon
bitblit                 5120  1 fbcon
vesafb                  6948  0
cfbcopyarea             3968  1 vesafb
cfbimgblt               3072  1 vesafb
cfbfillrect             3584  1 vesafb

```

The prism2_usb driver seems to be loaded and associated with p80211.  I thought everything was fine but when I did an iwconfig and iwlist scan I got the following:

```

root@BigWilly:/home/wilson # iwconfig
lo        no wireless extensions.

wlan0     no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

root@BigWilly:/home/wilson # iwlist scan
lo        Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Function not implemented

eth0      Interface doesn't support scanning.

sit0      Interface doesn't support scanning.


```

I also tried using the wlanctl-ng command suggested in the aforementioned thread and got the following:

```

root@BigWilly:/home/wilson # wlanctl-ng wlan0 lnxreq_ifstate ifstate=enable
message=lnxreq_ifstate
  ifstate=enable
  resultcode=implementation_failure

```

Can someone tell me if the driver is working and if so what I have to do to get the wireless up and running?

Thanks in advance.

---

### Post by NoIdentity on 2006-09-08
Update:

I got the Actiontec Prism2.5 USB Wireless card working on the HP Omnibook 510 using ndiswrapper.  The Windows driver is called aeiwlnic.inf (I also copied over aeiwlnic.sys for good measure). I unloaded the prism2_usb module using modprobe.  I edited /etc/modules.conf not to use prism2_usb with wlan0.  I edited /etc/modules to include ndiswrapper.  I then restarted the laptop and hey presto.  Under System->Administration->Networking (Gnome) I configured the wireless to connect to my network.

It works flawlessly.

Hope this helps those in a similar circumstance.

---

