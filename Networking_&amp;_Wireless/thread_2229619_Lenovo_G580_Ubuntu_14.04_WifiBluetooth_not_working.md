---
title: "Lenovo G580 Ubuntu 14.04 Wifi/Bluetooth not working."
date: 2014-06-14
forum: Networking &amp; Wireless
---

### Post by ManthanRB on 2014-06-14
I just made a dualboot of Ubuntu 14.04 with windows 7, coming straight to the topic.

The wifi & Bluetooth are not working

Wifi:-

After a fresh installation the wifi just didn't worked, i can see my SSID & can connect to it but unable to access the internet
as for a workaround i removed the driver by the following command

```
sudo apt-get remove bcmwl-kernel-source
```

Now the wifi is connected & working but in proprietory drivers its says "This device in not working" obvious as i removed the drivers
i can use the Broadcom STA drivers but it again comes to same "Connected but no internet access"
Please give some solution on how to use the proper driver 

Bluetooth :-

I don't know anything about it as it just says "No bluetooth Device found" in system settings

```
manthanrb@Mario:~$ sudo lshw 
[sudo] password for manthanrb: 
mario                     
    description: Notebook
    product: 20157 (System SKUNumber)
    vendor: LENOVO
    version: Lenovo G580
    serial: WB07906647WB02082114
    width: 64 bits
    capabilities: smbios-2.7 dmi-2.7 vsyscall32
    configuration: administrator_password=unknown boot=normal chassis=notebook family=ChiefRiver System frontpanel_password=unknown keyboard_password=unknown power-on_password=unknown sku=System SKUNumber uuid=F88382A0-ECBD-11E1-91FF-A671DD23F968
  *-core
       description: Motherboard
       product: Emerald Lake 2
       vendor: LENOVO
       physical id: 0
       version: FAB1
       serial: WB07906647
       slot: Part Component
     *-firmware
          description: BIOS
          vendor: LENOVO
          physical id: 0
          version: 62CN37WW
          date: 06/13/2012
          size: 128KiB
          capacity: 4032KiB
          capabilities: pci upgrade shadowing cdboot bootselect edd int5printscreen int9keyboard int14serial int17printer int10video pc98 acpi usb biosbootspecification netboot uefi
     *-cpu
          description: CPU
          product: Intel(R) Core(TM) i5-3210M CPU @ 2.50GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: Intel(R) Core(TM) i5-3210M CPU @ 2.50GHz
          serial: To Be Filled By O.E.M.
          slot: CPU Socket - U3E1
          size: 1200MHz
          capacity: 1200MHz
          width: 64 bits
          clock: 100MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf eagerfpu pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm ida arat epb xsaveopt pln pts dtherm tpr_shadow vnmi flexpriority ept vpid fsgsbase smep erms cpufreq
          configuration: cores=2 enabledcores=2 threads=4
     *-cache:0
          description: L1 cache
          physical id: 5
          slot: L1-Cache
          size: 32KiB
          capacity: 32KiB
          capabilities: internal write-through data
     *-cache:1
          description: L1 cache
          physical id: 6
          slot: L1-Cache
          size: 32KiB
          capacity: 32KiB
          capabilities: internal write-through instruction
     *-cache:2
          description: L2 cache
          physical id: 7
          slot: L2-Cache
          size: 256KiB
          capacity: 256KiB
          capabilities: internal write-through unified
     *-cache:3
          description: L3 cache
          physical id: 8
          slot: L3-Cache
          size: 3MiB
          capacity: 3MiB
          capabilities: internal write-back unified
     *-memory
          description: System Memory
          physical id: 34
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: DIMM [empty]
             physical id: 0
             slot: ChannelA-DIMM0
        *-bank:1
             description: DIMM [empty]
             physical id: 1
             slot: ChannelA-DIMM1
        *-bank:2
             description: SODIMM DDR3 Synchronous 1600 MHz (0.6 ns)
             product: M471B5273DH0-CK0
             vendor: Samsung
             physical id: 2
             serial: B3205DEE
             slot: ChannelB-DIMM0
             size: 4GiB
             width: 64 bits
             clock: 1600MHz (0.6ns)
        *-bank:3
             description: DIMM [empty]
             physical id: 3
             slot: ChannelB-DIMM1
     *-pci
          description: Host bridge
          product: 3rd Gen Core processor DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 09
          width: 32 bits
          clock: 33MHz
        *-display
             description: VGA compatible controller
             product: 3rd Gen Core processor Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 09
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:42 memory:f0000000-f03fffff memory:e0000000-efffffff ioport:3000(size=64)
        *-usb:0
             description: USB controller
             product: 7 Series/C210 Series Chipset Family USB xHCI Host Controller
             vendor: Intel Corporation
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi xhci bus_master cap_list
             configuration: driver=xhci_hcd latency=0
             resources: irq:40 memory:f0600000-f060ffff
        *-communication
             description: Communication controller
             product: 7 Series/C210 Series Chipset Family MEI Controller #1
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=mei_me latency=0
             resources: irq:43 memory:f0615000-f061500f
        *-usb:1
             description: USB controller
             product: 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:16 memory:f0619000-f06193ff
        *-multimedia
             description: Audio device
             product: 7 Series/C210 Series Chipset Family High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:44 memory:f0610000-f0613fff
        *-pci:0
             description: PCI bridge
             product: 7 Series/C210 Series Chipset Family PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: c4
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16
        *-pci:1
             description: PCI bridge
             product: 7 Series/C210 Series Chipset Family PCI Express Root Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: c4
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:17 memory:f0500000-f05fffff
           *-network
                description: Network controller
                product: BCM4313 802.11bgn Wireless Network Adapter
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                version: 01
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=bcma-pci-bridge latency=0
                resources: irq:17 memory:f0500000-f0503fff
        *-pci:2
             description: PCI bridge
             product: 7 Series/C210 Series Chipset Family PCI Express Root Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: c4
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:19 ioport:2000(size=4096) memory:f0400000-f04fffff
           *-network
                description: Ethernet interface
                product: AR8162 Fast Ethernet
                vendor: Qualcomm Atheros
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: eth0
                version: 10
                serial: 3c:97:0e:17:42:65
                capacity: 100Mbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi msix bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=alx latency=0 link=no multicast=yes port=twisted pair
                resources: irq:45 memory:f0400000-f043ffff ioport:2000(size=128)
        *-usb:2
             description: USB controller
             product: 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:23 memory:f0618000-f06183ff
        *-isa
             description: ISA bridge
             product: HM76 Express Chipset LPC Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-storage
             description: SATA controller
             product: 7 Series Chipset Family 6-port SATA Controller [AHCI mode]
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 04
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:41 ioport:3088(size=8) ioport:3094(size=4) ioport:3080(size=8) ioport:3090(size=4) ioport:3060(size=32) memory:f0617000-f06177ff
        *-serial UNCLAIMED
             description: SMBus
             product: 7 Series/C210 Series Chipset Family SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 04
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:f0614000-f06140ff ioport:efa0(size=32)
     *-scsi:0
          physical id: 1
          logical name: scsi1
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: ST9500325AS
             vendor: Seagate
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/sda
             version: 0011
             serial: S2WNAFL9
             size: 465GiB (500GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=512 signature=d9556627
           *-volume:0
                description: Extended partition
                physical id: 1
                bus info: scsi@1:0.0.0,1
                logical name: /dev/sda1
                size: 19GiB
                capacity: 19GiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume:0
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 977MiB
                   capabilities: nofs
              *-logicalvolume:1
                   description: Linux filesystem partition
                   physical id: 6
                   logical name: /dev/sda6
                   logical name: /
                   capacity: 19GiB
                   configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered state=mounted
           *-volume:1
                description: Windows NTFS volume
                physical id: 2
                bus info: scsi@1:0.0.0,2
                logical name: /dev/sda2
                version: 3.1
                serial: 361a1dc3-456b-1f42-af65-f8eb9fe2b315
                size: 79GiB
                capacity: 79GiB
                capabilities: primary bootable ntfs initialized
                configuration: clustersize=4096 created=2014-06-14 02:11:00 filesystem=ntfs modified_by_chkdsk=true mounted_on_nt4=true resize_log_file=true state=dirty upgrade_on_mount=true
           *-volume:2
                description: Windows NTFS volume
                physical id: 3
                bus info: scsi@1:0.0.0,3
                logical name: /dev/sda3
                version: 3.1
                serial: ee74bc68-cc39-2544-8163-7215265def38
                size: 183GiB
                capacity: 183GiB
                capabilities: primary ntfs initialized
                configuration: clustersize=4096 created=2012-11-14 09:57:23 filesystem=ntfs label=Windows Storage state=clean
           *-volume:3
                description: Windows NTFS volume
                physical id: 4
                bus info: scsi@1:0.0.0,4
                logical name: /dev/sda4
                version: 3.1
                serial: fe0f84c0-e425-8d44-adde-d6991bcd4ed9
                size: 183GiB
                capacity: 183GiB
                capabilities: primary ntfs initialized
                configuration: clustersize=4096 created=2010-05-04 08:54:57 filesystem=ntfs label=Games state=clean
     *-scsi:1
          physical id: 2
          logical name: scsi4
          capabilities: emulated
        *-cdrom
             description: DVD-RAM writer
             product: CDDVDW SN-208AB
             vendor: TSSTcorp
             physical id: 0.0.0
             bus info: scsi@4:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/sr0
             version: LA03
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
     *-scsi:2
          physical id: 3
          bus info: usb@2:1.6
          logical name: scsi6
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             product: Card  Reader
             vendor: Multiple
             physical id: 0.0.0
             bus info: scsi@6:0.0.0
             logical name: /dev/sdb
             version: 1.00
             capabilities: removable
             configuration: sectorsize=512
           *-medium
                physical id: 0
                logical name: /dev/sdb
  *-battery
       product: Smart Battery
       vendor: Intel Corp.
       physical id: 1
       version: 2008
       serial: 1.0
       slot: Rear
  *-power UNCLAIMED
       description: TBD by ODM
       product: TBD by ODM
       vendor: TBD by ODM
       physical id: 2
       version: 1.0
       serial: TBD by ODM
       capacity: 32768mWh
  *-network
       description: Wireless interface
       physical id: 3
       logical name: wlan0
       serial: 84:4b:f5:b7:3a:dd
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=brcmsmac driverversion=3.13.0-24-generic firmware=610.812 ip=192.168.1.2 link=yes multicast=yes wireless=IEEE 802.11bgn


```

