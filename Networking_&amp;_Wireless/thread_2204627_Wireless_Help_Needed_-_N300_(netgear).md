---
title: "Wireless Help Needed - N300 (netgear)"
date: 2014-02-09
forum: Networking &amp; Wireless
---

### Post by Floyd_Williams on 2014-02-09
I have ready a dozen threads here about getting wireless to work here. I am sure it is just because I am new to Ubuntu that I have missed something.

I have a 32 bit system and a Netgear N300. I think that I have followed all the steps but I still dont see any networks nor do I have an option to enable wireless.

Wired works fine. I get a wireless looking icon at the top when I unplug the wired conection but thats it. No connections are shown .

```
Bus 001 Device 002: ID 1b1c:1a0a Corsair 
Bus 001 Device 004: ID 0846:9020 NetGear, Inc. WNA3100(v1) Wireless-N 300 [Broadcom BCM43231]
Bus 003 Device 002: ID 046d:c044 Logitech, Inc. LX3 Optical Mouse
Bus 004 Device 002: ID 046d:c30f Logitech, Inc. Logicool HID-Compliant Keyboard (106 key)
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


```

It looks like the system sees the device. Above is what lsusb shows.

PLEASE Help this newcomer

---

### Post by Floyd_Williams on 2014-02-09
ifconfig says
```
williams@williams-Dimension-8400:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:11:11:59:b8:13  
          inet addr:192.168.1.112  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::211:11ff:fe59:b813/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:14485 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9976 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:11971922 (11.9 MB)  TX bytes:1418225 (1.4 MB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:1783 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1783 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:132949 (132.9 KB)  TX bytes:132949 (132.9 KB)
```

---

### Post by Floyd_Williams on 2014-02-09
iwconfig:

```
williams@williams-Dimension-8400:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

```

---

### Post by praseodym on 2014-02-09
Hi,

which Ubuntu version is it?
```

lsb_release -a
uname -a
```
Install ndiswrapper, dkms, ndisgtk and ndiswrapper-dkms and check this driver (32bit inside):

