---
title: "Network suddenly stopped working"
date: 2021-08-19
forum: Networking &amp; Wireless
---

### Post by thegreatpretender on 2021-08-19
Hi 

I have been using linux since 1995, but I am still a noob. I think this is the first time I am posting a question on a forum so sorry to bother you, but I really hope some of you could lead me in the right direction to get network back up on my Ubuntu box including my kids Minecraft worlds :(. 

Problem: The network stopped working after a restart. I believe the reason for this could be that I cleaned up some network settings after removing a virtual machine - and I probably removed something I should not have removed. In the Ubuntu GUI, neither the network connection or the card is present in settings. There is of course no IP-address assigned to the card. It is a standard card integrated on the mother board. Nothing fancy. I also tried to add a wireless card (USB-stick), but nothing happens. The machine is dual boot with Windows 10 and the network works there so the hardware should be OK.

Thank you for any help!
Lars

-----

Here is some system output that I think could be useful:

lars@dellicious:~$ ifconfig
lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 82055  bytes 5903720 (5.9 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 82055  bytes 5903720 (5.9 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

virbr0: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        inet 192.168.122.1  netmask 255.255.255.0  broadcast 192.168.122.255
        ether 52:54:00:52:6c:78  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


lars@dellicious:~$ dmesg | grep -i 'eth|net|r816|error|fail|enp3s0'
<empty output>


lars@dellicious:~$ sudo lsmod
Module                  Size  Used by
nls_iso8859_1          16384  2
xt_CHECKSUM            16384  1
xt_MASQUERADE          20480  3
xt_conntrack           16384  1
ipt_REJECT             16384  2
nf_reject_ipv4         16384  1 ipt_REJECT
xt_tcpudp              20480  9
ip6table_mangle        16384  1
ip6table_nat           16384  1
iptable_mangle         16384  1
iptable_nat            16384  1
nf_nat                 45056  3 ip6table_nat,iptable_nat,xt_MASQUERADE
nf_conntrack          147456  3 xt_conntrack,nf_nat,xt_MASQUERADE
nf_defrag_ipv6         24576  1 nf_conntrack
nf_defrag_ipv4         16384  1 nf_conntrack
nf_tables             200704  0
libcrc32c              16384  3 nf_conntrack,nf_nat,nf_tables
nfnetlink              16384  1 nf_tables
ip6table_filter        16384  1
ip6_tables             32768  3 ip6table_filter,ip6table_nat,ip6table_mangle
iptable_filter         16384  1
bpfilter               16384  0
bridge                249856  0
stp                    16384  1 bridge
llc                    16384  2 bridge,stp
nvidia_uvm           1019904  0
nvidia_drm             57344  6
nvidia_modeset       1228800  9 nvidia_drm
nvidia              34168832  382 nvidia_uvm,nvidia_modeset
kvm_intel             294912  0
kvm                   819200  1 kvm_intel
crct10dif_pclmul       16384  1
crc32_pclmul           16384  0
ghash_clmulni_intel    16384  0
aesni_intel           372736  0
crypto_simd            16384  1 aesni_intel
cryptd                 24576  2 crypto_simd,ghash_clmulni_intel
joydev                 24576  0
input_leds             16384  0
glue_helper            16384  1 aesni_intel
drm_kms_helper        237568  1 nvidia_drm
serio_raw              20480  0
cec                    53248  1 drm_kms_helper
rc_core                61440  1 cec
fb_sys_fops            16384  1 drm_kms_helper
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
video                  49152  0
sch_fq_codel           20480  2
parport_pc             45056  0
ppdev                  24576  0
lp                     20480  0
parport                65536  3 parport_pc,lp,ppdev
drm                   548864  9 drm_kms_helper,nvidia_drm
sunrpc                540672  1
ip_tables              32768  3 iptable_filter,iptable_nat,iptable_mangle
x_tables               49152  11 ip6table_filter,xt_conntrack,iptable_filter,xt_tcpudp,xt_CHECKSUM,ip6_tables,ipt_REJECT,ip_tables,ip6table_mangle,xt_MASQUERADE,iptable_mangle
autofs4                45056  2
hid_generic            16384  0
usbhid                 57344  0
hid                   135168  2 usbhid,hid_generic
uas                    28672  0
usb_storage            73728  3 uas
psmouse               155648  0
ahci                   40960  3
libahci                36864  1 ahci
xhci_pci               20480  0
xhci_pci_renesas       20480  1 xhci_pci


lars@dellicious:~$ sudo lspci -nnk
00:00.0 Host bridge [0600]: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor DRAM Controller [8086:0150] (rev 09)
	Subsystem: Dell Xeon E3-1200 v2/3rd Gen Core processor DRAM Controller [1028:0585]
	Kernel driver in use: ivb_uncore
00:01.0 PCI bridge [0604]: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor PCI Express Root Port [8086:0151] (rev 09)
	Kernel driver in use: pcieport
00:16.0 Communication controller [0780]: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 [8086:1c3a] (rev 04)
	Subsystem: Dell 6 Series/C200 Series Chipset Family MEI Controller [1028:0585]
00:1a.0 USB controller [0c03]: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 [8086:1c2d] (rev 04)
	Subsystem: Dell 6 Series/C200 Series Chipset Family USB Enhanced Host Controller [1028:0585]
	Kernel driver in use: ehci-pci
00:1b.0 Audio device [0403]: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller [8086:1c20] (rev 04)
	Subsystem: Dell 6 Series/C200 Series Chipset Family High Definition Audio Controller [1028:0585]
00:1c.0 PCI bridge [0604]: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 [8086:1c10] (rev b4)
	Kernel driver in use: pcieport
00:1c.4 PCI bridge [0604]: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 5 [8086:1c18] (rev b4)
	Kernel driver in use: pcieport
00:1d.0 USB controller [0c03]: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 [8086:1c26] (rev 04)
	Subsystem: Dell 6 Series/C200 Series Chipset Family USB Enhanced Host Controller [1028:0585]
	Kernel driver in use: ehci-pci
00:1f.0 ISA bridge [0601]: Intel Corporation H61 Express Chipset LPC Controller [8086:1c5c] (rev 04)
	Subsystem: Dell H61 Express Chipset LPC Controller [1028:0585]
00:1f.2 SATA controller [0106]: Intel Corporation 6 Series/C200 Series Chipset Family 6 port Desktop SATA AHCI Controller [8086:1c02] (rev 04)
	Subsystem: Dell 6 Series/C200 Series Chipset Family 6 port Desktop SATA AHCI Controller [1028:0585]
	Kernel driver in use: ahci
	Kernel modules: ahci
00:1f.3 SMBus [0c05]: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller [8086:1c22] (rev 04)
	Subsystem: Dell 6 Series/C200 Series Chipset Family SMBus Controller [1028:0585]
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation Device [10de:2188] (rev a1)
	Subsystem: NVIDIA Corporation Device [10de:2188]
	Kernel driver in use: nvidia
	Kernel modules: nvidiafb, nvidia_drm, nvidia
01:00.1 Audio device [0403]: NVIDIA Corporation TU116 High Definition Audio Controller [10de:1aeb] (rev a1)
	Subsystem: NVIDIA Corporation TU116 High Definition Audio Controller [10de:2188]
01:00.2 USB controller [0c03]: NVIDIA Corporation TU116 USB 3.1 Host Controller [10de:1aec] (rev a1)
	Subsystem: NVIDIA Corporation Device [10de:2188]
	Kernel driver in use: xhci_hcd
	Kernel modules: xhci_pci
01:00.3 Serial bus controller [0c80]: NVIDIA Corporation TU116 [GeForce GTX 1650 SUPER] [10de:1aed] (rev a1)
	Subsystem: NVIDIA Corporation TU116 [GeForce GTX 1650 SUPER] [10de:2188]
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)
	Subsystem: Dell RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [1028:0585]
	Kernel modules: r8168


lars@dellicious:~$ sudo lshw -class network
  *-network UNCLAIMED       
       description: Ethernet controller
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 06
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list
       configuration: latency=0
       resources: ioport:d000(size=256) memory:f2204000-f2204fff memory:f2200000-f2203fff
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: virbr0-nic
       serial: 52:54:00:52:6c:78
       size: 10Mbit/s
       capabilities: ethernet physical
       configuration: autonegotiation=off broadcast=yes driver=tun driverversion=1.6 duplex=full link=no multicast=yes port=twisted pair speed=10Mbit/s


lars@dellicious:~$ sudo networkctl list
IDX LINK       TYPE     OPERATIONAL SETUP    
  1 lo         loopback carrier     unmanaged
  2 virbr0     bridge   no-carrier  unmanaged
  3 virbr0-nic ether    off         unmanaged

3 links listed.


lars@dellicious:~$ sudo lsusb
Bus 002 Device 006: ID 047f:c043 Plantronics, Inc. 
Bus 002 Device 005: ID 058f:6387 Alcor Micro Corp. Flash Drive
Bus 002 Device 004: ID 0781:5571 SanDisk Corp. Cruzer Fit
Bus 002 Device 003: ID 0bda:8179 Realtek Semiconductor Corp. RTL8188EUS 802.11n Wireless Network Adapter
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 1a7c:0191 Evoluent VerticalMouse 4
Bus 001 Device 004: ID 046d:c30e Logitech, Inc. UltraX Keyboard (Y-BL49)
Bus 001 Device 003: ID 03f0:4117 HP, Inc LaserJet 1018
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by chili555 on 2021-08-19
Please run and post the result of:

```
sudo modprobe r8168 && sudo dmesg | grep r8168
```

Thanks.

---

### Post by linerman on 2021-08-20
Apart from command asked by chili555, please check topics about your NIC and suggested solution.

[https://ubuntuforums.org/showthread.php?t=2461096&page=2&p=14038009#post14038009](https://ubuntuforums.org/showthread.php?t=2461096&page=2&p=14038009#post14038009)
[https://ubuntuforums.org/showthread.php?t=2465253](https://ubuntuforums.org/showthread.php?t=2465253)
[https://ubuntuforums.org/showthread.php?t=2466118](https://ubuntuforums.org/showthread.php?t=2466118)

---

