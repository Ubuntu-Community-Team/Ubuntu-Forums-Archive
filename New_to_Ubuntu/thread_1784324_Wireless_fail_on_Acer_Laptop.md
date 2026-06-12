---
title: "Wireless fail on Acer Laptop"
date: 2011-06-16
forum: New to Ubuntu
---

### Post by jondolar on 2011-06-16
Hi everybody

Newbie here. My first attempt at any linux distro.

Background: My main computer is a desktop running Win 7 connected to a Linksys wireless router WRT54G2. My second computer is an Acer Aspire 5315 laptop with internal WiFi capability, running Vista and running perfectly wirelessly to connect to the network.  

I installed Ubuntu 11.04 on the Acer from a DVD.The installation went totally smooth. After the installation, I updated all drivers with a wired connection then installed all updates.

After that, I tried to connect wirelessly to my WiFi network. After an apparent success (entering my network password), Any attempt to connect using Firefox failed. Furthermore, the connection keep asking for the network password about every 30 seconds. I tried no manually configure the connection to no avail. I tried the synaptic package manager solution suggested by someone on this forum. No luck. A friend suggested to uninstall 11.04 and go with 10.04.
Before doing that, would anyone have an idea on how to solve that problem?

Sorry for the long post but I wanted to provide as much info as possible.

Tia

Jondolar

---

### Post by jtarin on 2011-06-16
Have you enabled permissions for this device in your router and used the correct security key?

---

### Post by jondolar on 2011-06-16
yes I have
Jondolar

---

### Post by LowSky on 2011-06-16
> **jondolar said:**
> Hi everybody

Newbie here. My first attempt at any linux distro.

Background: My main computer is a desktop running Win 7 connected to a Linksys wireless router WRT54G2. My second computer is an Acer Aspire 5315 laptop with internal WiFi capability, running Vista and running perfectly wirelessly to connect to the network.  

I installed Ubuntu 11.04 on the Acer from a DVD.The installation went totally smooth. After the installation, I updated all drivers with a wired connection then installed all updates.

After that, I tried to connect wirelessly to my WiFi network. After an apparent success (entering my network password), Any attempt to connect using Firefox failed. Furthermore, the connection keep asking for the network password about every 30 seconds. I tried no manually configure the connection to no avail. I tried the synaptic package manager solution suggested by someone on this forum. No luck. A friend suggested to uninstall 11.04 and go with 10.04.
Before doing that, would anyone have an idea on how to solve that problem?

Sorry for the long post but I wanted to provide as much info as possible.

Tia

Jondolar


Hi welcome to the forums. Some Wifi cards run poorly or need aditional drivers, sometimes its just a simple update sometimes its a chore.

First is simple, go to router and unplug it. wait 2-5 minutes and plug it back in. Then try your laptop.

Next we look at the type of wifi connection you use. Do you use WPA2 or WEP. My own experiance WEP doesn't always work, and compared to WPA2  not as secure. Hopefully you do not have a unsecure wireless account, thats even worse.

The next step is to get the netbook on the internet, using a ethernet cable if possible directly connecting to the router. open Update manager and check for updates. then reboot and try wireless internet. If it still fails, keep reading.

The next steps can be tedious.

first open terminal

type or paste this command

```
lspci
``` that's 'LSPCI' in lowercase.

please post the results on this thread and we can then suggest the next line of repair work.

---

### Post by jondolar on 2011-06-17
Here is the lspci dump (not connected by wire)

serge@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (primary) (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (secondary) (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 04)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 04)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 04)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 04)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 04)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 04)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 04)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 04)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f4)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 04)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 04)
05:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
06:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)

Regards

Jondolar

Uninstalled 11.04 and installed 10.04........same problem!

---

