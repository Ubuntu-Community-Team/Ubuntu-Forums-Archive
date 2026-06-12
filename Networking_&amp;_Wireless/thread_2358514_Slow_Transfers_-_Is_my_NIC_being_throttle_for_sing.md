---
title: "Slow Transfers - Is my NIC being throttle for single files"
date: 2017-04-14
forum: Networking &amp; Wireless
---

### Post by Fizziks on 2017-04-14
Hi everyone,

Just curious about this weird behavior. With the following situation the first thing that came to mind was Ubuntu was network throttling but I could be wrong.

Windows 10 completely saturate 1Gb network transfers from Synology to PC.

Ubuntu 17.04 the same file transfers at 45.8MB/sec. I thought it might be a driver support issue, but I started a second transfer while the first was running, I got a combined speed of 81.3MB/s. I matched this combined speed with System Monitor and also the stats in Synology's Performance Monitor.

Doesn't this mean the NIC is capable of something faster. Strange that when transferring only one file at a time I don't get full speed. 

I have the following hardware everything is super faster locally, just the NIC performance that seems to be an issue.

motherboard [https://www.asus.com/au/Motherboards/PRIME-B250M-A/specifications/](https://www.asus.com/au/Motherboards/PRIME-B250M-A/specifications/)
storage Samsung 960 EVO, also a 4 SATA disks (zpool with raidz)
64GB RAM.

---

### Post by TheFu on 2017-04-14
Welcome to the forums.

There are many possible causes for the issue, including things that MS-windows does to the NIC leaving it is an odd state that it ignores, but the specs say shouldn't be ignored.  This is unlikely, however.  It is probably a a driver or driver setting.  Can't tell from the information provided. Sorry.

**sudo lshw -C network** output will help. Please use 'code tags' so things line up.  Also, if you can use mbits/sec - that is the normal way to show throughput. If not, be very careful to not mix MB/s and Mb/s.

Some **iperf** tests would be helpful too.

---

### Post by Fizziks on 2017-04-14
Thanks. I will post the lshw for now and figure out the iperf 

```
  *-network                 
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: enp2s0
       version: 15
       serial: 70:4d:7b:85:70:70
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168h-2_0.0.2 02/26/15 ip=10.6.0.43 latency=0 link=yes multicast=yes port=MII speed=1Gbit/s
       resources: irq:123 ioport:e000(size=256) memory:f7104000-f7104fff memory:f7100000-f7103fff
```

---

### Post by Fizziks on 2017-04-14
I performed another quick test.

I created a samba share on the Ubuntu PC. Then used a Windows PC to copy files to and from that share. I was able to saturate the network link.

I think I will try and perform file transfers using Ubuntu's CLI. I think the Ubuntu GUI is causing the issue somehow.

---

### Post by TheFu on 2017-04-14
I only get 65-75MB/s over samba on my GigE links once the disk buffers are full.  iperf shows 920-940 Mbps (which is about the best possible, in an ideal world).  You can use **free -mh** to see the buffer use.

Using **rsync** or **scp** generally gets much slower (45-50MB/s), but they are habits and much more convenient for me. Being slightly slower, but having an encrypted tunnel is worth it.  Most of my file transfers are batch processing for video stuff anyway.

I haven't used a GUI to transfer files on Linux/Unix in a very long time.  Just isn't something I do much. Sorry.

BTW, the driver doesn't match the product description for your card.  Might google to see if that matters for Ubuntu. I'm not a fan of realtek stuff.

---

### Post by Fizziks on 2017-04-14
No problem. Thanks for your help.

---

### Post by TheFu on 2017-04-15
[https://unixblogger.com/2016/08/11/how-to-get-your-realtek-rtl8111rtl8168-working-updated-guide/](https://unixblogger.com/2016/08/11/how-to-get-your-realtek-rtl8111rtl8168-working-updated-guide/) shows that getting a non-open-source driver might be needed. Also, that article shows using the 8168 driver for the NIC and blacklisting the 8169 driver. You aren't using the 8169, so perhaps the kernel already does this? I dunno.

Not suggesting you do anything. If you do, *please be able to put it back the way it was*. Lots of people have previously had issues with non-working rt8168 cards and yours seems to be working. Be very careful.

---

