---
title: "No wireless networks (Sometimes only)"
date: 2011-05-01
forum: New to Ubuntu
---

### Post by computerandu on 2011-05-01
Hi,
I am using Ubuntu 11.04. The problem is that **SOMETIMES **it doesn't detect any wireless networks. After few hours when I restart (instant restarting doesn't help) and login to Ubnutu it detects them perfectly. I am really pissed off because I cannot wait hours to use Linux. 
Remember that its not like that it never detects the networks. SOmetimes yes, sometimes NO....
Arrrggghhhh...........

---

### Post by computerandu on 2011-05-01
Here are some of the command outputs:


**lspci:**

00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 12)

00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 12)

00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)

00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)

00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)

00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06)

00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 06)

00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 06)

00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a6)

00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 06)

00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 6 port SATA AHCI Controller (rev 06)

00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06)

00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 06)

03:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)

04:00.0 Ethernet controller: Atheros Communications AR8152 v1.1 Fast Ethernet (rev c1)

ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)

ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)

ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)

ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)

ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)

ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)




**ifconfig:**

eth1      
Link encap:Ethernet  HWaddr 70:f1:a1:c2:f2:e9  
          inet6 addr: fe80::72f1:a1ff:fec2:f2e9/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 

frame:448
          TX packets:0 errors:17 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 


[B]
sudo dhclient eth1:[/B]   no output


[B]
netstat -r:[/B]
 
Kernel IP routing table

Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface


[B]
sudo lshw -C network[/B]

[sudo] password for takshak: 
  
*-network               
       
description: Wireless interface
       
product: BCM4313 802.11b/g/n Wireless LAN Controller
       
vendor: Broadcom Corporation
      
physical id: 0
       
bus info: pci@0000:03:00.0
      
logical name: eth1
       
version: 01
       
serial: 70:f1:a1:c2:f2:e9
       
width: 64 bits
       
clock: 33MHz
       
capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       
configuration: broadcast=yes driver=wl0 driverversion=5.100.82.38 latency=0 multicast=yes wireless=IEEE 802.11
       
resources: irq:17 memory:f0500000-f0503fff
  *-network
       
description: Ethernet interface
       product: AR8152 v1.1 Fast Ethernet
       
vendor: Atheros Communications
       physical id: 0
       
bus info: pci@0000:04:00.0
       
logical name: eth0
       
version: c1
       
serial: b8:ac:6f:67:11:46
       
capacity: 100Mbit/s
       
width: 64 bits
       
clock: 33MHz
       
capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       
configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       
resources: irq:43 memory:f0400000-f043ffff ioport:2000(size=128)

---

### Post by josephmills on 2011-05-01
> **computerandu said:**
> Hi,
I am using Ubuntu 11.04. The problem is that **SOMETIMES **it doesn't detect any wireless networks. After few hours when I restart (instant restarting doesn't help) and login to Ubnutu it detects them perfectly. I am really pissed off because I cannot wait hours to use Linux. 
Remember that its not like that it never detects the networks. SOmetimes yes, sometimes NO....
Arrrggghhhh...........

sometimes your switch gets turned of or there is a software block you can check this with ```
rfkill list
``` sometimes network manager acts funny you can use ```
nm-tool
``` to look at some stuff. sometimes the firmware acts funny also check it out with ```
dmesg
``` well hope that this helps. Do you have witrless right now?

---

### Post by colin.p on 2011-05-01
I feel your pain. The problem wireless card is an Atheros, on my daughter's Dell Mini 1012. The card will maybe connect 1 time out of 50 attempts. I have changed drivers, removed/re-installed the driver, even plugged in the cat5, and sometimes that will get the bloody card to work.

The only difference is, from yours, that MY PROBLEM IS IN XP.
 
The card works perfectly in lucid. Never, ever, refuses to connect, first time, every time. So I know the card works ok, the router settings are ok,
it's something in XP's settings, that I am doing wrong. Has to be, I am quite sure that I am not the only person to buy a 1012, and I don't see a million posts about wireless problems.
 
So, I say screw it, the frustration is not worth it. She just uses the cat5 and she uses the wired ethernet connection. If I need it to connect wirelessly, I boot into lucid.

The bottom line is that it isn't ubuntu to blame for your wireless problems, more that likely, a configuration issue that you will need to track down. Or be like me and say, screw it and use cat5.

