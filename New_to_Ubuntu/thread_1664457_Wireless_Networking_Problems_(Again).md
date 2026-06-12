---
title: "Wireless Networking Problems (Again)"
date: 2011-01-11
forum: New to Ubuntu
---

### Post by Tinker Tantrum on 2011-01-11
I've searched this forum to and fro for the solution to my problem with no luck. But I did learn about the info you all need to help me out quicker. Any help is appreciated, okay heres the skinny:

Just downloaded Ubuntu 10.4 and the wireless network "looks" fine. However I still cannot connect to Firefox or download the updates etc. I am using a Asus Q47 Notebook with Win7/Ubuntu dual-boot.  Ispci is as follows:
```
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 18)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 18)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 06)
00:1c.3 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 (rev 06)
00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 06)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a6)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 06)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 06)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 06)
02:00.0 Network controller: Intel Corporation WiFi Link 1000 Series
03:00.0 USB Controller: NEC Corporation Device 0194 (rev 03)
04:00.0 Ethernet controller: Atheros Communications AR8131 Gigabit Ethernet (rev c0)
3f:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 05)
3f:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 05)
3f:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 05)
3f:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 05)
3f:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 05)
3f:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 05)
```Heres if config if it helps:
```
eth0      Link encap:Ethernet  HWaddr 20:cf:30:35:ef:ee  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:36 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:120 errors:0 dropped:0 overruns:0 frame:0
          TX packets:120 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9536 (9.5 KB)  TX bytes:9536 (9.5 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1e:64:4e:6a:a6  
          inet addr:10.42.43.1  Bcast:10.42.43.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:64ff:fe4e:6aa6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:25 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:4376 (4.3 KB)
```Any help is greatly appreciated.

---

### Post by HDave on 2011-01-11
Hmmmm.  It looks like ifconfig is reporting that you have an internet address for your wlan0 network adapter, but it has 25 transmission errors.  Need more information to go from here though:

Can you confirm that 10.42.43.1 is a valid address for your LAN?

What happens if you ping that address from another computer?  

Is your LAN set up for DHCP?  Or is that address static?

What does the network manager report?

---

### Post by Tinker Tantrum on 2011-01-11
> **HDave said:**
>  
Can you confirm that 10.42.43.1 is a valid address for your LAN?
 
No it is not my valid address.
 
> **HDave said:**
> What happens if you ping that address from another computer?
 
I pinged it from the home PC and it could not find the IP. 
 
> **HDave said:**
> Is your LAN set up for DHCP? Or is that address static?
The "actual" IP address is static, I share it with our home PC. This only happens when I boot Ubuntu, but when I boot Win7, the wireless works fine.
 
> **HDave said:**
> What does the network manager report?
 
Not quite sure what you are asking for here. When I scroll over the wi-fi icon, it says that the wireless network is active at 70-75%. This is what boggles me.

---

### Post by Tinker Tantrum on 2011-01-12
yeah

---

### Post by Tinker Tantrum on 2011-01-12
bump

---

### Post by Tinker Tantrum on 2011-01-12
Still waiting for some brave soul to help me.

---

### Post by walt.smith1960 on 2011-01-12
> **Tinker Tantrum said:**
> 

The "actual" IP address is static, I share it with our home PC. This only happens when I boot Ubuntu, but when I boot Win7, the wireless works fine.

 


I'm not clear on the shared IP address. If you have the same address on 2 devices, that's a problem. It'd be like having 2 houses with the same postal address.

---

### Post by SuaSwe on 2011-01-12
I'm assuming that what you're saying is that you are dual-booting with Windows, and both Windows and Ubuntu use the same IP address (but obviously not at the same time) - is that right? If so, I don't believe the sharing of IP's is a problem. 

If you left-click on the wireless icon, which network does the PC claim it's connected to? If it's your regular one, right-click, go to Edit Connections > Wireless, click on your connection and click Edit, then IPv4 settings - what details are in there?

---

### Post by Tinker Tantrum on 2011-01-19
> **SuaSwe said:**
> I'm assuming that what you're saying is that you are dual-booting with Windows, and both Windows and Ubuntu use the same IP address (but obviously not at the same time) - is that right? If so, I don't believe the sharing of IP's is a problem. 

If you left-click on the wireless icon, which network does the PC claim it's connected to? If it's your regular one, right-click, go to Edit Connections > Wireless, click on your connection and click Edit, then IPv4 settings - what details are in there?
The IPv4 settings are set to "shared to other computers" its the only way I get a connection, and even then I can't get online.

---

### Post by deancasino on 2011-01-19
Try manually assigning your ISP's DNS server address/es, your router may be at fault.

---

### Post by Tinker Tantrum on 2011-05-27
I tried this, and still no luck. I can only get on-line with an ethernet connection.

---

