---
title: "Network card disappeared?"
date: 2006-12-08
forum: Networking &amp; Wireless
---

### Post by bradsucks on 2006-12-08
I was moving some hard drives around between computers this morning and hooking a new Ubuntu box up to the network. Eventually I put things back the way they were. When I went back to my old Linux box my network had stopped working. I can ping localhost but nothing else. The Network Settings panel doesn't even see there's a network device in the computer anymore.

I thought maybe the cable was bad or the machine had broken in some way so I booted to the Ubuntu live cd and the network works fine. Rebooting into my Ubuntu install it no longer does.

I read some network troubleshooting guides, lsmod doesn't show my interface, lspci does. I'm kind of at a loss for what else to try. 

The network card is an on-board SIS900, I'm running Ubuntu 6.10. Thanks for any help you can give me.

---

### Post by dbott67 on 2006-12-08
Seeing as the Live CD works, you could try the following:
1. Boot from the CD
2. Copy the Live CD version of **/etc/network/interfaces** to floppy or USB drive (or directly to the existing Ubuntu installation)
3. Re-boot
4. Backup the existing installation **/etc/network/interfaces** and replace with the one from floppy/USB
```
sudo mv /etc/network/interfaces /etc/network/interfaces.bak
```
```
sudo cp /path/to/working/interfaces /etc/network/interfaces
```
5. Restart the network
```
sudo/etc/init.d/networking restart
```

Failing that, can you copy & paste the output of the following commadns to a text file & save it to USB/floppy and bring it over to a working computer:

```
cat/etc/network/interfaces
```

Here's mine as an example:

```
dbott@dapper:~$ cat/etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
wireless-essid bott
wireless-key s:mysecretwepkey
```

This command shows ALL network interfaces on the system (whether enabled or not):

```
ifconfig -a
```

```
dbott@dapper:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:15:C5:0C:AD:XX
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:217

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:438044459 errors:0 dropped:0 overruns:0 frame:0
          TX packets:438044459 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1712747473 (1.5 GiB)  TX bytes:1712747473 (1.5 GiB)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:16:CE:31:88:XX
          inet addr:192.168.1.105  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:ceff:fe31:886f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:738503 errors:0 dropped:0 overruns:0 frame:0
          TX packets:500344 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:658372626 (627.8 MiB)  TX bytes:64530804 (61.5 MiB)
          Interrupt:169 Memory:dfcfc000-dfd00000
```

This command outputs the network hardware detected:

```
sudo lshw -C network
```

Here's mine for comparison:

```
dbott@dapper:~$ sudo lshw -C network
Password:
  *-network
       description: Wireless interface
       product: Broadcom Corporation
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0b:00.0
       logical name: wlan0
       version: 01
       serial: 00:16:ce:31:88:6f
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper driverversion=1.25 firmware=Broadcom,11/02/2005, 4.10.40.0 ip=192.168.1.105 link=yes multicast=yes wireless=IEEE 802.11b
       resources: iomemory:dfcfc000-dfcfffff irq:169
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@03:00.0
       logical name: eth0
       version: 02
       serial: 00:15:c5:0c:ad:05
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=b44 driverversion=0.97 duplex=half link=no multicast=yes port=twisted pair speed=10MB/s
       resources: iomemory:df9fe000-df9fffff irq:217

```

Thanks,
Dave

---

### Post by bradsucks on 2006-12-08
Thanks a lot for your reply. Okay I grabbed the interfaces file off  the live cd and it made no difference. The interfaces file was this:

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp 
```

On network restart I get this:

```

* Configuring network interfaces...

Failed to bring up eth0.
Failed to bring up eth1.
Failed to bring up eth2.
Failed to bring up ath0.
Failed to bring up wlan0.


```

Output of ifconfig -a:

```

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:172 (172.0 b)  TX bytes:172 (172.0 b)
 
```

Output of lshw -C network:

```

  *-network UNCLAIMED
       description: Ethernet controller
       product: SiS900 PCI Fast Ethernet
       vendor: Silicon Integrated Systems [SiS]
       physical id: 1.1
       bus info: pci@00:01.1
       version: 82
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       resources: ioport:e000-e0ff iomemory:ec121000-ec121fff irq:11 

```

I tried a few other things, like checking my MAC address and so on. No luck so far...

---

### Post by dbott67 on 2006-12-08
When you're running the Live Cd, can you please post the output of the following commands:
```
ifconfig -a
```
```
sudo lshw -C network
```
Because the Live CD works, this should reveal the driver and we can try to load it manually.

-Dave

---

### Post by bradsucks on 2006-12-08
ifconfig -a on the live cd:

```

