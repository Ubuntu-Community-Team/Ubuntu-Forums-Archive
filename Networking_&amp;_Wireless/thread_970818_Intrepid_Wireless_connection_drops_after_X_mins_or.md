---
title: "Intrepid: Wireless connection drops after X mins or Y no. of bytes?"
date: 2008-11-04
forum: Networking &amp; Wireless
---

### Post by bovine on 2008-11-04
Recently upgraded to Intrepid.
I'm having a problem whereby my wireless connection drops after what seems like a regular number of minutes or number of received bytes.

For example, if I try and download Eclipse JEE which is 162MB .tar.gz file it will get to approx ~40%-50% and the connection drops.

I can find no messages in the output from dmesg which would confirm a firmware problem or anything to do with ipw2200.

The following is a snippet from my daemon.log:

```

Nov  4 18:17:52 atlantis NetworkManager: <info>  (eth1): supplicant connection state change: 7 -> 0 
Nov  4 18:17:52 atlantis NetworkManager: <info>  (eth1): supplicant connection state change: 0 -> 2 
Nov  4 18:18:07 atlantis NetworkManager: <info>  (eth1): device state change: 8 -> 3 
Nov  4 18:18:07 atlantis NetworkManager: <info>  (eth1): deactivating device (reason: 11). 
Nov  4 18:18:07 atlantis NetworkManager: <info>  eth1: canceled DHCP transaction, dhcp client pid 14673 
Nov  4 18:18:07 atlantis NetworkManager: <WARN>  check_one_route(): (eth1) error -34 returned from rtnl_route_del(): Sucess  
Nov  4 18:18:07 atlantis avahi-daemon[4699]: Withdrawing address record for 10.82.60.81 on eth1.
Nov  4 18:18:07 atlantis avahi-daemon[4699]: Leaving mDNS multicast group on interface eth1.IPv4 with address 10.82.60.81.
Nov  4 18:18:07 atlantis avahi-daemon[4699]: Interface eth1.IPv4 no longer relevant for mDNS.

```

Not sure what this is telling me. 

Can anyone shed some light on the issue, point me to another thread or launchpad bug?

Some extra info: my router is set WPA2-PSK, Hidden SSID and Wireless Mode G only. Could it be the router dropping the connection?

Cheers

Joe


------ Output from lshw -C network ------------
```

  *-network:0             
       description: Wireless interface
       product: PRO/Wireless 2200BG [Calexico2] Network Connection
       vendor: Intel Corporation
       physical id: 4
       bus info: pci@0000:06:04.0
       logical name: eth1
       version: 05
       serial: 00:12:f0:6e:83:73
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) ip=10.82.60.81 latency=32 maxlatency=24 mingnt=3 module=ipw2200 multicast=yes wireless=IEEE 802.11g

```

---

### Post by NIT006.5 on 2008-11-04
I've had a very similar issue since upgrading, but in my case it's dropping the wireless connection after less than a minute. Restarting the interface brings it back, only to drop again less than a minute later. Although it's a bit too late for me to find a fix now, since I got so frustrated (after several hours and a REALLY bad day) that I pulled out the USB wireless adapter and threw it against the wall. Perhaps if I can get all the pieces to fit together again I could just wrap it with cellotape and hope for the best :)

---

### Post by mike310z on 2008-11-04
I think I have the same problem.

I had an old linksys wwp54g wireless card working perfectly in Ibex and the alphas etc for some time.

Yesterday I installed a shiny new linksys wwp300n wireless-N card that now uses the 'Broadcom STA' driver over the older propriety driver for my previous card. 

My connection now drops at repeatable intervals, it could be related to received bytes, I have not determined that yet, its about an hour by gut feel at this point, but it is pretty much every hour after a reboot.

---

### Post by mehrdadm on 2008-11-26
I have the same problem with my Dell inspiron 6400, wireless card :(

is there any help?!?

lspci output:
```
0b:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
```

lshw -C network output:
  ```
*-network                                                                                                                                                                         
       description: Network controller                                                                                                                                              
       product: BCM4311 802.11b/g WLAN                                                                                                                                              
       vendor: Broadcom Corporation                                                                                                                                                 
       physical id: 0                                                                                                                                                               
       bus info: pci@0000:0b:00.0                                                                                                                                                   
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:15:c5:b4:01:7e
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.1.2 latency=64 link=yes module=ssb multicast=yes port=twisted pair speed=100MB/s
  *-network:0
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:18:f3:93:1e:b6
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 1a:d6:b3:4a:bf:ab
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
```

---

### Post by dartmusic on 2008-11-26
It seems that this problem is not specific to adapter or chipset maker, but pretty prevalent nonetheless.  I've been having the same problem since installing Intrepid.  It's very curious that there are so many people having this issue but no info from Canonical or users who may have found a fix.  

In my situation I either have to disable/enable wireless up to 20x a day or (like last night) it will work for hours without any issue.  

This seems like a pretty large issue; it would be helpful to hear some sort of feedback.

---

### Post by CholericKoala on 2008-11-26
My lappy had that problem with kubuntu 8.10

---

### Post by Sneachtuil on 2008-11-27
I am also having the same problem with ipw2200.  The only "fix", for me, is to restart.

I have been posting in this bug report here about it:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/229611](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/229611)

