---
title: "Ethernet network card malfunctioning after upgrade"
date: 2020-11-01
forum: Networking &amp; Wireless
---

### Post by ra542 on 2020-11-01
Hello,

I was wondering if someone can point to the right direction with this problem.

A little back story:
I had ubuntu server 18 installed in my box (HP Z240) and everything was working fine. I decided to upgrade to ubuntu 20.04.01.
The upgrade ran successfully, however, I experienced a problem with the internet connection as I had no internet / no LAN ip address.
Initially, the problem was the netplan was not setup correctly, I changed it as follows

```

network:
    version: 2
    renderer: networkd
    ethernets:
        eno1:
             dhcp4: true

```

then ran
```

sudo netplan generate
sudo netplan apply

```

And it appeared that that had worked. I started getting an IP address and internet access, however, when I download upgrades for applications (**sudo apt-get install **x), the blinking lights on the ethernet port stop blinking and if immediately do an **ifconfig**, I no longer have the LAN ip nor internet access. After the sudo apt-get install times out and errors out, the lights start blinking again and I have internet back.

This is the result of **sudo lshw -c network**
```
  
*-network                 
       description: Ethernet interface
       product: Ethernet Connection (2) I219-LM
       vendor: Intel Corporation
       physical id: 1f.6
       bus info: pci@0000:00:1f.6
       logical name: eno1
       version: 31
       serial: 18:60:24:8a:8b:bc
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=3.2.6-k duplex=full firmware=0.8-4 ip=192.168.1.110 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:122 memory:d0000000-d001ffff

```

And this is the kernel version
```

5.4.0-52-generic

```

Ubuntu Version
```

"20.04.1 LTS (Focal Fossa)"

```

Your help will  be greatly appreciated as I don't know what's causing this problem.


Thanks,

---

### Post by daithi_dearg on 2020-11-03
Have you already tried hitting escape as the machine is booting and going into the advanced menu and seeing if this works with a different kernel.

I'm having issues with an Intel WiFI card since upgrading the kernel and wonder could it be something similar.

Haven't completely figured it out myself but looks like driver is missing in latest kernel. Not sure if this helps:

```
david@david-N7x0WU:~$ uname -r
5.4.0-42-generic

david@david-N7x0WU:~$ ls -ltr /boot/initrd.img*
lrwxrwxrwx 1 root root       27 Oct 21 08:11 /boot/initrd.img.old -> initrd.img-5.4.0-45-generic
lrwxrwxrwx 1 root root       27 Oct 21 08:11 /boot/initrd.img -> initrd.img-5.4.0-51-generic
-rw-r--r-- 1 root root 36294669 Oct 21 11:09 /boot/initrd.img-5.4.0-45-generic
-rw-r--r-- 1 root root 82535585 Oct 21 11:10 /boot/initrd.img-5.4.0-42-generic
-rw-r--r-- 1 root root 36304316 Nov  3 11:50 /boot/initrd.img-5.4.0-51-generic

david@david-N7x0WU:~$ ls /lib/modules/*/kernel/drivers/net/wireless/intel/iwlwifi/
dvm  iwlwifi.ko  mvm

david@david-N7x0WU:~$ ls /lib/modules/*/kernel/drivers/
/lib/modules/5.4.0-42-generic/kernel/drivers/:
acpi        bcma       cpufreq  edac      gpio     hwmon       input         leds       media     mtd     nvmem    platform  rapidio    siox       ssb          uio     visorbus
android     block      cpuidle  extcon    gpu      hwtracing   interconnect  lightnvm   memstick  net     parport  power     regulator  slimbus    staging      usb     vme
ata         bluetooth  crypto   firewire  greybus  i2c         iommu         macintosh  message   nfc     pci      powercap  reset      soc        target       vfio    w1
atm         char       dax      firmware  hid      i3c         ipack         mailbox    mfd       ntb     pcmcia   pps       rpmsg      soundwire  thermal      vhost   watchdog
auxdisplay  clk        dca      fpga      hsi      iio         irqchip       mcb        misc      nvdimm  phy      ptp       rtc        spi        thunderbolt  video   xen
base        counter    dma      gnss      hv       infiniband  isdn          md         mmc       nvme    pinctrl  pwm       scsi       spmi       tty          virtio

/lib/modules/5.4.0-45-generic/kernel/drivers/:
acpi  bcma   char    dca       gpu  hv   infiniband  md       mfd   net   parport  pcmcia  ssb     tty  usb   vhost  virtio    xen
ata   block  crypto  firmware  hid  i2c  input       message  misc  nvme  pci      scsi    target  uio  vfio  video  watchdog

/lib/modules/5.4.0-51-generic/kernel/drivers/:
acpi  bcma   char    dca       gpu  hv   infiniband  md       mfd   net   parport  pcmcia  ssb     tty  usb   vhost  virtio    xen
ata   block  crypto  firmware  hid  i2c  input       message  misc  nvme  pci      scsi    target  uio  vfio  video  watchdog

```

---

