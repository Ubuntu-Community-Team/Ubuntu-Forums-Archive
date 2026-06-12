---
title: "Realtec 8139 NIC can't connect"
date: 2005-09-09
forum: Networking &amp; Wireless
---

### Post by TeleTommy on 2005-09-09
Hi!

I have a mysterious networking problem with either Hoary 5.04 and breezy 5.10.
The built-in NIC Realtec 8139 can't connect to my network. DHCP gets no answer and manually configuration doesn't work too. Configuring is no problem but pinging the router afterwards doesn't work.
Using Windows and other Linux Distros this was never a problem.

I saw that two modules are loaded with system start:
8139too
8139cp

with other linux distros there where only 8139too loaded and it worked fine.
Is it possible that the two both are active and muddle the system?
Can this be the problem? How can i get rid of the 8139cp driver?

I'm very thankful for any hints to solve the problem.

Thank you,
Thomas

---

### Post by Steve1961 on 2005-09-09
I think you should be able to remove the module by typing sudo rmmod 8139cp

---

### Post by TeleTommy on 2005-09-09
removing works, but has no effect. How do i remove it permanently from booting?
It seems to me that the NIC does not recognizes the cable...

i post some outputs:
eth0 ist the affected interface.

Thank you!


```
thecker@thomas-asus:~$ s[COLOR=Red]udo dhclient eth0[/COLOR]
Internet Systems Consortium DHCP Client V3.0.1
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/eth0/00:0e:a6:28:a6:83
Sending on   LPF/eth0/00:0e:a6:28:a6:83
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```


[COLOR=Red]thecker@thomas-asus:~$ dmesg[/COLOR]
eady [0x1][0x700300]
codec_semaphore: semaphore is not ready [0x1][0x700300]
codec_semaphore: semaphore is not ready [0x1][0x700300]
codec_semaphore: semaphore is not ready [0x1][0x700300]
codec_semaphore: semaphore is not ready [0x1][0x700300]
codec_semaphore: semaphore is not ready [0x1][0x700300]
codec_semaphore: semaphore is not ready [0x1][0x700300]
codec_semaphore: semaphore is not ready [0x1][0x700300]
codec_semaphore: semaphore is not ready [0x1][0x700300]
codec_semaphore: semaphore is not ready [0x1][0x700300]
intel8x0_measure_ac97_clock: measured 49203 usecs
intel8x0: clocking to 48000
Linux Kernel Card Services
  options:  [pci] [cardbus] [pm]
ACPI: PCI interrupt 0000:01:03.0[A] -> GSI 5 (level, low) -> IRQ 5
Yenta: CardBus bridge found at 0000:01:03.0 [1043:1754]
Yenta: ISA IRQ mask 0x0000, PCI irq 5
Socket status: 30000006
ACPI: PCI interrupt 0000:01:03.1[B] -> GSI 5 (level, low) -> IRQ 5
Yenta: CardBus bridge found at 0000:01:03.1 [1043:1754]
Yenta: ISA IRQ mask 0x0000, PCI irq 5
Socket status: 30000006
ohci1394: $Rev: 1223 $ Ben Collins <bcollins@debian.org>
ACPI: PCI interrupt 0000:01:03.2[C] -> GSI 5 (level, low) -> IRQ 5
ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[5]  MMIO=[ff7ef000-ff7ef7ff]  Max Packet=[2048]
8139too Fast Ethernet driver 0.9.27
ACPI: PCI interrupt 0000:01:04.0[A] -> GSI 5 (level, low) -> IRQ 5
eth0: RealTek RTL8139 at 0xc800, 00:0e:a6:28:a6:83, IRQ 5
eth0:  Identified 8139 chip type 'RTL-8101'
8139cp: 10/100 PCI Ethernet driver v1.2 (Mar 22, 2004)
ieee80211_crypt: registered algorithm 'NULL'
ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 0.19
ipw2200: Copyright(c) 2003-2004 Intel Corporation
ACPI: PCI interrupt 0000:01:05.0[A] -> GSI 5 (level, low) -> IRQ 5
ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00e01800031472b4]
NET: Registered protocol family 17
codec_semaphore: semaphore is not ready [0x1][0x700300]
codec_write 0: semaphore is not ready for register 0x2
Asus Laptop ACPI Extras version 0.29
  M2N model detected, supported
