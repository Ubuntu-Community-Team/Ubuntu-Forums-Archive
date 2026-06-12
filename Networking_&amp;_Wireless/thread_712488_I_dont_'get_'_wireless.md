---
title: "I dont 'get ' wireless"
date: 2008-03-01
forum: Networking &amp; Wireless
---

### Post by johnbl on 2008-03-01
I have a Netgear WGR614 setup.
iwconfig retunrs;
 IEEE 802.11g  ESSID:"interserve"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:1B:2F:5F:63:26   
          Bit Rate:54 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=52/100  Signal level=-42 dBm  Noise level=-84 dBm
          Rx invalid nwid:0  Rx invalid crypt:2  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:33

wireless connection crawls and is unusable. But I keep reading about how great wireless is ... So It's this notebook OR..!

Am I correct in reading the above that;
Link Quality 52 / 100 means very bad
That
Noise Level 84dBm isn't good..
Signal level 42 dBm = useless!

Am using Wicd as the manager for connections and where everything else failed completely, it does at least work and set itself up pretty well.

Any light that can be thrown on this mess would be most appreciated.

John

---

### Post by wieman01 on 2008-03-01
How close are you to the router?

Second, you might want to change the frequency i.e. wireless channel. There might be interference with other networks around you. So choose a channel (router setting) that is not used by any other network. Please try and let us know how you go.

Also post:
> sudo iwlist scan

---

### Post by johnbl on 2008-03-05
Thanks for that suggestion. Have tried all 13 channels with the following result - 
Noise seems to remain constant, Link Q varies considerably but not signal...

Any other suggestions as to what other bits I could check for there must be something else getting in the ' way ' of a useable signal as none of these channel settings can cut it..
I KNOW that if this result was the the norm for Wireless, there would be no wireless! 

Help! <g>

John
```
Region : Australia

Channel: 1
eth1      IEEE 802.11g  ESSID:"stuartpark"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:1C:2F:5F:63:26   
          Bit Rate:54 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=42/100  Signal level=-37 dBm  Noise level=-83 dBm
          Rx invalid nwid:0  Rx invalid crypt:6  Rx invalid frag:0
          Tx excessive retries:1  Invalid misc:0   Missed beacon:35

Channel: 2
eth1      IEEE 802.11g  ESSID:"stuartpark"  
          Mode:Managed  Frequency:2.427 GHz  Access Point: 00:1C:2F:5F:63:26   
          Bit Rate:54 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=73/100  Signal level=-41 dBm  Noise level=-81 dBm
          Rx invalid nwid:0  Rx invalid crypt:3  Rx invalid frag:0
          Tx excessive retries:1  Invalid misc:0   Missed beacon:31


Channel: 3
eth1      IEEE 802.11g  ESSID:"stuartpark"  
          Mode:Managed  Frequency:2.417 GHz  Access Point: 00:1C:2F:5F:63:26   
          Bit Rate:54 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=73/100  Signal level=-42 dBm  Noise level=-83 dBm
          Rx invalid nwid:0  Rx invalid crypt:1  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:25

Channel: 4
eth1      IEEE 802.11g  ESSID:"stuartpark"  
          Mode:Managed  Frequency:2.432 GHz  Access Point: 00:1C:2F:5F:63:26   
          Bit Rate:54 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=73/100  Signal level=-38 dBm  Noise level=-81 dBm
          Rx invalid nwid:0  Rx invalid crypt:4  Rx invalid frag:0
          Tx excessive retries:1  Invalid misc:0   Missed beacon:29

Channel: 5
eth1      IEEE 802.11g  ESSID:"stuartpark"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:1C:2F:5F:63:26   
          Bit Rate:54 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=68/100  Signal level=-38 dBm  Noise level=-83 dBm
          Rx invalid nwid:0  Rx invalid crypt:5  Rx invalid frag:0
          Tx excessive retries:1  Invalid misc:0   Missed beacon:27

Channel: 6
eth1      IEEE 802.11g  ESSID:"stuartpark"  
          Mode:Managed  Frequency:2.442 GHz  Access Point: 00:1C:2F:5F:63:26   
          Bit Rate:54 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=78/100  Signal level=-33 dBm  Noise level=-81 dBm
          Rx invalid nwid:0  Rx invalid crypt:7  Rx invalid frag:0
          Tx excessive retries:1  Invalid misc:0   Missed beacon:33

Channel: 7
eth1      IEEE 802.11g  ESSID:"stuartpark"  
          Mode:Managed  Frequency:2.447 GHz  Access Point: 00:1C:2F:5F:63:26   
          Bit Rate:54 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=63/100  Signal level=-31 dBm  Noise level=-82 dBm
          Rx invalid nwid:0  Rx invalid crypt:8  Rx invalid frag:0
          Tx excessive retries:1  Invalid misc:0   Missed beacon:32

Channel: 8
eth1      IEEE 802.11g  ESSID:"stuartpark"  
          Mode:Managed  Frequency:2.452 GHz  Access Point: 00:1C:2F:5F:63:26   
          Bit Rate:54 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=84/100  Signal level=-31 dBm  Noise level=-82 dBm
          Rx invalid nwid:0  Rx invalid crypt:9  Rx invalid frag:0
          Tx excessive retries:1  Invalid misc:0   Missed beacon:28

Channel: 9
eth1      IEEE 802.11g  ESSID:"stuartpark"  
          Mode:Managed  Frequency:2.457 GHz  Access Point: 00:1C:2F:5F:63:26   
          Bit Rate:54 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=68/100  Signal level=-37 dBm  Noise level=-83 dBm
          Rx invalid nwid:0  Rx invalid crypt:10  Rx invalid frag:0
          Tx excessive retries:1  Invalid misc:0   Missed beacon:28

Channel: 10
eth1      IEEE 802.11g  ESSID:"stuartpark"  
          Mode:Managed  Frequency:2.467 GHz  Access Point: 00:1C:2F:5F:63:26   
          Bit Rate:54 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=68/100  Signal level=-30 dBm  Noise level=-84 dBm
          Rx invalid nwid:0  Rx invalid crypt:11  Rx invalid frag:0
          Tx excessive retries:1  Invalid misc:0   Missed beacon:35

Channel: 12
eth1      IEEE 802.11g  ESSID:"stuartpark"  
          Mode:Managed  Frequency:2.472 GHz  Access Point: 00:1C:2F:5F:63:26   
          Bit Rate:54 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=89/100  Signal level=-33 dBm  Noise level=-84 dBm
          Rx invalid nwid:0  Rx invalid crypt:13  Rx invalid frag:0
          Tx excessive retries:1  Invalid misc:0   Missed beacon:25

Channel: 13
eth1      IEEE 802.11g  ESSID:"stuartpark"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:1C:2F:5F:63:26   
          Bit Rate:54 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=73/100  Signal level=-34 dBm  Noise level=-85 dBm
          Rx invalid nwid:0  Rx invalid crypt:14  Rx invalid frag:0
          Tx excessive retries:1  Invalid misc:1   Missed beacon:32
```

