---
title: "Add network drivers to Ubuntu 14.04 minimal installation"
date: 2017-06-12
forum: Networking &amp; Wireless
---

### Post by damianhlozano on 2017-06-12
Hello,
I am not sure about if it is the right place to set this thread
I just installed a Ubuntu minimal and everything was working fine, but when I connect the HD to other PC, I lost network connection, in /etc/network/interfaces does not appear any adapter ethx.  I think I will need to add networks drivers, but I want to install standard network drivers or generic drivers to make it Works in many different PCs, but I dont know how to accomplish that.
My original PC is not available now.
Any ideas?

Thanks in advance.
Regards,
Damián

---

### Post by slickymaster on 2017-06-12
*Thread moved to **Networking & Wireless*** for a better fit

---

### Post by damianhlozano on 2017-06-19
bump

---

### Post by QIII on 2017-06-19
Hello!

After a week, a thread settles to the bottom of the sea never to be seen again.  You would be better off to bump your thread at about 12 hours if you do not get a response.

Cheers!

---

### Post by damianhlozano on 2017-06-23
Anyone?

---

### Post by jeremy31 on 2017-06-23
Post results for ```
dpkg -l | grep linux-image
```

---

### Post by ian-weisser on 2017-06-23
> **damianhlozano said:**
> I want to install standard network drivers or generic drivers to make it Works in many different PCs, 

That's what a minimal install already does.
Perhaps your newer hardware does not have standard components compatible with those drivers?
Until you provide information about your hardware, that's a guess.

---

### Post by damianhlozano on 2017-06-27
Guys, thank for the reply
Jeremy, Why is that for?
Ian, I just need to clone a disk with Ubuntu to use it in many machines, but it seems that when I installed Ubuntu, it just installed drivers for current devices, so it doesnt work in other machines, I dont know the hardware, so I need basic drivers

---

### Post by chili555 on 2017-06-27
Minimal install includes drivers for, if I remember correctly, about ten network devices. Many, perhaps even most, computers have devices other than the ten or so and therefore will have no network connectivity until you install a complete suite of drivers.

Jeremy suspects, as do I, that minimal does not include linux-image-extra. You will confirm this when you run the command, we think. Jeremy will then suggest that you install the package matching your running kernel. 

From my machine, for comparison:```
ii  linux-image-extra-4.10.0-20-generic                         4.10.0-20.22                                amd64        Linux kernel extra modules for version 4.10.0 on 64 bit x86 SMP
ii  linux-image-extra-4.10.0-21-generic                         4.10.0-21.23                                amd64        Linux kernel extra modules for version 4.10.0 on 64 bit x86 SMP
ii  linux-image-extra-4.10.0-22-generic                         4.10.0-22.24                                amd64        Linux kernel extra modules for version 4.10.0 on 64 bit x86 SMP
ii  linux-image-extra-4.10.0-24-generic                         4.10.0-24.28                                amd64        Linux kernel extra modules for version 4.10.0 on 64 bit x86 SMP
<snip>
```

---

### Post by damianhlozano on 2017-06-28
Hi,
Thanks
I paste here the results:
```
ii  linux-image-3.13.0-119-generic       3.13.0-119.166                  amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-119-generic 3.13.0-119.166               amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-generic                  3.13.0.119.129                        amd64        Generic Linux kernel image
```

Install a Ubuntu Server without any additional feature will solve the issue?

Thanks again!
Regards

---

### Post by chili555 on 2017-06-28
> Install a Ubuntu Server without any additional feature will solve the issue?
Not perfectly. You will have, and probably have now, the needed drivers, but in a server, you will need to manually edit /etc/network/interfaces to get connected.

Let's see what Jeremy has to say.

---

### Post by damianhlozano on 2017-06-29
I have installed Ubuntu Server 16.04 with the same results, It Worked fine but when I connect the HD in other PC, Ubuntu Server do not recognize the network adapter
¿Any Idea?

---

### Post by damianhlozano on 2017-06-29
I just see your reply, I did not try to set manually the eth0 in /etc/network/interfaces

---

### Post by damianhlozano on 2017-06-29
I just tried adding those lines to /etc/network/interfaces:
auto eth0
allow-hotplug eth0
iface eth0 inet dhcp

That did not solve the issue, even after restart the PC
When I try "ifup eth0" I got the following error:
Cannot find device "eth0"
Error getting hardware address for eth0: No such device

---

