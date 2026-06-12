---
title: "problem recognizing my wireless card"
date: 2008-03-01
forum: Networking &amp; Wireless
---

### Post by skylancer90 on 2008-03-01
here's my stuff:

ubuntu 7.10 gutsy
broadcom 802.11bg wlan
intel dual core processor
and i use my neighbors unencrypted wireless network "linksys"

the scenario:
after installing ubuntu, i downloaded the file "native bcm43xx driver" according to this guide-

[http://ubuntuforums.org/showthread.php?t=197102&highlight=dependency+issue](http://ubuntuforums.org/showthread.php?t=197102&highlight=dependency+issue)

so, after some minor problems with installing that, it was done. okay. so i typed in the command:

*lshw -C network*

while following this guide:

[http://ubuntuforums.org/showthread.php?t=571188&highlight=wireless](http://ubuntuforums.org/showthread.php?t=571188&highlight=wireless)

and it appeared that it recognized the driver "driver=r8169 driverversion=2.2LK". but later (following the same guide) i typed in the command:

*sudo ifconfig eth0 up*

and didn't get any response, it just went to the next line like a normal command. but when i typed:

*sudo iwconfig eth0 essid "linksys"*

it said "error for wireless request 'set essid' (8b1a) :
  SET failed on device eth0 ; Operation not supported." (im typing this out cause i only have a connection on my windows computer....) 

and when i type "iwconfig" the result is:

"lo      no wireless extensions.

eth0 no wireless extensions."

so it seems that my wireless card isnt being recognized even after installing the drivers. 
another thing that you might need that ive seen people ask for in other threads is my "/etc/network/interfaces" this is what it says:

"auto lo
iface lo inet loopback" 

if you need any more information to figure out whats wrong, i'll be here, so dont hesitate!

---

### Post by Hightide on 2008-03-01
Hi skylancer90

See will this [guide]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Gutsy") help


regards

:)

---

### Post by skylancer90 on 2008-03-01
> **Hightide said:**
> Hi skylancer90

See will this [guide]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Gutsy") help


regards

:)

yeah, thanks that guide seems appropriate, but on step 6, it says to click my restricted driver manager. well when i click on it, it says "your hardware does not need any restricted drivers" 

its almost like my wireless card doesnt exist on here. there isnt even an option to connect to wireless under "network settings". please help!!

---

### Post by uberlube on 2008-03-01
You have to install your wireless driver with ndiswrapper. Try my guide and let me know if it helps.
[http://ubuntuforums.org/showthread.php?t=706034](http://ubuntuforums.org/showthread.php?t=706034)

---

### Post by skylancer90 on 2008-03-01
> **uberlube said:**
> You have to install your wireless driver with ndiswrapper. Try my guide and let me know if it helps.
[http://ubuntuforums.org/showthread.php?t=706034](http://ubuntuforums.org/showthread.php?t=706034)

that guides easy to follow, but at the part where i have to type

*wget [http://ftp.us.dell.com/network/R151517.EXE](http://ftp.us.dell.com/network/R151517.EXE)*

i cant get any farther cause i dont have any connection whatsoever. also, wlan0 doesnt even show up during ifconfig or iwconfig. all i get is "lo" and "eth0". its seriously like my wireless card doesnt exist.

---

### Post by uberlube on 2008-03-01
Your system doesnt recognize it yet thats why its not showing up. As for the file you need to download, can you get it off another cpu with an internet connection and transfer it into that file you created?

---

### Post by skylancer90 on 2008-03-01
> **uberlube said:**
> Your system doesnt recognize it yet thats why its not showing up. As for the file you need to download, can you get it off another cpu with an internet connection and transfer it into that file you created?

any idea of what files i would have to download? the weird thing is. when i type in "lshw -C network", it seems to show my broadcom card:

*-network UNCLAIMED
        description: Network controller
        product: BCM4310 USB Controller
        vendor: Broadcom Corporation
        physical id: 0
        bus info: pci@0000:06:00.0
        version: 01
        width: 64 bits
        clock: 33MHz
        capabilities: bus_master cap_list
        configuration: latency=0
*-network
        description: Ethernet interface
        product: RTL8101E PCI Express Fast Ethernet controller
        vendor: Realtek Semiconductor Co., Ltd.
        physical id: 0
        bus info: pci@0000:06:00.0
        logical name: eth0
        version: 01
        serial: 00:1b:24:fe:fa:78
        width: 64 bits
        clock: 33MHz
        capabilities: bus_master cap_list ethernet physical
        configuration: broadcast=yes driver=r8169 driverversion=2.2LK latency=0 module=r8169 multicast=yes

weird huh?

---

### Post by uberlube on 2008-03-01
In you last post you wrote the 'wget' line and there is an address beside it. Click on that address and it will download the file you need.

---

### Post by skylancer90 on 2008-03-01
> **uberlube said:**
> In you last post you wrote the 'wget' line and there is an address beside it. Click on that address and it will download the file you need.

ok i followed your guide, but nothin seemed to really happen. this is still the result of "iwconfig":

[I]lo no wireless extensions.

eth0 no wireless extensions.[/I]

---

### Post by Hightide on 2008-03-02
HI Skylancer90

see will this ubuntu [wiki]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Gutsy") help

regards
:)

---

