---
title: "Problem strting wireless Atheros AR242x/Ubuntu 8.10/HP dv7-1132nr"
date: 2008-11-20
forum: Networking &amp; Wireless
---

### Post by Gerald Farmer on 2008-11-20
Thanks for looking at this thread.  I have just installed Ubuntu 8.10 on this new HP laptop.  I am running a dual boot system with MS Vista and the wireless works fine with Vista so I don't think it is a hardware probem.  When I check the hardware drivers the report is that the atheros driver is installed and activated.  I have done some other checks and the results follow:

lspci

 AR242x 802.11abg Wireless PCI Express Adapter (rev 01) 

gerald@HPlaptop:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:1e:ec:b9:07:bd  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:6231540529 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
          Interrupt:251 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:736 (736.0 B)  TX bytes:736 (736.0 B) 

gerald@HPlaptop:~$ iwconfig 
lo        no wireless extensions. 

eth0      no wireless extensions. 

pan0      no wireless extensions. 

gerald@HPlaptop:~$ sudo lshw -C network 
[sudo] password for gerald: 
  *-network UNCLAIMED     
       description: Ethernet controller 
       product: AR242x 802.11abg Wireless PCI Express Adapter 
       vendor: Atheros Communications Inc. 
       physical id: 0 
       bus info: pci@0000:09:00.0 
       version: 01 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpress msix cap_list 
       configuration: latency=0 
  *-network 
       description: Ethernet interface 
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller 
       vendor: Realtek Semiconductor Co., Ltd. 
       physical id: 0 
       bus info: pci@0000:0a:00.0 
       logical name: eth0 
       version: 02 
       serial: 00:1e:ec:b9:07:bd 
       size: 1GB/s 
       capacity: 1GB/s 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical fibre 1000bt-fd autonegotiation 
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full latency=0 link=no module=r8169 multicast=yes port=fibre speed=1GB/s 
  *-network DISABLED 
       description: Ethernet interface 
       physical id: 1 
       logical name: pan0 
       serial: ca:f3:2a:f3:7f:70 
       capabilities: ethernet physical 
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes 

gerald@HPlaptop:~$ lsb_release -d 
Description:	Ubuntu 8.10 

lsmod

wlan                  234784  1 ath_pci 
ath_hal               225904  1 ath_pci 

gerald@HPlaptop:~$ uname -mr 
2.6.27-7-generic x86_64 

gerald@HPlaptop:~$ sudo /etc/init.d/networking restart 
[sudo] password for gerald: 
 * Reconfiguring network interfaces...            

After reconfiguring nothing has changed.  If you can offer suggestions toward a solution to my problem I will be very grateful.  Thanks again for looking at the thread.

---

### Post by K3N8 on 2008-12-01
Hi Gerald,

Just install the backported drivers for generic kernels: ```
apt-get install linux-backports-modules-intrepid-generic
```

Once you've done that go to the hardware section and activate the new adition and deactite the old one. That fixed it for me.

Gr. Alexander

HP Pavilion DV7 1120

---

### Post by mnhobbie on 2011-02-27
Also using HP Pavilion dv7-1132nr
 
Fast Forward to 2011 with Ubuntu 10.10 (64-bit). Same problem. "Enable Wireless" is greyed out.
 
I want to ditch Vista, but where I live, I need to get the wireless to work. 
 
Where do I start?
 
I tried changing "apt-get install linux-backports-modules-[COLOR=red]intrepid[/COLOR]-generic" to "...linux-backports-modules-[COLOR=red]maverick[/COLOR]-generic" but no luck.

---