[http://media.cdn.ubuntu-de.org/forum/attachments/06/41/2612284-Broadcom_bcm43xx_USB_32_64bit_v2.tar.gz](http://media.cdn.ubuntu-de.org/forum/attachments/06/41/2612284-Broadcom_bcm43xx_USB_32_64bit_v2.tar.gz)

You may need to change the router settings to b/g mode. Check the manual

---

### Post by Floyd_Williams on 2014-02-09
Thanks for the reply

```
williams@williams-Dimension-8400:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.4 LTS
Release:    12.04
Codename:    precise


```

---

### Post by Floyd_Williams on 2014-02-09
ndiswrapper, dkms, ndisgtk and ndiswrapper-dkms installed

I also get this 

```
williams@williams-Dimension-8400:~$ sudo ndisgtk
[sudo] password for williams: 

(ndisgtk:2732): libglade-WARNING **: Could not load support for `gnome': libgnome.so: cannot open shared object file: No such file or directory


```

---

### Post by Floyd_Williams on 2014-02-09
gnomr now installed that one error is gone

---

### Post by praseodym on 2014-02-09
Unpack the driver and start the tool
```

gksudo ndisgtk
```
Install the 32bit *.INF file with it.

---

### Post by Floyd_Williams on 2014-02-09
driver installed

---

### Post by Floyd_Williams on 2014-02-09
Still no network

```
williams@williams-Dimension-8400:~$ sudo lshw -C network
[sudo] password for williams: 
  *-network               
       description: Ethernet interface
       product: NetXtreme BCM5751 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:11:11:59:b8:13
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.132 duplex=full firmware=5751-v3.23a ip=192.168.1.112 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:16 memory:dfcf0000-dfcfffff


```

---

### Post by praseodym on 2014-02-09
Ok, lets check

```
sudo ndiswrapper -ma
sudo modprobe -v ndiswrapper
ndiswrapper -l
cat /etc/modprobe.d/ndiswrapper.conf
dmesg | grep ndis
```

---

### Post by Floyd_Williams on 2014-02-09
```
williams@williams-Dimension-8400:~$ sudo modprobe -v ndiswrapper
FATAL: Module ndiswrapper not found.
williams@williams-Dimension-8400:~$ ndiswrapper -l
bcmn43xx32 : driver installed
    device (0846:9020) present
williams@williams-Dimension-8400:~$ cat /etc/modprobe.d/ndiswrapper.conf
alias usb:v050Dp6050d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v050Dp615Ad*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v050Dp825Cd*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v0846p9011d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v0846p9020d*dc*dsc*dp*ic*isc*ip* ndiswrapper
williams@williams-Dimension-8400:~$ dmesg | grep ndis


```

---

### Post by praseodym on 2014-02-09
Obviously, its not fully installed. Check:
```

sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential ndisgtk ndiswrapper-dkms dkms
```
Then try it again.

---

### Post by Floyd_Williams on 2014-02-09
got this
```
williams@williams-Dimension-8400:~$ ndiswrapper -l
bcmn43xx32 : driver installed
    device (0846:9020) present
williams@williams-Dimension-8400:~$ cat /etc/modprobe.d/ndiswrapper.conf
alias usb:v050Dp6050d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v050Dp615Ad*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v050Dp825Cd*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v0846p9011d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v0846p9020d*dc*dsc*dp*ic*isc*ip* ndiswrapper
williams@williams-Dimension-8400:~$ dmesg | grep ndis


```

---

### Post by praseodym on 2014-02-09
Driver loaded?
```

sudo ndiswrapper -ma
sudo modprobe -v ndiswrapper
```
Maybe you try to install the *.INF via terminal:
```

sudo ndiswrapper -i [COLOR="#FF0000"]/exact/path/to/*.INF[/COLOR]
```

---

### Post by Floyd_Williams on 2014-02-09
```
williams@williams-Dimension-8400:~$ sudo ndiswrapper -i /home/williams/Desktop/bcmn43xx32.inf
driver bcmn43xx32 is already installed
williams@williams-Dimension-8400:~$ 
```

---

### Post by praseodym on 2014-02-09
Ndiswrapper is found?
```

locate ndiswrapper.ko | grep lib
sudo modprobe -v ndiswrapper
dmesg | grep ndis
modinfo ndiswrapper
```

---

### Post by Floyd_Williams on 2014-02-09
and now.......

```
williams@williams-Dimension-8400:~$ locate ndiswrapper.ko | grep lib
williams@williams-Dimension-8400:~$ sudo modprobe -v ndiswrapper
FATAL: Module ndiswrapper not found.
williams@williams-Dimension-8400:~$ dmesg | grep ndis
williams@williams-Dimension-8400:~$ modinfo ndiswrapper
ERROR: modinfo: could not find module ndiswrapper
williams@williams-Dimension-8400:~$ 

```

---

### Post by praseodym on 2014-02-09
Weired. Maybe its the wrong wrapper version?!
```

sudo apt-get remove --purge ndisgtk ndiswrapper*
```
New one:

```
wget https://launchpad.net/ubuntu/+archive/primary/+files/ndiswrapper-common_1.58-2_all.deb
wget https://launchpad.net/ubuntu/+archive/primary/+files/ndiswrapper-dkms_1.58-2_all.deb
```
Additionally for 32bit
```
wget https://launchpad.net/ubuntu/+archive/primary/+files/ndiswrapper-utils-1.9_1.58-2_i386.deb
```

or for 64bit```

https://launchpad.net/ubuntu/+archive/primary/+files/ndiswrapper-utils-1.9_1.58-2_amd64.deb
```
Installation:
```

sudo dpkg -i *.deb
```
Then try it again via terminal

---

### Post by Floyd_Williams on 2014-02-09
Installs appeared to go with no errors....

after running:
```
 
sudo ndiswrapper -ma
sudo modprobe -v ndiswrapper
ndiswrapper -l
cat /etc/modprobe.d/ndiswrapper.conf
dmesg | grep ndis
```

I got this:



```
williams@williams-Dimension-8400:~$ sudo ndiswrapper -ma
module configuration information is stored in /etc/modprobe.d/ndiswrapper.conf
williams@williams-Dimension-8400:~$ sudo modprobe -v ndiswrapper
williams@williams-Dimension-8400:~$ ndiswrapper -l
bcmn43xx32 : driver installed
    device (0846:9020) present
williams@williams-Dimension-8400:~$ cat /etc/modprobe.d/ndiswrapper.conf
alias usb:v050Dp6050d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v050Dp615Ad*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v050Dp825Cd*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v0846p9011d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v0846p9020d*dc*dsc*dp*ic*isc*ip* ndiswrapper
williams@williams-Dimension-8400:~$ dmesg | grep ndis
[15456.103135] ndiswrapper: module verification failed: signature and/or required key missing - tainting kernel
[15456.106080] ndiswrapper version 1.58 loaded (smp=yes, preempt=no)
[15456.405759] ndiswrapper: driver bcmn43xx32 (,08/26/2009, 5.10.79.30) loaded
[15456.915618] usbcore: registered new interface driver ndiswrapper
williams@williams-Dimension-8400:~$ 


```

However, it got to this line:
```
williams@williams-Dimension-8400:~$ dmesg | grep ndis
```

and stopped. I let it sit for a while and nothing.
Pressing enter gave this:
```
[15456.103135] ndiswrapper: module verification failed: signature and/or required key missing - tainting kernel
[15456.106080] ndiswrapper version 1.58 loaded (smp=yes, preempt=no)
[15456.405759] ndiswrapper: driver bcmn43xx32 (,08/26/2009, 5.10.79.30) loaded
[15456.915618] usbcore: registered new interface driver ndiswrapper
williams@williams-Dimension-8400:~$
```

---

### Post by praseodym on 2014-02-10
Which kernel is it?

uname -a

---