ACPI: AC Adapter [AC0] (off-line)
ACPI: Battery Slot [BAT0] (battery present)
ACPI: Power Button (FF) [PWRF]
ACPI: Sleep Button (CM) [SLPB]
ACPI: Lid Switch [LID]
[drm] Initialized drm 1.0.0 20040925
ACPI: PCI interrupt 0000:00:02.0[A] -> GSI 5 (level, low) -> IRQ 5
[drm] Initialized i915 1.2.0 20040405 on minor 0: Intel Corp. 82852/855GM Integrated Graphics Device
[drm] Initialized i915 1.2.0 20040405 on minor 1: Intel Corp. 82852/855GM Integrated Graphics Device (#2)
mtrr: base(0xf0020000) is not aligned on a size(0x300000) boundary
ibm_acpi: ec object not found
ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
apm: overridden by ACPI.
cs: IO port probe 0x0100-0x04ff: excluding 0x4d0-0x4d7
cs: IO port probe 0x0800-0x08ff: clean.
cs: IO port probe 0x0c00-0x0cff: clean.
cs: IO port probe 0x0a00-0x0aff: clean.
NET: Registered protocol family 10
Disabled Privacy Extensions on device c02f0500(lo)
IPv6 over IPv4 tunneling driver
eth1: no IPv6 routers present
eth0: link down
eth0: no IPv6 routers present

[COLOR=Red]thecker@thomas-asus:~$ lspci[/COLOR]
0000:00:00.0 Host bridge: Intel Corp. 82852/855GM Host Bridge (rev 02)
0000:00:00.1 System peripheral: Intel Corp. 855GM/GME GMCH Memory I/O Control Re gisters (rev 02)
0000:00:00.3 System peripheral: Intel Corp. 855GM/GME GMCH Configuration Process  Registers (rev 02)
0000:00:02.0 VGA compatible controller: Intel Corp. 82852/855GM Integrated Graph ics Device (rev 02)
0000:00:02.1 Display controller: Intel Corp. 82852/855GM Integrated Graphics Dev ice (rev 02)
0000:00:1d.0 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) US B UHCI Controller #1 (rev 03)
0000:00:1d.1 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) US B UHCI Controller #2 (rev 03)
0000:00:1d.2 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) US B UHCI Controller #3 (rev 03)
0000:00:1d.7 USB Controller: Intel Corp. 82801DB/DBM (ICH4/ICH4-M) USB 2.0 EHCI Controller (rev 03)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev 83)
0000:00:1f.0 ISA bridge: Intel Corp. 82801DBM LPC Interface Controller (rev 03)
0000:00:1f.1 IDE interface: Intel Corp. 82801DBM (ICH4) Ultra ATA Storage Contro ller (rev 03)
0000:00:1f.3 SMBus: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Contr oller (rev 03)
0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4 -L/ICH4-M) AC'97 Audio Controller (rev 03)
0000:00:1f.6 Modem: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem  Controller (rev 03)
0000:01:03.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev a9)
0000:01:03.1 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev a9)
0000:01:03.2 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev  01)
0000:01:04.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C /8139C+ (rev 10)
0000:01:05.0 Network controller: Intel Corp. PRO/Wireless 2200BG (rev 05)
thecker@thomas-asus:~$ lspci
0000:00:00.0 Host bridge: Intel Corp. 82852/855GM Host Bridge (rev 02)
0000:00:00.1 System peripheral: Intel Corp. 855GM/GME GMCH Memory I/O Control Registers (rev 02 )
0000:00:00.3 System peripheral: Intel Corp. 855GM/GME GMCH Configuration Process Registers (rev  02)
0000:00:02.0 VGA compatible controller: Intel Corp. 82852/855GM Integrated Graphics Device (rev  02)
0000:00:02.1 Display controller: Intel Corp. 82852/855GM Integrated Graphics Device (rev 02)
0000:00:1d.0 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controll er #1 (rev 03)
0000:00:1d.1 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controll er #2 (rev 03)
0000:00:1d.2 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controll er #3 (rev 03)
0000:00:1d.7 USB Controller: Intel Corp. 82801DB/DBM (ICH4/ICH4-M) USB 2.0 EHCI Controller (rev  03)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev 83)
0000:00:1f.0 ISA bridge: Intel Corp. 82801DBM LPC Interface Controller (rev 03)
0000:00:1f.1 IDE interface: Intel Corp. 82801DBM (ICH4) Ultra ATA Storage Controller (rev 03)
0000:00:1f.3 SMBus: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'9 7 Audio Controller (rev 03)
0000:00:1f.6 Modem: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (re v 03)
0000:01:03.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev a9)
0000:01:03.1 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev a9)
0000:01:03.2 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 01)
0000:01:04.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10 )
0000:01:05.0 Network controller: Intel Corp. PRO/Wireless 2200BG (rev 05)
thecker@thomas-asus:~$ lspci
0000:00:00.0 Host bridge: Intel Corp. 82852/855GM Host Bridge (rev 02)
0000:00:00.1 System peripheral: Intel Corp. 855GM/GME GMCH Memory I/O Control Registers (rev 02)
0000:00:00.3 System peripheral: Intel Corp. 855GM/GME GMCH Configuration Process Registers (rev 02)
0000:00:02.0 VGA compatible controller: Intel Corp. 82852/855GM Integrated Graphics Device (rev 02)
0000:00:02.1 Display controller: Intel Corp. 82852/855GM Integrated Graphics Device (rev 02)
0000:00:1d.0 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)0000:00:1d.1 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)0000:00:1d.2 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)0000:00:1d.7 USB Controller: Intel Corp. 82801DB/DBM (ICH4/ICH4-M) USB 2.0 EHCI Controller (rev 03)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev 83)
0000:00:1f.0 ISA bridge: Intel Corp. 82801DBM LPC Interface Controller (rev 03)
0000:00:1f.1 IDE interface: Intel Corp. 82801DBM (ICH4) Ultra ATA Storage Controller (rev 03)
0000:00:1f.3 SMBus: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
0000:00:1f.6 Modem: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
0000:01:03.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev a9)
0000:01:03.1 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev a9)
0000:01:03.2 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 01)
0000:01:04.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0000:01:05.0 Network controller: Intel Corp. PRO/Wireless 2200BG (rev 05)

