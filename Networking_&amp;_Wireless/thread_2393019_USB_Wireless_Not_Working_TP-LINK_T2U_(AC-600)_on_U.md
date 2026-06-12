---
title: "USB Wireless Not Working TP-LINK T2U (AC-600) on Ubuntu 17.10"
date: 2018-05-28
forum: Networking &amp; Wireless
---

### Post by yami7 on 2018-05-28
Hey,

i have read topic from here: [https://ubuntuforums.org/showthread.php?t=2367163&highlight=Mt7610u](https://ubuntuforums.org/showthread.php?t=2367163&highlight=Mt7610u)

But i think that i have other situation. I will post many outputs of commands from that thread from my computer.
Tp-link is connected now to my pc, here's outputs of commands:


```
sudo lshw -C network

```
```
  *-network                 
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlp3s0
       version: 01
       serial: 74:2f:68:d5:2e:90
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=4.13.0-43-generic firmware=N/A ip=192.168.0.185 latency=0 link=yes multicast=yes wireless=IEEE 802.11
       resources: irq:17 memory:ddc00000-ddc0ffff
  *-network
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: enp5s0
       version: 06
       serial: 54:04:a6:1d:a8:0f
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8168e-2.fw latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:29 ioport:9000(size=256) memory:d2104000-d2104fff memory:d2100000-d2103fff
  *-network:0
       description: Ethernet interface
       physical id: 6
       logical name: br-c1117af9c790
       serial: 02:42:28:9f:07:15
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A ip=172.18.0.1 link=no multicast=yes
  *-network:1
       description: Ethernet interface
       physical id: 7
       logical name: br-8f112f5c658f
       serial: 02:42:a1:0e:5f:81
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A ip=172.19.0.1 link=no multicast=yes
  *-network:2
       description: Ethernet interface
       physical id: 8
       logical name: br-a45f7839a9b4
       serial: 02:42:1f:27:35:a2
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A ip=172.20.0.1 link=no multicast=yes
  *-network:3
       description: Ethernet interface
       physical id: 9
       logical name: br-b1c6dbe33f06
       serial: 02:42:f2:59:8d:ea
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A ip=172.21.0.1 link=no multicast=yes
  *-network:4
       description: Ethernet interface
       physical id: a
       logical name: docker0
       serial: 02:42:06:3a:66:61
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A ip=172.17.0.1 link=no multicast=yes



```





```
ifconfig


```


```
br-8f112f5c658f: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500        inet 172.19.0.1  netmask 255.255.0.0  broadcast 0.0.0.0
        ether 02:42:a1:0e:5f:81  txqueuelen 0  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


br-a45f7839a9b4: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        inet 172.20.0.1  netmask 255.255.0.0  broadcast 0.0.0.0
        ether 02:42:1f:27:35:a2  txqueuelen 0  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


br-b1c6dbe33f06: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        inet 172.21.0.1  netmask 255.255.0.0  broadcast 0.0.0.0
        ether 02:42:f2:59:8d:ea  txqueuelen 0  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


br-c1117af9c790: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        inet 172.18.0.1  netmask 255.255.0.0  broadcast 0.0.0.0
        ether 02:42:28:9f:07:15  txqueuelen 0  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


docker0: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        inet 172.17.0.1  netmask 255.255.0.0  broadcast 0.0.0.0
        ether 02:42:06:3a:66:61  txqueuelen 0  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


enp5s0: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        ether 54:04:a6:1d:a8:0f  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 4643578  bytes 375958668 (375.9 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 4643578  bytes 375958668 (375.9 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


wlp3s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.0.185  netmask 255.255.255.0  broadcast 192.168.0.255
        inet6 fe80::48ef:421e:e7fc:76a6  prefixlen 64  scopeid 0x20<link>
        inet6 2a02:a31a:4141:d580:1dae:b891:7d67:40a7  prefixlen 64  scopeid 0x0<global>
        inet6 2a02:a31a:4141:d580:4556:1a90:edfe:11c8  prefixlen 64  scopeid 0x0<global>
        ether 74:2f:68:d5:2e:90  txqueuelen 1000  (Ethernet)
        RX packets 53679  bytes 28963149 (28.9 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 45022  bytes 8346299 (8.3 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0



```



```
[COLOR=#000000][FONT=&amp]rfkill list all[/FONT][/COLOR]
```

```
0: phy0: Wireless LAN    Soft blocked: no
    Hard blocked: no
1: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: asus-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
3: asus-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no



```



```
[COLOR=#000000]iwconfig[/COLOR]
```

```
br-c1117af9c790  no wireless extensions.

br-8f112f5c658f  no wireless extensions.


wlp3s0    IEEE 802.11  ESSID:"UPC5300508"  
          Mode:Managed  Frequency:2.422 GHz  Access Point: 38:43:7D:5E:38:3B   
          Bit Rate=52 Mb/s   Tx-Power=15 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=50/70  Signal level=-60 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1  Invalid misc:755   Missed beacon:0


br-a45f7839a9b4  no wireless extensions.


br-b1c6dbe33f06  no wireless extensions.


enp5s0    no wireless extensions.


lo        no wireless extensions.


docker0   no wireless extensions.



```
```
lsusb
```
```
Bus 002 Device 004: ID 148f:761a Ralink Technology, Corp. 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 002: ID 04f3:0234 Elan Microelectronics Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 0bda:0139 Realtek Semiconductor Corp. RTS5139 Card Reader Controller
Bus 001 Device 003: ID 0cf3:3005 Atheros Communications, Inc. AR3011 Bluetooth
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub



```

```
lsmod
```

```
Module                  Size  Used byrfcomm                 77824  2
ipt_MASQUERADE         16384  5
nf_nat_masquerade_ipv4    16384  1 ipt_MASQUERADE
nf_conntrack_netlink    40960  0
nfnetlink              16384  2 nf_conntrack_netlink
xfrm_user              32768  1
xfrm_algo              16384  1 xfrm_user
iptable_nat            16384  1
nf_nat_ipv4            16384  1 iptable_nat
br_netfilter           24576  0
bridge                143360  1 br_netfilter
stp                    16384  1 bridge
llc                    16384  2 bridge,stp
aufs                  229376  0
pci_stub               16384  1
vboxpci                24576  0
vboxnetadp             28672  0
vboxnetflt             28672  0
vboxdrv               471040  3 vboxnetadp,vboxnetflt,vboxpci
ccm                    20480  3
bnep                   20480  2
bbswitch               16384  0
intel_rapl             20480  0
asus_nb_wmi            28672  0
mxm_wmi                16384  0
x86_pkg_temp_thermal    16384  0
asus_wmi               28672  1 asus_nb_wmi
sparse_keymap          16384  1 asus_wmi
intel_powerclamp       16384  0
coretemp               16384  0
kvm_intel             200704  0
kvm                   593920  1 kvm_intel
irqbypass              16384  1 kvm
btusb                  45056  0
btrtl                  16384  1 btusb
btbcm                  16384  1 btusb
crct10dif_pclmul       16384  0
btintel                16384  1 btusb
bluetooth             544768  31 btrtl,btintel,bnep,btbcm,rfcomm,btusb
crc32_pclmul           16384  0
ecdh_generic           24576  1 bluetooth
ghash_clmulni_intel    16384  0
pcbc                   16384  0
aesni_intel           188416  2
aes_x86_64             20480  1 aesni_intel
snd_hda_codec_hdmi     49152  1
rtsx_usb_ms            20480  0
crypto_simd            16384  1 aesni_intel
snd_hda_codec_realtek    98304  1
snd_hda_codec_generic    73728  1 snd_hda_codec_realtek
glue_helper            16384  1 aesni_intel
snd_hda_intel          40960  6
cryptd                 24576  3 crypto_simd,ghash_clmulni_intel,aesni_intel
snd_hda_codec         126976  4 snd_hda_intel,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec_realtek
memstick               16384  1 rtsx_usb_ms
snd_hda_core           81920  5 snd_hda_intel,snd_hda_codec,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec_realtek
snd_hwdep              20480  1 snd_hda_codec
intel_cstate           20480  0
snd_pcm                98304  4 snd_hda_intel,snd_hda_codec,snd_hda_core,snd_hda_codec_hdmi
intel_rapl_perf        16384  0
snd_seq_midi           16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
nvidia_uvm            667648  0
joydev                 20480  0
snd_rawmidi            32768  1 snd_seq_midi
arc4                   16384  2
ath9k                 151552  0
ath9k_common           36864  1 ath9k
ath9k_hw              471040  2 ath9k,ath9k_common
ath                    28672  3 ath9k_hw,ath9k,ath9k_common
snd_seq                65536  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
mac80211              782336  1 ath9k
snd_timer              32768  2 snd_seq,snd_pcm
input_leds             16384  0
snd                    81920  23 snd_hda_intel,snd_hwdep,snd_seq,snd_hda_codec,snd_timer,snd_rawmidi,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_seq_device,snd_hda_codec_realtek,snd_pcm
cfg80211              614400  4 mac80211,ath9k,ath,ath9k_common
serio_raw              16384  0
soundcore              16384  1 snd
wmi                    24576  2 asus_wmi,mxm_wmi
ip6t_REJECT            16384  1
nf_reject_ipv6         16384  1 ip6t_REJECT
shpchp                 36864  0
nf_log_ipv6            16384  4
lpc_ich                24576  0
mei_me                 40960  0
mei                   102400  1 mei_me
xt_hl                  16384  22
ip6t_rt                16384  3
nf_conntrack_ipv6      20480  10
nf_defrag_ipv6         36864  1 nf_conntrack_ipv6
ipt_REJECT             16384  1
nf_reject_ipv4         16384  1 ipt_REJECT
mac_hid                16384  0
nf_log_ipv4            16384  4
nf_log_common          16384  2 nf_log_ipv6,nf_log_ipv4
xt_LOG                 16384  8
xt_limit               16384  11
xt_tcpudp              16384  38
xt_addrtype            16384  6
nf_conntrack_ipv4      16384  21
nf_defrag_ipv4         16384  1 nf_conntrack_ipv4
xt_conntrack           16384  25
ip6table_filter        16384  1
ip6_tables             28672  1 ip6table_filter
nf_conntrack_netbios_ns    16384  0
nf_conntrack_broadcast    16384  1 nf_conntrack_netbios_ns
nf_nat_ftp             16384  0
nf_nat                 28672  3 nf_nat_ftp,nf_nat_masquerade_ipv4,nf_nat_ipv4
nf_conntrack_ftp       20480  1 nf_nat_ftp
nf_conntrack          131072  12 nf_conntrack_ipv6,nf_conntrack_ftp,nf_conntrack_ipv4,ipt_MASQUERADE,nf_conntrack_broadcast,nf_nat_ftp,nf_conntrack_netlink,nf_conntrack_netbios_ns,nf_nat_masquerade_ipv4,xt_conntrack,nf_nat_ipv4,nf_nat
libcrc32c              16384  2 nf_conntrack,nf_nat
iptable_filter         16384  1
parport_pc             32768  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,parport_pc,ppdev
ip_tables              24576  2 iptable_filter,iptable_nat
x_tables               40960  14 xt_LOG,ipt_REJECT,ip_tables,iptable_filter,xt_tcpudp,ipt_MASQUERADE,xt_limit,ip6t_REJECT,ip6table_filter,xt_addrtype,ip6t_rt,xt_conntrack,ip6_tables,xt_hl
autofs4                40960  2
rtsx_usb_sdmmc         28672  0
rtsx_usb               20480  2 rtsx_usb_sdmmc,rtsx_usb_ms
hid_generic            16384  0
usbhid                 49152  0
hid                   118784  2 hid_generic,usbhid
i915                 1822720  6
nvidia_drm             45056  8
nvidia_modeset        860160  7 nvidia_drm
nvidia              13139968  641 nvidia_modeset,nvidia_uvm
i2c_algo_bit           16384  1 i915
ahci                   36864  1
psmouse               147456  0
libahci                32768  1 ahci
r8169                  86016  0
drm_kms_helper        167936  2 i915,nvidia_drm
mii                    16384  1 r8169
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
fb_sys_fops            16384  1 drm_kms_helper
drm                   360448  12 i915,nvidia_drm,drm_kms_helper
video                  40960  2 asus_wmi,i915



```


Also i have tried installing driver from: [https://www.tp-link.com/us/download/Archer-T2UH.html](https://www.tp-link.com/us/download/Archer-T2UH.html)

But i had error with ```
make
``` command. Then i started trying to change ```
gcc
```
but still ```
make
``` gives me some error. Now it gives me this output:
```
~/Downloads/Archer_T2UH_Linux/Driver$ makemake -C UTIL/ osutil
make[1]: Entering directory '/home/kamil/Downloads/Archer_T2UH_Linux/Driver/UTIL'
cp -f os/linux/Makefile.6.util /home/kamil/Downloads/Archer_T2UH_Linux/Driver/UTIL/os/linux/Makefile
make -C /lib/modules/4.13.0-43-generic/build SUBDIRS=/home/kamil/Downloads/Archer_T2UH_Linux/Driver/UTIL/os/linux modules
make[2]: Entering directory '/usr/src/linux-headers-4.13.0-43-generic'
  CC [M]  /home/kamil/Downloads/Archer_T2UH_Linux/Driver/UTIL/os/linux/../../common/rt_os_util.o
gcc: error: unrecognized command line option &#8216;-fstack-protector-strong&#8217;
scripts/Makefile.build:316: recipe for target '/home/kamil/Downloads/Archer_T2UH_Linux/Driver/UTIL/os/linux/../../common/rt_os_util.o' failed
make[3]: *** [/home/kamil/Downloads/Archer_T2UH_Linux/Driver/UTIL/os/linux/../../common/rt_os_util.o] Error 1
Makefile:1550: recipe for target '_module_/home/kamil/Downloads/Archer_T2UH_Linux/Driver/UTIL/os/linux' failed
make[2]: *** [_module_/home/kamil/Downloads/Archer_T2UH_Linux/Driver/UTIL/os/linux] Error 2
make[2]: Leaving directory '/usr/src/linux-headers-4.13.0-43-generic'
Makefile:527: recipe for target 'osutil' failed
make[1]: *** [osutil] Error 2
make[1]: Leaving directory '/home/kamil/Downloads/Archer_T2UH_Linux/Driver/UTIL'
Makefile:3: recipe for target 'all' failed
make: *** [all] Error 2



```

I've focued on "gcc: error: unrecognized command line option &#8216;-fstack-protector-strong&#8217;" Part.
And i was trying to upgrade gcc.

```
gcc -v


```

```
Using built-in specs.COLLECT_GCC=gcc
COLLECT_LTO_WRAPPER=/usr/lib/gcc/x86_64-linux-gnu/4.8/lto-wrapper
Target: x86_64-linux-gnu
Configured with: ../src/configure -v --with-pkgversion='Ubuntu 4.8.5-4ubuntu6' --with-bugurl=file:///usr/share/doc/gcc-4.8/README.Bugs --enable-languages=c,c++,java,go,d,fortran,objc,obj-c++ --prefix=/usr --program-suffix=-4.8 --enable-shared --enable-linker-build-id --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --with-gxx-include-dir=/usr/include/c++/4.8 --libdir=/usr/lib --enable-nls --with-sysroot=/ --enable-clocale=gnu --enable-libstdcxx-debug --enable-libstdcxx-time=yes --enable-gnu-unique-object --disable-libmudflap --enable-plugin --with-system-zlib --disable-browser-plugin --enable-java-awt=gtk --enable-gtk-cairo --with-java-home=/usr/lib/jvm/java-1.5.0-gcj-4.8-amd64/jre --enable-java-home --with-jvm-root-dir=/usr/lib/jvm/java-1.5.0-gcj-4.8-amd64 --with-jvm-jar-dir=/usr/lib/jvm-exports/java-1.5.0-gcj-4.8-amd64 --with-arch-directory=amd64 --with-ecj-jar=/usr/share/java/eclipse-ecj.jar --enable-objc-gc --enable-multiarch --disable-werror --with-arch-32=i686 --with-abi=m64 --with-multilib-list=m32,m64,mx32 --with-tune=generic --enable-checking=release --build=x86_64-linux-gnu --host=x86_64-linux-gnu --target=x86_64-linux-gnu
Thread model: posix
gcc version 4.8.5 (Ubuntu 4.8.5-4ubuntu6) 



```


I've also tried [https://askubuntu.com/a/674122/755206](https://askubuntu.com/a/674122/755206)
without luck (similiar error on make command).
To be exact:
```
make -C toolsmake[1]: Entering directory '/home/kamil/mt7610u_wifi_sta_v3002_dpo_20130916/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory '/home/kamil/mt7610u_wifi_sta_v3002_dpo_20130916/tools'
/home/kamil/mt7610u_wifi_sta_v3002_dpo_20130916/tools/bin2h
chipset = mt7610u
cp -f os/linux/Makefile.6 /home/kamil/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux/Makefile
make -C /lib/modules/4.13.0-43-generic/build SUBDIRS=/home/kamil/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux modules
make[1]: Entering directory '/usr/src/linux-headers-4.13.0-43-generic'
  CC [M]  /home/kamil/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux/../../os/linux/rt_profile.o
gcc: error: unrecognized command line option &#8216;-fstack-protector-strong&#8217;
scripts/Makefile.build:316: recipe for target '/home/kamil/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux/../../os/linux/rt_profile.o' failed
make[2]: *** [/home/kamil/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux/../../os/linux/rt_profile.o] Error 1
Makefile:1550: recipe for target '_module_/home/kamil/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux' failed
make[1]: *** [_module_/home/kamil/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-4.13.0-43-generic'
Makefile:403: recipe for target 'LINUX' failed
make: *** [LINUX] Error 2



```

```

cat /proc/version

```

```

Linux version 4.13.0-43-generic (buildd@lgw01-amd64-026) (gcc version 7.2.0 (Ubuntu 7.2.0-8ubuntu3.2)) #48-Ubuntu SMP Wed May 16 12:18:48 UTC 2018

```

```

lspci -knn | grep Net -A3; rfkill list

03:00.0 Network controller [0280]: Qualcomm Atheros AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
    Subsystem: AzureWave AW-NB037H 802.11bgn Wireless Half-size Mini PCIe Card [AR9002WB-1NGCD] [1a3b:2c37]
    Kernel driver in use: ath9k
    Kernel modules: ath9k
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: asus-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
3: asus-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no

```

---

