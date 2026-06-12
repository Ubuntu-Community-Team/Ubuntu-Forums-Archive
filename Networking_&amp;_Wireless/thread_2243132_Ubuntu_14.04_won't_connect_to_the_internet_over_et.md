---
title: "Ubuntu 14.04 won't connect to the internet over ethernet"
date: 2014-09-06
forum: Networking &amp; Wireless
---

### Post by veldermanb on 2014-09-06
I have just set up Ubuntu as a dual boot with my windows 7 machine and I haven't been able to get it to connect yet. It always just says connecting for about a minute or two and then says you are disconnected. Thanks for the help.

---

### Post by roger_1960 on 2014-09-06
Hi

Try this:

Boot to windows, connect to internet.  _Make sure_ networking is connected when you quit windows; Reboot in ubuntu.

Roger

---

### Post by veldermanb on 2014-09-06
The internet has been working on windows and still does when I boot back into it.

---

### Post by varunendra on 2014-09-06
Welcome to the forums veldermanb!

Please open a terminal (Ctrl-Alt-T) and post back the outputs of the following commands -
```
sudo lshw -C network
sudo ethtool eth0
```

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Use Code Tags" link in my signature.

---

### Post by veldermanb on 2014-09-08
I think I have found the problem. I didn't install any drivers on Linux. And as gigabyte has no support for Linux it looks like I am screwed.

---

### Post by chili555 on 2014-09-08
> **veldermanb said:**
> I think I have found the problem. I didn't install any drivers on Linux. And as gigabyte has no support for Linux it looks like I am screwed.Based upon what? If you'll post the information requested, I'm quite sure Varun can help. Neither he nor anyone else can help with no clues to go on.

---

### Post by QIII on 2014-09-08
Hello!

I have several Gigabyte boards and have never had trouble with them.

With the possible exception of wireless (which generally works but every so often requires some fiddling with certain chipsets) all the drivers you need are already in the kernel or will be put there when you install.

Unlike Windows, you do not need to run a driver disk.

---

### Post by veldermanb on 2014-09-08
Oh ok sorry the idiots I work with apparently don't know what they are talking about. I will get the results of those commands tomorrow since it is really late here.

---

### Post by veldermanb on 2014-09-09
ok for
```
sudo lshw -C network
```
i got this
```
  *-network                      description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 06
       serial: 74:d4:35:99:90:cf
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168e-3_0.0.4 03/27/12 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:73 ioport:d000(size=256) memory:fe800000-fe800fff memory:d0000000-d0003fff
  *-network               
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 06
       serial: 74:d4:35:99:90:cf
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168e-3_0.0.4 03/27/12 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:73 ioport:d000(size=256) memory:fe800000-fe800fff memory:d0000000-d0003fff




```
and for
```
sudo ethtool eth0
```
I got this
```
Settings for eth0:    Supported ports: [ TP MII ]
    Supported link modes:   10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Half 1000baseT/Full 
    Supported pause frame use: No
    Supports auto-negotiation: Yes
    Advertised link modes:  10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Half 1000baseT/Full 
    Advertised pause frame use: Symmetric Receive-only
    Advertised auto-negotiation: Yes
    Link partner advertised link modes:  10baseT/Half 10baseT/Full 
                                         100baseT/Half 100baseT/Full 
    Link partner advertised pause frame use: Symmetric
    Link partner advertised auto-negotiation: Yes
    Speed: 100Mb/s
    Duplex: Full
    Port: MII
    PHYAD: 0
    Transceiver: internal
    Auto-negotiation: on
    Supports Wake-on: pumbg
    Wake-on: g
    Current message level: 0x00000033 (51)
                   drv probe ifdown ifup
    Link detected: yes



```

---

