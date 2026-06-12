---
title: "fixed sdound now net not working..."
date: 2007-05-21
forum: Networking &amp; Wireless
---

### Post by djbenny on 2007-05-21
i did this to make the sound work:
> ## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
## kopt_2_6_8=root=/dev/hdc1 ro
## kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=/dev/sda1 ro acpi=off

#### DELETED STUFF #####

## ## End Default Options ##

title Ubuntu, kernel 2.6.15-26-686
root (hd0,0)
kernel /boot/vmlinuz-2.6.15-26-686 root=/dev/sda1 ro quiet splash acpi=off
initrd /boot/initrd.img-2.6.15-26-686
savedefault
boot

then i had to reconfigure the xorg file so i did that, rebooted now i have sound but no internet?

---

### Post by djbenny on 2007-05-21
need this sorted urgently!

---

### Post by djbenny on 2007-05-21
is it not possible to fix?

---

### Post by Kobalt on 2007-05-21
how do you connect to the internet ?

---

### Post by djbenny on 2007-05-21
via ethernet LAN wired connection

it was working before hand though!

---

### Post by djbenny on 2007-05-22
any ideas?

---

### Post by djbenny on 2007-05-22
info bout network:


  *-network               
       description: Ethernet interface
       product: 82573L Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@02:00.0
       logical name: eth0
       version: 00
       serial: 00:16:36:4b:14:3d
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.15-k2-NAPI firmware=0.5-5 latency=0 link=no multicast=yes port=twisted pair
       resources: iomemory:d2000000-d201ffff ioport:3000-301f irq:17
  
*-network
       description: Network controller
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@03:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=ipw3945 latency=0
       resources: iomemory:d2200000-d2200fff irq:17

---

