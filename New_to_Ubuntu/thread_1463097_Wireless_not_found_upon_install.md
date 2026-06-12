---
title: "Wireless not found upon install"
date: 2010-04-26
forum: New to Ubuntu
---

### Post by pastorbobbyp on 2010-04-26
I'm brand new to ubuntu.  I installed version 9.10 within Windows7.  When I boot to ubuntu it doesn't pickup my wireless device at all.  Is there something I need to do to get the device recognized?  I looked for some kind of a hardware list that might show me whether or not my wireless card is active ubuntu but found nothing.  I really want to use ubuntu, but this wireless thing is a show stopper for me.  Thanx.

---

### Post by Hospadar on 2010-04-26
A couple things:
Since you're brand new to ubuntu, and don't even have a working  installation yet, I'd first install the latest version, 10.4, it's not  technically out yet, but it will be officially released in a couple  days, and installing the 10.4 release candidate would save you the  upgrading hassle (especially since you probably aren't yet very tied to  your current ubuntu installation).

You can get a cd for this latest version here:  [http://mirror.csclub.uwaterloo.ca/ubuntu-releases/10.04/](http://mirror.csclub.uwaterloo.ca/ubuntu-releases/10.04/) (you'll  probably want the AMD64 desktop cd, but if you have an older machine,  pentium-3 ish, perhaps the x86 cd)

You may find in this newer version that your wireless works out of the  box.  If not, clicking on the wireless icon in the system tray area  should at least give a little more detailed info about what wifi card  you have, so you can relay it here, and/or google the correct things.

Aside from installing the new version, the first thing you'll want to  check is the hardware drivers tool.  This contains various  non-open-source drivers which are not installed by default for legal  reasons.  You can find this tool in  System->Administration->Hardware Drivers.  If there is a  non-open-source driver available, it will show up here and you can  install it.  Note that, for this to work, you'll need a network  connection, which means either an ethernet cable or perhaps a usb wifi  card that works with out-of-the-box ubuntu (that's what I use, I have  one floating around).

If that proves to be of no use, you'll need more detailed info about  your wireless card so you can search around for a more specific  solution.  To get that, open up a terminal  (Applications->Accesories->Terminal) and type in the following two  commands ```
lspci
sudo lshw -C network
```

The goal of these commands is to try and figure out the chipset (i.e.  make/model) of your wifi hardware, if you can't figure that out from  just looking at the output of those commands (they are somewhat  information-rich and cryptic), just post the output to these forums and  ask someone what your wifi chipset is and they'll be able to help for  sure.

---

### Post by pastorbobbyp on 2010-04-26
I tried installing 10.4.  Now, at least I can see the network icon at the top of the page.  It shows no connection.  When I did the "sudo" command it showed the wireless controller as DISABLES.  In Windows I can go into the hardware manager and enable the device.  How is this accomplished in ubuntu?  **Thanx!**

   pastorbob@ubuntu:~$ lspci
  00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
  00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
  00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
  00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
  00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
  00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
  00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
  00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
  00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
  00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
  00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
  00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
  00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
  00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
  00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
  00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
  00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
  00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 02)
  00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
  03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
  03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
  03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
  03:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
  03:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
  0c:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
  pastorbob@ubuntu:~$ sudo lshw -C network
  [sudo] password for pastorbob: 
    *-network               
         description: Network controller
         product: BCM4311 802.11b/g WLAN
         vendor: Broadcom Corporation
         physical id: 0
         bus info: pci@0000:0c:00.0
         version: 01
         width: 32 bits
         clock: 33MHz
         capabilities: pm msi pciexpress bus_master cap_list
         configuration: driver=b43-pci-bridge latency=0
         resources: irq:17 memory:fe8fc000-fe8fffff
    *-network
         description: Ethernet interface
         product: BCM4401-B0 100Base-TX
         vendor: Broadcom Corporation
         physical id: 0
         bus info: pci@0000:03:00.0
         logical name: eth0
         version: 02
         serial: 00:1c:23:aa:2a:08
         size: 10MB/s
         capacity: 100MB/s
         width: 32 bits
         clock: 33MHz
         capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
         configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half latency=64 link=no multicast=yes port=twisted pair speed=10MB/s
         resources: irq:17 memory:fe5fe000-fe5fffff
   ***-network DISABLED**
  **       description: Wireless interface**
  **       physical id: 2**
  **       logical name: wlan0**
  **       serial: 00:1d:60:4f:e2:85**
  **       capabilities: ethernet physical wireless**
  **       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg**
  pastorbob@ubuntu:~$

---

### Post by anewguy on 2010-04-26
These steps might get you going - it requires that you hard-wire your computer to your router for a minute or two.

sudo apt-get update

Now look under System/Administration/Hardware Drivers and see if a driver shows - if so enable it.

Disconnect the hard-wire cable, wait a few seconds, then check in network manager to see if wireless is now working (be sure the "Enable Wireless" is checked in network manager).

Dave ;)

---

### Post by pastorbobbyp on 2010-04-27
That did the trick.  Thanx!

---

### Post by pastorbobbyp on 2010-04-27
Now, how do I mark something as **SOLVED**?

---

### Post by P4man on 2010-04-27
In thread tools (top right, in red)

---

### Post by Bob Appleby on 2010-04-27
How do I   (be sure the "Enable Wireless" is checked in network manager)?

I see network connections, network proxy, network tools, but no network manager.

---

### Post by P4man on 2010-04-27
> **Bob Appleby said:**
> How do I   (be sure the "Enable Wireless" is checked in network manager)?

I see network connections, network proxy, network tools, but no network manager.

Right click the network icon in the top right panel. You should see "enable networking" and "enable wireless networking" (the latter only if your wifi card is detected).

---

### Post by Bob Appleby on 2010-04-27
(Right click the network icon in the top right panel. You should see "enable networking" and "enable wireless networking" (the latter only if your wifi card is detected).)

The wifi card is not detected. wifi works with Windows on this same machine. Perhaps 10.04 will work. I've tried all sorts of ideas over the last few months to no avail.

Thanks for the information.

Bob

---

### Post by P4man on 2010-04-27
If you read the rest of this thread, you may have noticed its convenient we know what wifi card you have, what laptop, which ubuntu version. Run the commands given higher up and post the results, and maybe we can help. You may even try the suggestion made to run update and detect hardware drivers while plugged in to a wired network (again see above). let us know what happens.

---

### Post by anewguy on 2010-04-27
> **Bob Appleby said:**
> (Right click the network icon in the top right panel. You should see "enable networking" and "enable wireless networking" (the latter only if your wifi card is detected).)

The wifi card is not detected. wifi works with Windows on this same machine. Perhaps 10.04 will work. I've tried all sorts of ideas over the last few months to no avail.

Thanks for the information.

Bob

Since the OP has posted that theirs is working, you need to open your own thread and we can reply there.  As mentioned above, we need all the information first (lspci, lsusb, even lshw -C network) before we can help.  Just to say it doesn't work doesn't do us any good.

So, please do the following:

- open your own thread for this

- that thread include the output from:

lspci

lsusb

lshw -C network

We'll go from there.

Dave ;)

---

