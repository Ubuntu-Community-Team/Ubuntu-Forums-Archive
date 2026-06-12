---
title: "No ethernet in 14.04 since yesterday. Wifi works"
date: 2014-08-30
forum: Networking &amp; Wireless
---

### Post by seshomaru samma on 2014-08-30
Hi , I installed 14.04 on a Lenovo laptop and the internet was a bit slow. I followed an interent tutorial that suggested upgrading the driver, but on the next reboot there was no ethernet connection at all. The network manager is greyed but it connects to wifi fine. It's not a hardware issue cause a live USB connects to wired network fine.
Can anyone help?

```
i@Desktop:~$ sudo lshw -C network           *-network UNCLAIMED     
       description: Ethernet controller
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 10
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd cap_list
       configuration: latency=0
       resources: ioport:2000(size=256) memory:90504000-90504fff memory:90500000-90503fff
  *-network
       description: Wireless interface
       product: RTL8723BE PCIe Wireless Network Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       .....
....

```

```
i@Desktop:~$ cat /etc/network/interfaces
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback
```


```
i@Desktop:~$ sudo ifup eth0
Ignoring unknown interface eth0=eth0.
```

These are the steps I followed , I wonder if I should just reverse them :
```
 Downloaded driver and - 
sudo dkms install -m r8168-dkms -v 8.038.00

sudo modprobe -rfv r8169

sudo modprobe -v r8168

echo “blacklist r8169“ | sudo tee -a /etc/modprobe.d/blacklist.conf


 sudo depmod -a

sudo update-initramfs -u
```

---

### Post by kurt18947 on 2014-08-31
No expert in this stuff but to my newby-grade eye, it looks like you installed r8168 before removing r8169.  I wonder if there's something conflicting and breaking both? Maybe remove both, make sure the blacklist statement is doing what you want, do a restart for luck then reinstall the desired module?

---

### Post by seshomaru samma on 2014-09-02
You are right the, there was some conflict. I ended up reinstlling and now it works. Thanks

---