---

### Post by Steve1961 on 2005-09-09
You can stop the driver loading at startup by editing the modules file.  Just type sudo gedit /etc/modules and remove the entry.

I'm still relatively new to this myself but in the output you've pasted you seem to have a wireless card and a network card.  I've had problems in the past getting my ethernet to pick up an IP address from the router until I disabled the wireless card in the bios.  Might be worth a try.

---

### Post by TeleTommy on 2005-09-09
The module isn't listed in the /etc/modules file... why is it loaded?

deactivating the card in bios would be very unpractical because i want to use it too fo r university. it runs with other distros...

---

### Post by Steve1961 on 2005-09-09
Good question, and not one I know the answer to.  Sorry.  Can anyone else cast some light on this problem please?

---

### Post by mo_x on 2005-09-09
Maybe it is loaded by hotplug. You can add the module to /etc/hotplug/blacklist to prevent it being loaded.

---

### Post by TeleTommy on 2005-09-11
Right, adding it into the file prevents it from loading. But that wasn't the failure.
I can't understand that such an widespread NIC does some problems on an todays Linux system.

Any other ideas?

---

### Post by AndreAPL on 2005-09-11
have the same problem  :-?  :-? 
did u try do deactivate ipv6 and see the effect?

---

### Post by mlomker on 2005-09-11
Have you tried booting up to a working version of linux (Knoppix or whatever) and double-checking that it sees the card on the same IRQ and IO ports?  I had a similar problem when I tried to run Linspire on my current laptop--it kept thinking my SIS900 was on a different IRQ than a working version of linux did.