### Post by vocx on 2017-06-29
> **damianhlozano said:**
> Guys, thank for the reply
Jeremy, Why is that for?
Ian, I just need to clone a disk with Ubuntu to use it in many machines, but it seems that when I installed Ubuntu, it just installed drivers for current devices, so it doesnt work in other machines, **I dont know the hardware, so I need basic drivers**
You cannot use "generic" or "basic" drivers for any computer. Hardware and operating systems don't work that way. Think about tires in a car. You cannot use the same tires for all cars in existence. Some tires may fit a variety of models, but others may not. The same with computers. Essentially all hardware devices need their own driver, but some may be essentially the same and work with the same kernel module.

If you install Ubuntu originally in computer A, and it has a wireless device W, Ubuntu will install the drivers for device W.

If you move the cloned system to computer B, and it has a wireless device X, Ubuntu will not have the drivers for device X ready, it will only have those for device W, as it was originally installed in computer A.

What you need to do is to install your Ubuntu in a machine B, with the device X. Then Ubuntu will set up the appropriate drivers, you will be able to clone the drive, and install it in identical machines B.

Usually Linux is smart enough to load the drivers for various devices as needed, that's what "plug and play" means. However, the fact that you cannot make it work so easily means that probably machine B has a device that needs the driver manually installed and configured, or some other trick.

It is not useful to edit "/etc/network/interfaces" with "eth0", or make some other configurations if you don't even know the hardware that you are using. In modern Linux, the network interface may no be called "eth0", or "wlan0", as it was common before. Nowadays, the interface may have another name such as "enp0s25", "enp1s15", "enp1s35", "wlp3s0", "wlp3s1", "wlp3s3", etc., so just moving the hard drive to another machine does not guarantee that it will be found by the same name.

Please go into machine A (originally installed) and B (to where you move the hard drive), run the commands, and post the results
```
lspci -nnk
lshw -c network
ifconfig
```

Also, you are using a kernel 3.13. That is an old kernel, that indicates you are probably using Ubuntu 14.04 or older. I would suggest you install 16.04, for a more recent kernel in the 4.4 series, which will provide hardware support to more devices.

---

### Post by damianhlozano on 2017-06-29
Vocx, thanks for your reply.
I understand what you said, I had the hope to easily install generic drivers because I remember that about 2 years ago, I installed an Ubuntu desktop 14.04 and I could clone the disk to other different computers without any problem.  Also I could do the same with a Centos 6.
It seems that desktop OSs have more drivers than minimall or server editions
I dont have the original PC where I installed the Ubuntu 14.04 minimal, but I have the PC where I instaled Ubuntu 16.04 Server (Other HD)
I could run these commands with the Ubuntu Server 16.04 in 2 different machines (1 of these, was where I installed the OS), in few minutes

Thanks again
Regards

---

