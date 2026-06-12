---
title: "Atheros AR9485 - Can't acces any page"
date: 2014-03-07
forum: Networking &amp; Wireless
---

### Post by adrian22 on 2014-03-07
Hello.

I have some problems with wi-fi connection . 

All look ok ,i can access the router ;connection is ok; but i can't access any page. 

I tried Fedora 20 and all was working good. 
May be a problem with kernel, i don't know... Fedora use 3.12 kernel and Ubuntu 3.11. I see many topics about Atheros wi-fi drivers , but no one worked for me .

Or may be a problem with my router configuration...
So all is working fine and never had problems with Windows 7 and other Android devices.I got problems only with Ubuntu. 


PC: Acer Aspire 5733

Wi-fi router : Serioux SRX WR 150 A1

Wi-fi: Atheros AR9485

OS: Ubuntu 13.10

Wi-fi Network mode : 11b/g/n Mixed Mode 

Security mode is: Disable

MAC Access Control is : Disable ( i am not sure what this is ,was by default)



Network controller [0280]: Qualcomm Atheros AR9485 Wireless Network Adapter [168c:0032] (rev 01)




**iwconfig wlan0 :**

    wlan0     IEEE 802.11bgn  ESSID:"Baza"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 48:02:2A:63:2C:18   
          Bit Rate=1 Mb/s   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-27 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


**Lspci** :

        00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
    00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
    00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
    00:1a.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
    00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
    00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
    00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
    00:1d.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
    00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
    00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
    00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
    00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
    00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
    01:00.0 Ethernet controller: Broadcom Corporation NetLink BCM57780 Gigabit Ethernet PCIe (rev 01)
    02:00.0 Network controller: Qualcomm Atheros AR9485 Wireless Network Adapter (rev 01)
    ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
    ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
    ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
    ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
    ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
    ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)



**rfkill list all**

   

     0: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: no
    1: acer-wireless: Wireless LAN
        Soft blocked: no
        Hard blocked: no

---

### Post by varunendra on 2014-03-08
Hello adrian22!

Please use 'Code' tags to post command outputs. It preserves the characters and formatting thus making it more readable. Please follow the "Using Code Tags" link in my signature below to see how to do it.

As for the wireless issue, please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates. It will give us some extra info that may be helpful in solving the problem.

Along with the report, please also post the output of -
```
grep [[:alnum:]] /sys/module/ath*/parameters/*
```

---

