---
title: "Driver Installed - No connection"
date: 2007-03-11
forum: Networking &amp; Wireless
---

### Post by ReKast on 2007-03-11
Hi all, i am a new linux user, only 2 weeks in, and i have to say i love it. i have been constantly working on fixing all the miner problems that come from not getting support from manufacturers, but this is where the linux, and ubuntu community shine.

Ok so enough intro, i have finally gotten my wireless pci adapter to install (after having to recompile the source ndiswrapper) and now my problem seems to be not being able to connect, my device is working and can pick up the router, however if i enable the wireless internet connection from the networking tab and cancel the current ethernet one i cant connect, any help would be apreciated, and if this problem has been solved before please forgive and post the link.


device is WMP54GX
it is a PCI wireless adapter

this is the output of the etc/network/interfaces file

auto lo
iface lo inet loopback


iface eth0 inet static
address 192.168.0.2
netmask 255.255.255.0
gateway 192.168.0.1

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp


iface wlan0 inet static
wireless-essid BARSOUM1507
wireless-key 2525242422
address 192.168.0.2
netmask 255.255.255.0
gateway 192.168.0.1

and as to lspci

00:00.0 Host bridge: Intel Corporation 925X/XE Express Memory Controller Hub (rev 04)
00:01.0 PCI bridge: Intel Corporation 925X/XE Express PCI Express Root Port (rev 04)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FR/FRW (ICH6R/ICH6RW) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
04:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8050 PCI-E ASF Gigabit Ethernet Controller (rev 17)
06:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 MX 420] (rev a3)
06:02.0 Ethernet controller: Airgo Networks Inc Unknown device 0001 (rev 03)
06:05.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 61)

---

### Post by bernied on 2007-03-11
A couple of ideas:
- it is probably a bad idea to assign the same IP address to eth0 and wlan0. When the computer starts, eth0 will come up whether it is connected or not, and it will be assigned the IP address first. I don't know what happens when you try to assign the same address again to the wireless adapter, but it is probably best avoided (unless you know that this will work)
- what is the output of 'iwconfig'? (This shows you the status of your connection with the accesspoint, you can also control the connection, try 'man iwconfig' for details)

---

### Post by ReKast on 2007-03-11
i have tried DHCP before with the same result, now theres a new problem, i started my computer and the device is not on, it is not in hte networking section either, does this have anything to do with ndiswrapper ? also i realized that i installed the whole kernel header package and not just the one for my processor, would this be a problem with manual recompile?

so iwconfig is now

lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

before it was showing the status of wlan0, if the ip was static it would list it, if now it wouldnt be able to get one, im gonna try getting the device to work again and repost the iwconfig

---

### Post by ReKast on 2007-03-11
so i know i might be thinking way off, but is it possible that its because i used ndiswrapper-1.38 
the output to that version goes like this
netani : driver installed
        device (17CB:0001) present

just a thought

---

### Post by ReKast on 2007-03-11
ok output for iwconfig is the following

lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

wlan0     Auto  ESSID: off/any  
          Mode:Managed  Channel: 0  Access Point: Not-Associated   
          Bit Rate:108 Mb/s   
          Encryption key: off
          Power Management: off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by ReKast on 2007-03-11
i tried setting the ESSID manually through the terminal, but whenever i run iwconfig the information is not there

---

### Post by ReKast on 2007-03-12
Bump

---

### Post by bernied on 2007-03-12
> **ReKast said:**
> i tried setting the ESSID manually through the terminal, but whenever i run iwconfig the information is not there
What did you try and what was the output?

---

### Post by bernied on 2007-03-12
Have you read [this](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Windows_Wireless_Drivers_.28Ndiswrapper.29)?

Have you tried using network-manager?
Something like [this](http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html)?

Be careful with this howto, it's for an older version of ubuntu, but it should still work. You might be able to find network-manager using your GUI package manager rather than using apt-get. If you are using kde, then don't install the gnome package, use knetworkmanager, which is the kde equivalent. I've used network-manager and it works well.

You might want to take backup copies of any configuration files that you are about to modify, for instance, for the interfaces file:
```
sudo cp /etc/interfaces /etc/interfaces.backup
```(sudo means do it as root user, cp means copy)
If you write down which files you've changed, then if anything goes wrong you can reverse your changes like this:```
sudo cp /etc/interfaces.backup /etc/interfaces
```

---

### Post by ReKast on 2007-03-12
im having the same problem again, i restarted my computer and the device was not recognized, i reinstalled ndiswrapper and the drivers, and tried loading the modules again, still not on, any advice? could it just be the device or do you think that its ubuntu?

---

