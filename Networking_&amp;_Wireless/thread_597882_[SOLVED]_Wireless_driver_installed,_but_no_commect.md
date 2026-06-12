---
title: "[SOLVED] Wireless driver installed, but no commection"
date: 2007-10-30
forum: Networking &amp; Wireless
---

### Post by leileicats on 2007-10-30
Hi folks, 
I follow the proceduce as above to configure my BCM4311 wireless card on HP NX7400:
[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_(ndiswrapper)]("https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_(ndiswrapper)")

I dowload the sp33008.exe and install the drivers:

lei@lei-laptop:~/driver1$ ndiswrapper -l
Installed ndis drivers:
bcmwl5          driver present, hardware present

Follow the document, 
" If all you see is the driver, but there is no message displayed about the hardware being present, then you need to tell ndiswrapper to use your driver with your device. You will need to determine what the device ID is by typing 'lspci -n' or 'lsusb'. Once you have the device ID, then use the driver:

***user@ubuntu:~/bcm4311$ sudo ndiswrapper -a 14E4:4324 bcmwl5***

Make sure you fill in '14E4:4324' with YOUR device id, and 'bcmwl5' with your driver."

However, on my system:

Usage: ndiswrapper OPTION

Manage ndis drivers for ndiswrapper.
-i inffile        Install driver described by 'inffile'
-d devid driver   Use installed 'driver' for 'devid'
-e driver         Remove 'driver'
-l                List installed drivers
-m                Write configuration for modprobe

I don't have the "-a" option, how can I fix this problem

---

### Post by buntunub on 2007-10-30
That looks like one of those hack job threads. Just follow the guide on this forum for wifi in 5 minutes or less. Worked like a champ for my 4311 chip and has been running flawlessly ever since.

---

### Post by leileicats on 2007-10-30
Hi folks, I just installed Ubuntu 7.04 on my laptop HP NX7400. My wireless card is Broadcom Corporation Dell Wireless 1390 WLAN Mini-PCI Card 14e4:4311 (rev 01). I have "wireless connection" in "Networking settings". However, I can't access Internet if I unplug the cable. It will show "Disconnected" when I am using "Enabling roaming mode". Even I try to set "Network name(ESSID)" as "linksys", no encryption and set "DHCP", but it still don't work.

```

lei@maverick:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4311"
          Mode:Managed  Access Point: Invalid   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```
[B][COLOR="Red"]
If I key in command " lshw -C network "[/COLOR][/B]
```

root@maverick:/home/lei# lshw -C network
  *-network DISABLED      
       description: Wireless interface
       product: Dell Wireless 1390 WLAN Mini-PCI Card
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@10:00.0
       logical name: eth1
       version: 01
       serial: 00:14:a5:d4:f5:36
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.20-15-generic latency=0 link=no multicast=yes wireless=IEEE 802.11b/g
       resources: iomemory:f4000000-f4003fff irq:17
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: e
       bus info: pci@02:0e.0
       logical name: eth0
       version: 02
       serial: 00:17:08:44:8b:99
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=1.01 duplex=full ip=131.104.81.161 latency=64 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: iomemory:f4108000-f4109fff irq:16

```

Could anybody give me some advice?

---

### Post by leileicats on 2007-10-30
Hi folks, I just installed Ubuntu 7.04 on my laptop HP NX7400. My wireless card is Broadcom Corporation Dell Wireless 1390 WLAN Mini-PCI Card 14e4:4311 (rev 01). I have "wireless connection" in "Networking settings". However, I can't access Internet if I unplug the cable. It will show "Disconnected" when I am using "Enabling roaming mode". Even I try to set "Network name(ESSID)" as "linksys", no encryption and set "DHCP", but it still don't work.

```

lei@maverick:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4311"
          Mode:Managed  Access Point: Invalid   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```
[B][COLOR="Red"]
If I key in command " lshw -C network "[/COLOR][/B]
```

root@maverick:/home/lei# lshw -C network
  *-network DISABLED      
       description: Wireless interface
       product: Dell Wireless 1390 WLAN Mini-PCI Card
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@10:00.0
       logical name: eth1
       version: 01
       serial: 00:14:a5:d4:f5:36
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.20-15-generic latency=0 link=no multicast=yes wireless=IEEE 802.11b/g
       resources: iomemory:f4000000-f4003fff irq:17
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: e
       bus info: pci@02:0e.0
       logical name: eth0
       version: 02
       serial: 00:17:08:44:8b:99
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=1.01 duplex=full ip=131.104.81.161 latency=64 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: iomemory:f4108000-f4109fff irq:16

```

Could anybody give me some advice?

---

### Post by JawsThemeSwimming428 on 2007-10-30
Can you explain in detail the steps you took in installing your wireless cards driver?

---

### Post by kevdog on 2007-10-30
You havent installed the user space utilities of the driver -- hence the key word UNCLAIMED in your output -- meaning no driver is claiming the device.  You need an internet connection and install the driver via the linux-restricted package within Synaptic.  Id recommend ndiswrapper anyway -- the bcm43xx driver although it might be better in the future seems very buggy, and many people trying both seem to prefer ndiswrapper.

---

### Post by leileicats on 2007-10-30
When I installed the system, the "Wireless connection" is already in the "Network settings". But I couldn't access the internet. Then I followed "WifiDocs/Driver/bcm43xx/Feisty No-Fluff" to install  the driver again.
[HTML]https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff[/HTML]

There are something wired:
1) 
```
[COLOR="Red"]**eth1**[/COLOR]      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4311"
```
Why it is "eth1", not "wlan0"?

2) When I key in ```
ndiswrapper -v
```
It shows:
```

lei@maverick:~/driver$ ndiswrapper -v
utils Error: no version specified!
driver version:        1.38
vermagic:       2.6.20-16-generic SMP mod_unload 586 

```
Is there something wrong with my NDISwrapper?

Thanks

---

### Post by leileicats on 2007-10-30
When I installed the system, the "Wireless connection" is already in the "Network settings". But I couldn't access the internet. Then I followed "WifiDocs/Driver/bcm43xx/Feisty No-Fluff" to install  the driver again.
[HTML]https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff[/HTML]

There are something wired:
1) 
```
[COLOR="Red"]**eth1**[/COLOR]      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4311"
```
Why it is "eth1", not "wlan0"?

2) When I key in ```
ndiswrapper -v
```
It shows:
```

lei@maverick:~/driver$ ndiswrapper -v
utils Error: no version specified!
driver version:        1.38
vermagic:       2.6.20-16-generic SMP mod_unload 586 

```
Is there something wrong with my NDISwrapper?

Thank

---

### Post by kevdog on 2007-10-30
That is the problem with your bcm43xx -- you had to be corrected to the internet to complete the installation.

As far as ndiswrapper - there is no problem, however I can see that you are using the version from the repository.  I know Im sending you more into hot water, but you would be better off installing from source code (yikes).  There is a guide in my signature to help you.

---

### Post by leileicats on 2007-10-31
Hi Kevdog, I reviewed your guide and fixed my problem. That guide is really awesome. Thanks a lot!:lolflag:

---

