---
title: "wi-fi is disabled"
date: 2018-10-03
forum: Networking &amp; Wireless
---

### Post by malaykar on 2018-10-03
unable to connect wi-fi,  on cable its working fine ...


$ iwconfig
enp0s18   no wireless extensions.

wlx00106092e218  IEEE 802.11  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          
lo        no wireless extensions.


$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes


$ sudo lshw -class network
  *-usb DISABLED            
       description: Wireless interface
       product: 802.11 bg WLAN
       vendor: Ralink
       physical id: 5
       bus info: usb@1:5
       logical name: wlx00106092e218
       version: 0.01
       serial: 00:10:60:92:e2:18
       capabilities: usb-2.00 ethernet physical wireless
       configuration: broadcast=yes driver=rt73usb driverversion=4.15.0-36-generic firmware=N/A link=no maxpower=300mA multicast=yes speed=480Mbit/s wireless=IEEE 802.11
  *-network
       description: Ethernet interface
       product: VT6102/VT6103 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: enp0s18
       version: 7c
       serial: 00:40:d0:e8:3d:2d
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.5.1 duplex=full latency=32 link=yes maxlatency=8 mingnt=3 multicast=yes port=MII speed=100Mbit/s
       resources: irq:9 ioport:4800(size=256) memory:cb300400-cb3004ff


$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge (rev 80)
00:00.1 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:00.5 PIC: VIA Technologies, Inc. CN896/VN896/P4M900 I/O APIC Interrupt Controller
00:00.6 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Security Device
00:00.7 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/VX700 PCI Bridge
00:02.0 PCI bridge: VIA Technologies, Inc. CN896/VN896/P4M900 PCI to PCI Bridge Controller
00:03.0 PCI bridge: VIA Technologies, Inc. CN896/VN896/P4M900 PCI to PCI Bridge Controller (rev 80)
00:0f.0 IDE interface: VIA Technologies, Inc. VT8237A SATA 2-Port Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07)
00:10.0 USB controller: VIA Technologies, Inc. VT82xx/62xx UHCI USB 1.1 Controller (rev a0)
00:10.1 USB controller: VIA Technologies, Inc. VT82xx/62xx UHCI USB 1.1 Controller (rev a0)
00:10.2 USB controller: VIA Technologies, Inc. VT82xx/62xx UHCI USB 1.1 Controller (rev a0)
00:10.3 USB controller: VIA Technologies, Inc. VT82xx/62xx UHCI USB 1.1 Controller (rev a0)
00:10.4 USB controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237A PCI to ISA Bridge
00:11.7 Host bridge: VIA Technologies, Inc. VT8237/8251 Ultra VLINK Controller
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102/VT6103 [Rhine-II] (rev 7c)
00:13.0 PCI bridge: VIA Technologies, Inc. VT8237A Host Bridge
00:13.1 PCI bridge: VIA Technologies, Inc. VT8237A PCI to PCI Bridge
01:00.0 VGA compatible controller: VIA Technologies, Inc. CN896/VN896/P4M900 [Chrome 9 HC] (rev 01)
06:01.0 Audio device: VIA Technologies, Inc. VT8237A/VT8251 HDA Controller (rev 10)




$ lsusb
Bus 001 Device 002: ID 148f:2573 Ralink Technology, Corp. RT2501/RT2573 Wireless Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub




$ lsmod
Module                  Size  Used by
ndiswrapper           282624  0
arc4                   16384  2
snd_hda_codec_hdmi     49152  1
snd_hda_codec_realtek   106496  1
snd_hda_codec_generic    73728  1 snd_hda_codec_realtek
rt73usb                32768  0
snd_hda_intel          40960  3
rt2x00usb              20480  1 rt73usb
snd_hda_codec         126976  4 snd_hda_intel,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec_realtek
rt2x00lib              53248  2 rt73usb,rt2x00usb
snd_hda_core           81920  5 snd_hda_intel,snd_hda_codec,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec_realtek
snd_hwdep              20480  1 snd_hda_codec
snd_pcm                98304  4 snd_hda_intel,snd_hda_codec,snd_hda_core,snd_hda_codec_hdmi
mac80211              778240  2 rt2x00lib,rt2x00usb
snd_timer              32768  1 snd_pcm
cfg80211              622592  2 rt2x00lib,mac80211
snd                    81920  14 snd_hda_intel,snd_hwdep,snd_hda_codec,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec_realtek,snd_pcm
crc_itu_t              16384  1 rt73usb
soundcore              16384  1 snd
input_leds             16384  0
coretemp               16384  0
joydev                 24576  0
mac_hid                16384  0
serio_raw              16384  0
shpchp                 36864  0
ip6t_REJECT            16384  1
nf_reject_ipv6         16384  1 ip6t_REJECT
nf_log_ipv6            16384  5
xt_hl                  16384  22
ip6t_rt                16384  3
nf_conntrack_ipv6      20480  8
nf_defrag_ipv6         36864  1 nf_conntrack_ipv6
ipt_REJECT             16384  1
nf_reject_ipv4         16384  1 ipt_REJECT
nf_log_ipv4            16384  5
nf_log_common          16384  2 nf_log_ipv6,nf_log_ipv4
xt_LOG                 16384  10
xt_limit               16384  13
xt_tcpudp              16384  18
xt_addrtype            16384  4
nf_conntrack_ipv4      16384  8
nf_defrag_ipv4         16384  1 nf_conntrack_ipv4
xt_conntrack           16384  16
sch_fq_codel           20480  2
ip6table_filter        16384  1
ip6_tables             28672  1 ip6table_filter
nf_conntrack_netbios_ns    16384  0
nf_conntrack_broadcast    16384  1 nf_conntrack_netbios_ns
nf_nat_ftp             16384  0
nf_nat                 32768  1 nf_nat_ftp
nf_conntrack_ftp       20480  1 nf_nat_ftp
parport_pc             36864  0
nf_conntrack          131072  8 nf_conntrack_ipv6,nf_conntrack_ftp,nf_conntrack_ipv4,nf_conntrack_broadcast,nf_nat_ftp,nf_conntrack_netbios_ns,xt_conntrack,nf_nat
libcrc32c              16384  2 nf_conntrack,nf_nat
ppdev                  20480  0
iptable_filter         16384  1
lp                     20480  0
parport                49152  3 lp,parport_pc,ppdev
ip_tables              28672  1 iptable_filter
x_tables               40960  13 xt_LOG,ipt_REJECT,ip_tables,iptable_filter,xt_tcpudp,xt_limit,ip6t_REJECT,ip6table_filter,xt_addrtype,ip6t_rt,xt_conntrack,ip6_tables,xt_hl
autofs4                40960  2
pata_acpi              16384  0
via_rhine              36864  0
psmouse               147456  0
mii                    16384  1 via_rhine
i2c_viapro             16384  0
sata_via               20480  1
pata_via               16384  0



