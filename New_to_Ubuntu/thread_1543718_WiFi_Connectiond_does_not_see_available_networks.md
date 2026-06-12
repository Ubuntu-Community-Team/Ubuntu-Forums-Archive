---
title: "WiFi Connectiond does not see available networks"
date: 2010-08-01
forum: New to Ubuntu
---

### Post by GuildedMason on 2010-08-01
Hi there – Linux newbie here. 
  I have installed Ubuntu 10.4 on my HP Mini 1010NR and it is all working well *apart* from the WiFi connection.
  Apparently this is fairly common. I have found plenty of threads online that discuss this – but I have not been able to fix my issue. 

I have tried to follow instructions from online forums - but got hopelessly lost!

  In essence – it seems like the WiFi connection is not able to view whichever networks are available, so I don’t get the option to connect (it has actually displayed networks a couple of times, it never connected though. Now it is not even showing networks.)
  I don’t have an Ethernet port on this machine – so I can’t connect a network wire to it.
  My WiFi card seems to be a Broadcom BCM4312 (14e4:4315 (rev01))
  From reading other posts … here is the info people tend to ask for …
  ~$ lspci
  00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
  00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
  00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
  00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
  00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
  00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
  00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 02)
  00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
  00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
  00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
  00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
  00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
  00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
  00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
  00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
  01:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
  02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller
   
  ~$ iwconfig
  lo        no wireless extensions.
  eth0      no wireless extensions.
  wlan0     IEEE 802.11bg  ESSID:off/any  
            Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
            Retry  long limit:7   RTS thr:off   Fragment thr:off
            Power Management:off
            
  ~$ lshw -c network
  WARNING: you should run this program as super-user.
    *-network               
         description: Network controller
         product: BCM4312 802.11b/g
         vendor: Broadcom Corporation
         physical id: 0
         bus info: pci@0000:01:00.0
         version: 01
         width: 64 bits
         clock: 33MHz
         capabilities: bus_master cap_list
         configuration: driver=b43-pci-bridge latency=0
         resources: irq:16 memory:feafc000-feafffff
    *-network
         description: Ethernet interface
         product: 88E8040 PCI-E Fast Ethernet Controller
         vendor: Marvell Technology Group Ltd.
         physical id: 0
         bus info: pci@0000:02:00.0
         logical name: eth0
         version: 00
         serial: 00:24:81:58:ad:24
         width: 64 bits
         clock: 33MHz
         capabilities: bus_master cap_list ethernet physical
         configuration: broadcast=yes driver=sky2 driverversion=1.25 firmware=N/A latency=0 multicast=yes
         resources: irq:26 memory:febfc000-febfffff ioport:ec00(size=256)
    *-network
         description: Wireless interface
         physical id: 2
         logical name: wlan0
         serial: 00:23:4d:66:a8:5d
         capabilities: ethernet physical wireless
         configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
   
  I really would appreciate some help in trying to fix this.
  Thanks.

---

### Post by NFblaze on 2010-08-01
Off the bat it looks to me that your wifi card is in "Managed Access Point" mode which I have a hankering isnt the correct mode. Let me consult the manpages or perhaps someone knows offhand how to change it.

Alright try entering:
```
sudo iwconfig wlan0 mode Managed
```

---

### Post by GuildedMason on 2010-08-01
OK tried that command - resulted in ...

Error for wireless request "Set Mode" (8B06) :
      SET failed on device wlan0 ; Device or resource busy.

---

### Post by beew on 2010-08-01
See if this helps.

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx")

---

### Post by GuildedMason on 2010-08-01
After a re-start and re-try ... it seems to be working.

Only that the speeds are REALLY REALLY slow ... ;o(

Thanks for the help with the original problem ... I guess now I need to figure out why it is SO slow!!

---

### Post by beew on 2010-08-01
You may have to wait a bit for the speed to pick up for some reasons I have fixed someone's computer with a broadcom card last week. The only difference is that his is a really old computer and the drivers have to be downloaded manually ("legacy" package) After the drivers were installed it was very slow at reboot. But somehow the speed and connection stregnth picked up in maybe 30 minutes and an hour and after that it connected normally even after reboot.

---