I was searching for this issues from 2 days its a common problem with Broadcom 43xx chips but no solution..
Thanks

---

### Post by varunendra on 2014-06-15
Welcome to the forums ManthanRB!

Please follow the instructions in this post to download and run 'wireless_script' (experimental version) and post back the report it generates : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

---

### Post by ManthanRB on 2014-06-18
> **varunendra said:**
> Welcome to the forums ManthanRB!

Please follow the instructions in this post to download and run 'wireless_script' (experimental version) and post back the report it generates : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

```

    ======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

Mario 3.13.0-24-generic x86_64,  Ubuntu 14.04 LTS, trusty

CPU    : Intel(R) Core(TM) i5-3210M CPU @ 2.50GHz
Memory : 3800 MB
Uptime : 00:39:46 up 4 min,  2 users,  load average: 0.33, 0.35, 0.17


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

02:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)
    Subsystem: Broadcom Corporation Device [14e4:051b]
    Kernel driver in use: bcma-pci-bridge
03:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8162 Fast Ethernet [1969:1090] (rev 10)
    Subsystem: Lenovo Device [17aa:3978]
    Kernel driver in use: alx


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 002 Device 003: ID 058f:6366 Alcor Micro Corp. Multi Flash Reader
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 5986:0294 Acer, Inc 
Bus 001 Device 003: ID 0461:4d0f Primax Electronics, Ltd HP Optical Mouse
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~



iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     IEEE 802.11bgn  ESSID:"Mario"  
          Mode:Managed  Frequency:2.447 GHz  Access Point: <MAC C-01 Mario>   
          Bit Rate=65 Mb/s   Tx-Power=19 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-34 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:57   Missed beacon:0



rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

      Interface        Soft blocked  Hard blocked
2: phy0: Wireless LAN      no            no


lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

brcmsmac              563041  0 
cordic                 12574  1 brcmsmac
brcmutil               15618  1 brcmsmac
b43                   387371  0 
mac80211              626489  2 b43,brcmsmac
cfg80211              484040  3 b43,brcmsmac,mac80211
ssb                    62379  1 b43
bcma                   52096  3 b43,brcmsmac
wmi                    19177  0 


module parameters ~~~~~~~~~~~~~~~~~~

b43          (10): allhwsupport=0 | bad_frames_preempt=0 | btcoex=1 | hwpctl=0 | hwtkip=0 | nohwcrypt=0 | pio=0 | qos=1 | verbose=2
cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500
wmi           (2): debug_dump_wdg=N | debug_event=N


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: unknown
================o======o========o==============o=========o===========o==============o===========
 Interface & ID | Type | Driver | State        | Default | Speed     | Support      | HW Addr   
================o======o========o==============o=========o===========o==============o===========
                |      |        |              |         |           |              |           
----------------+------+--------+--------------+---------+-----------+--------------+-----------


NetworkManager.state ~~~~~~~~~~~~~~~
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


NetworkManager.conf ~~~~~~~~~~~~~~~~

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false


NM WiFi Profiles ~~~~~~~~~~~~~~~~~~~

Mario                : ssid=Mario | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 


interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~

nameserver 127.0.1.1


Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

--- 192.168.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 2.493/28.648/54.803/26.155 ms

--- 127.0.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.032/0.034/0.037/0.006 ms


iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~

(Region : "en_IN")
country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     13 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 13 (2.472 GHz)

          Current Frequency:2.447 GHz (Channel 8)


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     Scan completed :
          Cell 01 - Address: <MAC C-01 Mario>
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=70/70  Signal level=-36 dBm  
                    Encryption key:on
                    ESSID:"Mario"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000bc4092f19
                    Extra: Last beacon: 88ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK


blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[brcmsmac]
filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/brcm80211/brcmsmac/brcmsmac.ko
firmware:       brcm/bcm43xx_hdr-0.fw
firmware:       brcm/bcm43xx-0.fw
srcversion:     43D6897F7EB716081DF69BE
depends:        bcma,mac80211,brcmutil,cfg80211,cordic

[cordic]
filename:       /lib/modules/3.13.0-24-generic/kernel/lib/cordic.ko
srcversion:     810E6E73D80DD7F75AC5B42
depends:        

[brcmutil]
filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/brcm80211/brcmutil/brcmutil.ko
srcversion:     E81EE4CBB6A7A689150D93D
depends:        

[b43]
filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/b43/b43.ko
firmware:       b43/ucode9.fw
firmware:       b43/ucode5.fw
firmware:       b43/ucode16_mimo.fw
firmware:       b43/ucode15.fw
firmware:       b43/ucode14.fw
firmware:       b43/ucode13.fw
firmware:       b43/ucode11.fw
srcversion:     BED87D210887FFC71A4BDE0
depends:        bcma,ssb,mac80211,cfg80211
parm:           bad_frames_preempt:enable(1) / disable(0) Bad Frames Preemption (int)
parm:           fwpostfix:Postfix for the .fw files to load. (string)
parm:           hwpctl:Enable hardware-side power control (default off) (int)
parm:           nohwcrypt:Disable hardware encryption. (int)
parm:           hwtkip:Enable hardware tkip. (int)
parm:           qos:Enable QOS support (default on) (int)
parm:           btcoex:Enable Bluetooth coexistence (default on) (int)
parm:           verbose:Log message verbosity: 0=error, 1=warn, 2=info(default), 3=debug (int)
parm:           pio:Use PIO accesses by default: 0=DMA, 1=PIO (int)
parm:           allhwsupport:Enable support for all hardware (even it if overlaps with the brcmsmac driver) (int)

[mac80211]
filename:       /lib/modules/3.13.0-24-generic/kernel/net/mac80211/mac80211.ko
srcversion:     C0F95BBF832E05DEFD722F4
depends:        cfg80211
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.13.0-24-generic/kernel/net/wireless/cfg80211.ko
srcversion:     8B3D642D1F2E6406EF33F74
depends:        
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

[ssb]
filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/ssb/ssb.ko
srcversion:     3DE188310F77C566C2E8CB3
depends:        

[bcma]
filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/bcma/bcma.ko
srcversion:     E41B811D88783DD5BC38565
depends:        


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~

# PCI device 0x1969:0x1090 (alx)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x14e4:0x4727 (brcmsmac)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


Custom files/entries ~~~~~~~~~~~~~~~

/etc/modules        : Default
/etc/rc.local       : Default
/etc/modprobe.d     : Not Default
/etc/pm/(cnf|pw|sl) : Default

[/etc/modprobe.d]
iwlwifi.conf      : remove iwlwifi \
                    (/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
                    && /sbin/modprobe -r mac80211
mlx4.conf         : softdep mlx4_core post: mlx4_en


Kernel boot line ~~~~~~~~~~~~~~~~~~~

BOOT_IMAGE=/boot/vmlinuz-3.13.0-24-generic root=UUID=27d00d8d-1b1c-4505-99fa-30560b7a5dab ro quiet splash acpi_backlight=vendor vt.handoff=7


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    0.453200] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.453477] audit: initializing netlink socket (disabled)
[    0.724394] alx 0000:03:00.0 eth0: Qualcomm Atheros AR816x/AR817x Ethernet [<MAC eth0>]
[   10.796941] wmi: Mapper loaded
[   10.955734] bcma: bus0: Found chip with id 0x4313, rev 0x01 and package 0x08
[   10.955769] bcma: bus0: Core 0 found: ChipCommon (manuf 0x4BF, id 0x800, rev 0x24, class 0x0)
[   10.955798] bcma: bus0: Core 1 found: IEEE 802.11 (manuf 0x4BF, id 0x812, rev 0x18, class 0x0)
[   10.955854] bcma: bus0: Core 2 found: PCIe (manuf 0x4BF, id 0x820, rev 0x11, class 0x0)
[   10.968752] bcma: bus0: Bus registered
[   11.416063] Support for cores revisions 0x17 and 0x18 disabled by module param allhwsupport=0. Try b43.allhwsupport=1
[   11.416066] b43: probe of bcma0:0 failed with error -524
[   11.669808] psmouse serio1: elantech: assuming hardware version 3 (with firmware version 0x450f03)
[   11.745841] brcmsmac bcma0:0: mfg 4bf core 812 rev 24 class 0 irq 17
[   11.772522] ieee80211 phy0: registered radio enabled led device: brcmsmac-phy0:radio gpio: 243
[   12.909391] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   14.284624] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[   14.284662] brcmsmac bcma0:0: brcms_ops_config: change power-save mode: false (implement)
[   14.285306] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   14.285586] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   15.151614] wlan0: authenticate with <MAC C-01 Mario>
[   15.155269] wlan0: send auth to <MAC C-01 Mario> (try 1/3)
[   15.158175] wlan0: authenticated
[   15.158670] wlan0: associate with <MAC C-01 Mario> (try 1/3)
[   15.162729] wlan0: RX AssocResp from <MAC C-01 Mario> (capab=0x431 status=0 aid=2)
[   15.165221] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[   15.165225] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[   15.165235] wlan0: associated
[   15.165242] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   20.148703] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: 1 addresses (implement)

    ======== Done ========

```

