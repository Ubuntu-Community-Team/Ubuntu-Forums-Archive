---
title: "Network problem in Dell Inspiron 6400"
date: 2009-08-21
forum: New to Ubuntu
---

### Post by ovroniil on 2009-08-21
I am using [Dell Inspiron 6400]("http://www.dell.com/us/en/dfb/notebooks/inspn_6400/pd.aspx?refid=inspn_6400&cs=28&s=dfb"). I've just installed new kernel _*Linux 2.6.30-020530-generic*_ and it works fine except my net  connection (which was working fine before the conversion). Network Manager Applet on the upper panel shows that "No network devices available". 

So I manually edit the following file:

```
**$ sudo vim /etc/network/interfaces**

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.0.**.**
netmask 255.255.252.0
gateway 192.0.0.1

```I also configured nameserver at /etc/resolve.conf. Then I restarted the network, which shows following output:

```
**$ sudo invoke-rc.d networking restart**

 * Reconfiguring network interfaces...            
SIOCSIFHWADDR: No such device
eth0: ERROR while getting interface flags: No such device
Failed to bring up eth0.
```If I apply ifconfig, it returns following result
```
**$ ifconfig**

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B
```But by lspci, it shows that there is something for controlling ethernet:

```
**$ lspci**

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
[COLOR=Red]**03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)**[/COLOR]
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
03:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 0a)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 05)
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
0b:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
```eth0 can't be spotted from *Sytem>Administration>Network Tools. *Below is a screen shot of Network Tools with the available devices in it. from the screen shot you'll find that there are only two Network Devices; one is "lo" and another is "pan0".

[IMG]http://img33.imageshack.us/img33/9039/screenshotdln.png[/IMG]

Any solution for solving this problem??

---

