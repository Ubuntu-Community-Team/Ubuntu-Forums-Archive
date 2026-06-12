---
title: "Wireless firmware missing on a DELL D630 Laptop"
date: 2015-07-15
forum: Networking &amp; Wireless
---

### Post by dan182 on 2015-07-15
Hi !

First, I would like to said many thanks to all members of the forum. I only made my inscription today, but I use ubuntu since 1 year and your forum helps me several times. So, thank you to all the passionates. Perdon my english too, which is my third tongue. 

I use Xunbuntu 12.04 with a Live USB "I choose 'Try xuntubu without installing'. But I'm completely stuck with a Dell D630 computer where there is not HDD, where I must not connect an ethenet connexion. I never have this problem with others laptop. 

So, I worked on a problem during 30 hours the last few days but with no solution. Always a thing who doesn't work. I try to follow many tutorials several times because I know that I'm not the first who have this probelm (like [HTML]http://ubuntuforums.org/showthread.php?t=2077104[/HTML] or [HTML]https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx?action=show&redirect=BroadcomSTA%28Wireless%29[/HTML]). I tried also to install bcmwl-kernel-source_6.30.223.248+bdcom-0ubuntu0.1_amd64, dkms, wl_apsta-3.130.20.0....

I also connected a TP-Link USB Wifi 725, but this is not working too.  Also, Networking and Wireless are enabled, and it marks "Wireless  Networkds device not ready". Also, I try to install additionnal drivers with the Xubuntu window "Broadcom STA wireless driver", but I click on activate, It crash definitely my USB live ! That makes more than one week that I try,  and it's very annoying, because I'm for much weeks in a foreign country with no ethernet connection. 

My main Bios section:

> Onboard devices :
 Integrated NIC : Enabled w/PXR
 Internal modem : Enabled
 External USB Ports : Enabled
 Parallel port : ECP
 Serial port : COM
 PC Card and 1394 : Enabled
 SATA Operation : ATA
 Module bay device : Enabled
 Flash cache module : Off
 ASF Mode : Off
 

 Wireless :
 Internal Bluetooth : Enabled
 Internal Wi-fi : Enabled
 Internal cellular : Enabled
Wireless switch : All
 Wi-fi catcher : Enabled
LAN/Wi-fi auto switch : Off



This is the information that I got from  lspci -vvnn | grep -A 9 Network:
 
```

Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
    Subsystem: Dell Wireless 1390 WLAN Mini-Card [1028:0007]
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 17
    Region 0: Memory at f6cfc000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: b43-pci-bridge
    Kernel modules: ssb
```

Rf-kill list:

```
0: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
```

And iwconfig:

```
lo        no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
   
eth0      no wireless extensions.

``` 

And to eliminate all previous change, I'm using a new Live USB key. 

Thanks a lot,

Dan.

---

### Post by PaulW2U on 2015-07-15
*Thread moved to **Networking & Wireless**.* at dan182's request

---

### Post by dan182 on 2015-07-15
Thanks for the move :)

---

### Post by praseodym on 2015-07-15
Hi,

this device need another firmware which is not present anymore in "linux-firmware-nonfree":
```

sudo apt-get remove --purge bcmwl-kernel-source
```

Download this file and save it in "Downloads":

[http://media.cdn.ubuntu-de.org/forum/attachments/04/32/2480236-Broadcom_Firmware.tar.gz](http://media.cdn.ubuntu-de.org/forum/attachments/04/32/2480236-Broadcom_Firmware.tar.gz) 

Installation

```
cd ~/Downloads/
sudo tar xvf 2480236-Broadcom_Firmware.tar.gz -C /lib/firmware/ 
```

Reboot.

---

### Post by dan182 on 2015-07-16
> **praseodym said:**
> Hi,

this device need another firmware which is not present anymore in "linux-firmware-nonfree":
```

sudo apt-get remove --purge bcmwl-kernel-source
```

Download this file and save it in "Downloads":

[http://media.cdn.ubuntu-de.org/forum/attachments/04/32/2480236-Broadcom_Firmware.tar.gz](http://media.cdn.ubuntu-de.org/forum/attachments/04/32/2480236-Broadcom_Firmware.tar.gz) 

Installation

```
cd ~/Downloads/
sudo tar xvf 2480236-Broadcom_Firmware.tar.gz -C /lib/firmware/ 
```

Reboot.

Wow, Man, that's work perfectly ! You are really a life saver ! Many many thanks, problem solved. 
Wow

---

### Post by aaronLund on 2015-09-22
Worked for me too. 

Many thanks.

---

