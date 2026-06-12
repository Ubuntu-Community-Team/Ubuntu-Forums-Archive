---
title: "Acer Aspire 5517 / Broadcom BCM4312"
date: 2014-02-17
forum: Networking &amp; Wireless
---

### Post by jordan16 on 2014-02-17
It doesn't even give me the option to connect to any network. I have tried some other things on the forum, but none relate to me specifically. I have an Acre aspire 5517 and just partitioned part of my hard drive with windows 7 on it for Ubuntu. I've even tried connecting through a wired connection, but that doesn't work ether. Any help would be appreciated!

---

### Post by Bucky Ball on 2014-02-17
Welcome. Open a terminal and copy/paste this:
```

sudo lshw -C network
```

Hit 'return' and post the output back here, thanks.

---

### Post by jordan16 on 2014-02-18
```
*-network               
       description: Network controller 
       product: BCM4312 802.11b/gLP-PHY 
       vendor: Broadcom Corporation 
       physical id: 0 
       bus info: pci@0000:02:00.0 
       version: 01 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpressbus_master cap_list 
       configuration:driver=b43-pci-bridge latency=0 
       resources: irq:16memory:f1100000-f1103fff 
  *-network 
       description: Ethernet interface 
       product: AR8132 Fast Ethernet 
       vendor: Qualcomm Atheros 
       physical id: 0 
       bus info: pci@0000:08:00.0 
       logical name: eth0 
       version: c0 
       serial: 00:26:22:19:36:27 
       capacity: 100Mbit/s 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpressvpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt100bt-fd autonegotiation 
       configuration:autonegotiation=on broadcast=yes driver=atl1cdriverversion=1.0.1.1-NAPI latency=0 link=no multicast=yesport=twisted pair 
       resources: irq:43memory:f1000000-f103ffff ioport:2000(size=128)
```

---

### Post by Vladlenin5000 on 2014-02-18
AFAIK both the Ethernet and the WiFi are already natively supported therefore I really don't understand why neither works.
I'll leave it to the resident expert. Good luck.

---

### Post by Bucky Ball on 2014-02-18
These links should provide some interesting reading:

For BCM4312:
[http://www.ubuntuask.com/q/answers-no-wireless-connection-detected-hp-pavilion-dv6-1220-with-a-broadcom-bcm-4312-101104.html](http://www.ubuntuask.com/q/answers-no-wireless-connection-detected-hp-pavilion-dv6-1220-with-a-broadcom-bcm-4312-101104.html)

For BCM43**:
[http://askubuntu.com/questions/55868/how-to-install-broadcom-wireless-drivers-bcm43xx](http://askubuntu.com/questions/55868/how-to-install-broadcom-wireless-drivers-bcm43xx)

Check supported cards/more info here:
[http://wireless.kernel.org/en/users/Drivers/b43](http://wireless.kernel.org/en/users/Drivers/b43)

This is your wireless device so the first link should fix it. 

product: BCM4312 802.11b/gLP-PHY 

The problem is that you have no cable connection either, but that can be overcome. Read about installing b43 with no internet here:

Ubuntu b43 wifi docs:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43_-_No_Internet_access](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43_-_No_Internet_access)

This is what I would advise, from that first link:

```
sudo apt-get remove bcmwl-kernel-source
sudo apt-get purge b43-fwcutter firmware-b43-installer firmware-b43-lpphy-installer firmware-b43legacy-installer bcmwl*
sudo apt-get install b43-fwcutter firmware-b43-installer bcmwl*
```

... but as I say, without a cable connection, that ain't going to work.

PS: Yes, they are both natively supported, but the bcm4312 can sometimes get the wrong driver. Odd things happen. Don't understand the wired connection also being out, though. But I don't have a lot of experience with them. :-k

---

### Post by varunendra on 2014-02-18
jordan16,

First of all, please use 'Code' tags for posting command outputs. It preserves their formatting and makes them more readable. Please follow the "Using Code Tags" link in my signature below to see a quick HowTo with screenshots.

About your problem, your card is a "Low Power" model from Broadcom, and so uses an "LP" variation of the firmware -
> **jordan16 said:**
> 
       product: BCM4312 802.11b/g **LP-PHY** 

I believe this firmware is included in the "linux-firmware-nonfree" package. You can download it manually on another computer then install it on Ubuntu by simply double-clicking it.

Here is the link for Saucy (version doesn't matter, but the 'double-click' way to install it would only work if the version matches your Ubuntu version) : [http://packages.ubuntu.com/saucy/all/linux-firmware-nonfree/download](http://packages.ubuntu.com/saucy/all/linux-firmware-nonfree/download)

Download from any of the mirrors listed on the page > Copy it to your Ubuntu Desktop > double-click to install with your default package manager.

If the "Install" button is disabled in the package manager, you can install it forcibly via terminal (there is no harm in doing so with 'This' package). To install it that way, open a terminal (Ctrl-Alt-T) and run the following command (assuming the downloaded package is on your desktop) -
```
sudo dpkg -i Desktop/linux-firmware-nonfree*.deb
```
After that, either reboot, or manually reload the driver with the following commands -
```
sudo modprobe -rv b43
sudo modprobe -v b43
```
Your wifi should be working now.

Your Ethernet should be working too.. it already has a suitable driver loaded. So let us know if you wish to troubleshoot that too.

---

