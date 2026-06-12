---
title: "[SOLVED] Wireless won't work on 8.10"
date: 2008-11-02
forum: Networking &amp; Wireless
---

### Post by ewinslow on 2008-11-02
I have a fresh install of 8.10 and it will not hook up to my home wireless network. All other Macintosh devices (iPhone, iBook) are having no problems. I'm using 128 bit WEP security.

Here is the output from syslog when I try to connect:
```

Nov  2 21:54:29 ubuntu NetworkManager: <info>  Activation (eth1) starting connection 'THE NET' 
Nov  2 21:54:29 ubuntu NetworkManager: <info>  (eth1): device state change: 3 -> 4 
Nov  2 21:54:29 ubuntu NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Nov  2 21:54:29 ubuntu NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Nov  2 21:54:29 ubuntu NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Nov  2 21:54:29 ubuntu NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Nov  2 21:54:29 ubuntu NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Nov  2 21:54:29 ubuntu NetworkManager: <info>  (eth1): device state change: 4 -> 5 
Nov  2 21:54:29 ubuntu NetworkManager: <info>  Activation (eth1/wireless): access point 'THE NET' has security, but secrets are required. 
Nov  2 21:54:29 ubuntu NetworkManager: <info>  (eth1): device state change: 5 -> 6 
Nov  2 21:54:29 ubuntu NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Nov  2 21:54:29 ubuntu NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Nov  2 21:54:29 ubuntu NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Nov  2 21:54:29 ubuntu NetworkManager: <info>  (eth1): device state change: 6 -> 4 
Nov  2 21:54:29 ubuntu NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Nov  2 21:54:29 ubuntu NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Nov  2 21:54:29 ubuntu NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Nov  2 21:54:29 ubuntu NetworkManager: <info>  (eth1): device state change: 4 -> 5 
Nov  2 21:54:29 ubuntu NetworkManager: <info>  Activation (eth1/wireless): connection 'THE NET' has security, and secrets exist.  No new secrets needed. 
Nov  2 21:54:29 ubuntu NetworkManager: <info>  Config: added 'ssid' value 'THE NET' 
Nov  2 21:54:29 ubuntu NetworkManager: <info>  Config: added 'scan_ssid' value '1' 
Nov  2 21:54:29 ubuntu NetworkManager: <info>  Config: added 'key_mgmt' value 'NONE' 
Nov  2 21:54:29 ubuntu NetworkManager: <info>  Config: added 'auth_alg' value 'OPEN' 
Nov  2 21:54:29 ubuntu NetworkManager: <info>  Config: added 'wep_key0' value '<omitted>' 
Nov  2 21:54:29 ubuntu NetworkManager: <info>  Config: added 'wep_tx_keyidx' value '0' 
Nov  2 21:54:29 ubuntu NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Nov  2 21:54:29 ubuntu NetworkManager: <info>  Config: set interface ap_scan to 1 
Nov  2 21:54:29 ubuntu NetworkManager: <info>  (eth1): supplicant connection state change: 1 -> 2 
Nov  2 21:54:54 ubuntu NetworkManager: <info>  Activation (eth1/wireless): association took too long, failing activation. 
Nov  2 21:54:54 ubuntu NetworkManager: <info>  (eth1): device state change: 5 -> 9 
Nov  2 21:54:54 ubuntu NetworkManager: <info>  Activation (eth1) failed for access point (THE NET) 
Nov  2 21:54:54 ubuntu NetworkManager: <info>  Marking connection 'THE NET' invalid. 
Nov  2 21:54:54 ubuntu NetworkManager: <info>  Activation (eth1) failed. 
Nov  2 21:54:54 ubuntu NetworkManager: <info>  (eth1): device state change: 9 -> 3 
Nov  2 21:54:54 ubuntu NetworkManager: <info>  (eth1): deactivating device (reason: 0). 
Nov  2 21:54:54 ubuntu NetworkManager: <WARN>  check_one_route(): (eth1) error -34 returned from rtnl_route_del(): Sucess  

```

Here is lspci output:
```

00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 915GM/PM Express PCI Express Root Port (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc M22 [Mobility Radeon X300]
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b3)
03:01.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 08)
03:01.2 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 17)
03:03.0 Network controller: Intel Corporation PRO/Wireless 2915ABG [Calexico2] Network Connection (rev 05)

```

Here is lshw -C network output:
```

  *-network:0
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:12:3f:d6:c9:22
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half latency=64 link=no module=ssb multicast=yes port=twisted pair speed=10MB/s
  *-network:1
       description: Wireless interface
       product: PRO/Wireless 2915ABG [Calexico2] Network Connection
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@0000:03:03.0
       logical name: eth1
       version: 05
       serial: 00:12:f0:83:45:28
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) latency=64 link=no maxlatency=24 mingnt=3 module=ipw2200 multicast=yes wireless=radio off
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: a2:e3:aa:e8:be:1c
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```

And last, but not least is iwconfig output:
```

eth1      radio off  ESSID:off/any  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=off   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```

This is the first version of Ubuntu where I've had any issues at all with wireless. 

I hope a keener eye than mine can notice an anomaly.

Thanks

---

### Post by ewinslow on 2008-11-03
Bump! I just need to see if I can get a pair of eyes on this besides mine.

I hope someone can help.

---

### Post by ewinslow on 2008-11-04
I'm not sure what is going on here, but I do think it has to do with the wireless being turned off when the machine comes up. I believe that's why we see the
```

radio off

```
in the iwconfig output in the 1st post.

On booting this time I hit the function key on the Dell Inspiron 6000 to toggle the wireless and this time it actually associated with the network.

Here's the iwconfig now:
```

eth1      IEEE 802.11g  ESSID:"THE NET"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:12:0E:87:7F:ED   
          Bit Rate:54 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=83/100  Signal level=-47 dBm  Noise level=-91 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:1

```

I toggled this function key yesterday and actually started seeing networks in the Network Manager applet menu, but even then it would not associate with the network.

Tonight it works.

Now, the question is why the wireless is not activated on boot?

---

### Post by Arabiest on 2008-11-04
Friends,

Currently, I am connected thru my office LAN and its ok.

My case is to a certain extent similar to all of those complaining about their Wireless Network...but what is different is that I do see wireless networks despite those shown in the attached image (which are merely dedicated servers for some of my work mate team...database server and not to access internet), I am unable to access them....which means tha RADIO is on all the time.

What is also strange is that I am able to pick up wireless of PC's, Secure modems...etc, but those that FREE (UNSECURE) wireless, I am unable to appear in the NM list....

Could anyone help.

---

### Post by ewinslow on 2008-11-07
> **ewinslow said:**
> 

Now, the question is why the wireless is not activated on boot?

I'm still not sure about the answer to that question, but the machine is now coming up with wireless activated and functioning as advertised. Perhaps the power on state for radio is remembered?

Not sure, but it's working fine now.

---

