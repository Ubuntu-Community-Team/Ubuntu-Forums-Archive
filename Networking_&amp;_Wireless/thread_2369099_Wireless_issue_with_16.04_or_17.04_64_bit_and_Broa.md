---
title: "Wireless issue with 16.04 or 17.04 64 bit and Broadcom card"
date: 2017-08-18
forum: Networking &amp; Wireless
---

### Post by rfrenkel1232 on 2017-08-18
I had a perfectly functioning 16.04 32 bit Ubuntu (updated version 10 or whatever I had) including wireless. I decided to replace it with 17.04 (64 bit) but couldn't get wireless working so loaded 16.04 (64 bit) but still no luck with wireless. 

The hardware is Broadcom BCM4311

I tried the instructions and various drivers indicated for the card at [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx). None of those got as far as turning on the wifi indicator light. So I installed the Windows driver from Dell using ndiswrapper and the instructions at [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper). Once the driver (bcmwl5) was installed, the wifi indicator lit up and has remained lit ever since. However I still get "device not ready" in network manager. 

Some outputs below. I'm discouraged that this didn't work "out of box". I like Unix and appreciate the "turnkey" ease of use of Ubuntu, and when something breaks as badly as this and in as time consuming a manner, it's frustrating.

lspci -v
0c:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
    Subsystem: Dell Wireless 1390 WLAN Mini-Card
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at efdfc000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: [40] Power Management version 2
    Capabilities: [58] MSI: Enable- Count=1/1 Maskable- 64bit-
    Capabilities: [d0] Express Legacy Endpoint, MSI 00
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [13c] Virtual Channel
    Kernel driver in use: ndiswrapper
    Kernel modules: ssb, w


ndiswrapper -l
bcmwl5 : driver installed
    device (14E4:4311) present (alternate driver: ssb)

lshw -C network
*-network DISABLED      
       description: Wireless interface
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: enp12s0
       version: 01
       serial: 00:19:7e:06:c2:ff
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
        configuration: broadcast=yes driver=ndiswrapper+bcmwl5  driverversion=1.60+Broadcom,08/25/2009, 5.60.1 latency=0 link=no  multicast=yes wireless=IEEE 802.11g
       resources: irq:17 memory:efdfc000-efdfffff


iwconfig
enp12s0   IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

ip addr
3: enp12s0: <BROADCAST,MULTICAST> mtu 1500 qdisc pfifo_fast state DOWN group default qlen 1000
    link/ether 00:19:7e:06:c2:ff brd ff:ff:ff:ff:ff:ff

ifconfig enp12s0 up

no error , state changed to "up" after a while but in Network Manger get "Wifi Networks: Device not ready"

What is required to change the state from "Device not ready" ?  

NOTE: when I first installed the driver using ndiswrapper I did get a list of SSIDs but was not able to enter the required info to connect to them. After rebooting, got the above.

---

### Post by praseodym on 2017-08-18
Hi,

Ndiswrapper is not needed here, you should uninstall it and install this firmware instead:
```

wget https://media-cdn.ubuntu-de.org/forum/attachments/04/32/2480236-Broadcom_Firmware.tar.gz  
sudo tar xvf 2480236-Broadcom_Firmware.tar.gz -C /lib/firmware/ 
```

---

### Post by rfrenkel1232 on 2017-08-19
Thanks, I should have posted when struggling with the included drivers!

To get ndiswrapper working I added 
modprobe ndiswrapper
sudo service network-manager restart
to a systemd onetime service and wireless now starts on boot. It's almost exactly 1/2 the speed of wireless on the Windows laptop sitting next to it, but searching indicates this is normal. So I'll live with this for now. Also installed a power manager so I don't get burned with it on my lap :) Details. 

This is admittedly an ancient inadequate Dell 620 laptop, so maybe that's the reason newer versions of Ubuntu don't properly configure wireless out of box.

---

### Post by Hadaka on 2017-08-19
Hi, there are hundreds of old Dell 620's running Ubuntu. 
You don't need to use ndiswrapper to load the correct linux
driver for your broadcom card. Let's get some system information
so we may help you load the driver correctly. Please open a terminal...ctrl/alt/t
then COPY and paste one line at a time.
```
arch
sudo dmidecode -s bios-release-date
free -m | awk '/Mem/{print"Ram "$2}'
lspci -n | awk '/0200|0280/{print$3}'
lsmod | awk '/mac80211/{print$4}'
lsmod | grep -i ndis
```
Please post the output.
*Does your wired connection work ok ???

Thanks

---

