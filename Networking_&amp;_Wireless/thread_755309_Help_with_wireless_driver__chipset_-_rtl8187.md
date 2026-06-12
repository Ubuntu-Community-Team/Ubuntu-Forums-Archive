---
title: "Help with wireless driver / chipset - rtl8187"
date: 2008-04-14
forum: Networking &amp; Wireless
---

### Post by Siph0n on 2008-04-14
Hey I had some questions about my internal wireless card in my Gateway laptop. I read that the chipset can be determined from lspci:

```
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8038 PCI-E Fast Ethernet Controller (rev 14)
03:09.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
03:09.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
03:09.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)

```

And the modules/drivers in use from lsmod - rtl
rtl8187                35328  0 
mac80211              171016  2 rc80211_simple,rtl8187
eeprom_93cx6            3200  1 rtl8187
usbcore               138632  4 rtl8187,ehci_hcd,uhci_hcd


So I assume that I am using the rtl8187 driver, but I dont see my chipset above. Also, is this the best driver, or should I be using the madwifi or a different driver? Thanks!

Edit:
Shouldn't lshw -C network show me the driver being used also? Here is the output of that:

```

  *-network DISABLED      
       description: Ethernet interface
       product: 88E8038 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 14
       serial: 00:e0:b8:eb:24:30
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.18 firmware=N/A latency=0 module=sky2 multicast=yes
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:c0:a8:eb:55:c1
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.0.108 multicast=yes wireless=IEEE 802.11g

```

---

### Post by dstew on 2008-04-14
Is your wireless working? Is it a USB card?

---

### Post by kevdog on 2008-04-14
Likely its an internal USB connection.  If you list

lsusb -v 

What shows up?

---

### Post by game_plan on 2008-04-15
I have the same wireless card. If lsusb shows something like:
```

Bus 006 Device 002: ID 0bda:8197 Realtek Semiconductor Corp.

```

Then you can use this modified Realtek driver from a previous thread I can't find right now. (There's updates there as well but I have not installed them as there's no release notes) 

[http://www.datanorth.net/~cuervo/blog/2007/09/26/no-more-vista/]("http://www.datanorth.net/~cuervo/blog/2007/09/26/no-more-vista/")

---

### Post by Siph0n on 2008-04-15
You are right! It is an internal usb connected device.... and as to dstew's question, my wireless does work, out of the box actually.... I don't really know about my connectivity issues tho. It seems that my wireless stops working every so often. If I do sudo /etc/init.d/networking restart ,it sometimes helps... other times I need to reboot.... Would using ndiswrapper help, or even the modified driver from [http://www.datanorth.net/~cuervo/blo...no-more-vista/](http://www.datanorth.net/~cuervo/blo...no-more-vista/)  ? I will try it out when I get home from work. Thanks all for the help! :)

---

### Post by kevdog on 2008-04-15
The cuervo device is good only if you have the correct USB id.  If you list lsusb -v it will tell you the id of the device.  This is explained in detail on cuervo's site.  If your id doesn't match, the driver will not help you.  This issue is discussed thoroughly on cuervo's website where the driver is available.  I also think there may be some conflict with this driver and network manager.  Can anyone confirm?  I believe however WICD and manually command line connection work with the driver.

[http://www.datanorth.net/~cuervo/rtl8187b/FAQ.html](http://www.datanorth.net/~cuervo/rtl8187b/FAQ.html)

ndiswrapper is another solution if you find the correct windows driver -- a tall task indeed.  You would have to hunt through the forums to find the correct driver being that this issue has been discussed before.

---

### Post by game_plan on 2008-04-15
The modified driver shows wireless in Network Manager, but some people were complaining about not seeing signal strength in network manager. I cannot confirm this since I have my SSID hidden so it wouldn't show up anyways.

I CAN confirm that you have surprisingly low signal...
```

xxxxx@xxxxxx:~/Desktop/rtl8187b-modified$ iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: xx:xx:xx:xx:xx:xx
                    ESSID:"<hidden>"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:2
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54 
                    Quality:17  Signal level:0  Noise level:38
                    Extra: Last beacon: 249ms ago

```

And its an N router on the same desk not 3 feet away! I would really like a better solution, but haven't found one yet

---

