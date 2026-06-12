---
title: "No ethernet connection in 14.04"
date: 2015-01-17
forum: Networking &amp; Wireless
---

### Post by adam81 on 2015-01-17
Hi,

I just upgraded to 14.04 from 12.04 and have lost my ethernet connection.  I'm not that savvy with Ubuntu but can use the terminal and have done so on many occasions trying to fix issues with XBMC and other programs

I now have wireless but this was really ropey previously.

I've had some searches on the forums, but couldn't fix it but I think you will need to see these outputs?

Any advice wold be great, and if needed wil post any reports.
Thanks

adam@Revo:~$ sudo ethtool eth0
Settings for eth0:
Cannot get device settings: No such device
Cannot get wake-on-lan settings: No such device
Cannot get message level: No such device
Cannot get link status: No such device
No data available

adam@Revo:~$ lspci

00:00.0 Host bridge: Intel Corporation Atom Processor D4xx/D5xx/N4xx/N5xx DMI Bridge (rev 02)
00:1b.0 Audio device: Intel Corporation NM10/ICH7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 1 (rev 02)
00:1c.2 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 4 (rev 02)
00:1d.0 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB controller: Intel Corporation NM10/ICH7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation NM10/ICH7 Family SATA Controller [IDE mode] (rev 02)
00:1f.3 SMBus: Intel Corporation NM10/ICH7 Family SMBus Controller (rev 02)
01:00.0 VGA compatible controller: NVIDIA Corporation GT218 [ION] (rev a2)
01:00.1 Audio device: NVIDIA Corporation High Definition Audio Controller (rev a1)
02:00.0 Network controller: Ralink corp. RT3090 Wireless 802.11n 1T/1R PCIe
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 06)

---

### Post by weatherman2 on 2015-01-17
Don't try to act on "eth0" unless you have a device identified by "eth0."  That's a default network device but may not be yours.  Perhaps in the upgrade, a new network device was identified and now you are on "eth1" or something.

Try these commands to give us more information - what is the output of each?

```
sudo lshw -C network
```
```
ifconfig
```

If you had an eth0 in 12.04 but no longer, an easy way to fix this might be to blow away the existing /etc/udev/rules.d/70-persistent-net.rules file, which may have "eth0" in it if you had eth0 before.  Just erase it (sudo rm /etc/udev/rules.d/70-persistent-net.rules ).  Then reboot and it will be re-generated (wireless card will go back to wlan0 as well, so you may have to re-connect to WiFi).  But eth0 will probably be assigned to the first network card, and  that may allow old configurations left over from 12.04 to work.

---

### Post by adam81 on 2015-01-18
Tried the persistent rules command, no luck there so here are the outputs you said to show.

I also tried all the way upto eth6 with same result.

Looking the connection is apparently in my network connections, but unable to connect still even when disabling wireless.

I guess the lines saying network unclaimed might  have something to do with it?

```
sudo lshw -C network
*-network               
       description: Wireless interface
       product: RT3090 Wireless 802.11n 1T/1R PCIe
       vendor: Ralink corp.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 00
       serial: d0:df:9a:75:46:1c
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2800pci driverversion=3.13.0-24-generic firmware=0.34 ip=192.168.0.12 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:18 memory:febf0000-febfffff
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
       resources: ioport:e800(size=256) memory:fbffb000-fbffbfff memory:fbffc000-fbffffff

ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:814 errors:0 dropped:0 overruns:0 frame:0
          TX packets:814 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:226474 (226.4 KB)  TX bytes:226474 (226.4 KB)


wlan0     Link encap:Ethernet  HWaddr d0:df:9a:75:46:1c  
          inet addr:192.168.0.12  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::d2df:9aff:fe75:461c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3009 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3756 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:840355 (840.3 KB)  TX bytes:1864808 (1.8 MB)
```

---