---

### Post by varunendra on 2014-06-19
Please open a terminal (Ctrl-Alt-T) and run the following command to blacklist the "b43" and "ssb" drivers so that they don't conflict with the correct driver "brcmsmac" -
```
echo -e "blacklist b43\nblacklist ssb" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
Then reboot and check if the problem is solved. If not, please post a fresh report of the wireless_script.

---

### Post by ManthanRB on 2014-06-19
> **varunendra said:**
> Please open a terminal (Ctrl-Alt-T) and run the following command to blacklist the "b43" and "ssb" drivers so that they don't conflict with the correct driver "brcmsmac" -
```
echo -e "blacklist b43\nblacklist ssb" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
Then reboot and check if the problem is solved. If not, please post a fresh report of the wireless_script.

My wifi is working but its using the brcmsmac drivers and not the Broadcom Drivers, i am asking why am i having the problem while using the Broadcom drivers?

---

### Post by varunendra on 2014-06-20
> **ManthanRB said:**
> My wifi is working but its using the **brcmsmac drivers and [COLOR="#FF0000"]not the Broadcom[/COLOR] Drivers**, i am asking why am i having the problem while using the Broadcom drivers?
..and my post tells you why you are having the problem -
> **varunendra said:**
> ..run the following command to blacklist the "b43" and "ssb" drivers **so that they don't conflict with the [COLOR="#0000CD"]correct[/COLOR] driver "brcmsmac"**..
"brcmsmac" is also a Broadcom driver, the three others are - b43, wl and brcm**f**mac. The card you have can be controlled by two of these - the "wl" (also called "STA" driver) and the "brcmsmac" drivers. The sta driver (wl) is proprietary and usually doesn't work as good as brcmsmac with this card. The "b43" does not work with this card as far as I know and have seen. It gets loaded because, I guess (can't be sure), both brcmsmac and b43 _now_ depend on a supporting driver - 'bcma' (the 'brcmsmac' didn't depend on it in earlier kernel versions), which contains the device ID of this card. This maybe a bug that needs to be fixed, so that this conflict of drivers with this particular card can be prevented.

So.. trust me, I know what I am doing here, and somehow I know the story with these broadcom cards/drivers very well. I just don't have much time these days to properly and deliberately explain things like I loved to do a few months ago. I am not a developer myself so can't guarantee that my suggestions would definitely work, but sometimes experience counts a lot. :)

