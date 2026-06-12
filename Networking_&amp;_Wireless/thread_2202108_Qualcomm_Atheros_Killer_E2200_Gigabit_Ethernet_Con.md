---
title: "Qualcomm Atheros Killer E2200 Gigabit Ethernet Controller driver for ubuntu 12.04.3"
date: 2014-01-27
forum: Networking &amp; Wireless
---

### Post by sugat_itlog on 2014-01-27
Hi,

I have an MSI Z77A-G45 GAMING and tried to make my onboard NIC  work. And it worked, I just followed the procedures on page 7 in this post ([http://ubuntuforums.org/showthread.php?t=2008332&page=14](http://ubuntuforums.org/showthread.php?t=2008332&page=14)).

But my  problem now is, the VLAN tag was stripped off. Meaning if VLAN is used,  it cannot communicate or connect.

I have 2 NICs

onboard is ...
[FONT=courier new]02:00.0 Ethernet controller [0200]: Qualcomm Atheros Killer E2200 Gigabit Ethernet Controller [1969:e091] (rev 13)
Subsystem: Micro-Star International Co., Ltd. Device [1462:7752][/FONT]

pci is ...

[FONT=courier new]03:00.0  Ethernet controller [0200]: Realtek Semiconductor Co., Ltd.  RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168]  (rev 06)
Subsystem: Device [7470:3468]
Kernel driver in use: r8169
Kernel modules: r8169[/FONT]

My pci NIC works well and VLAN tag is present or working. I can use the Inter VLAN. But for the onboard NIC, cannot ping when using Inter VLAN.

Is it the NIC model of (my) onboard do not support VLAN? Or the driver that I used?

Really appreciate for everything. And I need assistance about this.

Am using 12.04.3 and using GNS3 for my cisco review.

And thanks in advance.

========
[FONT=courier new]
:~# uname -a
Linux ALYCOMP 3.8.0-35-generic #50~precise1-Ubuntu SMP Wed Dec 4 17:25:51 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux[/FONT]

========

:~$ lspci -knn
00:00.0 Host bridge [0600]: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor DRAM Controller [8086:0150] (rev 09)
    Subsystem: Micro-Star International Co., Ltd. Device [1462:7752]
00:02.0  VGA compatible controller [0300]: Intel Corporation Xeon E3-1200 v2/3rd  Gen Core processor Graphics Controller [8086:0162] (rev 09)
    Subsystem: Micro-Star International Co., Ltd. Device [1462:2111]
    Kernel driver in use: i915
    Kernel modules: i915
00:14.0  USB controller [0c03]: Intel Corporation 7 Series/C210 Series Chipset  Family USB xHCI Host Controller [8086:1e31] (rev 04)
    Subsystem: Micro-Star International Co., Ltd. Device [1462:7752]
    Kernel driver in use: xhci_hcd
00:16.0  Communication controller [0780]: Intel Corporation 7 Series/C210 Series  Chipset Family MEI Controller #1 [8086:1e3a] (rev 04)
    Subsystem: Micro-Star International Co., Ltd. Device [1462:7752]
    Kernel driver in use: mei
    Kernel modules: mei
00:1a.0  USB controller [0c03]: Intel Corporation 7 Series/C210 Series Chipset  Family USB Enhanced Host Controller #2 [8086:1e2d] (rev 04)
    Subsystem: Micro-Star International Co., Ltd. Device [1462:7752]
    Kernel driver in use: ehci-pci
00:1b.0  Audio device [0403]: Intel Corporation 7 Series/C210 Series Chipset  Family High Definition Audio Controller [8086:1e20] (rev 04)
    Subsystem: Micro-Star International Co., Ltd. Device [1462:f752]
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel
00:1c.0 PCI bridge [0604]: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 [8086:1e10] (rev c4)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.1 PCI bridge [0604]: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 2 [8086:1e12] (rev c4)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.3 PCI bridge [0604]: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 4 [8086:1e16] (rev c4)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1d.0  USB controller [0c03]: Intel Corporation 7 Series/C210 Series Chipset  Family USB Enhanced Host Controller #1 [8086:1e26] (rev 04)
    Subsystem: Micro-Star International Co., Ltd. Device [1462:7752]
    Kernel driver in use: ehci-pci
00:1f.0 ISA bridge [0601]: Intel Corporation Z77 Express Chipset LPC Controller [8086:1e44] (rev 04)
    Subsystem: Micro-Star International Co., Ltd. Device [1462:7752]
    Kernel driver in use: lpc_ich
    Kernel modules: lpc_ich
00:1f.2  SATA controller [0106]: Intel Corporation 7 Series/C210 Series Chipset  Family 6-port SATA Controller [AHCI mode] [8086:1e02] (rev 04)
    Subsystem: Micro-Star International Co., Ltd. Device [1462:7752]
    Kernel driver in use: ahci
    Kernel modules: ahci
00:1f.3 SMBus [0c05]: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller [8086:1e22] (rev 04)
    Subsystem: Micro-Star International Co., Ltd. Device [1462:7752]
    Kernel modules: i2c-i801
02:00.0 Ethernet controller [0200]: Qualcomm Atheros Killer E2200 Gigabit Ethernet Controller [1969:e091] (rev 13)
    Subsystem: Micro-Star International Co., Ltd. Device [1462:7752]
    Kernel modules: alx
03:00.0  Ethernet controller [0200]: Realtek Semiconductor Co., Ltd.  RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168]  (rev 06)
    Subsystem: Device [7470:3468]
    Kernel driver in use: r8169
    Kernel modules: r8169

