---
title: "intel driver problems..."
date: 2009-09-27
forum: New to Ubuntu
---

### Post by kayaksmak on 2009-09-27
I'm completely new to Ubuntu, and i just dual booted it onto my Dell Latitude 830.  The major problem is that the wireless doesn't connect.  I think it's that I don't have the right drivers for it.  The wireless card is an Intel 3945.  Below is the Terminal outputs for [FONT=Courier New]sudo lshw -c[/FONT] and [FONT=Courier New]iwconfig[/FONT]


> 
[FONT=Courier New]ryan@Wilder:~$ sudo lshw -C
[sudo] password for ryan: 
Hardware Lister (lshw) - B.02.13
usage: lshw [-format] [-options ...]
       lshw -version

    -version        print program version (B.02.13)

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

ryan@Wilder:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.[/FONT]


---

### Post by cariboo on 2009-09-27
The command you are looking for is:

```
sudo lshw -C network
```

This should show a list of your network devices and whether they are detected and the driver is loaded.

Paste the output of the above command in your next post.

---

### Post by kayaksmak on 2009-09-27
here's the new command.  thanks for the help!

```
ryan@Wilder:~$ sudo lshw -C network
[sudo] password for ryan: 
  *-network               
       description: Network controller
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network
       description: Ethernet interface
       product: NetXtreme BCM5755M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:21:70:70:fd:ee
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.94 duplex=full firmware=5755m-v3.29 ip=128.143.38.97 latency=0 link=yes module=tg3 multicast=yes port=twisted pair speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 1a:ca:23:b7:42:79
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
ryan@Wilder:~$ 

```

---

### Post by kayaksmak on 2009-09-28
I searched around on my own and figured out that I have a BCM4328 instead of an Intel 3945, and found a number of descriptions of 7.10 (?) and 8.04, some of which I tried.  I kind of mashed the first two together and then tried the third later.  

[http://www.micahcarrick.com/11-04-2007/ubuntu-d830-install-notes.html#4](http://www.micahcarrick.com/11-04-2007/ubuntu-d830-install-notes.html#4)
[http://hasin.wordpress.com/2008/02/27/getting-dell-bcm4328-wifi-card-working-on-ubuntu-710/](http://hasin.wordpress.com/2008/02/27/getting-dell-bcm4328-wifi-card-working-on-ubuntu-710/)
[http://ubuntuforums.org/showthread.php?t=297092&highlight=BCM4328](http://ubuntuforums.org/showthread.php?t=297092&highlight=BCM4328)

Here are the new codes, if anything's changed 
```
  
sudo lshw -C network

*-network               
       description: Network controller
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network
       description: Ethernet interface
       product: NetXtreme BCM5755M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:21:70:70:fd:ee
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.94 duplex=full firmware=5755m-v3.29 ip=128.143.35.164 latency=0 link=yes module=tg3 multicast=yes port=twisted pair speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 3e:fa:88:47:77:9e
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```

iwconfig
```

lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.


```

---