---

### Post by wieman01 on 2008-03-05
The scan looks really odd. I think there is an issue with your wireless driver. What wireless adapter have you got & what chipset does it use (in case you know).#

Please also post:
> sudo lshw -C network
Strange...

---

### Post by johnbl on 2008-03-05
Thanks for the help with this, strange is it ...
AS requested

John

```
 sudo lshw -C network
  *-network:0             
       description: Wireless interface
       product: PRO/Wireless 2200BG Network Connection
       vendor: Intel Corporation
       physical id: 7
       bus info: pci@0000:01:07.0
       logical name: eth1
       version: 05
       serial: 00:12:f0:b8:fd:3e
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.0kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) ip=10.0.0.3 latency=64 link=yes maxlatency=24 mingnt=3 module=ipw2200 multicast=yes wireless=IEEE 802.11g
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: c
       bus info: pci@0000:01:0c.0
       logical name: eth0
       version: 10
       serial: 00:03:0d:28:4b:2d
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full latency=64 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s

```

---

### Post by wieman01 on 2008-03-05
It's a IPW2200BG, good news. The device is well supported at least (I also have on).

Now let's not used WICD for a minute, perhaps even remove it, does Network Manager do a better job perhaps? Have you tried it?

How far are you away from the router in question?

---

### Post by imdano on 2008-03-05
I don't think the output in his second post was from "iwlist scan", it looked like a bunch of iwconfig outputs for his AP on a bunch of different channels.  Since it seems like his problem is that his internet is slow (not dropping), I'd be surprised if a switch in network management app made much of a difference, as both are utitlizing the same tools to make connections.  There's no harm in giving NM a try, though.

---

### Post by wieman01 on 2008-03-05
Imdano, 

Yes, you are right. Basically. But there is definitely a difference between manual connections (through command line) and NM for instance, as NM handles connection drop-outs much better so that users won't even notice sometimes. Manual connections quietly drop and you'll have to restart the network yourself. 

You are also right concerning the scan:
> sudo iwlist scan

---

### Post by johnbl on 2008-03-05
> **wieman01 said:**
> It's a IPW2200BG, good news. The device is well supported at least (I also have on).

Now let's not used WICD for a minute, perhaps even remove it, does Network Manager do a better job perhaps? Have you tried it?

How far are you away from the router in question?
Thanks,
On a point basis;

Under Network manager I couldn't get anything from the router! Hence wicd that at least gets that far.

The router is currently maybe a short 2 meters away from the notebook. Reading the  ' people 300 meters away being able to access your router ' in the manual.. Yeah right! <VBG>

In testing the channels I had it disconnect from the internet, just the router talking to the notebook. Wired connection not via the router to the actual ADSL modem speed isn't a problem at all.

John

---

### Post by wieman01 on 2008-03-05
Could you do another scan for us and post the results please:
> sudo iwlist scan
Just to see how strong the signal actually is.

---

