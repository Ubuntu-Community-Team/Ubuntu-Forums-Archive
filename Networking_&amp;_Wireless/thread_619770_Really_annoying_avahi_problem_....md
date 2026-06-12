---
title: "Really annoying avahi problem ..."
date: 2007-11-21
forum: Networking &amp; Wireless
---

### Post by dbee on 2007-11-21
So I've been staring at this problem for months now. It seems that I all-but trashed my ubuntu laptop by clicking on the Network-Manager applet on the bottom bar of X. I'm rather surprised that the system could be that temperamental. Can someone pls help out so I can restore my faith and tell all my friends that linux isn't as temperamental as everyone says it is ?

The applet now has a red stop sign in front of it to signify that it's not working. When I click it, I get the message ...

Could not find information on interface 'eth1:avahi' in /proc/net/dev

That message seems to indicate that the DHCP client isn't getting an address from the DHCP server. The thing is though - I can connect fine if I manually build my wireless connection myself on eth1 ...

su root
iwconfig eth1 mode managed key -------------------
iwconfig eth1 essid '---------'
dhclient

My eth1 connection will work fine, but my vmnet connections won't come online. I've just used eth1 for a while now, but I want to start working with virtual machines, and I think this error may be the cause of the connectivity problems for my VM's.

I'm on a HP Pavillion laptop and lspci gives my network controller as ...

```

babo@eire:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation G72M [GeForce Go 7400] (rev a1)
02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
05:00.0 Ethernet controller: Intel Corporation 82573L Gigabit Ethernet Controller
07:05.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
07:05.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
07:05.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 01)
07:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
07:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)

```

also 

```

babo@eire:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:16:36:B3:86:1B  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Base address:0x4000 Memory:da000000-da020000 

eth1      Link encap:Ethernet  HWaddr 00:18:DE:0B:5F:2B  
          inet addr:192.168.1.4  Bcast:255.255.255.255  Mask:255.255.255.0
          inet6 addr: fe80::218:deff:fe0b:5f2b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:330872 errors:2 dropped:99035 overruns:0 frame:0
          TX packets:297368 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:333572151 (318.1 MB)  TX bytes:137275841 (130.9 MB)
          Interrupt:16 Base address:0xe000 Memory:d8000000-d8000fff 

eth0:avah Link encap:Ethernet  HWaddr 00:16:36:B3:86:1B  
          inet addr:169.254.5.59  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Base address:0x4000 Memory:da000000-da020000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3635 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3635 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:868758 (848.3 KB)  TX bytes:868758 (848.3 KB)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:C0:00:01  
          inet addr:192.168.80.128  Bcast:192.168.80.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:65 errors:0 dropped:0 overruns:0 frame:0
          TX packets:131 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:C0:00:08  
          inet addr:192.168.40.128  Bcast:192.168.40.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:79 errors:0 dropped:0 overruns:0 frame:0
          TX packets:186 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

``` 

Does anyone have any idea what's wrong here ?

I'd like to fix the network manager so that I don't have to manually switch to root and build my eth1 connection every time I log in.

And I'd also like to get connectivity for my VM's ....

Thanks

---

### Post by mpierce on 2007-11-21
I'm not sure what you're asking here but first off, I'd set my wireless up to be permanent on by editing /etc/net/interfaces for eth1:

# The primary network interface
auto eth1
iface eth1 inet dhcp
        # wireless-* options are implemented by the wireless-tools package
        wireless-mode managed
        wireless-essid BiPAC_7402GL
        wireless-key1 10c51axxxxxxxxxxxxxxxx

That will solve your having to reinitiate it everytime you start your machine. It should come up OK.

Obviously eth0 is not getting an address. I assume this is your LAN and that you don't have a cable in it hence it is being assign the avhi bogus address by default.

Hope this helps...

---