========

:~# lshw -C network
  *-network UNCLAIMED     
       description: Ethernet controller
       product: Killer E2200 Gigabit Ethernet Controller
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 13
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi msix cap_list
       configuration: latency=0
       resources: memory:f7d00000-f7d3ffff ioport:e000(size=128)
  *-network
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 06
       serial: 10:fe:ed:07:a7:f9
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
        capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet  physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd  autonegotiation
       configuration: autonegotiation=on  broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full  firmware=rtl_nic/rtl8168e-2.fw ip=192.168.1.200 latency=0 link=yes  multicast=yes port=MII speed=100Mbit/s
       resources: irq:43 ioport:d000(size=256) memory:f7c04000-f7c04fff memory:f7c00000-f7c03fff

========

[FONT=courier new]:~# lsmod
Module                  Size  Used by
atl1                   45310  0 
atl1c                  46279  0 
atl1e                  42078  0 
usb_storage            61749  1 
vmnet                  55751  13 
vsock                  52918  0 
vmci                   87405  1 vsock
vmmon                  80278  0 
rfcomm                 47922  0 
bnep                   18399  2 
bluetooth             247324  10 rfcomm,bnep
parport_pc             28284  1 
ppdev                  17113  0 
snd_hda_codec_hdmi     37463  1 
snd_hda_codec_realtek    79962  1 
snd_hda_intel          44339  3 
snd_hda_codec         141761  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm               102477  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30417  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
coretemp               13596  0 
kvm_intel             137928  0 
kvm                   456261  1 kvm_intel
snd_seq                61930  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29989  2 snd_pcm,snd_seq
snd_seq_device         14497  3 snd_seq_midi,snd_rawmidi,snd_seq
ch341                  13544  2 
usbserial              37161  5 ch341
ghash_clmulni_intel    13259  0 
i915                  621477  3 
drm_kms_helper         49597  1 i915
aesni_intel            55495  0 
drm                   287796  4 i915,drm_kms_helper
psmouse                97902  0 
mei                    45974  0 
snd                     69533  16  snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
joydev                 17613  0 
ablk_helper            13597  1 aesni_intel
cryptd                 20530  3 ghash_clmulni_intel,aesni_intel,ablk_helper
lrw                    13323  1 aesni_intel
aes_x86_64             17255  1 aesni_intel
xts                    12951  1 aesni_intel
gf128mul               14951  2 lrw,xts
soundcore              12680  1 snd
snd_page_alloc         18798  2 snd_hda_intel,snd_pcm
mxm_wmi                13021  0 
microcode              23075  0 
wmi                    19256  1 mxm_wmi
lpc_ich                17144  0 
i2c_algo_bit           13564  1 i915
mac_hid                13253  0 
serio_raw              13215  0 
video                  19652  1 i915
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
hid_generic            12540  0 
usbhid                 47346  0 
hid                   105826  2 hid_generic,usbhid
ahci                   25879  2 
libahci                31636  1 ahci
r8169                  68904  0[/FONT]

