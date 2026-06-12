---
title: "Intel Ultimate N WiFi 5300 wireless not working in Lubuntu 1404"
date: 2014-05-08
forum: Networking &amp; Wireless
---

### Post by jtreubig on 2014-05-08
I had Lubuntu 1310 installed on my system with the Intel WiFi 5300 working fine and decided to upgrade to 1404.  I installed 1404 from scratch and get no wireless connections available.   Doesn't even pop up the normal dialog at boot indicating it is attempting to find them, nor is the tray icon for network available.

Here's what I've seen so far:

lspci shows:0c:00.0 Network controller: Intel Corporation Ultimate N WiFi Link 5300

dmesg grep for iwlwifi shows:

[  110.677286] iwlwifi 0000:0c:00.0: can't disable ASPM; OS doesn't have ASPM control
[  110.677344] iwlwifi 0000:0c:00.0: irq 49 for MSI/MSI-X
[  114.132723] iwlwifi 0000:0c:00.0: loaded firmware version 8.83.5.1 build 33692 op_mode iwldvm
[  122.079067] iwlwifi 0000:0c:00.0: CONFIG_IWLWIFI_DEBUG disabled
[  122.079071] iwlwifi 0000:0c:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[  122.079073] iwlwifi 0000:0c:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[  122.079075] iwlwifi 0000:0c:00.0: Detected Intel(R) Ultimate N WiFi Link 5300 AGN, REV=0x24
[  122.079149] iwlwifi 0000:0c:00.0: L1 Enabled; Disabling L0S
[  138.418233] iwlwifi 0000:0c:00.0: L1 Enabled; Disabling L0S
[  138.418652] iwlwifi 0000:0c:00.0: Radio type=0x0-0x2-0x0
[  138.555403] iwlwifi 0000:0c:00.0: L1 Enabled; Disabling L0S
[  138.555843] iwlwifi 0000:0c:00.0: Radio type=0x0-0x2-0x0

iwconfig shows:

wlan0     IEEE 802.11abgn  ESSID off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr: off   Fragment thr: off
          Power Management: off



Strangely enough the WIFI LED on the laptop is on continuously and the side switch is in the on position.  I've verified the hardware is fine in that I can boot from my 1310 install CD and the WIFI comes up and finds access points with no changes to the laptop settings.  Any suggestions would be much appreciated.

---

### Post by jtreubig on 2014-05-09
A little more information: System is a Dell E6400.

From lshw -C network
>   *-network       description: Ethernet interface
       product: 82567LM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 03
       serial: 00:24:e8:99:be:85
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list ethernet physical
       configuration: broadcast=yes driver=e1000e latency=0 multicast=yes
       resources: irq:22 memory:f6fe0000-f6ffffff memory:f6fdb000-f6fdbfff ioport:efe0(size=32)
  *-network
       description: Wireless interface
       product: Ultimate N WiFi Link 5300
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: wlan0
       version: 00
       serial: 00:21:6a:7c:c1:8c
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.13.0-24-generic firmware=8.83.5.1 build 33692 latency=0 link=no multicast=yes wireless=IEEE 802.11abgn
       resources: irq:49 memory:f1ffe000-f1ffffff
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: wwan0
       serial: 02:80:37:ec:02:00
       capabilities: ethernet physical
       configuration: broadcast=yes driver=cdc_ether driverversion=22-Aug-2005 firmware=Mobile Broadband Network Device link=no multicast=yes


nm-tool output
> 
NetworkManager Tool

State: disconnected

- Device: ttyACM1 --------------------------------------------------------------
  Type:              Mobile Broadband (GSM)
  Driver:            cdc_acm, cdc_ether, cdc_wdm
  State:             disconnected
  Default:           no

Capabilities:

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             disconnected
  Default:           no
  HW Address:        00:21:6A:7C:C1:8C

Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    linksys:         Infra, 00:18:F8:76:01:09, Freq 2437 MHz, Rate 54 Mb/s, Strength 29 WPA
    NETGEAR39:       Infra, 44:94:FC:77:C6:B8, Freq 2437 MHz, Rate 54 Mb/s, Strength 24 WPA2
    belkin.34e:      Infra, 08:86:3B:60:03:4E, Freq 2417 MHz, Rate 54 Mb/s, Strength 12 WPA WPA2

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            e1000e
  State:             unavailable
  Default:           no
  HW Address:        00:24:E8:99:BE:85

Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


---

