---
title: "network disabled after Chromium lockup"
date: 2016-05-13
forum: Networking &amp; Wireless
---

### Post by JamButty on 2016-05-13
Chromium locked up system while streaming, required hard boot/poweroff (not an unusual situation, sadly), but this time the system came up with network disabled. No network menu icon on menu bar. "network" under system settings says "the system network services are not compatible with this version". Ostensible wireless on/off fn+f2 invokes email on my keyboard - no wireless keyboard function key found. Not hard blocked. Wireless works fine on Windows side. Here is output of lshw and rfkill list (nm-tools result png as attachment):
> *-network DISABLED
description: Ethernet interface
product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
vendor: Realtek Semiconductor Co., Ltd.
physical id: 0
bus info: pci@0000:02:00.0
logical name: eth0
version: 0c 
serial: 64:00:6a:0b:02:24
size: 10Mbit/s
capacity: 1Gbit/s
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s
resources: irq:31 ioport:e000(size=256) memory:f7d00000-f7d00fff memory:f0000000-f0003fff
        *-pci:2
             


*-network DISABLED
description: Wireless interface
product: QCA9565 / AR9565 Wireless Network Adapter
vendor: Qualcomm Atheros
physical id: 0
bus info: pci@0000:03:00.0
logical name: wlan0
version: 01
serial: 4c:bb:58:de:7d:a8
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical wireless
configuration: broadcast=yes driver=ath9k driverversion=4.2.0-36-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
resources: irq:16 memory:f7c00000-f7c7ffff memory:f7c80000-f7c8ffff
  


$ rfkill list all
0: phy0: Wireless LAN
 Soft blocked: no
 Hard blocked: no
1: hci0: Bluetooth
Soft blocked: no
Hard blocked: no


---

### Post by QDR06VV9 on 2016-05-13
What dose this show
```
gedit /etc/network/interfaces
```
Paste back the output

---

### Post by JamButty on 2016-05-13
> # interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback



thanks

---

### Post by QDR06VV9 on 2016-05-13
Huumm?
One more if you would
```
apt-cache policy dhcpcd5
```
And again paste back here.

---

### Post by JamButty on 2016-05-13
> torfkopf@torfkopf-Inspiron-3847:~$ apt-cache policy dhcpcd5
dhcpcd5:
  Installed: (none)
  Candidate: 6.0.5-1.1
  Version table:
     6.0.5-1.1 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty/universe amd64 Packages
torfkopf@torfkopf-Inspiron-3847:~$ 


....

---

### Post by QDR06VV9 on 2016-05-13
Ok Try this
```
sudo apt-get install dhcpcd5
```
After that is finished...Try to restart your network manager.
```
sudo service network-manager restart

```
And it has come to my attention of a bad update in trusty(14.04)
Networking Bug && Workaround
[http://ubuntuforums.org/showthread.php?t=2324504](http://ubuntuforums.org/showthread.php?t=2324504)

---

### Post by JamButty on 2016-05-13
Gotta run. Will resume tomorrow afternoon.

Thanks!

---

### Post by JamButty on 2016-05-14
maybe I am missing something, but if I have no network, how can apt-get get anything to install? output plus "system error" popup.
> torfkopf@torfkopf-Inspiron-3847:~$ sudo apt-get install dhcpcd5
[sudo] password for torfkopf: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-4.2.0-27 linux-headers-4.2.0-27-generic
  linux-image-4.2.0-27-generic linux-image-extra-4.2.0-27-generic
Use 'apt-get autoremove' to remove them.
Suggested packages:
  dhcpcd-gtk
The following NEW packages will be installed:
  dhcpcd5
0 upgraded, 1 newly installed, 0 to remove and 5 not upgraded.
Need to get 94.4 kB of archives.
After this operation, 283 kB of additional disk space will be used.
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty/universe dhcpcd5 amd64 6.0.5-1.1
  Could not resolve 'us.archive.ubuntu.com'
E: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/universe/d/dhcpcd5/dhcpcd5_6.0.5-1.1_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/d/dhcpcd5/dhcpcd5_6.0.5-1.1_amd64.deb)  Could not resolve 'us.archive.ubuntu.com'

E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
torfkopf@torfkopf-Inspiron-3847:~$ sudo service network-manager restart
stop: Unknown instance: 
network-manager start/running, process 2220


[ATTACH=CONFIG]269061[/ATTACH]

---

### Post by JamButty on 2016-05-14
In case this helps, after the above, I booted into Ubuntu again, got the "system error" popup twice, clicked on "report" on the second one and got this (sorry for the pngs, but I found no way to capture the text)
[ATTACH=CONFIG]269062[/ATTACH][ATTACH=CONFIG]269063[/ATTACH][ATTACH=CONFIG]269064[/ATTACH][ATTACH=CONFIG]269065[/ATTACH]

---

### Post by QDR06VV9 on 2016-05-14
Well i assumed here that you had perhaps used an ethernet cord.
But you will need  the network to follow this from my post above.
> Networking Bug && Workaround
[http://ubuntuforums.org/showthread.php?t=2324504](http://ubuntuforums.org/showthread.php?t=2324504).
There was a bug show up the same time as your problem was posted.

---

### Post by jeremy31 on 2016-05-14
Moved to Networking and Wireless
You might want to search for r8168-dkms and see if it works

What Ubuntu version?

---

### Post by jkeenan on 2016-05-14
That error message is the same as I and others had today.  Following this explanation solved my problem:  [http://ubuntuforums.org/showthread.php?t=2324504](http://ubuntuforums.org/showthread.php?t=2324504)
YMMV

---

### Post by JamButty on 2016-05-14
runrickus - I assumed since the ethernet is also listed as disabled, that a hard wire would not work either. It is a large screen desktop unit, so it does not lend itself to carting over to the router to hard wire it, but I will try that tomorrow, and try out the r8168-dkms and downgrade possibilities (currently 14.04)

thanks!

---

### Post by JamButty on 2016-05-20
OK! finally got a day off to look at this - ethernet was out, so hard wire did not work, but downgrading libnl via .deb files pulled on the Windoze side did work. Still getting "system error" popups, but I can live with that for now.

---