It seems it also affects ipw3945BG.

If you could, please do/post the following in this bug report:

1.  Ensure you have updated to the latest kernel and you are running Ubuntu 8.10 (or another flavor, like Kubuntu)

2.  Please be sure to attach each file as a separate attachment:

* cat /proc/version_signature > version.log
* dmesg > dmesg.log
* sudo lspci -vvnn > lspci-vvnn.log

3.  Check your dmesg.log file and see if something comes up saying "IRQ ###:  Nobody cared."  If it does, turning on irqpolling may prevent issues (in my case, they slow down the issues occurring, but also significantly decrease performance on my computer).  To do this, you'll have to edit your GRUB boot options either in the main config file or as you boot up - just google "turn on irqpoll" and you'll find loads of instructions for it.

4.  Assuming you still see issues with wifi after booting with the "irqpoll" option, or if it doesn't seem like you need to, please also then try installing the linux-backports-modules-intrepid package (you'll need to reboot after installing) as it contains and updated version of the compat-wireless stack.

5.  After completing steps 1-4, post results again.

Also note that new bug reports may or may not have to be filed depending on what happens.  Leann Ogasawara has already said as much inside the bug report.  Please continue to use this thread on the forums to monitor updates, though.  Hopefully we can get this issue resolved soon, as its very annoying for a college student such as myself.  =)

---

### Post by tiger12506 on 2009-02-03
I am having the same problem with a HP Compaq 8510w.
The wireless worked beautifully with Hardy, but fails miserably, disconnecting every minute or so with Intrepid.

