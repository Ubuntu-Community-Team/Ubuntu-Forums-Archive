---
title: "network not connecting on MSI GE62 with Killer Shield card"
date: 2016-02-24
forum: Networking &amp; Wireless
---

### Post by Dolphik on 2016-02-24
Hello,

I'm running a MSI GE62 laptop and after installing ubuntu 14.04 networking is only in tether mode from my mobile phone connected over usb. I've tried solutions from atheros posts but it wasn't working

In attachment I've added wireless_info.txt and additionally for quick review:

```
dolph@dolph-MSI:~$ sudo lshw -class network
  *-network UNCLAIMED     
       description: Network controller
       product: Wireless 3165
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 81
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:df300000-df301fff
  *-network UNCLAIMED
       description: Ethernet controller
       product: Qualcomm Atheros
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 10
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi msix bus_master cap_list
       configuration: latency=0
       resources: memory:df200000-df23ffff ioport:d000(size=128)
  *-network
       description: Ethernet interface
       physical id: 2
       logical name: usb0
       serial: 3e:bc:a8:5d:96:ee
       capabilities: ethernet physical
       configuration: broadcast=yes driver=rndis_host driverversion=22-Aug-2005 firmware=RNDIS device ip=192.168.42.51 link=yes multicast=yes


```

Any ideas how to solve it?

---

### Post by jeremy31 on 2016-02-24
Ethernet should work after ```
sudo -i
modprobe alx
echo '1969 e0a1' > /sys/bus/pci/drivers/alx/new_id
exit
```

For wireless ```
sudo apt-get install linux-headers-generic build-essential
wget https://www.kernel.org/pub/linux/kernel/projects/backports/2015/12/18/backports-20151218.tar.gz
tar -zvxf backports-20151218.tar.gz
cd backports-20151218
make defconfig-iwlwifi
make
sudo make install
```

And to make ethernet work after reboot
```
gksudo gedit /etc/rc.local
```

Enter the following two lines above the last line which needs to be exit 0
```
modprobe alx
echo '1969 e0a1' > /sys/bus/pci/drivers/alx/new_id
```

Save, exit program, and reboot

With any luck ethernet and wireless should both work

---

### Post by Dolphik on 2016-02-25
Everything works! Many thanks for help!

---

### Post by jeremy31 on 2016-02-25
After a kernel update you might lose wireless again, if that happens
```
cd backports-20151218
make defconfig-iwlwifi
make
sudo make install
```
Reboot

---