That driver is included with the kernel, so I'm not sure if there's a later version that you could locate and compile.  I did some cursory Google searches but didn't come up with anything.  

If you know how you could try compiling a 2.6.13 kernel and see if it works.

---

### Post by TeleTommy on 2005-09-11
[QUOTE=AndreAPL]have the same problem  :-?  :-? 
did u try do deactivate ipv6 and see the effect?[/QUOTE]
 not tried to deactivate ip6 support because I don't know how. I will search the forum for any hints tomorrow .
IRQ I will check tomorrow too, because of a missing knoppix cd right now. Stay tuned :)

---

### Post by TeleTommy on 2005-09-12
Good hint! Thank you!
I think the card uses an other I/O port with knoppix (here working!). you can compare with my posting above.

dmesg output now contains:

eth0: RealTek RTL8139 at 0xe05b4c00, 00:0e:a6:28:a6:83, IRQ 5
eth0:  Identified 8139 chip type 'RTL-8101'
...
eth0: link up, 100Mbps, full-duplex, lpa 0x41E1


what can I do to fix the card to a certain IO port with ubuntu?

---

### Post by mlomker on 2005-09-12
Do a search for **linux-image** in Synaptic and see what version of the kernel you are running and if a newer one is available.  I'd recommend trying a newer kernel if there is a 2.6.11 kernel listed there as a first attempt.  If you can't get to the Internet from that machine then you'll somehow have to get [this file](http://packages.ubuntu.com/hoary/base/linux-image-2.6.11-1-386) onto the machine and install it manually (using the **dpkg -i packagename.deb** command).

If that doesn't work then your options are to attempt recompiling [the driver](http://www.scyld.com/rtl8139.html) or building your own kernel (both of which won't be easy if you don't know linux well).

---

### Post by TeleTommy on 2005-09-12
Hi!

A good and a bad message:

good: 
It works!! After rebooting with 2.6.11 the card got an ip adress via dhcp and was online

bad: that was via console before login with gdm. starting gnome the machine crashed. after reboot the filesystem is damaged and i shall it repair "manually" because chkdsk or however it's called can't. no idea how to do this. I'm afraid I have to reinstall the system... :)

Thank you all very much!

---

### Post by oracel on 2005-09-13
[QUOTE=TeleTommy]Hi!

I have a mysterious networking problem with either Hoary 5.04 and breezy 5.10.
The built-in NIC Realtec 8139 can't connect to my network. DHCP gets no answer and manually configuration doesn't work too. Configuring is no problem but pinging the router afterwards doesn't work.
Using Windows and other Linux Distros this was never a problem.

I saw that two modules are loaded with system start:
8139too
8139cp

with other linux distros there where only 8139too loaded and it worked fine.
Is it possible that the two both are active and muddle the system?
Can this be the problem? How can i get rid of the 8139cp driver?

I'm very thankful for any hints to solve the problem.

Thank you,
Thomas[/QUOTE]

 Hi, I use the 8139too driver when using the realtek 8139 cards. This works on even pretty old kernels.

---

### Post by TeleTommy on 2005-09-13
[QUOTE=oracel]Hi, I use the 8139too driver when using the realtek 8139 cards. This works on even pretty old kernels.[/QUOTE]

yes normally with my computer too. but don't with ubuntu...here It didn't reach the network...

---

### Post by mlomker on 2005-09-13
>  
It works!! After rebooting with 2.6.11 the card got an ip adress via dhcp and was online


Sorry to hear that!  I used the 2.6.11 kernel with no problems.

The command for repairing the disks is **fsck**.  If you haven't already reloaded your machine then you could try going into the 'rescue' option in grub and running it there.

---