Am I missing something ?

---

### Post by chili555 on 2018-10-03
> $ rfkill list all
0: phy0: Wireless LAN
Soft blocked: no
[COLOR="#FF0000"]Hard blocked: yes[/COLOR]That suggests that you should find the wireless or airplane mode switch or button and switch it.> $ lsmod
Module Size Used by
[COLOR="#FF0000"]ndiswrapper [/COLOR]282624 0
arc4 16384 2
snd_hda_codec_hdmi 49152 1
snd_hda_codec_realtek 106496 1
snd_hda_codec_generic 73728 1 snd_hda_codec_realtek
rt73usb 32768 0
snd_hda_intel 40960 3
rt2x00usb 20480 1 rt73usb
snd_hda_codec 126976 4 snd_hda_intel,snd_hda_codec_hdmi,snd_hda_codec_gen eric,snd_hda_codec_realtek
rt2x00lib 53248 2 rt73usb,rt2x00usb
<snip>That suggests that you tried to install the Windows driver to get the wireless to work. Even the great and powerful Windows can't reach out and press the wireless switch! Let's remove it:```
sudo apt-get purge ndiswrapper*
```Also, the fact that you even have a wireless switch that is turned off suggests that there is or was an internal wireless device. Is it disabled in the BIOS?

---

### Post by malaykar on 2018-10-04
ok  <sudo apt-get purge ndiswrapper*>  done. 
bios does not have such option its "Phoenix R1.24" and am in need to update the bios.




              *-usb DISABLED
                   description: Wireless interface
                   product: 802.11 bg WLAN
                   vendor: Ralink
                   physical id: 5
                   bus info: usb@1:5
                   logical name: wlx00106092e218
                   version: 0.01
                   serial: 00:10:60:92:e2:18
                   capabilities: usb-2.00 ethernet physical wireless
                   configuration: broadcast=yes driver=rt73usb driverversion=4.15.0-36-generic firmware=N/A link=no maxpower=300mA multicast=yes speed=480Mbit/s wireless=IEEE 802.11

            *-network
             description: Ethernet interface
             product: VT6102/VT6103 [Rhine-II]
             vendor: VIA Technologies, Inc.
             physical id: 12
             bus info: pci@0000:00:12.0
             logical name: enp0s18
             version: 7c
             serial: 00:40:d0:e8:3d:2d
             size: 100Mbit/s
             capacity: 100Mbit/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.5.1 duplex=full ip=192.168.0.103 latency=32 link=yes maxlatency=8 mingnt=3 multicast=yes port=MII speed=100Mbit/s
             resources: irq:9 ioport:4800(size=256) memory:cb300400-cb3004ff



$ sudo lshw
raktim-notebook-pc          
    description: Computer
    product: Notebook PC
    vendor: HCL Infosystems Limited
    version: VT6363A
    serial: 8084AX059803
    width: 64 bits
    capabilities: smbios-2.4 dmi-2.4 vsyscall32
    configuration: administrator_password=disabled boot=oem-specific frontpanel_password=unknown keyboard_password=unknown power-on_password=disabled uuid=00000000-0000-0000-0000-0040D0E83D2D
  *-core
       description: Motherboard
       product: Notebook PC
       vendor: HCL Infosystems Limited
       physical id: 0
       version: VT6363A
       serial: 1234567890
       slot: Modem
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies LTD
          physical id: 0
          version: R1.24
          date: 06/18/2008
          size: 97KiB
          capabilities: pci pnp upgrade shadowing escd cdboot bootselect edd int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot smartbattery biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) Dual  CPU  T2390  @ 1.86GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: Intel(R) Pentium(R) Dual  CPU  T2
          slot: mPGA 479m
          size: 1860MHz
          capacity: 3600MHz
          width: 64 bits
          clock: 200MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx x86-64 constant_tsc arch_perfmon pebs bts rep_good nopl cpuid aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm lahf_lm pti dtherm

---

### Post by chili555 on 2018-10-04
> ok <sudo apt-get purge ndiswrapper*> done. 
bios does not have such option its "Phoenix R1.24" and am in need to update the bios.Yes, but what about this??> 
```
$ rfkill list all
0: phy0: Wireless LAN
Soft blocked: no
[COLOR="#FF0000"]Hard blocked: yes[/COLOR]
```
That suggests that you should find the wireless or airplane mode switch or button and switch it.Until you fix the hard block, the wireless will not work.

---

