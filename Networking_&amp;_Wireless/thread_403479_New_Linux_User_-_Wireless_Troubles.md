---
title: "New Linux User - Wireless Troubles"
date: 2007-04-07
forum: Networking &amp; Wireless
---

### Post by Salo on 2007-04-07
Im new to linux, but not challenged when it comes to computers, so please elaborate when you give instructions.

Heres the problem, I cannot connect via wireless to the internet in Ubuntu 6.10

Im currently dual booting windows xp professional.

Let me make clear that I have no internet on the Ubuntu boot of my computer, so if you recommend a package or file, ensure I can download it via windows and transfer it over manually.

My wireless card is a dlink wda 1320 using an atheros chipset 
(found here [https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported))

I have gone to the GUI settings in the administration section, entered my network name correctly with hexadecimal selected as the passphrase type, and the passphrase is correct. Automatic is set as well, but this brings me nothing but a cannot find server error in firefox.

I have tried manually downloading WPA Supplicant using all the instruction readmes and howtos,
here:
[http://www.neowin.net/forum/lofiversion/index.php/t399787.html](http://www.neowin.net/forum/lofiversion/index.php/t399787.html)

and here:
[http://ubuntuforums.org/showthread.php?t=318539](http://ubuntuforums.org/showthread.php?t=318539)


 and when I get to the part after extracting here:


```
make 
sudo make install 
```

 I get an output full of many errors, I can provide the exact output if required.

The first time around, I didnt think those errors were out of the ordinary so I continued on. I created and configured the wpa config, I added the lines to /network/interfaces (correct path I believe) file to no avail. I retried several times before I noticed that the errors in terminal would have been a problem.

I have already installed madwifi tools, but not madwifi.

but again after extracting the madwifi .tar.gz I attempt to compile/install and recieve an output full of errors. And again I can provide the exact errors if required.

I have heard of people using network manager, but since I dont have internet add/remove programs doesn't function, and I cant find anywhere that will allow me to download a working package.

Just now after my last reboot into ubuntu, my wireless device has disappeared out of Network configuration in the admin menu.

iwconfig only displays lo, and eth1

Been at this for several hours, help would be appreciated.

---

### Post by spd106 on 2007-04-07
You haven't said whether you are using WEP or WPA, so I'll assume you want to use WPA-PSK.

This page provides directions to installing Network Manager [https://help.ubuntu.com/community/WifiDocs/NetworkManager](https://help.ubuntu.com/community/WifiDocs/NetworkManager)
Click on the link to Edgy/Universe then download the package that matches your Architecture (prob i386).

Now reboot to Ubuntu and try to get the card working again, this might just be a simple matter of running this command to insert the card's driver module. ```
sudo modprobe ath_pci
```  Running this comamand will tell you if it was successful. ```
lsmod | grep ath
``` Then proceed to install Network Manager (double-click the .deb file).

If your card still doesn't work then can you post back here with your /etc/network/interfaces file and the output of ```
sudo lshw -class network
```

---

### Post by Salo on 2007-04-07
after typing this:
 ```
sudo modprobe ath_pci

This is the output I get

WARNING: Could not open '/lib/modules/2.6.17-10-generic/madwifi/wlan.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.17-10-generic/madwifi/ath_rate_sample.ko': No such file or directory
FATAL: Could not open '/lib/modules/2.6.17-10-generic/madwifi/ath_pci.ko': No such file or directory
```

After typing this:
```
 lsmod | grep ath

I get this

ath_hal               192976  0 

```

After running:
```
sudo lshw -class network


I get:

  *-network:0 DISABLED    
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 7
       bus info: pci@02:07.0
       logical name: eth0
       version: 10
       serial: 00:01:80:60:94:66
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=8139too driverversion=0.9.27 duplex=half link=no multicast=yes port=MII speed=10MB/s
       resources: ioport:a000-a0ff iomemory:fa010000-fa0100ff irq:209
  *-network:1 UNCLAIMED
       description: Ethernet controller
       product: AR5005G 802.11abg NIC
       vendor: Atheros Communications, Inc.
       physical id: a
       bus info: pci@02:0a.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       resources: iomemory:fa000000-fa00ffff irq:11
```

Output of etc/network/interfaces:

```
auto lo
iface lo inet loopback


iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp


auto wlan0
iface wlan0 inet dhcp
```

_________

And finally, after trying to install the .deb for network manager you linked me to, It said on the top "requires the installation of 2 packages"

And when I click details it lists: to be installed libnl1-pre6 and to be installed libnm-util0

Im checking out for the night, I appreciate your help.
Thanks.

---

### Post by spd106 on 2007-04-07
You need to (re)install the linux-restricted-modules-generic package that matches your kernel, this will provide those missing files. This should be on the installation disk, so it should be installable through Synaptic. If not click [here]("http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Frestricted%2Fl%2Flinux-restricted-modules-2.6.17%2Flinux-restricted-modules-2.6.17-10-generic_2.6.17.7-10.1_i386.deb&md5sum=8557d4dada52b5599601ab350d4be024&arch=i386&type=security")

Sorry about the dependencies I should have checked first. You will need to download

[libnl1-pre6]("http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Flibn%2Flibnl%2Flibnl1-pre6_1.0~pre5%2Bsvn21-2ubuntu2_i386.deb&md5sum=0d836551f19893b6dbc34888b173d809&arch=i386&type=main")
[libnm-util0]("http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fn%2Fnetwork-manager%2Flibnm-util0_0.6.3-2ubuntu6_i386.deb&md5sum=35f0369504c376261c6cddc76e29c64d&arch=i386&type=main")
[dhcdbd]("http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fd%2Fdhcdbd%2Fdhcdbd_1.14-2ubuntu2_i386.deb&md5sum=f597e9322731e08b68815383d274bac2&arch=i386&type=main")
and
[network-manager-gnome]("http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fn%2Fnetwork-manager%2Fnetwork-manager-gnome_0.6.3-2ubuntu6_i386.deb&md5sum=1f857fb5abaa57675e4695baf66289b5&arch=i386&type=main")

---

### Post by Salo on 2007-04-07
Hey man just updating.


Network manager did the trick, after installing those dependencies and then network manager it booted right up, accepted my key, and let me on. Im not ever messing with wpa supplicant or madwifi again.

Thanks for all your help./

---