Just try what I suggested and post back the outcome. Be assured, reverting a blacklist is a matter of seconds, if required at all.

---

### Post by ManthanRB on 2014-06-20
> **varunendra said:**
> ..and my post tells you why you are having the problem -

"brcmsmac" is also a Broadcom driver, the three others are - b43, wl and brcm**f**mac. The card you have can be controlled by two of these - the "wl" (also called "STA" driver) and the "brcmsmac" drivers. The sta driver (wl) is proprietary and usually doesn't work as good as brcmsmac with this card. The "b43" does not work with this card as far as I know and have seen. It gets loaded because, I guess (can't be sure), both brcmsmac and b43 _now_ depend on a supporting driver - 'bcma' (the 'brcmsmac' didn't depend on it in earlier kernel versions), which contains the device ID of this card. This maybe a bug that needs to be fixed, so that this conflict of drivers with this particular card can be prevented.

So.. trust me, I know what I am doing here, and somehow I know the story with these broadcom cards/drivers very well. I just don't have much time these days to properly and deliberately explain things like I loved to do a few months ago. I am not a developer myself so can't guarantee that my suggestions would definitely work, but sometimes experience counts a lot. :)

Just try what I suggested and post back the outcome. Be assured, reverting a blacklist is a matter of seconds, if required at all.

Thanks, it worked!
I asked because i didn't knew that brcmsmac is also a broadcom driver.
thanks again for clearing my doubt.:KS

i can't find anything to mark the best answer/reward you or anythin!

---

### Post by genius2 on 2015-03-07
Hi Varun,
                I am facing the same problem as is mnentioned in the post for my laptop (Lenovo G580). I tried to follow the solution and have generated the output of wireless_script, I am posting the same under :
======== Wireless-Info START ========


System-Info ~~~~~~~~~~~~~~~~~~~~~~~~


genius-Lenovo-G580 3.13.0-46-generic x86_64,  Ubuntu 14.04.2 LTS, trusty


CPU    : Intel(R) Core(TM) i5-3210M CPU @ 2.50GHz
Memory : 3800 MB
Uptime : 15:34:25 up 6 min,  2 users,  load average: 0.28, 0.61, 0.35




lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


02:00.0 Network controller [0280]: Qualcomm Atheros AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
	Subsystem: Lenovo Device [17aa:30a1]
	Kernel driver in use: ath9k
03:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8162 Fast Ethernet [1969:1090] (rev 10)
	Subsystem: Lenovo Device [17aa:3978]
	Kernel driver in use: alx




lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


Bus 002 Device 004: ID 058f:6366 Alcor Micro Corp. Multi Flash Reader
Bus 002 Device 003: ID 0489:e042 Foxconn / Hon Hai 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0c45:6455 Microdia 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 004: ID 12d1:140b Huawei Technologies Co., Ltd. EC1260 Wireless Data Modem HSD USB Card
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub




PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~






iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~


wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          




rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


      Interface        Soft blocked  Hard blocked
0: phy0: Wireless LAN      no            yes
1: hci0: Bluetooth         yes           no




lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


ath9k                 164164  0 
ath9k_common           13551  1 ath9k
ath9k_hw              453856  2 ath9k_common,ath9k
ath                    28698  3 ath9k_common,ath9k,ath9k_hw
mac80211              630669  1 ath9k
cfg80211              484040  3 ath,ath9k,mac80211
wmi                    19177  0 




module parameters ~~~~~~~~~~~~~~~~~~


ath9k         (5): blink=0 | bt_ant_diversity=0 | btcoex_enable=0 | nohwcrypt=0 | ps_enable=0
cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500
wmi           (2): debug_dump_wdg=N | debug_event=N




nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~


State: connected (global)
================================================o=========================o=========o=============o=========o===========o==============o===========
 Interface & ID                                 | Type                    | Driver  | State       | Default | Speed     | Support      | HW Addr   
================================================o=========================o=========o=============o=========o===========o==============o===========
 ttyUSB2  [Tata Indicom (Photon+) connection 1] | Mobile Broadband (CDMA) | option1 | connected   | yes     |           |              |           


    Address:         14.98.77.67
    Prefix:          32 (255.255.255.255)
    Gateway:         172.29.145.129
    DNS:             103.8.44.5
    DNS:             103.8.45.5
------------------------------------------------+-------------------------+---------+-------------+---------+-----------+--------------+-----------
 eth0                                           | Wired                   | alx     | unavailable | no      |           |              | <MAC eth0>
------------------------------------------------+-------------------------+---------+-------------+---------+-----------+--------------+-----------
 wlan0                                          | 802.11 WiFi             | ath9k   | unavailable | no      |           | WEP/WPA/WPA2 | <MAC wlan0>
------------------------------------------------+-------------------------+---------+-------------+---------+-----------+--------------+-----------




NetworkManager.state ~~~~~~~~~~~~~~~
[main]
NetworkingEnabled=true
WirelessEnabled=false
WWANEnabled=true
WimaxEnabled=true


Could you please suggest me something.

---

### Post by genius2 on 2015-03-07
Sorry here is the complete output

    ======== Wireless-Info START ========


System-Info ~~~~~~~~~~~~~~~~~~~~~~~~


genius-Lenovo-G580 3.13.0-46-generic x86_64,  Ubuntu 14.04.2 LTS, trusty


CPU    : Intel(R) Core(TM) i5-3210M CPU @ 2.50GHz
Memory : 3800 MB
Uptime : 15:34:25 up 6 min,  2 users,  load average: 0.28, 0.61, 0.35




lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


02:00.0 Network controller [0280]: Qualcomm Atheros AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
    Subsystem: Lenovo Device [17aa:30a1]
    Kernel driver in use: ath9k
03:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8162 Fast Ethernet [1969:1090] (rev 10)
    Subsystem: Lenovo Device [17aa:3978]
    Kernel driver in use: alx




lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


Bus 002 Device 004: ID 058f:6366 Alcor Micro Corp. Multi Flash Reader
Bus 002 Device 003: ID 0489:e042 Foxconn / Hon Hai 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0c45:6455 Microdia 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 004: ID 12d1:140b Huawei Technologies Co., Ltd. EC1260 Wireless Data Modem HSD USB Card
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub




PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~






iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~


wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thrff
          Power Managementff
          




rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


      Interface        Soft blocked  Hard blocked
0: phy0: Wireless LAN      no            yes
1: hci0: Bluetooth         yes           no




lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


ath9k                 164164  0 
ath9k_common           13551  1 ath9k
ath9k_hw              453856  2 ath9k_common,ath9k
ath                    28698  3 ath9k_common,ath9k,ath9k_hw
mac80211              630669  1 ath9k
cfg80211              484040  3 ath,ath9k,mac80211
wmi                    19177  0 




module parameters ~~~~~~~~~~~~~~~~~~


ath9k         (5): blink=0 | bt_ant_diversity=0 | btcoex_enable=0 | nohwcrypt=0 | ps_enable=0
cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500
wmi           (2): debug_dump_wdg=N | debug_event=N




nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~