### Post by damianhlozano on 2017-06-29
I will paste here the results, in the order that you asked, first in the machine where the OS (Ubuntu server 16.04) was installed, and after the other machine.
-----------------------------------------------------------------------
```
00:00.0 Host bridge [0600]: Intel Corporation 4 Series Chipset DRAM Controller [8086:2e30] (rev 03)
 Subsystem: Hewlett-Packard Company 4 Series Chipset DRAM Controller [103c:2a8c]
 Kernel driver in use: agpgart-intel
00:02.0 VGA compatible controller [0300]: Intel Corporation 4 Series Chipset Integrated Graphics Controller [8086:2e32] (rev 03)
 Subsystem: Hewlett-Packard Company 4 Series Chipset Integrated Graphics Controller [103c:2a8c]
 Kernel driver in use: i915
 Kernel modules: i915
00:1b.0 Audio device [0403]: Intel Corporation NM10/ICH7 Family High Definition Audio Controller [8086:27d8] (rev 01)
 Subsystem: Hewlett-Packard Company NM10/ICH7 Family High Definition Audio Controller [103c:2a8c]
 Kernel driver in use: snd_hda_intel
 Kernel modules: snd_hda_intel
00:1c.0 PCI bridge [0604]: Intel Corporation NM10/ICH7 Family PCI Express Port 1 [8086:27d0] (rev 01)
 Kernel driver in use: pcieport
 Kernel modules: shpchp
00:1c.1 PCI bridge [0604]: Intel Corporation NM10/ICH7 Family PCI Express Port 2 [8086:27d2] (rev 01)
 Kernel driver in use: pcieport
 Kernel modules: shpchp
00:1d.0 USB controller [0c03]: Intel Corporation NM10/ICH7 Family USB UHCI Controller #1 [8086:27c8] (rev 01)
 Subsystem: Hewlett-Packard Company NM10/ICH7 Family USB UHCI Controller [103c:2a8c]
 Kernel driver in use: uhci_hcd
00:1d.1 USB controller [0c03]: Intel Corporation NM10/ICH7 Family USB UHCI Controller #2 [8086:27c9] (rev 01)
 Subsystem: Hewlett-Packard Company NM10/ICH7 Family USB UHCI Controller [103c:2a8c]
 Kernel driver in use: uhci_hcd
00:1d.2 USB controller [0c03]: Intel Corporation NM10/ICH7 Family USB UHCI Controller #3 [8086:27ca] (rev 01)
 Subsystem: Hewlett-Packard Company NM10/ICH7 Family USB UHCI Controller [103c:2a8c]
 Kernel driver in use: uhci_hcd
00:1d.3 USB controller [0c03]: Intel Corporation NM10/ICH7 Family USB UHCI Controller #4 [8086:27cb] (rev 01)
 Subsystem: Hewlett-Packard Company NM10/ICH7 Family USB UHCI Controller [103c:2a8c]
 Kernel driver in use: uhci_hcd
00:1d.7 USB controller [0c03]: Intel Corporation NM10/ICH7 Family USB2 EHCI Controller [8086:27cc] (rev 01)
 Subsystem: Hewlett-Packard Company NM10/ICH7 Family USB2 EHCI Controller [103c:2a8c]
 Kernel driver in use: ehci-pci
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev e1)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge [8086:27b8] (rev 01)
 Subsystem: Hewlett-Packard Company 82801GB/GR (ICH7 Family) LPC Interface Bridge [103c:2a8c]
 Kernel driver in use: lpc_ich
 Kernel modules: intel_rng, lpc_ich, leds_ss4200
00:1f.1 IDE interface [0101]: Intel Corporation 82801G (ICH7 Family) IDE Controller [8086:27df] (rev 01)
 Subsystem: Hewlett-Packard Company 82801G (ICH7 Family) IDE Controller [103c:2a8c]
 Kernel driver in use: ata_piix
 Kernel modules: pata_acpi
00:1f.2 IDE interface [0101]: Intel Corporation NM10/ICH7 Family SATA Controller [IDE mode] [8086:27c0] (rev 01)
 Subsystem: Hewlett-Packard Company NM10/ICH7 Family SATA Controller [IDE mode] [103c:2a8c]
 Kernel driver in use: ata_piix
 Kernel modules: pata_acpi
00:1f.3 SMBus [0c05]: Intel Corporation NM10/ICH7 Family SMBus Controller [8086:27da] (rev 01)
 Subsystem: Hewlett-Packard Company NM10/ICH7 Family SMBus Controller [103c:2a8c]
 Kernel modules: i2c_i801
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [10ec:8136] (rev 02)
 Subsystem: Hewlett-Packard Company RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [103c:2a8c]
 Kernel driver in use: r8169
 Kernel modules: r8169

-----------------------------------------------------------------------
-----------------------------------------------------------------------
  *-network
       description: Ethernet interface
       product: RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: ens33
       version: 02
       serial: 78:ac:c0:ab:3f:3a
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.0.188 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:26 ioport:e800(size=256) memory:febff000-febfffff memory:fdff0000-fdffffff memory:febc0000-febdffff

-----------------------------------------------------------------------
-----------------------------------------------------------------------
ens33     Link encap:Ethernet  direcciónHW 78:ac:c0:ab:3f:3a  
          Direc. inet:192.168.0.188  Difus.:192.168.0.255  Másc:255.255.255.0
          Dirección inet6: fe80::7aac:c0ff:feab:3f3a/64 Alcance:Enlace
          ACTIVO DIFUSIÓN FUNCIONANDO MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:2313 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:37 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:1000 
          Bytes RX:169514 (169.5 KB)  TX bytes:3309 (3.3 KB)
lo        Link encap:Bucle local  
          Direc. inet:127.0.0.1  Másc:255.0.0.0
          Dirección inet6: ::1/128 Alcance:Anfitrión
          ACTIVO BUCLE FUNCIONANDO  MTU:65536  Métrica:1
          Paquetes RX:160 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:160 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:1 
          Bytes RX:11840 (11.8 KB)  TX bytes:11840 (11.8 KB)
 
-----------------------------------------------------------------------
-----------------------------------------------------------------------
00:00.0 Host bridge [0600]: Intel Corporation 4 Series Chipset DRAM Controller [8086:2e20] (rev 03)
 Subsystem: Hewlett-Packard Company 4 Series Chipset DRAM Controller [103c:3664]
 Kernel driver in use: agpgart-intel
00:02.0 VGA compatible controller [0300]: Intel Corporation 4 Series Chipset Integrated Graphics Controller [8086:2e22] (rev 03)
 Subsystem: Hewlett-Packard Company 4 Series Chipset Integrated Graphics Controller [103c:3664]
 Kernel driver in use: i915
 Kernel modules: i915
00:02.1 Display controller [0380]: Intel Corporation 4 Series Chipset Integrated Graphics Controller [8086:2e23] (rev 03)
 Subsystem: Hewlett-Packard Company 4 Series Chipset Integrated Graphics Controller [103c:3664]
00:1a.0 USB controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4 [8086:3a37]
 Subsystem: Hewlett-Packard Company 82801JI (ICH10 Family) USB UHCI Controller [103c:3664]
 Kernel driver in use: uhci_hcd
00:1a.1 USB controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5 [8086:3a38]
 Subsystem: Hewlett-Packard Company 82801JI (ICH10 Family) USB UHCI Controller [103c:3664]
 Kernel driver in use: uhci_hcd
00:1a.2 USB controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #6 [8086:3a39]
 Subsystem: Hewlett-Packard Company 82801JI (ICH10 Family) USB UHCI Controller [103c:3664]
 Kernel driver in use: uhci_hcd
00:1a.7 USB controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2 [8086:3a3c]
 Subsystem: Hewlett-Packard Company 82801JI (ICH10 Family) USB2 EHCI Controller [103c:3664]
 Kernel driver in use: ehci-pci
00:1b.0 Audio device [0403]: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller [8086:3a3e]
 Subsystem: Hewlett-Packard Company 82801JI (ICH10 Family) HD Audio Controller [103c:3664]
 Kernel driver in use: snd_hda_intel
 Kernel modules: snd_hda_intel
00:1c.0 PCI bridge [0604]: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 1 [8086:3a40]
 Kernel driver in use: pcieport
 Kernel modules: shpchp
00:1c.1 PCI bridge [0604]: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 2 [8086:3a42]
 Kernel driver in use: pcieport
 Kernel modules: shpchp
00:1d.0 USB controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1 [8086:3a34]
 Subsystem: Hewlett-Packard Company 82801JI (ICH10 Family) USB UHCI Controller [103c:3664]
 Kernel driver in use: uhci_hcd
00:1d.1 USB controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2 [8086:3a35]
 Subsystem: Hewlett-Packard Company 82801JI (ICH10 Family) USB UHCI Controller [103c:3664]
 Kernel driver in use: uhci_hcd
00:1d.2 USB controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3 [8086:3a36]
 Subsystem: Hewlett-Packard Company 82801JI (ICH10 Family) USB UHCI Controller [103c:3664]
 Kernel driver in use: uhci_hcd
00:1d.7 USB controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1 [8086:3a3a]
 Subsystem: Hewlett-Packard Company 82801JI (ICH10 Family) USB2 EHCI Controller [103c:3664]
 Kernel driver in use: ehci-pci
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev 90)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801JIR (ICH10R) LPC Interface Controller [8086:3a16]
 Subsystem: Hewlett-Packard Company 82801JIR (ICH10R) LPC Interface Controller [103c:3664]
 Kernel driver in use: lpc_ich
 Kernel modules: lpc_ich
00:1f.2 SATA controller [0106]: Intel Corporation 82801JI (ICH10 Family) SATA AHCI Controller [8086:3a22]
 Subsystem: Hewlett-Packard Company 82801JI (ICH10 Family) SATA AHCI Controller [103c:3664]
 Kernel driver in use: ahci
 Kernel modules: ahci
00:1f.3 SMBus [0c05]: Intel Corporation 82801JI (ICH10 Family) SMBus Controller [8086:3a30]
 Subsystem: Hewlett-Packard Company 82801JI (ICH10 Family) SMBus Controller [103c:3664]
 Kernel modules: i2c_i801
01:00.0 Network controller [0280]: Qualcomm Atheros AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
 Subsystem: Qualcomm Atheros AR9285 Wireless Network Adapter (PCI-Express) [168c:30a1]
 Kernel driver in use: ath9k
 Kernel modules: ath9k
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 03)
 Subsystem: Hewlett-Packard Company RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [103c:3664]
 Kernel driver in use: r8169
 Kernel modules: r8169

-----------------------------------------------------------------------
-----------------------------------------------------------------------
  *-network DISABLED
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wlp1s0
       version: 01
       serial: 90:f6:52:d5:1e:f5
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=4.4.0-62-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:16 memory:feaf0000-feafffff
  *-network DISABLED
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: enp2s0
       version: 03
       serial: 40:61:86:f6:6d:d1
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full latency=0 link=no multicast=yes port=MII speed=100Mbit/s
       resources: irq:26 ioport:e800(size=256) memory:febff000-febfffff memory:fdffc000-fdffffff memory:febc0000-febdffff

-----------------------------------------------------------------------
-----------------------------------------------------------------------
lo        Link encap:Bucle local  
          Direc. inet:127.0.0.1  Másc:255.0.0.0
          Dirección inet6: ::1/128 Alcance:Anfitrión
          ACTIVO BUCLE FUNCIONANDO  MTU:65536  Métrica:1
          Paquetes RX:1120 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:1120 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:1 
          Bytes RX:82880 (82.8 KB)  TX bytes:82880 (82.8 KB)
```

