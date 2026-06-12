---
title: "No Internet connection"
date: 2011-05-15
forum: New to Ubuntu
---

### Post by jsl90 on 2011-05-15
Hi I'm new to Linux i've tried Ubuntu 10.04 on my asus 1001ha/xp netbook,updated the kernel now i have no wireless or wired connection.  I've done the same on my desktop which is an acer X3400 .  I've looked at all the fixes on the differnt posts tried them and they havent helped so I downloaded 11.04 made a live usb stick booted the destop and again no wired connection.  I've a BT Home Hub on WPA and WPA2.  They both used to work fine until i updated.  Can someone help me out please.:(

---

### Post by corrytonapple on 2011-05-15
Do you even see the avability of any connections in the connections manager window?  If not, make sure drivers are installed.  To do so, go to **System > Administration > Additional Drivers**.  If there are any, install them.
Good Luck and Report Back.

---

### Post by Johnley on 2011-05-15
if he has no wired connection, how can he download and install drivers? 

also, try rolling back to the previous kernel by selecting it in grub at boot time. if that works, probably ought to report it as a bug, and remove the new kernel.

---

### Post by corrytonapple on 2011-05-15
Those were instructions for after he has found a connection, if any.  I am unsure if he happens to be using a network connection manager besides the default one.

---

### Post by garvinrick4 on 2011-05-15
> **Johnley said:**
> if he has no wired connection, how can he download and install drivers? 

also, try rolling back to the previous kernel by selecting it in grub at boot time. if that works, probably ought to report it as a bug, and remove the new kernel.
Run this so we can see card and drivers post back here. Just need bit about network cards so can find drivers. If they are in Synaptics will be OK for you.
```
lspci -k
``````
sudo lshw -C network
```

---

### Post by jsl90 on 2011-05-16
thanks for the help sorry i havent replied havent beem doing much on the comp i will post the info you need soon.

---

### Post by jsl90 on 2011-05-16
HI 
here is the info 
  lspci -k
  00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
              Kernel driver in use: agpgart-intel
              Kernel modules: intel-agp
  00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
              Kernel driver in use: i915
              Kernel modules: i915
  00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
  00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
              Kernel driver in use: HDA Intel
              Kernel modules: snd-hda-intel
  00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
              Kernel driver in use: pcieport
              Kernel modules: shpchp
  00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
              Kernel driver in use: pcieport
              Kernel modules: shpchp
  00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 02)
              Kernel driver in use: pcieport
              Kernel modules: shpchp
  00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 02)
              Kernel driver in use: uhci_hcd
  00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
              Kernel driver in use: uhci_hcd
  00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
              Kernel driver in use: uhci_hcd
  00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
              Kernel driver in use: uhci_hcd
  00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
              Kernel driver in use: ehci_hcd
  00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
  00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
              Kernel modules: iTCO_wdt, intel-rng
  00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02)
              Kernel driver in use: ahci
              Kernel modules: ahci
  01:00.0 Ethernet controller: Atheros Communications Atheros AR8132 / L1c Gigabit Ethernet Adapter (rev c0)
              Kernel driver in use: atl1c
              Kernel modules: atl1c
  02:00.0 Network controller: RaLink RT3090 Wireless 802.11n 1T/1R PCIe
              Kernel driver in use: rt2860
              Kernel modules: rt3090sta
   
    $ sudo lshw -C network
   
    *-network               
         description: Wireless interface
         product: RT3090 Wireless 802.11n 1T/1R PCIe
         vendor: RaLink
         physical id: 0
         bus info: pci@0000:02:00.0
         logical name: ra0
         version: 00
         serial: 1c:4b:d6:2b:a8:77
         width: 32 bits
         clock: 33MHz
         capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
         configuration: broadcast=yes driver=RALINK WLAN driverversion=2.3.1.3 latency=0 multicast=yes wireless=Ralink STA
         resources: irq:17 memory:fbff0000-fbffffff
    *-network
         description: Ethernet interface
         product: Atheros AR8132 / L1c Gigabit Ethernet Adapter
         vendor: Atheros Communications
         physical id: 0
         bus info: pci@0000:01:00.0
         logical name: eth0
         version: c0
         serial: e0:cb:4e:89:83:11
         size: 100MB/s
         capacity: 100MB/s
         width: 64 bits
         clock: 33MHz
         capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
         configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.0.1-NAPI duplex=full firmware=N/A latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
         resources: irq:28 memory:f7fc0000-f7ffffff ioport:ec00(size=128)


that was for the netbook


