---
title: "Ethernet no longer working after reboot/autoremove."
date: 2021-08-20
forum: Networking &amp; Wireless
---

### Post by dfk789 on 2021-08-20
Hi, my ethernet stopped working on my machine last night and I'm not able to get it working again.

I've tried a few things such as bunch of commands to try and reset network settings, which did not work. 
Manually installing r8168-dkms driver does not work and gives error about missing headers.

At some in trying to fix, I removed the default wired connection, from the network manager and tried to create a new one, but my ethernet does not show in the devices.
I'm really not sure what I need to do to fix it. 

I'll post below some informations I think are relevant, if you would like any more, I should be able to provide. But I am unable get internet access on this machine in any capacity right now.  

**Autoremoved packages**
```
Remove: linux-objects-nvidia-390-5.11.0-22-generic:amd64 (5.11.0-22.23), linux-modules-extra-5.11.0-22-generic:amd64 (5.11.0-22.23), wmdocker:amd64 (1.5-2), linux-image-5.11.0-22-generic:amd64 (5.11.0-22.23), linux-signatures-nvidia-5.11.0-22-generic:amd64 (5.11.0-22.23), linux-headers-5.11.0-22:amd64 (5.11.0-22.23), linux-headers-5.11.0-22-generic:amd64 (5.11.0-22.23), linux-modules-5.11.0-22-generic:amd64 (5.11.0-22.23)
End-Date: 2021-08-20  01:29:27
```

**ip link show**
```
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN mode DEFAULT group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
```

**lshw -class network**
```
  *-network UNCLAIMED       
       description: Ethernet controller
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 0c
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list
       configuration: latency=0
       resources: ioport:d000(size=256) memory:f6100000-f6100fff memory:ec100000-ec103fff
```

**networkctl list**
```
WARNING: systemd-networkd is not running, output will be incomplete.

IDX LINK TYPE     OPERATIONAL SETUP
  1 lo   loopback n/a         unmanaged

1 links listed.
```

---

### Post by linerman on 2021-08-20
> **dfk789 said:**
> 
Manually installing r8168-dkms driver does not work and gives error about missing headers.



Hi,

So you need to install headers (it is essential to build that driver)
Just follow the steps from the post:
[https://ubuntuforums.org/showthread.php?t=2456227&p=14012451#post14012451](https://ubuntuforums.org/showthread.php?t=2456227&p=14012451#post14012451)

> **dfk789 said:**
> 
At some in trying to fix, I removed the default wired connection, from the network manager and tried to create a new one, but my ethernet does not show in the devices.
I'm really not sure what I need to do to fix it. 

That NIC is buggy and it is hard to make it work without r8168 driver.
Have you got Windows OS on your computer?


> **dfk789 said:**
> 
I'll post below some informations I think are relevant, if you would like any more, I should be able to provide. But I am unable get internet access on this machine in any capacity right now.  

**Autoremoved packages**
```
Remove: linux-objects-nvidia-390-5.11.0-22-generic:amd64 (5.11.0-22.23), linux-modules-extra-5.11.0-22-generic:amd64 (5.11.0-22.23), wmdocker:amd64 (1.5-2), linux-image-5.11.0-22-generic:amd64 (5.11.0-22.23), linux-signatures-nvidia-5.11.0-22-generic:amd64 (5.11.0-22.23), linux-headers-5.11.0-22:amd64 (5.11.0-22.23), linux-headers-5.11.0-22-generic:amd64 (5.11.0-22.23), linux-modules-5.11.0-22-generic:amd64 (5.11.0-22.23)
End-Date: 2021-08-20  01:29:27
```



These files mainly have nothing to do with that driver.

---

### Post by dfk789 on 2021-08-20
> **linerman said:**
> Hi,

So you need to install headers (it is essential to build that driver)
Just follow the steps from the post:
[https://ubuntuforums.org/showthread.php?t=2456227&p=14012451#post14012451](https://ubuntuforums.org/showthread.php?t=2456227&p=14012451#post14012451)



Thank you! This helped a lot and it is now working again.

I copied over the linux header packages I needed and got those installed. After that the driver showed as installed but was still not working.

So I just grabbed the latest driver from the realtek website, ran the script and it is now working.

Much appreciated!

---

### Post by linerman on 2021-08-20
Good!
Remember to always have on the disk that installation driver in case you will be out of the net again.
(That could happen if you blacklisted r8169 driver and will upgrade the kernel - so be aware of the fact that in such situation, after upgrading the kernel, you would need to repeat the process of installing driver again).

Also, if you have Windows OS and reboot that system instead of shutting down, you would have not ethernet again as I wrote here:
[https://ubuntuforums.org/showthread.php?t=2461096&page=2&p=14038009#post14038009](https://ubuntuforums.org/showthread.php?t=2461096&page=2&p=14038009#post14038009)

---

