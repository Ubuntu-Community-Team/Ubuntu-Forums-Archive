---
title: "WIFI laptop MSI Winf U160"
date: 2010-10-09
forum: New to Ubuntu
---

### Post by SG12010 on 2010-10-09
Hi

Dose anyone know how to  get WIFI working for a laptop MSI Wind U160 on ubuntu  9.10

Thanks SG.

---

### Post by lbrty on 2010-10-09
Have you tried the following?

System>Administration>Hardware Drivers

Once you click Hardware Drivers, it will present drivers not activated. Click the desired driver(s) and click Activate.

---

### Post by anewguy on 2010-10-10
If the above didn't work, there are other ways to try to get things going.

The preferred method would be:

- temporarily hard-wire your laptop to the router
- open a terminal window (Applications/Accessories/Terminal) and type:

sudo apt-get update <press enter>  When promted, enter your normal password (it won't show on the screen).  Let this step finish before moving on.

- NOW do as suggested - look in System/Adminnistration/Hardware Drivers and see if a driver is listed for your adapter - if so, enable it.  It may download something from the net then.

- physically disconnect the hard-wire connection to your router

- right-click the network manager icon - be sure "Enable Wireless" is checked

- left-click the network manager icon and see if wireless networks now show

- remember that if you use encryption you will need to supply the type and the password/passphrase when you try to connect

- if you use MAC filtering on the router, be sure to update the table to include the MAC of this laptop

If you can't do the above, then please do the following:

- open a terminal window (Applications/Accessories/Terminal)
- type each of the following and post the outputs back here in a reply:

lscpi <press enter>

lsusb <press enter>

ifconfig <press enter>

iwconfig <press enter>

lshw -C network <press enter>

This will give us more information to go on to try to help you.

Dave ;)

---

### Post by SG12010 on 2010-10-10
I tried the two options without any success here is the read out from terminal.


Thanks SG


$ lscpi
No command 'lscpi' found, did you mean:
 Command 'lscpu' from package 'util-linux' (main)
 Command 'lspci' from package 'pciutils' (main)
 Command 'lscp' from package 'nilfs2-tools' (universe)
lscpi: command not found

laptop:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

ifconfig
eth0      Link encap:Ethernet  HWaddr 40:61:86:ae:bc:d1  
          inet addr:192.168.2.3  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::4261:86ff:feae:bcd1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4125 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3569 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4624016 (4.6 MB)  TX bytes:564204 (564.2 KB)
          Interrupt:28 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:39 errors:0 dropped:0 overruns:0 frame:0
          TX packets:39 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4110 (4.1 KB)  TX bytes:4110 (4.1 KB)



iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.


laptop:~$ lshw C network
Hardware Lister (lshw) - B.02.14
usage: lshw [-format] [-options ...]
       lshw -version

    -version        print program version (B.02.14)

format can be
    -html           output hardware tree as HTML
    -xml            output hardware tree as XML
    -short          output hardware paths
    -businfo        output bus information

options can be
    -class CLASS    only show a certain class of hardware
    -C CLASS        same as '-class CLASS'
    -c CLASS        same as '-class CLASS'
    -disable TEST   disable a test (like pci, isapnp, cpuid, etc. )
    -enable TEST    enable a test (like pci, isapnp, cpuid, etc. )
    -quiet          don't display status
    -sanitize       sanitize output (remove sensitive information like serial numbers, etc.)
    -numeric        output numeric IDs (for PCI, USB, etc.)

zen@zen-laptop:~$ 














> **anewguy said:**
> If the above didn't work, there are other ways to try to get things going.

The preferred method would be:

- temporarily hard-wire your laptop to the router
- open a terminal window (Applications/Accessories/Terminal) and type:

sudo apt-get update <press enter>  When promted, enter your normal password (it won't show on the screen).  Let this step finish before moving on.

- NOW do as suggested - look in System/Adminnistration/Hardware Drivers and see if a driver is listed for your adapter - if so, enable it.  It may download something from the net then.

- physically disconnect the hard-wire connection to your router

- right-click the network manager icon - be sure "Enable Wireless" is checked

- left-click the network manager icon and see if wireless networks now show

- remember that if you use encryption you will need to supply the type and the password/passphrase when you try to connect

- if you use MAC filtering on the router, be sure to update the table to include the MAC of this laptop

If you can't do the above, then please do the following:

- open a terminal window (Applications/Accessories/Terminal)
- type each of the following and post the outputs back here in a reply:

lscpi <press enter>

lsusb <press enter>

ifconfig <press enter

iwconfig <press enter>

lshw -C network <press enter>

This will give us more information to go on to try to help you.

Dave ;)

---

### Post by bkratz on 2010-10-10
He/she actually wanted

lspci

and just misstyped it.
(that is LSPCI ) in lowercase

---

### Post by QLee on 2010-10-10
Oh my! the fates seem to have ganged up on you in this issue. First, anewguy, made a typo and the first suggestion should have been,  
lspci <press enter>,
then, you mis typed the,
lshw -C network <press enter>,
by leaving off the "-",
so, not as much information as anewguy requested.

However,

[QUOTE=SG12010]...
ifconfig
eth0      Link encap:Ethernet  HWaddr 40:61:86:ae:bc:d1  
          inet addr:192.168.2.3  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::4261:86ff:feae:bcd1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4125 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3569 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4624016 (4.6 MB)  TX bytes:564204 (564.2 KB)
          Interrupt:28 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:39 errors:0 dropped:0 overruns:0 frame:0
          TX packets:39 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4110 (4.1 KB)  TX bytes:4110 (4.1 KB)[/QUOTE]

shows us that you don't have a wireless interface configured, you do have a wired interface and it has obtained an IP address (likely through DHCP from your gateway/router).

If I saw those conditions on my system, I would continue on with anewguy's advice from "The preferred method would be:" since it looks like you already have the wired connection plugged in. It looks like anewguy isn't around at the moment, that's why I commented, in case you wanted to continue, no problem if you want to wait for someone you trust, I think that prudent.

---

### Post by SG12010 on 2010-10-12
I have actvated the WiFi, still no success, plus tried the other suggestions.


Since the Wifi has been activated I shall try those commands again.

lscpi
No command 'lscpi' found, did you mean:
 Command 'lscpu' from package 'util-linux' (main)
 Command 'lspci' from package 'pciutils' (main)
 Command 'lscp' from package 'nilfs2-tools' (universe)
lscpi: command not found

lsusb 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

 ifconfig
eth0      Link encap:Ethernet  HWaddr 40:61:86:ae:bc:d1  
          inet addr:192.168.2.3  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::4261:86ff:feae:bcd1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2823 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2447 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3410153 (3.4 MB)  TX bytes:358609 (358.6 KB)
          Interrupt:28 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:38 errors:0 dropped:0 overruns:0 frame:0
          TX packets:38 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4058 (4.0 KB)  TX bytes:4058 (4.0 KB)


iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.


lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 02
       serial: 40:61:86:ae:bc:d1
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI ip=192.168.2.3 latency=0 multicast=yes
       resources: irq:28 ioport:e000(size=256) memory:e2110000-e2110fff(prefetchable) memory:e2100000-e210ffff(prefetchable) memory:fe000000-fe01ffff(prefetchable)
  *-network UNCLAIMED
       description: Network controller
       product: RT3090 Wireless 802.11n 1T/1R PCIe
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0
       resources: memory:fd600000-fd60ffff
zen@zen-laptop:~$ 



Thanks SG1

---

### Post by SG12010 on 2010-10-14
Unsolved

---

