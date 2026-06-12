---
title: "How can i get wireless detection?"
date: 2008-07-09
forum: Networking &amp; Wireless
---

### Post by MasterNetra on 2008-07-09
I was wondering how do i get my system to detect available wireless connections? I'm using Ubuntu on a Dell Latitude D530 (not sure if pc type is any use.)

---

### Post by pytheas22 on 2008-07-09
Please open a terminal (Applications>Accessories menu) and run these commands, and then post here the output:
```

iwconfig
lspci
lsusb
lshw -C Network
```

That will tell us what kind of wireless cards you have, and from there we can figure out what you need to do to get them working.

---

### Post by MasterNetra on 2008-07-09
> **pytheas22 said:**
> Please open a terminal (Applications>Accessories menu) and run these commands, and then post here the output:
```

iwconfig
lspci
lsusb
lshw -C Network
```

That will tell us what kind of wireless cards you have, and from there we can figure out what you need to do to get them working.

[iwconfig Result]:

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

[lspci result]:

[Relevent Info]
09:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5755M Gigabit Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11a/b/g (rev 01)

[lsusb only detected mouse]

[lshw -C Result]:
  *-network               
       description: Network controller
       product: BCM4312 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network
       description: Ethernet interface
       product: NetXtreme BCM5755M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:1d:09:a9:47:0f
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.86 firmware=5755m-v3.32 ip=192.168.1.3 latency=0 module=tg3 multicast=yes
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1e:4c:15:05:3b
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

---

### Post by chalewa on 2008-07-09
so i take it no networks show up when you look in the network manager?

---

### Post by Kevbert on 2008-07-09
What's the output of 
```
iwlist scanning
```
If you get nothing, are you sure there's a network nearby ?  It looks like your Broadcom card is working.  It may still be a driver (firmware) problem.
Please have a look at this [[COLOR="Red"]link[/COLOR]]("http://ubuntuforums.org/showthread.php?t=766560").

---

### Post by pytheas22 on 2008-07-09
Thanks for the information.  You have a Broadcom bcm4312 chipset.  There is a native driver for it (called b43), but from what I gather, it doesn't work well, if at all, for your particular card.  That should change in the next release of Ubuntu.

In the meantime, it's possible to drive your card using ndiswrapper, a utility that loads Windows drivers for wireless cards.  Here are directions, adapted from [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-bc33832c0547766a33c3a84f13f971ca757b2851](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-bc33832c0547766a33c3a84f13f971ca757b2851) :

```
sudo -s
echo 'blacklist b43' >> /etc/modprobe.d/blacklist
echo 'blacklist ssb' >> /etc/modprobe.d/blacklist
echo 'blacklist b43legacy' >> /etc/modprobe.d/blacklist
apt-get install ndiswrapper* cabextract
wget [ftp://ftp.compaq.com/pub/softpaq/sp33001-33500/sp33008.exe](ftp://ftp.compaq.com/pub/softpaq/sp33001-33500/sp33008.exe)
cabextract sp33008.exe
ndiswrapper -i bcmwl5.inf
```

Then reboot and your connection should work.  If it still doesn't, please post:
```

cat /etc/modprobe.d/blacklist
iwconfig
ndiswrapper -l
```

Also, please note that the instructions above assume that you're using a 32-bit system.  If you're on 64-bit, please say so because the directions need to be changed a little bit.

---

### Post by MasterNetra on 2008-07-09
> **Kevbert said:**
> What's the output of 
```
iwlist scanning
```
If you get nothing, are you sure there's a network nearby ?  It looks like your Broadcom card is working.  It may still be a driver (firmware) problem.
Please have a look at this [[COLOR="Red"]link[/COLOR]]("http://ubuntuforums.org/showthread.php?t=766560").

I am 100% sure there are networks nearby. I've used them with windows and one is provided by my router and thats not even seen. SO i guess it is a driver thing.

---

### Post by linuxonbute on 2008-07-09
> **MasterNetra said:**
> [iwconfig Result]:

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


This seems to indicate that your wireless card is just not configured.

try  System/administration/Network

if you see an option for your wireless then you should be able to set it up from there.

---

### Post by MasterNetra on 2008-07-09
I figured it out I was right clicking instead of left-clicking i feel like a idiot x.x

---

