---
title: "wireless internet"
date: 2008-07-29
forum: Networking &amp; Wireless
---

### Post by blake005 on 2008-07-29
Hi. Sorry if this is a stupid question but im really new to linux. I have a sierra wireless compass 597 usb. How can I use this to connect to the internet on Ubuntu 8.04 it wont recognize it.

---

### Post by pytheas22 on 2008-07-29
Please provide the output of:
```

lshw -C Network
lsusb
```

That will give the information needed to figure out what you have to do to make the wireless work.  The name under which the adapter is sold is not very useful, because manufacturers often change the guts of wireless cards but don't change the name on the box.

---

### Post by blake005 on 2008-07-29
lshw -c network
Hardware Lister  (lshw  -  B.02.12.01
usage:  lshw   [-format]   [options  ...]
        lshw   -version

         -version           print program version  (B.02.1.01)

foramt can be
    -html               output hardware tree as HTML
    -xml                output hardware tree as XML
    -short              output hardware paths
    -businfo            output bus information

options can be
    -class  CLASS       only show a certain class of hardware
    -C CLASS            same as '-class CLASS'
    -disable TEST       disable a test (like pci,isapnp,cpuid,ect
    -enable TEST        enable a test (like pci,isapnp,cpuid,ect.
    -quiet              dont display status
    -sanatize           sanatize output (remove sensitive information like serial numbers, etx.)

---

### Post by blake005 on 2008-07-29
lsusb
bus 005   device 005:  ID  1199:0023 Sierra Wireless, INC.

---

### Post by pytheas22 on 2008-07-29
Please run:
```

lshw -C Network
```

with a capital C (you did lowercase before :)) and post the output.

in the meantime I'm searching for the USB ID of your device.

---

### Post by amp711 on 2008-08-08
root@joekr-laptop:/home/joekr# lshw -C Network
  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wmaster0
       version: 02
       serial: 00:1c:bf:cf:9a:4a
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11g
  *-network
       description: Ethernet interface
       product: NetLink BCM5787M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:37:24:17:fc
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.86 duplex=full ip=10.22.133.63 latency=0 link=yes module=tg3 multicast=yes port=twisted pair speed=100MB/s
root@joekr-laptop:/home/joekr# lsusb
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 003: ID 1199:0023 Sierra Wireless, Inc. 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

Here mine is w/ a capital C...

Any help would be appreciated.  I know there is a guy on the EEE PC forums that got his working w/ the EEE linux distro...

---

### Post by pytheas22 on 2008-08-08
Sorry, I didn't realize what kind of a device this was at first...I thought it was just a normal USB wireless card, not a broadband modem.

The only real step-by-step directions I found for installing it are post here [here]("http://forum.eeeuser.com/viewtopic.php?id=27824").  Unfortunately I don't think there's an easier way--you will have to recompile your kernel and everything.

If you want to make it work, try following the instructions in that eeepc thread, post 8--I think that they should work in Ubuntu even though they're written for Xandros (both are based on Debian); even the Xandros repositories should work on Ubuntu.  If not, let me know which steps give you errors and we can try to work around it.

Also, as a warning, backup your data first because with recompiling the kernel and all that, there's a chance that you could break your system (shouldn't happen, but be safe).

---