========

[FONT=courier new]:~# lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.4 LTS
Release:    12.04
Codename:    precise
[/FONT]

---

### Post by chili555 on 2014-01-27
I'm sure I don't know *anything* about VLAN tagging but I know a bit about compiling a driver and troubleshooting. I wonder why these are loaded:> :~# lsmod
Module Size Used by
[COLOR="#FF0000"]atl1[/COLOR] 45310 0
[COLOR="#FF0000"]atl1c[/COLOR] 46279 0
[COLOR="#FF0000"]atl1e[/COLOR] 42078 0
usb_storage 61749 1
vmnet 55751 13
vsock 52918 0 And why *alx* is not. Are the atl brothers called in /etc/modules? They shouldn't be. Is there any error here?```
sudo modprobe alx
```And then does the Killer no longer show as unclaimed in *lshw*?

I would also try the alx package here: [http://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.13/backports-3.13-1.tar.xz](http://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.13/backports-3.13-1.tar.xz)

If you need a step-by-step, please post back.

---

### Post by sugat_itlog on 2014-01-27
Hi Chili. Appreciate for the reply. And sorry for the late response.

Reason why it was loaded, cause I was trying other module to see if it works. But that was before I discovered about my problem.

I  was able to successfully load the alx when I followed the instruction  on page 7 on this thread  ([http://ubuntuforums.org/showthread.php?t=2008332&page=7](http://ubuntuforums.org/showthread.php?t=2008332&page=7)). I used  sauyon patch. Downloaded the driver here  [https://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.8/](https://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.8/).

When I loaded the alx, my NIC appeared and after reboot able to see my nic again and able to use it.

But  my concern is, in windows I cannot use the inter vlan cause it stripped  off the VLAN tag(ging) because thats probably how windows is.

I used ubuntu cause the vlan tag is working. And even my pci nic is working with inter vlan.

Is  there anything you want me to do to check again? Or better to format my  pc again and install (again) ubuntu and do the installation of the nic  again?

Thanks and appreciate for the assistance.

---

### Post by chili555 on 2014-01-27
I must be corn-fused:> I used ubuntu cause the vlan tag is working. And even my pci nic is working with inter vlan.If everything is working as expected in Ubuntu, then what's the question? What am I missing?

If your question is why does it work perfectly in Ubuntu but not in Windows, I don't have any idea and doubt this is a good forum to ask. 

I doubt any change, such as a re-install or an updated driver in Ubuntu is going to help or hurt you in Windows.

---

### Post by sugat_itlog on 2014-01-27
Hi Chili. Really appreciate for everything. For real.

Your backports-3.13-1 worked.

I guess your way is better than sauyon. Though wanted to know how you make it worked. How you do create/compile a driver for linux. May I know the steps, readings, etc.

For the benefit of others, below are the steps I did after a reboot and did a sudo modprobe -r alx (if you had an alx that did not worked). My motherboard is MSI Z77A-G45 GAMING (MS-7752)

1. sudo modprobe -r alx. Do this if you have an existing alx loaded.
2. Download (checked the link provided by Chili just above this).
3. Extract the file. Right click, then Extract here.
4. cd Downloads/backports-3.13-1/
5. make defconfig-alx
If no errors, proceed to the next step. Otherwise, open a thread for your issue (I guess).
6. make
7. sudo make install
8. reboot

Sorry for the confusion Chili as am not really good in english (though I tried).

[SIZE=5]Thanks again Chili. More power to you and to Ubuntu.
[/SIZE]
Below was the cli events when I did it.

```
:~/Downloads/backports-3.13-1$ make defconfig-alx
cc -Wall -Wmissing-prototypes -Wstrict-prototypes -O2 -fomit-frame-pointer   -c -o conf.o conf.c
cc -Wall -Wmissing-prototypes -Wstrict-prototypes -O2 -fomit-frame-pointer   -c -o zconf.tab.o zconf.tab.c
cc   conf.o zconf.tab.o   -o conf
#
# configuration written to .config
#
:~/Downloads/backports-3.13-1$ 
:~/Downloads/backports-3.13-1$ make
make[5]: `conf' is up to date.
#
# configuration written to .config
#
Building backport-include/backport/autoconf.h ... done.
  CC [M]  /home/simpleboy/Downloads/backports-3.13-1/compat/main.o
  CC [M]  /home/simpleboy/Downloads/backports-3.13-1/compat/compat-3.9.o
  CC [M]  /home/simpleboy/Downloads/backports-3.13-1/compat/backport-3.10.o
  CC [M]  /home/simpleboy/Downloads/backports-3.13-1/compat/backport-3.12.o
  CC [M]  /home/simpleboy/Downloads/backports-3.13-1/compat/backport-3.13.o
  LD [M]  /home/simpleboy/Downloads/backports-3.13-1/compat/compat.o
  CC [M]  /home/simpleboy/Downloads/backports-3.13-1/drivers/net/ethernet/atheros/alx/main.o
  CC [M]  /home/simpleboy/Downloads/backports-3.13-1/drivers/net/ethernet/atheros/alx/ethtool.o
  CC [M]  /home/simpleboy/Downloads/backports-3.13-1/drivers/net/ethernet/atheros/alx/hw.o
  LD [M]  /home/simpleboy/Downloads/backports-3.13-1/drivers/net/ethernet/atheros/alx/alx.o
  Building modules, stage 2.
  MODPOST 2 modules
  CC      /home/simpleboy/Downloads/backports-3.13-1/compat/compat.mod.o
  LD [M]  /home/simpleboy/Downloads/backports-3.13-1/compat/compat.ko
  CC      /home/simpleboy/Downloads/backports-3.13-1/drivers/net/ethernet/atheros/alx/alx.mod.o
  LD [M]  /home/simpleboy/Downloads/backports-3.13-1/drivers/net/ethernet/atheros/alx/alx.ko
:~/Downloads/backports-3.13-1$ 
:~/Downloads/backports-3.13-1$ sudo make install
[sudo] password for simpleboy: 
  Building modules, stage 2.
  MODPOST 2 modules
  INSTALL /home/simpleboy/Downloads/backports-3.13-1/compat/compat.ko
Can't read private key
  INSTALL /home/simpleboy/Downloads/backports-3.13-1/drivers/net/ethernet/atheros/alx/alx.ko
Can't read private key
  DEPMOD  3.8.0-35-generic
depmod will prefer updates/ over kernel/ -- OK!
Note:
You may or may not need to update your initramfs, you should if
any of the modules installed are part of your initramfs. To add
support for your distribution to do this automatically send a
patch against "update-initramfs.sh". If your distribution does not
require this send a patch with the '/usr/bin/lsb_release -i -s'
("Ubuntu") tag for your distribution to avoid this warning.

Your backported driver modules should be installed now.
Reboot.

:~/Downloads/backports-3.13-1$ sudo init 6
```

---

### Post by chili555 on 2014-01-27
Glad it's working.

---