---

### Post by damianhlozano on 2017-06-29
Nice commands, I didnt know
Maybe I should config "enp2s0" on /network/interfaces, instead of eth0
I will try soon

---

### Post by damianhlozano on 2017-06-29
Ok, solved, thanks a lot
It was not a driver issue, I dont know why desktop versions configure automatically "/etc/network/interfaces" file and Ubuntu server or Ubuntu minimal does not
I could do this work with Ubuntu server, configuring manually the "/etc/network/interfaces" file

---

### Post by chili555 on 2017-06-29
>  I dont know why desktop versions configure automatically "/etc/network/interfaces" file It does not. It uses Network Manager that does all the work. In most desktop installs, including mine, /etc/network/interfaces says:```
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback
```

---

### Post by vocx on 2017-06-29
> **damianhlozano said:**
> Nice commands, I didnt know
Maybe I should config "enp2s0" on /network/interfaces, instead of eth0
I will try soon

Whenever you post terminal output in this forum please use "```
" tags, which means surrounding the text with the word CODE inside brackets. You have an opening tag and a closing tag. For example
[PHP]
[CODE]
lshw -c network

```
[/PHP]

```

*-network
       description: Ethernet interface
       product: RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: ens33
       version: 02
       serial: 78:ac:c0:ab:3f:3a
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.0.188 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:26 ioport:e800(size=256) memory:febff000-febfffff memory:fdff0000-fdffffff memory:febc0000-febdffff

