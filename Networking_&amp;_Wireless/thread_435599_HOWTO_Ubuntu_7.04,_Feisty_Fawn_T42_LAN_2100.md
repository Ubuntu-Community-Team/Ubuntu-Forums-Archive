---
title: "HOWTO: Ubuntu 7.04, Feisty Fawn T42 LAN 2100"
date: 2007-05-07
forum: Networking &amp; Wireless
---

### Post by LEVONO_T42 on 2007-05-07
INTEL PRO/Wireless LAN 2100 3B Mini PCI Adapter Setup

They aren't any recent support/HOWTO for the latest ipw2100-fw-1.3.tgz driver or infamous INTEL PRO/Wireless LAN 2100 3B Mini PCI Adapter. That is why I am pleading to the internet community for tech support/HELP! Please ole wise ones, THE Geek gurus out there! Together we can create a "sticky" for the reliable, fading Levono T series laptop. I am not ready to let it gather dust with XP installed. I like to use it to learn Linux. 

I started following the instructions at:
[http://www.columbia.edu/~em36/ubuntubreezythinkpadt42.html](http://www.columbia.edu/~em36/ubuntubreezythinkpadt42.html)
without success and thought that if I slowly upgraded to next distro (in an ascending order), there might be a chance one of the later kernels would detect the wireless adapter. I ended at the latest, Ubuntu 7.04 with no such luck!!. My painful experience only tested my patience. It failed to bear any result but only frustration. I am on the verge on giving up hope on LINUX-UBUNTU. I was told it was the dummy version of Linux.

andy@andy-laptop:~$ iwlist eth0 scanning
eth0      Interface doesn't support scanning.

I have also tried at:
[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)
[http://www.stoltenow.com/archives/2006/12/ubuntu_configur.html](http://www.stoltenow.com/archives/2006/12/ubuntu_configur.html)
to set up my wireless network card. It is futile! I am a basic unix/linux user. 

SO PLEASE someone out there help me before I go back back to using XP.


[B]           *-network:1 UNCLAIMED
[/B]                description: Network controller
               [COLOR="Red"] product: PRO/Wireless LAN 2100 3B Mini PCI Adapter[/COLOR]
                vendor: Intel Corporation
                physical id: 2
                bus info: pci@02:02.0
                version: 04
                width: 32 bits
                clock: 33MHz
                capabilities: cap_list
                configuration: latency=64 maxlatency=34 mingnt=2
                resources: iomemory:c0214000-c0214fff irq:11

The command "sudo lshw" output  with only relevant information:
      
andy-laptop               
    description: Notebook
    product: 2373T42
    vendor: IBM
    version: ThinkPad T42
    serial: L3Z4R9X
    width: 32 bits
    capabilities: smbios-2.33 dmi-2.33
    configuration: administrator_password=disabled boot=normal chassis=notebook frontpanel_password=unknown keyboard_password=disabled power-on_password=disabled uuid=5B39D201-47C0-11CB-9FB7-BE92F7834A3F
 
     *-firmware
          description: BIOS
          vendor: IBM
          physical id: 0
          version: 1RETDKWW (3.16 ) (04/19/2005)
          size: 144KB
          capacity: 960KB

     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) M processor 1.70GHz
          vendor: Intel Corp.
          physical id: 6
          bus info: cpu@0
          version: 6.13.6
          slot: None
          size: 1700MHz
          capacity: 1700MHz
          width: 32 bits
          clock: 400MHz

     *-memory
          description: System Memory
          physical id: 2c
          slot: System board or motherboard
          size: 512MB
          capacity: 1GB
 
       *-pci:0
             description: PCI bridge
             product: 82855PM Processor to AGP Controller
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@00:01.0
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master

           *-display
                description: VGA compatible controller
                product: Radeon Mobility M7 LW [Radeon Mobility 7500]
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@01:00.0
                version: 00
                size: 128MB
                width: 32 bits
                clock: 66MHz

 Ethernet interface
                product: 82540EP Gigabit Ethernet Controller (Mobile)
                vendor: Intel Corporation
                physical id: 1
                bus info: pci@02:01.0
                logical name: eth0
                version: 03
                serial: 00:11:25:18:21:29
                size: 100MB/s
                capacity: 1GB/s
                width: 32 bits
                clock: 66MHz

---

### Post by LEVONO_T42 on 2007-05-07
andy@andy-laptop:~$ iwlist ath0 scanning
ath0      Interface doesn't support scanning.

andy@andy-laptop:~$ sudo iwconfig
Password:
lo        no wireless extensions.
eth0      no wireless extensions.

andy@andy-laptop:~$ sudo pccardctl ident
Socket 0:
  no product info available
Socket 1:
  no product info available
:mad:

---

### Post by LEVONO_T42 on 2007-05-07
Please Someone.....

---

### Post by Gatecrasherc6 on 2007-06-23
I'm running with the same bad luck with that card.  It worked fine with Edgy but when I did a fresh install of Feisty, my wireless never worked again.  There has been talk that the Network Manager application has something to do with it who knows, anybody?

---