### Post by johnbl on 2008-03-06
```
sudo iwlist scan
[sudo] password for john:
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:1B:2F:5F:63:26
                    ESSID:"interserve"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 9 Mb/s; 11 Mb/s
                              6 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=95/100  Signal level=-32 dBm  
                    IE: WPA Version 1
                        Group Cipher : WEP-40
                        Pairwise Ciphers (2) : WEP-40 TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : WEP-40
                        Pairwise Ciphers (2) : WEP-40 TKIP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    Extra: Last beacon: 96ms ago

```

---

### Post by roshm on 2008-03-06
I'm trying to get my system working to, and am still very much a newbie.  But I think "Rx invalid nwid " = receive invalid network identification

---

### Post by wieman01 on 2008-03-06
**@johnbl:**

I must say I don't know what's going on. Last thing we could try is to disable wireless B. Only run wireless G and see if it gets any better. Sorry I have not got any smarter idea at the moment...

---

### Post by johnbl on 2008-03-08
Have been digging around some more, wondering about drivers; dmesg |grep ipw

SEEMS to suggest that ipw is running into an error...

HOWEVER RealTec site states that the updated drivers [ 2007 eara ] are built into the linux kernel.

The error does show up in google, mostly pointing here to Ubuntu forums, however as I read it its an old bug from V6#, which would both figure from Realtex and the kernel fix given the time span.

Any ideas how to definatively id just what is happening with the Realtex chip - 
sudo ispci - v ```
01:07.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)
        Subsystem: Intel Corporation Unknown device 2702
        Flags: bus master, medium devsel, latency 64, IRQ 5
        Memory at ffbff000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [dc] Power Management version 2

```suggests to me some control can be exerted but no idea where or how access is gained to vary PowerManagement or see what else might be available.


```
[   23.224000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.0kmprq
[   23.224000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   23.248000] uvcvideo: Found UVC 1.00 device <unnamed> (046d:0991)
[   23.276000] usbcore: registered new interface driver uvcvideo
[   23.276000] USB Video Class driver (v0.1.0)
[   23.332000] psmouse.c: Failed to reset mouse on isa0060/serio3
[   23.372000] Yenta: ISA IRQ mask 0x00d0, PCI irq 3
[   23.372000] Socket status: 30000006
[   23.372000] Yenta: Raising subordinate bus# of parent bus (#01) from #01 to #05
[   23.372000] pcmcia: parent PCI bridge I/O window: 0xc000 - 0xcfff
[   23.372000] cs: IO port probe 0xc000-0xcfff: clean.
[   23.372000] pcmcia: parent PCI bridge Memory window: 0xffb00000 - 0xffbfffff
[   23.372000] pcmcia: parent PCI bridge Memory window: 0x40000000 - 0x43ffffff
[   23.372000] ACPI: PCI Interrupt 0000:01:07.0[A] -> Link [LNKD] -> GSI 5 (level, low) -> IRQ 5
[   23.372000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   23.496000] ipw2200: Detected geography ZZR (14 802.11bg channels, 0 802.11a channels)
[   23.560000] ACPI: PCI Interrupt 0000:00:1f.5[B] -> Link [LNKB] -> GSI 3 (level, low) -> IRQ 3




[168.024000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  170.828000] NET: Registered protocol family 17
[  178.172000] eth1: no IPv6 routers present
[  178.632000] eth0: no IPv6 routers present
[  673.484000] ipw2200: Firmware error detected.  Restarting.
[  689.876000] ipw2200: Firmware error detected.  Restarting.
[  697.232000] ipw2200: Firmware error detected.  Restarting.
[  711.768000] ipw2200: Firmware error detected.  Restarting.
[  759.800000] ipw2200: Firmware error detected.  Restarting.

```

It's clear I think the problem is in this damb notebook but given it runs AOK on everything else I'm not tripping over myself to bin it....

Johnbl

---

### Post by johnbl on 2008-03-09
Well guys and galls, either;
some one liked my ' bin it ' line and managed to access the system and really do a number on the hardware
OR
The computer felt threatened and committed suicide ..

cause it's now completely dead.

Pity was a nice little thing really ...

---

### Post by wieman01 on 2008-03-10
Perhaps it was a hardware issue after all. I cannot explain what happened but trying another piece of hardware is the only option that is left for now.

Sorry to hear this.

---

### Post by johnbl on 2008-03-10
I figure it is just the power supply. Looking around for a parts source but.. I saved $s by getting a w/sale non name brand and I think I'm now about to find out about that particular money saving option! Still I suppose 3 years for a notebook is about it anyway. Mind you it HAS had a full mother board replacement and in stripping it I find that most of the screws were left out. Including one of the HDD anchors. Might be a case of salvaging bits for later and leaving the rest to rot! 

Did have the opportunity to pull the wireless card though, had a sneaking that it might not have been connected to an antenna loop in the case given the crap performance - not the case though so I can cancel out that possible flaw in the setup..

So, anyone know of an external HDD drive housing for notebook sized drives.. [ Seagate Momentus 4200 2  80GB ]!

Johnbl

---