```

As you can see, in one machine the network interface is called "ens33", and in the other it's called "enp2s0". The different names are because the devices are physically in different buses in the different computers. More information can be found online [https://askubuntu.com/questions/689070/network-interface-name-changes-after-update-to-15-10-udev-changes](https://askubuntu.com/questions/689070/network-interface-name-changes-after-update-to-15-10-udev-changes)  This is a new naming convention basically.

Yes, a minimal or server install typically is for advanced users who know exactly what they want to install, and how to install it. For most users the desktop install produces a working system without needing much configuration.

As chili55 mentioned, probably the minimal install doesn't include "network-manager" to manage Internet connectivity. I guess you could still edit the interfaces file directly and configure the network that way, but network-manager is supposed to facilitate this process, and it is what the desktop installations normally use. It's up to you, depending on your needs, whether you want a really minimal install, or minimal with some utilities.
```
sudo apt install network-manager
```

---

### Post by damianhlozano on 2017-06-30
Thanks guys,
Now I have another related issue:
I had installed Ubuntu minimal in PC1 and worked
After that, I had installed Ubuntu Server in PC2 and worked, then I could make it work (With the same disk) in PC3 with your help
Now, PC1 is not available
I connected HD with Ubuntu minimal to PC2 and didnt work, I configured the /etc/network/interfaces with the logical name
I cannot install network-manager, unless I make it work in any Machine
How can I see which is the problem? How can I see if Ubuntu minimal has drivers for this network adapter?

Thanks

---

### Post by chili555 on 2017-06-30
> I configured the /etc/network/interfaces with the logical nameWith the logical name that you confirmed?```
ifconfig
```For example, from my machine:```
chili@T440p:~$ ifconfig
[COLOR="#FF0000"]enp0s25[/COLOR]: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        etherxx:f7:28:ae:83:xx  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
        device interrupt 20  memory 0xf0600000-f0620000  

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 642  bytes 42524 (42.5 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 642  bytes 42524 (42.5 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
```So, in my case, I'd populate the interfaces file with:```
auto lo
iface lo inet loopback

auto enp0s25
iface enp0s25 inet dhcp
```Then I'd either reboot or restart the interface:```
sudo ifdown enp0s25 && sudo ifup -v enp0s25
```I'd watch the terminal output to see if there is either a problem or the interface gets an IP address, If it does, I'd test:```
ping -c3 8.8.8.8
ping -c3 www.ubuntu.com
```If I get ping returns in both cases, I'd open a cold beverage and call it a day!

---

### Post by vocx on 2017-06-30
> **damianhlozano said:**
> Thanks guys,
Now I have another related issue:
I had installed Ubuntu minimal in PC1 and worked
After that, I had installed Ubuntu Server in PC2 and worked, then I could make it work (With the same disk) in PC3 with your help
Now, PC1 is not available
I connected HD with Ubuntu minimal to PC2 and didnt work, I configured the /etc/network/interfaces with the logical name
I cannot install network-manager, unless I make it work in any Machine
How can I see which is the problem? How can I see if Ubuntu minimal has drivers for this network adapter?

Thanks

If I understand your question correctly, you have the following case:
```

PC1
- Physical computer: no
- Hard drive: yes
- Internet: no

PC2
- Physical computer: yes
- Hard drive: yes
- Internet: yes

PC3
- Physical computer: yes
- Hard drive: yes
- Internet: yes

```
What you want is to move the hard drive of PC1 to PC2, in order to upgrade it. However, as the hard drive of PC1 was installed in a computer that you physically don't have any more, it does not have the appropriate drivers for the hardware of PC2.

In your previous posts, you pasted the output of "lscpi" and "lshw". I believe this is for PC2.
```

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [10ec:8136] (rev 02)
 Subsystem: Hewlett-Packard Company **RTL8101/2/6E** PCI Express Fast/Gigabit Ethernet controller [103c:2a8c]
 **Kernel driver in use: r8169**
 Kernel modules: r8169

-----------------------------------------------------------------------
  *-network
       description: Ethernet interface
       product:** RTL8101/2/6E** PCI Express Fast/Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: ens33
       version: 02
       serial: 78:ac:c0:ab:3f:3a
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes **driver=r8169** driverversion=2.3LK-NAPI duplex=full ip=192.168.0.188 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:26 ioport:e800(size=256) memory:febff000-febfffff memory:fdff0000-fdffffff memory:febc0000-febdffff

```

I believe this is for PC3.
```

01:00.0 Network controller [0280]: Qualcomm Atheros AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
 Subsystem: Qualcomm Atheros AR9285 Wireless Network Adapter (PCI-Express) [168c:30a1]
 Kernel driver in use: ath9k
 Kernel modules: ath9k
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 03)
 Subsystem: Hewlett-Packard Company **RTL8111/8168/8411** PCI Express Gigabit Ethernet Controller [103c:3664]
** Kernel driver in use: r8169**
 Kernel modules: r8169

-----------------------------------------------------------------------
  *-network DISABLED
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wlp1s0
       version: 01
       serial: 90:f6:52:d5:1e:f5
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=4.4.0-62-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:16 memory:feaf0000-feafffff
  *-network DISABLED
       description: Ethernet interface
       product: **RTL8111/8168/8411** PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: enp2s0
       version: 03
       serial: 40:61:86:f6:6d:d1
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes **driver=r8169** driverversion=2.3LK-NAPI duplex=full latency=0 link=no multicast=yes port=MII speed=100Mbit/s
       resources: irq:26 ioport:e800(size=256) memory:febff000-febfffff memory:fdffc000-fdffffff memory:febc0000-febdffff

```

Since both PC2 and PC3 are using similar Realtek Ethernet cards, they both use the same "r8169" driver. Thus when you moved the hard drive from PC2 to PC3, it was possible to make it work. Is this right?

So, it seems you need to have the same driver "r8169" installed in the hard drive of PC1 for it to work when you move the drive to PC2 or PC3.

According to this guide [https://unixblogger.com/2016/08/11/how-to-get-your-realtek-rtl8111rtl8168-working-updated-guide/](https://unixblogger.com/2016/08/11/how-to-get-your-realtek-rtl8111rtl8168-working-updated-guide/), it seems you should be using the "r8168" driver, which is not open source, and a bit of a headache. If it does not find that driver, the kernel uses the "r8169" driver, which is what you have currently. So you need to install at least "r8169" in PC1, and later on, you can decide to install "r8168" in all three PC1, PC2, PC3, if you wish.

In my computer if I use the command
```

modinfo r8169

```

It gives me the location of the kernel module
```

filename:       /lib/modules/4.4.0-83-generic/kernel/drivers/net/ethernet/realtek/r8169.ko
firmware:       rtl_nic/rtl8107e-2.fw
firmware:       rtl_nic/rtl8107e-1.fw
firmware:       rtl_nic/rtl8168h-2.fw
firmware:       rtl_nic/rtl8168h-1.fw
firmware:       rtl_nic/rtl8168g-3.fw
firmware:       rtl_nic/rtl8168g-2.fw
firmware:       rtl_nic/rtl8106e-2.fw
firmware:       rtl_nic/rtl8106e-1.fw
firmware:       rtl_nic/rtl8411-2.fw
firmware:       rtl_nic/rtl8411-1.fw
firmware:       rtl_nic/rtl8402-1.fw
firmware:       rtl_nic/rtl8168f-2.fw
firmware:       rtl_nic/rtl8168f-1.fw
firmware:       rtl_nic/rtl8105e-1.fw
firmware:       rtl_nic/rtl8168e-3.fw
firmware:       rtl_nic/rtl8168e-2.fw
firmware:       rtl_nic/rtl8168e-1.fw
firmware:       rtl_nic/rtl8168d-2.fw
firmware:       rtl_nic/rtl8168d-1.fw
version:        2.3LK-NAPI
license:        GPL
description:    RealTek RTL-8169 Gigabit Ethernet driver
...

```

You could try copying these files from PC2 or PC3 to the hard drive of PC1.

The single "r8169.ko" file is the kernel module, which is under the "/lib/modules/" as shown above.
You also need the firmware files, which are under "/lib/firmware/rtl_nic/" as shown above.

Now, as you see, the modules depend on the kernel version, in my case this is "4.4.0-83-generic". If you have different kernels in PC1, say 4.2, and in PC2, say 4.8, just copying the module and firmware files from one computer to the other may not work. The best way to get the files is to upgrade the kernel of PC1. You should install a recent kernel with the most up to date drivers for your Ubuntu version.

When you use
```

uname -r

```

it will tell you the kernel
```

4.4.0-83-generic

```

You need to use PC2, or another computer with internet access, to download a ".deb" file with the most recent kernel for PC1.

All packages for all versions of Ubuntu are in [https://packages.ubuntu.com/](https://packages.ubuntu.com/) The package for the kernel is called "linux-image-4.4.0-83-generic" or similar.

You download it in PC2, but you have to move it to PC1, and install it there.
```

sudo dpkg -i linux-image-4.4.0-83-generic.deb
sudo dpkg -i linux-image-extra-4.4.0-83-generic.deb
sudo dpkg -i linux-firmware_1.157.11.deb

```

You should also download and install the packages for "linux-image-extra" and "linux-firmware", again, for the specific version of Ubuntu in PC1, not PC2.

---

### Post by damianhlozano on 2017-07-03
Sorry, I just read your reply vocx.
What you think is correct.
Now it seems a driver issue, and I am wondering again, why I never had a problem by moving an HD with Ubuntu desktop to another machine.  Is network-manager the solution? What does it make? Does it install drivers in offline machines?
If network-manager is the solution, I can format an HD, install Ubuntu minimal and add network-manager to it before move the disk

---

### Post by vocx on 2017-07-03
> **damianhlozano said:**
> Sorry, I just read your reply vocx.
What you think is correct.
Now it seems a driver issue, and I am wondering again, why I never had a problem by moving an HD with **Ubuntu desktop to another machine**.  Is network-manager the solution? What does it make? Does it install drivers in offline machines?
If network-manager is the solution, I can format an HD, install Ubuntu minimal and add network-manager to it before move the disk
Eh, I think you are missing the point. This was already mentioned before in the thread.

> **chili555 said:**
> Minimal install includes drivers for, if I remember correctly, about ten network devices. Many, perhaps even most, computers have devices other than the ten or so and therefore will have no network connectivity until you install a complete suite of drivers.

The program "network-manager" just manages the network connections with a router, so that you don't have to configure manually the "interfaces" file, or "wpa_supplicant", which specify details such as network IP, mask, security, etc. It does not provide the wireless drivers. The wireless drivers come with the Linux kernel, these are all the ".ko" files inside the /lib/modules directory.

When people install a normal desktop distribution, it has a large collection of kernel modules for many types of hardware, so the system is ready to run with many different computers. When you install a minimal or server install, probably it only has some very common drivers for a few computers, as they focus on a lightweight system.

So, it's not the fact that network-manager was installed, but rather that a full collection of kernel modules were installed. Did you try what I outlined in the previous post? If you install the complete kernel in the minimal or server installs, you will probably see that you have more kernel modules, and probably your Ethernet connection will work as you want, even when moving the hard driver to different computers.

---

### Post by ian-weisser on 2017-07-03
> **damianhlozano said:**
>  I am wondering again, why I never had a problem by moving an HD with Ubuntu desktop to another machine.

Quite simply: You got lucky. Your new hardware happened to be compatible with the kernel modules installed in the HDD. I've been lucky, too. With ethernet, most compatible hardware is covered by just a few modules (drivers). Most...but not all.

This time, you were not lucky. I have also been unlucky.

---

### Post by damianhlozano on 2017-07-03
Vocx, I didnt try, I will try soon, thanks
Ian-weisser, you are wrong

---

### Post by chili555 on 2017-07-03
There are two or maybe more issues here. First, is the minimal install iso. As I said before:> Minimal install includes drivers for, if I remember correctly, about ten network devices.If you do a minimal install on a server, it is quite likely to have an ethernet card with one of the ten or so. You are golden.

If you transfer that HDD to another computer, it may or may not have one of the ten or so. Maybe it works, therefore, and maybe it doesn't.

The other issue is the subject of simply moving an HDD from one computer to another. If it is a full install, not minimal, it includes driver for, depending on the kernel version, drivers for dozens and dozens of network devices. Your chance of success is therefore quite high. I have done this myself many times and my success rate is 100%. It is not because I have the golden touch or because I am the wireless whisperer, but because before I ever buy a computer with a network device, not just wireless, I make double-dog sure that it is fully supported in Linux.

There are, however, still network devices that require human intervention to get (especially wireless) working; most particularly Broadcoms.

The answer as to whether you can get internet connectivity without fail in a minimal install is maybe. The answer as to whether you can get internet connectivity without fail in a full install by swapping HDDs is probably. The answer as to whether you can get internet connectivity without fail in any fashion is that you cannot without analyzing the hardware and, in a few cases, taking extra steps.

Unless the hardware is controlled and the hardware and operating system are bundled, e.g. Apple and Chrome, it is impossible for any operation system to be all things to all hardware at all times.

---

### Post by damianhlozano on 2017-07-04
Thanks Chili,
I understand and I agree, I just want to install all drivers that are installed in Ubuntu desktop, in a Ubuntu minimal
Is the following enought?
```

sudo dpkg -i linux-image-4.4.0-83-generic.deb
sudo dpkg -i linux-image-extra-4.4.0-83-generic.deb
sudo dpkg -i linux-firmware_1.157.11.deb

```

---

### Post by chili555 on 2017-07-04
> **damianhlozano said:**
> Thanks Chili,
I understand and I agree, I just want to install all drivers that are installed in Ubuntu desktop, in a Ubuntu minimal
Is the following enought?
```

sudo dpkg -i linux-image-4.4.0-83-generic.deb
sudo dpkg -i linux-image-extra-4.4.0-83-generic.deb
sudo dpkg -i linux-firmware_1.157.11.deb

```It should, although I have a few caveats. First, although I usually try to test before I answer, I haven't done this previously. However, when I extract the linux-image-extra package, it contains the expected dozens and dozens of network drivers.

Second, there may also be a minor dependency or two. I'd try it as you outline first to find out. It is a simple matter to get the missing dependencies here: [https://packages.ubuntu.com/](https://packages.ubuntu.com/)

Finally, there is a newer firmware package that I suggest instead of 1.157: [http://mirrors.kernel.org/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.164_all.deb](http://mirrors.kernel.org/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.164_all.deb)

Post back and let us and the searchers know how it goes.

---

