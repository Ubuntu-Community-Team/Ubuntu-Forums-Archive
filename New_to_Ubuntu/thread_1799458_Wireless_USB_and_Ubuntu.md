---
title: "Wireless USB and Ubuntu"
date: 2011-07-07
forum: New to Ubuntu
---

### Post by domoappo on 2011-07-07
I'm trying to put Ubuntu on my moms computer, a fairly old desktop that has been using XP. I had Ubuntu running with Wubi. We have a wireless USB stick for internet. After Ubuntu was working, it wouldn't offer me any wireless networks to connect to, even thought the USB wireless stick was in. What do I need to do to get the Internet working? Any help would be appreciated : )

---

### Post by terrykiwi83 on 2011-07-07
Do you know what type of wireless adapter it is? go to terminal and type

```

lshw

```

and post your output here

---

### Post by domoappo on 2011-07-07
I should also mention that while starting up Ubuntu, I pick the "generic" (not the recovery mode option) and it tells me "error: file not found" but when I go back and try the "generic" again, it works.

Here's what putting in that command did.


	  To run a command as administrator (user "root"), use "sudo <command>".  
 See "man sudo_root" for details.  
 

 iris@ubuntu:~$ lshw  
 WARNING: you should run this program as super-user.  
 PCI (sysfs)   
 ubuntu                     
     description: Computer  
     width: 32 bits  
   *-core  
        description: Motherboard  
        physical id: 0  
      *-memory  
           description: System memory  
           physical id: 0  
           size: 494MiB  
      *-cpu  
           product: Intel(R) Celeron(R) CPU 2.40GHz  
           vendor: Intel Corp.  
           physical id: 1  
           bus info: cpu@0  
           version: 15.2.9  
           size: 2400MHz  
           width: 32 bits  
           capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe up pebs bts cid xtpr  
           configuration: id=0  
         *-cache  
              description: L1 cache  
              physical id: 0  
              size: 8KiB  
      *-pci  
           description: Host bridge  
           product: 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface  
           vendor: Intel Corporation  
           physical id: 100  
           bus info: pci@0000:00:00.0  
           version: 01  
           width: 32 bits  
           clock: 33MHz  
           configuration: driver=agpgart-intel  
           resources: irq:0 memory:f0000000-f7ffffff  
         *-display  
              description: VGA compatible controller  
              product: 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device  
              vendor: Intel Corporation  
              physical id: 2  
              bus info: pci@0000:00:02.0 
              version: 01  
              width: 32 bits  
              clock: 33MHz  
              capabilities: vga_controller bus_master cap_list rom  
              configuration: driver=i915 latency=0  
              resources: irq:16 memory:e8000000-efffffff memory:feb80000-febfffff  
         *-usb:0  
              description: USB Controller  
              product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1  
              vendor: Intel Corporation  
              physical id: 1d  
              bus info: pci@0000:00:1d.0 
              version: 01  
              width: 32 bits  
              clock: 33MHz  
              capabilities: uhci bus_master  
              configuration: driver=uhci_hcd latency=0  
              resources: irq:16 ioport:ff80(size=32)  
         *-usb:1  
              description: USB Controller  
              product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2  
              vendor: Intel Corporation  
              physical id: 1d.1  
              bus info: pci@0000:00:1d.1 
              version: 01  
              width: 32 bits  
              clock: 33MHz  
              capabilities: uhci bus_master  
              configuration: driver=uhci_hcd latency=0  
              resources: irq:19 ioport:ff60(size=32)  
         *-usb:2  
              description: USB Controller  
              product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3  
              vendor: Intel Corporation  
              physical id: 1d.2  
              bus info: pci@0000:00:1d.2 
              version: 01  
              width: 32 bits  
              clock: 33MHz  
              capabilities: uhci bus_master  
              configuration: driver=uhci_hcd latency=0  
              resources: irq:18 ioport:ff40(size=32)  
         *-usb:3  
              description: USB Controller  
              product: 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller  
              vendor: Intel Corporation  
              physical id: 1d.7  
              bus info: pci@0000:00:1d.7 
              version: 01  
              width: 32 bits  
              clock: 33MHz  
              capabilities: ehci bus_master cap_list  
              configuration: driver=ehci_hcd latency=0  
              resources: irq:23 memory:ffa80800-ffa80bff  
         *-pci  
              description: PCI bridge  
              product: 82801 PCI Bridge  
              vendor: Intel Corporation  
              physical id: 1e  
              bus info: pci@0000:00:1e.0 
              version: 81  
              width: 32 bits  
              clock: 33MHz  
              capabilities: pci normal_decode bus_master  
              resources: memory:fe900000-feafffff  
            *-network  
                 description: Ethernet interface  
                 product: BCM4401 100Base-T  
                 vendor: Broadcom Corporation  
                 physical id: 9  
                 bus info: pci@0000:01:09.0  
                 logical name: eth0  
                 version: 01  
                 serial: 00:0f:1f:82:e9:64  
                 size: 10Mbit/s  
                 capacity: 100Mbit/s  
                 width: 32 bits  
                 clock: 33MHz  
                 capabilities: bus_master cap_list rom ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation  
                 configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half latency=64 multicast=yes port=twisted pair speed=10Mbit/s 
                 resources: irq:17 memory:fe9fe000-fe9fffff memory:fea00000-fea03fff  
         *-isa  
              description: ISA bridge  
              product: 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge  
              vendor: Intel Corporation  
              physical id: 1f  
              bus info: pci@0000:00:1f.0 
              version: 01  
              width: 32 bits  
              clock: 33MHz  
              capabilities: isa bus_master  
              configuration: latency=0  
         *-ide  
              description: IDE interface 
              product: 82801DB (ICH4) IDE Controller  
              vendor: Intel Corporation  
              physical id: 1f.1  
              bus info: pci@0000:00:1f.1 
              version: 01  
              width: 32 bits  
              clock: 33MHz  
              capabilities: ide bus_master  
              configuration: driver=ata_piix latency=0  
              resources: irq:18 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:ffa0(size=16) memory:feb7fc00-feb7ffff  
         *-serial UNCLAIMED  
              description: SMBus  
              product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller  
              vendor: Intel Corporation  
              physical id: 1f.3  
              bus info: pci@0000:00:1f.3 
              version: 01  
              width: 32 bits  
              clock: 33MHz  
              configuration: latency=0  
              resources: ioport:eda0(size=32)  
         *-multimedia  
              description: Multimedia audio controller  
              product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller  
              vendor: Intel Corporation  
              physical id: 1f.5  
              bus info: pci@0000:00:1f.5 
              version: 01  
              width: 32 bits  
              clock: 33MHz  
              capabilities: bus_master cap_list  
              configuration: driver=Intel ICH latency=0  
              resources: irq:17 ioport:ee00(size=256) ioport:edc0(size=64) memory:feb7fa00-feb7fbff memory:feb7f900-feb7f9ff  
   *-network DISABLED  
        description: Wireless interface  
        physical id: 1  
        bus info: usb@1:6  
        logical name: wlan0  
        serial: 00:02:72:78:0b:75  
        capabilities: ethernet physical wireless  
        configuration: broadcast=yes driver=rtl819xU multicast=yes wireless=802.11b/g/n  
 WARNING: output may be incomplete or inaccurate, you should run this program as super-user.  
 iris@ubuntu:~$  
 iris@ubuntu:~$

