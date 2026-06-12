---
title: "Can not install ndiswrapper or wicd on Feisty x64"
date: 2007-10-20
forum: Networking &amp; Wireless
---

### Post by sethtriggs on 2007-10-20
It is absolutely impossible to get these working, and as a result, my Broadcom Airforce 4318 will refuse to work.

Here's the result of trying to get WICD installed:
```

seth@seth-laptop:~$ sudo apt-get install wicd
Reading package lists... Done
Building dependency tree       
Reading state information... Done
wicd is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up ndiswrapper (1.47) ...
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.20-16-generic/misc/ndiswrapper.ko): Invalid module format
dpkg: error processing ndiswrapper (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 ndiswrapper
E: Sub-process /usr/bin/dpkg returned an error code (1)
seth@seth-laptop:~$ 

```

And here is the trouble trying to get ndiswrapper installed:

```

FATAL: Error inserting ndiswrapper (/lib/modules/2.6.20-16-generic/misc/ndiswrapper.ko): Invalid module format
```

I'm at my wit's end with this, really! I have no idea what to do with this. Even the bcm43xx installation tools (with the python script) don't work, and I think this is the issue.

I did notice that the onboard wired LAN card and the wireless card have the same name, except the wireless uses the form eth1:avahi - while the onboard card uses eth1. Could that be the issue? I cannot find how to change that anyway and I'm worried about breaking something.

Thank you in advance! My computer information is found in my signature.


-Seth

On edit: Here is my ndiswrapper output.

```
seth@seth-laptop:~$ ndiswrapper -l
bcmwl5 : driver installed
        device (14E4:4318) present (alternate driver: bcm43xx)

```

---

### Post by sethtriggs on 2007-10-20
OK, I have discovered that wicd does operate, but cannot "see" the proper device.

I am still worried about the "avahi" thing though. Any clue as to what to do?

-Seth

On edit: I ran sudo lshw -C network
```

seth@seth-laptop:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 88E8036 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@03:00.0
       logical name: eth1
       version: 10
       serial: 00:e0:b8:8d:7c:28
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.13 firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: iomemory:d0200000-d0203fff ioport:a000-a0ff irq:18
  *-network UNCLAIMED
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@05:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: latency=64
       resources: iomemory:d0304000-d0305fff irq:10

```

Somehow I don't think this would be good. Does anyone know where I could get 64-bit drivers and ndiswrapper? Maybe that's the problem?

I'm really regretting running 64-bit here, to be honest. I probably will need to reinstall Ubuntu with a 32-bit version; there's just not a lot of 64-bit support for me it seems. (Well, where I need it most.) None of the tutorials seem to be working for me like with others.

-Seth

---

### Post by Selcal on 2007-10-28
i tried at the beginning to do the 64 thing when it came to the OS.  I ended up installing the x86 software in both of my 64 machines.  It is just easier to get software support for.

---

### Post by sethtriggs on 2007-10-28
Heh heh well I went back to 32-bit but still can't get my wireless to install. I think it's just because the Broadcom 4318 doesn't really work for Linux period; I have to wait for an improved system or something to work with mine. Hope things work for you! Linux is doing great for me otherwise.

-Seth

---

