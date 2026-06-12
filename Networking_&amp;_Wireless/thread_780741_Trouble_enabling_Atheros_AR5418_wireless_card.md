---
title: "Trouble enabling Atheros AR5418 wireless card"
date: 2008-05-03
forum: Networking &amp; Wireless
---

### Post by Basil101 on 2008-05-03
Hey all,
Basically as the title says I can't get my wireless card to function under Ubuntu 8.04 (worked with 7.10)
I think that the hardware is disabled as the wireless LED doesn't light up as it used too in 7.10 but I am at a loss to enable the card.

Finally some often asked for command outputs;

**lspci;**
05:00.0 Network controller: Atheros Communications Inc. AR5418 802.11abgn Wireless PCI Express Adapter (rev 01)

**iwconfig;**
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

**lshw;**
*-network
                description: Wireless interface
                product: AR5418 802.11abgn Wireless PCI Express Adapter
                vendor: Atheros Communications Inc.
                physical id: 0
                bus info: pci@0000:05:00.0
                logical name: wlan0
                version: 01
                serial: 00:15:af:4e:6b:09
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ndiswrapper+net5416 driverversion=1.52+,06/26/2007,6.0.3.94 latency=0 module=ndiswrapper multicast=yes wireless=IEEE 802.11g

Any help greatly appreciated, if you need the outputs of any other commands just ask.
Thanks!

---

### Post by Basil101 on 2008-05-05
I have fiddled with computer a little more and the card is turned on during boot (the duration of the splash screen) before turning off again. 
Any ideas?

---

### Post by echo6 on 2008-05-05
I have the same problem.  Possibly udev rules or driver?!

Try sudo modprobe ath_pci

It still didn't work for me, the driver loaded fine.
```
[  535.330498] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[  535.464676] wlan: 0.9.4
[  535.495048] ath_pci: 0.9.4
```

```
04:00.0 Network controller: Atheros Communications Inc. AR5418 802.11abgn Wireless PCI Express Adapter (rev 01)
        *-pci:2
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-network UNCLAIMED
                description: Network controller
                product: AR5418 802.11abgn Wireless PCI Express Adapter
                vendor: Atheros Communications Inc.
                physical id: 0
                bus info: pci@0000:04:00.0
                version: 01
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix cap_list
                configuration: latency=0

```

---

### Post by echo6 on 2008-05-05
OK I have it working using the latest svn trunk, try this:-

```
sudo apt-get install build-essential autoconf automake
svn checkout http://svn.madwifi.org/madwifi/trunk/ madwifi-ng
cd madwifi-ng
sudo ./scripts/madwifi-unload
make
sudo make install
sudo modprobe ath_pci

```

Hmmmm,  its not as hopeful as I thought.  Installing the driver detects the presence of the interface correctly and I can connect ok but after a while the connection drops with no indication.  It may be worth trying different revision number though.

---

### Post by echo6 on 2008-05-05
I'm having better luck with this version though.
[http://snapshots.madwifi.org/madwifi-trunk/madwifi-ng-r3550-20080420.tar.gz](http://snapshots.madwifi.org/madwifi-trunk/madwifi-ng-r3550-20080420.tar.gz)

---

### Post by Totempoles on 2008-05-20
Echo 6: 

Thanks for your guidance; I was able to install wireless driver for AR5418, and now see AP visible, but am able to connect. I see that my wireless indicator light is on not on, could the radio be off? But I have no idea how to turn it back on in Unbuntu. Under Vista, there was a utility. Any suggetions? 

I'm new to Ubuntu and Terminal, so any easy tutorial is appreciated. 
Below is my configuration:

 *-network
       description: Wireless interface
       product: AR5418 802.11abgn Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wifi0
       version: 01
       serial: 00:19:7e:2f:61:f8
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci latency=0 module=ath_pci multicast=yes wireless=IEEE 802.11g
timothy@Ubuntu-T60p:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:14 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-96 dBm  Noise level=-96 dBm
          Rx invalid nwid:48522  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

irda0     no wireless extensions.

Following day:

I've resorted to using NDISwrapper and was able to download the driver for this Atheros card from IBM/Lenovo Web site, extract drivers and install using NDISwrapper.

Now, the LED wireless indicator blinks rhythmically, and AP are visible via Network Mgr, but no luck in connecting to restricted or unrestricted points. 

1. Since I previously tried Madwifi with no luck, does this pose any conflict with Windows driver? (It is disabled in hardware drivers)
2. Any guess on how I might connect T60? I did try Wicd, but system froze after installation.

Thanks for any pointers.

---

