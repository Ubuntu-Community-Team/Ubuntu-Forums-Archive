---
title: "I installed 11.04, and Internet wont work"
date: 2011-08-25
forum: New to Ubuntu
---

### Post by PirateKarma on 2011-08-25
HI! So just now I installed 11.04 on my brand new Hp g7-1150US laptop. And well it doesn't detect my wireless connection. And when I plug it in via Ethernet, it says it's connected, but the internet doesn't work. What I mean by that is that Firefox doesn't load any web pages. Plus when I plug it in via Ethernet my Desktop, and other laptops loose connection. It's really weird.

---

### Post by carverj on 2011-08-26
Are you using DHCP or static IP? 
Please post output of ifconfig command

---

### Post by Idefix82 on 2011-08-26
Hit Ctrl-Alt-T, that will take you to a terminal. Run the following commands and post the output of each of them here:

```

ifconfig
lshw -C network
lspci

```

---

### Post by PirateKarma on 2011-08-26
Thanks for the reply guys, so to be honest I have no idea if I'm using static or DHCP IP. Here are the outputs to the commands. 

ifconfig

```
ifconfig
eth0      Link encap:Ethernet  HWaddr 2c:27:d7:e4:ff:cf  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:40 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:112 errors:0 dropped:0 overruns:0 frame:0
          TX packets:112 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:8544 (8.5 KB)  TX bytes:8544 (8.5 KB)
```

sudo lshw -c network

```
*-network UNCLAIMED      
       description: Network controller 
       product: Ralink corp. 
       vendor: Ralink corp. 
       physical id: 0 
       bus info: pci@0000:02:00.0 
       version: 00 
       width: 32 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpress bus_master cap_list 
       configuration: latency=0 
       resources: memory:b5400000-b540ffff 
  *-network 
       description: Ethernet interface 
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller 
       vendor: Realtek Semiconductor Co., Ltd. 
       physical id: 0 
       bus info: pci@0000:03:00.0 
       logical name: eth0 
       version: 05 
       serial: 2c:27:d7:e4:ff:cf 
       size: 10Mbit/s 
       capacity: 100Mbit/s 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation 
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s 
       resources: irq:40 ioport:3000(size=256) memory:b1404000-b1404fff memory:b1400000-b1403fff 
```

lspci

```
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02) 
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02) 
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06) 
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05) 
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05) 
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05) 
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05) 
00:1c.2 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 (rev 05) 
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05) 
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5) 
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05) 
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05) 
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05) 
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05) 
02:00.0 Network controller: Ralink corp. Device 5390 
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05) 
04:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device 5209 (rev 01) 
7f:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02) 
7f:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02) 
7f:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02) 
7f:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02) 
7f:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02) 
7f:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
```

---

### Post by Idefix82 on 2011-08-26
Let's start by getting your wireless card to work. You are one of the unlucky people who actually have to work a little bit for that. Head over [to the Ralink website]("http://www.ralinktech.com/support.php?s=2") and download the RT539x driver, the top link.

After that follow the steps in [this thread]("http://ubuntuforums.org/showpost.php?p=10924640&postcount=2"), but with a small simplification. According to that thread, you do not need to download the patches any more, accordingly you don't need to execute any of the first commands that start with "patch". Also, after the command "sudo su", you will be asked to type in your password, but you will not see any feedback on the screen, not even asterisks. Just type it in confidently.

Remember exactly what you do, so that if something goes wrong you can report here describing your steps.

---

### Post by ofnuts on 2011-08-26
The result of ifconfig shows that you Ethernet interface is there, but has not been configured. Get into your network configuration application and check anything related to DHCP and enable it.

---

### Post by PirateKarma on 2011-08-26
OMG THANK YOU SO MUCH IDEFIX86!!! God Bless You!! It worked instantly, you rock! I can't thank you enough! <3

---

### Post by Idefix82 on 2011-08-26
Great, glad it worked and you are welcome. Your happiness is enough of a reward to me, I can do without God's blessings. And thank you also for politely making me 4 years younger than I am.

---