this is for the desktop


  Desktop - $ lspci -k
  00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 03)
              Kernel driver in use: agpgart-intel
              Kernel modules: intel-agp
  00:02.0 VGA compatible controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)
              Kernel driver in use: i915
              Kernel modules: i915
  00:02.1 Display controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)
  00:19.0 Ethernet controller: Intel Corporation 82567V-2 Gigabit Network Connection
              Kernel driver in use: e1000e
              Kernel modules: e1000e
  00:1a.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4
              Kernel driver in use: uhci_hcd
  00:1a.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5
              Kernel driver in use: uhci_hcd
  00:1a.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #6
              Kernel driver in use: uhci_hcd
  00:1a.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2
              Kernel driver in use: ehci_hcd
  00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
              Kernel driver in use: HDA Intel
              Kernel modules: snd-hda-intel
  00:1c.0 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 1
              Kernel driver in use: pcieport
              Kernel modules: shpchp
  00:1d.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1
              Kernel driver in use: uhci_hcd
  00:1d.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2
              Kernel driver in use: uhci_hcd
  00:1d.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3
              Kernel driver in use: uhci_hcd
  00:1d.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1
              Kernel driver in use: ehci_hcd
  00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 90)
  00:1f.0 ISA bridge: Intel Corporation 82801JIB (ICH10) LPC Interface Controller
              Kernel modules: iTCO_wdt
  00:1f.2 SATA controller: Intel Corporation 82801JI (ICH10 Family) SATA AHCI Controller
              Kernel driver in use: ahci
              Kernel modules: ahci
  00:1f.3 SMBus: Intel Corporation 82801JI (ICH10 Family) SMBus Controller
              Kernel modules: i2c-i801
  01:00.0 FireWire (IEEE 1394): VIA Technologies, Inc. Device 3403
              Kernel driver in use: ohci1394
              Kernel modules: firewire-ohci, ohci1394


   *-network               
         description: Ethernet interface
         product: 82567V-2 Gigabit Network Connection
         vendor: Intel Corporation
         physical id: 19
         bus info: pci@0000:00:19.0
         logical name: eth0
         version: 00
         serial: 00:1f:16:fd:ff:63
         size: 100MB/s
         capacity: 1GB/s
         width: 32 bits
         clock: 33MHz
         capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
         configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.0.2-k2 duplex=full firmware=1.8-5 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
         resources: irq:25 memory:feac0000-feadffff memory:feafa000-feafafff ioport:d880(size=32)


thanks again for the help.

---

### Post by jsl90 on 2011-05-16
I tried the additional drivers but there were none.

---

### Post by astex on 2011-05-16
Could you run the command 'ifconfig'?

---

### Post by jsl90 on 2011-05-16
Desktop

ifconfig
  eth0      Link encap:Ethernet  HWaddr 00:1f:16:fd:ff:63  
            inet6 addr: fe80::21f:16ff:fefd:ff63/64 Scope:Link
            UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
            RX packets:12 errors:0 dropped:0 overruns:0 frame:0
            TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
            collisions:0 txqueuelen:100
            RX bytes:2419 (2.4 KB)  TX bytes:1152 (1.1 KB)
            Memory:feac0000-feae0000
   
  lo        Link encap:Local Loopback  
            inet addr:127.0.0.1  Mask:255.0.0.0
            inet6 addr: ::1/128 Scope:Host
            UP LOOPBACK RUNNING  MTU:16436  Metric:1
            RX packets:88 errors:0 dropped:0 overruns:0 frame:0
            TX packets:88 errors:0 dropped:0 overruns:0 carrier:0
            collisions:0 txqueuelen:0
            RX bytes:9521 (9.5 KB)  TX bytes:9521 (9.5 KB)
   
Netbook

ifconfig
  eth0      Link encap:Ethernet  HWaddr e0:cb:4e:89:83:11  
            UP BROADCAST MULTICAST  MTU:1500  Metric:1
            RX packets:0 errors:0 dropped:0 overruns:0 frame:0
            TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
            collisions:0 txqueuelen:1000
            RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
            Interrupt:28
   
  lo        Link encap:Local Loopback  
            inet addr:127.0.0.1  Mask:255.0.0.0
            inet6 addr: ::1/128 Scope:Host
            UP LOOPBACK RUNNING  MTU:16436  Metric:1
            RX packets:8 errors:0 dropped:0 overruns:0 frame:0
            TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
            collisions:0 txqueuelen:0
            RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)
   
  ra0       Link encap:Ethernet  HWaddr 1c:4b:d6:2b:a8:77  
            inet6 addr: fe80::1e4b:d6ff:fe2b:a877/64 Scope:Link
            UP BROADCAST MULTICAST  MTU:1500  Metric:1
            RX packets:1354 errors:0 dropped:0 overruns:0 frame:0
            TX packets:87 errors:0 dropped:0 overruns:0 carrier:0
            collisions:0 txqueuelen:1000
            RX bytes:288623 (288.6 KB)  TX bytes:4389 (4.3 KB)
            Interrupt:17


thanks.

---