eth0      Link encap:Ethernet  HWaddr 00:0A:E6:47:B5:CD  
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20a:e6ff:fe47:b5cd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:241 errors:0 dropped:0 overruns:0 frame:0
          TX packets:125 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:29170 (28.4 KiB)  TX bytes:14388 (14.0 KiB)
          Interrupt:11 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:458 errors:0 dropped:0 overruns:0 frame:0
          TX packets:458 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:22900 (22.3 KiB)  TX bytes:22900 (22.3 KiB)

sit0      Link encap:IPv6-in-IPv4  
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```

lshw -C network:

```

  *-network
       description: Ethernet interface
       product: SiS900 PCI Fast Ethernet
       vendor: Silicon Integrated Systems [SiS]
       physical id: 1.1
       bus info: pci@00:01.1
       logical name: eth0
       version: 82
       serial: 00:0a:e6:47:b5:cd
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=sis900 driverversion=v1.08.09 Sep. 19 2005 duplex=full ip=192.168.1.103 link=yes multicast=yes port=MII speed=100MB/s
       resources: ioport:e000-e0ff iomemory:ec121000-ec121fff irq:11

```

---

### Post by dbott67 on 2006-12-09
> **bradsucks said:**
> ifconfig -a on the live cd:

```

eth0      Link encap:Ethernet  HWaddr 00:0A:E6:47:B5:CD  
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20a:e6ff:fe47:b5cd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:241 errors:0 dropped:0 overruns:0 frame:0
          TX packets:125 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:29170 (28.4 KiB)  TX bytes:14388 (14.0 KiB)
          Interrupt:11 Base address:0xe000

```

lshw -C network:

```

  *-network
       description: Ethernet interface
       product: SiS900 PCI Fast Ethernet
       vendor: Silicon Integrated Systems [SiS]
       physical id: 1.1
       bus info: pci@00:01.1
       logical name: eth0
       version: 82
       serial: 00:0a:e6:47:b5:cd
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes **[COLOR="Red"]driver=sis900[/COLOR]** driverversion=v1.08.09 Sep. 19 2005 duplex=full ip=192.168.1.103 link=yes multicast=yes port=MII speed=100MB/s
       resources: ioport:e000-e0ff iomemory:ec121000-ec121fff irq:11

```

Okay, the output above tells me that your NIC uses the 'sis900' driver.

If you list all loaded modules (when booted up from the hard drive, not the Live CD) you *should* see the sis900 module:
```
lsmod | grep sis900
```
or to show all presently loaded modules
```
lsmod
```

If the sis900 module does not show up, then we can try loading it manually:
```
sudo modprobe sis900
```
Check the end of the dmesg log for any errors:
```
dmesg
```

Then take another look at **ifconfig -a** & see if you have an 'eth0'.  If so, re-start the network '**sudo/etc/init.d/networking restart**' and pray.

Otherwise, you may need to do a re-install as something is very goofy.

-Dave

---

### Post by bradsucks on 2006-12-09
The plot thickens.

I rebooted to try your suggestions and Ubuntu scanned my hard drive on the 30th boot. It found some "bad or duplicate blocks". I rebooted to the live CD, mounted the drive and fsck'd it and it found a lot of cloned/duplicated blocks. I repaired them all, rebooted and tried your suggestions.

lsmod didn't show the sis900 driver, modprobe showed this:

```
WARNING: /lib/modules/2.6.15-27-386/modules.alias line 1: ignoring bad line starting with 'ELF'
WARNING: /lib/modules/2.6.15-27-386/modules.alias line 2: ignoring bad line starting with ''
WARNING: /lib/modules/2.6.15-27-366/modules.alias line 3: ignoring bad line starting with ''
FATAL: Modules sis900 not found.
```

So now I'm assuming my hard drive has managed to eat the driver somehow.

---

### Post by dbott67 on 2006-12-09
The scan on every 30 boots is normal, but the bad blocks could spell trouble.  Something is definitely amiss... maybe a re-install is necessary.

Did you ever edit/modify the **/lib/modules/2.6.15-27-366/modules.alias** file?  If so, you may just want to replace it with the one from the Live CD as you did with the other files in Post #2.

-Dave

---

### Post by bradsucks on 2006-12-09
Nope, I definitely didn't modify that file.

I think I'm going to assume that this computer is haunted and this is a sign that I should upgrade to the new machine rather than try to salvage this one. 

Thanks for all your help, it's been frustrating but I've learned a lot about Linux and specifically Linux networking in the process.

---

