---
title: "Wireless Problems &gt; Installed ndiswrapper &gt; Now wlan0 &quot;Unclaimed&quot;"
date: 2009-08-14
forum: New to Ubuntu
---

### Post by johnnyking on 2009-08-14
Tried to summarise what happened in the title.

There's some sort of incompatibility between my laptop wireless card (Intel 4965AGN), the default Ubuntu driver, and my router (Linksys WAG160N)

At first the laptop would only connect to the router with no security - which I didn't want to stick to.

Then after I setup manual IP's it worked a bit.

So I tried WICD - didn't make a difference.

Installed ndiswrapper. Worked perfectly. Then I rebooted and no there's no wireless option showing and its reported to be 'unclaimed'

Any idea how I go about fixing this?

---

### Post by zerhacke on 2009-08-14
wicd replaces network-manager.  If you install wicd you no longer have network-manager.

You'll need to start the wicd daemon, use wicd to connect to your network, and then sudo apt-get install network-manager to get back to where you were.

---

### Post by johnnyking on 2009-08-14
Ok, so I do understand that much.

However WICD wasn't recognising a wireless driver either.

I've reinstalled network manager - so I'm back to default. However I need to get network manager to recognise the wireless adapter.

I hope that makes it clearer?

---

### Post by mapes12 on 2009-08-14
> **johnnyking said:**
> Ok, so I do understand that much.

However WICD wasn't recognising a wireless driver either.

I've reinstalled network manager - so I'm back to default. However I need to get network manager to recognise the wireless adapter.

I hope that makes it clearer?Doesn't matter if your using Network Manager or WICD, if your wifi adapter is not supported by the Linux kernel then it won't work. As for ndiswrapper I've managed to get it running with some adapters but then the connection always deteriorates to the point of being unusable.

Let's have a closer look at your adapter. Post the output to >Terminal  ```
lspci
```

---

### Post by Firestem4 on 2009-08-14
Your device may not be initiated. Try this

```
sudo ifconfig wlan0 up
```

After that restart networkmanager

```
sudo /etc/init.d/NetworkManager restart
```
(if restart isn't an option do)
```
sudo /etc/init.d/NetworkManager stop
sudo /etc/init.d/NetworkManager start
```

I am not sure what exactly "unclaimed' is referring to but the interface may not be up at all and therefore any utility is not able to find whats attached to it (?unclaimed?)


I prefer to use wicd over NetworkManager for the simple reason that it works; well.

Wicd, if you decide to try it again has two components. the Wicd Daemon (wicd) and wicd-client. (gui-window/tray icon).

to start the wicd daemon from the command line run

```
sudo wicd
```
or
```
sudo /etc/init.d/wicd start
```

you can run the client from your programs menu or command line via:
```
wicd-client
```

---

### Post by johnnyking on 2009-08-15
The results of typing "lspci" are:

```
jk@JK-Laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8400M GS (rev a1)
02:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
08:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)
09:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
09:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
09:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
09:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
09:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)

```

When I tried to type:

```

sudo ifconfig wlan0 up

```

Terminal threw me up this error:

```

wlan0: ERROR while getting interface flags: No such device

```

The command I used that showed my wireless adapter as unclaimed was this

```

sudo lshw -C network; sudo iwlist scanning; cat /etc/network/interfaces; cat /etc/lsb-release; lspci -nn; lsusb; uname -a; dmesg | grep ound; dmesg | grep b43; iwconfig

```

it came from the start of this thread:

[https://answers.launchpad.net/ubuntu/+question/74211](https://answers.launchpad.net/ubuntu/+question/74211)

the first bit of the output showed

```

 *-network UNCLAIMED     
       description: Network controller
       product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 61
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0

```

---

### Post by johnnyking on 2009-08-15
> **mapes12 said:**
> Doesn't matter if your using Network Manager or WICD, if your wifi adapter is not supported by the Linux kernel then it won't work.

Just felt I needed to add that my wifi adapter is indeed supported by the Linux kernal... and was "claimed" - and working to a certain extent when I installed. It's something I've done, inadvertently or not, that has stopped the wifi adapter being recognised.

---

### Post by mapes12 on 2009-08-16
> 02:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)

Try this link where other posts appear to have fixed the problem. Looks like there is a .deb package created to reconfigure your settings to make you wifi work:

[http://ubuntuforums.org/showthread.php?t=695756](http://ubuntuforums.org/showthread.php?t=695756)

And other solutions here: 

[http://www.google.co.uk/#hl=en&q=Intel+Corporation+PRO%2FWireless+4965+AG+ubuntu&meta=&fp=1b311284ac0b25f6](http://www.google.co.uk/#hl=en&q=Intel+Corporation+PRO%2FWireless+4965+AG+ubuntu&meta=&fp=1b311284ac0b25f6)

---

