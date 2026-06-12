---
title: "ar9285 wireless problems  on maverick"
date: 2011-02-13
forum: New to Ubuntu
---

### Post by MYHEADHURTS on 2011-02-13
Hello,
  [I]I'm new at this, I have a new MSI cr620 64bit, with the Atheros AR9285 wireless card and 5 series /3400 chipset(I think) running on Ubuntu10:10.
      My problem is I can't work out how to enable the wireless card,[/I]I'v been reading for days and am non the wiser, I did read someware that ther is no driver for it and I need to use an old Kernal ( I am very waery of doing this,as I switched my old PC on one day and lost the entire Ubuntu system!)

---

### Post by MYHEADHURTS on 2011-02-13
john@john-Calpella-platform:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 40:61:86:ba:6b:57  
          inet addr:192.168.1.105  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::4261:86ff:feba:6b57/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:156798 errors:0 dropped:0 overruns:0 frame:0
          TX packets:87625 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:227009802 (227.0 MB)  TX bytes:7459097 (7.4 MB)
          Interrupt:44 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

john@john-Calpella-platform:~$ lspci
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1c.3 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 (rev 05)
00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
05:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
3f:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
3f:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
3f:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
3f:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
3f:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
3f:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
john@john-Calpella-platform:~$ 

I did this aswell, It doesn't  make an awful lot of sense to me.
 
Also I want to upgrade to Ubunu Studio , I presume  I do that before doing anything about the wireless.

---

### Post by Cuppa-Chino on 2011-02-13
hmm I have the same card in sony, one odd question: did you boot into windows and was the card disabled there? on mine when I disable it in windows I cannot restart it in ubuntu

took me forever to figure that out

---

### Post by MYHEADHURTS on 2011-02-14
Hia, thanks for getting back to me so soon,,

Sorry I did mean to say that I didn't buy Windows  It is a soul boot (:Dif thats the right expression)

---

### Post by MYHEADHURTS on 2011-03-06
Also,,I MEANT TO SAY i HAVE INSTALLED THE DRIVER ath9k

john@john-Calpella-platform:~$ sudo lshw -C network
  *-network DISABLED      
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: wlan0
       version: 01
       serial: 48:5d:60:61:f3:07
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=2.6.35-27-generic-pae firmware=N/A latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:19 memory:f4000000-f400ffff

 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)

---

### Post by AndrewD257 on 2011-03-24
> **MYHEADHURTS said:**
> Hello,
  [I]I'm new at this, I have a new MSI cr620 64bit, with the Atheros AR9285 wireless card and 5 series /3400 chipset(I think) running on Ubuntu10:10.
      My problem is I can't work out how to enable the wireless card,[/I]I'v been reading for days and am non the wiser, I did read someware that ther is no driver for it and I need to use an old Kernal ( I am very waery of doing this,as I switched my old PC on one day and lost the entire Ubuntu system!)

I may be too late, but I just upgraded to maverick and have an ar9285 which I had some problems with.  In the end, all I had to do was run the command:
```
rfkill unblock all
```and it worked great.  If that works for you, you also have to add it to the correct config file so that if runs that command every time at startup.  you do this by entering:
```
gedit /etc/rc.local
```
and adding:
```
rfkill unblock all
```
to the end of the file, before the exit 0

Hope this helps

---

### Post by MYHEADHURTS on 2012-07-21
Thanks for that Andrew,I just tried it but it didn't work,it may be because I'm now on 11.04 (naty), it says wireless disabled by hardware switch,but I switched it on and the light on the machine to tell me that the switch is on ,is on but no joy,,  thanks  jon

---

### Post by wildmanne39 on 2012-07-21
Hi, this is an old thread so it has been closed please start a new thread of your own with a descriptive title. 
Thanks

---