---

### Post by terrykiwi83 on 2011-07-07
```

*-network **DISABLED** 
description: Wireless interface 
physical id: 1 
bus info: usb@1:6 
logical name: wlan0 
serial: 00:02:72:78:0b:75 
capabilities: ethernet physical wireless 
configuration: broadcast=yes driver=rtl819xU multicast=yes wireless=802.11b/g/n 

```

So it seems your device is disabled. Did you install drivers manually or did Ubuntu install them by default. Run iwconfig or ifconfig (can't remember which one) in the terminal and post the output here.

The other problem could possibly be your hard drive is failing, possible bad sectors. Go to System > Administration > Disk Utility

Find your disk and if available look at the SMART data for bad sectors.

---

### Post by domoappo on 2011-07-07
I'm not sure. Someone else set up the wireless USB, and from what I hear, apparently it didn't come with a CD or anything. The USB was in use with XP before Ubuntu.

  	 	 	 	 	 	  To run a command as administrator (user "root"), use "sudo <command>".  
 See "man sudo_root" for details.  
 

 iwiris@ubuntu:~$ iwconfig  
 lo        no wireless extensions.  
 

 eth0      no wireless extensions.  
 

 wlan0     802.11b/g/n  Mode:Managed  Access Point: Not-Associated    
           Bit Rate:1 Mb/s    
           Retry min limit:7   RTS thr:off   Fragment thr:off  
           Power Management:off  
           Link Quality=0/100  Signal level=0 dBm  Noise level=0 dBm  
           Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0  
           Tx excessive retries:0  Invalid misc:0   Missed beacon:0  
 

 iris@ubuntu:~$ ifconfig  
 eth0      Link encap:Ethernet  HWaddr 00:0f:1f:82:e9:64   
           UP BROADCAST MULTICAST  MTU:1500  Metric:1  
           RX packets:0 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:0 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:1000  
           RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)  
           Interrupt:17  
 

 lo        Link encap:Local Loopback   
           inet addr:127.0.0.1  Mask:255.0.0.0  
           inet6 addr: ::1/128 Scope:Host  
           UP LOOPBACK RUNNING  MTU:16436  Metric:1  
           RX packets:80 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:80 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:0  
           RX bytes:6080 (6.0 KB)  TX bytes:6080 (6.0 KB)  
 

 iris@ubuntu:~$  
 

I checked for bad sectors, and there was one that had a few bad sectors.

---