### Post by corrytonapple on 2011-05-16
If possible, click the "#" button when you are replying with the "New Reply" button.  Then, put your code between the tags it gives you.  Like this:
```
This is code
```

---

### Post by jsl90 on 2011-05-17
[CODE  eth0      Link encap:Ethernet  HWaddr 00:1f:16:fd:ff:63  
            inet6 addr: fe80::21f:16ff:fefd:ff63/64 Scope:Link
            UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
            RX packets:12 errors:0 dropped:0 overruns:0 frame:0
            TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
            collisions:0 txqueuelen:100
            RX bytes:2419 (2.4 KB)  TX bytes:1152 (1.1 KB)
            Memory:feac0000-feae0000
   
  lo        Link encap:Local Loopback  
            inet addr:127.0.0.1  Mask:255.0.0.0
            inet6 addr: ::1/128 Scope:Host
            UP LOOPBACK RUNNING  MTU:16436  Metric:1
            RX packets:88 errors:0 dropped:0 overruns:0 frame:0
            TX packets:88 errors:0 dropped:0 overruns:0 carrier:0
            collisions:0 txqueuelen:0
            RX bytes:9521 (9.5 KB)  TX bytes:9521 (9.5 KB)
   
Netbook

ifconfig
  eth0      Link encap:Ethernet  HWaddr e0:cb:4e:89:83:11  
            UP BROADCAST MULTICAST  MTU:1500  Metric:1
            RX packets:0 errors:0 dropped:0 overruns:0 frame:0
            TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
            collisions:0 txqueuelen:1000
            RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
            Interrupt:28
   
  lo        Link encap:Local Loopback  
            inet addr:127.0.0.1  Mask:255.0.0.0
            inet6 addr: ::1/128 Scope:Host
            UP LOOPBACK RUNNING  MTU:16436  Metric:1
            RX packets:8 errors:0 dropped:0 overruns:0 frame:0
            TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
            collisions:0 txqueuelen:0
            RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)
   
  ra0       Link encap:Ethernet  HWaddr 1c:4b:d6:2b:a8:77  
            inet6 addr: fe80::1e4b:d6ff:fe2b:a877/64 Scope:Link
            UP BROADCAST MULTICAST  MTU:1500  Metric:1
            RX packets:1354 errors:0 dropped:0 overruns:0 frame:0
            TX packets:87 errors:0 dropped:0 overruns:0 carrier:0
            collisions:0 txqueuelen:1000
            RX bytes:288623 (288.6 KB)  TX bytes:4389 (4.3 KB)
            Interrupt:17

][/CODE]

is that it.

---

### Post by jsl90 on 2011-05-17
ooops that didnt work:confused:

---

### Post by ibizatunes on 2011-05-17
Download 11.04 instead, it will have a newer kernel and more likely to have the drivers for your hardware

[www.ubuntu.com](www.ubuntu.com)

---

### Post by jsl90 on 2011-05-17
Done that , made a live usb stick and you guessed it no internet connection.  Might have to stay with Xp and 7, tis a shame cause i  was getting to like Linux a lot.

---

### Post by Swagman on 2011-05-17
Your ISP isn't BT and you're using their Home Hub perchance ?

---

### Post by jtarin on 2011-05-17
> **jsl90 said:**
> Hi I'm new to Linux i've tried Ubuntu 10.04 on my asus 1001ha/xp netbook,updated the kernel now i have no wireless or wired connection.  I've done the same on my desktop which is an acer X3400 .  I've looked at all the fixes on the differnt posts tried them and they havent helped so I downloaded 11.04 made a live usb stick booted the destop and again no wired connection.  I've a BT Home Hub on WPA and WPA2.  They both used to work fine until i updated.  Can someone help me out please.:(You were using 10.04.....updated its kernel......no internet.......so upgraded the version 11.04.......no internet.OK....both computers have one common denominator outside the box ......what is it?

---

### Post by jsl90 on 2011-05-17
My ISP is BT, yeah the funny thing is that both computers used to work with ubuntu but after the update they don't so all I'm thinking is that i might just re-install an older version of 10.04 and see what happens.  What do u think?

---

### Post by Swagman on 2011-05-17
We have found the cause.