State: connected (global)
================================================o=========================o=========o=============o=========o===========o==============o===========
 Interface & ID                                 | Type                    | Driver  | State       | Default | Speed     | Support      | HW Addr   
================================================o=========================o=========o=============o=========o===========o==============o===========
 ttyUSB2  [Tata Indicom (Photon+) connection 1] | Mobile Broadband (CDMA) | option1 | connected   | yes     |           |              |           


    Address:         14.98.77.67
    Prefix:          32 (255.255.255.255)
    Gateway:         172.29.145.129
    DNS:             103.8.44.5
    DNS:             103.8.45.5
------------------------------------------------+-------------------------+---------+-------------+---------+-----------+--------------+-----------
 eth0                                           | Wired                   | alx     | unavailable | no      |           |              | <MAC eth0>
------------------------------------------------+-------------------------+---------+-------------+---------+-----------+--------------+-----------
 wlan0                                          | 802.11 WiFi             | ath9k   | unavailable | no      |           | WEP/WPA/WPA2 | <MAC wlan0>
------------------------------------------------+-------------------------+---------+-------------+---------+-----------+--------------+-----------




NetworkManager.state ~~~~~~~~~~~~~~~
[main]
NetworkingEnabled=true
WirelessEnabled=false
WWANEnabled=true
WimaxEnabled=true




NetworkManager.conf ~~~~~~~~~~~~~~~~


