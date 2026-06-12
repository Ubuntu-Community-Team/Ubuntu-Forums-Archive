---
title: "BCM4352 wireless driver issue modprobe: ERROR: could not insert 'wl': Invalid argumen"
date: 2015-11-08
forum: Networking &amp; Wireless
---

### Post by TCP_RDG on 2015-11-08
Hello all, 

I have this same exact problem as mentioned in "http://askubuntu.com/questions/590442/how-can-i-install-broadcom-wireless-adapter-bcm4352-802-11ac-pcid-14e443b1-r/695346#695346"with no luck whatsoever. Hope Chili555 (who very actively helped lots of other folks with broadcom driver issue) is still around and helps me with this. Here is the summary of my issue:

**Laptop model:** DELL XPS 2015 (model:9343)
**Operating System:** Ubuntu 14.04
**Kernel:**

 **uname -a**
Linux hostname 3.16.0-52-generic #71~14.04.1-Ubuntu SMP Fri Oct 23 17:24:53 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

**Broadcom wireless module:**

02:00.0 Network controller: Broadcom Corporation BCM4352 802.11ac Wireless Network Adapter (rev 03)

dpkg --list | grep bcm
ii  bcmwl-kernel-source                                   6.30.223.248+bdcom-0ubuntu0.1                              amd64        Broadcom 802.11 Linux STA wireless driver source

lspci -n | grep 14e4
02:00.0 0280: 14e4:43b1 (rev 03)

At the end of "apt-get install --reinstall bcmwl-kernel-source" I get this error: modprobe: ERROR: could not insert 'wl': Invalid argument

**sudo apt-get install --reinstall bcmwl-kernel-source**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0 B/1,512 kB of archives.
After this operation, 0 B of additional disk space will be used.
(Reading database ... 263526 files and directories currently installed.)
Preparing to unpack .../bcmwl-kernel-source_6.30.223.248+bdcom-0ubuntu0.1_amd64.deb ...
Removing all DKMS Modules
Done.
Unpacking bcmwl-kernel-source (6.30.223.248+bdcom-0ubuntu0.1) over (6.30.223.248+bdcom-0ubuntu0.1) ...
Setting up bcmwl-kernel-source (6.30.223.248+bdcom-0ubuntu0.1) ...
Loading new bcmwl-6.30.223.248+bdcom DKMS files...
Building only for 3.16.0-52-generic
Building for architecture x86_64
Building initial module for 3.16.0-52-generic
Done.

wl:
Running module version sanity check.
- Original module
   - No original module exists within this kernel
- Installation
   - Installing to /lib/modules/3.16.0-52-generic/updates/dkms/

depmod....

DKMS: install completed.
**[COLOR=#ff0000]modprobe: ERROR: could not insert 'wl': Invalid argument[/COLOR]**
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools (0.103ubuntu4.2) ...
update-initramfs: Generating /boot/initrd.img-3.16.0-52-generic

And the wireless network  shows as UNCLAIMED:

** lshw -C network**
[COLOR=#ff0000]**  *-network UNCLAIMED     **[/COLOR]
       description: Network controller
       product: BCM4352 802.11ac Wireless Network Adapter
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:f7204000-f7207fxf memory:f7000000-f71fdfff
  *-network
       description: Ethernet interface
       physical id: 2
       logical name: eth0
       serial: dc:9b:9c:ed:a9:43
       size: 100Mbit/s
       capacity: 100Mbit/s
       capabilities: ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=asix driverversion=22-Dec-2011 duplex=full firmware=ASIX AX88772 USB 2.0 Ethernet ip=192.168.1.126 link=yes multicast=yes port=MII speed=100Mbit/s


** iwconfig**
eth0      no wireless extensions.

lo        no wireless extensions.

** ifconfig wlan0**
wlan0: error fetching interface information: Device not found

modprobe wl
[COLOR=#ff0000]modprobe: ERROR: could not insert 'wl': Invalid argument
modprobe: ERROR: ../libkmod/libkmod-module.c:959 command_do() Error running install command for wl
modprobe: ERROR: could not insert 'wl': Operation not permitted

[/COLOR]
I searched numerous forums and tried re-installing BCM driver several times and rebooting with no luck. I have ethernet up and running.

I can't afford to re-install entire Ubuntu for this. Appreciate any help in this.

---

### Post by Bucky Ball on 2015-11-08
Just a bump and a reminder: Please use code tags for 

```
TERMINAL OUTPUT.
```

See the last link in my signature. Neater, easier to read, and space saving. Haven't seen chili for a bit, but there are other wireless gurus about who'll hopefully see this. 

Thanks and good luck. ;)

---

### Post by TCP_RDG on 2015-11-08
Hi All,

I just resolved this issue by running 2 commands:

sudo apt-get install --reinstall linux-headers-generic-lts-utopic
dpkg -i bcmwl-kernel-source_6.30.223.248+bdcom-0ubuntu0.1_amd64.deb  (i had this file locally downloaded)


I think the key was the first command. I was always trying to reinstall linux-headers-generic and not linux-headers-generic-lts-utopic. 

Posted it for anyone else who face this issue.  Till now I am not able to figure out the root cause of this issue. It just popped up when I restarted my laptop yesterday .

---

### Post by Bucky Ball on 2015-11-08
Thanks for sharing. Please see the first link in my signature. Enjoy! :)

---

