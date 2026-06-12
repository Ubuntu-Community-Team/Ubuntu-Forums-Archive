---
title: "eth1 not detected?"
date: 2008-10-19
forum: Networking &amp; Wireless
---

### Post by allenbradley on 2008-10-19
Hello. I am running Hardy on an Inspiron 1525. I tried to connect to the wireless network in my house using the command :
```
sudo iwconfig eth1 essid <network name> 
```.

But I get the error :
```
 Error for Wireless request "Set ESSID" (8B1A) :
    Set failed on device eth1 : no such device. 
```

What should I do?

---

### Post by Kevbert on 2008-10-19
The device may be on eth0. What is your output of
```
ifconfig
```

---

### Post by allenbradley on 2008-10-19
hey thanks for the reply. Heres what I got for ifconfig :
```

 
eth0      Link encap:Ethernet  HWaddr 00:1d:09:53:6e:5f
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16

eth0:avahi Link encap:Ethernet  HWaddr 00:1d:09:53:6e:5f
          inet addr:169.254.4.188  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:16

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1619 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1619 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:200522 (195.8 KB)  TX bytes:200522 (195.8 KB)

wlan0     Link encap:UNSPEC  HWaddr 00-1F-3C-54-26-DF-00-00-00-00-00-00-00-00-00-00
          UP BROADCAST RUNNING PROMISC MULTICAST  MTU:1500  Metric:1
          RX packets:157 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:17741 (17.3 KB)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-1F-3C-54-26-DF-00-00-00-00-00-00-00-00-00-00
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

I got the same for ifconfig -a

---

### Post by ratmandall on 2008-10-19
> **allenbradley said:**
> hey thanks for the reply. Heres what I got for ifconfig :
```

 
eth0      Link encap:Ethernet  HWaddr 00:1d:09:53:6e:5f
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16

eth0:avahi Link encap:Ethernet  HWaddr 00:1d:09:53:6e:5f
          inet addr:169.254.4.188  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:16

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1619 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1619 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:200522 (195.8 KB)  TX bytes:200522 (195.8 KB)

wlan0     Link encap:UNSPEC  HWaddr 00-1F-3C-54-26-DF-00-00-00-00-00-00-00-00-00-00
          UP BROADCAST RUNNING PROMISC MULTICAST  MTU:1500  Metric:1
          RX packets:157 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:17741 (17.3 KB)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-1F-3C-54-26-DF-00-00-00-00-00-00-00-00-00-00
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

I got the same for ifconfig -a

If you're trying to connect to a wireless network then wlan0 is the wireless interface.

---

### Post by allenbradley on 2008-10-19
I thought the code for joining a wiress network was :
```
iwconfig eth1 essid <network name>
dhclient eth1

```
Is there an alternative to connect via terminal?

---

### Post by superprash2003 on 2008-10-19
its the same, sudo gives root access.. and do an iwconfig to find your wifi interface... are you able to connect to other networks.. has ubuntu successfully recognized your wifi card?

---

### Post by allenbradley on 2008-10-19
it has... i downloaded kismet to make sure i could see my network. I can see the network but I am not able to connevct to it.

---

### Post by Kevbert on 2008-10-19
Your hard wired connection is eth0 and wireless is wlan0. It looks like you may need to download some wireless firmware drivers, hence the errors. What is the output of 
```
lspci
```

---

### Post by allenbradley on 2008-11-01
Thanks for the reply.
Sorry for the huge delay, but here it is.

```
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
02:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
02:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
02:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
02:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
02:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 12)
0b:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

```
Thanks in advance!

---

### Post by allenbradley on 2008-11-01
I have a netgear router, if that helps in any way possible.

---

### Post by allenbradley on 2008-11-01
oh, and Kevbert, what drivers should I download?

---

