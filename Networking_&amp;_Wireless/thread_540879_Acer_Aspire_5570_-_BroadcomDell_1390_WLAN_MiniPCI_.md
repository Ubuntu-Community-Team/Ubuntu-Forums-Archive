---
title: "Acer Aspire 5570 - Broadcom/Dell 1390 WLAN MiniPCI Card"
date: 2007-09-02
forum: Networking &amp; Wireless
---

### Post by delibercogito on 2007-09-02
Broadcom Corporation Dell Wireless 1390 WLAN Mini-PCI Card (rev 01)

Installed Feisty Earlier today.  The wireless card was detected, but didn't show any networks. 

Followed this guide: [http://ubuntuforums.org/showthread.php?t=297092](http://ubuntuforums.org/showthread.php?t=297092)

It worked.  Fantastically.

And then I made the tragic mistake of doing my updates, and it broke.  Googling revealed that some kernel update is breaking wireless.  So I figured, if I reload Ubuntu again, and don't update, and follow that guide again precisely, it should work.  And it should have, logically.

Except it didn't.  So I then tried these, too: 

[http://www.linux-geek.org/index.php/2007/04/22/dell-1390-native-linux-driver-how-to-updated](http://www.linux-geek.org/index.php/2007/04/22/dell-1390-native-linux-driver-how-to-updated)

[http://linux.dell.com/wiki/index.php/Tech/Wireless/Truemobile_ndiswrapper](http://linux.dell.com/wiki/index.php/Tech/Wireless/Truemobile_ndiswrapper)

[http://ubuntuforums.org/showthread.php?t=405990](http://ubuntuforums.org/showthread.php?t=405990)

EVERYTIME I tried a new solution I did so with a COMPLETELY clean, non updated install.  Yes, I've reloaded Ubuntu about 6 times tonight. 

BCMxx drivers made the LED indicator work, the card scanned, no networks found.  
NDISWrapper iwlist scanning gives the same result.  Network manager finds nothing.  What I can't understand is why it worked the first time, and didn't work under the same exact conditions the next time.

If anyone has any suggestions, that'd be fantastic.  I adore Ubuntu.  I have it on 4 desktops, but unfortunately a laptop that can't do wifi isn't acceptable.  I'm hating that I might have to install windows to have a functional laptop.

EDIT:

I've been trying for over 12 total hours to get a Broadcom Corporation Dell 1390 WLAN Mini PCI Card working.  I've tried every HowTo on the entire internet.  I even went so far as to make every different attempt on a completely fresh install to avoid leftover complications.  I am happy to say, that it now works. 

Now, WHY it works, makes little sense.  But it does.  This is on an Acer Aspire 5570-2052.  This is with a completely clean install from a Ubuntu 7.04 LiveCD.  Completely clean meaning I DID NOT DO ANY UPDATES.  I am sure that based on previous issues, UPDATES WILL BREAK THIS.

YOU MUST HAVE A USB WIRELESS ADAPTER FOR THIS TO WORK.

Skip the following UNLESS you are using an Acer that is listed as compatible here: [http://code.google.com/p/aceracpi/wiki/SupportedHardware](http://code.google.com/p/aceracpi/wiki/SupportedHardware) 

Go to:
[http://code.google.com/p/aceracpi/](http://code.google.com/p/aceracpi/)

Download acer_acpi-0.8.1.tar.bz2
Extract it.

Open a terminal and navigate to the acer_acpi-0.8.1 directory.
make
sudo make install

Follow this guide: [http://ubuntuforums.org/showthread.php?t=224349](http://ubuntuforums.org/showthread.php?t=224349) starting at Load the acer_acpi into memory and activate the wireless:

Note the typo in the original post at:


Code:

ls /etc/rcS.d/S39acer-acpi-wireless-enable
ls /etc/rc0.d/S34acer-acpi-wireless-enable
ls /etc/rc6.d/S34acer-acpi-wireless-enable

should be

Code:

ls /etc/rcS.d/S39acer_acpi_wireless_enable
ls /etc/rc0.d/S34acer_acpi_wireless_enable
ls /etc/rc6.d/S34acer_acpi_wireless_enable

Finish the guide and reboot.

Go to [http://ubuntu.cafuego.net/dists/feisty-cafuego/bcm43xx/](http://ubuntu.cafuego.net/dists/feisty-cafuego/bcm43xx/)

Download and install 	bcm43xx-firmware_1.3-1ubuntu2_all.deb

reboot.

You'll notice that network manager will still not list any networks.

Plug in a USB Wireless Adapter. I used a Linksys WUSB54GC.  Wait for a second.  Click on Network Manager again.  It should now list both wireless devices.  Unplug the USB adapter.  Your onboard wireless should still list networks at this point.  Make sure you can connect to one.  Reboot.

[I plugged in the Linksys adapter because I'd given up on getting the onboard to work and figured I'd just try the USB adapter.  Imagine my suprise (and cursing) when suddenly, the onboard worked.]

---

### Post by noob12 on 2007-09-02
This has worked for a lot of people and is pretty much automated.

[http://ubuntuforums.org/showthread.php?t=405990](http://ubuntuforums.org/showthread.php?t=405990)

UPDATE: Stupid me.  I just now noticed that you had included that in your list.

---

### Post by noob12 on 2007-09-02
Sorry for my previous useless posting.  

By any chance did you disable the wireless radio at some point?

Can you show us your current situation:

```

sudo lshw -C network

ndiswrapper -l

sudo iwconfig

sudo iwlist scan

```

---

### Post by delibercogito on 2007-09-03
My current configuration is a fresh NON UPDATED install, with acer_acpi installed as described here: [http://ubuntuforums.org/showthread.php?t=224349&page=2](http://ubuntuforums.org/showthread.php?t=224349&page=2)

```

liber@eris:~$ sudo lshw -C network
Password:
  *-network               
       description: Ethernet interface
       product: 88E8038 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@02:00.0
       logical name: eth0
       version: 14
       serial: 00:1b:24:45:71:7c
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.13 duplex=full firmware=N/A ip=192.168.1.100 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: iomemory:54000000-54003fff ioport:2000-20ff irq:16
  *-network DISABLED
       description: Wireless interface
       product: Dell Wireless 1390 WLAN Mini-PCI Card
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@03:00.0
       logical name: eth1
       version: 01
       serial: 00:19:7e:73:3a:43
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.20-15-generic latency=0 link=no multicast=yes wireless=IEEE 802.11b/g
       resources: iomemory:54100000-54103fff irq:17
liber@eris:~$ ndiswrapper -l
The program 'ndiswrapper' is currently not installed.  You can install it by typing:
sudo apt-get install ndiswrapper-common
bash: ndiswrapper: command not found
liber@eris:~$ 
liber@eris:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:""  Nickname:"Broadcom 4311"
          Mode:Managed  Access Point: Invalid   
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

liber@eris:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Interface doesn't support scanning : No such device

```

---

### Post by noob12 on 2007-09-03
As I understand now from your edited initial post, you have got things working and no longer need help?  or do you still need assistance?

---