### Post by varunendra on 2014-09-10
Everything looks good to me in the outputs. Can you try manual assignment of IP in Network Manager? If you don't know what I'm talking about, please try this in a terminal -
```
sudo ifconfig eth0 down
sudo ifconfig eth0 192.168.1.100
```
..assuming the IPs on your local network are of the pattern 192.168.1.xx, and '...100' is not already in use by any other device. Does it let you connect (to the local network only. For internet, you'll need some extra steps).

If none of the above makes any sense, can you tell us what your Router's IP is?

---

### Post by veldermanb on 2014-09-12
Ok so I tried what you said and it seemed to do nothing but I piggybacked on your idea and manually set my ipv4 address. When I just put in the address (which will be 192.168.254.25 for future reference), the netmask, and the gateway it immediately connected but when I went on the internet it immediately said no connection. I them snooped around my router a little more and found the DNS server ip and I put that into the configuration. It then took a few seconds to connect and when I went on the internet it just said connecting forever. Also during both of these tests I tried to connect to my router through the internet to test the local network and it didn't work either time. I hope some of this info helps with my problem.

---

### Post by varunendra on 2014-09-12
Something I forgot to mention in my previous post, and it is very important!

Newer Gigabyte motherboards have a feature called "IOMMU" in their BIOS setup. It happens very often that users need to enable it (by default it is disabled). Please try that if you haven't already.

If this works, you can keep it that way (if it doesn't cause any other troubles in Ubuntu or Windows part), or try a boot-option "iommu=soft". Let me know the result of the test and I'll elaborate the boot-option if required.

---

### Post by veldermanb on 2014-09-13
> **varunendra said:**
> Something I forgot to mention in my previous post, and it is very important!

Newer Gigabyte motherboards have a feature called "IOMMU" in their BIOS setup. It happens very often that users need to enable it (by default it is disabled). Please try that if you haven't already.

If this works, you can keep it that way (if it doesn't cause any other troubles in Ubuntu or Windows part), or try a boot-option "iommu=soft". Let me know the result of the test and I'll elaborate the boot-option if required.

I couldn't find that in the bios what would it be under? Also I have a gigabyte g970a-ds3p if that helps

---

### Post by praseodym on 2014-09-13
Download these 2 files and save them in "Downloads":

[http://media.cdn.ubuntu-de.org/forum/attachments/45/14/3005217-r8168-dkms-8.038.00.tar.gz](http://media.cdn.ubuntu-de.org/forum/attachments/45/14/3005217-r8168-dkms-8.038.00.tar.gz)

[http://de.archive.ubuntu.com/ubuntu/pool/main/d/dkms/dkms_2.2.0.3-1.1ubuntu5_all.deb](http://de.archive.ubuntu.com/ubuntu/pool/main/d/dkms/dkms_2.2.0.3-1.1ubuntu5_all.deb)

Installation:

```
cd ~/Downloads/
sudo dpkg -i *.deb
sudo tar xvf 3005217-r8168-dkms-8.038.00.tar.gz -C /usr/src
sudo dkms add -m r8168-dkms -v 8.038.00
sudo dkms build -m r8168-dkms -v 8.038.00
sudo dkms install -m r8168-dkms -v 8.038.00
sudo depmod -a
sudo update-initramfs -u 
echo "blacklist r8169" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
Reboot. This changes the driver from r8169 to r8168

---

### Post by varunendra on 2014-09-13
> **veldermanb said:**
> I couldn't find that in the bios what would it be under? Also I have a gigabyte g970a-ds3p if that helps

I don't have any gigabyte mobo around to check that, but I guess it should be under "Advanced BIOS Features" or "Chipset Configuration" (or something alike). Your motherboard is indeed a new model, so I'm pretty sure it should have this feature, disabled by default.

---

### Post by veldermanb on 2014-09-16
> **varunendra said:**
> I don't have any gigabyte mobo around to check that, but I guess it should be under "Advanced BIOS Features" or "Chipset Configuration" (or something alike). Your motherboard is indeed a new model, so I'm pretty sure it should have this feature, disabled by default.
That worked perfectly thank you!

---

### Post by varunendra on 2014-09-17
You're welcome! :)

---

### Post by kyle47 on 2015-05-11
The BIOS fix worked for me as well. Thank you!

---