[http://community.bt.com/t5/BB-Speed-Connection-Issues/BT-HomeHub-firmware-upgrade-broken-network-connectivity-Ubuntu/td-p/176473](http://community.bt.com/t5/BB-Speed-Connection-Issues/BT-HomeHub-firmware-upgrade-broken-network-connectivity-Ubuntu/td-p/176473)

> 

    BT have acknowledged this:

    PaddyB wrote:

    Hi All,

     

    The latest firmware version (4.7.5.1.83.3.18) included a fix to ensure disconnected devices are released from the Hubs DHCP table.

     

    As our requirements for the hub don&#8217;t specifically support multiple IP hosts with the same MAC address, this specific scenario with dual boot set-ups was not tested for this upgrade.  After your reports on the forum we are now working on a solution, thanks for flagging this to us. 

     

    In the meantime we have identified a work around that you can use. The network interface on the Ubuntu operating system needs to be configured to use a fixed IP address. This must be set in the operating system&#8217;s network settings and not the Hub&#8217;s GUI.
 

    Cheers

    Paddy,



---

### Post by jsl90 on 2011-05-17
That's great now i know the cause how do I do the work around, forgive my ignorance in these things.

---

### Post by jsl90 on 2011-05-17
[QUOTE][BT have acknowledged this:

    PaddyB wrote:

    Hi All,

     

    The latest firmware version (4.7.5.1.83.3.1:cool: included a fix to ensure disconnected devices are released from the Hubs DHCP table.

     

    As our requirements for the hub don’t specifically support multiple  IP hosts with the same MAC address, this specific scenario with dual  boot set-ups was not tested for this upgrade.  After your reports on the  forum we are now working on a solution, thanks for flagging this to us.  

     

    In the meantime we have identified a work around that you can use.  The network interface on the Ubuntu operating system needs to be  configured to use a fixed IP address. This must be set in the operating  system’s network settings and not the Hub’s GUI.
 

    Cheers

    Paddy,
			 		 	 	  		                   		  		  		  		  		 		 			 				]

How do i configure the network interface then?

---

### Post by jsl90 on 2011-05-17
Did a factory reset on the BT HomeHub and now i'm up and running not to sure if it will stay that way, when i boot back into windows.:)

---

### Post by Swagman on 2011-05-17
I suspect that'll b0rk again after you've used Windows and then gone back into Ubuntu

Fix is on page 9 of that link I posted.

[http://community.bt.com/t5/BB-Speed-Connection-Issues/BT-HomeHub-firmware-upgrade-broken-network-connectivity-Ubuntu/td-p/176473/page/9](http://community.bt.com/t5/BB-Speed-Connection-Issues/BT-HomeHub-firmware-upgrade-broken-network-connectivity-Ubuntu/td-p/176473/page/9)

---

### Post by jsl90 on 2011-05-17
Thank you, thank you!!! That link helped me and now i'm connected.  Did the work around and then rebooted  into windows 7 then back into 10.04 and its still connecting excellent.  Now all i have to do is do the same for the netbook.

---

### Post by corrytonapple on 2011-05-17
Good to see it is working.  Sorry I could not help more than I did though....
Since your thread is solved, please click Thread Tools in the top right hand corner of this page, and then Mark Thread as Solved.
Happy Ubuntu-ing!

---

### Post by jsl90 on 2011-05-18
I spoke too soon.  Desktop is up and running connects al the time, however the netbook is nt i've done what was suggested but still no internet connection wired or wireless is seems that there is onlt one dhcp client identifier when it comes to editing but i have 2 Hwaddrs one for etho and one for the ra0 is the info from ifconfig -a


                     p { margin-bottom: 0.21cm; }  eth0      Link encap:Ethernet  **HWaddr e0:cb:4e:89:83:11**   
           inet6 addr: fe80::e2cb:4eff:fe89:8311/64 Scope:Link
           UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
           RX packets:8205 errors:0 dropped:0 overruns:0 frame:0
           TX packets:9 errors:0 dropped:0 overruns:0 carrier:3
           collisions:0 txqueuelen:1000  
           RX bytes:2041 (2.0 KB)  TX bytes:1494 (1.4 KB)
           Interrupt:28  
 

 lo        Link encap:Local Loopback   
           inet addr:127.0.0.1  Mask:255.0.0.0
           inet6 addr: ::1/128 Scope:Host
           UP LOOPBACK RUNNING  MTU:16436  Metric:1
           RX packets:8 errors:0 dropped:0 overruns:0 frame:0
           TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
           collisions:0 txqueuelen:0  
           RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)
 

 ra0       Link encap:Ethernet  **HWaddr 1c:4b:d6:2b:a8:77   **
           inet6 addr: fe80::1e4b:d6ff:fe2b:a877/64 Scope:Link
           UP BROADCAST MULTICAST  MTU:1500  Metric:1
           RX packets:18622 errors:0 dropped:0 overruns:0 frame:0
           TX packets:455 errors:0 dropped:0 overruns:0 carrier:0
           collisions:0 txqueuelen:1000  
           RX bytes:3978970 (3.9 MB)  TX bytes:2701 (2.7 KB)
           Interrupt:17 



do i enter them both?

---

### Post by jtarin on 2011-05-18
I would suggest you dump the BT router and get a Linux compatible one.

---

### Post by jsl90 on 2011-05-18
Well I've found a solution i've kept my old 1.5 hub so I've connected that and its all working, until BT sorts themselves out i will have to accept that.  Thanks for all the help!

---

