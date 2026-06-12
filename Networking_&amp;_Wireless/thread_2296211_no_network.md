---
title: "no network"
date: 2015-09-24
forum: Networking &amp; Wireless
---

### Post by dourvas on 2015-09-24
Hallo.

Forgive me if i sound too novice but i am.
i installed the last version of edubuntu (fat client). During installation everything were going wanderfull. i even were connected to internet (the 2 arrows were visible). when the installation process completed and the edubuntu started to load for the first time it crashed. I did not record the message. i had to reset the mashine. the edubuntu works fine now but there is no sign of the network adaptor  (3com pci tx nic)

I know that i maybe provide small ammount of info but i imagine that you will ask for important information.

Please help

---

### Post by howefield on 2015-09-24
Thread moved to the "*Networking & Wireless*" forum for better support.

---

### Post by Bucky Ball on 2015-09-24
Welcome. Could you please open a terminal (not sure what desktop environment Edubuntu uses, but you should be able to find it somewhere, perhaps in 'Accessories') and input this command:

```
sudo lshw -C network
```

You will be asked for your password. When you type it, it will be invisible. This is normal.

Could you copy (control+shift+c or 'Edit> Copy') and paste the output back here between code tags, please (see last link in my signature). Thanks.

---

### Post by dourvas on 2015-09-24
here it is. the ethernet cart is visible aftrer all. I am waiting for my next moves...      

 ```

description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       &#954;&#945;&#964;&#945;&#963;&#954;&#949;&#965;&#945;&#963;&#964;&#942;&#962;: Realtek Semiconductor Co., Ltd.
       physical id: 0
       &#960;&#955;&#951;&#961;&#959;&#966;&#959;&#961;&#943;&#949;&#962; &#948;&#953;&#945;&#973;&#955;&#959;&#965;: pci@0000:03:00.0
       &#955;&#959;&#947;&#953;&#954;&#972; &#972;&#957;&#959;&#956;&#945;: eth0
       version: 02
       serial: 00:24:1d:c0:66:de
       &#956;&#941;&#947;&#949;&#952;&#959;&#962;: 100Mbit/s
       &#967;&#969;&#961;&#951;&#964;&#953;&#954;&#972;&#964;&#951;&#964;&#945;: 1Gbit/s
       &#960;&#955;&#940;&#964;&#959;&#962;: 64 bits
       &#961;&#959;&#955;&#972;&#953;: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.0.1 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       &#960;&#972;&#961;&#959;&#953;: irq:27 ioport:c000(size=256) &#956;&#957;&#942;&#956;&#951;:e4010000-e4010fff &#956;&#957;&#942;&#956;&#951;:e4000000-e400ffff &#956;&#957;&#942;&#956;&#951;:e3000000-e300ffff

```

---

### Post by dourvas on 2015-09-25
the light of the ethernet card is on (green). The option "ethernet network" from the menu at the up-right next to language connection is not choosable and there are no network connections.

How to connect to the internet and see the other devices;

someone?

---

### Post by dourvas on 2015-09-25
```
description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       constructor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:24:1d:c0:66:de
       size: 100Mbit/s
       capacity: 1Gbit/s
       length: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.0.1 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:27 ioport:c000(size=256) memory:e4010000-e4010fff memory:e4000000-e400ffff memory:e3000000-e300ffff
```

i translated the code in case that is the problem for not getting any answers

---

### Post by nknwn on 2015-09-25
I can't see why that's not connecting - is your router correctly set up and connecting to the internet?

---

### Post by dourvas on 2015-09-26
It is a computer in a computer lab. There is a partition with windows (vista) an the network works fine. I have made the installation to 3 pcs more. not by ghosting but one by one. the problem is the same. It is probably stupid the above info but since i did that installation some other problems with the network occured like that there is no internet occasionally. probably this have not got to do with the ubuntu though.  All that in the shooll i  am working. Last night i decided to install ubuntu to my laptop. This time i needed the 64bit version. I followed the same procedure. During the installation the wifi were on. When everything finished and i boot the machine there are no wifi networks  I thought i should boot from the installation media i used (usb). And miracle! there is wifi. I am writing now from ubuntu. If i boot from the hard drive no wifi network exists or i do not now how to find it. there is no sign of it in the above gray line.  Something i am doing wrong. but what? what should i do. Please remember that i am completely novice about linux

---

### Post by dourvas on 2015-09-26
It is a computer in a computer lab. There is a partition with windows (vista) an the network works fine. I have made the installation to 3 pcs more. not by ghosting but one by one. the problem is the same. It is probably stupid the above info but since i did that installation some other problems with the network occured like that there is no internet occasionally. probably this have not got to do with the ubuntu though.

All that in the shooll i  am working. Last night i decided to install ubuntu to my laptop. This time i needed the 64bit version. I followed the same procedure. During the installation the wifi were on. When everything finished and i boot the machine there are no wifi networks