---

### Post by computerandu on 2011-05-02
> **colin.p said:**
> I feel your pain. The problem wireless card is an Atheros, on my daughter's Dell Mini 1012. The card will maybe connect 1 time out of 50 attempts. I have changed drivers, removed/re-installed the driver, even plugged in the cat5, and sometimes that will get the bloody card to work.

The only difference is, from yours, that MY PROBLEM IS IN XP.
 
The card works perfectly in lucid. Never, ever, refuses to connect, first time, every time. So I know the card works ok, the router settings are ok,
it's something in XP's settings, that I am doing wrong. Has to be, I am quite sure that I am not the only person to buy a 1012, and I don't see a million posts about wireless problems.
 
So, I say screw it, the frustration is not worth it. She just uses the cat5 and she uses the wired ethernet connection. If I need it to connect wirelessly, I boot into lucid.

The bottom line is that it isn't ubuntu to blame for your wireless problems, more that likely, a configuration issue that you will need to track down. Or be like me and say, screw it and use cat5.



I have only wireless networks available at my student residence. I cannot go for wired connections..:(

---

### Post by computerandu on 2011-05-02
> **josephmills said:**
> sometimes your switch gets turned of or there is a software block you can check this with ```
rfkill list
``` sometimes network manager acts funny you can use ```
nm-tool
``` to look at some stuff. sometimes the firmware acts funny also check it out with ```
dmesg
``` well hope that this helps. Do you have witrless right now?




**rfkill**
list

0: dell-wifi: Wireless LAN
    
Soft blocked: no
    
Hard blocked: no

1: dell-bluetooth: Bluetooth
    
Soft blocked: no
    
Hard blocked: no

2: brcmwl-0: Wireless LAN
    
Soft blocked: no
    
Hard blocked: no



[B]
NetworkManager Too[/B]l


State: disconnected

- 
Device: eth1 -----------------------------------------------------------------
  Type:              802.11 
WiFi
  Driver:            wl
  
State:             disconnected
  
Default:           no
  
HW Address:        70:F1:A1:C2:F2:E9

  
Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 


- 

Device: eth0 -----------------------------------------------------------------
  
Type:              Wired
  
Driver:            atl1c
  
State:             unavailable
  
Default:           no
  
HW Address:        B8:AC:6F:67:11:46

  
Capabilities:
    Carrier Detect:  yes

  
Wired Properties
    Carrier:         off



It says that Network manager is disconnected ....what does it mean> How to connect it?

---

### Post by computerandu on 2011-05-02
Any help...any one?

---

### Post by computerandu on 2011-05-02
I tried a fresh install of Ubuntu 11.04. To my frustration, while installing it detected the wireless network and was connected to one of them. And now when I boot into Ubuntu after installing...it detects no wireless....WHY????????

:(

---

### Post by idoitprone on 2011-05-02
broadcom has pretty bad linux support

[http://ubuntuforums.org/showthread.php?p=10057878](http://ubuntuforums.org/showthread.php?p=10057878)
[http://ubuntuforums.org/showthread.php?t=1604868](http://ubuntuforums.org/showthread.php?t=1604868)

two threads that has the same problems

---

### Post by computerandu on 2011-05-03
Those two forum suggest me to update and download through network. Problem is, I have only wireless network available at the residence and since I cannot connect to wireless those solutions are irrelevant to me.

---

### Post by idoitprone on 2011-05-03
So you cant use another computer that has internet and search through [https://launchpad.net/ubuntu](https://launchpad.net/ubuntu) or anyother website. Download the .deb package or other package. Save it to an usb and send it to your computer?

Edit: Seems like your not the only one recently [http://ubuntuforums.org/showthread.php?t=1748246](http://ubuntuforums.org/showthread.php?t=1748246)
The guy suggested using maverick driver, since they broke natty's

---

### Post by Peter09 on 2011-05-03
Its not really a fix but you may find that taking the battery out of your laptop for a couple of seconds and putting it back will reset the card and allow you to connect - rather than waiting for hours.

(Note - ensure you are not on mains either)

---

### Post by computerandu on 2011-05-03
I reinstalled it using DVD rather than USB (with all the updates). Its not hanging anymore...and wireless is also working (at least for this session)....

Since I am no longer having the problem, i'll close the thread.

---