### Post by chait3 on 2015-01-19
Hi, 
  I happen to see a line in your output: [COLOR=#000000]*-network UNCLAIMED

Found this, maybe helpful: [/COLOR][http://ubuntuforums.org/showthread.php?t=1314693](http://ubuntuforums.org/showthread.php?t=1314693)

---

### Post by Hadaka on 2015-01-19
Hi, this should get you going..
[http://ubuntuforums.org/showthread.php?t=2237873](http://ubuntuforums.org/showthread.php?t=2237873)
post #2 and possibly #4, dont forget your blacklist.

---

### Post by adam81 on 2015-01-21
Hi,

Read and tried the post you linked to Hadaka, the other post seemed to refer to pre 14.04.

Did post 4 first, no change, then post 2, but have probably done something wrong and get an error in the terminal

When I entered the 2nd command..
sudo tar xvf 3005217-r8168-dkms-8.038.00.tar.gz -C /usr/src

It threw up the following error, any ideas?  It all seemed to unpack as I'd expect.  The files are named the same so not sure..
Cannot open: No such file or directory
tar: Error is not recoverable: exiting now

---

### Post by adam81 on 2015-02-07
Hi,

I've still not solved this issue even after trying the stuff in the posts.

Anyone got any other ideas?

---

### Post by Haven_McClure on 2015-02-09
Hi, I have Ubuntu Studio 14.10 on a Lenovo z40 laptop. I cannot get the  wireless on this computer to work at all either. In reading these  forums, I need to do the same thing that adam81 is trying to do.  But when I try, I get these results.

```


haven@haven-Lenovo-Z40-70:~$  sudo apt-get install --reinstall linux-headers0$(uname -r)  linux-headers-generic build-essential dkms
[sudo] password for haven: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package linux-headers03.16.0-30-lowlatency
E: Couldn't find any package by regex 'linux-headers03.16.0-30-lowlatency'
haven@haven-Lenovo-Z40-70:~$ ^C
haven@haven-Lenovo-Z40-70:~$ wget http://media.cdn.ubuntu-de.org/forum/attachments/45/14/3005217-r8168-dkms-8.038.00.tar.gz
--2015-02-09 09:28:12--  http://media.cdn.ubuntu-de.org/forum/attachments/45/14/3005217-r8168-dkms-8.038.00.tar.gz
Resolving media.cdn.ubuntu-de.org (media.cdn.ubuntu-de.org)... 213.95.41.4, 2001:780:0:25:dead:beef:cafe:1
Connecting to media.cdn.ubuntu-de.org (media.cdn.ubuntu-de.org)|213.95.41.4|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 100104 (98K) [application/octet-stream]
Saving to: &#8216;3005217-r8168-dkms-8.038.00.tar.gz&#8217;

100%[======================================>] 100,104      206KB/s   in 0.5s   

2015-02-09 09:28:13 (206 KB/s) - &#8216;3005217-r8168-dkms-8.038.00.tar.gz&#8217; saved [100104/100104]

haven@haven-Lenovo-Z40-70:~$ sudo tar xvf 3005217-r8168-dkms-8.038.00.tar.gz -C /usr/src
r8168-dkms-8.038.00/src/Makefile
r8168-dkms-8.038.00/src/Makefile_linux24x
r8168-dkms-8.038.00/src/r8168.h
r8168-dkms-8.038.00/src/r8168_asf.c
r8168-dkms-8.038.00/src/r8168_asf.h
r8168-dkms-8.038.00/src/r8168_dash.h
r8168-dkms-8.038.00/src/r8168_n.c
r8168-dkms-8.038.00/src/rtltool.c
r8168-dkms-8.038.00/src/rtltool.h
r8168-dkms-8.038.00/src/rtl_eeprom.c
r8168-dkms-8.038.00/src/rtl_eeprom.h
r8168-dkms-8.038.00/dkms.conf
r8168-dkms-8.038.00/autorun.sh
r8168-dkms-8.038.00/Makefile
r8168-dkms-8.038.00/README
r8168-dkms-8.038.00/src/
r8168-dkms-8.038.00/
haven@haven-Lenovo-Z40-70:~$ sudo dkms add -m r8168-dkms -v 8.038.00
Error! DKMS tree already contains: r8168-dkms-8.038.00
You cannot add the same module/version combo more than once.
haven@haven-Lenovo-Z40-70:~$ sudo dkms build -m r8168-dkms -v 8.038.00

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....
'make' -C src/ all............(bad exit status: 2)
ERROR (dkms apport): binary package for r8168-dkms: 8.038.00 not found
Error! Bad return status for module build on kernel: 3.16.0-30-lowlatency (x86_64)
Consult /var/lib/dkms/r8168-dkms/8.038.00/build/make.log for more information.

```

I tried consulting the file it recommended but it gave me no clues.

---

### Post by adam81 on 2015-02-09
Hi,

I fixed mine over the weekend..

Followed post 5 in this link.
[http://ubuntuforums.org/showthread.php?t=2238805](http://ubuntuforums.org/showthread.php?t=2238805)

Whether than works for WiFi don't know

---