I thought i should boot from the installation media i used (usb). And miracle! there is wifi. I am writing now from ubuntu. If i boot from the hard drive no wifi network exists or i do not know how to find it. there is no sign of it in the above gray line.

Something i am doing wrong. but what? what should i do. Please remember that i am completely novice about linux

---

### Post by praseodym on 2015-09-26
Hi,

please download these files and save them in "Downloads":

[http://de.archive.ubuntu.com/ubuntu/pool/universe/r/r8168/r8168-dkms_8.040.00-1_all.deb](http://de.archive.ubuntu.com/ubuntu/pool/universe/r/r8168/r8168-dkms_8.040.00-1_all.deb)

[http://de.archive.ubuntu.com/ubuntu/pool/main/d/dkms/dkms_2.2.0.3-1.1ubuntu5_all.deb](http://de.archive.ubuntu.com/ubuntu/pool/main/d/dkms/dkms_2.2.0.3-1.1ubuntu5_all.deb)

Installation:

```
sudo dpkg -i ~/Downloads/*.deb
echo "blacklist r8169" | sudo tee -a /etc/modprobe.d/blacklist.conf 
```
Reboot.

---

### Post by dourvas on 2015-09-26
thanks for the answer. I downloaded the files using windows and i executed inside ubuntu.

Still no wifi

```


giannis@giannis-Compaq-Presario-CQ61-Notebook-PC:~$ sudo dpkg -i /home/giannis/*.deb
Selecting previously unselected package dkms.
(&#913;&#957;&#940;&#947;&#957;&#969;&#963;&#951; &#946;&#940;&#963;&#951;&#962; &#948;&#949;&#948;&#959;&#956;&#941;&#957;&#969;&#957; ... 291824 files and directories currently installed.)
Preparing to unpack .../dkms_2.2.0.3-1.1ubuntu5_all.deb ...
Unpacking dkms (2.2.0.3-1.1ubuntu5) ...
Selecting previously unselected package r8168-dkms.
Preparing to unpack .../r8168-dkms_8.040.00-1_all.deb ...
Unpacking r8168-dkms (8.040.00-1) ...
&#915;&#943;&#957;&#949;&#964;&#945;&#953; &#949;&#947;&#954;&#945;&#964;&#940;&#963;&#964;&#945;&#963;&#951; dkms (2.2.0.3-1.1ubuntu5) ...
&#915;&#943;&#957;&#949;&#964;&#945;&#953; &#949;&#947;&#954;&#945;&#964;&#940;&#963;&#964;&#945;&#963;&#951; r8168-dkms (8.040.00-1) ...
Loading new r8168-8.040.00 DKMS files...
First Installation: checking all kernels...
Building only for 3.19.0-25-generic
Building initial module for 3.19.0-25-generic
Done.

r8168:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.19.0-25-generic/updates/dkms/

depmod.......

Backing up initrd.img-3.19.0-25-generic to /boot/initrd.img-3.19.0-25-generic.old-dkms
Making new initrd.img-3.19.0-25-generic
(If next boot fails, revert to initrd.img-3.19.0-25-generic.old-dkms image)
update-initramfs....

DKMS: install completed.
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Processing triggers for initramfs-tools (0.103ubuntu4.2) ...
update-initramfs: Generating /boot/initrd.img-3.19.0-25-generic
giannis@giannis-Compaq-Presario-CQ61-Notebook-PC:~$ 
giannis@giannis-Compaq-Presario-CQ61-Notebook-PC:~$ echo "blacklist r8169" | sudo tee -a /etc/modprobe.

```


Any ideas?????????????????????
How it is possible to be connected when i boot from the installation media (usb) and not when i boot from drive? Please help

---

### Post by nknwn on 2015-09-27
Does it connect with the live disk? If yes, boot to the live disk, connect to verify the device is working for WIFI and then run the 
**sudo lshw -C network** command again. Let's see which device and driver is reported.

---

### Post by praseodym on 2015-09-27
> echo "blacklist r8169" | sudo tee -a /etc/modprobe.
It needs to be:
```

echo "blacklist r8169" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
Now run:
```

sudo modprobe -rfv r8169
sudo modprobe -v r8168
sudo service network-manager restart
```

---

### Post by dourvas on 2015-09-28
thanks for your replies.

I did not try the last 2 hints because i decided to uninstall the edubuntu 14.04 and install the ubuntu 15.04. That worked for both pc's in the lab and my labtop. No problem now (for now)

thanks

---

### Post by Bucky Ball on 2015-09-28
> **dourvas said:**
> That worked for both pc's in the lab and my labtop. No problem now (for now)



For now. In January you will need to upgrade to 15.10 if you haven't already done so by then. Interim releases are supported for nine months with a new release every six months. LTS releases have five years support. 

Anyway, all working. When you eventually get to 16.04 LTS you will be able to stay there for a few years. LTS releases can upgrade directly to the next LTS release, leap-frogging the interim releases in between. :)

Please see the first link in my signature and mark the thread as solved. Thanks.

---