[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq


no-auto-default=<MAC eth0>,


[ifupdown]
managed=false




NM WiFi Profiles ~~~~~~~~~~~~~~~~~~~


cmswire              : ssid=cmswire | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
davis                : ssid=davis | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
ehepd210             : ssid=ehepd210 | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
guesthouse           : ssid=guesthouse | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
Guest Network        : ssid=Guest Network | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
IITG_GUEST           : ssid=IITG_GUEST | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
internet             : ssid=internet | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
internet 1           : ssid=internet | autoconnect=false | mac-address=<MAC wlan0> | ipv4=shared | ipv6=auto 
kirti mobile         : ssid=kirti mobile | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
Panasonic P81        : ssid=Panasonic P81 | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
PU@CAMPUS            : ssid=PU@CAMPUS | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
RAMANUJAN            : ssid=RAMANUJAN | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
scorp                : ssid=scorp | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
Tata-Photon-Max-Wi-Fi-2812 : ssid=Tata-Photon-Max-Wi-Fi-2812 | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
TP-LINK_ED8319       : ssid=TP-LINK_ED8319 | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
Tuta                 : ssid=Tuta | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
Wi-Fi connection 1   : ssid=inter | ipv6=auto | ipv4=auto 




interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~


# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback


resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~


nameserver 127.0.1.1




Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         172.29.145.129  0.0.0.0         UG    0      0        0 ppp0
172.29.145.129  0.0.0.0         255.255.255.255 UH    0      0        0 ppp0


--- 172.29.145.129 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 88.650/90.855/93.060/2.205 ms


--- 127.0.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.025/0.032/0.040/0.009 ms




iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~


(Region : "en_IN")
country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS




iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~


wlan0     13 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 13 (2.472 GHz)




iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~






blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~


[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci




modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~


[ath9k]
filename:       /lib/modules/3.13.0-46-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
srcversion:     274594FBD61F5DF88102A4C
depends:        ath9k_hw,mac80211,ath9k_common,cfg80211,ath
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           bt_ant_diversity:Enable WLAN/BT RX antenna diversity (int)
parm:           ps_enable:Enable WLAN PowerSave (int)


[ath9k_common]
filename:       /lib/modules/3.13.0-46-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
srcversion:     93644B269B570BC55CF5154
depends:        ath,ath9k_hw


[ath9k_hw]
filename:       /lib/modules/3.13.0-46-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
srcversion:     65C14EF588BF1A68181643C
depends:        ath


[ath]
filename:       /lib/modules/3.13.0-46-generic/kernel/drivers/net/wireless/ath/ath.ko
srcversion:     88A67C5359B02C5A710AFCF
depends:        cfg80211


[mac80211]
filename:       /lib/modules/3.13.0-46-generic/kernel/net/mac80211/mac80211.ko
srcversion:     B8DF1ECC076C2FCEAC70533
depends:        cfg80211
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/3.13.0-46-generic/kernel/net/wireless/cfg80211.ko
srcversion:     5C139B156678DB83EDA757D
depends:        
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


[wmi]
filename:       /lib/modules/3.13.0-46-generic/kernel/drivers/platform/x86/wmi.ko
srcversion:     CED5410F008DC70DF5F064B
depends:        
parm:           debug_event:Log WMI Events [0/1] (bool)
parm:           debug_dump_wdg:Dump available WMI interfaces [0/1] (bool)




udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~


# PCI device 0x1969:0x1090 (alx)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# PCI device 0x168c:0x002b (ath9k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"




Custom files/entries ~~~~~~~~~~~~~~~


/etc/modules        : Default
/etc/rc.local       : Default
/etc/modprobe.d     : Not Default
/etc/pm/(cnf|pw|sl) : Default


[/etc/modprobe.d]
iwlwifi.conf      : remove iwlwifi \
                    (/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
                    && /sbin/modprobe -r mac80211
mlx4.conf         : softdep mlx4_core post: mlx4_en




Kernel boot line ~~~~~~~~~~~~~~~~~~~


BOOT_IMAGE=/boot/vmlinuz-3.13.0-46-generic.efi.signed root=UUID=f1de0020-1f39-4c43-89d5-214805c9a690 ro quiet splash vt.handoff=7




dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


[    0.476795] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.477078] audit: initializing netlink socket (disabled)
[    0.610861] alx 0000:03:00.0 eth0: Qualcomm Atheros AR816x/AR817x Ethernet [<MAC eth0>]
[   12.826449] wmi: Mapper loaded
[   13.002752] ath: phy0: Enable LNA combining
[   13.005489] ath: phy0: ASPM enabled: 0x43
[   13.005492] ath: EEPROM regdomain: 0x65
[   13.005494] ath: EEPROM indicates we should expect a direct regpair map
[   13.005495] ath: Country alpha2 being used: 00
[   13.005496] ath: Regpair used: 0x65
[   41.888752] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   44.210017] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready


    ======== Done ========

---

### Post by jeremy31 on 2015-03-07
> **genius2 said:**
> Sorry here is the complete output

```
======== Wireless-Info START ========


System-Info ~~~~~~~~~~~~~~~~~~~~~~~~


genius-Lenovo-G580 3.13.0-46-generic x86_64,  Ubuntu 14.04.2 LTS, trusty


CPU    : Intel(R) Core(TM) i5-3210M CPU @ 2.50GHz
Memory : 3800 MB
Uptime : 15:34:25 up 6 min,  2 users,  load average: 0.28, 0.61, 0.35




lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


02:00.0 Network controller [0280]: Qualcomm Atheros AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
    Subsystem: Lenovo Device [17aa:30a1]
    Kernel driver in use: ath9k
03:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8162 Fast Ethernet [1969:1090] (rev 10)
    Subsystem: Lenovo Device [17aa:3978]
    Kernel driver in use: alx




lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


Bus 002 Device 004: ID 058f:6366 Alcor Micro Corp. Multi Flash Reader
Bus 002 Device 003: ID 0489:e042 Foxconn / Hon Hai 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0c45:6455 Microdia 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 004: ID 12d1:140b Huawei Technologies Co., Ltd. EC1260 Wireless Data Modem HSD USB Card
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub




PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~






iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~


wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thrff
          Power Managementff
          




rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


      Interface        Soft blocked  Hard blocked
0: phy0: Wireless LAN      no            yes
1: hci0: Bluetooth         yes           no




lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


ath9k                 164164  0 
ath9k_common           13551  1 ath9k
ath9k_hw              453856  2 ath9k_common,ath9k
ath                    28698  3 ath9k_common,ath9k,ath9k_hw
mac80211              630669  1 ath9k
cfg80211              484040  3 ath,ath9k,mac80211
wmi                    19177  0 




module parameters ~~~~~~~~~~~~~~~~~~


ath9k         (5): blink=0 | bt_ant_diversity=0 | btcoex_enable=0 | nohwcrypt=0 | ps_enable=0
cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500
wmi           (2): debug_dump_wdg=N | debug_event=N




nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~


State: connected (global)
================================================o=========================o=========o=============o=========o===========o==============o===========
 Interface & ID                                 | Type                    | Driver  | State       | Default | Speed     | Support      | HW Addr   
================================================o=========================o=========o=============o=========o===========o==============o===========
 ttyUSB2  [Tata Indicom (Photon+) connection 1] | Mobile Broadband (CDMA) | option1 | connected   | yes     |           |              |           


    Address:         14.98.77.67
    Prefix:          32 (255.255.255.255)
    Gateway:         172.29.145.129
    DNS:             103.8.44.5
    DNS:             103.8.45.5
------------------------------------------------+-------------------------+---------+-------------+---------+-----------+--------------+-----------
 eth0                                           | Wired                   | alx     | unavailable | no      |           |              | <MAC eth0>
------------------------------------------------+-------------------------+---------+-------------+---------+-----------+--------------+-----------
 wlan0                                          | 802.11 WiFi             | ath9k   | unavailable | no      |           | WEP/WPA/WPA2 | <MAC wlan0>
------------------------------------------------+-------------------------+---------+-------------+---------+-----------+--------------+-----------




NetworkManager.state ~~~~~~~~~~~~~~~
[main]
NetworkingEnabled=true
WirelessEnabled=false
WWANEnabled=true
WimaxEnabled=true




NetworkManager.conf ~~~~~~~~~~~~~~~~


[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq


no-auto-default=<MAC eth0>,


[ifupdown]
managed=false




NM WiFi Profiles ~~~~~~~~~~~~~~~~~~~


cmswire              : ssid=cmswire | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
davis                : ssid=davis | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
ehepd210             : ssid=ehepd210 | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
guesthouse           : ssid=guesthouse | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
Guest Network        : ssid=Guest Network | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
IITG_GUEST           : ssid=IITG_GUEST | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
internet             : ssid=internet | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
internet 1           : ssid=internet | autoconnect=false | mac-address=<MAC wlan0> | ipv4=shared | ipv6=auto 
kirti mobile         : ssid=kirti mobile | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
Panasonic P81        : ssid=Panasonic P81 | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
PU@CAMPUS            : ssid=PU@CAMPUS | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
RAMANUJAN            : ssid=RAMANUJAN | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
scorp                : ssid=scorp | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
Tata-Photon-Max-Wi-Fi-2812 : ssid=Tata-Photon-Max-Wi-Fi-2812 | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
TP-LINK_ED8319       : ssid=TP-LINK_ED8319 | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
Tuta                 : ssid=Tuta | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
Wi-Fi connection 1   : ssid=inter | ipv6=auto | ipv4=auto 




interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~


# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback


resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~


nameserver 127.0.1.1




Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         172.29.145.129  0.0.0.0         UG    0      0        0 ppp0
172.29.145.129  0.0.0.0         255.255.255.255 UH    0      0        0 ppp0


--- 172.29.145.129 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 88.650/90.855/93.060/2.205 ms


--- 127.0.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.025/0.032/0.040/0.009 ms




iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~


(Region : "en_IN")
country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS




iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~


wlan0     13 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 13 (2.472 GHz)




iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~






blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~


[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci




modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~


[ath9k]
filename:       /lib/modules/3.13.0-46-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
srcversion:     274594FBD61F5DF88102A4C
depends:        ath9k_hw,mac80211,ath9k_common,cfg80211,ath
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           bt_ant_diversity:Enable WLAN/BT RX antenna diversity (int)
parm:           ps_enable:Enable WLAN PowerSave (int)


[ath9k_common]
filename:       /lib/modules/3.13.0-46-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
srcversion:     93644B269B570BC55CF5154
depends:        ath,ath9k_hw


[ath9k_hw]
filename:       /lib/modules/3.13.0-46-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
srcversion:     65C14EF588BF1A68181643C
depends:        ath


[ath]
filename:       /lib/modules/3.13.0-46-generic/kernel/drivers/net/wireless/ath/ath.ko
srcversion:     88A67C5359B02C5A710AFCF
depends:        cfg80211


[mac80211]
filename:       /lib/modules/3.13.0-46-generic/kernel/net/mac80211/mac80211.ko
srcversion:     B8DF1ECC076C2FCEAC70533
depends:        cfg80211
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/3.13.0-46-generic/kernel/net/wireless/cfg80211.ko
srcversion:     5C139B156678DB83EDA757D
depends:        
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


[wmi]
filename:       /lib/modules/3.13.0-46-generic/kernel/drivers/platform/x86/wmi.ko
srcversion:     CED5410F008DC70DF5F064B
depends:        
parm:           debug_event:Log WMI Events [0/1] (bool)
parm:           debug_dump_wdg:Dump available WMI interfaces [0/1] (bool)




udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~


# PCI device 0x1969:0x1090 (alx)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# PCI device 0x168c:0x002b (ath9k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"




Custom files/entries ~~~~~~~~~~~~~~~


/etc/modules        : Default
/etc/rc.local       : Default
/etc/modprobe.d     : Not Default
/etc/pm/(cnf|pw|sl) : Default


[/etc/modprobe.d]
iwlwifi.conf      : remove iwlwifi \
                    (/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
                    && /sbin/modprobe -r mac80211
mlx4.conf         : softdep mlx4_core post: mlx4_en




Kernel boot line ~~~~~~~~~~~~~~~~~~~


BOOT_IMAGE=/boot/vmlinuz-3.13.0-46-generic.efi.signed root=UUID=f1de0020-1f39-4c43-89d5-214805c9a690 ro quiet splash vt.handoff=7




dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


[    0.476795] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.477078] audit: initializing netlink socket (disabled)
[    0.610861] alx 0000:03:00.0 eth0: Qualcomm Atheros AR816x/AR817x Ethernet [<MAC eth0>]
[   12.826449] wmi: Mapper loaded
[   13.002752] ath: phy0: Enable LNA combining
[   13.005489] ath: phy0: ASPM enabled: 0x43
[   13.005492] ath: EEPROM regdomain: 0x65
[   13.005494] ath: EEPROM indicates we should expect a direct regpair map
[   13.005495] ath: Country alpha2 being used: 00
[   13.005496] ath: Regpair used: 0x65
[   41.888752] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   44.210017] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready


    ======== Done ========
```

It seems your wifi is disabled as rfkill shows a hard block.  You can try ```
echo "blacklist ideapad_laptop" | sudo tee /etc/modprobe.d/ideapad.conf
``` and reboot  and see if it works

---

### Post by genius2 on 2015-03-07
Jeremy thanks for quick reply, but the problem still persists.

---

### Post by jeremy31 on 2015-03-07
What modules are loaded ```
lsmod
``` The rfkill block is coming from somewhere and I don't think the Lenovo G series have a wifi switch other than the FN combo but that doesn't cause a hard block.  You could also try ```
sudo rfkill unblock all
```

---

### Post by genius2 on 2015-03-07
Yes Jeremy i tried Fn+F5, but It did not help. I even tried rfkill unblock all, but no use. Here is the output of lsmod :

Module                  Size  Used by
ppp_deflate            12950  0 
bsd_comp               12921  0 
ppp_async              17413  1 
crc_ccitt              12707  1 ppp_async
option                 46789  3 
usb_wwan               20429  1 option
usbserial              45014  9 option,usb_wwan
rfcomm                 69160  8 
bnep                   19624  2 
nls_iso8859_1          12713  1 
snd_hda_codec_hdmi     46368  1 
snd_hda_codec_realtek    65580  1 
uvcvideo               80885  0 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
videobuf2_core         40664  1 uvcvideo
btusb                  32412  0 
videodev              134688  2 uvcvideo,videobuf2_core
bluetooth             391136  22 bnep,btusb,rfcomm
keucr                  72238  0 
arc4                   12608  2 
snd_hda_intel          56531  5 
snd_hda_codec         192906  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
ath9k                 164164  0 
ath9k_common           13551  1 ath9k
ath9k_hw              453856  2 ath9k_common,ath9k
ath                    28698  3 ath9k_common,ath9k,ath9k_hw
snd_pcm               102099  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
mac80211              630669  1 ath9k
dm_multipath           22873  0 
scsi_dh                14882  1 dm_multipath
intel_rapl             18773  0 
x86_pkg_temp_thermal    14205  0 
intel_powerclamp       14705  0 
coretemp               13435  0 
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
cfg80211              484040  3 ath,ath9k,mac80211
kvm                   455835  0 
crct10dif_pclmul       14289  0 
crc32_pclmul           13113  0 
ghash_clmulni_intel    13216  0 
aesni_intel            55624  0 
aes_x86_64             17131  1 aesni_intel
lrw                    13286  1 aesni_intel
gf128mul               14951  1 lrw
glue_helper            13990  1 aesni_intel
ablk_helper            13597  1 aesni_intel
cryptd                 20359  3 ghash_clmulni_intel,aesni_intel,ablk_helper
i915                  784111  4 
snd_rawmidi            30144  1 snd_seq_midi
joydev                 17381  0 
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29482  2 snd_pcm,snd_seq
drm_kms_helper         55071  1 i915
snd                    69322  20 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
drm                   303102  5 i915,drm_kms_helper
serio_raw              13462  0 
lpc_ich                21080  0 
soundcore              12680  1 snd
shpchp                 37032  0 
mei_me                 18627  0 
i2c_algo_bit           13413  1 i915
mei                    82276  1 mei_me
wmi                    19177  0 
video                  19476  1 i915
mac_hid                13205  0 
parport_pc             32701  0 
ppdev                  17671  0 
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
usb_storage            62209  0 
psmouse               106714  0 
ahci                   29915  3 
alx                    32452  0 
mdio                   13807  1 alx
libahci                32716  1 ahci
dm_mirror              22135  0 
dm_region_hash         20862  1 dm_mirror
dm_log                 18411  2 dm_region_hash,dm_mirror

---

### Post by jeremy31 on 2015-03-07
Might have to use a different method on this one ```
sudo rm /etc/modprobe.d/ideapad.conf
```

Then follow instructions here [http://iseborn.eu/2014/07/21/activating-wifi-in-ubuntu-on-lenovo-yoga-2/](http://iseborn.eu/2014/07/21/activating-wifi-in-ubuntu-on-lenovo-yoga-2/) except use this [ATTACH]260505[/ATTACH]  instead of the ideapad_laptop.c from the website, you will need to extract it to /workspace/ideapad
The Makefile from the site should work

---

### Post by genius2 on 2015-03-07
Thank a million jeremy...u made my day!! The issue is resolved :D:D

---

### Post by jeremy31 on 2015-03-07
> **genius2 said:**
> Thank a million jeremy...u made my day!! The issue is resolved :D:D

When your kernel updates, your wifi might stop working until the Ubuntu kernel fixes the issue.  If a kernel update causes the rfkill issue again do
```
cd ~/workspace/ideapad
``````
make clean
```
```
make
```
```
make install
```
Reboot

If you happen to notice the new kernel is version 3.16.0-?, you can check with ```
uname -a
``` Use this [ATTACH]260507[/ATTACH] file for ideapad_laptop.c in 3.16

---

### Post by nick-gokuz on 2015-10-24
Hi Here is my list, both my bluetooth is not working, please help



########## wireless info START ##########


Report from: 24 Oct 2015 21:31 IST +0530


Booted last: 24 Oct 2015 18:19 IST +0530


Script from: 27 Sep 2015 00:34 UTC +0000


##### release ###########################


Distributor ID:	LinuxMint
Description:	Linux Mint 17.2 Rafaela
Release:	17.2
Codename:	rafaela


##### kernel ############################


Linux 3.16.0-38-generic #52~14.04.1-Ubuntu SMP Fri May 8 09:43:57 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Cinnamon


##### lspci #############################


01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
	Subsystem: Lenovo Device [17aa:380a]
	Kernel driver in use: r8169


02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter [10ec:b723]
	Subsystem: Lenovo Device [17aa:b736]
	Kernel driver in use: rtl8723be


##### lsusb #############################


Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 004: ID 0bda:b728 Realtek Semiconductor Corp. 
Bus 002 Device 003: ID 5986:0652 Acer, Inc 
Bus 002 Device 002: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 002 Device 006: ID 18d1:4ee4 Google Inc. Nexus 4 (debug + tether)
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: ideapad_wlan: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
1: ideapad_bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
2: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
3: phy0: Wireless LAN
	Soft blocked: yes
	Hard blocked: no


##### lsmod #############################


rtl8723be              85054  0 
btcoexist              50304  1 rtl8723be
rtl8723_common         23361  1 rtl8723be
rtl_pci                26690  1 rtl8723be
rtlwifi                64255  2 rtl_pci,rtl8723be
mac80211              652777  3 rtl_pci,rtlwifi,rtl8723be
cfg80211              494362  2 mac80211,rtlwifi
snd_soc_rt5640         93042  0 
ideapad_laptop         18278  0 
snd_soc_rl6231         13037  1 snd_soc_rt5640
sparse_keymap          13948  1 ideapad_laptop
snd_soc_core          200204  1 snd_soc_rt5640
snd_pcm               104112  7 snd_soc_rt5640,snd_soc_core,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller,snd_pcm_dmaengine


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:440194 errors:0 dropped:0 overruns:0 frame:0
          TX packets:289200 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:560790170 (560.7 MB)  TX bytes:30563793 (30.5 MB)


##### iwconfig ##########################


eth0      no wireless extensions.


usb0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.42.129  0.0.0.0         UG    0      0        0 usb0
192.168.42.0    0.0.0.0         255.255.255.0   U     1      0        0 usb0


##### resolv.conf #######################


nameserver 127.0.1.1


##### network managers ##################


Installed:


	NetworkManager


Running:


root       891     1  0 18:19 ?        00:00:01 NetworkManager


##### NetworkManager info ###############


NetworkManager Tool


State: connected (global)


- Device: usb0  [Wired connection 2] -------------------------------------------
  Type:              Wired
  Driver:            rndis_host
  State:             connected
  Default:           yes
  HW Address:        <MAC 'usb0' [IF]>


  Capabilities:
    Carrier Detect:  yes


  Wired Properties
    Carrier:         on


  IPv4 Settings:
    Address:         192.168.42.244
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.42.129


    DNS:             192.168.42.129


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8723be
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'wlan0' [IF]>


  Capabilities:


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points 


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'eth0' [IF]>


  Capabilities:
    Carrier Detect:  yes


  Wired Properties
    Carrier:         off


##### NetworkManager.state ##############


[main]
NetworkingEnabled=true
WirelessEnabled=false
WWANEnabled=true
WimaxEnabled=true


##### NetworkManager.conf ###############


[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq


[ifupdown]
managed=false


##### NetworkManager profiles ###########


[[/etc/NetworkManager/system-connections/Auto dlink-n]] (600 root)
[connection] id=Auto dlink-n | type=802-11-wireless
[802-11-wireless] ssid=dlink-n | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: Asia/Kolkata (based on set time zone)


country 00:
	(2402 - 2472 @ 40), (3, 20)
	(2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
	(5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


##### iwlist channels ###################


eth0      no frequency information.


usb0      no frequency information.


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


##### iwlist scan #######################


eth0      Interface doesn't support scanning.


wlan0     Interface doesn't support scanning : Network is down


usb0      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


##### module infos ######################


[rtl8723be]
filename:       /lib/modules/3.16.0-38-generic/kernel/drivers/net/wireless/rtlwifi/rtl8723be/rtl8723be.ko
firmware:       rtlwifi/rtl8723befw.bin
description:    Realtek 8723BE 802.11n PCI wireless
license:        GPL
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         PageHe	<page_he@realsil.com.cn>
srcversion:     C94095C986767A931B924EF
depends:        rtlwifi,rtl8723-common,rtl_pci,btcoexist,mac80211
intree:         Y
vermagic:       3.16.0-38-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        C2:84:ED:AC:CF:0B:47:36:52:C3:4D:23:BE:C3:56:94:42:36:E6:3B
sig_hashalgo:   sha512
parm:           swlps:bool
parm:           swenc:using hardware crypto (default 0 [hardware])
 (bool)
parm:           ips:using no link power save (default 1 is open)
 (bool)
parm:           fwlps:using linked fw control power save (default 1 is open)
 (bool)
parm:           msi:Set to 1 to use MSI interrupts mode (default 0)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)


[rtl8723_common]
filename:       /lib/modules/3.16.0-38-generic/kernel/drivers/net/wireless/rtlwifi/rtl8723com/rtl8723-common.ko
description:    Realtek RTL8723AE/RTL8723BE 802.11n PCI wireless common routines
license:        GPL
author:         Larry Finger	<Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
srcversion:     7410431A59C24B1BC33226E
depends:        
intree:         Y
vermagic:       3.16.0-38-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        C2:84:ED:AC:CF:0B:47:36:52:C3:4D:23:BE:C3:56:94:42:36:E6:3B
sig_hashalgo:   sha512


[rtl_pci]
filename:       /lib/modules/3.16.0-38-generic/kernel/drivers/net/wireless/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger	<Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     3273ECD6028617EFD27E4F4
depends:        mac80211,rtlwifi
intree:         Y
vermagic:       3.16.0-38-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        C2:84:ED:AC:CF:0B:47:36:52:C3:4D:23:BE:C3:56:94:42:36:E6:3B
sig_hashalgo:   sha512


[rtlwifi]
filename:       /lib/modules/3.16.0-38-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger	<Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     8362106E96F806A9DBAE565
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.16.0-38-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        C2:84:ED:AC:CF:0B:47:36:52:C3:4D:23:BE:C3:56:94:42:36:E6:3B
sig_hashalgo:   sha512


[mac80211]
filename:       /lib/modules/3.16.0-38-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     376BFDE8E6207B0AAA6339B
depends:        cfg80211
intree:         Y
vermagic:       3.16.0-38-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        C2:84:ED:AC:CF:0B:47:36:52:C3:4D:23:BE:C3:56:94:42:36:E6:3B
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/3.16.0-38-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     33ED2C1448F5AEDBE7AF59E
depends:        
intree:         Y
vermagic:       3.16.0-38-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        C2:84:ED:AC:CF:0B:47:36:52:C3:4D:23:BE:C3:56:94:42:36:E6:3B
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


[rtl8723be]
debug: 0
fwlps: Y
ips: Y
msi: N
swenc: N
swlps: N


[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
probe_wait_ms: 500


[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00


##### /etc/modules ######################


lp
rtc


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
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x10ec:0xb723 (rtl8723be)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


##### dmesg #############################


[   31.925428] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   31.925745] rtlwifi: wireless switch is on
[   36.285305] r8169 0000:01:00.0 eth0: link down
[   36.285348] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[  123.273771] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  125.083627] wlan0: authenticate with <MAC address>
[  125.103673] wlan0: send auth to <MAC address> (try 1/3)
[  125.207133] wlan0: send auth to <MAC address> (try 2/3)
[  125.311080] wlan0: send auth to <MAC address> (try 3/3)
[  125.415077] wlan0: authentication with <MAC address> timed out
[  219.408397] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  220.291207] wlan0: authenticate with <MAC address>
[  220.301438] wlan0: send auth to <MAC address> (try 1/3)
[  220.302898] wlan0: authenticated
[  220.304725] wlan0: associate with <MAC address> (try 1/3)
[  220.308520] wlan0: RX AssocResp from <MAC address> (capab=0x431 status=0 aid=3)
[  220.308735] wlan0: associated
[  220.308762] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 3773.179481] rndis_host 2-3:1.0 usb0: register 'rndis_host' at usb-0000:00:14.0-3, RNDIS device, <MAC 'usb0' [IF]>
[ 3795.260978] wlan0: deauthenticating from <MAC address> by local choice (Reason: 3=DEAUTH_LEAVING)


########## wireless info END ############

---

### Post by jeremy31 on 2015-10-24
If you don't plan on many kernel updates you can 
```
sudo apt-get install build-essential git linux-headers-$(uname -r)
git clone https://github.com/lwfinger/rtlwifi_new.git
cd rtlwifi_new
make
sudo make install
cd ~
git clone -b troy https://github.com/lwfinger/rtl8723au_bt.git
cd rtl8723au_bt
make
sudo make install
```
Reboot

---

### Post by nick-gokuz on 2015-10-25
Really appreciate you quick response.
Is there any other way as I may like to update kernel

---

### Post by jeremy31 on 2015-10-25
If you do update kernel you can
```
cd rtlwifi_new
make clean
make
sudo make install
cd ~/rtl8723au_bt
make clean
make 
sudo make install
```

Reboot

---

### Post by nick-gokuz on 2015-10-26
Thanks a lot!! will try this.

---