```
[14130.756195] wlan0: disassociating by local choice (reason=3)
[14134.410989] wlan0: associate with AP 00:15:e8:e4:2c:83
[14134.423884] wlan0: authenticate with AP 00:15:e8:e4:4e:42
[14134.429542] wlan0: authenticate with AP 00:15:e8:e4:4e:42
[14134.429568] wlan0: authenticated
[14134.429575] wlan0: associate with AP 00:15:e8:e4:4e:42
[14134.436779] wlan0: authenticate with AP 00:15:e8:e4:4e:42
[14134.436813] wlan0: authenticated
[14134.436820] wlan0: associate with AP 00:15:e8:e4:4e:42
[14134.440511] wlan0: authenticate with AP 00:15:e8:e4:4e:42
[14134.440538] wlan0: authenticated
[14134.440546] wlan0: associate with AP 00:15:e8:e4:4e:42
[14134.454848] wlan0: RX ReassocResp from 00:15:e8:e4:4e:42 (capab=0x411 status=0 aid=2)
[14134.454860] wlan0: associated
[14144.465222] wlan0: disassociating by local choice (reason=3)
[14147.954205] wlan0: associate with AP 00:15:e8:e4:4e:42
[14147.968246] wlan0: authenticate with AP 00:15:e8:e5:f4:43
[14147.970309] wlan0: authenticate with AP 00:15:e8:e5:f4:43
[14147.972799] wlan0: authenticate with AP 00:15:e8:e5:f4:43
[14148.168140] wlan0: authenticate with AP 00:15:e8:e5:f4:43
[14148.169083] wlan0: authenticated
[14148.169095] wlan0: associate with AP 00:15:e8:e5:f4:43
[14148.187100] wlan0: RX ReassocResp from 00:15:e8:e5:f4:43 (capab=0x411 status=0 aid=1)
[14148.187112] wlan0: associated
[14151.926983] wlan0: disassociating by local choice (reason=3)
[14155.205554] wlan0: authenticate with AP 00:15:e8:e4:4e:43
[14155.207622] wlan0: authenticate with AP 00:15:e8:e4:4e:43
[14155.209808] wlan0: authenticate with AP 00:15:e8:e4:4e:43
[14155.408094] wlan0: authenticate with AP 00:15:e8:e4:4e:43
[14155.410264] wlan0: authenticated
[14155.410278] wlan0: associate with AP 00:15:e8:e4:4e:43
[14155.430671] wlan0: RX AssocResp from 00:15:e8:e4:4e:43 (capab=0x411 status=0 aid=1)
[14155.430681] wlan0: associated
[14170.137079]  CIFS VFS: Unexpected lookup error -112
[14180.136067]  CIFS VFS: Unexpected lookup error -112
[14190.137318]  CIFS VFS: Unexpected lookup error -112
[14200.136096]  CIFS VFS: Unexpected lookup error -112
[14210.136076]  CIFS VFS: Unexpected lookup error -112
[14211.464964] wlan0: authenticate with AP 00:15:e8:e5:f4:42
[14211.467010] wlan0: authenticated
[14211.467025] wlan0: associate with AP 00:15:e8:e5:f4:42
[14211.483221] wlan0: RX ReassocResp from 00:15:e8:e5:f4:42 (capab=0x411 status=0 aid=1)
[14211.483232] wlan0: associated
[14220.136092]  CIFS VFS: Unexpected lookup error -112
[14230.136094]  CIFS VFS: Unexpected lookup error -112
[14240.136067]  CIFS VFS: Unexpected lookup error -112
[14274.408893] mac80211-phy0: failed to remove key (0, 00:15:e8:e4:4e:43) from hardware (-22)
[14274.410995] wlan0: authenticate with AP 00:15:e8:e4:4e:43
[14274.608114] wlan0: authenticate with AP 00:15:e8:e4:4e:43
[14274.608821] wlan0: authenticated
[14274.608829] wlan0: associate with AP 00:15:e8:e4:4e:43
[14274.651796] wlan0: RX ReassocResp from 00:15:e8:e4:4e:43 (capab=0x411 status=0 aid=1)
[14274.651807] wlan0: associated
[14351.857336] wlan0: authenticate with AP 00:15:e8:e4:2c:82
[14351.858900] wlan0: authenticated
[14351.858913] wlan0: associate with AP 00:15:e8:e4:2c:82
[14351.878701] wlan0: RX ReassocResp from 00:15:e8:e4:2c:82 (capab=0x411 status=0 aid=3)
[14351.878713] wlan0: associated
```

It keeps reassociating with different access points. The university I am at has many access points with the same SSID. Could this be a problem?

```
10:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection [8086:4229] (rev 61)
	Subsystem: Intel Corporation Device [8086:1100]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 217
	Region 0: Memory at e4000000 (64-bit, non-prefetchable) [size=8K]
	Capabilities: [c8] Power Management version 3
		Flags: PMEClk- DSI+ D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [d0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+
		Address: 00000000fee0300c  Data: 41aa
	Capabilities: [e0] Express (v1) Endpoint, MSI 00
		DevCap:	MaxPayload 128 bytes, PhantFunc 0, Latency L0s <512ns, L1 unlimited
			ExtTag- AttnBtn- AttnInd- PwrInd- RBE+ FLReset-
		DevCtl:	Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
			RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop+
			MaxPayload 128 bytes, MaxReadReq 128 bytes
		DevSta:	CorrErr+ UncorrErr- FatalErr- UnsuppReq+ AuxPwr+ TransPend-
		LnkCap:	Port #0, Speed 2.5GT/s, Width x1, ASPM L0s L1, Latency L0 <128ns, L1 <64us
			ClockPM+ Suprise- LLActRep- BwNot-
		LnkCtl:	ASPM L1 Enabled; RCB 64 bytes Disabled- Retrain- CommClk+
			ExtSynch- ClockPM+ AutWidDis- BWInt- AutBWInt-
		LnkSta:	Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
	Capabilities: [100] Advanced Error Reporting <?>
	Capabilities: [140] Device Serial Number 9b-72-a1-ff-ff-3b-1f-00
	Kernel driver in use: iwlagn
	Kernel modules: iwlagn

```

Linux schmidjw 2.6.27-11-generic #1 SMP Thu Jan 29 19:24:39 UTC 2009 i686 GNU/Linux

Ubuntu

If anything else would help, name it. I would like this resolved.

---

### Post by kafkaian on 2009-02-27
I look forward to the next LTS release which I'll stick with. Intrepid has caused all sorts of issues not least the continual wireless drop out

---

### Post by tarahmarie on 2011-03-19
Same here, and now we're on Meerkat. Does anyone know why wlan0 interfaces drop connections seemingly randomly and require authentication to restart?

---

